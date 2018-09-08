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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8914d3c443971f73e6f3fa366c26567bae60dbe1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135052"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Postupy: Určení možností sloučení v PLINQ
Tento příklad ukazuje postup určení možností sloučení, které budou platit pro všechny následující operátory v dotazu PLINQ. Není nutné explicitně nastavit možnosti sloučení, ale to může zlepšit výkon. Další informace o možnosti sloučení, naleznete v tématu [možností sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
>  V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje chování možnosti sloučení v základní scénář, který obsahuje Neseřazený zdroj a nákladná funkce se vztahuje na každý prvek.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 V případech, kde <xref:System.Linq.ParallelMergeOptions.AutoBuffered> možnost způsobuje nežádoucí zpoždění před první prvek, je vhodné, zkuste <xref:System.Linq.ParallelMergeOptions.NotBuffered> možnost pro získání výsledku prvků rychleji a plynuleji.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelMergeOptions>  
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
