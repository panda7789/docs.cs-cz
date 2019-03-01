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
ms.openlocfilehash: fde68d0a938ed04380bf0e99cc0c544793571d77
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965576"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Postupy: Zrychlení malých smyček
Když <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> má malé tělo smyčky, jako například může pomaleji než ekvivalentní sekvenčních smyčkách, proveďte [pro](../../csharp/language-reference/keywords/for.md) smyčky v C# a [pro](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) smyčky v jazyce Visual Basic. Snížení výkonu způsobuje režie spojená s dělení dat a náklady na volání delegáta při každé iteraci smyčky. K řešení scénářů, <xref:System.Collections.Concurrent.Partitioner> třída poskytuje <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodu, která umožňuje poskytovat sekvenčních smyčkách pro tělo delegáta, tak, aby je delegát vyvolán jenom jednou na oddíl, ne jednou za iteraci. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Přístup předvedené v tomto příkladu je užitečný, pokud smyčka provádí minimální množství práce. Jakmile je výpočetně náročná, bude pravděpodobně získat stejný nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky pomocí výchozího rozdělovače.  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Iterátory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iterátory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
