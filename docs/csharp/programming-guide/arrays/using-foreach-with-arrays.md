---
title: Použití foreach s poli - C# Programovací průvodce
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705675"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití foreach s poli (C# Programovací průvodce)

[Foreach](../../language-reference/keywords/foreach-in.md) prohlášení poskytuje jednoduchý, čistý způsob iterate prostřednictvím prvků pole.

U jednorozměrných polí `foreach` příkaz zpracovává prvky ve zvýšení pořadí indexu, `Length - 1`počínaje indexem 0 a konče indexem :

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

U vícerozměrných polí jsou prvky provázány tak, že indexy nejvýraznější ho vpravo jsou nejprve zvýšeny, pak další levý rozměr a tak dále doleva:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Však s vícerozměrných polí, pomocí vnořené [pro](../../language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad pořadí, ve kterém chcete zpracovat prvky pole.

## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Programovací příručka jazyka C#](../index.md)
- [Pole](index.md)
- [Jednorozměrná pole](single-dimensional-arrays.md)
- [Vícerozměrná pole](multidimensional-arrays.md)
- [Vícenásobná pole](jagged-arrays.md)
