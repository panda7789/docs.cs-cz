---
title: typ char – Referenční dokumentace jazyka C#
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: f771626e9777deab30e798559d847615d6124e6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205783"
---
# <a name="char-c-reference"></a>char (Referenční dokumentace jazyka C#)

`char`Klíčové slovo Type je alias pro <xref:System.Char?displayProperty=nameWithType> typ struktury .NET, který představuje znak Unicode UTF-16.

|Typ|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------------------|
|`char`|U + 0000 až U + FFFF|16 bitů|<xref:System.Char?displayProperty=nameWithType>|

Výchozí hodnota `char` typu je `\0` , tedy U + 0000.

`char`Typ podporuje operátory [porovnání](../operators/comparison-operators.md), [rovnosti](../operators/equality-operators.md), [zvýšení](../operators/arithmetic-operators.md#increment-operator-)a [snížení](../operators/arithmetic-operators.md#decrement-operator---) . Kromě toho pro `char` operandy [aritmetické](../operators/arithmetic-operators.md) a [bitové logické](../operators/bitwise-and-shift-operators.md) operátory provádějí operaci s odpovídajícími kódy znaků a vytvoří výsledek `int` typu.

Typ [řetězce](reference-types.md#the-string-type) představuje text jako sekvenci `char` hodnot.

## <a name="literals"></a>Literály

Hodnotu můžete zadat `char` pomocí:

- znakový literál.
- řídicí sekvence Unicode, která `\u` následuje hexadecimální reprezentace kódu znaku se čtyřmi symboly.
- šestnáctková řídicí sekvence, která `\x` následuje hexadecimální reprezentace kódu znaku.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Jak ukazuje předchozí příklad, můžete také přetypovat hodnotu kódu znaku na odpovídající `char` hodnotu.

> [!NOTE]
> V případě řídicí sekvence Unicode je nutné zadat všechny čtyři šestnáctkové číslice. To znamená, že `\u006A` je platná řídicí sekvence, zatímco `\u06A` a `\u6A` nejsou platné.
>
> V případě hexadecimální sekvence escape můžete vynechat úvodní nuly. To znamená, že `\x006A` `\x06A` `\x6A` řídicí sekvence, a jsou platné a odpovídají stejnému znaku.

## <a name="conversions"></a>Převody

`char`Typ je implicitně převoditelné na následující [celočíselné](integral-numeric-types.md) typy: `ushort` , `int` , `uint` , `long` a `ulong` . Je také implicitně převoditelné na předdefinované číselné typy s [plovoucí desetinnou](floating-point-numeric-types.md) čárkou: `float` , a `double` `decimal` . Je explicitně převoditelná na `sbyte` , `byte` a `short` integrální typy.

Neexistují žádné implicitní převody z jiných typů na `char` typ. Jakýkoli [celočíselný](integral-numeric-types.md) typ nebo číslo [s plovoucí desetinnou](floating-point-numeric-types.md) čárkou je však explicitně převoditelné na `char` .

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [integrální typy](~/_csharplang/spec/types.md#integral-types) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [Řetězce](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [Kódování znaků v rozhraní .NET](../../../standard/base-types/character-encoding-introduction.md)
