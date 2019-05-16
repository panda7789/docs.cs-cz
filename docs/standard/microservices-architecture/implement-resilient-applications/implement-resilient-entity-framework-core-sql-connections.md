---
title: Implementace odolných připojení Entity Framework Core SQL
description: Zjistěte, jak implementovat odolnost připojení Entity Framework Core SQL. Tato technika je zvlášť důležité při používání Azure SQL Database v cloudu.
ms.date: 10/16/2018
ms.openlocfilehash: 3bf5c1827cee1da69aeccdc9f15573c301fc9363
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639899"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="b80e8-104">Implementace odolných připojení Entity Framework Core SQL</span><span class="sxs-lookup"><span data-stu-id="b80e8-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="b80e8-105">Pro službu Azure SQL DB Entity Framework (EF) Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku.</span><span class="sxs-lookup"><span data-stu-id="b80e8-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="b80e8-106">Ale je potřeba povolit strategie provádění Entity Framework pro každou <xref:Microsoft.EntityFrameworkCore.DbContext> připojení, pokud chcete mít [odolnost připojení EF Core](/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="b80e8-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="b80e8-107">Například následující kód na úrovni připojení EF Core umožňuje odolnost připojení SQL, které se zopakují, pokud se nepovede.</span><span class="sxs-lookup"><span data-stu-id="b80e8-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="b80e8-108">Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts</span><span class="sxs-lookup"><span data-stu-id="b80e8-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="b80e8-109">Pokud opakované pokusy jsou povolené v EF Core připojení, bude každé operace, které můžete provádět pomocí EF Core vyvolaly provozu.</span><span class="sxs-lookup"><span data-stu-id="b80e8-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="b80e8-110">Každý dotaz a každé volání `SaveChanges` bude zopakován jako celek, pokud dojde k přechodnému selhání.</span><span class="sxs-lookup"><span data-stu-id="b80e8-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="b80e8-111">Nicméně pokud váš kód zahájí transakci pomocí `BeginTransaction`, definujete vlastní skupinu operací, které je třeba zacházet jako celek.</span><span class="sxs-lookup"><span data-stu-id="b80e8-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="b80e8-112">Všechno, co je uvnitř transakce má být vrácena zpět, pokud dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="b80e8-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="b80e8-113">Pokud se pokusíte spustit transakci, při použití strategie provádění EF (zásady opakování) a zavoláte `SaveChanges` z více DbContexts, zobrazí se výjimka podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="b80e8-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="b80e8-114">System.InvalidOperationException: Strategie provádění nakonfigurované "SqlServerRetryingExecutionStrategy" nepodporuje transakce iniciované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b80e8-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="b80e8-115">Použití strategie provádění vrácený "DbContext.Database.CreateExecutionStrategy()" provádět všechny operace v transakci jako vyvolaly jednotky.</span><span class="sxs-lookup"><span data-stu-id="b80e8-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="b80e8-116">Řešením je vyvolat strategie provádění EF s všechno, co představuje delegáta, který je nutné spustit ručně.</span><span class="sxs-lookup"><span data-stu-id="b80e8-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="b80e8-117">Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta.</span><span class="sxs-lookup"><span data-stu-id="b80e8-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="b80e8-118">Například následující kód zobrazí, jak se má implementovat v aplikaci eShopOnContainers se dvěma více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a potom uložení ProductPriceChangedIntegrationEvent objektu, který je potřeba použít jiné DbContext.</span><span class="sxs-lookup"><span data-stu-id="b80e8-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="b80e8-119">První <xref:Microsoft.EntityFrameworkCore.DbContext> je `_catalogContext` a druhá `DbContext` spadá `_integrationEventLogService` objektu.</span><span class="sxs-lookup"><span data-stu-id="b80e8-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_integrationEventLogService` object.</span></span> <span data-ttu-id="b80e8-120">Provedení akce potvrzení napříč všemi `DbContext` objektů pomocí EF strategie provádění.</span><span class="sxs-lookup"><span data-stu-id="b80e8-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="b80e8-121">K dosažení této více `DbContext` potvrzení, `SaveEventAndCatalogContextChangesAsync` používá `ResilientTransaction` třídy, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b80e8-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

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

<span data-ttu-id="b80e8-122">`ResilientTransaction.ExecuteAsync` Metoda začíná v podstatě transakce z předaného `DbContext` (`_catalogContext`) a pak `EventLogService` můžete uložit změny z dané transakce `IntegrationEventLogContext` a potom potvrzení celá transakce.</span><span class="sxs-lookup"><span data-stu-id="b80e8-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="b80e8-123">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b80e8-123">Additional resources</span></span>

- <span data-ttu-id="b80e8-124">**Odolnost připojení a zachycení příkazů s EF v aplikaci ASP.NET MVC** \\</span><span class="sxs-lookup"><span data-stu-id="b80e8-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** \\</span></span>
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="b80e8-125">**De la Torre Cesarovi. Pomocí odolné Entity Framework Core SQL připojení a transakce** \\</span><span class="sxs-lookup"><span data-stu-id="b80e8-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** \\</span></span>
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="b80e8-126">[Předchozí](implement-retries-exponential-backoff.md)
>[další](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="b80e8-126">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>
