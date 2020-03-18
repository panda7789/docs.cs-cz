---
title: 'Postupy: Implementace dynamických oddílů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3970566b4e3f51ce538c328d4e69b20ec22ec09b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091423"
---
# <a name="how-to-implement-dynamic-partitions"></a>Postupy: Implementace dynamických oddílů

Následující příklad ukazuje, jak <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> implementovat vlastní, který implementuje dynamické <xref:System.Threading.Tasks.Parallel.ForEach%2A> dělení a lze použít z určitých přetížení a z PLINQ.  
  
## <a name="example"></a>Příklad

Pokaždé, když <xref:System.Collections.IEnumerator.MoveNext%2A> oddíl volá čítače výčtu, čítač výčtu poskytuje oddíl s jedním list element. V případě PLINQ <xref:System.Threading.Tasks.Parallel.ForEach%2A>a , oddíl <xref:System.Threading.Tasks.Task> je instance. Vzhledem k tomu, že požadavky probíhají souběžně ve více vláknech, je synchronizován přístup k aktuálnímu indexu.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Toto je příklad rozdělení bloku, přičemž každý blok se skládá z jednoho prvku. Poskytnutím více prvků najednou, můžete snížit konflikty přes zámek a teoreticky dosáhnout vyššího výkonu. V určitém okamžiku však větší bloky mohou vyžadovat další logiku vyrovnávání zatížení, aby byla všechna vlákna zaneprázdněna, dokud nebude provedena veškerá práce.  
  
## <a name="see-also"></a>Viz také

* [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [Postupy: Implementace rozdělovače pro statické dělení](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
