---
title: typ znaku – C# odkaz
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3952e9e30706a8cd362ef248955918de5dacf4a3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787807"
---
# <a name="char-c-reference"></a>char (C# Referenční dokumentace)

Klíčové slovo Type `char` je alias pro typ struktury <xref:System.Char?displayProperty=nameWithType> .NET, který představuje znak Unicode UTF-16.

|Type|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 až U + FFFF|16 bitů|<xref:System.Char?displayProperty=nameWithType>|

Výchozí hodnota typu `char` je `\0`, tedy U + 0000.

Typ [řetězce](reference-types.md#the-string-type) představuje text jako posloupnost hodnot `char`.

## <a name="literals"></a>Literály

`char` hodnotu můžete zadat pomocí:

- znakový literál.
- řídicí sekvence Unicode, která je `\u` následovaná hexadecimálním znázorněním kódu znaku se čtyřmi symboly.
- šestnáctková řídicí sekvence, která je `\x` následovaná hexadecimálním znázorněním kódu znaku.

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

Jak ukazuje předchozí příklad, můžete také přetypovat hodnotu kódu znaku na odpovídající `char`ovou hodnotu.

> [!NOTE]
> V případě řídicí sekvence Unicode je nutné zadat všechny čtyři šestnáctkové číslice. To znamená, že `\u006A` je platná řídicí sekvence, zatímco `\u06A` a `\u6A` nejsou platné.
>
> V případě hexadecimální sekvence escape můžete vynechat úvodní nuly. To znamená, že řídicí sekvence `\x006A`, `\x06A`a `\x6A` jsou platné a odpovídají stejnému znaku.

## <a name="conversions"></a>Převody

`char` typ je implicitně převoditelný na následující [celočíselné](integral-numeric-types.md) typy: `ushort`, `int`, `uint`, `long`a `ulong`. Je také implicitně převoditelná na předdefinované číselné typy s [plovoucí desetinnou](floating-point-numeric-types.md) čárkou: `float`, `double`a `decimal`. Je explicitně převoditelná na `sbyte`, `byte`a `short` integrálních typů.

Neexistují žádné implicitní převody z jiných typů na typ `char`. Jakýkoli [celočíselný](integral-numeric-types.md) typ nebo číslo [s plovoucí desetinnou](floating-point-numeric-types.md) čárkou však lze explicitně převést na `char`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [celočíselné typy](~/_csharplang/spec/types.md#integral-types) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Tabulka předdefinovaných typů](../keywords/built-in-types-table.md)
- [Řetězce](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
