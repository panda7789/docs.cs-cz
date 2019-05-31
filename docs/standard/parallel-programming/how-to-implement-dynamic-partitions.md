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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5719c6afc1c5efc6138f0a4931d1725a6f20909a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424047"
---
# <a name="how-to-implement-dynamic-partitions"></a>Postupy: Implementace dynamických oddílů

Následující příklad ukazuje, jak implementovat vlastní <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , který implementuje dynamické dělení na oddíly a je možné z určité přetížení <xref:System.Threading.Tasks.Parallel.ForEach%2A> a PLINQ.  
  
## <a name="example"></a>Příklad

Pokaždé, když volá oddílu <xref:System.Collections.IEnumerator.MoveNext%2A> v čítači výčtu, enumerátor obsahuje oddíl s elementem jeden seznam. V případě PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A>, je oddíl <xref:System.Threading.Tasks.Task> instance. Protože požadavky se dějí souběžně na několika vláknech, se synchronizuje přístup k aktuální index.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Toto je příklad bloků dělení každý blok, který se skládá z jednoho prvku. Tím, že poskytuje další elementy v čase, můžete omezit kolize přes zámek a teoreticky dosáhnout vyššího výkonu. Ale v určitém okamžiku větší bloky vyžadovat další logiku vyrovnávání zatížení aby bylo možné udržovat zaneprázdněný všechna vlákna, dokud se provádí veškerou práci.  
  
## <a name="see-also"></a>Viz také:

* [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [Postupy: Implementace rozdělovače pro statické dělení](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
