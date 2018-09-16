---
title: Implementace odolných připojení Entity Framework Core SQL
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace odolných připojení Entity Framework Core SQL. Tato technika je zvlášť důležité při používání Azure SQL Database v cloudu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 59db9cdb894f76f54e77732be47dc6140a594121
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668805"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="f0086-104">Implementace odolných připojení Entity Framework Core SQL</span><span class="sxs-lookup"><span data-stu-id="f0086-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="f0086-105">Pro službu Azure SQL DB Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku.</span><span class="sxs-lookup"><span data-stu-id="f0086-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="f0086-106">Ale je potřeba povolit strategie provádění Entity Framework pro každé připojení kontext databáze. Pokud chcete mít [odolnost připojení EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="f0086-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="f0086-107">Například následující kód na úrovni připojení EF Core umožňuje odolnost připojení SQL, které se zopakují, pokud se nepovede.</span><span class="sxs-lookup"><span data-stu-id="f0086-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="f0086-108">Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts</span><span class="sxs-lookup"><span data-stu-id="f0086-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="f0086-109">Pokud opakované pokusy jsou povolené v EF Core připojení, bude každé operace, které můžete provádět pomocí EF Core vlastní opakovatelné operace.</span><span class="sxs-lookup"><span data-stu-id="f0086-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="f0086-110">Každý dotaz a každé volání SaveChanges bude zopakován jako celek, pokud dojde k přechodnému selhání.</span><span class="sxs-lookup"><span data-stu-id="f0086-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="f0086-111">Ale pokud váš kód zahájí transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je potřeba za jednotku považuje – všechno, co je uvnitř transakce se vrátila zpět, pokud dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="f0086-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="f0086-112">Výjimku vypadat asi takto se zobrazí, pokud se pokusíte spustit transakci, při použití strategie provádění EF (zásady opakování) a zahrnují několik SaveChanges volání z více DbContexts v transakci.</span><span class="sxs-lookup"><span data-stu-id="f0086-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="f0086-113">System.InvalidOperationException: Strategie provádění nakonfigurované "SqlServerRetryingExecutionStrategy" nepodporuje transakce iniciované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="f0086-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="f0086-114">Použití strategie provádění vrácený "DbContext.Database.CreateExecutionStrategy()" provádět všechny operace v transakci jako vyvolaly jednotky.</span><span class="sxs-lookup"><span data-stu-id="f0086-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="f0086-115">Řešením je vyvolat strategie provádění EF s všechno, co představuje delegáta, který je nutné spustit ručně.</span><span class="sxs-lookup"><span data-stu-id="f0086-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="f0086-116">Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta.</span><span class="sxs-lookup"><span data-stu-id="f0086-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="f0086-117">Například následující kód zobrazí, jak je implementován v aplikaci eShopOnContainers se dvěma více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a potom uložení ProductPriceChangedIntegrationEvent objektu, který je potřeba použít jiné DbContext.</span><span class="sxs-lookup"><span data-stu-id="f0086-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="f0086-118">Je první objekt DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu.</span><span class="sxs-lookup"><span data-stu-id="f0086-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="f0086-119">Provedení akce potvrzení napříč více DbContexts použitím strategie provádění EF.</span><span class="sxs-lookup"><span data-stu-id="f0086-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f0086-120">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="f0086-120">Additional resources</span></span>

-   <span data-ttu-id="f0086-121">**Odolnost připojení EF** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="f0086-121">**EF Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="f0086-122">**Odolnost připojení a zachycení příkazů s rozhraním Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="f0086-122">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="f0086-123">**De la Torre Cesarovi. Pomocí odolné Entity Framework Core Sql připojení a transakce**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="f0086-123">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f0086-124">[Předchozí](implement-retries-exponential-backoff.md)
[další](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="f0086-124">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>
