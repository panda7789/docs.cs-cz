---
title: Trvalé funkce Azure Functions – aplikace bez serveru
description: Trvalé funkce Azure rozšiřuje modul runtime Azure Functions, aby bylo možné v kódu Povolit stavové pracovní postupy.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522860"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="f1b8c-103">Odolné funkce Azure</span><span class="sxs-lookup"><span data-stu-id="f1b8c-103">Durable Azure functions</span></span>

<span data-ttu-id="f1b8c-104">Když vytváříte aplikace bez serveru s Azure Functions, vaše operace obvykle budou navržené tak, aby se spouštěly bezstavový způsob.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="f1b8c-105">Důvodem pro tento návrh je, že vzhledem k tomu, že se platforma škáluje, je obtížné zjistit, na kterých serverech je kód spuštěný.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="f1b8c-106">Také může být obtížné zjistit, kolik instancí je v jakémkoli okamžiku aktivní.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="f1b8c-107">Existují však třídy aplikací, které vyžadují, aby byl známý aktuální stav procesu.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="f1b8c-108">Vezměte v úvahu proces odeslání objednávky do online obchodu.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="f1b8c-109">Operace registrace může být pracovní postup, který se skládá z více operací, které potřebují znát stav procesu.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="f1b8c-110">Tyto informace mohou zahrnovat inventář produktů, pokud zákazník obsahuje kredity na účet a také výsledky zpracování platební karty.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="f1b8c-111">Tyto operace můžou snadno být vlastními interními pracovními postupy nebo i službami ze systémů třetích stran.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="f1b8c-112">V dnešní době existují různé vzory, které pomáhají s koordinaci stavu aplikace mezi interními a externími systémy.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="f1b8c-113">Je běžné, že v řešeních, která se spoléhají na centralizované systémy front, úložiště pro distribuované hodnoty klíčů nebo sdílené databáze, je možné spravovat tento stav.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="f1b8c-114">Jsou to ale všechny další prostředky, které je teď potřeba zřídit a spravovat.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="f1b8c-115">V prostředí bez serveru může být váš kód náročný na to, aby se tyto prostředky koordinovaly ručně.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="f1b8c-116">Azure Functions nabízí alternativu pro vytváření stavových funkcí nazývaných Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="f1b8c-117">Durable Functions je rozšíření modulu runtime Azure Functions, které umožňuje definici stavových pracovních postupů v kódu.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="f1b8c-118">Rozdělením pracovních postupů na aktivity může rozšíření Durable Functions spravovat stav, vytvářet kontrolní body průběhu a zpracovávat distribuci volání funkcí mezi servery.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="f1b8c-119">Na pozadí používá Azure Storage účet k uchování historie spouštění, plánování funkcí aktivity a načítání odpovědí.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="f1b8c-120">Váš kód bez serveru by nikdy neměl spolupracovat s uloženými informacemi v účtu úložiště a obvykle se nejedná o něco, se kterým vývojáři potřebují pracovat.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="f1b8c-121">Aktivace stavového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="f1b8c-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="f1b8c-122">Stavové pracovní postupy v Durable Functions můžou být rozdělené na dvě vnitřní součásti. Orchestrace a triggery aktivit.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="f1b8c-123">Aktivační události a vazby jsou základními součástmi, které používá Azure Functions k tomu, aby byly funkce bez serveru upozorněny na zahájení, přijetí vstupu a vrácení výsledků.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="f1b8c-124">Práce s klientem Orchestration</span><span class="sxs-lookup"><span data-stu-id="f1b8c-124">Working with the Orchestration client</span></span>

<span data-ttu-id="f1b8c-125">Orchestrace jsou v porovnání s jinými styly aktivovaných operací v Azure Functions jedinečné.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="f1b8c-126">Durable Functions umožňuje spuštění funkcí, které mohou trvat hodiny nebo dokonce i dny.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="f1b8c-127">Tento typ chování je v případě potřeby schopný kontrolovat stav probíhající orchestrace, ukončit ukončení nebo odesílat oznámení o externích událostech.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="f1b8c-128">V takových případech rozšíření Durable Functions poskytuje `DurableOrchestrationClient` třídu, která umožňuje interakci s orchestrací funkcí.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="f1b8c-129">Přístup k klientovi Orchestration získáte pomocí `OrchestrationClientAttribute` vazby.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="f1b8c-130">Obecně platí, že byste tento atribut zahrnuli do jiného typu triggeru, například `HttpTrigger` nebo `ServiceBusTrigger`.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="f1b8c-131">Po aktivaci zdrojové funkce lze pomocí klienta Orchestration spustit funkci nástroje Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="f1b8c-132">Funkce Orchestrator</span><span class="sxs-lookup"><span data-stu-id="f1b8c-132">The orchestrator function</span></span>

<span data-ttu-id="f1b8c-133">Poznámka k funkci s OrchestrationTriggerAttribute ve Azure Functions označuje, že funguje jako funkce nástroje Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="f1b8c-134">Zodpovídá za správu různých aktivit, které tvoří stavový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="f1b8c-135">Funkce Orchestrator nemohou používat jiné vazby než OrchestrationTriggerAttribute.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="f1b8c-136">Tento atribut lze použít pouze s typem parametru DurableOrchestrationContext.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="f1b8c-137">Žádné jiné vstupy nelze použít, protože deserializace vstupů v signatuře funkce není podporována.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="f1b8c-138">Chcete-li získat vstupy poskytované klientem Orchestration, je nutné použít metodu GetInput \<T \>.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="f1b8c-139">Návratové typy funkcí orchestrace musí být také typu void, Task nebo serializovatelného hodnoty JSON.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="f1b8c-140">*Kód pro zpracování chyb byl pro zkrácení vynechán.*</span><span class="sxs-lookup"><span data-stu-id="f1b8c-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="f1b8c-141">Můžete spustit a spustit více instancí orchestrace.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="f1b8c-142">Volání metody `StartNewAsync` v `DurableOrchestrationClient` spouští novou instanci orchestrace.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="f1b8c-143">Metoda vrátí `Task<string>`, který se dokončí při zahájení orchestrace.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="f1b8c-144">Výjimka typu `TimeoutException` vyvolána, pokud orchestrace nebyla zahájena během 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="f1b8c-145">Dokončená `Task<string>` z `StartNewAsync` by měla obsahovat jedinečné ID instance Orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="f1b8c-146">Toto ID instance lze použít k vyvolání operací na konkrétní orchestraci.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="f1b8c-147">Orchestrace se dá dotazovat na stav nebo odeslaná oznámení o událostech.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="f1b8c-148">Funkce aktivity</span><span class="sxs-lookup"><span data-stu-id="f1b8c-148">The activity functions</span></span>

<span data-ttu-id="f1b8c-149">Funkce aktivity jsou diskrétní operace, které se skládají společně v rámci orchestrace k vytvoření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="f1b8c-150">Tady je místo, kde se bude provádět většina skutečných prací.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="f1b8c-151">Představují obchodní logiku, dlouho běžící procesy a skládanky na větší řešení.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="f1b8c-152">`ActivityTriggerAttribute` slouží k přidání poznámky k parametru funkce typu `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="f1b8c-153">Použití poznámky informuje modul runtime o tom, že funkce je určena pro použití jako funkce aktivity.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="f1b8c-154">Vstupní hodnoty funkcí aktivity jsou načteny pomocí metody `GetInput<T>` parametru `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="f1b8c-155">Podobně jako funkce orchestrace, návratové typy funkcí aktivity musí být void, Task nebo serializovatelný hodnota JSON.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="f1b8c-156">Všechny neošetřené výjimky, které jsou vyvolány v rámci funkcí aktivity, budou odeslány až do volání funkce Orchestrator a zobrazí se jako `TaskFailedException`.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="f1b8c-157">V tomto okamžiku může být chyba zachycena a zaznamenána v nástroji Orchestrator a aktivitu lze opakovat.</span><span class="sxs-lookup"><span data-stu-id="f1b8c-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="f1b8c-158">Doporučené prostředky</span><span class="sxs-lookup"><span data-stu-id="f1b8c-158">Recommended resources</span></span>

- [<span data-ttu-id="f1b8c-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="f1b8c-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="f1b8c-160">Vazby pro Durable Functions</span><span class="sxs-lookup"><span data-stu-id="f1b8c-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="f1b8c-161">Správa instancí v Durable Functions</span><span class="sxs-lookup"><span data-stu-id="f1b8c-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="f1b8c-162">[Předchozí](event-grid.md)
>[Další](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f1b8c-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
