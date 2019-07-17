---
title: Číselné typy s plovoucí desetinnou čárkou - C# odkaz
description: Přehled vestavěné typy C# s plovoucí desetinnou čárkou
ms.date: 06/30/2019
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236060"
---
# <a name="floating-point-numeric-types-c-reference"></a>Číselné typy s plovoucí desetinnou čárkou (C# odkaz)

**Typy s plovoucí desetinnou čárkou** jsou podmnožinou **jednoduché typy** a mohou být inicializovány pomocí [ *literály*](#floating-point-literals). Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot. Všechny číselné typy s plovoucí desetinnou čárkou podporují [aritmetické](../operators/arithmetic-operators.md), [porovnání a rovnost](../operators/equality-operators.md) operátory.

## <a name="characteristics-of-the-floating-point-types"></a>Vlastnosti typů s plovoucí desetinnou čárkou

C#podporuje následující předdefinované typy s plovoucí desetinnou čárkou:
  
|C#typ nebo klíčové slovo|Přibližný rozsah|Přesnost|Typ formátu .NET|
|----------|-----------------------|---------------|--------------|
|`float`|±1.5 x 10<sup>−45</sup> k ±3.4 x 10<sup>38</sup>|~ 6. až 9 číslic|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup>|~ 15-17 číslic|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1.0 x 10<sup>– 28</sup> k ±7.9228 x 10<sup>28</sup>|28 – 29 číslic|<xref:System.Decimal?displayProperty=nameWithType>|

V předchozí tabulce každý C# – klíčové slovo typ ve sloupci nejvíce vlevo je alias pro odpovídající typ formátu .NET. Jsou zaměnitelné. Například následující deklarace deklarování proměnných stejného typu:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

Výchozí hodnota u každého typu s plovoucí desetinnou čárkou je nula, `0`. Každý z typů s plovoucí desetinnou čárkou nemá `MinValue` a `MaxValue` konstanty, minimální a maximální konečnou hodnotu daného typu. `float` a `double` typy také poskytují konstanty, které představují hodnoty not a number a nekonečno. Například `double` typ poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Protože `decimal` typ má větší přesnost a má menší rozsah než obě `float` a `double`, je vhodný pro výpočty finančních a přepočty měn.

Je možné kombinovat [integrální](integral-numeric-types.md) typy a typy s plovoucí desetinnou čárkou ve výrazu. V takovém případě integrální typy jsou převedeny na typy s plovoucí desetinnou čárkou. Vyhodnocení výrazu se provádí dle následujících pravidel:

- Pokud jeden z typů s plovoucí desetinnou čárkou je `double`, je výraz vyhodnocen `double`, nebo [bool](../keywords/bool.md) v relační porovnání nebo porovnání rovnosti.
- Pokud není žádný `double` zadejte výraz, výraz je vyhodnocen jako `float`, nebo [bool](../keywords/bool.md) v relační porovnání nebo porovnání rovnosti.

Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:

- Kladnou a zápornou nulou
- Kladné a záporné nekonečno.
- Hodnota not-a-Number (NaN)
- Konečná sada nenulové hodnoty

Další informace o těchto hodnotách naleznete v části Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](https://www.ieee.org) webu.

Můžete použít buď [řetězce standardního číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md) nebo [vlastní řetězce číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) pro formátování hodnoty s plovoucí desetinnou čárkou.

## <a name="floating-point-literals"></a>Literály s plovoucí desetinnou čárkou

Ve výchozím nastavení, je číselný literál s plovoucí desetinnou čárkou na pravé straně operátoru považováno za `double`. Můžete převést literál s plovoucí desetinnou čárkou nebo celočíselné na konkrétní typ přípony:

- `d` Nebo `D` přípona převede na literál `double`.
- `f` Nebo `F` přípona převede na literál `float`.
- `m` Nebo `M` přípona převede na literál `decimal`.

Následující příklady ukazují jednotlivých přípon:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Převody

Je implicitní převod (volá *rozšiřující převod*) z `float` k `double` protože rozsah `float` hodnoty jsou správné podmnožinou `double` a nedochází ke ztrátě přesnosti z `float` k `double`.

Převést jeden typ s plovoucí desetinnou čárkou k jinému typu s plovoucí desetinnou čárkou, když implicitní převod není definován zdrojový typ pro cílový typ je nutné použít explicitní přetypování. Jedná se *zužující převod*. Explicitní případu se totiž převod může dojít ke ztrátě. Neexistuje žádný implicitní převod mezi ostatní typy s plovoucí desetinnou čárkou a `decimal` typu, protože `decimal` typ má zato větší přesnost než buď `float` nebo `double`.

Další informace o implicitním číselném převodu naleznete v tématu [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).

Další informace o explicitním číselném převodu naleznete v tématu [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Celočíselné typy](integral-numeric-types.md)
- [Tabulka předdefinovaných typů](../keywords/built-in-types-table.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
- [Přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md)
- [Tabulka implicitních číselných převodů](../keywords/implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Tabulka formátování číselných výsledků](../keywords/formatting-numeric-results-table.md)
- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
