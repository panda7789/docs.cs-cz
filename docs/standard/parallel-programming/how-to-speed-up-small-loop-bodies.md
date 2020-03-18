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
ms.openlocfilehash: 29d7fa8200ddd972c1a5c98ea6f30a7c8ff732e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139746"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Postupy: Zrychlení malých smyček
Pokud <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> má smyčka malé tělo, může provádět pomaleji než ekvivalentní sekvenční smyčka, jako je například [smyčka for](../../csharp/language-reference/keywords/for.md) v jazyce C# a [smyčka For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) v jazyce Visual Basic. Pomalejší výkon je způsoben režií, která se podílí na dělení dat, a náklady na vyvolání delegáta v každé iteraci smyčky. Chcete-li řešit <xref:System.Collections.Concurrent.Partitioner> tyto scénáře, třída poskytuje metodu, <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> která umožňuje poskytnout sekvenční smyčky pro tělo delegáta, tak, aby delegát je vyvolána pouze jednou za oddíl, namísto jednou za iteraci. Další informace naleznete [v tématu Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Přístup demonstrovaný v tomto příkladu je užitečný, když smyčka provádí minimální množství práce. Vzhledem k tomu, že práce se stává více výpočetní nákladné, <xref:System.Threading.Tasks.Parallel.For%2A> budete <xref:System.Threading.Tasks.Parallel.ForEach%2A> pravděpodobně získat stejný nebo lepší výkon pomocí nebo smyčky s výchozím partitioner.  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Iterátory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iterátory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
