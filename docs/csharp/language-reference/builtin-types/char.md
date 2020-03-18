---
title: typ znaku – odkaz jazyka C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846519"
---
# <a name="char-c-reference"></a>char (odkaz C#)

Klíčové `char` slovo type je alias <xref:System.Char?displayProperty=nameWithType> pro typ struktury .NET, který představuje znak Unicode UTF-16.

|Typ|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 až U+FFFF|16 bitů|<xref:System.Char?displayProperty=nameWithType>|

Výchozí hodnota `char` typu je `\0`, to znamená U + 0000.

Typ [řetězce](reference-types.md#the-string-type) představuje text jako `char` posloupnost hodnot.

## <a name="literals"></a>Literály

Hodnotu `char` můžete zadat pomocí:

- znak literál.
- řídicí sekvence Unicode, `\u` po níž následuje šestnáctková reprezentace znakového kódu se čtyřmi symboly.
- šestnáctková escape sekvence, `\x` po které následuje šestnáctkové znázornění znakového kódu.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Jak ukazuje předchozí příklad, můžete také přetypovat hodnotu `char` kódu znaku do odpovídající hodnoty.

> [!NOTE]
> V případě sekvence escape Unicode je nutné zadat všechny čtyři šestnáctkové číslice. To znamená, `\u006A` že je platná `\u06A` `\u6A` sekvence escape, zatímco a nejsou platné.
>
> V případě šestnáctkové únikové sekvence můžete vynechat úvodní nuly. To znamená `\x006A`, `\x06A`, `\x6A` a escape sekvence jsou platné a odpovídají stejnému znaku.

## <a name="conversions"></a>Převody

Typ `char` je implicitně převoditelný na `int`následující `uint` `long` [integrální](integral-numeric-types.md) typy: `ushort`, , , a `ulong`. Je také implicitně převoditelný na předdefinované číselné `float` `double`typy `decimal` [s plovoucí desetinnou desetinnou desetinnou desetinnou hodnotou:](floating-point-numeric-types.md) , , a . Je explicitně převoditelný na `sbyte`, `byte`a `short` integrální typy.

Neexistují žádné implicitní převody z `char` jiných typů na typ. Všechny [integrální](integral-numeric-types.md) nebo [plovoucí desetinné](floating-point-numeric-types.md) číselné typy je však explicitně převodonvertorní na `char`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [v](~/_csharplang/spec/types.md#integral-types) části Integral types ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [Řetězce](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
