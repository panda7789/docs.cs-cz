---
title: Implementace odolných připojení Entity Framework Core SQL
description: Zjistěte, jak implementovat odolnost připojení Entity Framework Core SQL. Tato technika je zvlášť důležité při používání Azure SQL Database v cloudu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 022fa482cf7b629be00a979550b02a2616830d09
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462575"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementace odolných připojení Entity Framework Core SQL

Pro službu Azure SQL DB Entity Framework (EF) Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku. Ale je potřeba povolit strategie provádění Entity Framework pro každou <xref:Microsoft.EntityFrameworkCore.DbContext> připojení, pokud chcete mít [odolnost připojení EF Core](/ef/core/miscellaneous/connection-resiliency).

Například následující kód na úrovni připojení EF Core umožňuje odolnost připojení SQL, které se zopakují, pokud se nepovede.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts

Pokud opakované pokusy jsou povolené v EF Core připojení, bude každé operace, které můžete provádět pomocí EF Core vyvolaly provozu. Každý dotaz a každé volání `SaveChanges` bude zopakován jako celek, pokud dojde k přechodnému selhání.

Nicméně pokud váš kód zahájí transakci pomocí `BeginTransaction`, definujete vlastní skupinu operací, které je třeba zacházet jako celek. Všechno, co je uvnitř transakce má být vrácena zpět, pokud dojde k chybě.

Pokud se pokusíte spustit transakci, při použití strategie provádění EF (zásady opakování) a zavoláte `SaveChanges` z více DbContexts, zobrazí se výjimka podobný následujícímu:

> System.InvalidOperationException: Strategie provádění nakonfigurované "SqlServerRetryingExecutionStrategy" nepodporuje transakce iniciované uživatelem. Použití strategie provádění vrácený "DbContext.Database.CreateExecutionStrategy()" provádět všechny operace v transakci jako vyvolaly jednotky.

Řešením je vyvolat strategie provádění EF s všechno, co představuje delegáta, který je nutné spustit ručně. Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta. Například následující kód zobrazí, jak se má implementovat v aplikaci eShopOnContainers se dvěma více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a potom uložení ProductPriceChangedIntegrationEvent objektu, který je potřeba použít jiné DbContext.

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

První <xref:Microsoft.EntityFrameworkCore.DbContext> je `_catalogContext` a druhá `DbContext` spadá `_integrationEventLogService` objektu. Provedení akce potvrzení napříč všemi `DbContext` objektů pomocí EF strategie provádění.

K dosažení této více `DbContext` potvrzení, `SaveEventAndCatalogContextChangesAsync` používá `ResilientTransaction` třídy, jak je znázorněno v následujícím kódu:

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database 
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

`ResilientTransaction.ExecuteAsync` Metoda začíná v podstatě transakce z předaného `DbContext` (`_catalogContext`) a pak `EventLogService` můžete uložit změny z dané transakce `IntegrationEventLogContext` a potom potvrzení celá transakce.

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts 
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            using (var transaction = _context.Database.BeginTransaction())
            {
                await action();
                transaction.Commit();
            }
        });
    }
}
```

## <a name="additional-resources"></a>Další zdroje

- **Odolnost připojení a zachycení příkazů s EF v aplikaci ASP.NET MVC** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **De la Torre Cesarovi. Pomocí odolné Entity Framework Core SQL připojení a transakce** \
  [https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/](https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/)

>[!div class="step-by-step"]
>[Předchozí](implement-retries-exponential-backoff.md)
>[další](explore-custom-http-call-retries-exponential-backoff.md)