---
title: 'Postupy: Určení možností sloučení v PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 40abe2f101f6fa23d804ef30e27d642a36908196
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139266"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Postupy: Určení možností sloučení v PLINQ
Tento příklad ukazuje, jak určit možnosti sloučení, které se budou vztahovat na všechny následné operátory v dotazu PLINQ. Není třeba explicitně nastavit možnosti sloučení, ale to může zlepšit výkon. Další informace o možnostech sloučení naleznete [v tématu Sloučit možnosti v plinq](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
> Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu. Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje chování možností sloučení v základním scénáři, který má neuspořádaný zdroj a použije nákladné funkce pro každý prvek.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 V případech, <xref:System.Linq.ParallelMergeOptions.AutoBuffered> kdy možnost vznikne nežádoucí latence před první prvek <xref:System.Linq.ParallelMergeOptions.NotBuffered> je výnosný, zkuste možnost výnos u datovat prvky výsledku rychleji a plynuleji.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelMergeOptions>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
