---
title: Trvalé funkce Azure – aplikace bez serveru
description: Trvalé funkce Azure rozšiřují runtime Azure Functions tak, aby umožňovala stavové pracovní postupy v kódu.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522860"
---
# <a name="durable-azure-functions"></a>Odolné funkce Azure

Při vytváření bezserverových aplikací pomocí funkce Azure budou vaše operace obvykle navrženy tak, aby fungovaly bezstavovým způsobem. Důvodem pro tuto volbu návrhu je, protože jako platforma škáluje, je obtížné vědět, jaké servery kód běží na. Je také obtížné zjistit, kolik instancí jsou aktivní v daném okamžiku. Existují však třídy aplikací, které vyžadují aktuální stav procesu, které mají být známy. Zvažte proces odeslání objednávky do internetového obchodu. Operace pokladny může být pracovní postup, který se skládá z více operací, které potřebují znát stav procesu. Tyto informace mohou zahrnovat produktové zásoby, pokud má zákazník na svém účtu nějaké kredity, a také výsledky zpracování kreditní karty. Tyto operace mohou být snadno jejich vlastní interní pracovní postupy nebo dokonce služby ze systémů třetích stran.

Dnes existují různé vzorce, které pomáhají s koordinací stavu aplikace mezi interními a externími systémy. Je běžné narazit na řešení, která se spoléhají na centralizované systémy řazení do fronty, distribuovaná úložiště hodnot klíčů nebo sdílené databáze pro správu tohoto stavu. To jsou však všechny další prostředky, které je nyní třeba zřídit a spravovat. V prostředí bez serveru může být váš kód těžkopádný, když se pokoušíte koordinovat s těmito prostředky ručně. Funkce Azure nabízí alternativu pro vytváření stavových funkcí s názvem Trvalé funkce.

Trvalé funkce je rozšíření runtime Azure Functions, který umožňuje definici stavových pracovních postupů v kódu. Rozdělením pracovních postupů na aktivity může rozšíření Durable Functions spravovat stav, vytvářet kontrolní body průběhu a zpracovávat distribuci volání funkcí mezi servery. Na pozadí využívá účet Azure Storage k zachování historie spuštění, plánování funkcí aktivity a načtení odpovědí. Váš kód bez serveru by nikdy neměl pracovat s trvalými informacemi v tomto účtu úložiště a obvykle není něco, s čím vývojáři potřebují interakci.

## <a name="triggering-a-stateful-workflow"></a>Spuštění stavového pracovního postupu

Stavové pracovní postupy v trvanlivé funkce lze rozdělit na dvě vnitřní součásti; orchestrace a aktivační události aktivity. Aktivační události a vazby jsou základní součásti používané funkce Azure k tomu, aby vaše funkce bez serveru byly upozorňovány, kdy mají být spouštěny, přijímány vstupy a vracejí výsledky.

### <a name="working-with-the-orchestration-client"></a>Práce s klientem Orchestrace

Orchestrations jsou jedinečné ve srovnání s jinými styly aktivovaných operací v Azure Functions. Trvalé funkce umožňuje provádění funkcí, které může trvat hodiny nebo dokonce dny. Tento typ chování přichází s potřebou zkontrolovat stav spuštěné orchestrace, preventivně ukončit nebo odeslat oznámení externích událostí.

Pro takové případy trvalé funkce `DurableOrchestrationClient` rozšíření poskytuje třídu, která umožňuje interakci s orchestrované funkce. Získáte přístup ke klientovi orchestrace `OrchestrationClientAttribute` pomocí vazby. Obecně byste tento atribut zahrnuli s jiným `HttpTrigger` `ServiceBusTrigger`typem aktivační události, například nebo . Jakmile je aktivována zdrojová funkce, klient orchestrace lze spustit funkci orchestrator.

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

### <a name="the-orchestrator-function"></a>Funkce orchestrator

Anotace funkce s OrchestrationTriggerAttribute v Azure Functions značky, které fungují jako funkce orchestrator. Je zodpovědný za správu různých aktivit, které tvoří váš stavové pracovní postup.

Funkce Orchestrator nelze použít vazby než OrchestrationTriggerAttribute. Tento atribut lze použít pouze s typem parametru DurableOrchestrationContext. Žádné jiné vstupy nelze použít, protože není podporována deserializace vstupů v podpisu funkce. Chcete-li získat vstupy poskytované klientem orchestrace, getinput\<T\> metoda musí být použita.

Také návratové typy funkcí orchestrace musí být buď void, Task nebo JSON serializovatelné hodnoty.

> *Kód zpracování chyb byl vynechán pro stručnost*

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

Více instancí orchestraci lze spustit a spustit současně. Volání `StartNewAsync` metody na `DurableOrchestrationClient` spuštění nové instance orchestraci. Metoda `Task<string>` vrátí, který dokončí po spuštění orchestrace. Výjimka typu `TimeoutException` vyvolá, pokud orchestrace nebyla spuštěna do 30 sekund.

Dokončeno `Task<string>` `StartNewAsync` z by měl obsahovat jedinečné ID instance orchestrace. Toto ID instance lze vyvolat operace na konkrétní orchestraci. Orchestrace může být dotazován na stav nebo odeslané oznámení událostí.

### <a name="the-activity-functions"></a>Funkce činnosti

Funkce aktivity jsou samostatné operace, které se skládají společně v rámci funkce orchestrace k vytvoření pracovního postupu. Zde je místo, kde by se většina skutečné práce konala. Představují obchodní logiku, dlouho běžící procesy a dílky skládačky k většímu řešení.

Používá `ActivityTriggerAttribute` se k anotace parametru `DurableActivityContext`funkce typu . Pomocí poznámky informuje za běhu, že funkce je určena k použití jako funkce aktivity. Vstupní hodnoty pro funkce aktivity `GetInput<T>` jsou `DurableActivityContext` načteny metodou parametru.

Podobně jako funkce orchestrace, návratové typy funkcí aktivity musí být buď void, Task nebo JSON serializovatelné hodnoty.

Všechny neošetřené výjimky, které se vrámci funkcí aktivity vyvolají, `TaskFailedException`budou odeslány do funkce volajícího orchestratoru a prezentovány jako . V tomto okamžiku může být chyba zachycena a zaznamenána v orchestrátoru a aktivitu lze opakovat.

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>Doporučené zdroje

- [Odolná služba Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [Vázání pro trvanlivé funkce](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [Správa instancí v trvalých funkcích](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[Předchozí](event-grid.md)
>[další](orchestration-patterns.md)
