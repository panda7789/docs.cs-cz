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
ms.openlocfilehash: 7416f2f9c200d687d3f2c1f14b01cafdb48f85b1
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988186"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Postupy: Řazení ovládacích prvků v PLINQ dotazu
Tyto příklady ukazují, jak řídit řazení v PLINQ dotazu pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> metody rozšíření.  
  
> [!WARNING]
> Tyto příklady jsou primárně určeny k předvedení používání a mohou nebo nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad zachovává řazení zdrojové sekvence. V některých případech je to nezbytné. Například některé operátory dotazů vyžadují seřazenou zdrojovou sekvenci, která vytváří správné výsledky.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje některé operátory dotazů, jejichž zdrojová sekvence je pravděpodobně objednána. Tyto operátory budou fungovat na neseřazených sekvencích, ale mohou způsobit neočekávané výsledky.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkových dat pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a stiskněte klávesu F5.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachovat řazení první části dotazu, pak odebrat řazení pro zvýšení výkonu klauzule JOIN a pak znovu použít řazení na konečné pořadí výsledků.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkových dat pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a stiskněte klávesu F5.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
