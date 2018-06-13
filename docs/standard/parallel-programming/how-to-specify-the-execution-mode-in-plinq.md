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
ms.openlocfilehash: ebea62f33c5df252dd73a0708f31612cd2998728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580936"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="50012-102">Postupy: Určení režimu spouštění v PLINQ</span><span class="sxs-lookup"><span data-stu-id="50012-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="50012-103">Tento příklad ukazuje, jak vynutit PLINQ obejití výchozí heuristiky a paralelní dotaz bez ohledu na tvar dotazu.</span><span class="sxs-lookup"><span data-stu-id="50012-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="50012-104">Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="50012-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="50012-105">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="50012-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50012-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="50012-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="50012-107">PLINQ je navržen tak, aby využil příležitosti pro paralelizace.</span><span class="sxs-lookup"><span data-stu-id="50012-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="50012-108">Ne všechny dotazy však těžit z paralelní provádění.</span><span class="sxs-lookup"><span data-stu-id="50012-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="50012-109">Například pokud dotaz obsahuje delegát jednoho uživatele, který nemá uživatele příliš mnoho zásahů, se obvykle spustí dotaz rychleji postupně.</span><span class="sxs-lookup"><span data-stu-id="50012-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="50012-110">Je to proto, že režie spojená s povolením paralelního spuštění je větší než zrychlení, který byl získán.</span><span class="sxs-lookup"><span data-stu-id="50012-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="50012-111">Proto PLINQ není paralelní automaticky každých dotazu.</span><span class="sxs-lookup"><span data-stu-id="50012-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="50012-112">Nejprve zkontroluje tvar dotazu a různé operátory, které ji tvoří.</span><span class="sxs-lookup"><span data-stu-id="50012-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="50012-113">Na základě této analýzy PLINQ ve výchozím režimu zpracování rozhodnout postupně provést některé nebo všechny dotazu.</span><span class="sxs-lookup"><span data-stu-id="50012-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="50012-114">Ale v některých případech může vědět více o dotazu než PLINQ je možné určit, ze své analýza.</span><span class="sxs-lookup"><span data-stu-id="50012-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="50012-115">Můžete například vědět, že delegát je velmi náročná a aby dotaz výborný využívat paralelizace.</span><span class="sxs-lookup"><span data-stu-id="50012-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="50012-116">V takových případech můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metoda a zadejte <xref:System.Linq.ParallelExecutionMode.ForceParallelism> hodnotu vždy spusťte dotaz paralelně.</span><span class="sxs-lookup"><span data-stu-id="50012-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50012-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="50012-117">Compiling the Code</span></span>  
 <span data-ttu-id="50012-118">Vyjmout a vložit tento kód do [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a volat metodu z `Main`.</span><span class="sxs-lookup"><span data-stu-id="50012-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50012-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="50012-119">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [<span data-ttu-id="50012-120">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="50012-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
