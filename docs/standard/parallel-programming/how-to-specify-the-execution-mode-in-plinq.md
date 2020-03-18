---
title: 'Postupy: Určení režimu spouštění v PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: c602aba6e18f80b007b15cd61dfd2b48a36dd2c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139243"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="165d7-102">Postupy: Určení režimu spouštění v PLINQ</span><span class="sxs-lookup"><span data-stu-id="165d7-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="165d7-103">Tento příklad ukazuje, jak vynutit PLINQ obejít jeho výchozí heuristiky a paralelizovat dotaz bez ohledu na tvar dotazu.</span><span class="sxs-lookup"><span data-stu-id="165d7-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="165d7-104">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="165d7-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="165d7-105">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="165d7-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="165d7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="165d7-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="165d7-107">PLINQ je navržen tak, aby využíval příležitostí pro paralelizaci.</span><span class="sxs-lookup"><span data-stu-id="165d7-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="165d7-108">Však ne všechny dotazy těžit z paralelního provádění.</span><span class="sxs-lookup"><span data-stu-id="165d7-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="165d7-109">Například pokud dotaz obsahuje delegáta jednoho uživatele, který dělá velmi málo práce, dotaz obvykle běží rychleji postupně.</span><span class="sxs-lookup"><span data-stu-id="165d7-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="165d7-110">Důvodem je, že režie podílejí na povolení paralelní spuštění je dražší než zrychlení, které je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="165d7-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="165d7-111">Proto PLINQ není automaticky paralelizovat každý dotaz.</span><span class="sxs-lookup"><span data-stu-id="165d7-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="165d7-112">Nejprve zkoumá tvar dotazu a různé operátory, které jej tvoří.</span><span class="sxs-lookup"><span data-stu-id="165d7-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="165d7-113">Na základě této analýzy PLINQ ve výchozím režimu spuštění se může rozhodnout provést některé nebo všechny dotazu postupně.</span><span class="sxs-lookup"><span data-stu-id="165d7-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="165d7-114">V některých případech však můžete vědět více o dotazu než PLINQ je schopen určit z jeho analýzy.</span><span class="sxs-lookup"><span data-stu-id="165d7-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="165d7-115">Například můžete vědět, že delegát je velmi nákladné a že dotaz bude určitě těžit z paralelizace.</span><span class="sxs-lookup"><span data-stu-id="165d7-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="165d7-116">V takových případech můžete <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> použít metodu <xref:System.Linq.ParallelExecutionMode.ForceParallelism> a zadat hodnotu pokyn PLINQ vždy spustit dotaz jako paralelní.</span><span class="sxs-lookup"><span data-stu-id="165d7-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="165d7-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="165d7-117">Compiling the Code</span></span>  
 <span data-ttu-id="165d7-118">Vyjmout a vložit tento kód do [ukázky dat PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a volání metody z `Main`.</span><span class="sxs-lookup"><span data-stu-id="165d7-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165d7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="165d7-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="165d7-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="165d7-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
