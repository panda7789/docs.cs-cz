---
title: Číselné typy s plovoucí desetinnou čárkou – reference jazyka C#
description: 'Přečtěte si o integrovaných typech s plovoucí desetinnou čárkou v jazyce C#: float, Double a Decimal'
ms.date: 02/10/2020
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a1142d1aa04003ae1942902672cfc7a05edc99c0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662664"
---
# <a name="floating-point-numeric-types-c-reference"></a>Číselné typy s plovoucí desetinnou čárkou (Referenční dokumentace jazyka C#)

*Číselné typy s plovoucí desetinnou* čárkou reprezentují reálné číslo. Všechny číselné typy s plovoucí desetinnou čárkou jsou [typy hodnot](value-types.md). Jsou to také [jednoduché typy](value-types.md#built-in-value-types) a lze je inicializovat pomocí [literálů](#real-literals). Všechny číselné typy s plovoucí desetinnou čárkou podporují operátory [aritmetické](../operators/arithmetic-operators.md), [porovnání](../operators/comparison-operators.md)a [rovnosti](../operators/equality-operators.md) .

## <a name="characteristics-of-the-floating-point-types"></a>Vlastnosti typů s plovoucí desetinnou čárkou

Jazyk C# podporuje následující předdefinované typy s plovoucí desetinnou čárkou:
  
|Typ/klíčové slovo jazyka C#|Přibližný rozsah|Přesnost|Velikost|Typ .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|± 1,5 × 10<sup>− 45</sup> až ± 3,4 × 10<sup>38</sup>|~ 6-9 číslic|4 bajty|<xref:System.Single?displayProperty=nameWithType>|
|`double`|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 číslic|8 bajtů|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|± 1,0 × 10<sup>– 28</sup> až 7,9228 × 10<sup>28</sup>|28-29 číslic|16 bajtů|<xref:System.Decimal?displayProperty=nameWithType>|

V předchozí tabulce je každé klíčové slovo typu C# ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET. Jsou zaměnitelné. Například následující deklarace deklaruje proměnné stejného typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Výchozí hodnota každého typu s plovoucí desetinnou čárkou je nula, `0` . Každý z typů s plovoucí desetinnou čárkou `MinValue` má `MaxValue` konstanty a, které poskytují minimální a maximální konečnou hodnotu tohoto typu. `float`Typy a `double` také poskytují konstanty, které představují hodnoty nečíselné a nekonečno. Například `double` Typ poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType> , <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .

Vzhledem k tomu, že `decimal` typ má větší přesnost a menší rozsah než obojí `float` `double` , je vhodný pro finanční a peněžní výpočty.

Můžete kombinovat [integrální](integral-numeric-types.md) typy a `float` `double` typy a ve výrazu. V tomto případě jsou celočíselné typy implicitně převedeny na jeden z typů s plovoucí desetinnou čárkou a v případě potřeby `float` je typ implicitně převeden na `double` . Výraz se vyhodnotí takto:

- Pokud je `double` ve výrazu typ, je výraz vyhodnocen jako `double` nebo [`bool`](bool.md) v porovnání s relačním a rovností.
- Pokud `double` ve výrazu není žádný typ, výraz se vyhodnotí jako `float` nebo `bool` v relačních porovnáních a porovnávání rovnosti.

Můžete také kombinovat integrální typy a `decimal` typ ve výrazu. V tomto případě jsou celočíselné typy implicitně převedeny na `decimal` typ a výraz je vyhodnocen jako `decimal` nebo `bool` v porovnání s relačním a rovností.

Ve výrazu nelze kombinovat `decimal` typ s `float` typy a `double` . V takovém případě, pokud chcete provádět operace aritmetické, porovnání nebo rovnosti, je nutné explicitně převést operandy buď z nebo na `decimal` typ, jak ukazuje následující příklad:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

K formátování hodnoty s plovoucí desetinnou čárkou můžete použít buď [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) , nebo [řetězce vlastního číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) .

## <a name="real-literals"></a>Reálné literály

Typ reálného literálu je určen jeho příponou takto:

- Literál bez přípony nebo s `d` `D` příponou nebo je typu.`double`
- Literál s `f` `F` příponou nebo je typu.`float`
- Literál s `m` `M` příponou nebo je typu.`decimal`

Následující kód ukazuje příklad každé z nich:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován počínaje jazykem C# 7,0. Oddělovač číslic se dá použít u všech druhů číselných literálů.

Můžete také použít vědeckou notaci, to znamená, že určíte exponent, který je součástí reálného literálu, jak ukazuje následující příklad:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Převody

Existuje pouze jeden implicitní převod mezi číselnými typy s plovoucí desetinnou čárkou: od `float` do `double` . Můžete však převést libovolný typ s plovoucí desetinnou čárkou na jakýkoli jiný typ s plovoucí desetinnou čárkou s [explicitním přetypováním](../operators/type-testing-and-cast.md#cast-expression). Další informace najdete v tématu [integrované číselné převody](numeric-conversions.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Typy s plovoucí desetinnou čárkou](~/_csharplang/spec/types.md#floating-point-types)
- [Typ Decimal](~/_csharplang/spec/types.md#the-decimal-type)
- [Reálné literály](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [Celočíselné typy](integral-numeric-types.md)
- [Standardní řetězce formátu čísla](../../../standard/base-types/standard-numeric-format-strings.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
