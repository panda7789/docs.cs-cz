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
ms.openlocfilehash: b2d46264113cb4c961f6c4b971b5986bdd9eb6a7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180962"
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
