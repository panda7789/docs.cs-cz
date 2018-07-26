---
title: Trvalý Azure functions – aplikace bez serveru
description: Odolná služba Azure functions rozšíření modulu runtime Azure Functions umožňuje stavové pracovních postupů v kódu.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 03197ad57813b8132fe592f4e555c6a35edbd9bd
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404900"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="59424-103">Odolná služba Azure functions</span><span class="sxs-lookup"><span data-stu-id="59424-103">Durable Azure functions</span></span>

<span data-ttu-id="59424-104">Při vytváření aplikace bez serveru s využitím Azure Functions, vaše operace obvykle navrženy ke spuštění v podobě bezstavové.</span><span class="sxs-lookup"><span data-stu-id="59424-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="59424-105">I důvod vybraného návrhu tohoto je, protože jako platformu měřítka, bude obtížné vědět, jaké servery je kód spuštěn na.</span><span class="sxs-lookup"><span data-stu-id="59424-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="59424-106">Také bude obtížné zjistit, kolik instancí jsou aktivní v libovolném časovém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="59424-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="59424-107">Existují však třídy aplikace, které vyžadují aktuální stav procesu být známý.</span><span class="sxs-lookup"><span data-stu-id="59424-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="59424-108">Berte v úvahu proces odeslání objednávky na online obchod.</span><span class="sxs-lookup"><span data-stu-id="59424-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="59424-109">Operace rezervace může být pracovní postup, který se skládá z více operací, které potřebujete znát stav procesu.</span><span class="sxs-lookup"><span data-stu-id="59424-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="59424-110">Tyto informace mohou zahrnovat inventář produktů, pokud má zákazník jakékoli kredity na svůj účet a také výsledky zpracování platební karty.</span><span class="sxs-lookup"><span data-stu-id="59424-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="59424-111">Tyto operace může být snadno vlastní interní pracovní postupy nebo dokonce services ze systémů jiných výrobců.</span><span class="sxs-lookup"><span data-stu-id="59424-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="59424-112">Různé způsoby existovat ještě dnes této pomoc s koordinace stav aplikace mezi interními a externími systémy.</span><span class="sxs-lookup"><span data-stu-id="59424-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="59424-113">Je běžné řešení, které spoléhají na centralizované systémy zařazování do fronty, distribuované dvojicí klíč hodnota nebo sdílené databáze ke správě stavu setkali.</span><span class="sxs-lookup"><span data-stu-id="59424-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="59424-114">Ty jsou však všechny další prostředky, které je teď potřeba zřizovat a spravovat.</span><span class="sxs-lookup"><span data-stu-id="59424-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="59424-115">V prostředí bez serveru váš kód může poněkud těžkopádné zkusit součinnost s těmito prostředky ručně.</span><span class="sxs-lookup"><span data-stu-id="59424-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="59424-116">Služba Azure Functions nabízí alternativu pro vytvoření stavové funkce volané Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="59424-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="59424-117">Odolná služba Functions je rozšíření modulu runtime Azure Functions, která umožňuje definice stavové pracovních postupů v kódu.</span><span class="sxs-lookup"><span data-stu-id="59424-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="59424-118">Rozdělením pracovních postupů do aktivit rozšíření Durable Functions spravovat stav, vytváření kontrolních bodů průběhu a zpracování distribuce volání funkcí mezi servery.</span><span class="sxs-lookup"><span data-stu-id="59424-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="59424-119">Na pozadí díky použití účtu služby Azure Storage k zachování historie spuštění, naplánujte funkce aktivity a načíst odpovědi.</span><span class="sxs-lookup"><span data-stu-id="59424-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="59424-120">Váš kód bez serveru by nikdy interakci s trvalou informace v tomto účtu úložiště a není obvykle něco, které vývojáři potřebují pracovat.</span><span class="sxs-lookup"><span data-stu-id="59424-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="59424-121">Aktivuje se stavové pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="59424-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="59424-122">Stavové pracovních postupů v odolná služba Functions je možné rozdělit do dvou vnitřní součásti; Orchestrace a aktivita aktivační události.</span><span class="sxs-lookup"><span data-stu-id="59424-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="59424-123">Triggery a vazby tvoří klíčové součásti, které používá služba Azure Functions k povolení vaše funkce bez serveru, která vás upozorní, když chcete začít, zobrazí vstupní a vrácení výsledků.</span><span class="sxs-lookup"><span data-stu-id="59424-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="59424-124">Práce s klientskou Orchestrace</span><span class="sxs-lookup"><span data-stu-id="59424-124">Working with the Orchestration client</span></span>

<span data-ttu-id="59424-125">Orchestrace jsou jedinečné ve srovnání s jinými styly aktivovaných operací ve službě Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="59424-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="59424-126">Odolná služba Functions umožňuje spuštění funkce, které může trvat hodiny nebo dokonce dní na provedení.</span><span class="sxs-lookup"><span data-stu-id="59424-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="59424-127">Tento typ chování se dodává spolu s potřebou možnost zkontrolovat stav běžící Orchestrace, preventivně ukončit nebo odesílat upozornění na vnější události.</span><span class="sxs-lookup"><span data-stu-id="59424-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="59424-128">Pro tyto případy rozšíření Durable Functions poskytuje `DurableOrchestrationClient` třídu, která umožňuje pracovat s orchestrované funkce.</span><span class="sxs-lookup"><span data-stu-id="59424-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="59424-129">Získat přístup ke klientovi Orchestrace pomocí `OrchestrationClientAttribute` vazby.</span><span class="sxs-lookup"><span data-stu-id="59424-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="59424-130">Obecně platí, zahrňte tento atribut s jiným typem aktivační událost, například `HttpTrigger` nebo `ServiceBusTrigger`.</span><span class="sxs-lookup"><span data-stu-id="59424-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="59424-131">Jakmile došlo ke spuštění funkce zdroje, klient Orchestrace lze použít ke spuštění funkce orchestrátoru.</span><span class="sxs-lookup"><span data-stu-id="59424-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="59424-132">Funkce orchestrátoru</span><span class="sxs-lookup"><span data-stu-id="59424-132">The orchestrator function</span></span>

<span data-ttu-id="59424-133">Zadávání poznámek do funkce s OrchestrationTriggerAttribute v Azure Functions značky, že fungují jako funkce orchestrátoru.</span><span class="sxs-lookup"><span data-stu-id="59424-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="59424-134">Zodpovídá za správu různých činností, které tvoří stavové pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="59424-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="59424-135">Funkce nástroje Orchestrator nelze provést pomocí vazeb než OrchestrationTriggerAttribute.</span><span class="sxs-lookup"><span data-stu-id="59424-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="59424-136">Tento atribut lze použít pouze s parametrem typu DurableOrchestrationContext.</span><span class="sxs-lookup"><span data-stu-id="59424-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="59424-137">Žádné další vstupy. můžete použít, protože deserializace vstupů v signatuře funkce není podporována.</span><span class="sxs-lookup"><span data-stu-id="59424-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="59424-138">Chcete-li získat klient Orchestrace, GetInput zadané vstupy\<T\> musí použít metoda.</span><span class="sxs-lookup"><span data-stu-id="59424-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="59424-139">Návratové typy funkcí Orchestrace musí být buď prázdná hodnota, úkolu nebo serializable hodnoty JSON.</span><span class="sxs-lookup"><span data-stu-id="59424-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="59424-140">*Kód pro zpracování chyb byla ponechána navýšení kapacity pro zkrácení*</span><span class="sxs-lookup"><span data-stu-id="59424-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="59424-141">Více instancí Orchestrace může být spuštěn a spuštěné ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="59424-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="59424-142">Volání `StartNewAsync` metodu `DurableOrchestrationClient` spustí novou instanci třídy orchestraci.</span><span class="sxs-lookup"><span data-stu-id="59424-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="59424-143">Metoda vrátí `Task<string>` , která se dokončí po spuštění orchestraci.</span><span class="sxs-lookup"><span data-stu-id="59424-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="59424-144">Výjimka typu `TimeoutException` získá vyvolána, pokud nebyl spuštěn orchestraci během 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="59424-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="59424-145">Dokončené `Task<string>` z `StartNewAsync` by měl obsahovat jedinečný ID instance Orchestrace.</span><span class="sxs-lookup"><span data-stu-id="59424-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="59424-146">Toto ID instance můžete použít k vyvolání operace v této konkrétní Orchestrace.</span><span class="sxs-lookup"><span data-stu-id="59424-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="59424-147">Orchestraci můžete dotazovat na stav nebo odeslání oznámení události.</span><span class="sxs-lookup"><span data-stu-id="59424-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="59424-148">Funkce aktivity</span><span class="sxs-lookup"><span data-stu-id="59424-148">The activity functions</span></span>

<span data-ttu-id="59424-149">Aktivita funkce jsou samostatné operace, které získáte složené společně v rámci Orchestrace funkce k vytvoření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="59424-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="59424-150">Zde je, kde by proběhnout většinu samotnou práci.</span><span class="sxs-lookup"><span data-stu-id="59424-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="59424-151">Které představují obchodní logiku, dlouhé spuštěné procesy a částí díl stavebnice větší řešení.</span><span class="sxs-lookup"><span data-stu-id="59424-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="59424-152">`ActivityTriggerAttribute` Používaná k anotaci funkce parametr typu `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="59424-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="59424-153">Použití anotace informuje o modulu runtime, že funkce je určena pro použití jako funkce aktivity.</span><span class="sxs-lookup"><span data-stu-id="59424-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="59424-154">Vstupní hodnoty do funkce aktivity se načítají pomocí `GetInput<T>` metodu `DurableActivityContext` parametru.</span><span class="sxs-lookup"><span data-stu-id="59424-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="59424-155">Podobně jako funkce Orchestrace návratové typy funkce aktivity musí být void, úkolu nebo serializable hodnoty JSON.</span><span class="sxs-lookup"><span data-stu-id="59424-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="59424-156">Všechny neošetřené výjimky, které získáte vyvolána v rámci funkce aktivity získat odesílat volání funkce orchestrátoru, který se zobrazí jako `TaskFailedException`.</span><span class="sxs-lookup"><span data-stu-id="59424-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="59424-157">V tomto okamžiku chyby můžete zachytit a přihlášení orchestrátor a aktivity, které umožňují opakovaný pokus.</span><span class="sxs-lookup"><span data-stu-id="59424-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="59424-158">Doporučené studijní materiály</span><span class="sxs-lookup"><span data-stu-id="59424-158">Recommended resources</span></span>

* [<span data-ttu-id="59424-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="59424-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="59424-160">Vazby pro Durable Functions</span><span class="sxs-lookup"><span data-stu-id="59424-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [<span data-ttu-id="59424-161">Správa instancí v Durable Functions</span><span class="sxs-lookup"><span data-stu-id="59424-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
<span data-ttu-id="59424-162">[Předchozí](event-grid.md)
[další](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="59424-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>