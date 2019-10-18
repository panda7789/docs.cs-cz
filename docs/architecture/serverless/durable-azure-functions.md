---
title: Trvalé funkce Azure Functions – aplikace bez serveru
description: Trvalé funkce Azure rozšiřuje modul runtime Azure Functions, aby bylo možné v kódu Povolit stavové pracovní postupy.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522860"
---
# <a name="durable-azure-functions"></a>Odolné funkce Azure

Když vytváříte aplikace bez serveru s Azure Functions, vaše operace obvykle budou navržené tak, aby se spouštěly bezstavový způsob. Důvodem pro tento návrh je, že vzhledem k tomu, že se platforma škáluje, je obtížné zjistit, na kterých serverech je kód spuštěný. Také může být obtížné zjistit, kolik instancí je v jakémkoli okamžiku aktivní. Existují však třídy aplikací, které vyžadují, aby byl známý aktuální stav procesu. Vezměte v úvahu proces odeslání objednávky do online obchodu. Operace registrace může být pracovní postup, který se skládá z více operací, které potřebují znát stav procesu. Tyto informace mohou zahrnovat inventář produktů, pokud zákazník obsahuje kredity na účet a také výsledky zpracování platební karty. Tyto operace můžou snadno být vlastními interními pracovními postupy nebo i službami ze systémů třetích stran.

V dnešní době existují různé vzory, které pomáhají s koordinaci stavu aplikace mezi interními a externími systémy. Je běžné, že v řešeních, která se spoléhají na centralizované systémy front, úložiště pro distribuované hodnoty klíčů nebo sdílené databáze, je možné spravovat tento stav. Jsou to ale všechny další prostředky, které je teď potřeba zřídit a spravovat. V prostředí bez serveru může být váš kód náročný na to, aby se tyto prostředky koordinovaly ručně. Azure Functions nabízí alternativu pro vytváření stavových funkcí nazývaných Durable Functions.

Durable Functions je rozšíření modulu runtime Azure Functions, které umožňuje definici stavových pracovních postupů v kódu. Rozdělením pracovních postupů na aktivity může rozšíření Durable Functions spravovat stav, vytvářet kontrolní body průběhu a zpracovávat distribuci volání funkcí mezi servery. Na pozadí používá Azure Storage účet k uchování historie spouštění, plánování funkcí aktivity a načítání odpovědí. Váš kód bez serveru by nikdy neměl spolupracovat s uloženými informacemi v účtu úložiště a obvykle se nejedná o něco, se kterým vývojáři potřebují pracovat.

## <a name="triggering-a-stateful-workflow"></a>Aktivace stavového pracovního postupu

Stavové pracovní postupy v Durable Functions můžou být rozdělené na dvě vnitřní součásti. Orchestrace a triggery aktivit. Aktivační události a vazby jsou základními součástmi, které používá Azure Functions k tomu, aby byly funkce bez serveru upozorněny na zahájení, přijetí vstupu a vrácení výsledků.

### <a name="working-with-the-orchestration-client"></a>Práce s klientem Orchestration

Orchestrace jsou v porovnání s jinými styly aktivovaných operací v Azure Functions jedinečné. Durable Functions umožňuje spuštění funkcí, které mohou trvat hodiny nebo dokonce i dny. Tento typ chování je v případě potřeby schopný kontrolovat stav probíhající orchestrace, ukončit ukončení nebo odesílat oznámení o externích událostech.

V takových případech rozšíření Durable Functions poskytuje `DurableOrchestrationClient` třídu, která umožňuje interakci s orchestrací funkcí. Přístup k klientovi Orchestration získáte pomocí `OrchestrationClientAttribute` vazby. Obecně platí, že byste tento atribut zahrnuli do jiného typu triggeru, například `HttpTrigger` nebo `ServiceBusTrigger`. Po aktivaci zdrojové funkce lze pomocí klienta Orchestration spustit funkci nástroje Orchestrator.

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a>Funkce Orchestrator

Poznámka k funkci s OrchestrationTriggerAttribute ve Azure Functions označuje, že funguje jako funkce nástroje Orchestrator. Zodpovídá za správu různých aktivit, které tvoří stavový pracovní postup.

Funkce Orchestrator nemohou používat jiné vazby než OrchestrationTriggerAttribute. Tento atribut lze použít pouze s typem parametru DurableOrchestrationContext. Žádné jiné vstupy nelze použít, protože deserializace vstupů v signatuře funkce není podporována. Chcete-li získat vstupy poskytované klientem Orchestration, je nutné použít metodu GetInput \<T \>.

Návratové typy funkcí orchestrace musí být také typu void, Task nebo serializovatelného hodnoty JSON.

> *Kód pro zpracování chyb byl pro zkrácení vynechán.*

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

Můžete spustit a spustit více instancí orchestrace. Volání metody `StartNewAsync` v `DurableOrchestrationClient` spouští novou instanci orchestrace. Metoda vrátí `Task<string>`, který se dokončí při zahájení orchestrace. Výjimka typu `TimeoutException` vyvolána, pokud orchestrace nebyla zahájena během 30 sekund.

Dokončená `Task<string>` z `StartNewAsync` by měla obsahovat jedinečné ID instance Orchestration. Toto ID instance lze použít k vyvolání operací na konkrétní orchestraci. Orchestrace se dá dotazovat na stav nebo odeslaná oznámení o událostech.

### <a name="the-activity-functions"></a>Funkce aktivity

Funkce aktivity jsou diskrétní operace, které se skládají společně v rámci orchestrace k vytvoření pracovního postupu. Tady je místo, kde se bude provádět většina skutečných prací. Představují obchodní logiku, dlouho běžící procesy a skládanky na větší řešení.

@No__t_0 slouží k přidání poznámky k parametru funkce typu `DurableActivityContext`. Použití poznámky informuje modul runtime o tom, že funkce je určena pro použití jako funkce aktivity. Vstupní hodnoty funkcí aktivity jsou načteny pomocí metody `GetInput<T>` parametru `DurableActivityContext`.

Podobně jako funkce orchestrace, návratové typy funkcí aktivity musí být void, Task nebo serializovatelný hodnota JSON.

Všechny neošetřené výjimky, které jsou vyvolány v rámci funkcí aktivity, budou odeslány až do volání funkce Orchestrator a zobrazí se jako `TaskFailedException`. V tomto okamžiku může být chyba zachycena a zaznamenána v nástroji Orchestrator a aktivitu lze opakovat.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Doporučené prostředky

- [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Vazby pro Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Správa instancí v Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Předchozí](event-grid.md)
>[Další](orchestration-patterns.md)
