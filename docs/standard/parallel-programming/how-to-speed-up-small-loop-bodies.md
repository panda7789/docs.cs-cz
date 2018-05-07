---
title: 'Postupy: Zrychlení malých smyček'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bff41416dd2263c185cc94de045b2c8a26ea194d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Postupy: Zrychlení malých smyček
Když <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčky má malé tělo, jako například může pomaleji než ekvivalentní sekvenční smyčka, proveďte [pro](~/docs/csharp/language-reference/keywords/for.md) smyčky v jazyce C# a [pro](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) v jazyce Visual Basic. Pomalejší výkon je způsobená režie spojená s dělení dat a náklady na vyvolání delegáta na každé iteraci smyčky. Chcete-li vyřešit takových scénářů <xref:System.Collections.Concurrent.Partitioner> třída poskytuje <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metoda, která umožňuje poskytovat sekvenční smyčka pro tělo delegáta, tak, aby delegáta je jenom jednou vyvolána na oddíl, namísto jednou za iteraci. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Přístup ukázáno v tomto příkladu je užitečný, když smyčky provede minimální množství práce. Jakmile je výpočetně náročná, pravděpodobně obdržíte stejnou nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky pomocí výchozí dělicí metody.  
  
## <a name="see-also"></a>Viz také  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Iterátory](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
