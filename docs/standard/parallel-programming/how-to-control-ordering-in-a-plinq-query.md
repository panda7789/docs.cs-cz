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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Postupy: Řazení ovládacích prvků v PLINQ dotazu
Tyto příklady ukazují, jak řídit pořadí v PLINQ dotazu pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> metoda rozšíření.  
  
> [!WARNING]
>  Tyto příklady jsou primárně určené k předvedení využití a může nebo nemusí běžet rychleji než ekvivalentní sekvenčních LINQ na objekty dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad zachová řazení zdrojové sekvence. To je někdy nutné; třeba vyžadovat některé operátory dotazu už seřazený zdroj pořadí pro správné výsledky.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje některé operátory, jejichž zdrojové sekvence je pravděpodobně očekává mají být sdruženy do dotazů. Tyto operátory budou fungovat na neuspořádaný pořadí, ale jejich může vést k neočekávaným výsledkům.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Chcete-li spustit tuto metodu, vložte jej do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stisknutím klávesy F5.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachovat řazení pro první část dotazu, pak odeberte řazení a zvyšuje výkon klauzule join a poté znovu přidat konečný výsledek pořadí řazení.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Chcete-li spustit tuto metodu, vložte jej do PLINQDataSample v [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu a stisknutím klávesy F5.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
