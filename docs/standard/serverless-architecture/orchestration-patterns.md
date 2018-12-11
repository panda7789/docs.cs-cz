---
title: Orchestrace vzorky – aplikace bez serveru
description: Žádost o přijetí změn Azure Durable functions
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: c3b9dbe473ba9272a8c8c07cec86e11fcd9fc12d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129308"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="ca6bb-103">Vzory Orchestrace</span><span class="sxs-lookup"><span data-stu-id="ca6bb-103">Orchestration patterns</span></span>

<span data-ttu-id="ca6bb-104">Odolná služba Functions usnadňuje vytváření stavové pracovních postupů, které se skládají z aktivit diskrétní, dlouho běžící v prostředí bez serveru.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="ca6bb-105">Protože Durable Functions průběh můžete sledovat vaše pracovní postupy a pravidelně kontrolní body historie spuštění, ho slouží k provádění některých zajímavých vzorců.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="ca6bb-106">Funkce řetězení</span><span class="sxs-lookup"><span data-stu-id="ca6bb-106">Function chaining</span></span>

<span data-ttu-id="ca6bb-107">Aktivity v typické sekvenční procesu, potřebují spustit jeden za druhým v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="ca6bb-108">Volitelně můžete nadcházející aktivita může vyžadovat některé výstup z předchozí funkce.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="ca6bb-109">Tato závislost na pořadí aktivit vznikne řetěz funkce spuštění.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="ca6bb-110">Výhodou použití Durable Functions k implementaci tohoto modelu pracovního postupu pochází z jeho možnost vytváření kontrolních bodů.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="ca6bb-111">Pokud dojde k chybě na serveru, sítě vyprší časový limit nebo dojde k některý problém, Durable functions můžete obnovit z posledního známého stavu a pokračování ve spouštění pracovního postupu, i v případě, že je na jiný server.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

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

<span data-ttu-id="ca6bb-112">V předchozí ukázce kódu `CallActivityAsync` funkce je zodpovědný za spouštění danou aktivitu na virtuálním počítači v datovém centru.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="ca6bb-113">Po dokončení vrátí await a základní úkol, provádění se zaznamená do tabulky historie.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="ca6bb-114">Kód ve funkci orchestrator můžete vytvořit pomocí některého z známé konstrukce Task Parallel Library a klíčová slova async/await.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="ca6bb-115">Následující kód je zjednodušený příklad postupu `ProcessPayment` metoda může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="ca6bb-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

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

## <a name="asynchronous-http-apis"></a><span data-ttu-id="ca6bb-116">Asynchronní rozhraní API protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="ca6bb-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="ca6bb-117">V některých případech může obsahovat pracovní postupy aktivity, které trvat poměrně dlouhou dobu čas dokončení.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="ca6bb-118">Představte si je proces, který zahajuje zálohování média soubory do úložiště objektů blob.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="ca6bb-119">V závislosti na velikosti a množství mediálních souborů tento záložní proces může trvat hodiny.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="ca6bb-120">V tomto scénáři `DurableOrchestrationClient`na kontrolu stavu s běžícím workflowem bloků se stává užitečným.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="ca6bb-121">Při použití `HttpTrigger` se spustit pracovní postup `CreateCheckStatusResponse` metodu je možné vrátit instanci `HttpResponseMessage`.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="ca6bb-122">Tato odpověď poskytuje klienta s identifikátorem URI v datové části je možné zkontrolovat stav běžící proces.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

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

<span data-ttu-id="ca6bb-123">Následující ukázka výsledku znázorňuje strukturu datové části odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="ca6bb-124">Pomocí upřednostňovaných klienta protokolu HTTP, požadavky GET lze provádět na identifikátor URI v statusQueryGetUri kontrolovat stav spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="ca6bb-125">Odpověď vrácená stavu by měla vypadat následovně.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-125">The returned status response should resemble the following code.</span></span>

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

<span data-ttu-id="ca6bb-126">Jak proces pokračuje, odpověď na stav se změní na buď **neúspěšné** nebo **dokončeno**.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="ca6bb-127">Při úspěšném dokončení **výstup** vlastnost v datové části bude obsahovat všechny vrácená data.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="ca6bb-128">Monitorování</span><span class="sxs-lookup"><span data-stu-id="ca6bb-128">Monitoring</span></span>

<span data-ttu-id="ca6bb-129">Pro jednoduché opakované úlohy, služba Azure Functions umožňuje `TimerTrigger` , který můžete naplánovat na základě výrazu CRON.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="ca6bb-130">Časovač se dá použít i pro jednoduché, krátkodobé a jednorázové úlohy, mohou se však vyskytnout scénáře, které vyžadují více flexibilní plánování.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="ca6bb-131">Tento scénář je při monitorování vzor a odolná služba Functions může pomoct.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="ca6bb-132">Odolná služba Functions umožňuje flexibilní plánování intervalech a správa životního cyklu a také vytváří více procesů monitorování z jednoho Orchestrace funkce.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="ca6bb-133">Jeden případ použití pro tuto funkci může být vytvoření sledovací procesy pro minimální cenu akcie změny, které po splnění určitou prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

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

<span data-ttu-id="ca6bb-134">`DurableOrchestrationContext`společnosti `CreateTimer` metoda nastaví plán, další vyvolání příkazu smyčky, která zkontroluje změny minimální cenu akcie.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="ca6bb-135">`DurableOrchestrationContext` má také `CurrentUtcDateTime` vlastnost k získání aktuální hodnoty datum a čas ve standardu UTC.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="ca6bb-136">Je vhodnější použít tuto vlastnost místo `DateTime.UtcNow` vzhledem k tomu, že je snadno imitace pro testování.</span><span class="sxs-lookup"><span data-stu-id="ca6bb-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="ca6bb-137">Doporučené studijní materiály</span><span class="sxs-lookup"><span data-stu-id="ca6bb-137">Recommended resources</span></span>

* [<span data-ttu-id="ca6bb-138">Odolná služba Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ca6bb-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="ca6bb-139">Testování jednotek v .NET Core a .NET Standard</span><span class="sxs-lookup"><span data-stu-id="ca6bb-139">Unit Testing in .NET Core and .NET Standard</span></span>](https://docs.microsoft.com/dotnet/core/testing/)

>[!div class="step-by-step"]
><span data-ttu-id="ca6bb-140">[Předchozí](durable-azure-functions.md)
>[další](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="ca6bb-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>