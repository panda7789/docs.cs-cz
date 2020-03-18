---
title: Číselné typy s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou tázkou – odkaz
description: 'Informace o předdefinovaných typech c# s plovoucí desetinnou čárkou: float, double a decimal'
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
ms.openlocfilehash: 95b7f266654bbbcdcd0f81e3aa11cfc94af9f0e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77215239"
---
# <a name="floating-point-numeric-types-c-reference"></a>Číselné typy s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou tázkou (odkaz Jazyka C#

*Číselné typy s plovoucí desetinnou desetinnou desetinnou hodnotou* představují reálná čísla. Všechny číselné typy s plovoucí desetinnou [desetinnou desetinnou hodnotou](value-types.md)jsou typy hodnot . Jsou to také [jednoduché typy](value-types.md#built-in-value-types) a mohou být inicializovány [literály](#real-literals). Všechny číselné typy s plovoucí [desetinnou desetinnou hodnotou podporují aritmetické operátory](../operators/arithmetic-operators.md), [porovnání](../operators/comparison-operators.md)a [rovnost.](../operators/equality-operators.md)

## <a name="characteristics-of-the-floating-point-types"></a>Charakteristiky typů s plovoucí desetinnou tázkem

C# podporuje následující předdefinované typy s plovoucí desetinnou desetinnou a střední tok:
  
|C# typ/klíčové slovo|Přibližný rozsah|Přesnost|Velikost|Typ .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1,5 x 10<sup>−45</sup> až ±3,4 x 10<sup>38</sup>|~6-9 číslic|4 bajty|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5,0 × 10<sup>−324</sup> až ±1,7 × 10<sup>308</sup>|~15-17 číslic|8 bajtů|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1,0 x 10<sup>-28</sup> až ±7,9228 x 10<sup>28</sup>|28-29 číslic|16 bajtů|<xref:System.Decimal?displayProperty=nameWithType>|

V předchozí tabulce je každé klíčové slovo typu C# ze sloupce zcela vlevo aliasem odpovídajícího typu .NET. Jsou zaměnitelné. Například následující deklarace deklarují proměnné stejného typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Výchozí hodnota každého typu s plovoucí `0`desetinnou cípem je nula . Každý z typů `MinValue` s plovoucí `MaxValue` desetinnou desetinnou a konstantami, které poskytují minimální a maximální konečnou hodnotu tohoto typu. Typy `float` `double` a také poskytují konstanty, které představují hodnoty ne čísla a nekonečna. Například `double` typ obsahuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Vzhledem `decimal` k tomu, že typ `float` má `double`větší přesnost a menší rozsah než oba a , je vhodné pro finanční a měnové výpočty.

Můžete kombinovat [integrální](integral-numeric-types.md) typy `float` a a `double` typy ve výrazu. V tomto případě integrální typy jsou implicitně převedeny na jeden `float` z typů s plovoucí `double`desetinnou táceka a v případě potřeby je typ implicitně převeden na . Výraz se vyhodnotí takto:

- Pokud je `double` typ ve výrazu, výraz `double`vyhodnotí na , nebo [`bool`](bool.md) v relační a rovnosti porovnání.
- Pokud není `double` žádný typ ve výrazu, `float`výraz vyhodnotí na , nebo `bool` v porovnání relační a rovnosti.

Můžete také kombinovat integrální typy a `decimal` typ ve výrazu. V tomto případě integrální typy `decimal` jsou implicitně převedeny `decimal`na `bool` typ a výraz vyhodnotí na , nebo v porovnání relační a rovnosti.

`decimal` Typ nelze kombinovat s `float` `double` typy a ve výrazu. V tomto případě, pokud chcete provést operace aritmetiky, porovnání nebo rovnosti, je nutné explicitně převést operandy z nebo na `decimal` typ, jak ukazuje následující příklad:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

K formátování hodnoty s plovoucí desetinnou desetinnou hodnotou můžete použít [standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) nebo [vlastní číselné formátovací řetězce.](../../../standard/base-types/custom-numeric-format-strings.md)

## <a name="real-literals"></a>Skutečné literály

Typ skutečného literálu je určen jeho příponou takto:

- Doslovbez přípony nebo s `d` `D` příponou nebo je typu`double`
- Literál s `f` `F` příponou nebo je typu`float`
- Literál s `m` `M` příponou nebo je typu`decimal`

Následující kód ukazuje příklad každého z nich:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován počínaje C# 7.0. Oddělovač číslic můžete použít se všemi druhy číselných literál.

Můžete také použít vědecký zápis, to znamená, že zadáte exponentní část skutečného literálu, jak ukazuje následující příklad:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Převody

Existuje pouze jeden implicitní převod mezi číselnými typy s plovoucí desetinnou desetinnou hodnotou: z `float` na `double`. Můžete však převést libovolný typ s plovoucí desetinnou tácek na jakýkoli jiný typ s plovoucí desetinnou tácek s [explicitním přetypátkem](../operators/type-testing-and-cast.md#cast-operator-). Další informace naleznete [v tématu Předdefinované číselné převody](numeric-conversions.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Typy s plovoucí desetinnou tálicí](~/_csharplang/spec/types.md#floating-point-types)
- [Desetinný typ](~/_csharplang/spec/types.md#the-decimal-type)
- [Skutečné literály](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [Integrální typy](integral-numeric-types.md)
- [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
