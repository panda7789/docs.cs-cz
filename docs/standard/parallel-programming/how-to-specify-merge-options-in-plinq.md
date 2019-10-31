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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139266"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Postupy: Určení možností sloučení v PLINQ
Tento příklad ukazuje, jak určit možnosti sloučení, které budou použity pro všechny následné operátory v dotazu PLINQ. Explicitně není nutné nastavovat možnosti sloučení, ale v takovém případě může dojít ke zvýšení výkonu. Další informace o možnostech sloučení naleznete v tématu [možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje chování možností sloučení v základním scénáři, který má neuspořádaný zdroj a aplikuje nákladný funkce na každý prvek.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 V případech, kdy <xref:System.Linq.ParallelMergeOptions.AutoBuffered> možnost dochází k nežádoucí latenci před tím, než se první prvek vrátí, vyzkoušejte možnost <xref:System.Linq.ParallelMergeOptions.NotBuffered>, která vrátí prvky výsledků rychleji a hladce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelMergeOptions>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
