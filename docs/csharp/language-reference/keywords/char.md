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
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698779"
---
# <a name="char-c-reference"></a>char (Referenční dokumentace jazyka C#)

Klíčové slovo `char` slouží k deklaraci instance struktury <xref:System.Char?displayProperty=nameWithType>, kterou .NET Framework používá pro reprezentaci znaku Unicode. Hodnota objektu `Char` je 16bitová číselná hodnota (Ordinal).

 Znaky Unicode slouží k reprezentaci většiny psaných jazyků po celém světě.

|Typ|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 až U + FFFF|16 bitový znak Unicode|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Konstanty typu `char` lze zapsat jako znakové literály, hexadecimální sekvence escape nebo reprezentace v kódování Unicode. Můžete také přetypovat kódy integrálních znaků. V následujícím příkladu jsou čtyři prvky pole `char` inicializovány se stejným znakem `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Převody

@No__t-0 lze implicitně převést na [UShort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)nebo [Decimal](../builtin-types/floating-point-numeric-types.md). Neexistují však žádné implicitní převody z jiných typů na typ `char`.

Typ <xref:System.Char?displayProperty=nameWithType> poskytuje několik statických metod pro práci s hodnotami `char`.

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
- [Řetězce](../../programming-guide/strings/index.md)
