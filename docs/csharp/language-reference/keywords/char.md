---
title: klíčové slovo char C# – referenční informace
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771804"
---
# <a name="char-c-reference"></a>char (C# Referenční dokumentace)

Klíčové slovo Type `char` je alias pro typ struktury <xref:System.Char?displayProperty=nameWithType> .NET, který představuje znak Unicode UTF-16:

|Typ|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 až U + FFFF|16 bitů|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Konstanty `char`ho typu lze zapsat jako znakové literály, hexadecimální sekvence escape nebo reprezentace v kódování Unicode. Můžete také přetypovat celočíselný kód znaku do odpovídající `char` hodnoty. V následujícím příkladu jsou všechny čtyři prvky pole `char` inicializovány se stejným znakem `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Převody

`char` typ je implicitně převoditelný na následující [celočíselné](../builtin-types/integral-numeric-types.md) typy: `ushort`, `int`, `uint`, `long`a `ulong`. Je také implicitně převoditelná na předdefinované číselné typy s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou: `float`, `double`a `decimal`. Je explicitně převoditelná na `sbyte`, `byte`a `short` integrálních typů.

Neexistují žádné implicitní převody z jiných typů na typ `char`. Jakýkoli [celočíselný](../builtin-types/integral-numeric-types.md) typ nebo číslo [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou však lze explicitně převést na `char`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [celočíselné typy](~/_csharplang/spec/types.md#integral-types) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Tabulka předdefinovaných typů](./built-in-types-table.md)
- [Řetězce](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
