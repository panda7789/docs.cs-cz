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
ms.openlocfilehash: 8bffc25cb5c3ae3671fdf6018158b81549c360e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-dynamic-partitions"></a>Postupy: Implementace dynamických oddílů
Následující příklad ukazuje, jak implementovat vlastní <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , implementuje dynamické rozdělení a dá se použít z určité přetížení <xref:System.Threading.Tasks.Parallel.ForEach%2A> a PLINQ.  
  
## <a name="example"></a>Příklad  
 Pokaždé, když oddíl volá <xref:System.Collections.IEnumerator.MoveNext%2A> na enumerátor, enumerátor poskytuje oddílu jeden element ze seznamu. V případě PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A>, zda je oddíl <xref:System.Threading.Tasks.Task> instance. Protože požadavky se dějí souběžně na více vláken, přístup k aktuální index je synchronizován.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Toto je příklad bloku rozdělení do oddílů s každého bloku, který se skládá z jeden element. Tím, že poskytuje další prvky současně, můžete snížit boj zámek a teoreticky dosáhnout vyšší výkon. Ale v určitém okamžiku větší bloky vyžadovat další vyrovnávání zátěže abychom zachovali všechna vlákna zaneprázdněný, dokud všechny práci.  
  
## <a name="see-also"></a>Viz také  
 [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Postupy: Implementace rozdělovače pro statické dělení](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
