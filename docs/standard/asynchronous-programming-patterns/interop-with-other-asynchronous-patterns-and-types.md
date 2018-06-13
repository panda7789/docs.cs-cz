---
title: Interoperabilita s jinými asynchronními vzory a typy
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92725a43e43877488ff9ba93007530c794dd290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571095"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="89cbf-102">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="89cbf-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="89cbf-103">Rozhraní .NET Framework 1.0 zavedená <xref:System.IAsyncResult> vzoru známé jako [asynchronní programování modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), nebo `Begin/End` vzor.</span><span class="sxs-lookup"><span data-stu-id="89cbf-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="89cbf-104">Rozhraní .NET Framework 2.0, přidat [na základě událostí asynchronní vzor (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="89cbf-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="89cbf-105">Od verze rozhraní .NET Framework 4 [založený na úlohách asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) nahrazuje APM a EAP, ale umožňuje snadno vytvářet rutiny migraci ze starších vzory.</span><span class="sxs-lookup"><span data-stu-id="89cbf-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="89cbf-106">V tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="89cbf-106">In this topic:</span></span>  
  
-   <span data-ttu-id="89cbf-107">[Úlohy a APM](#APM) ([z APM můžete na](#ApmToTap) nebo [z klepněte sem a můžete APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="89cbf-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
-   [<span data-ttu-id="89cbf-108">Úlohy a protokolu EAP</span><span class="sxs-lookup"><span data-stu-id="89cbf-108">Tasks and EAP</span></span>](#EAP)  
  
-   <span data-ttu-id="89cbf-109">[Úlohy a obslužné rutiny čekání](#WaitHandles) ([z obslužné rutiny čekání na klepněte na](#WHToTap) nebo [z klepněte sem a můžete obslužné rutiny čekání](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="89cbf-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="89cbf-110">Úlohy a Model asynchronního programování (APM)</span><span class="sxs-lookup"><span data-stu-id="89cbf-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="89cbf-111">Z APM můžete na</span><span class="sxs-lookup"><span data-stu-id="89cbf-111">From APM to TAP</span></span>  
 <span data-ttu-id="89cbf-112">Protože [asynchronní programování modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) vzor je velmi strukturovaných, je poměrně snadné sestavení obálku vystavit jako implementace klepněte na implementaci APM.</span><span class="sxs-lookup"><span data-stu-id="89cbf-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="89cbf-113">V faktu, rozhraní .NET Framework, počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obsahuje pomocné rutiny ve formě <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> přetížení metody zajistit tento překlad.</span><span class="sxs-lookup"><span data-stu-id="89cbf-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="89cbf-114">Vezměte v úvahu <xref:System.IO.Stream> třídy a jeho <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A> metody, které představuje protějšku APM synchronní <xref:System.IO.Stream.Read%2A> metoda:</span><span class="sxs-lookup"><span data-stu-id="89cbf-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="89cbf-115">Můžete použít <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody k implementaci klepněte na obálku pro tuto operaci následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="89cbf-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="89cbf-116">Tato implementace je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="89cbf-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="89cbf-117">Z klepněte sem a můžete APM</span><span class="sxs-lookup"><span data-stu-id="89cbf-117">From TAP to APM</span></span>  
 <span data-ttu-id="89cbf-118">Pokud vaše stávající infrastruktury očekává vzoru APM, budete chtít taky trvat klepněte na implementaci a použít ho, kde je očekávána implementace APM.</span><span class="sxs-lookup"><span data-stu-id="89cbf-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="89cbf-119">Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci.</span><span class="sxs-lookup"><span data-stu-id="89cbf-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="89cbf-120">Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít skoro stejné funkce pro neobecný úlohy.</span><span class="sxs-lookup"><span data-stu-id="89cbf-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="89cbf-121">Nyní Představte si případ, kdy máte následující implementaci klepněte na:</span><span class="sxs-lookup"><span data-stu-id="89cbf-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="89cbf-122">a chcete poskytovat tato implementace APM:</span><span class="sxs-lookup"><span data-stu-id="89cbf-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="89cbf-123">Následující příklad ukazuje jeden migrace APM:</span><span class="sxs-lookup"><span data-stu-id="89cbf-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="89cbf-124">Úlohy a asynchronní vzor (EAP) založených na událostech</span><span class="sxs-lookup"><span data-stu-id="89cbf-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="89cbf-125">Zabalení [na základě událostí asynchronní vzor (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementace je složitější než zabalení APM vzoru, protože vzoru EAP má menší struktury než vzoru APM a další variace.</span><span class="sxs-lookup"><span data-stu-id="89cbf-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="89cbf-126">K předvedení, se zabalí následující kód `DownloadStringAsync` metoda.</span><span class="sxs-lookup"><span data-stu-id="89cbf-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="89cbf-127">`DownloadStringAsync` přijímá identifikátor URI, vyvolá `DownloadProgressChanged` události při stahování za účelem hlášení více statistiky na průběh a vyvolá `DownloadStringCompleted` událost, pokud se provádí.</span><span class="sxs-lookup"><span data-stu-id="89cbf-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="89cbf-128">Konečný výsledek je řetězec, který obsahuje obsah na stránce na zadaný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="89cbf-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="89cbf-129">Úlohy a obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="89cbf-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="89cbf-130">Z obslužné rutiny čekání na klepněte na</span><span class="sxs-lookup"><span data-stu-id="89cbf-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="89cbf-131">I když obslužné rutiny čekání nebudete implementovat asynchronní vzor, pokročilé vývojáři mohou použít <xref:System.Threading.WaitHandle> třídy a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody pro asynchronní oznámení, když je nastaven popisovač čekání.</span><span class="sxs-lookup"><span data-stu-id="89cbf-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="89cbf-132">Může obtékat <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> způsob povolení založený na úlohách alternativu, která umožňuje všechny synchronní čekání na popisovač čekání:</span><span class="sxs-lookup"><span data-stu-id="89cbf-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="89cbf-133">Pomocí této metody můžete použít existující <xref:System.Threading.WaitHandle> implementace v asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="89cbf-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="89cbf-134">Například pokud chcete omezit počet asynchronních operací, které jsou prováděny v jakémkoli čase, můžete využít semafor ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> objekt).</span><span class="sxs-lookup"><span data-stu-id="89cbf-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="89cbf-135">Můžete omezit na *N* počet operací, které běží souběžně podle inicializace semafor počet *N*, čekání na semaforu vždy, když chcete provést operace a uvolněním semafor, když jste hotovi s operace:</span><span class="sxs-lookup"><span data-stu-id="89cbf-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="89cbf-136">Můžete také vytvořit asynchronní semafor, který není závislý na obslužné rutiny čekání a místo toho pracuje úplně úlohy.</span><span class="sxs-lookup"><span data-stu-id="89cbf-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="89cbf-137">K tomuto účelu můžete použít techniky, jako jsou popsané v [použití asynchronního vzoru založeného na úloze](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytvoření datové struktury na <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="89cbf-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="89cbf-138">Z klepněte sem a můžete obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="89cbf-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="89cbf-139">Jak už jsme zmínili, <xref:System.Threading.Tasks.Task> třída implementuje <xref:System.IAsyncResult>, a že implementace zveřejňuje <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> vlastnost, která vrací popisovač čekání, které bude nastaveno při <xref:System.Threading.Tasks.Task> dokončení.</span><span class="sxs-lookup"><span data-stu-id="89cbf-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="89cbf-140">Můžete získat <xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="89cbf-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="89cbf-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="89cbf-141">See Also</span></span>  
 [<span data-ttu-id="89cbf-142">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="89cbf-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [<span data-ttu-id="89cbf-143">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="89cbf-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [<span data-ttu-id="89cbf-144">Použití asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="89cbf-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
