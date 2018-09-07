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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85731b991399e92297d6109a3000c1e345e02f6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087204"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="48895-102">Postupy: Určení režimu spouštění v PLINQ</span><span class="sxs-lookup"><span data-stu-id="48895-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="48895-103">Tento příklad ukazuje, jak k vynucení PLINQ paralelizovat dotaz bez ohledu na to, na tvar dotazu a obejít své výchozí heuristické metody.</span><span class="sxs-lookup"><span data-stu-id="48895-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="48895-104">V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům.</span><span class="sxs-lookup"><span data-stu-id="48895-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="48895-105">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="48895-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48895-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="48895-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="48895-107">PLINQ je navržená ke zneužití příležitosti pro paralelizaci.</span><span class="sxs-lookup"><span data-stu-id="48895-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="48895-108">Ale ne všechny dotazy výhod paralelního provádění.</span><span class="sxs-lookup"><span data-stu-id="48895-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="48895-109">Například pokud dotaz obsahuje jeden uživatelský delegát, který nemá příliš mnoho zásahů, dotaz bude obvykle fungovat rychleji postupně.</span><span class="sxs-lookup"><span data-stu-id="48895-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="48895-110">Je to proto dražší než zrychlení, která se získá je režie spojená s povolením paralelního spuštění.</span><span class="sxs-lookup"><span data-stu-id="48895-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="48895-111">Proto PLINQ paralelní provádění automaticky každého dotazu.</span><span class="sxs-lookup"><span data-stu-id="48895-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="48895-112">Nejprve zkontroluje tvar dotaz a různé operátory, které ho tvoří.</span><span class="sxs-lookup"><span data-stu-id="48895-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="48895-113">Na základě této analýzy, PLINQ ve výchozím režimu zpracování může rozhodnout provést některé nebo všechny dotaz sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="48895-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="48895-114">Ale v některých případech může vědět více o dotazu než PLINQ je schopna určit z jejich analýzu.</span><span class="sxs-lookup"><span data-stu-id="48895-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="48895-115">Může například vědět, že delegát je velmi náročná a, že dotaz bude určitě těžit z paralelního zpracování.</span><span class="sxs-lookup"><span data-stu-id="48895-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="48895-116">V takovém případě můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metodu a zadejte <xref:System.Linq.ParallelExecutionMode.ForceParallelism> hodnotu k vynucení PLINQ dotaz vždy spustit paralelně.</span><span class="sxs-lookup"><span data-stu-id="48895-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48895-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="48895-117">Compiling the Code</span></span>  
 <span data-ttu-id="48895-118">Vyjmout a vložit tento kód do [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a volejte metodu z `Main`.</span><span class="sxs-lookup"><span data-stu-id="48895-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48895-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48895-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
- [<span data-ttu-id="48895-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="48895-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
