---
title: Orchestrace vzorky – aplikace bez serveru
description: Žádost o přijetí změn Azure Durable functions
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: b3f0587241a940941f40512504f7838ef94e3150
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404891"
---
# <a name="orchestration-patterns"></a>Vzory Orchestrace

Odolná služba Functions usnadňuje vytváření stavové pracovních postupů, které se skládají z aktivit diskrétní, dlouho běžící v prostředí bez serveru. Protože Durable Functions průběh můžete sledovat vaše pracovní postupy a pravidelně kontrolní body historie spuštění, ho slouží k provádění některých zajímavých vzorců.

## <a name="function-chaining"></a>Funkce řetězení

Aktivity v typické sekvenční procesu, potřebují spustit jeden za druhým v určitém pořadí. Volitelně můžete nadcházející aktivita může vyžadovat některé výstup z předchozí funkce. Tato závislost na pořadí aktivit vznikne řetěz funkce spuštění.

Výhodou použití Durable Functions k implementaci tohoto modelu pracovního postupu pochází z jeho možnost vytváření kontrolních bodů. Pokud dojde k chybě na serveru, sítě vyprší časový limit nebo dojde k některý problém, Durable functions můžete obnovit z posledního známého stavu a pokračování ve spouštění pracovního postupu, i v případě, že je na jiný server.

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

V předchozí ukázce kódu `CallActivityAsync` funkce je zodpovědný za spouštění danou aktivitu na virtuálním počítači v datovém centru. Po dokončení vrátí await a základní úkol, provádění se zaznamená do tabulky historie. Kód ve funkci orchestrator můžete vytvořit pomocí některého z známé konstrukce Task Parallel Library a klíčová slova async/await.

Následující kód je zjednodušený příklad postupu `ProcessPayment` metoda může vypadat takto:

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

## <a name="asynchronous-http-apis"></a>Asynchronní rozhraní API protokolu HTTP

V některých případech může obsahovat pracovní postupy aktivity, které trvat poměrně dlouhou dobu čas dokončení. Představte si je proces, který zahajuje zálohování média soubory do úložiště objektů blob. V závislosti na velikosti a množství mediálních souborů tento záložní proces může trvat hodiny.

V tomto scénáři `DurableOrchestrationClient`na kontrolu stavu s běžícím workflowem bloků se stává užitečným. Při použití `HttpTrigger` se spustit pracovní postup `CreateCheckStatusResponse` metodu je možné vrátit instanci `HttpResponseMessage`. Tato odpověď poskytuje klienta s identifikátorem URI v datové části je možné zkontrolovat stav běžící proces.

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

Následující ukázka výsledku znázorňuje strukturu datové části odpovědi.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

Pomocí upřednostňovaných klienta protokolu HTTP, požadavky GET lze provádět na identifikátor URI v statusQueryGetUri kontrolovat stav spuštění pracovního postupu. Odpověď vrácená stavu by měla vypadat následovně.

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

Jak proces pokračuje, odpověď na stav se změní na buď **neúspěšné** nebo **dokončeno**. Při úspěšném dokončení **výstup** vlastnost v datové části bude obsahovat všechny vrácená data.

## <a name="monitoring"></a>Monitorování

Pro jednoduché opakované úlohy, služba Azure Functions umožňuje `TimerTrigger` , který můžete naplánovat na základě výrazu CRON. Časovač se dá použít i pro jednoduché, krátkodobé a jednorázové úlohy, mohou se však vyskytnout scénáře, které vyžadují více flexibilní plánování. Tento scénář je při monitorování vzor a odolná služba Functions může pomoct.

Odolná služba Functions umožňuje flexibilní plánování intervalech a správa životního cyklu a také vytváří více procesů monitorování z jednoho Orchestrace funkce. Jeden případ použití pro tuto funkci může být vytvoření sledovací procesy pro minimální cenu akcie změny, které po splnění určitou prahovou hodnotu.

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

`DurableOrchestrationContext`společnosti `CreateTimer` metoda nastaví plán, další vyvolání příkazu smyčky, která zkontroluje změny minimální cenu akcie. `DurableOrchestrationContext` má také `CurrentUtcDateTime` vlastnost k získání aktuální hodnoty datum a čas ve standardu UTC. Je vhodnější použít tuto vlastnost místo `DateTime.UtcNow` vzhledem k tomu, že je snadno imitace pro testování.

## <a name="recommended-resources"></a>Doporučené studijní materiály

* [Odolná služba Azure Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Testování jednotek v .NET Core a .NET Standard](https://docs.microsoft.com/en-us/dotnet/core/testing/)

>[!div class="step-by-step"]
[Předchozí](durable-azure-functions.md)
[další](serverless-business-scenarios.md)
