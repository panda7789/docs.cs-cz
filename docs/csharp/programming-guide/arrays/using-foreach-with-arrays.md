---
title: Použití příkazu foreach s poli - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a290cd709dd6491981658f467fa0163011290128
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238465"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití příkazu foreach s poli (C# Programming Guide)

[Foreach](../../language-reference/keywords/foreach-in.md) příkaz umožňuje jednoduchý a přímý způsob iterace prvků pole.

Pro jednorozměrné pole `foreach` příkaz zpracovává prvky ve vzestupném pořadí index, od indexu 0 a končí index `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

Pro vícerozměrná pole je provázán prvků tak, že indexy rozměr nejvíce vpravo se zvýšenou první pak dimenzi a tak dále zleva další vlevo:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

Však s multidimenzionálními poli použijete [pro](../../language-reference/keywords/for.md) smyčky vám dává větší kontrolu nad pořadí, ve které se má zpracovat prvky pole.

## <a name="see-also"></a>Viz také

- <xref:System.Array>  
- [Průvodce programováním v jazyce C#](../index.md)  
- [Pole](index.md)  
- [Jednorozměrná pole](single-dimensional-arrays.md)  
- [Vícerozměrná pole](multidimensional-arrays.md)  
- [Vícenásobná pole](jagged-arrays.md)
