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
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="10bcd-104">Implementace odolných Entity Framework Core připojení SQL</span><span class="sxs-lookup"><span data-stu-id="10bcd-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="10bcd-105">Pro Azure SQL DB, Entity Framework (EF), již základní jádro poskytuje odolnost interního připojení databáze a logiku opakování.</span><span class="sxs-lookup"><span data-stu-id="10bcd-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="10bcd-106">Pro každé připojení <xref:Microsoft.EntityFrameworkCore.DbContext> ale musíte povolit strategii spouštění Entity Framework, pokud chcete mít [odolná EF Coreová připojení](/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="10bcd-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="10bcd-107">Například následující kód na úrovni připojení EF Core umožňuje odolné připojení SQL, které se opakuje, pokud se připojení nepovede.</span><span class="sxs-lookup"><span data-stu-id="10bcd-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="10bcd-108">Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts</span><span class="sxs-lookup"><span data-stu-id="10bcd-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="10bcd-109">Když jsou v EF Core připojení povolené opakované pokusy, každá operace, kterou provedete pomocí EF Core, se stal svou vlastní operací vyvolaly.</span><span class="sxs-lookup"><span data-stu-id="10bcd-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="10bcd-110">Každý dotaz a každé volání `SaveChanges` se bude opakovat jako jednotka, pokud dojde k přechodnému selhání.</span><span class="sxs-lookup"><span data-stu-id="10bcd-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="10bcd-111">Nicméně pokud váš kód inicializuje transakci pomocí `BeginTransaction`, definujete vlastní skupinu operací, které je třeba považovat za jednotku.</span><span class="sxs-lookup"><span data-stu-id="10bcd-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="10bcd-112">Vše uvnitř transakce se musí vrátit zpátky, pokud dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="10bcd-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="10bcd-113">Pokud se pokusíte provést tuto transakci při použití strategie provádění EF (opakování zásad) a zavoláte `SaveChanges` z více DbContexts, získáte výjimku, jako je tato:</span><span class="sxs-lookup"><span data-stu-id="10bcd-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="10bcd-114">System. InvalidOperationException: nakonfigurovaná strategie provádění SqlServerRetryingExecutionStrategy nepodporuje transakce iniciované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="10bcd-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="10bcd-115">K provedení všech operací v transakci jako jednotky vyvolaly použijte strategii spuštění vrácenou funkcí DbContext. Database. CreateExecutionStrategy ().</span><span class="sxs-lookup"><span data-stu-id="10bcd-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="10bcd-116">Řešením je ruční vyvolání strategie provádění EF s delegátem, který představuje všechno, co je třeba provést.</span><span class="sxs-lookup"><span data-stu-id="10bcd-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="10bcd-117">Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta.</span><span class="sxs-lookup"><span data-stu-id="10bcd-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="10bcd-118">Například následující kód ukazuje, jak je implementován v eShopOnContainers pomocí dvou více DbContexts (\_catalogContext a IntegrationEventLogContext) při aktualizaci produktu a následném uložení ProductPriceChangedIntegrationEvent objekt, který potřebuje použít jiný DbContext.</span><span class="sxs-lookup"><span data-stu-id="10bcd-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="10bcd-119">První <xref:Microsoft.EntityFrameworkCore.DbContext> je `_catalogContext` a druhý `DbContext` v rámci objektu `_integrationEventLogService`.</span><span class="sxs-lookup"><span data-stu-id="10bcd-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_integrationEventLogService` object.</span></span> <span data-ttu-id="10bcd-120">Akce potvrzení se provádí napříč všemi `DbContext` objekty pomocí strategie provádění EF.</span><span class="sxs-lookup"><span data-stu-id="10bcd-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="10bcd-121">Chcete-li dosáhnout tohoto vícenásobného potvrzení `DbContext`, `SaveEventAndCatalogContextChangesAsync` používá třídu `ResilientTransaction`, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="10bcd-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

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

<span data-ttu-id="10bcd-122">Metoda `ResilientTransaction.ExecuteAsync` v podstatě zahájí transakci z předaného `DbContext` (`_catalogContext`) a pak `EventLogService` tuto transakci použije k uložení změn z `IntegrationEventLogContext` a následnému potvrzení celé transakce.</span><span class="sxs-lookup"><span data-stu-id="10bcd-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="10bcd-123">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="10bcd-123">Additional resources</span></span>

- <span data-ttu-id="10bcd-124">**Odolnost připojení a zachycení příkazů pomocí EF v aplikaci ASP.NET MVC** </span><span class="sxs-lookup"><span data-stu-id="10bcd-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** </span></span>\
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="10bcd-125">**Cesar de la Torre. Používání odolných Entity Framework Core připojení a transakcí SQL** </span><span class="sxs-lookup"><span data-stu-id="10bcd-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="10bcd-126">[Předchozí](implement-retries-exponential-backoff.md)
>[Další](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="10bcd-126">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>
