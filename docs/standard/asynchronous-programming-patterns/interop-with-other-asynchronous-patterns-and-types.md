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
ms.openlocfilehash: 981c13c68eaf1eb0c19f95eb1b097935ea02a16d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159751"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="f07e4-102">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="f07e4-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="f07e4-103">Rozhraní .NET Framework 1.0 <xref:System.IAsyncResult> zavedlo vzor, jinak známý jako [asynchronní programovací model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)nebo `Begin/End` vzor.</span><span class="sxs-lookup"><span data-stu-id="f07e4-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="f07e4-104">Rozhraní .NET Framework 2.0 přidalo [asynchronní vzor založený na událostech (EAP).](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)</span><span class="sxs-lookup"><span data-stu-id="f07e4-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="f07e4-105">Počínaje rozhraním .NET Framework 4 nahrazuje [asynchronní vzor (TAP) asynchronní vzor (APM)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) a EAP, ale poskytuje možnost snadno vytvářet rutiny migrace z dřívějších vzorů.</span><span class="sxs-lookup"><span data-stu-id="f07e4-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="f07e4-106">V tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="f07e4-106">In this topic:</span></span>  
  
- <span data-ttu-id="f07e4-107">[Úkoly a APM](#APM) [(od APM do TAP](#ApmToTap) nebo [z TAP do APM)](#TapToApm)</span><span class="sxs-lookup"><span data-stu-id="f07e4-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
- [<span data-ttu-id="f07e4-108">Úkoly a eAP</span><span class="sxs-lookup"><span data-stu-id="f07e4-108">Tasks and EAP</span></span>](#EAP)  
  
- <span data-ttu-id="f07e4-109">[Úkoly a popisovače čekání](#WaitHandles) [(od úchytů čekání po klepnutí na klepnutím](#WHToTap) nebo z [klepnutelů na úchyty](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="f07e4-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="f07e4-110">Úkoly a asynchronní programovací model (APM)</span><span class="sxs-lookup"><span data-stu-id="f07e4-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a><span data-ttu-id="f07e4-111">Od APM do TAP</span><span class="sxs-lookup"><span data-stu-id="f07e4-111">From APM to TAP</span></span>  
 <span data-ttu-id="f07e4-112">Vzhledem k tomu, že vzor [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) je velmi strukturovaný, je poměrně snadné vytvořit obálku, která zpřístupní implementaci APM jako implementaci TAP.</span><span class="sxs-lookup"><span data-stu-id="f07e4-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="f07e4-113">Ve skutečnosti rozhraní .NET Framework, počínaje rozhraním .NET Framework 4, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> zahrnuje pomocné rutiny ve formě přetížení metody k poskytnutí tohoto překladu.</span><span class="sxs-lookup"><span data-stu-id="f07e4-113">In fact, the .NET Framework, starting with .NET Framework 4, includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="f07e4-114">Zvažte <xref:System.IO.Stream> třídu <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> a její metody a metody, které <xref:System.IO.Stream.Read%2A> představují protějšek APM synchronní metody:</span><span class="sxs-lookup"><span data-stu-id="f07e4-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="f07e4-115">Metodu <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> můžete použít k implementaci obálky TAP pro tuto operaci následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f07e4-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="f07e4-116">Tato implementace je podobná následující:</span><span class="sxs-lookup"><span data-stu-id="f07e4-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a><span data-ttu-id="f07e4-117">Z TAP na APM</span><span class="sxs-lookup"><span data-stu-id="f07e4-117">From TAP to APM</span></span>  
 <span data-ttu-id="f07e4-118">Pokud vaše stávající infrastruktura očekává vzor APM, budete také chtít provést implementaci TAP a použít ji tam, kde se očekává implementace APM.</span><span class="sxs-lookup"><span data-stu-id="f07e4-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="f07e4-119">Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci.</span><span class="sxs-lookup"><span data-stu-id="f07e4-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="f07e4-120">Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít téměř identické funkce pro neobecné úkoly.</span><span class="sxs-lookup"><span data-stu-id="f07e4-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="f07e4-121">Nyní zvažte případ, kdy máte následující implementaci TAP:</span><span class="sxs-lookup"><span data-stu-id="f07e4-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="f07e4-122">a chcete zadat tuto implementaci APM:</span><span class="sxs-lookup"><span data-stu-id="f07e4-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="f07e4-123">Následující příklad ukazuje jednu migraci do APM:</span><span class="sxs-lookup"><span data-stu-id="f07e4-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="f07e4-124">Úkoly a asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="f07e4-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="f07e4-125">Obtékání implementace [asynchronního vzoru (EAP) založené na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) je více než obtékání vzoru APM, protože vzor Protokolu EAP má více variant a menší strukturu než vzorek APM.</span><span class="sxs-lookup"><span data-stu-id="f07e4-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="f07e4-126">Chcete-li demonstrovat, následující `DownloadStringAsync` kód obtéká metodu.</span><span class="sxs-lookup"><span data-stu-id="f07e4-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="f07e4-127">`DownloadStringAsync`přijímá identifikátor URI, `DownloadProgressChanged` vyvolá událost při stahování, aby bylo možné hlásit `DownloadStringCompleted` více statistik o průběhu, a vyvolá událost, když je hotová.</span><span class="sxs-lookup"><span data-stu-id="f07e4-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="f07e4-128">Konečným výsledkem je řetězec, který obsahuje obsah stránky na zadaný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="f07e4-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="f07e4-129">Úkoly a popisovače čekání</span><span class="sxs-lookup"><span data-stu-id="f07e4-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="f07e4-130">Od úchyty čekání k tap</span><span class="sxs-lookup"><span data-stu-id="f07e4-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="f07e4-131">Přestože popisovače čekání neimplementují asynchronní vzor, pokročilí vývojáři mohou použít třídu <xref:System.Threading.WaitHandle> a metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> pro asynchronní oznámení při nastavení popisovače čekání.</span><span class="sxs-lookup"><span data-stu-id="f07e4-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="f07e4-132">Metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> můžete zabalit a povolit alternativu založenou na úlohách k libovolnému synchronnímu čekání na popisovači čekání:</span><span class="sxs-lookup"><span data-stu-id="f07e4-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="f07e4-133">Pomocí této metody můžete <xref:System.Threading.WaitHandle> použít existující implementace v asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="f07e4-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="f07e4-134">Například pokud chcete omezit počet asynchronních operací, které jsou prováděny v určitém okamžiku, můžete využít <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> semafor (objekt).</span><span class="sxs-lookup"><span data-stu-id="f07e4-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="f07e4-135">Můžete omezit na *N* počet operací, které běží souběžně inicializací semaforu počet *N*, čekání na semafor kdykoli chcete provést operaci a uvolnění semaforu, když jste hotovi s operací:</span><span class="sxs-lookup"><span data-stu-id="f07e4-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="f07e4-136">Můžete také vytvořit asynchronní semafor, který nespoléhá na popisovače čekání a místo toho pracuje zcela s úkoly.</span><span class="sxs-lookup"><span data-stu-id="f07e4-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="f07e4-137">Chcete-li to provést, můžete použít techniky, jako jsou popsány v [náročné task-based asynchronní vzor](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytváření datových <xref:System.Threading.Tasks.Task>struktur nad .</span><span class="sxs-lookup"><span data-stu-id="f07e4-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="f07e4-138">Od klepnutí klepnutím na úchyty čekání</span><span class="sxs-lookup"><span data-stu-id="f07e4-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="f07e4-139">Jak již bylo <xref:System.Threading.Tasks.Task> zmíněno, <xref:System.IAsyncResult>třída implementuje <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> a že implementace zpřístupňuje vlastnost, <xref:System.Threading.Tasks.Task> která vrátí popisovač čekání, který bude nastaven po dokončení.</span><span class="sxs-lookup"><span data-stu-id="f07e4-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="f07e4-140">Můžete získat <xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> následující:</span><span class="sxs-lookup"><span data-stu-id="f07e4-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="f07e4-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="f07e4-141">See also</span></span>

- [<span data-ttu-id="f07e4-142">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="f07e4-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="f07e4-143">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="f07e4-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="f07e4-144">Použití asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="f07e4-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
