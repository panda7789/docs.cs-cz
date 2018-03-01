---
title: "Postupy: Implementace dynamických oddílů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b08c387c9b10a9d6fa8728a7fce87a7894a37fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
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
