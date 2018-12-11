---
title: Trvalý Azure functions – aplikace bez serveru
description: Odolná služba Azure functions rozšíření modulu runtime Azure Functions umožňuje stavové pracovních postupů v kódu.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8ad354e1708eb88f016130f8235f534b967eb122
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147304"
---
# <a name="durable-azure-functions"></a>Odolná služba Azure functions

Při vytváření aplikace bez serveru s využitím Azure Functions, vaše operace obvykle navrženy ke spuštění v podobě bezstavové. I důvod vybraného návrhu tohoto je, protože jako platformu měřítka, bude obtížné vědět, jaké servery je kód spuštěn na. Také bude obtížné zjistit, kolik instancí jsou aktivní v libovolném časovém okamžiku. Existují však třídy aplikace, které vyžadují aktuální stav procesu být známý. Berte v úvahu proces odeslání objednávky na online obchod. Operace rezervace může být pracovní postup, který se skládá z více operací, které potřebujete znát stav procesu. Tyto informace mohou zahrnovat inventář produktů, pokud má zákazník jakékoli kredity na svůj účet a také výsledky zpracování platební karty. Tyto operace může být snadno vlastní interní pracovní postupy nebo dokonce services ze systémů jiných výrobců.

Různé způsoby existovat ještě dnes této pomoc s koordinace stav aplikace mezi interními a externími systémy. Je běžné řešení, které spoléhají na centralizované systémy zařazování do fronty, distribuované dvojicí klíč hodnota nebo sdílené databáze ke správě stavu setkali. Ty jsou však všechny další prostředky, které je teď potřeba zřizovat a spravovat. V prostředí bez serveru váš kód může poněkud těžkopádné zkusit součinnost s těmito prostředky ručně. Služba Azure Functions nabízí alternativu pro vytvoření stavové funkce volané Durable Functions.

Odolná služba Functions je rozšíření modulu runtime Azure Functions, která umožňuje definice stavové pracovních postupů v kódu. Rozdělením pracovních postupů do aktivit rozšíření Durable Functions spravovat stav, vytváření kontrolních bodů průběhu a zpracování distribuce volání funkcí mezi servery. Na pozadí díky použití účtu služby Azure Storage k zachování historie spuštění, naplánujte funkce aktivity a načíst odpovědi. Váš kód bez serveru by nikdy interakci s trvalou informace v tomto účtu úložiště a není obvykle něco, které vývojáři potřebují pracovat.

## <a name="triggering-a-stateful-workflow"></a>Aktivuje se stavové pracovního postupu

Stavové pracovních postupů v odolná služba Functions je možné rozdělit do dvou vnitřní součásti; Orchestrace a aktivita aktivační události. Triggery a vazby tvoří klíčové součásti, které používá služba Azure Functions k povolení vaše funkce bez serveru, která vás upozorní, když chcete začít, zobrazí vstupní a vrácení výsledků.

### <a name="working-with-the-orchestration-client"></a>Práce s klientskou Orchestrace

Orchestrace jsou jedinečné ve srovnání s jinými styly aktivovaných operací ve službě Azure Functions. Odolná služba Functions umožňuje spuštění funkce, které může trvat hodiny nebo dokonce dní na provedení. Tento typ chování se dodává spolu s potřebou možnost zkontrolovat stav běžící Orchestrace, preventivně ukončit nebo odesílat upozornění na vnější události.

Pro tyto případy rozšíření Durable Functions poskytuje `DurableOrchestrationClient` třídu, která umožňuje pracovat s orchestrované funkce. Získat přístup ke klientovi Orchestrace pomocí `OrchestrationClientAttribute` vazby. Obecně platí, zahrňte tento atribut s jiným typem aktivační událost, například `HttpTrigger` nebo `ServiceBusTrigger`. Jakmile došlo ke spuštění funkce zdroje, klient Orchestrace lze použít ke spuštění funkce orchestrátoru.

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

### <a name="the-orchestrator-function"></a>Funkce orchestrátoru

Zadávání poznámek do funkce s OrchestrationTriggerAttribute v Azure Functions značky, že fungují jako funkce orchestrátoru. Zodpovídá za správu různých činností, které tvoří stavové pracovního postupu.

Funkce nástroje Orchestrator nelze provést pomocí vazeb než OrchestrationTriggerAttribute. Tento atribut lze použít pouze s parametrem typu DurableOrchestrationContext. Žádné další vstupy. můžete použít, protože deserializace vstupů v signatuře funkce není podporována. Chcete-li získat klient Orchestrace, GetInput zadané vstupy\<T\> musí použít metoda.

Návratové typy funkcí Orchestrace musí být buď prázdná hodnota, úkolu nebo serializable hodnoty JSON.

> *Kód pro zpracování chyb byla ponechána navýšení kapacity pro zkrácení*

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

Více instancí Orchestrace může být spuštěn a spuštěné ve stejnou dobu. Volání `StartNewAsync` metodu `DurableOrchestrationClient` spustí novou instanci třídy orchestraci. Metoda vrátí `Task<string>` , která se dokončí po spuštění orchestraci. Výjimka typu `TimeoutException` získá vyvolána, pokud nebyl spuštěn orchestraci během 30 sekund.

Dokončené `Task<string>` z `StartNewAsync` by měl obsahovat jedinečný ID instance Orchestrace. Toto ID instance můžete použít k vyvolání operace v této konkrétní Orchestrace. Orchestraci můžete dotazovat na stav nebo odeslání oznámení události.

### <a name="the-activity-functions"></a>Funkce aktivity

Aktivita funkce jsou samostatné operace, které získáte složené společně v rámci Orchestrace funkce k vytvoření pracovního postupu. Zde je, kde by proběhnout většinu samotnou práci. Které představují obchodní logiku, dlouhé spuštěné procesy a částí díl stavebnice větší řešení.

`ActivityTriggerAttribute` Používaná k anotaci funkce parametr typu `DurableActivityContext`. Použití anotace informuje o modulu runtime, že funkce je určena pro použití jako funkce aktivity. Vstupní hodnoty do funkce aktivity se načítají pomocí `GetInput<T>` metodu `DurableActivityContext` parametru.

Podobně jako funkce Orchestrace návratové typy funkce aktivity musí být void, úkolu nebo serializable hodnoty JSON.

Všechny neošetřené výjimky, které získáte vyvolána v rámci funkce aktivity získat odesílat volání funkce orchestrátoru, který se zobrazí jako `TaskFailedException`. V tomto okamžiku chyby můžete zachytit a přihlášení orchestrátor a aktivity, které umožňují opakovaný pokus.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Doporučené studijní materiály

* [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Vazby pro Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Správa instancí v Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Předchozí](event-grid.md)
>[další](orchestration-patterns.md)