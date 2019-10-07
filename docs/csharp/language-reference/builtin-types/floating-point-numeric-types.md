---
title: Číselné typy s plovoucí desetinnou C# čárkou – referenční informace
description: Přehled předdefinovaných typů s C# plovoucí desetinnou čárkou
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
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 17ae154780679dd1f42f43f1ec345cdc722815d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002191"
---
# <a name="floating-point-numeric-types-c-reference"></a>Číselné typy s plovoucí desetinnouC# čárkou (referenční)

**Typy s plovoucí desetinnou** čárkou jsou podmnožinou **jednoduchých typů** a lze je inicializovat pomocí [*literálů*](#floating-point-literals). Všechny typy s plovoucí desetinnou čárkou jsou také typy hodnot. Všechny číselné typy s plovoucí desetinnou čárkou podporují operátory [aritmetické](../operators/arithmetic-operators.md), [porovnání a rovnosti](../operators/equality-operators.md) .

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

Výchozí hodnota každého typu s plovoucí desetinnou čárkou je nula, `0`. Každý z typů s plovoucí desetinnou čárkou má konstanty `MinValue` a `MaxValue`, které poskytují minimální a maximální hodnotu konečné hodnoty tohoto typu. Typy `float` a `double` také poskytují konstanty, které nepředstavují hodnoty nečíselné a nekonečno. Například typ `double` poskytuje následující konstanty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Vzhledem k tomu, že typ `decimal` má větší přesnost a menší rozsah než obě `float` a `double`, je vhodné pro finanční a peněžní výpočty.

Ve výrazu můžete kombinovat [integrální](integral-numeric-types.md) typy a typy s plovoucí desetinnou čárkou. V tomto případě jsou integrální typy převedeny na typy s plovoucí desetinnou čárkou. Vyhodnocení výrazu je provedeno podle následujících pravidel:

- Pokud je jeden z typů s plovoucí desetinnou čárkou `double`, výraz se vyhodnotí jako `double` nebo na [logickou](../keywords/bool.md) hodnotu v relačních porovnáních nebo porovnávání pro rovnost.
- Pokud ve výrazu není žádný typ `double`, výraz se vyhodnotí jako `float` nebo na [logickou](../keywords/bool.md) hodnotu v relačních porovnáních nebo porovnávání pro rovnost.

Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:

- Kladná a záporná nula
- Kladné a záporné nekonečno
- Hodnota není číslo (NaN).
- Konečná sada nenulových hodnot

Další informace o těchto hodnotách najdete v tématu IEEE standard pro binární aritmetické operace s plovoucí desetinnou čárkou, která je k dispozici na webu [IEEE](https://www.ieee.org) .

K formátování hodnoty s plovoucí desetinnou čárkou můžete použít buď [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md) , nebo [řetězce vlastního číselného formátu](../../../standard/base-types/custom-numeric-format-strings.md) .

## <a name="floating-point-literals"></a>Literály s plovoucí desetinnou čárkou

Ve výchozím nastavení je číselný literál s plovoucí desetinnou čárkou na pravé straně operátoru přiřazení považován za `double`. Můžete použít přípony pro převod plovoucí desetinné čárky nebo integrálního literálu na konkrétní typ:

- Přípona `d` nebo `D` převede literál na `double`.
- Přípona `f` nebo `F` převede literál na `float`.
- Přípona `m` nebo `M` převede literál na `decimal`.

Následující příklady znázorňují jednotlivé přípony:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Převody

Existuje implicitní převod (nazývaný *rozšiřující převod*) z `float` na `double`, protože rozsah hodnot `float` je správnou podmnožinou `double` a nedochází ke ztrátě přesnosti od `float` do `double`.

Je nutné použít explicitní přetypování pro převod jednoho typu s plovoucí desetinnou čárkou na jiný typ s plovoucí desetinnou čárkou, pokud implicitní převod není definován ze zdrojového typu na cílový typ. Tato metoda se nazývá *zužující převod*. Explicitní případ je vyžadován, protože převod může mít za následek ztrátu dat. Neexistuje žádný implicitní převod mezi jinými typy s plovoucí desetinnou čárkou a typem `decimal`, protože typ `decimal` má větší přesnost než `float` nebo `double`.

Další informace o implicitním číselném převodu naleznete v tématu [implicitní číselná převodová tabulka](../keywords/implicit-numeric-conversions-table.md).

Další informace o explicitních číselných převodech naleznete v tématu [explicitní číselná](../keywords/explicit-numeric-conversions-table.md)převodová tabulka.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Celočíselné typy](integral-numeric-types.md)
- [Tabulka předdefinovaných typů](../keywords/built-in-types-table.md)
- [Číslovky v technologii .NET](../../../standard/numerics.md)
- [Přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md)
- [Tabulka implicitních číselných převodů](../keywords/implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Tabulka formátování číselných výsledků](../keywords/formatting-numeric-results-table.md)
- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
