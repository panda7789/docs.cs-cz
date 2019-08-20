---
title: klíčové slovo char C# – referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605946"
---
# <a name="char-c-reference"></a>char (Referenční dokumentace jazyka C#)

Klíčové slovo slouží k deklaraci instance <xref:System.Char?displayProperty=nameWithType> struktury, kterou .NET Framework používá pro reprezentaci znaku Unicode. `char` Hodnota `Char` objektu je 16bitová číselná hodnota (Ordinal).

 Znaky Unicode slouží k reprezentaci většiny psaných jazyků po celém světě.

|type|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 až U + FFFF|16 bitový znak Unicode|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Konstanty `char` typu lze zapsat jako znakové literály, šestnáctkové řídicí sekvence nebo reprezentace v kódování Unicode. Můžete také přetypovat kódy integrálních znaků. V následujícím příkladu jsou čtyři `char` proměnné inicializovány se stejným znakem `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Převody

[](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md)Lze implicitně převést na UShort, int, uint, Double nebo Decimal. `char` Neexistují však žádné implicitní převody z jiných typů na `char` typ.

Typ poskytuje několik statických metod pro práci s `char` hodnotami. <xref:System.Char?displayProperty=nameWithType>

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace naleznete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) ve [ C# specifikaci jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.Char>
- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Celočíselné typy](../builtin-types/integral-numeric-types.md)
- [Tabulka předdefinovaných typů](./built-in-types-table.md)
- [Tabulka implicitních číselných převodů](./implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](./explicit-numeric-conversions-table.md)
- [Typy s povolenou hodnotou Null](../../programming-guide/nullable-types/index.md)
- [Řetězce](../../programming-guide/strings/index.md)
