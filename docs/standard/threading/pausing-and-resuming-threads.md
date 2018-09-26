---
title: Pozastavení a přerušení vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b66881a8a42c0c34b5c2119f7404fe7787c8f3f2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072979"
---
# <a name="pausing-and-interrupting-threads"></a><span data-ttu-id="92d8c-102">Pozastavení a přerušení vlákna</span><span class="sxs-lookup"><span data-stu-id="92d8c-102">Pausing and interrupting threads</span></span>

<span data-ttu-id="92d8c-103">Nejběžnější způsoby pro synchronizaci činností vlákna jsou bloku a verzi vlákna, nebo uzamčení objektů nebo oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="92d8c-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="92d8c-104">Další informace o těchto zamykání a blokování mechanismy, naleznete v tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="92d8c-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="92d8c-105">Je také možné vlákna vložit samotné do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="92d8c-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="92d8c-106">Když jsou zablokované podprocesy nebo režimu spánku, můžete použít <xref:System.Threading.ThreadInterruptedException> přerušení mimo jejich stavů čekání.</span><span class="sxs-lookup"><span data-stu-id="92d8c-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="92d8c-107">Thread.Sleep – metoda</span><span class="sxs-lookup"><span data-stu-id="92d8c-107">The Thread.Sleep method</span></span>

 <span data-ttu-id="92d8c-108">Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metoda způsobí, že aktuální vlákno, okamžitě zablokovat pro počet milisekund nebo časový interval předat metodě a vrací zbytek jeho časovém intervalu do jiného vlákna.</span><span class="sxs-lookup"><span data-stu-id="92d8c-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="92d8c-109">Po uplynutí tohoto intervalu spící vlákno pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="92d8c-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="92d8c-110">Jedno vlákno nemůže volat <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="92d8c-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="92d8c-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> je statická metoda, která způsobí, že vždy aktuální vlákno do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="92d8c-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="92d8c-112">Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> s hodnotou <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> způsobí, že vlákno do režimu spánku, dokud je přerušeno jiným vláknem, která volá <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodu v režimu spánku vlákno nebo dokud nebude ukončen voláním jeho <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="92d8c-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="92d8c-113">Následující příklad znázorňuje oba způsoby by bylo třeba přerušit vlákno režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="92d8c-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="92d8c-114">Přerušení vlákna</span><span class="sxs-lookup"><span data-stu-id="92d8c-114">Interrupting threads</span></span>

 <span data-ttu-id="92d8c-115">Voláním můžete přerušit vlákno čeká <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodu na blokovaná vlákna vyvolání <xref:System.Threading.ThreadInterruptedException>, který přeruší vlákna mimo blokovacího hovoru.</span><span class="sxs-lookup"><span data-stu-id="92d8c-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="92d8c-116">Vlákno byste zachytit <xref:System.Threading.ThreadInterruptedException> a dělat všechno, co je třeba pokračovat v práci.</span><span class="sxs-lookup"><span data-stu-id="92d8c-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="92d8c-117">Pokud vlákno ignoruje výjimka, modul runtime zachytí výjimku a přestane vlákno.</span><span class="sxs-lookup"><span data-stu-id="92d8c-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92d8c-118">Pokud je cílové vlákno blokované, kdy <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> je volána, vlákno proces se nepřerušil dokud bloky.</span><span class="sxs-lookup"><span data-stu-id="92d8c-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="92d8c-119">Pokud se nikdy blokuje vlákno, se stihlo dokončit bez nikdy přerušen.</span><span class="sxs-lookup"><span data-stu-id="92d8c-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="92d8c-120">Pokud čekání se spravované Počkejte, potom <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> obě funkce vlákno okamžitě.</span><span class="sxs-lookup"><span data-stu-id="92d8c-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="92d8c-121">Při čekání na nespravované čekání (například voláním rozhraní Win32 vyvolání platformy [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) funkce), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> může převzít kontrolu nad vlákno, dokud se vrátí do nebo volá do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="92d8c-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="92d8c-122">Chování ve spravovaném kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="92d8c-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="92d8c-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> vlákna mimo všechny čekání, je možné a způsobí, že se probudí <xref:System.Threading.ThreadInterruptedException> vyvolání v cílové vlákno.</span><span class="sxs-lookup"><span data-stu-id="92d8c-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="92d8c-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> vlákna mimo všechny čekání, je možné a způsobí, že se probudí <xref:System.Threading.ThreadAbortException> vyvolání ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="92d8c-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="92d8c-125">Podrobnosti najdete v tématu [ničení vlákna](../../../docs/standard/threading/destroying-threads.md).</span><span class="sxs-lookup"><span data-stu-id="92d8c-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d8c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92d8c-126">See also</span></span>

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadInterruptedException>  
- <xref:System.Threading.ThreadAbortException>  
- [<span data-ttu-id="92d8c-127">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="92d8c-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="92d8c-128">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="92d8c-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
- [<span data-ttu-id="92d8c-129">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="92d8c-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
