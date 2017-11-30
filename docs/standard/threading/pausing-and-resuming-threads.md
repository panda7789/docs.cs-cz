---
title: "Pozastavování a obnovování vláken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a><span data-ttu-id="6426b-102">Pozastavování a obnovování vláken</span><span class="sxs-lookup"><span data-stu-id="6426b-102">Pausing and Resuming Threads</span></span>
<span data-ttu-id="6426b-103">Nejběžnější způsoby pro synchronizaci aktivity vláken jsou bloku a verzi vlákna nebo objekty uzamčení nebo oblastech kódu.</span><span class="sxs-lookup"><span data-stu-id="6426b-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="6426b-104">Další informace o těchto zamykání a blokování mechanismy najdete v tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="6426b-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="6426b-105">Můžete taky nechat vláken put sami do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="6426b-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="6426b-106">Když jsou zablokované podprocesy nebo režimu spánku, můžete použít <xref:System.Threading.ThreadInterruptedException> pro přerušení je mimo stavy jejich čekání.</span><span class="sxs-lookup"><span data-stu-id="6426b-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="6426b-107">Metoda Thread.Sleep</span><span class="sxs-lookup"><span data-stu-id="6426b-107">The Thread.Sleep Method</span></span>  
 <span data-ttu-id="6426b-108">Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metoda způsobí, že aktuální vlákno okamžitě blokování pro počet milisekund nebo časový interval, předáte metodě a vypočítá zbytek jeho časovém intervalu na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="6426b-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="6426b-109">Po uplynutí této interval obnoví spící vláken provádění.</span><span class="sxs-lookup"><span data-stu-id="6426b-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="6426b-110">Nelze volat jedno vlákno <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="6426b-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="6426b-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>je statická metoda, která způsobí, že vždy aktuální vlákno do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="6426b-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="6426b-112">Volání metody <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> s hodnotou <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> způsobí, že vlákno do režimu spánku, dokud bude přerušen přívod jiné vlákno, která volá <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metoda ve vlákně, v režimu spánku, nebo dokud není ukončen voláním jeho <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="6426b-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="6426b-113">Následující příklad ilustruje obě metody přerušení spící vlákna.</span><span class="sxs-lookup"><span data-stu-id="6426b-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="6426b-114">Přerušení vláken</span><span class="sxs-lookup"><span data-stu-id="6426b-114">Interrupting Threads</span></span>  
 <span data-ttu-id="6426b-115">Čekání na vlákno může přerušit voláním <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> blokované vlákno vyvolá metodu <xref:System.Threading.ThreadInterruptedException>, která dělí vlákna mimo blokování volání.</span><span class="sxs-lookup"><span data-stu-id="6426b-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="6426b-116">Vlákno by měl catch <xref:System.Threading.ThreadInterruptedException> a jakékoli je vhodné pokračovat v práci.</span><span class="sxs-lookup"><span data-stu-id="6426b-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="6426b-117">Pokud vlákno ignoruje výjimka, modul runtime zachytí výjimky a zastaví vlákno.</span><span class="sxs-lookup"><span data-stu-id="6426b-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6426b-118">Pokud cílový vlákno není blokované při <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> je volána, vlákno proces se nepřerušil dokud bloky.</span><span class="sxs-lookup"><span data-stu-id="6426b-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="6426b-119">Pokud vlákno nikdy blokuje, mohli dokončit bez někdy přerušena.</span><span class="sxs-lookup"><span data-stu-id="6426b-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="6426b-120">Pokud čekání je spravovaný čekání, pak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> obě vlákno probuzení okamžitě.</span><span class="sxs-lookup"><span data-stu-id="6426b-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="6426b-121">Pokud čekání nespravované čekání (například platformu vyvolat volání Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) funkce), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> může převzít kontrolu nad vlákno, dokud vrátí nebo volá do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6426b-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="6426b-122">Ve spravovaném kódu chování je následující:</span><span class="sxs-lookup"><span data-stu-id="6426b-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="6426b-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>vlákna mimo žádné čekání to může být v a způsobí, že se probudí <xref:System.Threading.ThreadInterruptedException> vyvolání ve vlákně na cílový.</span><span class="sxs-lookup"><span data-stu-id="6426b-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="6426b-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>vlákna mimo žádné čekání to může být v a způsobí, že se probudí <xref:System.Threading.ThreadAbortException> vyvolání na vlákno.</span><span class="sxs-lookup"><span data-stu-id="6426b-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="6426b-125">Podrobnosti najdete v tématu [zničení vláken](../../../docs/standard/threading/destroying-threads.md).</span><span class="sxs-lookup"><span data-stu-id="6426b-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6426b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="6426b-126">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [<span data-ttu-id="6426b-127">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="6426b-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="6426b-128">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="6426b-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="6426b-129">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="6426b-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
