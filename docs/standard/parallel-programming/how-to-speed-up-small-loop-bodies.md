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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139746"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Postupy: Zrychlení malých smyček
Pokud má <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčka malý text, může to být pomalejší než ekvivalentní sekvenční smyčka, jako je například smyčka [for](../../csharp/language-reference/keywords/for.md) v C# a smyčka [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) v Visual Basic. Pomalejší výkon je způsoben režijními náklady souvisejícími s rozdělením dat do oddílů a náklady na vyvolání delegáta v každé iteraci smyčky. Pro řešení takových scénářů poskytuje třída <xref:System.Collections.Concurrent.Partitioner> <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodu, která umožňuje poskytnout sekvenční smyčku pro tělo delegáta, aby byl delegát vyvolán pouze jednou pro každý oddíl, nikoli jednou pro iteraci. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Přístup, který ukazuje tento příklad, je užitečný, když smyčka provede minimální množství práce. Jakmile se práce vyřadí efektivněji, budete pravděpodobně mít stejný nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky s výchozím rozdělovačem.  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Iterátory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iterátory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
