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
ms.openlocfilehash: f9fe33bb46f0ba78756c4172032dfbaf45d6fc89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123977"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="6b2b3-102">Interoperabilita s jinými asynchronními vzory a typy</span><span class="sxs-lookup"><span data-stu-id="6b2b3-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="6b2b3-103">.NET Framework 1,0 představil vzor <xref:System.IAsyncResult>, jinak označované jako [asynchronní programovací model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)nebo vzor `Begin/End`.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="6b2b3-104">.NET Framework 2,0 přidal [asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="6b2b3-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="6b2b3-105">Počínaje .NET Framework 4, [asynchronní vzor založený na úlohách (klepněte) nahrazuje rozhraní](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) APM i EAP, ale poskytuje možnost snadného sestavení rutin migrace z předchozích vzorů.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="6b2b3-106">V tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-106">In this topic:</span></span>  
  
- <span data-ttu-id="6b2b3-107">[Úlohy a APM](#APM) ([od APM po klepnutí](#ApmToTap) nebo [z klepněte na APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="6b2b3-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
- [<span data-ttu-id="6b2b3-108">Úlohy a EAP</span><span class="sxs-lookup"><span data-stu-id="6b2b3-108">Tasks and EAP</span></span>](#EAP)  
  
- <span data-ttu-id="6b2b3-109">[Úlohy a obslužné rutiny čekání](#WaitHandles) ([z obslužných rutin čekání na klepnutí](#WHToTap) nebo [z klepnutí na obslužné rutiny čekání](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="6b2b3-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="6b2b3-110">Úlohy a model asynchronního programování (APM)</span><span class="sxs-lookup"><span data-stu-id="6b2b3-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="6b2b3-111">Od APM po klepnutí</span><span class="sxs-lookup"><span data-stu-id="6b2b3-111">From APM to TAP</span></span>  
 <span data-ttu-id="6b2b3-112">Vzhledem k tomu, že je vzor [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) velmi strukturovaný, je poměrně snadné vytvořit obálku, aby vystavila implementaci APM jako klepnutím na implementaci.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="6b2b3-113">Ve skutečnosti .NET Framework, počínaje .NET Framework 4, obsahuje pomocné rutiny ve formě <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> přetížení metod pro poskytnutí tohoto překladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-113">In fact, the .NET Framework, starting with .NET Framework 4, includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="6b2b3-114">Zvažte třídu <xref:System.IO.Stream> a její metody <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A>, které reprezentují protějšek APM pro synchronní <xref:System.IO.Stream.Read%2A> metodu:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="6b2b3-115">Pomocí metody <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> můžete pro tuto operaci implementovat obálku klepnutím následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="6b2b3-116">Tato implementace je podobná následující:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="6b2b3-117">Z klepnutí na APM</span><span class="sxs-lookup"><span data-stu-id="6b2b3-117">From TAP to APM</span></span>  
 <span data-ttu-id="6b2b3-118">Pokud vaše stávající infrastruktura očekává vzor APM, budete také chtít provést implementaci klepnutím a použít ji tam, kde se očekává implementace APM.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="6b2b3-119">Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="6b2b3-120">Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít téměř totožnou funkci pro neobecné úlohy.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="6b2b3-121">Nyní vezměte v úvahu případ, kde máte následující implementaci klepnutím:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="6b2b3-122">a chcete poskytnout tuto implementaci APM:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="6b2b3-123">Následující příklad ukazuje jednu migraci na APM:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="6b2b3-124">Úlohy a asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="6b2b3-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="6b2b3-125">Zabalení implementace [asynchronního vzoru založeného na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) je větší než zabalení vzoru APM, protože vzor protokolu EAP má větší variaci a méně než strukturu APM.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="6b2b3-126">K předvedení následujícího kódu zabalí metodu `DownloadStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="6b2b3-127">`DownloadStringAsync` přijímá identifikátor URI, vyvolává během stahování událost `DownloadProgressChanged`, aby bylo možné ohlásit více statistik průběhu, a událost `DownloadStringCompleted` po dokončení vyvolá.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="6b2b3-128">Konečný výsledek je řetězec, který obsahuje obsah stránky se zadaným identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="6b2b3-129">Úlohy a obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="6b2b3-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="6b2b3-130">Z obslužných rutin čekání na klepnutí</span><span class="sxs-lookup"><span data-stu-id="6b2b3-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="6b2b3-131">Ačkoli obslužné rutiny čekání neimplementují asynchronní vzorek, pokročilí vývojáři mohou použít třídu <xref:System.Threading.WaitHandle> a metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> pro asynchronní oznámení, když je nastaven popisovač čekání.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="6b2b3-132">Metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> lze zabalit, chcete-li povolit alternativu na základě úlohy do synchronního čekání na popisovač čekání:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="6b2b3-133">Pomocí této metody můžete použít existující implementace <xref:System.Threading.WaitHandle> v asynchronních metodách.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="6b2b3-134">Například pokud chcete omezit počet asynchronních operací, které jsou spuštěny v určitém čase, můžete použít semafor (objekt <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="6b2b3-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="6b2b3-135">Můžete omezit na *n* počet operací, které se souběžně spouštějí, inicializací počtu semaforu na *N*, čekáním na semafor kdykoli chcete provést operaci, a uvolněním semaforu, když jste dokončili operaci:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="6b2b3-136">Můžete také vytvořit asynchronní semafor, který nespoléhá na obslužné rutiny čekání a místo toho funguje zcela s úkoly.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="6b2b3-137">K tomu můžete použít techniky, jako jsou popsány v tématu použití [asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytváření datových struktur nad <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="6b2b3-138">Od klepnutí do čekání na zpracování</span><span class="sxs-lookup"><span data-stu-id="6b2b3-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="6b2b3-139">Jak už jsme uvedli, třída <xref:System.Threading.Tasks.Task> implementuje <xref:System.IAsyncResult>a tato implementace zpřístupňuje vlastnost <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A>, která vrací popisovač čekání, který se nastaví po dokončení <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="6b2b3-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="6b2b3-140"><xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> můžete získat takto:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="6b2b3-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b2b3-141">See also</span></span>

- [<span data-ttu-id="6b2b3-142">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="6b2b3-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="6b2b3-143">Implementace asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="6b2b3-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="6b2b3-144">Použití asynchronního vzoru založeného na úlohách</span><span class="sxs-lookup"><span data-stu-id="6b2b3-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
