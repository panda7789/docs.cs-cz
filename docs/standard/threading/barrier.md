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
ms.openlocfilehash: 5aa34f7f39f4b9b626bea29372cf984f3cefb361
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138153"
---
# <a name="barrier"></a><span data-ttu-id="b68e2-102">Bariéra</span><span class="sxs-lookup"><span data-stu-id="b68e2-102">Barrier</span></span>

<span data-ttu-id="b68e2-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> je synchronizace primitivní, který umožňuje více podprocesů (označované jako *účastníci*) pracovat současně na algoritmu ve fázích.</span><span class="sxs-lookup"><span data-stu-id="b68e2-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="b68e2-104">Každý účastník provede, dokud nedosáhne bodu bariéry v kódu.</span><span class="sxs-lookup"><span data-stu-id="b68e2-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="b68e2-105">Bariéra představuje konec jedné fáze práce.</span><span class="sxs-lookup"><span data-stu-id="b68e2-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="b68e2-106">Když účastník dosáhne bariéry, blokuje, dokud všichni účastníci nedosáhnou stejné bariéry.</span><span class="sxs-lookup"><span data-stu-id="b68e2-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="b68e2-107">Poté, co všichni účastníci dosáhli bariéry, můžete volitelně vyvolat akci po fázi.</span><span class="sxs-lookup"><span data-stu-id="b68e2-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="b68e2-108">Tuto akci po fázi lze použít k provádění akcí jedním vláknem, zatímco všechna ostatní vlákna jsou stále blokována.</span><span class="sxs-lookup"><span data-stu-id="b68e2-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="b68e2-109">Po provedení akce jsou všichni účastníci odblokováni.</span><span class="sxs-lookup"><span data-stu-id="b68e2-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="b68e2-110">Následující fragment kódu zobrazuje základní bariérový vzor.</span><span class="sxs-lookup"><span data-stu-id="b68e2-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="b68e2-111">Úplný příklad naleznete v [tématu Jak: synchronizovat souběžné operace s Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="b68e2-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="b68e2-112">Přidání a odebrání účastníků</span><span class="sxs-lookup"><span data-stu-id="b68e2-112">Adding and removing participants</span></span>

 <span data-ttu-id="b68e2-113">Při vytváření <xref:System.Threading.Barrier> instance zadejte počet účastníků.</span><span class="sxs-lookup"><span data-stu-id="b68e2-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="b68e2-114">Účastníky můžete také kdykoli dynamicky přidávat nebo odebírat.</span><span class="sxs-lookup"><span data-stu-id="b68e2-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="b68e2-115">Například pokud jeden účastník řeší jeho část problému, můžete uložit výsledek, zastavit provádění <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> v tomto vlákně a volání snížení počtu účastníků v bariéry.</span><span class="sxs-lookup"><span data-stu-id="b68e2-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="b68e2-116">Přidáte-li účastníka <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>voláním , vrátí hodnota určuje aktuální číslo fáze, které může být užitečné pro inicializaci práce nového účastníka.</span><span class="sxs-lookup"><span data-stu-id="b68e2-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="b68e2-117">Rozbité bariéry</span><span class="sxs-lookup"><span data-stu-id="b68e2-117">Broken barriers</span></span>

 <span data-ttu-id="b68e2-118">Zablokování může dojít, pokud jeden účastník nedosáhne bariéry.</span><span class="sxs-lookup"><span data-stu-id="b68e2-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="b68e2-119">Chcete-li se vyhnout těmto zablokování, <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> použijte přetížení metody k určení časového období a token zrušení.</span><span class="sxs-lookup"><span data-stu-id="b68e2-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="b68e2-120">Tato přetížení vrátí logickou hodnotu, kterou může každý účastník zkontrolovat, než bude pokračovat do další fáze.</span><span class="sxs-lookup"><span data-stu-id="b68e2-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="b68e2-121">Výjimky po fázi</span><span class="sxs-lookup"><span data-stu-id="b68e2-121">Post-phase exceptions</span></span>

 <span data-ttu-id="b68e2-122">Pokud delegát po fázi vyvolá výjimku, je zabalen <xref:System.Threading.BarrierPostPhaseException> do objektu, který je pak rozšířen všem účastníkům.</span><span class="sxs-lookup"><span data-stu-id="b68e2-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="b68e2-123">Bariéra versus ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="b68e2-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="b68e2-124">Bariéry jsou zvláště užitečné, když vlákna provádějí více fází ve smyčkách.</span><span class="sxs-lookup"><span data-stu-id="b68e2-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="b68e2-125">Pokud váš kód vyžaduje pouze jednu nebo dvě <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> fáze práce, zvažte, zda použít objekty s libovolným druhem implicitního spojení, včetně:</span><span class="sxs-lookup"><span data-stu-id="b68e2-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="b68e2-126">Další informace naleznete v [tématu Chaining Tasks pomocí pokračování úlohy](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="b68e2-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68e2-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b68e2-127">See also</span></span>

- [<span data-ttu-id="b68e2-128">Dělení objektů a funkcí na vlákna</span><span class="sxs-lookup"><span data-stu-id="b68e2-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="b68e2-129">Postup: synchronizace souběžných operací s bariérou</span><span class="sxs-lookup"><span data-stu-id="b68e2-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
