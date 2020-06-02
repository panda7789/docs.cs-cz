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
ms.openlocfilehash: 80e199d75471eba219f1f3da12d307b6cd1d90cf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285453"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="a307f-102">Postupy: Řazení ovládacích prvků v PLINQ dotazu</span><span class="sxs-lookup"><span data-stu-id="a307f-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="a307f-103">Tyto příklady ukazují, jak řídit řazení v PLINQ dotazu pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a307f-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a307f-104">Tyto příklady jsou primárně určeny k předvedení používání a mohou nebo nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotazy.</span><span class="sxs-lookup"><span data-stu-id="a307f-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a307f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a307f-105">Example</span></span>  
 <span data-ttu-id="a307f-106">Následující příklad zachovává řazení zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="a307f-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="a307f-107">V některých případech je to nezbytné. Například některé operátory dotazů vyžadují seřazenou zdrojovou sekvenci, která vytváří správné výsledky.</span><span class="sxs-lookup"><span data-stu-id="a307f-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="a307f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a307f-108">Example</span></span>  
 <span data-ttu-id="a307f-109">Následující příklad ukazuje některé operátory dotazů, jejichž zdrojová sekvence je pravděpodobně objednána.</span><span class="sxs-lookup"><span data-stu-id="a307f-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="a307f-110">Tyto operátory budou fungovat na neseřazených sekvencích, ale mohou způsobit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="a307f-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="a307f-111">Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkových dat pro PLINQ](plinq-data-sample.md) a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="a307f-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a307f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a307f-112">Example</span></span>  
 <span data-ttu-id="a307f-113">Následující příklad ukazuje, jak zachovat řazení první části dotazu, pak odebrat řazení pro zvýšení výkonu klauzule JOIN a pak znovu použít řazení na konečné pořadí výsledků.</span><span class="sxs-lookup"><span data-stu-id="a307f-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="a307f-114">Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkových dat pro PLINQ](plinq-data-sample.md) a stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="a307f-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a307f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a307f-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="a307f-116">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a307f-116">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
