---
title: Vzory orchestrace – aplikace bez serveru
description: Funkce Azure Durable pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2bd81c29e727254af6c8ecf39ee4bfef1f39d009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522634"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="d2f26-103">Vzory orchestrace</span><span class="sxs-lookup"><span data-stu-id="d2f26-103">Orchestration patterns</span></span>

<span data-ttu-id="d2f26-104">Trvalé funkce usnadňuje vytváření stavových pracovních postupů, které se skládají z diskrétních, dlouhotrvajících aktivit v prostředí bez serveru.</span><span class="sxs-lookup"><span data-stu-id="d2f26-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="d2f26-105">Vzhledem k tomu, že trvalé funkce můžete sledovat průběh pracovních postupů a pravidelně kontrolní body historie provádění, půjčuje se k implementaci některé zajímavé vzory.</span><span class="sxs-lookup"><span data-stu-id="d2f26-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="d2f26-106">Řetězení funkcí</span><span class="sxs-lookup"><span data-stu-id="d2f26-106">Function chaining</span></span>

<span data-ttu-id="d2f26-107">V typickém sekvenčním procesu je třeba aktivity provádět jeden po druhém v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="d2f26-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="d2f26-108">Volitelně nadcházející aktivita může vyžadovat určitý výstup z předchozí funkce.</span><span class="sxs-lookup"><span data-stu-id="d2f26-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="d2f26-109">Tato závislost na řazení aktivit vytvoří řetězec funkcí provádění.</span><span class="sxs-lookup"><span data-stu-id="d2f26-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="d2f26-110">Výhodou použití trvalé funkce k implementaci tohoto vzoru pracovního postupu pochází z jeho schopnost provádět vytváření kontrolních bodů.</span><span class="sxs-lookup"><span data-stu-id="d2f26-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="d2f26-111">Pokud dojde k chybě serveru, časový mat v síti nebo dojde k jinému problému, trvalé funkce mohou pokračovat z posledního známého stavu a pokračovat ve spuštění pracovního postupu, i když je na jiném serveru.</span><span class="sxs-lookup"><span data-stu-id="d2f26-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="d2f26-112">V předchozí ukázce `CallActivityAsync` kódu je funkce zodpovědná za spuštění dané aktivity na virtuálním počítači v datovém centru.</span><span class="sxs-lookup"><span data-stu-id="d2f26-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="d2f26-113">Když await vrátí a základní Task dokončí, spuštění se zaznamená do tabulky historie.</span><span class="sxs-lookup"><span data-stu-id="d2f26-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="d2f26-114">Kód ve funkci orchestrator můžete využít některé známé konstrukce task paralelní knihovny a async/await klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="d2f26-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="d2f26-115">Následující kód je zjednodušeným příkladem `ProcessPayment` toho, jak může metoda vypadat:</span><span class="sxs-lookup"><span data-stu-id="d2f26-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a><span data-ttu-id="d2f26-116">Asynchronní http api</span><span class="sxs-lookup"><span data-stu-id="d2f26-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="d2f26-117">V některých případech mohou pracovní postupy obsahovat aktivity, které jejich dokončení trvá poměrně dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="d2f26-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="d2f26-118">Představte si proces, který spustí zálohování mediálních souborů do úložiště objektů blob.</span><span class="sxs-lookup"><span data-stu-id="d2f26-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="d2f26-119">V závislosti na velikosti a množství mediálních souborů může dokončení tohoto procesu zálohování trvat hodiny.</span><span class="sxs-lookup"><span data-stu-id="d2f26-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="d2f26-120">V tomto scénáři `DurableOrchestrationClient`'s schopnost zkontrolovat stav spuštěného pracovního postupu se stane užitečné.</span><span class="sxs-lookup"><span data-stu-id="d2f26-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="d2f26-121">Při použití `HttpTrigger` a ke spuštění `CreateCheckStatusResponse` pracovního postupu lze metodu použít k vrácení instance aplikace `HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="d2f26-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="d2f26-122">Tato odpověď poskytuje klientovi identifikátor URI v datové části, který lze použít ke kontrole stavu spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="d2f26-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

<span data-ttu-id="d2f26-123">Ukázkový výsledek níže ukazuje strukturu datové části odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d2f26-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="d2f26-124">Pomocí upřednostňovaného klienta HTTP mohou být požadavky GET provedeny na identifikátor URI ve statusQueryGetUri ke kontrole stavu spuštěného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d2f26-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="d2f26-125">Vrácená odpověď na stav by se měla podobat následujícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="d2f26-125">The returned status response should resemble the following code.</span></span>

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

<span data-ttu-id="d2f26-126">Jak proces pokračuje, odpověď na stav se změní na **Neúspěšná** nebo **Dokončená**.</span><span class="sxs-lookup"><span data-stu-id="d2f26-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="d2f26-127">Po úspěšném dokončení **bude výstupní** vlastnost v datové části obsahovat všechna vrácená data.</span><span class="sxs-lookup"><span data-stu-id="d2f26-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="d2f26-128">Monitorování</span><span class="sxs-lookup"><span data-stu-id="d2f26-128">Monitoring</span></span>

<span data-ttu-id="d2f26-129">Pro jednoduché opakované úkoly `TimerTrigger` Azure Functions poskytuje, které lze naplánovat na základě výrazu CRON.</span><span class="sxs-lookup"><span data-stu-id="d2f26-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="d2f26-130">Časovač funguje dobře pro jednoduché, krátkodobé úkoly, ale mohou existovat scénáře, kde je potřeba flexibilnější plánování.</span><span class="sxs-lookup"><span data-stu-id="d2f26-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="d2f26-131">Tento scénář je, když může pomoci vzor monitorování a trvalé funkce.</span><span class="sxs-lookup"><span data-stu-id="d2f26-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="d2f26-132">Trvalé funkce umožňuje flexibilní intervaly plánování, správu životnosti a vytváření více procesů monitorování z jediné funkce orchestrace.</span><span class="sxs-lookup"><span data-stu-id="d2f26-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="d2f26-133">Jeden případ použití pro tuto funkci může být vytvoření sledovacích modulů pro změny cen akcií, které dokončí po splnění určité prahové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2f26-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

<span data-ttu-id="d2f26-134">`DurableOrchestrationContext`Metoda `CreateTimer` programu nastaví plán pro další vyvolání smyčky a zkontroluje se změna ceny akcií.</span><span class="sxs-lookup"><span data-stu-id="d2f26-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="d2f26-135">`DurableOrchestrationContext`má také `CurrentUtcDateTime` vlastnost získat aktuální DateTime hodnotu v UTC.</span><span class="sxs-lookup"><span data-stu-id="d2f26-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="d2f26-136">Je lepší použít tuto vlastnost `DateTime.UtcNow` namísto toho, protože je to snadno zesměšňován pro testování.</span><span class="sxs-lookup"><span data-stu-id="d2f26-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="d2f26-137">Doporučené zdroje</span><span class="sxs-lookup"><span data-stu-id="d2f26-137">Recommended resources</span></span>

- [<span data-ttu-id="d2f26-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="d2f26-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="d2f26-139">Testování částí ve standardu .NET Core a .NET</span><span class="sxs-lookup"><span data-stu-id="d2f26-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="d2f26-140">[Předchozí](durable-azure-functions.md)
>[další](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="d2f26-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
