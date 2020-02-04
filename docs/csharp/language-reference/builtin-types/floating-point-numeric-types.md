---
title: Číselné typy s plovoucí desetinnou C# čárkou – referenční informace
description: Přehled předdefinovaných typů s C# plovoucí desetinnou čárkou
ms.date: 10/22/2019
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
ms.openlocfilehash: 9fde2b28288b58d7da3a4d003ec50af7d7e7a965
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980168"
---
# <a name="floating-point-numeric-types-c-reference"></a>Číselné typy s plovoucí desetinnouC# čárkou (referenční)

**Typy s plovoucí desetinnou** čárkou jsou podmnožinou **jednoduchých typů** a lze je inicializovat pomocí [*literálů*](#real-literals). Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot. Všechny číselné typy s plovoucí desetinnou čárkou podporují operátory [aritmetické](../operators/arithmetic-operators.md), [porovnání](../operators/comparison-operators.md)a [rovnosti](../operators/equality-operators.md) .

## <a name="characteristics-of-the-floating-point-types"></a>Vlastnosti typů s plovoucí desetinnou čárkou

C#podporuje následující předdefinované typy s plovoucí desetinnou čárkou:
  
|C#typ/klíčové slovo|Přibližný rozsah|Přesnost|Velikost|Typ .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|± 1,5 × 10<sup>− 45</sup> až ± 3,4 × 10<sup>38</sup>|~ 6-9 číslic|4 bajty|<xref:System.Single?displayProperty=nameWithType>|
|`double`|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 číslic|8 bajtů|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|± 1,0 × 10<sup>– 28</sup> až 7,9228 × 10<sup>28</sup>|28-29 číslic|16 bajtů|<xref:System.Decimal?displayProperty=nameWithType>|

V předchozí tabulce je každé C# klíčové slovo Type ze sloupce úplně vlevo alias pro odpovídající typ rozhraní .NET. Jsou zaměnitelné. Například následující deklarace deklaruje proměnné stejného typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Výchozí hodnota každého typu s plovoucí desetinnou čárkou je nula, `0`. Každý z typů s plovoucí desetinnou čárkou má `MinValue` a `MaxValue` konstanty, které poskytují minimální a maximální konečnou hodnotu tohoto typu. Typy `float` a `double` také poskytují konstanty, které nepředstavují hodnoty nečíselné a nekonečno. Například typ `double` poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Vzhledem k tomu, že typ `decimal` má větší přesnost a menší rozsah než `float` a `double`, je vhodné pro finanční a peněžní výpočty.

Ve výrazu můžete kombinovat [integrální](integral-numeric-types.md) typy a typy s plovoucí desetinnou čárkou. V tomto případě jsou integrální typy převedeny na typy s plovoucí desetinnou čárkou. Vyhodnocení výrazu je provedeno podle následujících pravidel:

- Pokud je jeden z typů s plovoucí desetinnou čárkou `double`, výraz se vyhodnotí jako `double`nebo [bool](bool.md) v relačních porovnáních a porovnávání rovnosti.
- Pokud ve výrazu není žádný typ `double`, výraz se vyhodnotí jako `float`nebo [bool](bool.md) v relačních porovnáních a porovnávání rovnosti.

Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:

- Kladná a záporná nula
- Kladné a záporné nekonečno
- Hodnota není číslo (NaN).
- Konečná sada nenulových hodnot

Další informace o těchto hodnotách najdete v tématu IEEE standard pro binární aritmetické operace s plovoucí desetinnou čárkou, která je k dispozici na webu [IEEE](https://www.ieee.org) .

K formátování hodnoty s plovoucí desetinnou čárkou můžete použít buď [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) , nebo [řetězce vlastního číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) .

## <a name="real-literals"></a>Reálné literály

Typ reálného literálu je určen jeho příponou takto:

- Literál bez přípony nebo s příponou `d` nebo `D` je typu `double`
- Literál s příponou `f` nebo `F` je typu `float`
- Literál s příponou `m` nebo `M` je typu `decimal`

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

Předchozí příklad také ukazuje použití `_` jako *oddělovač číslic*, který je podporován od C# 7,0. Oddělovač číslic se dá použít u všech druhů číselných literálů.

Můžete také použít vědeckou notaci, to znamená, že určíte exponent, který je součástí reálného literálu, jak ukazuje následující příklad:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Převody

Existuje pouze jeden implicitní převod mezi číselnými typy s plovoucí desetinnou čárkou: od `float` po `double`. Můžete však převést libovolný typ s plovoucí desetinnou čárkou na jakýkoli jiný typ s plovoucí desetinnou čárkou s [explicitním přetypováním](../operators/type-testing-and-cast.md#cast-operator-). Další informace najdete v tématu [integrované číselné převody](numeric-conversions.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Typy s plovoucí desetinnou čárkou](~/_csharplang/spec/types.md#floating-point-types)
- [Typ Decimal](~/_csharplang/spec/types.md#the-decimal-type)
- [Reálné literály](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Tabulka předdefinovaných typů](../keywords/built-in-types-table.md)
- [Celočíselné typy](integral-numeric-types.md)
- [Řetězce standardního číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
