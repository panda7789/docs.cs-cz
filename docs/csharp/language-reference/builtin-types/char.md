---
title: typ znaku – C# odkaz
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451162"
---
# <a name="char-c-reference"></a>char (C# Referenční dokumentace)

Klíčové slovo Type `char` je alias pro typ struktury <xref:System.Char?displayProperty=nameWithType> .NET, který představuje znak Unicode UTF-16.

|Typ|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 až U + FFFF|16 bitů|<xref:System.Char?displayProperty=nameWithType>|

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
