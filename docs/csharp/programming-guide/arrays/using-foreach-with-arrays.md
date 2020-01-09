---
title: Použití příkazu foreach s poli C# – Průvodce programováním
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705675"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití příkazu foreach s poliC# (Průvodce programováním)

Příkaz [foreach](../../language-reference/keywords/foreach-in.md) poskytuje jednoduchý a čistě způsob, jak iterovat prvky pole.

Pro jednorozměrná pole zpracovává příkaz `foreach` prvky ve vzestupném pořadí indexů počínaje indexem 0 a končí `Length - 1`indexu:

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

U multidimenzionálních polí jsou elementy procházeny tak, že jsou nejprve zvyšovány indexy pravého rozměru, potom následující levá dimenze atd. vlevo:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Nicméně s multidimenzionálními poli, pomocí vnořené smyčky [for](../../language-reference/keywords/for.md) , získáte větší kontrolu nad pořadím, ve kterém mají být zpracovány prvky pole.

## <a name="see-also"></a>Viz také:

- <xref:System.Array>
- [Průvodce programováním v jazyce C#](../index.md)
- [Pole](index.md)
- [Jednorozměrná pole](single-dimensional-arrays.md)
- [Vícerozměrná pole](multidimensional-arrays.md)
- [Vícenásobná pole](jagged-arrays.md)
