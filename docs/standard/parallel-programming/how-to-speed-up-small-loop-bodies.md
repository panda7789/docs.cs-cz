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
ms.openlocfilehash: 4983cafb9d4a72262dc7a6a6c37fab23937b3274
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288079"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Postupy: Zrychlení malých smyček
Pokud <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> má smyčka malý text, může to být pomalejší než ekvivalentní sekvenční smyčka, jako je například smyčka [for](../../csharp/language-reference/keywords/for.md) v jazyce C# a smyčka [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) v Visual Basic. Pomalejší výkon je způsoben režijními náklady souvisejícími s rozdělením dat do oddílů a náklady na vyvolání delegáta v každé iteraci smyčky. Pro řešení takových scénářů <xref:System.Collections.Concurrent.Partitioner> Třída poskytuje <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metodu, která umožňuje poskytnout sekvenční smyčku pro tělo delegáta, aby byl delegát vyvolán pouze jednou pro každý oddíl, nikoli jednou pro iteraci. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Přístup, který ukazuje tento příklad, je užitečný, když smyčka provede minimální množství práce. Jakmile se práce vyřadí efektivněji, budete pravděpodobně mít stejný nebo lepší výkon pomocí <xref:System.Threading.Tasks.Parallel.For%2A> <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky nebo s výchozím rozdělovačem.  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](data-parallelism-task-parallel-library.md)
- [Vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md)
- [Iterátory (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Iterátory (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [Výrazy lambda v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md)
