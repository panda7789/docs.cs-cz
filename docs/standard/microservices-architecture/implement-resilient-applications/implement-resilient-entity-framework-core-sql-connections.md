---
title: Implementace odolné připojení SQL základní Entity Framework
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace odolné připojení SQL základní Entity Framework
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 79f115a2d897463c213eda6f4d6951ff0cbeb3ca
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105472"
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="22825-103">Implementace odolné připojení SQL základní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="22825-103">Implementing resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="22825-104">Pro databáze SQL Azure Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku.</span><span class="sxs-lookup"><span data-stu-id="22825-104">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="22825-105">Ale musíte povolit strategii provádění Entity Framework pro každé připojení DbContext, pokud chcete mít [odolné připojení EF základní](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="22825-105">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="22825-106">Například následující kód na úrovni připojení EF základní umožňuje odolné připojení SQL, které jsou opakovat, pokud se nepovede připojit.</span><span class="sxs-lookup"><span data-stu-id="22825-106">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="22825-107">Strategie provádění a pomocí zahájení transakce a více DbContexts explicitních transakcí</span><span class="sxs-lookup"><span data-stu-id="22825-107">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="22825-108">Když opakování jsou povolena v připojení EF jádra, stane jednotlivých operací, které můžete provádět pomocí EF základní vlastní dá se zkusit znovu operaci.</span><span class="sxs-lookup"><span data-stu-id="22825-108">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="22825-109">Každý dotaz a každé volání SaveChanges bude zopakován jako jednotku, pokud dojde k přechodné chybě.</span><span class="sxs-lookup"><span data-stu-id="22825-109">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="22825-110">Ale pokud kódu inicializuje transakci pomocí zahájení transakce, definujete vlastní skupiny operací, které musí být považovány za jednotku – všechno uvnitř transakce se vrátila zpět v případě, že dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="22825-110">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="22825-111">Výjimku takto se zobrazí, pokud se pokusíte provést tuto transakci, při použití EF strategii provádění (zásady opakování) a zahrnují několik SaveChanges volání z více DbContexts v transakci.</span><span class="sxs-lookup"><span data-stu-id="22825-111">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="22825-112">System.InvalidOperationException: V nakonfigurované strategii provádění 'SqlServerRetryingExecutionStrategy' nepodporuje transakce inicializované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="22825-112">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="22825-113">Použijte strategii provádění vrácený 'DbContext.Database.CreateExecutionStrategy()' provádět všechny operace v rámci transakce jako nevyřeší jednotku.</span><span class="sxs-lookup"><span data-stu-id="22825-113">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="22825-114">Řešení je ručně vyvolání strategie provádění EF s představující všechno delegáta, který je třeba provést.</span><span class="sxs-lookup"><span data-stu-id="22825-114">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="22825-115">Pokud dojde k přechodné chybě, bude strategii provádění znovu vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="22825-115">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="22825-116">Například následující kód ukazují, jak jsou implementované v eShopOnContainers se dvěma více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a potom uložení ProductPriceChangedIntegrationEvent objekt, který se musí použít jiný DbContext.</span><span class="sxs-lookup"><span data-stu-id="22825-116">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="22825-117">Je první DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu.</span><span class="sxs-lookup"><span data-stu-id="22825-117">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="22825-118">Potvrzení akce se provádí napříč více DbContexts pomocí strategie provádění EF.</span><span class="sxs-lookup"><span data-stu-id="22825-118">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="22825-119">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="22825-119">Additional resources</span></span>

-   <span data-ttu-id="22825-120">**Odolnost připojení a zachycením příkaz s použitím Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="22825-120">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="22825-121">**Cesaru členka Torre. Pomocí připojení Sql základní odolné Entity Framework a transakce**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="22825-121">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="22825-122">[Předchozí](implement-retries-exponential-backoff.md)
[další](implement-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="22825-122">[Previous](implement-retries-exponential-backoff.md)
[Next](implement-custom-http-call-retries-exponential-backoff.md)</span></span>
