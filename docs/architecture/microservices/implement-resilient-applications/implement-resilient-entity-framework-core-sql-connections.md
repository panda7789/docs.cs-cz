---
title: Implementace odolných připojení SQL core entity frameworku
description: Zjistěte, jak implementovat odolná připojení SQL core entity frameworku. Tato technika je obzvláště důležité při použití Azure SQL Database v cloudu.
ms.date: 10/16/2018
ms.openlocfilehash: 7a047edca21d63a451e90f407b23f3358d461330
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241062"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementace odolných připojení SQL core entity frameworku

Pro Azure SQL DB, Entity Framework (EF) Core již poskytuje odolnost proti interní připojení databáze a logiku opakování. Ale musíte povolit strategii provádění entity <xref:Microsoft.EntityFrameworkCore.DbContext> framework pro každé připojení, pokud chcete mít [odolné EF core připojení](/ef/core/miscellaneous/connection-resiliency).

Například následující kód na úrovni připojení EF Core umožňuje odolná připojení SQL, která jsou opakována, pokud se připojení nezdaří.

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

Pokud jsou v připojeních EF Core povoleny opakované pokusy, každá operace, kterou provedete pomocí EF Core, se stane vlastní opakovatelnou operací. Každý dotaz a `SaveChanges` každé volání bude opakováno jako jednotka, pokud dojde k přechodné chybě.

Pokud však váš kód iniciuje transakci pomocí `BeginTransaction`, definujete vlastní skupinu operací, které je třeba považovat za jednotku. Vše uvnitř transakce musí být vrácena zpět, pokud dojde k chybě.

Pokud se pokusíte provést tuto transakci při použití strategie spuštění `SaveChanges` EF (zásady opakování) a volání z více DbContexts, dostanete výjimku, jako je tato:

> System.InvalidOperationException: Nakonfigurovaná strategie spuštění SqlServerRetryingExecutionStrategy nepodporuje transakce iniciované uživatelem. Pomocí strategie provádění vrácené 'DbContext.Database.CreateExecutionStrategy()' provést všechny operace v transakci jako retriable jednotky.

Řešením je ručně vyvolat strategii provádění EF s delegátem představující vše, co je třeba provést. Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta. Například následující kód ukazují, jak je implementována v eShopOnContainers\_se dvěma více DbContexts (catalogContext a IntegrationEventLogContext) při aktualizaci produktu a potom uložení ProductPriceChangedIntegrationEvent objekt, který potřebuje použít jiný DbContext.

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

První <xref:Microsoft.EntityFrameworkCore.DbContext> je `_catalogContext` a `DbContext` druhý je `_catalogIntegrationEventService` v rámci objektu. Akce Potvrzení se provádí `DbContext` napříč všemi objekty pomocí strategie provádění EF.

K dosažení `DbContext` tohoto více `SaveEventAndCatalogContextChangesAsync` násobné potvrzení, používá třídu, `ResilientTransaction` jak je znázorněno v následujícím kódu:

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

Metoda `ResilientTransaction.ExecuteAsync` v podstatě začíná transakce `DbContext` z`_catalogContext`předán ( `EventLogService` ) a pak umožňuje `IntegrationEventLogContext` použití této transakce uložit změny z a potom potvrdí celou transakci.

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

- **Odolnost proti chybám připojení a příkazové zachycení s EF v ASP.NET aplikace MVC** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. Použití odolných entit framework core sql připojení a transakce** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Předchozí](implement-retries-exponential-backoff.md)
>[další](use-httpclientfactory-to-implement-resilient-http-requests.md)
