---
title: Integrální číselné typy - C# odkaz
description: Další oblasti, velikosti úložiště a používá pro každý integrální číselné typy.
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236079"
---
# <a name="integral-numeric-types--c-reference"></a>Integrální číselné typy (C# odkaz)

**Integrální číselné typy** jsou podmnožinou **jednoduché typy** a mohou být inicializovány pomocí [ *literály*](#integral-literals). Typy hodnot jsou také všechny celočíselné typy. Všechny integrální číselné typy. podpora [aritmetické](../operators/arithmetic-operators.md), [bitový logický](../operators/bitwise-and-shift-operators.md), [porovnání a rovnost](../operators/equality-operators.md) operátory.

## <a name="characteristics-of-the-integral-types"></a>Vlastnosti celočíselných typů

C#podporuje následující předdefinované integrální typy:

|C#typ nebo klíčové slovo|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 až 127|8bitové celé číslo se znaménkem|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 až 255|Celé číslo bez znaménka 8 bitů|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32 768 do 32 767|16bitové celé číslo se znaménkem|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 až 65 535|Celé číslo bez znaménka 16 bitů|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2 147 483 648 do 2 147 483 647|32bitové celé číslo se znaménkem|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 do 4 294 967 295|Nepodepsané 32bitové celé číslo|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807|64bitové celé číslo se znaménkem|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 na 18,446,744,073,709,551,615|64-bit znaménka.|<xref:System.UInt64?displayProperty=nameWithType>|

V předchozí tabulce každý C# – klíčové slovo typ ve sloupci nejvíce vlevo je alias pro odpovídající typ formátu .NET. Jsou zaměnitelné. Například následující deklarace deklarování proměnných stejného typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Výchozí hodnota každý integrální typ je nula, `0`. Každý z celočíselných typů má `MinValue` a `MaxValue` konstanty, minimální a maximální hodnotu daného typu.

Použití <xref:System.Numerics.BigInteger?displayProperty=nameWithType> strukturu představující celé číslo se znaménkem s žádná horní nebo dolní meze.

## <a name="integral-literals"></a>Integrální literály

Integrální literály lze zadat jako *desítkové literály*, *šestnáctkové literály*, nebo *binární literály:* . Níže je uveden příklad každé:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Desítkové literály nevyžadují jakoukoli předponu. `x` Nebo `X` označuje, že předpona *šestnáctkové literál*. `b` Nebo `B` označuje, že předpona *binární literál*. Deklarace `binaryLiteral` demonstruje použití `_` jako *oddělovač číslic*. Oddělovač číslic jde použít s všechny číselné literály. Binární literály a oddělovače číslic `_` podporuje workflowy C# 7.0.

### <a name="literal-suffixes"></a>Přípony literálu

`l` Nebo `L` příponu Určuje, že by měl být celočíselný literál `long` typu. `ul` Nebo `UL` Určuje příponu `ulong` typu. Pokud `L` přípona se používá na literál, který je větší než 9,223,372,036,854,775,807 (maximální hodnota `long`), hodnota převedená na `ulong` typu. Pokud se překročí Hodnota reprezentovaná celočíselný literál <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, Chyba kompilátoru [CS1021](../../misc/cs1021.md) vyvolá. 

> [!NOTE]
> Malé písmeno "l" můžete použít jako příponu. Nicméně tím se vygeneruje upozornění kompilátoru protože písmeno "l" je snadno zaměnitelná s číslicí "1". Pro přehlednost použijte "L".

### <a name="type-of-an-integral-literal"></a>Typ celočíselný literál

Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:

1. `int`
1. `uint`
1. `long`
1. `ulong`

Celočíselný literál lze převést na typ s menší rozsah, než je výchozí přiřazení nebo výraz přetypování:

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

Celočíselný literál lze převést na typ s větším než výchozí, pomocí přiřazení, přetypování nebo příponu na literál:

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a>Převody

Je implicitní převod (volá se *rozšiřující převod*) mezi dvou celočíselných typů kde cílový typ můžete uložit všechny hodnoty typu zdroje. Například je implicitní převod z `int` k `long` protože rozsah `int` hodnoty jsou správné podmnožinou `long`. Nejsou k dispozici implicitní převod z menší celočíselný typ bez znaménka větší celočíselný typ se znaménkem. Existuje také implicitní převod z libovolný integrální typ na libovolný typ s plovoucí desetinnou čárkou.  Neexistuje žádný implicitní převod z libovolný integrální typ se znaménkem na libovolný integrální typ bez znaménka.

Pro převod jedné celočíselného typu na jiný celočíselný typ při implicitní převod není definován zdrojový typ pro cílový typ je nutné použít explicitní přetypování. Jedná se *zužující převod*. Explicitní případu se totiž převod může dojít ke ztrátě.

## <a name="see-also"></a>Viz také:

- [C#Specifikace jazyka - integrální typy](~/_csharplang/spec/types.md#integral-types)
- [C#referenční dokumentace](../index.md)
- [Typy s plovoucí desetinnou čárkou](floating-point-numeric-types.md)
- [Tabulka výchozích hodnot](../keywords/default-values-table.md)
- [Tabulka formátování číselných výsledků](../keywords/formatting-numeric-results-table.md)
- [Tabulka předdefinovaných typů](../keywords/built-in-types-table.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
