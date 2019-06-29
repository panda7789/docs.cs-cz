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
ms.openlocfilehash: 0b4f04a1ba6244373e36cc6a6188edabe33ec453
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424347"
---
# <a name="char-c-reference"></a>char (Referenční dokumentace jazyka C#)

`char` – Klíčové slovo se používá k deklaraci instance <xref:System.Char?displayProperty=nameWithType> strukturu, rozhraní .NET Framework používá k reprezentaci znaku Unicode. Hodnota `Char` objektu je hodnota číselná 16 bitů (pořadí).

 Znaky kódování Unicode se používá k reprezentování většinu psané jazyky po celém světě.

|type|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 U + FFFF|16bitový znak Unicode|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Konstanty objektu `char` typu lze zapsat jako znakových literálů, šestnáctková řídicí sekvence nebo reprezentace Unicode. Také můžete přetypovat kódy celočíselného znaku. V následujícím příkladu čtyři `char` proměnné jsou inicializována ve stejném `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Převody

A `char` lze implicitně převést na [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desetinné](../../../csharp/language-reference/keywords/decimal.md). Však nejsou žádné implicitní převody z jiných typů `char` typu.

<xref:System.Char?displayProperty=nameWithType> Typ poskytuje několik statické metody pro práci s `char` hodnoty.

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.Char>
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [Celočíselné typy](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)
- [Řetězce](../../../csharp/programming-guide/strings/index.md)
