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
ms.openlocfilehash: 4c04afb23a168a9cff60962bd5a75a65e3ebca4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134184"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="f9f62-102">Postupy: Kombinování paralelních a sekvenčních LINQ dotazů</span><span class="sxs-lookup"><span data-stu-id="f9f62-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="f9f62-103">Tento příklad ukazuje, jak použít metodu <xref:System.Linq.ParallelEnumerable.AsSequential%2A> k tomu, aby PLINQ zpracovával všechny následné operátory v dotazu sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="f9f62-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="f9f62-104">I když je sekvenční zpracování obecně pomalejší než paralelní, někdy je potřeba, abyste naprodukovali správné výsledky.</span><span class="sxs-lookup"><span data-stu-id="f9f62-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f9f62-105">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="f9f62-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="f9f62-106">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="f9f62-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f62-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f62-107">Example</span></span>  
 <span data-ttu-id="f9f62-108">Následující příklad ukazuje jeden scénář, ve kterém je vyžadováno <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, a to proto, aby bylo zachováno řazení, které bylo vytvořeno v předchozí klauzuli dotazu.</span><span class="sxs-lookup"><span data-stu-id="f9f62-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f9f62-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f9f62-109">Compiling the Code</span></span>  
 <span data-ttu-id="f9f62-110">Chcete-li zkompilovat a spustit tento kód, vložte jej do projektu [ukázkového data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) , přidejte řádek pro volání metody z `Main`a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="f9f62-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f62-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9f62-111">See also</span></span>

- [<span data-ttu-id="f9f62-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f9f62-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
