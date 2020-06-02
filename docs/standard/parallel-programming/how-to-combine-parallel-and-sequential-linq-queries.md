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
ms.openlocfilehash: 2bdf074bc2977dc501e0726a52e825c89828565f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289535"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="e30bd-102">Postupy: Kombinování paralelních a sekvenčních LINQ dotazů</span><span class="sxs-lookup"><span data-stu-id="e30bd-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>

<span data-ttu-id="e30bd-103">Tento příklad ukazuje, jak použít <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metodu k instruování PLINQ pro zpracování všech dalších operátorů v dotazu sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="e30bd-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="e30bd-104">I když je sekvenční zpracování často pomalejší než paralelní, někdy je potřeba, abyste naprodukovali správné výsledky.</span><span class="sxs-lookup"><span data-stu-id="e30bd-104">Although sequential processing is often slower than parallel, sometimes it's necessary to produce correct results.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e30bd-105">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="e30bd-105">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e30bd-106">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e30bd-106">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e30bd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e30bd-107">Example</span></span>  
 <span data-ttu-id="e30bd-108">Následující příklad ukazuje jeden scénář, ve kterém <xref:System.Linq.ParallelEnumerable.AsSequential%2A> je třeba zachovat řazení, které bylo vytvořeno v předchozí klauzuli dotazu.</span><span class="sxs-lookup"><span data-stu-id="e30bd-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e30bd-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e30bd-109">Compiling the Code</span></span>  
 <span data-ttu-id="e30bd-110">Chcete-li zkompilovat a spustit tento kód, vložte jej do projektu [ukázkového data pro PLINQ](plinq-data-sample.md) , přidejte řádek pro volání metody z `Main` a stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="e30bd-110">To compile and run this code, paste it into the [PLINQ Data Sample](plinq-data-sample.md) project, add a line to call the method from `Main`, and press **F5**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30bd-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e30bd-111">See also</span></span>

- [<span data-ttu-id="e30bd-112">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e30bd-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
