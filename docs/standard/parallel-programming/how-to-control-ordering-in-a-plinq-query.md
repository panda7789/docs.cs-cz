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
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44364829"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Postupy: Řazení ovládacích prvků v PLINQ dotazu
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
