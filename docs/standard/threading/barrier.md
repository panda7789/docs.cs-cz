---
title: Bariéra [.NET Framework]
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 385e370f205851630f809b285a93c2609220efeb
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527431"
---
# <a name="barrier-net-framework"></a><span data-ttu-id="cad30-102">Bariéra [.NET Framework]</span><span class="sxs-lookup"><span data-stu-id="cad30-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="cad30-103">A *bariéry* je uživatelem definovaný primitiv synchronizace, která umožňuje více vláken (označované jako *účastníci*) pracovat souběžně na algoritmus ve fázích.</span><span class="sxs-lookup"><span data-stu-id="cad30-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="cad30-104">Každý účastník opakuje, dokud se nedosáhne barrier bod v kódu.</span><span class="sxs-lookup"><span data-stu-id="cad30-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="cad30-105">Odbourejte překážky bránící představuje konec jednu fázi práce.</span><span class="sxs-lookup"><span data-stu-id="cad30-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="cad30-106">Odbourejte překážky bránící dosáhne účastníka blokuje, dokud všichni účastníci dosáhnou této bariéry stejné.</span><span class="sxs-lookup"><span data-stu-id="cad30-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="cad30-107">Jakmile všichni účastníci dosáhnou této bariéry, můžete volitelně vyvolat akce po fázi.</span><span class="sxs-lookup"><span data-stu-id="cad30-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="cad30-108">Tuto fázi po akci můžete využívat k provádění akcí jedním vláknem a když jsou všechny ostatní vlákna budou i nadále zablokované.</span><span class="sxs-lookup"><span data-stu-id="cad30-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="cad30-109">Po spuštění akce jsou všechny odblokované účastníci.</span><span class="sxs-lookup"><span data-stu-id="cad30-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="cad30-110">Následující fragment kódu ukazuje základní barrier vzor.</span><span class="sxs-lookup"><span data-stu-id="cad30-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="cad30-111">Kompletní příklad naleznete v tématu [postupy: synchronizace souběžných operací pomocí bariéry](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="cad30-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="cad30-112">Přidávání a odebírání účastníků</span><span class="sxs-lookup"><span data-stu-id="cad30-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="cad30-113">Když vytvoříte <xref:System.Threading.Barrier>, zadejte počet účastníků.</span><span class="sxs-lookup"><span data-stu-id="cad30-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="cad30-114">Můžete také přidat nebo odebrat účastníci dynamicky kdykoli.</span><span class="sxs-lookup"><span data-stu-id="cad30-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="cad30-115">Například, pokud jeden účastník řeší jeho část problému, můžete uložit výsledek, zastavit provádění na vlákno a volat <xref:System.Threading.Barrier.RemoveParticipant%2A> se sníží počet účastníků v odbourejte překážky bránící.</span><span class="sxs-lookup"><span data-stu-id="cad30-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="cad30-116">Když přidáte účastníka voláním <xref:System.Threading.Barrier.AddParticipant%2A>, návratová hodnota určuje číslo aktuální fázi, který může být užitečné, pokud chcete inicializovat pracovní nového účastníka.</span><span class="sxs-lookup"><span data-stu-id="cad30-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="cad30-117">Nefunkční překážek</span><span class="sxs-lookup"><span data-stu-id="cad30-117">Broken Barriers</span></span>  
 <span data-ttu-id="cad30-118">Zablokování může dojít, pokud jeden účastník nepodaří spojit odbourejte překážky bránící.</span><span class="sxs-lookup"><span data-stu-id="cad30-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="cad30-119">Aby se zabránilo tyto zablokování, použijte přetížení <xref:System.Threading.Barrier.SignalAndWait%2A> metoda zadat časový limit a token zrušení.</span><span class="sxs-lookup"><span data-stu-id="cad30-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="cad30-120">Tato přetížení návratový logická hodnota, která každých účastníka můžete zkontrolovat dříve, než bude pokračovat do další fáze.</span><span class="sxs-lookup"><span data-stu-id="cad30-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="cad30-121">Po fázi výjimky</span><span class="sxs-lookup"><span data-stu-id="cad30-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="cad30-122">Pokud po fázi delegáta vyvolá výjimku, je obalen <xref:System.Threading.BarrierPostPhaseException> objekt, který je pak šířený do všichni účastníci.</span><span class="sxs-lookup"><span data-stu-id="cad30-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="cad30-123">Barrier oproti ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="cad30-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="cad30-124">Vlákna provádění více fázích ve smyčkách jsou zvláště užitečné překážek.</span><span class="sxs-lookup"><span data-stu-id="cad30-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="cad30-125">Pokud váš kód vyžaduje pouze jednu nebo dvě fáze práce, zvažte, jestli se má použít <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty s jakýmkoli implicitní spojení, včetně:</span><span class="sxs-lookup"><span data-stu-id="cad30-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="cad30-126">Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování používání](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="cad30-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad30-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cad30-127">See also</span></span>

- [<span data-ttu-id="cad30-128">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="cad30-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="cad30-129">Postupy: Synchronizace souběžných operací pomocí třídy Barrier</span><span class="sxs-lookup"><span data-stu-id="cad30-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
