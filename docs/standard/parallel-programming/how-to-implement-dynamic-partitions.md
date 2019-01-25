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
ms.openlocfilehash: 792488e53ffb7f870e21fdd1ad3ef94bf0303b1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720233"
---
# <a name="how-to-implement-dynamic-partitions"></a>Postupy: Implementace dynamických oddílů
Následující příklad ukazuje, jak implementovat vlastní <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , který implementuje dynamické dělení na oddíly a je možné z určité přetížení <xref:System.Threading.Tasks.Parallel.ForEach%2A> a PLINQ.  
  
## <a name="example"></a>Příklad  
 Pokaždé, když volá oddílu <xref:System.Collections.IEnumerator.MoveNext%2A> v čítači výčtu, enumerátor obsahuje oddíl s elementem jeden seznam. V případě PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A>, je oddíl <xref:System.Threading.Tasks.Task> instance. Protože požadavky se dějí souběžně na několika vláknech, se synchronizuje přístup k aktuální index.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Toto je příklad bloků dělení každý blok, který se skládá z jednoho prvku. Tím, že poskytuje další elementy v čase, můžete omezit kolize přes zámek a teoreticky dosáhnout vyššího výkonu. Ale v určitém okamžiku větší bloky vyžadovat další logiku vyrovnávání zatížení aby bylo možné udržovat zaneprázdněný všechna vlákna, dokud se provádí veškerou práci.  
  
## <a name="see-also"></a>Viz také:

- [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Postupy: Implementace rozdělovače pro statické dělení](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
