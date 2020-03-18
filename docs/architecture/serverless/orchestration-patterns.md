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
# <a name="orchestration-patterns"></a>Vzory orchestrace

Trvalé funkce usnadňuje vytváření stavových pracovních postupů, které se skládají z diskrétních, dlouhotrvajících aktivit v prostředí bez serveru. Vzhledem k tomu, že trvalé funkce můžete sledovat průběh pracovních postupů a pravidelně kontrolní body historie provádění, půjčuje se k implementaci některé zajímavé vzory.

## <a name="function-chaining"></a>Řetězení funkcí

V typickém sekvenčním procesu je třeba aktivity provádět jeden po druhém v určitém pořadí. Volitelně nadcházející aktivita může vyžadovat určitý výstup z předchozí funkce. Tato závislost na řazení aktivit vytvoří řetězec funkcí provádění.

Výhodou použití trvalé funkce k implementaci tohoto vzoru pracovního postupu pochází z jeho schopnost provádět vytváření kontrolních bodů. Pokud dojde k chybě serveru, časový mat v síti nebo dojde k jinému problému, trvalé funkce mohou pokračovat z posledního známého stavu a pokračovat ve spuštění pracovního postupu, i když je na jiném serveru.

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

V předchozí ukázce `CallActivityAsync` kódu je funkce zodpovědná za spuštění dané aktivity na virtuálním počítači v datovém centru. Když await vrátí a základní Task dokončí, spuštění se zaznamená do tabulky historie. Kód ve funkci orchestrator můžete využít některé známé konstrukce task paralelní knihovny a async/await klíčová slova.

Následující kód je zjednodušeným příkladem `ProcessPayment` toho, jak může metoda vypadat:

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

## <a name="asynchronous-http-apis"></a>Asynchronní http api

V některých případech mohou pracovní postupy obsahovat aktivity, které jejich dokončení trvá poměrně dlouhou dobu. Představte si proces, který spustí zálohování mediálních souborů do úložiště objektů blob. V závislosti na velikosti a množství mediálních souborů může dokončení tohoto procesu zálohování trvat hodiny.

V tomto scénáři `DurableOrchestrationClient`'s schopnost zkontrolovat stav spuštěného pracovního postupu se stane užitečné. Při použití `HttpTrigger` a ke spuštění `CreateCheckStatusResponse` pracovního postupu lze metodu použít k vrácení instance aplikace `HttpResponseMessage`. Tato odpověď poskytuje klientovi identifikátor URI v datové části, který lze použít ke kontrole stavu spuštěného procesu.

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

Ukázkový výsledek níže ukazuje strukturu datové části odpovědi.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Pomocí upřednostňovaného klienta HTTP mohou být požadavky GET provedeny na identifikátor URI ve statusQueryGetUri ke kontrole stavu spuštěného pracovního postupu. Vrácená odpověď na stav by se měla podobat následujícímu kódu.

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

Jak proces pokračuje, odpověď na stav se změní na **Neúspěšná** nebo **Dokončená**. Po úspěšném dokončení **bude výstupní** vlastnost v datové části obsahovat všechna vrácená data.

## <a name="monitoring"></a>Monitorování

Pro jednoduché opakované úkoly `TimerTrigger` Azure Functions poskytuje, které lze naplánovat na základě výrazu CRON. Časovač funguje dobře pro jednoduché, krátkodobé úkoly, ale mohou existovat scénáře, kde je potřeba flexibilnější plánování. Tento scénář je, když může pomoci vzor monitorování a trvalé funkce.

Trvalé funkce umožňuje flexibilní intervaly plánování, správu životnosti a vytváření více procesů monitorování z jediné funkce orchestrace. Jeden případ použití pro tuto funkci může být vytvoření sledovacích modulů pro změny cen akcií, které dokončí po splnění určité prahové hodnoty.

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

`DurableOrchestrationContext`Metoda `CreateTimer` programu nastaví plán pro další vyvolání smyčky a zkontroluje se změna ceny akcií. `DurableOrchestrationContext`má také `CurrentUtcDateTime` vlastnost získat aktuální DateTime hodnotu v UTC. Je lepší použít tuto vlastnost `DateTime.UtcNow` namísto toho, protože je to snadno zesměšňován pro testování.

## <a name="recommended-resources"></a>Doporučené zdroje

- [Azure Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Testování částí ve standardu .NET Core a .NET](../../core/testing/index.md)

>[!div class="step-by-step"]
>[Předchozí](durable-azure-functions.md)
>[další](serverless-business-scenarios.md)
