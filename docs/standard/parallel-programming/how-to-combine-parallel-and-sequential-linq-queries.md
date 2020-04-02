---
title: 'Postupy: Kombinování paralelních a sekvenčních LINQ dotazů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 99c86e17c57a90d2268acb2a32c69bc4a693338a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587999"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="07bca-102">Postupy: Kombinování paralelních a sekvenčních LINQ dotazů</span><span class="sxs-lookup"><span data-stu-id="07bca-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="07bca-103">Tento příklad ukazuje, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jak pomocí metody pokyn PLINQ zpracovat všechny následné operátory v dotazu postupně.</span><span class="sxs-lookup"><span data-stu-id="07bca-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="07bca-104">Přestože sekvenční zpracování je obecně pomalejší než paralelní, někdy je nutné vytvořit správné výsledky.</span><span class="sxs-lookup"><span data-stu-id="07bca-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="07bca-105">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="07bca-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="07bca-106">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="07bca-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07bca-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="07bca-107">Example</span></span>  
 <span data-ttu-id="07bca-108">Následující příklad ukazuje jeden <xref:System.Linq.ParallelEnumerable.AsSequential%2A> scénář, ve kterém je požadováno, a to zachovat řazení, která byla stanovena v předchozí klauzuli dotazu.</span><span class="sxs-lookup"><span data-stu-id="07bca-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07bca-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="07bca-109">Compiling the Code</span></span>  
 <span data-ttu-id="07bca-110">Chcete-li tento kód zkompilovat a spustit, vložte jej do ukázkového projektu [PLINQ,](../../../docs/standard/parallel-programming/plinq-data-sample.md) přidejte řádek pro volání metody z `Main`aplikace a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="07bca-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07bca-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="07bca-111">See also</span></span>

- [<span data-ttu-id="07bca-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="07bca-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
