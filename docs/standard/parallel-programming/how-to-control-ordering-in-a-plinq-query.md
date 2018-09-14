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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa08106126212345bb594cdeabe6e7281cd7b5e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519744"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="71f3a-102">Postupy: Řazení ovládacích prvků v PLINQ dotazu</span><span class="sxs-lookup"><span data-stu-id="71f3a-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="71f3a-103">Tyto příklady znázorňují způsob řazení v dotazu PLINQ s použitím ovládacích prvků <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="71f3a-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="71f3a-104">Tyto příklady jsou primárně určeny k předvedení využití a může nebo nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazů.</span><span class="sxs-lookup"><span data-stu-id="71f3a-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71f3a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="71f3a-105">Example</span></span>  
 <span data-ttu-id="71f3a-106">V následujícím příkladu se zachová, řazení zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="71f3a-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="71f3a-107">To je někdy nezbytné; pro některé operátory dotazu vyžadovat sekvenci seřazeného zdrojového pro správné výsledky.</span><span class="sxs-lookup"><span data-stu-id="71f3a-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="71f3a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="71f3a-108">Example</span></span>  
 <span data-ttu-id="71f3a-109">Následující příklad ukazuje některé operátory, jehož zdrojové sekvence pravděpodobně byl očekáván povolujeme dotazů.</span><span class="sxs-lookup"><span data-stu-id="71f3a-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="71f3a-110">Tyto operátory bude fungovat na Neseřazený pořadí, ale jejich může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="71f3a-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="71f3a-111">Pokud chcete spustit tuto metodu, vložte ho do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="71f3a-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71f3a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="71f3a-112">Example</span></span>  
 <span data-ttu-id="71f3a-113">Následující příklad ukazuje, jak zachovat řazení pro první část dotazu, pak odebrat řazení a zvyšuje výkon klauzule join a pak znovu použít řazení pořadí konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="71f3a-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="71f3a-114">Pokud chcete spustit tuto metodu, vložte ho do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="71f3a-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f3a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71f3a-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="71f3a-116">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="71f3a-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
