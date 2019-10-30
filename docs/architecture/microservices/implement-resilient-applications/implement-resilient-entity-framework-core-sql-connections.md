---
title: Implementace odolných Entity Framework Core připojení SQL
description: Naučte se implementovat odolná Entity Framework Core připojení SQL. Tato technika je obzvláště důležitá při použití Azure SQL Database v cloudu.
ms.date: 10/16/2018
ms.openlocfilehash: 3128cf1be7f2dc8804a002556db232f4e0fc8c33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094052"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementace odolných Entity Framework Core připojení SQL

Pro Azure SQL DB, Entity Framework (EF), již základní jádro poskytuje odolnost interního připojení databáze a logiku opakování. Pro každé připojení <xref:Microsoft.EntityFrameworkCore.DbContext> ale musíte povolit strategii spouštění Entity Framework, pokud chcete mít [odolná EF Coreová připojení](/ef/core/miscellaneous/connection-resiliency).

Například následující kód na úrovni připojení EF Core umožňuje odolné připojení SQL, které se opakuje, pokud se připojení nepovede.

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

Když jsou v EF Core připojení povolené opakované pokusy, každá operace, kterou provedete pomocí EF Core, se stal svou vlastní operací vyvolaly. Každý dotaz a každé volání `SaveChanges` se bude opakovat jako jednotka, pokud dojde k přechodnému selhání.

Nicméně pokud váš kód inicializuje transakci pomocí `BeginTransaction`, definujete vlastní skupinu operací, které je třeba považovat za jednotku. Vše uvnitř transakce se musí vrátit zpátky, pokud dojde k selhání.

Pokud se pokusíte provést tuto transakci při použití strategie provádění EF (opakování zásad) a zavoláte `SaveChanges` z více DbContexts, získáte výjimku, jako je tato:

> System. InvalidOperationException: nakonfigurovaná strategie provádění SqlServerRetryingExecutionStrategy nepodporuje transakce iniciované uživatelem. K provedení všech operací v transakci jako jednotky vyvolaly použijte strategii spuštění vrácenou funkcí DbContext. Database. CreateExecutionStrategy ().

Řešením je ruční vyvolání strategie provádění EF s delegátem, který představuje všechno, co je třeba provést. Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta. Například následující kód ukazuje, jak je implementován v eShopOnContainers pomocí dvou více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a následném uložení ProductPriceChangedIntegrationEvent objekt, který potřebuje použít jiný DbContext.

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

První <xref:Microsoft.EntityFrameworkCore.DbContext> je `_catalogContext` a druhý `DbContext` v rámci objektu `_integrationEventLogService`. Akce potvrzení se provádí napříč všemi `DbContext` objekty pomocí strategie provádění EF.

Chcete-li dosáhnout tohoto vícenásobného potvrzení `DbContext`, `SaveEventAndCatalogContextChangesAsync` používá třídu `ResilientTransaction`, jak je znázorněno v následujícím kódu:

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

Metoda `ResilientTransaction.ExecuteAsync` v podstatě zahájí transakci z předaného `DbContext` (`_catalogContext`) a pak `EventLogService` tuto transakci použije k uložení změn z `IntegrationEventLogContext` a následnému potvrzení celé transakce.

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

- **Odolnost připojení a zachycení příkazů pomocí EF v aplikaci ASP.NET MVC** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. Používání odolných Entity Framework Core připojení a transakcí SQL** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Předchozí](implement-retries-exponential-backoff.md)
>[Další](explore-custom-http-call-retries-exponential-backoff.md)
