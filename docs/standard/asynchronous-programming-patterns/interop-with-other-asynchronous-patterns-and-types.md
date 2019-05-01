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
ms.openlocfilehash: 4f6cb2d387e3b979ed0d4407e17287fb93fa0a20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031210"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="bb369-102">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="bb369-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="bb369-103">Rozhraní .NET Framework 1.0 zavedené <xref:System.IAsyncResult> vzor, jinak známé jako [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), nebo `Begin/End` vzor.</span><span class="sxs-lookup"><span data-stu-id="bb369-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="bb369-104">Přidání rozhraní .NET Framework 2.0 [události asynchronní vzor založený (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="bb369-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="bb369-105">Od verze rozhraní .NET Framework 4 [úkolově orientovanou asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) nahrazuje funkce APM a protokolu EAP, ale umožňuje snadno vytvářet migraci rutin z předchozích vzory.</span><span class="sxs-lookup"><span data-stu-id="bb369-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="bb369-106">V tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="bb369-106">In this topic:</span></span>  
  
- <span data-ttu-id="bb369-107">[Úlohy a APM](#APM) ([z APM klepnutím](#ApmToTap) nebo [z klepnutím APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="bb369-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
- [<span data-ttu-id="bb369-108">Úlohy a protokolu EAP</span><span class="sxs-lookup"><span data-stu-id="bb369-108">Tasks and EAP</span></span>](#EAP)  
  
- <span data-ttu-id="bb369-109">[Úkoly a obslužné rutiny čekání](#WaitHandles) ([z obslužné rutiny čekání klepnutím](#WHToTap) nebo [z klepněte sem a můžete obslužné rutiny čekání](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="bb369-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="bb369-110">Úlohy a Model asynchronního programování (APM)</span><span class="sxs-lookup"><span data-stu-id="bb369-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="bb369-111">Z APM klepnutím</span><span class="sxs-lookup"><span data-stu-id="bb369-111">From APM to TAP</span></span>  
 <span data-ttu-id="bb369-112">Vzhledem k tomu, [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) vzor je velmi strukturovaných, je poměrně snadné sestavení obálky vystavit jako implementace TAP implementaci APM.</span><span class="sxs-lookup"><span data-stu-id="bb369-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="bb369-113">Ve skutečnosti, rozhraní .NET Framework počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obsahuje pomocné rutiny v podobě <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> přetížení metody k poskytování tohoto převodu.</span><span class="sxs-lookup"><span data-stu-id="bb369-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="bb369-114">Vezměte v úvahu <xref:System.IO.Stream> třídy a jeho <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A> metody, které představují protějšek APM synchronní <xref:System.IO.Stream.Read%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="bb369-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="bb369-115">Můžete použít <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody k implementaci klepněte na obálku pro tuto operaci následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bb369-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="bb369-116">Tato implementace se podobá této:</span><span class="sxs-lookup"><span data-stu-id="bb369-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="bb369-117">Z klepnutím APM</span><span class="sxs-lookup"><span data-stu-id="bb369-117">From TAP to APM</span></span>  
 <span data-ttu-id="bb369-118">Pokud vaší stávající infrastruktury očekává, že vzor APM, je také vhodné přijmout implementace TAP a jeho použití, kde je očekávána implementace APM.</span><span class="sxs-lookup"><span data-stu-id="bb369-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="bb369-119">Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci.</span><span class="sxs-lookup"><span data-stu-id="bb369-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="bb369-120">Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít téměř identické funkce pro obecné úlohy.</span><span class="sxs-lookup"><span data-stu-id="bb369-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="bb369-121">Nyní Představte si případ, kdy máte následující implementace TAP:</span><span class="sxs-lookup"><span data-stu-id="bb369-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="bb369-122">a chcete poskytnout implementaci této funkce APM:</span><span class="sxs-lookup"><span data-stu-id="bb369-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="bb369-123">Následující příklad ukazuje jednu migraci do APM:</span><span class="sxs-lookup"><span data-stu-id="bb369-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="bb369-124">Úlohy a asynchronní vzor (EAP) založených na událostech</span><span class="sxs-lookup"><span data-stu-id="bb369-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="bb369-125">Zabalení [události asynchronní vzor založený (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementace je složitější než pro zabalení APM vzor, protože vzoru EAP má méně struktury než vzor APM a více variant.</span><span class="sxs-lookup"><span data-stu-id="bb369-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="bb369-126">Abychom si předvedli, zabalí následující kód `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="bb369-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="bb369-127">`DownloadStringAsync` přijímá identifikátor URI, vyvolá `DownloadProgressChanged` událostí při stahování za účelem hlášení o průběhu a vyvolá více statistiky `DownloadStringCompleted` událost, když se to dělá.</span><span class="sxs-lookup"><span data-stu-id="bb369-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="bb369-128">Konečný výsledek je řetězec, který obsahuje obsah stránky se zadaným identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="bb369-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="bb369-129">Úlohy a obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="bb369-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="bb369-130">Z obslužné rutiny čekání klepnutím</span><span class="sxs-lookup"><span data-stu-id="bb369-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="bb369-131">I když obslužné rutiny čekání nemusíte implementovat asynchronní vzor, pokročilé mohou vývojáři <xref:System.Threading.WaitHandle> třídy a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody pro asynchronní oznámení, když je nastaven popisovač čekání.</span><span class="sxs-lookup"><span data-stu-id="bb369-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="bb369-132">Můžete zabalit <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metoda umožňuje založené na úlohách alternativu jakékoli synchronní čekání na popisovač čekání:</span><span class="sxs-lookup"><span data-stu-id="bb369-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="bb369-133">Pomocí této metody můžete použít existující <xref:System.Threading.WaitHandle> implementace v asynchronních metodách.</span><span class="sxs-lookup"><span data-stu-id="bb369-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="bb369-134">Například pokud chcete omezit počet asynchronních operací, které jsou spuštěny v určitém čase, můžete využít semafor ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> objekt).</span><span class="sxs-lookup"><span data-stu-id="bb369-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="bb369-135">Můžete omezit na *N* počet operací, které běží souběžně podle počtu semaforu pro inicializaci *N*, čeká na semaforu kdykoli chcete provádět operace a uvolněním Semaphore – až budete hotovi s operací:</span><span class="sxs-lookup"><span data-stu-id="bb369-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="bb369-136">Můžete také vytvořit asynchronní semafor, který nevyžaduje obslužné rutiny čekání a místo toho pracuje úplně s úkoly.</span><span class="sxs-lookup"><span data-stu-id="bb369-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="bb369-137">K tomuto účelu můžete použít techniky, jako jsou ty popsané v [využívání Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytváření datových struktur nad <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="bb369-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="bb369-138">Z klepněte sem a můžete obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="bb369-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="bb369-139">Jak už jsme zmínili, <xref:System.Threading.Tasks.Task> implementuje třída <xref:System.IAsyncResult>, a zpřístupňuje tuto implementaci <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> vlastnosti, která vrací popisovač čekání, který bude nastavit, když <xref:System.Threading.Tasks.Task> dokončí.</span><span class="sxs-lookup"><span data-stu-id="bb369-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="bb369-140">Můžete získat <xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bb369-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="bb369-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb369-141">See also</span></span>

- [<span data-ttu-id="bb369-142">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="bb369-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="bb369-143">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="bb369-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="bb369-144">Použití asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="bb369-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
