---
title: Integrální číselné typy – odkaz jazyka C#
description: Seznamte se s rozsahem, velikostí úložiště a použitím pro každý z integrovaných číselných typů.
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093198"
---
# <a name="integral-numeric-types--c-reference"></a>Integrální číselné typy (odkaz C#)

*Integrální číselné typy* představují celá čísla. Všechny integrální číselné typy jsou [typy hodnot](value-types.md). Jsou to také [jednoduché typy](value-types.md#built-in-value-types) a mohou být inicializovány [literály](#integer-literals). Všechny integrální číselné typy podporují [aritmetické](../operators/arithmetic-operators.md), [bitové logické](../operators/bitwise-and-shift-operators.md), [porovnávací](../operators/comparison-operators.md)a [rovnoprávné](../operators/equality-operators.md) operátory.

## <a name="characteristics-of-the-integral-types"></a>Charakteristika integrálních typů

C# podporuje následující předdefinované integrální typy:

|C# typ/klíčové slovo|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 až 127|Podepsané osmibitové celé číslo|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 až 255|Nepodepsané osmibitové celé číslo|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32 768 až 32 767|Podepsané 16bitové celé číslo|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 až 65 535|Nepodepsané 16bitové celé číslo|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2 147 483 648 až 2 147 483 647|Podepsané 32bitové celé číslo|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 až 4 294 967 295|Nepodepsané 32bitové celé číslo|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9 223 372 036 854 775 808 až 9 223 372 036 854 775 807|Podepsané 64bitové celé číslo|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 až 18 446 744 073 709 551 615|Nepodepsané 64bitové celé číslo|<xref:System.UInt64?displayProperty=nameWithType>|

V předchozí tabulce je každé klíčové slovo typu C# ze sloupce zcela vlevo aliasem odpovídajícího typu .NET. Jsou zaměnitelné. Například následující deklarace deklarují proměnné stejného typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Výchozí hodnota každého integrálního `0`typu je nula . Každý z integrální typy má `MinValue` konstanty a, `MaxValue` které poskytují minimální a maximální hodnotu tohoto typu.

Pomocí <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury reprezentujte podepsané celé číslo bez horních nebo dolních hranic.

## <a name="integer-literals"></a>Celé číslo literály

Celé literály lze

- *desítkové*: bez předpony
- *hexadecimální*: `0x` `0X` s předponou nebo
- *binární*: `0b` s `0B` předponou nebo (k dispozici v C# 7.0 a novější)

Následující kód ukazuje příklad každého z nich:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován počínaje C# 7.0. Oddělovač číslic můžete použít se všemi druhy číselných literál.

Typ literálu celého čísla je určen jeho příponou takto:

- Pokud literál nemá žádnou příponu, jeho typ je první z následujících `uint` `long`typů, ve kterých může být jeho hodnota reprezentována: `int`, , , `ulong`.
- Pokud je literál doplněn `U` nebo `u`, jeho typ je prvním z následujících typů, `uint` `ulong`ve kterém může být jeho hodnota reprezentována: , .
- Pokud je literál doplněn `L` nebo `l`, jeho typ je prvním z následujících typů, `long` `ulong`ve kterém může být jeho hodnota reprezentována: , .

  > [!NOTE]
  > Malé písmeno `l` můžete použít jako příponu. To však generuje upozornění kompilátoru, protože písmeno `l` může být zaměněno s číslicí `1`. Použití `L` pro přehlednost.

- Pokud je literál doplněn `UL`, `Ul` `uL`, `ul` `LU`, `Lu` `lU`, `lu`, , `ulong`, nebo , jeho typ je .

Pokud hodnota reprezentovaná literálem celé číslo překročí <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilátoru [CS1021.](../../misc/cs1021.md)

Pokud je `int` určený typ celého literálu a hodnota reprezentovaná literálem je v rozsahu cílového `sbyte` `byte`typu, může být hodnota implicitně převedena na `short`, , , `ushort`, `uint`, nebo `ulong`:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Jak ukazuje předchozí příklad, pokud hodnota literálu není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031.](../../misc/cs0031.md)

Přetypovat můžete také převést hodnotu reprezentovanou literálem celéčíslo na typ jiný než určený typ literálu:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Převody

Libovolný integrální číselný typ můžete převést na jakýkoli jiný integrální číselný typ. Pokud cílový typ může uložit všechny hodnoty typu zdroje, převod je implicitní. V opačném případě je nutné použít [operátor `()` přetypádka](../operators/type-testing-and-cast.md#cast-operator-) k vyvolání explicitní převod. Další informace naleznete [v tématu Předdefinované číselné převody](numeric-conversions.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Integrální typy](~/_csharplang/spec/types.md#integral-types)
- [Celé číslo literály](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [Typy s plovoucí desetinnou tálicí](floating-point-numeric-types.md)
- [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
