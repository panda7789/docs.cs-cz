---
title: "Postupy: Řazení ovládacích prvků v PLINQ dotazu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3aef90c1a1160905662f93a83d6536f6d804b179
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="3afc0-102">Postupy: Řazení ovládacích prvků v PLINQ dotazu</span><span class="sxs-lookup"><span data-stu-id="3afc0-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="3afc0-103">Tyto příklady ukazují, jak řídit pořadí v PLINQ dotazu pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3afc0-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3afc0-104">Tyto příklady jsou primárně určené k předvedení využití a může nebo nemusí běžet rychleji než ekvivalentní sekvenčních LINQ na objekty dotazy.</span><span class="sxs-lookup"><span data-stu-id="3afc0-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3afc0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3afc0-105">Example</span></span>  
 <span data-ttu-id="3afc0-106">Následující příklad zachová řazení zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="3afc0-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="3afc0-107">To je někdy nutné; třeba vyžadovat některé operátory dotazu už seřazený zdroj pořadí pro správné výsledky.</span><span class="sxs-lookup"><span data-stu-id="3afc0-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="3afc0-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3afc0-108">Example</span></span>  
 <span data-ttu-id="3afc0-109">Následující příklad ukazuje některé operátory, jejichž zdrojové sekvence je pravděpodobně očekává mají být sdruženy do dotazů.</span><span class="sxs-lookup"><span data-stu-id="3afc0-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="3afc0-110">Tyto operátory budou fungovat na neuspořádaný pořadí, ale jejich může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="3afc0-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="3afc0-111">Chcete-li spustit tuto metodu, vložte jej do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="3afc0-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3afc0-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3afc0-112">Example</span></span>  
 <span data-ttu-id="3afc0-113">Následující příklad ukazuje, jak zachovat řazení pro první část dotazu, pak odeberte řazení a zvyšuje výkon klauzule join a poté znovu přidat konečný výsledek pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="3afc0-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="3afc0-114">Chcete-li spustit tuto metodu, vložte jej do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="3afc0-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3afc0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3afc0-115">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="3afc0-116">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3afc0-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
