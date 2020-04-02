---
title: 'Postupy: Řazení ovládacích prvků v PLINQ dotazu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: 86011cff71fabed5e47e085f91b1759238638c9a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588493"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="c2b5d-102">Postupy: Řazení ovládacích prvků v PLINQ dotazu</span><span class="sxs-lookup"><span data-stu-id="c2b5d-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="c2b5d-103">Tyto příklady ukazují, jak řídit řazení v dotazu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> PLINQ pomocí metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c2b5d-104">Tyto příklady jsou primárně určeny k předvádění využití a může nebo nemusí běžet rychleji než ekvivalentní sekvenční LINQ na dotazy objekty.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2b5d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2b5d-105">Example</span></span>  
 <span data-ttu-id="c2b5d-106">Následující příklad zachová pořadí zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="c2b5d-107">To je někdy nezbytné; Například některé operátory dotazu vyžadují uspořádanou zdrojovou sekvenci k dosažení správných výsledků.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="c2b5d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2b5d-108">Example</span></span>  
 <span data-ttu-id="c2b5d-109">Následující příklad ukazuje některé operátory dotazu, jejichž zdrojová sekvence je pravděpodobně očekává, že bude objednáno.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="c2b5d-110">Tyto operátory budou pracovat na neuspořádané sekvence, ale mohou způsobit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="c2b5d-111">Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkový vzorek dat PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2b5d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2b5d-112">Example</span></span>  
 <span data-ttu-id="c2b5d-113">Následující příklad ukazuje, jak zachovat řazení pro první část dotazu, potom odeberte řazení zvýšit výkon join klauzule a potom znovu použít řazení na konečné pořadí výsledků.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="c2b5d-114">Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkový vzorek dat PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="c2b5d-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b5d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2b5d-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="c2b5d-116">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c2b5d-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
