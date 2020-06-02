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
ms.openlocfilehash: 197e71cf4f00c98891e58e5f72974c0ec407e6ce
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288443"
---
# <a name="how-to-implement-dynamic-partitions"></a>Postupy: Implementace dynamických oddílů

Následující příklad ukazuje, jak implementovat vlastní <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , který implementuje dynamické dělení a lze jej použít z určitých přetížení <xref:System.Threading.Tasks.Parallel.ForEach%2A> a z PLINQ.  
  
## <a name="example"></a>Příklad

Pokaždé, když oddíl volá <xref:System.Collections.IEnumerator.MoveNext%2A> na enumerátor, enumerátor poskytuje oddíl s jedním seznamem elementů. V případě PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A> je oddíl <xref:System.Threading.Tasks.Task> instancí. Vzhledem k tomu, že žádosti jsou souběžně na více vláknech, je přístup k aktuálnímu indexu synchronizovaný.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Toto je příklad dělení bloků dat s každým blokem, který se skládá z jednoho prvku. Poskytnutím více prvků v čase můžete snížit kolizí přes zámek a teoreticky dosáhnout rychlejšího výkonu. V některých případech ale větší počet bloků může vyžadovat další logiku vyrovnávání zatížení, aby všechna vlákna byla zaneprázdněná, dokud neproběhne veškerá práce.  
  
## <a name="see-also"></a>Viz také

* [Vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md)
* [Postupy: Implementace rozdělovače pro statické dělení](how-to-implement-a-partitioner-for-static-partitioning.md)
