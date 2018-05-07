---
title: Použití příkazu foreach s poli (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 8511d9dd3b7155d2f6bca229f264071b54ed173b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití příkazu foreach s poli (Průvodce programováním v C#)
C# také poskytuje [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz. Tento příkaz umožňuje jednoduchý a přímý způsob iterace prvků jakéhokoli pole nebo vyčíslitelné kolekce. `foreach` Příkaz zpracovává prvky v pořadí vrácených typu pole nebo kolekce enumerátor, který je obvykle z 0-té element na poslední. Například následující kód vytvoří pole s názvem `numbers` a její iteruje `foreach` příkaz:  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 S multidimenzionálními poli můžete použít stejnou metodu pro iteraci skrz prvky, například:  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 Nicméně s vícerozměrná pole pomocí vnořený [pro](../../../csharp/language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad prvků pole.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
