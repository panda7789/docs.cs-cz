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
ms.openlocfilehash: d38c039fa99433d9476d62c1e96dff7e306fd766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123124"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Postupy: Řazení ovládacích prvků v PLINQ dotazu
Tyto příklady ukazují, jak řídit řazení v dotazu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> PLINQ pomocí metody rozšíření.  
  
> [!WARNING]
> Tyto příklady jsou primárně určeny k předvádění využití a může nebo nemusí běžet rychleji než ekvivalentní sekvenční LINQ na dotazy objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad zachová pořadí zdrojové sekvence. To je někdy nezbytné; Například některé operátory dotazu vyžadují uspořádanou zdrojovou sekvenci k dosažení správných výsledků.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje některé operátory dotazu, jejichž zdrojová sekvence je pravděpodobně očekává, že bude objednáno. Tyto operátory budou pracovat na neuspořádané sekvence, ale mohou způsobit neočekávané výsledky.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkový vzorek dat PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a stiskněte klávesu F5.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachovat řazení pro první část dotazu, potom odeberte řazení zvýšit výkon join klauzule a potom znovu použít řazení na konečné pořadí výsledků.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Chcete-li spustit tuto metodu, vložte ji do třídy PLINQDataSample v projektu [ukázkový vzorek dat PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a stiskněte klávesu F5.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
