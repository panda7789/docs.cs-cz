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
# <a name="durable-azure-functions"></a><span data-ttu-id="97dbe-103">Odolné funkce Azure</span><span class="sxs-lookup"><span data-stu-id="97dbe-103">Durable Azure functions</span></span>

<span data-ttu-id="97dbe-104">Při vytváření bezserverových aplikací pomocí funkce Azure budou vaše operace obvykle navrženy tak, aby fungovaly bezstavovým způsobem.</span><span class="sxs-lookup"><span data-stu-id="97dbe-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="97dbe-105">Důvodem pro tuto volbu návrhu je, protože jako platforma škáluje, je obtížné vědět, jaké servery kód běží na.</span><span class="sxs-lookup"><span data-stu-id="97dbe-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="97dbe-106">Je také obtížné zjistit, kolik instancí jsou aktivní v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="97dbe-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="97dbe-107">Existují však třídy aplikací, které vyžadují aktuální stav procesu, které mají být známy.</span><span class="sxs-lookup"><span data-stu-id="97dbe-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="97dbe-108">Zvažte proces odeslání objednávky do internetového obchodu.</span><span class="sxs-lookup"><span data-stu-id="97dbe-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="97dbe-109">Operace pokladny může být pracovní postup, který se skládá z více operací, které potřebují znát stav procesu.</span><span class="sxs-lookup"><span data-stu-id="97dbe-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="97dbe-110">Tyto informace mohou zahrnovat produktové zásoby, pokud má zákazník na svém účtu nějaké kredity, a také výsledky zpracování kreditní karty.</span><span class="sxs-lookup"><span data-stu-id="97dbe-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="97dbe-111">Tyto operace mohou být snadno jejich vlastní interní pracovní postupy nebo dokonce služby ze systémů třetích stran.</span><span class="sxs-lookup"><span data-stu-id="97dbe-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="97dbe-112">Dnes existují různé vzorce, které pomáhají s koordinací stavu aplikace mezi interními a externími systémy.</span><span class="sxs-lookup"><span data-stu-id="97dbe-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="97dbe-113">Je běžné narazit na řešení, která se spoléhají na centralizované systémy řazení do fronty, distribuovaná úložiště hodnot klíčů nebo sdílené databáze pro správu tohoto stavu.</span><span class="sxs-lookup"><span data-stu-id="97dbe-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="97dbe-114">To jsou však všechny další prostředky, které je nyní třeba zřídit a spravovat.</span><span class="sxs-lookup"><span data-stu-id="97dbe-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="97dbe-115">V prostředí bez serveru může být váš kód těžkopádný, když se pokoušíte koordinovat s těmito prostředky ručně.</span><span class="sxs-lookup"><span data-stu-id="97dbe-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="97dbe-116">Funkce Azure nabízí alternativu pro vytváření stavových funkcí s názvem Trvalé funkce.</span><span class="sxs-lookup"><span data-stu-id="97dbe-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="97dbe-117">Trvalé funkce je rozšíření runtime Azure Functions, který umožňuje definici stavových pracovních postupů v kódu.</span><span class="sxs-lookup"><span data-stu-id="97dbe-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="97dbe-118">Rozdělením pracovních postupů na aktivity může rozšíření Durable Functions spravovat stav, vytvářet kontrolní body průběhu a zpracovávat distribuci volání funkcí mezi servery.</span><span class="sxs-lookup"><span data-stu-id="97dbe-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="97dbe-119">Na pozadí využívá účet Azure Storage k zachování historie spuštění, plánování funkcí aktivity a načtení odpovědí.</span><span class="sxs-lookup"><span data-stu-id="97dbe-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="97dbe-120">Váš kód bez serveru by nikdy neměl pracovat s trvalými informacemi v tomto účtu úložiště a obvykle není něco, s čím vývojáři potřebují interakci.</span><span class="sxs-lookup"><span data-stu-id="97dbe-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="97dbe-121">Spuštění stavového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="97dbe-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="97dbe-122">Stavové pracovní postupy v trvanlivé funkce lze rozdělit na dvě vnitřní součásti; orchestrace a aktivační události aktivity.</span><span class="sxs-lookup"><span data-stu-id="97dbe-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="97dbe-123">Aktivační události a vazby jsou základní součásti používané funkce Azure k tomu, aby vaše funkce bez serveru byly upozorňovány, kdy mají být spouštěny, přijímány vstupy a vracejí výsledky.</span><span class="sxs-lookup"><span data-stu-id="97dbe-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="97dbe-124">Práce s klientem Orchestrace</span><span class="sxs-lookup"><span data-stu-id="97dbe-124">Working with the Orchestration client</span></span>

<span data-ttu-id="97dbe-125">Orchestrations jsou jedinečné ve srovnání s jinými styly aktivovaných operací v Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="97dbe-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="97dbe-126">Trvalé funkce umožňuje provádění funkcí, které může trvat hodiny nebo dokonce dny.</span><span class="sxs-lookup"><span data-stu-id="97dbe-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="97dbe-127">Tento typ chování přichází s potřebou zkontrolovat stav spuštěné orchestrace, preventivně ukončit nebo odeslat oznámení externích událostí.</span><span class="sxs-lookup"><span data-stu-id="97dbe-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="97dbe-128">Pro takové případy trvalé funkce `DurableOrchestrationClient` rozšíření poskytuje třídu, která umožňuje interakci s orchestrované funkce.</span><span class="sxs-lookup"><span data-stu-id="97dbe-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="97dbe-129">Získáte přístup ke klientovi orchestrace `OrchestrationClientAttribute` pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="97dbe-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="97dbe-130">Obecně byste tento atribut zahrnuli s jiným `HttpTrigger` `ServiceBusTrigger`typem aktivační události, například nebo .</span><span class="sxs-lookup"><span data-stu-id="97dbe-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="97dbe-131">Jakmile je aktivována zdrojová funkce, klient orchestrace lze spustit funkci orchestrator.</span><span class="sxs-lookup"><span data-stu-id="97dbe-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="97dbe-132">Funkce orchestrator</span><span class="sxs-lookup"><span data-stu-id="97dbe-132">The orchestrator function</span></span>

<span data-ttu-id="97dbe-133">Anotace funkce s OrchestrationTriggerAttribute v Azure Functions značky, které fungují jako funkce orchestrator.</span><span class="sxs-lookup"><span data-stu-id="97dbe-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="97dbe-134">Je zodpovědný za správu různých aktivit, které tvoří váš stavové pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="97dbe-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="97dbe-135">Funkce Orchestrator nelze použít vazby než OrchestrationTriggerAttribute.</span><span class="sxs-lookup"><span data-stu-id="97dbe-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="97dbe-136">Tento atribut lze použít pouze s typem parametru DurableOrchestrationContext.</span><span class="sxs-lookup"><span data-stu-id="97dbe-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="97dbe-137">Žádné jiné vstupy nelze použít, protože není podporována deserializace vstupů v podpisu funkce.</span><span class="sxs-lookup"><span data-stu-id="97dbe-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="97dbe-138">Chcete-li získat vstupy poskytované klientem orchestrace, getinput\<T\> metoda musí být použita.</span><span class="sxs-lookup"><span data-stu-id="97dbe-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="97dbe-139">Také návratové typy funkcí orchestrace musí být buď void, Task nebo JSON serializovatelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="97dbe-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="97dbe-140">*Kód zpracování chyb byl vynechán pro stručnost*</span><span class="sxs-lookup"><span data-stu-id="97dbe-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="97dbe-141">Více instancí orchestraci lze spustit a spustit současně.</span><span class="sxs-lookup"><span data-stu-id="97dbe-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="97dbe-142">Volání `StartNewAsync` metody na `DurableOrchestrationClient` spuštění nové instance orchestraci.</span><span class="sxs-lookup"><span data-stu-id="97dbe-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="97dbe-143">Metoda `Task<string>` vrátí, který dokončí po spuštění orchestrace.</span><span class="sxs-lookup"><span data-stu-id="97dbe-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="97dbe-144">Výjimka typu `TimeoutException` vyvolá, pokud orchestrace nebyla spuštěna do 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="97dbe-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="97dbe-145">Dokončeno `Task<string>` `StartNewAsync` z by měl obsahovat jedinečné ID instance orchestrace.</span><span class="sxs-lookup"><span data-stu-id="97dbe-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="97dbe-146">Toto ID instance lze vyvolat operace na konkrétní orchestraci.</span><span class="sxs-lookup"><span data-stu-id="97dbe-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="97dbe-147">Orchestrace může být dotazován na stav nebo odeslané oznámení událostí.</span><span class="sxs-lookup"><span data-stu-id="97dbe-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="97dbe-148">Funkce činnosti</span><span class="sxs-lookup"><span data-stu-id="97dbe-148">The activity functions</span></span>

<span data-ttu-id="97dbe-149">Funkce aktivity jsou samostatné operace, které se skládají společně v rámci funkce orchestrace k vytvoření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="97dbe-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="97dbe-150">Zde je místo, kde by se většina skutečné práce konala.</span><span class="sxs-lookup"><span data-stu-id="97dbe-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="97dbe-151">Představují obchodní logiku, dlouho běžící procesy a dílky skládačky k většímu řešení.</span><span class="sxs-lookup"><span data-stu-id="97dbe-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="97dbe-152">Používá `ActivityTriggerAttribute` se k anotace parametru `DurableActivityContext`funkce typu .</span><span class="sxs-lookup"><span data-stu-id="97dbe-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="97dbe-153">Pomocí poznámky informuje za běhu, že funkce je určena k použití jako funkce aktivity.</span><span class="sxs-lookup"><span data-stu-id="97dbe-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="97dbe-154">Vstupní hodnoty pro funkce aktivity `GetInput<T>` jsou `DurableActivityContext` načteny metodou parametru.</span><span class="sxs-lookup"><span data-stu-id="97dbe-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="97dbe-155">Podobně jako funkce orchestrace, návratové typy funkcí aktivity musí být buď void, Task nebo JSON serializovatelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="97dbe-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="97dbe-156">Všechny neošetřené výjimky, které se vrámci funkcí aktivity vyvolají, `TaskFailedException`budou odeslány do funkce volajícího orchestratoru a prezentovány jako .</span><span class="sxs-lookup"><span data-stu-id="97dbe-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="97dbe-157">V tomto okamžiku může být chyba zachycena a zaznamenána v orchestrátoru a aktivitu lze opakovat.</span><span class="sxs-lookup"><span data-stu-id="97dbe-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="97dbe-158">Doporučené zdroje</span><span class="sxs-lookup"><span data-stu-id="97dbe-158">Recommended resources</span></span>

- [<span data-ttu-id="97dbe-159">Odolná služba Functions</span><span class="sxs-lookup"><span data-stu-id="97dbe-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="97dbe-160">Vázání pro trvanlivé funkce</span><span class="sxs-lookup"><span data-stu-id="97dbe-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="97dbe-161">Správa instancí v trvalých funkcích</span><span class="sxs-lookup"><span data-stu-id="97dbe-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="97dbe-162">[Předchozí](event-grid.md)
>[další](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="97dbe-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
