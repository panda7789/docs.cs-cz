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
ms.openlocfilehash: 84667fa1fbe2966c580d9c6d32e52ed686af7bb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288118"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Postupy: Určení možností sloučení v PLINQ
Tento příklad ukazuje, jak určit možnosti sloučení, které budou použity pro všechny následné operátory v dotazu PLINQ. Explicitně není nutné nastavovat možnosti sloučení, ale v takovém případě může dojít ke zvýšení výkonu. Další informace o možnostech sloučení naleznete v tématu [možnosti sloučení v PLINQ](merge-options-in-plinq.md).  
  
> [!WARNING]
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje chování možností sloučení v základním scénáři, který má neuspořádaný zdroj a aplikuje nákladný funkce na každý prvek.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 V případech, kdy u <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Možnosti dojde k nežádoucí latenci před dosažením prvního prvku, zkuste <xref:System.Linq.ParallelMergeOptions.NotBuffered> možnost vracet prvky výsledků rychleji a hladce.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelMergeOptions>
- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
