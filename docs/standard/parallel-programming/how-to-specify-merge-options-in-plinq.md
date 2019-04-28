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
ms.openlocfilehash: 87079337ae3cea81dbb4aab13ec2043b74498d9a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672702"
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
