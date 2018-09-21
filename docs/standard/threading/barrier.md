---
title: Bariéra
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbbf7055a250ae7fa630097f3014a6420228fed3
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485137"
---
# <a name="barrier"></a><span data-ttu-id="e4b6b-102">Bariéra</span><span class="sxs-lookup"><span data-stu-id="e4b6b-102">Barrier</span></span>

<span data-ttu-id="e4b6b-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> je primitiv synchronizace, která umožňuje více vláken (označované jako *účastníci*) pracovat souběžně na algoritmus ve fázích.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="e4b6b-104">Každý účastník opakuje, dokud se nedosáhne barrier bod v kódu.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="e4b6b-105">Odbourejte překážky bránící představuje konec jednu fázi práce.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="e4b6b-106">Odbourejte překážky bránící dosáhne účastníka blokuje, dokud všichni účastníci dosáhnou této bariéry stejné.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="e4b6b-107">Jakmile všichni účastníci dosáhnou této bariéry, můžete volitelně vyvolat akce po fázi.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="e4b6b-108">Tuto fázi po akci můžete využívat k provádění akcí jedním vláknem a když jsou všechny ostatní vlákna budou i nadále zablokované.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="e4b6b-109">Po spuštění akce jsou všechny odblokované účastníci.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="e4b6b-110">Následující fragment kódu ukazuje základní barrier vzor.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="e4b6b-111">Kompletní příklad naleznete v tématu [postupy: synchronizace souběh operací pomocí bariéry](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="e4b6b-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="e4b6b-112">Přidávání a odebírání účastníků</span><span class="sxs-lookup"><span data-stu-id="e4b6b-112">Adding and removing participants</span></span>

 <span data-ttu-id="e4b6b-113">Když vytvoříte <xref:System.Threading.Barrier> instance, zadejte počet účastníků.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="e4b6b-114">Můžete také přidat nebo odebrat účastníci dynamicky kdykoli.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="e4b6b-115">Například, pokud jeden účastník řeší jeho část problému, můžete uložit výsledek, zastavit provádění na vlákno a volat <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> se sníží počet účastníků v odbourejte překážky bránící.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="e4b6b-116">Když přidáte účastníka voláním <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, návratová hodnota určuje číslo aktuální fázi, který může být užitečné, pokud chcete inicializovat pracovní nového účastníka.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="e4b6b-117">Nefunkční překážek</span><span class="sxs-lookup"><span data-stu-id="e4b6b-117">Broken barriers</span></span>

 <span data-ttu-id="e4b6b-118">Zablokování může dojít, pokud jeden účastník nepodaří spojit odbourejte překážky bránící.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="e4b6b-119">Aby se zabránilo tyto zablokování, použijte přetížení <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> metoda zadat časový limit a token zrušení.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="e4b6b-120">Tato přetížení návratový logická hodnota, která každých účastníka můžete zkontrolovat dříve, než bude pokračovat do další fáze.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="e4b6b-121">Po fázi výjimky</span><span class="sxs-lookup"><span data-stu-id="e4b6b-121">Post-phase exceptions</span></span>

 <span data-ttu-id="e4b6b-122">Pokud po fázi delegáta vyvolá výjimku, je obalen <xref:System.Threading.BarrierPostPhaseException> objekt, který je pak šířený do všichni účastníci.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="e4b6b-123">Barrier oproti ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="e4b6b-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="e4b6b-124">Vlákna provádění více fázích ve smyčkách jsou zvláště užitečné překážek.</span><span class="sxs-lookup"><span data-stu-id="e4b6b-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="e4b6b-125">Pokud váš kód vyžaduje pouze jednu nebo dvě fáze práce, zvažte, jestli se má použít <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty s jakýmkoli implicitní spojení, včetně:</span><span class="sxs-lookup"><span data-stu-id="e4b6b-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="e4b6b-126">Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování používání](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="e4b6b-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b6b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4b6b-127">See also</span></span>

- [<span data-ttu-id="e4b6b-128">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="e4b6b-128">Threading objects and features</span></span>](threading-objects-and-features.md)  
- [<span data-ttu-id="e4b6b-129">Postupy: synchronizace souběh operací pomocí bariéry</span><span class="sxs-lookup"><span data-stu-id="e4b6b-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
