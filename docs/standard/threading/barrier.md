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
ms.openlocfilehash: 864571262d1c9c060235840424542856187341df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584295"
---
# <a name="barrier-net-framework"></a><span data-ttu-id="aa91d-102">Bariéra [.NET Framework]</span><span class="sxs-lookup"><span data-stu-id="aa91d-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="aa91d-103">A *barrier* je uživatelem definované synchronizaci primitivní umožňující více vláken (označované jako *účastníky*) pro práci současně na algoritmus ve fázích.</span><span class="sxs-lookup"><span data-stu-id="aa91d-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="aa91d-104">Každý účastník, provede, dokud nebude dosaženo bodem bariéry v kódu.</span><span class="sxs-lookup"><span data-stu-id="aa91d-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="aa91d-105">Bariéry představuje konec jednou z fází práce.</span><span class="sxs-lookup"><span data-stu-id="aa91d-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="aa91d-106">Když účastník dosáhne bariéry, zablokuje, dokud všichni účastníci dosáhli stejné bariéry.</span><span class="sxs-lookup"><span data-stu-id="aa91d-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="aa91d-107">Po všichni účastníci dosáhli bariéry, můžete případně vyvolat po fáze akce.</span><span class="sxs-lookup"><span data-stu-id="aa91d-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="aa91d-108">Tato fáze po akce slouží k provádění akcí podle jedním vláknem a při jiná vlákna jsou stále zablokované.</span><span class="sxs-lookup"><span data-stu-id="aa91d-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="aa91d-109">Po provedení akce, jsou všechny odblokuje jednotlivými účastníky.</span><span class="sxs-lookup"><span data-stu-id="aa91d-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="aa91d-110">Následující fragment kódu ukazuje základní bariéry vzor.</span><span class="sxs-lookup"><span data-stu-id="aa91d-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="aa91d-111">Úplný příklad najdete v tématu [postupy: synchronizace souběh operací pomocí bariéry](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="aa91d-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="aa91d-112">Přidávání a odebírání účastníky</span><span class="sxs-lookup"><span data-stu-id="aa91d-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="aa91d-113">Při vytváření <xref:System.Threading.Barrier>, zadejte počet účastníky.</span><span class="sxs-lookup"><span data-stu-id="aa91d-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="aa91d-114">Můžete také přidat nebo odebrat účastníky dynamicky kdykoli.</span><span class="sxs-lookup"><span data-stu-id="aa91d-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="aa91d-115">Například pokud jeden účastník řeší jeho součástí problém, můžete uložit výsledek zastavit provádění na vláken a volání <xref:System.Threading.Barrier.RemoveParticipant%2A> se sníží počet účastníků bariéry.</span><span class="sxs-lookup"><span data-stu-id="aa91d-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="aa91d-116">Když přidáte účastník voláním <xref:System.Threading.Barrier.AddParticipant%2A>, návratová hodnota určuje číslo aktuální fáze, které můžou být užitečné, chcete-li inicializovat pracovní nového člena.</span><span class="sxs-lookup"><span data-stu-id="aa91d-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="aa91d-117">Přerušený překážek</span><span class="sxs-lookup"><span data-stu-id="aa91d-117">Broken Barriers</span></span>  
 <span data-ttu-id="aa91d-118">Blokování může dojít, pokud jeden účastník nepodaří spojit bariéry.</span><span class="sxs-lookup"><span data-stu-id="aa91d-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="aa91d-119">Abyste se vyhnuli tyto zablokování, použijte přetížení <xref:System.Threading.Barrier.SignalAndWait%2A> metoda a zadat časový limit a token zrušení.</span><span class="sxs-lookup"><span data-stu-id="aa91d-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="aa91d-120">Tyto návratové přetížení logická hodnota, která každý účastník můžete zkontrolovat dříve, než se i nadále v další fázi.</span><span class="sxs-lookup"><span data-stu-id="aa91d-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="aa91d-121">Po první fáze výjimky</span><span class="sxs-lookup"><span data-stu-id="aa91d-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="aa91d-122">Pokud po fáze delegát vyvolá výjimku, je uzavřen do <xref:System.Threading.BarrierPostPhaseException> objekt, který je pak se rozšíří všichni účastníci.</span><span class="sxs-lookup"><span data-stu-id="aa91d-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="aa91d-123">Barrier Versus ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="aa91d-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="aa91d-124">Překážek jsou zvláště užitečné, když vláken provádění více fáze v smyčky.</span><span class="sxs-lookup"><span data-stu-id="aa91d-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="aa91d-125">Pokud váš kód vyžaduje pouze jednu nebo dvě fáze práce, zvažte použití <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty s jakýmkoli implicitní připojení, včetně:</span><span class="sxs-lookup"><span data-stu-id="aa91d-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="aa91d-126">Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování pomocí](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="aa91d-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa91d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa91d-127">See Also</span></span>  
 [<span data-ttu-id="aa91d-128">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="aa91d-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="aa91d-129">Postupy: Synchronizace souběžných operací pomocí třídy Barrier</span><span class="sxs-lookup"><span data-stu-id="aa91d-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
