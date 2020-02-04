---
title: Celočíselné číselné typy C# – referenční informace
description: Seznamte se s rozsahem, velikostí úložiště a s využitím pro každý celočíselný numerický typ.
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
ms.openlocfilehash: 2fb4d7185ac85b29f2cc2d2e7a29e192f91a0868
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980142"
---
# <a name="integral-numeric-types--c-reference"></a>Integrální číselné typy (C# Referenční dokumentace)

**Integrální číselné typy** jsou podmnožinou **jednoduchých typů** a lze je inicializovat pomocí [*literálů*](#integer-literals). Všechny celočíselné typy jsou také typy hodnot. Všechny integrální číselné typy podporují [aritmetické](../operators/arithmetic-operators.md)a [logické](../operators/bitwise-and-shift-operators.md)operátory, [porovnání](../operators/comparison-operators.md)a [rovnost](../operators/equality-operators.md) .

## <a name="characteristics-of-the-integral-types"></a>Charakteristiky integrálních typů

C#podporuje následující předdefinované celočíselné typy:

|C#typ/klíčové slovo|Rozsah|Velikost|Typ .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 až 127|8bitové celé číslo se znaménkem|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 až 255|8bitové celé číslo bez znaménka|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32 768 až 32 767|16bitové celé číslo se znaménkem|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 až 65 535|16bitové celé číslo bez znaménka|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2 147 483 648 až 2 147 483 647|Podepsané 32 – celé číslo se znaménkem|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 až 4 294 967 295|Celé číslo bez znaménka 32-bit|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|– 9223372036854775808 na 9 223 372 036 854 775 807|Podepsané 64 – celé číslo se znaménkem|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 až 18446744073709551615|Celé číslo bez znaménka 64-bit|<xref:System.UInt64?displayProperty=nameWithType>|

V předchozí tabulce je každé C# klíčové slovo Type ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET. Jsou zaměnitelné. Například následující deklarace deklaruje proměnné stejného typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Výchozí hodnota každého integrálního typu je nula, `0`. Každý celočíselný typ má `MinValue` a `MaxValue` konstanty, které poskytují minimální a maximální hodnotu tohoto typu.

Pomocí <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury reprezentovat celé číslo se znaménkem bez horních nebo dolních mezí.

## <a name="integer-literals"></a>Celočíselné literály

Celočíselné literály mohou být

- *Decimal*: bez předpony
- *šestnáctková*: s předponou `0x` nebo `0X`
- *binární*: s předponou `0b` nebo `0B` (k dispozici v C# 7,0 a novějším)

Následující kód ukazuje příklad každé z nich:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován od C# 7,0. Oddělovač číslic se dá použít u všech druhů číselných literálů.

Typ celočíselného literálu je určen jeho příponou takto:

- Pokud literál nemá žádnou příponu, je jeho typ prvním z následujících typů, ve kterém může být jeho hodnota reprezentovaná: `int`, `uint`, `long``ulong`.
- Je-li literál určen `U` nebo `u`, je jeho typ prvním z následujících typů, ve kterém lze jeho hodnotu reprezentovat: `uint`, `ulong`.
- Je-li literál určen `L` nebo `l`, je jeho typ prvním z následujících typů, ve kterém lze jeho hodnotu reprezentovat: `long`, `ulong`.

  > [!NOTE]
  > Jako příponu můžete použít malé písmeno `l`. Tím se však vygeneruje upozornění kompilátoru, protože písmeno `l` může být zaměněno pomocí číslice `1`. Pro přehlednost použijte `L`.

- Pokud má literál příponu `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`nebo `lu`, jeho typ je `ulong`.

Pokud hodnota reprezentovaná celočíselným literálem překračuje <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilátoru [CS1021](../../misc/cs1021.md) .

Pokud je určen typ celočíselného literálu `int` a hodnota reprezentovaná literálem je v rámci rozsahu cílového typu, hodnota může být implicitně převedena na `sbyte`, `byte`, `short`, `ushort`, `uint`nebo `ulong`:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Jak ukazuje předchozí příklad, pokud hodnota literálu není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031](../../misc/cs0031.md) .

Můžete také použít přetypování k převodu hodnoty reprezentované celočíselným literálem na jiný typ, než je určený typ literálu:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Převody

Libovolný celočíselný numerický typ můžete převést na jakýkoliv jiný integrální číselný typ. Pokud cílový typ může ukládat všechny hodnoty zdrojového typu, je převod implicitní. V opačném případě je nutné použít [operátor přetypování `()`](../operators/type-testing-and-cast.md#cast-operator-) k vyvolání explicitního převodu. Další informace najdete v tématu [integrované číselné převody](numeric-conversions.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Celočíselné typy](~/_csharplang/spec/types.md#integral-types)
- [Celočíselné literály](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Tabulka předdefinovaných typů](../keywords/built-in-types-table.md)
- [Typy s plovoucí desetinnou čárkou](floating-point-numeric-types.md)
- [Řetězce standardního číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
