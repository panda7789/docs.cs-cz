---
title: "Implementace odolné připojení SQL základní Entity Framework"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace odolné připojení SQL základní Entity Framework"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b37d2c5683aff44165d0330c8d42fc881effbb76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>Implementace odolné připojení SQL základní Entity Framework

Pro databáze SQL Azure Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku. Ale musíte povolit strategii provádění Entity Framework pro každé připojení DbContext, pokud chcete mít [odolné připojení EF základní](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

Například následující kód na úrovni připojení EF základní umožňuje odolné připojení SQL, které jsou opakovat, pokud se nepovede připojit.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 5,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie provádění a pomocí zahájení transakce a více DbContexts explicitních transakcí

Když opakování jsou povolena v připojení EF jádra, stane jednotlivých operací, které můžete provádět pomocí EF základní vlastní dá se zkusit znovu operaci. Každý dotaz a každé volání SaveChanges bude zopakován jako jednotku, pokud dojde k přechodné chybě.

Ale pokud kódu inicializuje transakci pomocí zahájení transakce, definujete vlastní skupiny operací, které musí být považovány za jednotku – všechno uvnitř transakce se vrátila zpět v případě, že dojde k chybě. Výjimku takto se zobrazí, pokud se pokusíte provést tuto transakci, při použití EF strategii provádění (zásady opakování) a zahrnují několik SaveChanges volání z více DbContexts v transakci.

> System.InvalidOperationException: V nakonfigurované strategii provádění 'SqlServerRetryingExecutionStrategy' nepodporuje transakce inicializované uživatelem. Použijte strategii provádění vrácený 'DbContext.Database.CreateExecutionStrategy()' provádět všechny operace v rámci transakce jako nevyřeší jednotku.

Řešení je ručně vyvolání strategie provádění EF s představující všechno delegáta, který je třeba provést. Pokud dojde k přechodné chybě, bude strategii provádění znovu vyvolání delegáta. Například následující kód ukazují, jak jsou implementované v eShopOnContainers se dvěma více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a potom uložení ProductPriceChangedIntegrationEvent objekt, který se musí použít jiný DbContext.

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

Je první DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu. Potvrzení akce se provádí napříč více DbContexts pomocí strategie provádění EF.

## <a name="additional-resources"></a>Další zdroje

-   **Odolnost připojení a zachycením příkaz s použitím Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesaru členka Torre. Pomocí připojení Sql základní odolné Entity Framework a transakce**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[Předchozí] (implementace opakování exponenciální backoff.md) [Další] (implement-custom-http-call-retries-exponential-backoff.md)
