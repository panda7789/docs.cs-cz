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
ms.openlocfilehash: f035dbcd5091d81a3cce3b9e9e683d836fe84bb7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635811"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="4db5b-102">Postupy: Určení režimu spouštění v PLINQ</span><span class="sxs-lookup"><span data-stu-id="4db5b-102">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="4db5b-103">Tento příklad ukazuje, jak vynutit PLINQ obejít jeho výchozí heuristiky a paralelizovat dotaz bez ohledu na tvar dotazu.</span><span class="sxs-lookup"><span data-stu-id="4db5b-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4db5b-104">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="4db5b-104">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="4db5b-105">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="4db5b-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4db5b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4db5b-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="4db5b-107">PLINQ je navržen tak, aby využíval příležitostí pro paralelizaci.</span><span class="sxs-lookup"><span data-stu-id="4db5b-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="4db5b-108">Však ne všechny dotazy těžit z paralelního provádění.</span><span class="sxs-lookup"><span data-stu-id="4db5b-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="4db5b-109">Například pokud dotaz obsahuje delegáta jednoho uživatele, který dělá málo práce, dotaz obvykle běží rychleji postupně.</span><span class="sxs-lookup"><span data-stu-id="4db5b-109">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="4db5b-110">Sekvenční spuštění je rychlejší, protože režie, která se podílí na povolení paralelního spuštění, je dražší než získané zrychlení.</span><span class="sxs-lookup"><span data-stu-id="4db5b-110">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="4db5b-111">Proto PLINQ není automaticky paralelizovat každý dotaz.</span><span class="sxs-lookup"><span data-stu-id="4db5b-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="4db5b-112">Nejprve zkoumá tvar dotazu a různé operátory, které jej tvoří.</span><span class="sxs-lookup"><span data-stu-id="4db5b-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="4db5b-113">Na základě této analýzy PLINQ ve výchozím režimu spuštění se může rozhodnout provést některé nebo všechny dotazu postupně.</span><span class="sxs-lookup"><span data-stu-id="4db5b-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="4db5b-114">V některých případech však můžete vědět více o dotazu než PLINQ je schopen určit z jeho analýzy.</span><span class="sxs-lookup"><span data-stu-id="4db5b-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="4db5b-115">Například můžete vědět, že delegát je nákladné a že dotaz bude určitě těžit z paralelizace.</span><span class="sxs-lookup"><span data-stu-id="4db5b-115">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="4db5b-116">V takových případech můžete <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> použít metodu <xref:System.Linq.ParallelExecutionMode.ForceParallelism> a zadat hodnotu pokyn PLINQ vždy spustit dotaz jako paralelní.</span><span class="sxs-lookup"><span data-stu-id="4db5b-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4db5b-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4db5b-117">Compiling the Code</span></span>  
 <span data-ttu-id="4db5b-118">Vyjmout a vložit tento kód do [ukázky dat PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a volání metody z `Main`.</span><span class="sxs-lookup"><span data-stu-id="4db5b-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db5b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4db5b-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="4db5b-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4db5b-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
