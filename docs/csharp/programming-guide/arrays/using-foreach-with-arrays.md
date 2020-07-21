---
title: Použití příkazu foreach s poli – Průvodce programováním v C#
description: Příkaz foreach v jazyce C# prochází prvky pole. Pro jednorozměrná pole zpracovávají foreach prvky ve vzestupném pořadí indexu.
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: d924a3ef3351cbb30b809a1542f35314ee721852
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474537"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Použití příkazu foreach s poli (Průvodce programováním v C#)

Příkaz [foreach](../../language-reference/keywords/foreach-in.md) poskytuje jednoduchý a čistě způsob, jak iterovat prvky pole.

Pro jednorozměrná pole `foreach` zpracuje příkaz prvky ve vzestupném pořadí indexu, počínaje indexem 0 a končící indexem `Length - 1` :

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

U multidimenzionálních polí jsou elementy procházeny tak, že jsou nejprve zvyšovány indexy pravého rozměru, potom následující levá dimenze atd. vlevo:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Nicméně s multidimenzionálními poli, pomocí vnořené smyčky [for](../../language-reference/keywords/for.md) , získáte větší kontrolu nad pořadím, ve kterém mají být zpracovány prvky pole.

## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Průvodce programováním v C#](../index.md)
- [Pole](index.md)
- [Jednorozměrná pole](single-dimensional-arrays.md)
- [Vícerozměrná pole](multidimensional-arrays.md)
- [Vícenásobná pole](jagged-arrays.md)
