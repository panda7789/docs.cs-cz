---
title: Použití příkazu foreach s poli - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 16f65bc4ddcc37bbc1abb5dfa6299670a738073b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503570"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití příkazu foreach s poli (C# Programming Guide)

[Foreach](../../language-reference/keywords/foreach-in.md) příkaz umožňuje jednoduchý a přímý způsob iterace prvků pole.

Pro jednorozměrné pole `foreach` příkaz zpracovává prvky ve vzestupném pořadí index, od indexu 0 a končí index `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

Pro vícerozměrná pole je provázán prvků tak, že indexy rozměr nejvíce vpravo se zvýšenou první pak dimenzi a tak dále zleva další vlevo:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

Však s multidimenzionálními poli použijete [pro](../../language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad pořadí, ve které se má zpracovat prvky pole.

## <a name="see-also"></a>Viz také:

- <xref:System.Array>
- [Průvodce programováním v jazyce C#](../index.md)
- [Pole](index.md)
- [Jednorozměrná pole](single-dimensional-arrays.md)
- [Vícerozměrná pole](multidimensional-arrays.md)
- [Vícenásobná pole](jagged-arrays.md)
