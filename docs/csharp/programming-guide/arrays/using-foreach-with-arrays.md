---
title: "Použití příkazu foreach s poli (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití příkazu foreach s poli (Průvodce programováním v C#)
C# také poskytuje [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz. Tento příkaz umožňuje jednoduchý a přímý způsob iterace prvků jakéhokoli pole nebo vyčíslitelné kolekce. `foreach` Příkaz zpracovává prvky v pořadí vrácených typu pole nebo kolekce enumerátor, který je obvykle z 0-té element na poslední. Například následující kód vytvoří pole s názvem `numbers` a její iteruje `foreach` příkaz:  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 S multidimenzionálními poli můžete použít stejnou metodu pro iteraci skrz prvky, například:  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 Nicméně s vícerozměrná pole pomocí vnořený [pro](../../../csharp/language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad prvků pole.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
