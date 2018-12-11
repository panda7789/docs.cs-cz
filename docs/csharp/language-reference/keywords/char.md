---
title: Char – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 6acb40117c4f59deb084965cb3db9e4a96f7f61a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242344"
---
# <a name="char-c-reference"></a>char (Referenční dokumentace jazyka C#)

`char` – Klíčové slovo se používá k deklaraci instance <xref:System.Char?displayProperty=nameWithType> strukturu, rozhraní .NET Framework používá k reprezentaci znaku Unicode. Hodnota `Char` objektu je hodnota číselná 16 bitů (pořadí).

 Znaky kódování Unicode se používá k reprezentování většinu psané jazyky po celém světě.

|Typ|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 U + FFFF|16bitový znak Unicode|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Konstanty objektu `char` typu lze zapsat jako znakových literálů, šestnáctková řídicí sekvence nebo reprezentace Unicode. Také můžete přetypovat kódy celočíselného znaku. V následujícím příkladu čtyři `char` proměnné jsou inicializována ve stejném `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Převody

A `char` lze implicitně převést na [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md). Však nejsou žádné implicitní převody z jiných typů `char` typu.

<xref:System.Char?displayProperty=nameWithType> Typ poskytuje několik statické metody pro práci s `char` hodnoty.

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.Char>  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
- [Řetězce](../../../csharp/programming-guide/strings/index.md)