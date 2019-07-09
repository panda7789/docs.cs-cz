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
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664206"
---
# <a name="floating-point-numeric-types-c-reference"></a>Číselné typy s plovoucí desetinnou čárkou (C# odkaz)

**Typy s plovoucí desetinnou čárkou** jsou podmnožinou **jednoduché typy** a mohou být inicializovány pomocí [ *literály*](#floating-point-literals). Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot. Všechny číselné typy s plovoucí desetinnou čárkou podporují [aritmetické](../operators/arithmetic-operators.md) [porovnání a rovnost](../operators/equality-operators.md) operátory.

V následující tabulce jsou uvedeny přesnosti a přibližné rozsahy typů s plovoucí desetinnou čárkou:
  
|type|Přibližný rozsah|Přesnost|  
|----------|-----------------------|---------------|  
|`float`|±1.5 x 10<sup>−45</sup> k ±3.4 x 10<sup>38</sup>|~ 6. až 9 číslic|  
|`double`|±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup>|~ 15-17 číslic|  
|`decimal`|±1.0 x 10<sup>– 28</sup> k ±7.9228 x 10<sup>28</sup>|28 – 29 číslic|  

Výchozí hodnota pro všechny typy s plovoucí desetinnou čárkou je `0`. Každý z typů s plovoucí desetinnou čárkou se konstanty s názvem `MinValue` a `MaxValue` pro minimální a maximální hodnotu daného typu. `float` a `double` typy mají další konstanty pro `PositiveInfinity`, `NegativeInfinity`, a `NaN` (pro "nejedná se číslo"). `decimal` Typ obsahuje konstanty pro `Zero`, `One`, a `MinusOne`.

`decimal` Typ má větší přesnost a má menší rozsah než obě `float` a `double`, takže je vhodné pro výpočty finančních a přepočty měn.

Integrální typy a typy s plovoucí desetinnou čárkou ve výrazu můžete kombinovat. V takovém případě integrální typy jsou převedeny na typy s plovoucí desetinnou čárkou. Vyhodnocení výrazu se provádí dle následujících pravidel:

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
- [Tabulka výchozích hodnot](../keywords/default-values-table.md)
- [Tabulka formátování číselných výsledků](../keywords/formatting-numeric-results-table.md)
- [Tabulka předdefinovaných typů](../keywords/built-in-types-table.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
- [Přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md)
- [Tabulka implicitních číselných převodů](../keywords/implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
