---
title: Použití příkazu foreach s poli (Průvodce programováním v C#)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: b858f35167e24390a729769487ce98908a3d349f
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití příkazu foreach s poli (Průvodce programováním v C#)

[Foreach](../../language-reference/keywords/foreach-in.md) příkaz poskytuje jednoduché a vyčištění způsob k iteraci v rámci prvků pole.

Pro jednorozměrná pole `foreach` příkaz zpracovává prvky v roste pořadí index s indexem 0 počáteční a koncovou s indexem `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

Pro vícerozměrných polí je elementy provázán tak, aby indexy, které nejvíce vpravo dimenze jsou vyšší první a pak další levém dimenze, a tak dále na levé straně:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

Nicméně s vícerozměrná pole pomocí vnořený [pro](../../language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad pořadí, ve které se má zpracovat elementy pole.

## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Průvodce programováním v jazyce C#](../index.md)  
 [Pole](index.md)  
 [Jednorozměrná pole](single-dimensional-arrays.md)  
 [Vícerozměrná pole](multidimensional-arrays.md)  
 [Vícenásobná pole](jagged-arrays.md)
