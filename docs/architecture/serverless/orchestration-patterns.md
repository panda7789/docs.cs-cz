---
title: Vzory orchestrace – aplikace bez serveru
description: Trvalá funkce Azure pro trvalou činnost
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 18e13c5355490ef4a019ceda459114bdb6bfd539
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676736"
---
# <a name="orchestration-patterns"></a>Vzory orchestrace

Durable Functions usnadňuje vytváření stavových pracovních postupů, které se skládají z diskrétních a dlouhodobě běžících aktivit v prostředí bez serveru. Vzhledem k tomu, že Durable Functions může sledovat průběh vašich pracovních postupů a pravidelně vystavovat historii spouštění, zapůjčuje se sama na implementaci některých zajímavých vzorů.

## <a name="function-chaining"></a>Řetězení funkcí

V typickém sekvenčním procesu musí aktivity provádět jednu po druhé v určitém pořadí. V případě potřeby může nadcházející aktivita vyžadovat nějaký výstup z předchozí funkce. Tato závislost na řazení aktivit vytvoří řetěz funkce provádění.

Výhoda použití Durable Functions k implementaci tohoto vzoru pracovního postupu přichází z jeho schopnosti provádět vytváření kontrolních bodů. Pokud dojde k chybě serveru, dojde k vypršení časového limitu sítě nebo k jinému problému, trvalé funkce můžou obnovit z posledního známého stavu a pokračovat ve spuštění pracovního postupu i v případě, že se nachází na jiném serveru.

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

V předchozím příkladu `CallActivityAsync` kódu je funkce zodpovědná za spuštění dané aktivity na virtuálním počítači v datovém centru. Když funkce await vrátí a podkladovou úlohu dokončí, bude spuštění zaznamenáno do tabulky historie. Kód ve funkci Orchestrator může využít jakékoli známé konstrukce úlohy paralelní knihovny a klíčová slova Async/await.

Následující kód je zjednodušený příklad toho, `ProcessPayment` jak může metoda vypadat takto:

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

## <a name="asynchronous-http-apis"></a>Asynchronní rozhraní HTTP API

V některých případech mohou pracovní postupy obsahovat aktivity, které mohou trvat poměrně dlouhou dobu. Představte si proces, který zahájí zálohování mediálních souborů do úložiště objektů BLOB. V závislosti na velikosti a množství mediálních souborů může tento proces zálohování trvat i hodiny.

V tomto scénáři je možnost `DurableOrchestrationClient`kontrolovat stav spuštěného pracovního postupu, což může být užitečné. Při použití `HttpTrigger` ke spuštění pracovního postupu `CreateCheckStatusResponse` lze metodu použít `HttpResponseMessage`k vrácení instance. Tato odpověď poskytuje klientovi identifikátor URI v datové části, který lze použít ke kontrole stavu spuštěného procesu.

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

Následující výsledek ukázky ukazuje strukturu datové části odpovědi.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Pomocí preferovaného klienta HTTP se dá k identifikátoru URI v statusQueryGetUri provést požadavky GET pro kontrolu stavu spuštěného pracovního postupu. Vrácená odpověď stavu by měla vypadat podobně jako následující kód.

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

Jak proces pokračuje, změní se odpověď na stav buď na **neúspěšnou** , nebo na **dokončeno**. Po úspěšném dokončení bude vlastnost **Output** v datové části obsahovat všechna vrácená data.

## <a name="monitoring"></a>Monitorování

V případě jednoduchých opakujících se úloh Azure Functions `TimerTrigger` poskytuje, které mohou být naplánovány na základě výrazu cron. Časovač funguje dobře pro jednoduché krátkodobé úlohy, ale může se jednat o scénáře, kde je potřeba pružnější plánování. Tento scénář je, když vám může pomáhat model monitorování a Durable Functions.

Durable Functions umožňuje flexibilní plánovací intervaly, správu životnosti a vytváření více procesů monitorování z jedné funkce orchestrace. Jedním z případů použití této funkce může být vytvoření sledovacích procesů pro změny cen akcií, které se dokončí po splnění určité prahové hodnoty.

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

`DurableOrchestrationContext``CreateTimer` metoda nastavuje plán pro další vyvolání smyčky, aby kontroloval změny cen akcií. `DurableOrchestrationContext`má `CurrentUtcDateTime` také vlastnost pro získání aktuální hodnoty DateTime ve standardu UTC. Místo toho `DateTime.UtcNow` je vhodnější použít tuto vlastnost, protože je snadno napodobná pro testování.

## <a name="recommended-resources"></a>Doporučené prostředky

* [Durable Functions Azure](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Testování částí v .NET Core a .NET Standard](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Předchozí](durable-azure-functions.md)Další
>[](serverless-business-scenarios.md)
