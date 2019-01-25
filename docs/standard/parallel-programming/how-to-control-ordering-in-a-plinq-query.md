---
title: 'Postupy: Ovládací prvek řazení v dotazu PLINQ'
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
ms.openlocfilehash: 30be9fc661ce05a664f9e901edef621d9de62e34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713441"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Postupy: Ovládací prvek řazení v dotazu PLINQ
Tyto příklady znázorňují způsob řazení v dotazu PLINQ s použitím ovládacích prvků <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> – metoda rozšíření.  
  
> [!WARNING]
>  Tyto příklady jsou primárně určeny k předvedení využití a může nebo nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se zachová, řazení zdrojové sekvence. To je někdy nezbytné; pro některé operátory dotazu vyžadovat sekvenci seřazeného zdrojového pro správné výsledky.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje některé operátory, jehož zdrojové sekvence pravděpodobně byl očekáván povolujeme dotazů. Tyto operátory bude fungovat na Neseřazený pořadí, ale jejich může vést k neočekávaným výsledkům.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Pokud chcete spustit tuto metodu, vložte ho do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stiskněte klávesu F5.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachovat řazení pro první část dotazu, pak odebrat řazení a zvyšuje výkon klauzule join a pak znovu použít řazení pořadí konečný výsledek.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Pokud chcete spustit tuto metodu, vložte ho do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stiskněte klávesu F5.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
