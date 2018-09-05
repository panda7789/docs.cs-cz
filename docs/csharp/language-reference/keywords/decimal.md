---
title: Decimal – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: c9d40238ca4c34238d5663185f93afbce73195cf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506516"
---
# <a name="decimal-c-reference"></a>decimal (Referenční dokumentace jazyka C#)

`decimal` – Klíčové slovo označuje typ 128bitových dat. Ve srovnání s jinými typy s plovoucí desetinnou čárkou `decimal` typ má větší přesnost a menší rozsah, díky čemuž je vhodný pro výpočty finančních a přepočty měn. Přibližný rozsah a přesnost `decimal` typu jsou uvedeny v následující tabulce.

|Typ|Přibližný rozsah|Přesnost|Typ formátu .NET|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|±1.0 x 10<sup>– 28</sup> k ±7.9228 x 10<sup>28</sup>|28–29 významných číslic|<xref:System.Decimal?displayProperty=nameWithType>|

Výchozí hodnota `decimal` je 0 m.

## <a name="literals"></a>Literály

Pokud chcete, aby číselný literál reálného čísla jsou považovány za `decimal`, použijte příponu m nebo M, například:

```csharp
decimal myMoney = 300.5m;
```

Bez přípony m je číslo považováno za [double](../../../csharp/language-reference/keywords/double.md) a vygeneruje chybu kompilátoru.

## <a name="conversions"></a>Převody

Integrální typy jsou implicitně převedeny na `decimal` a výsledek je vyhodnocen jako `decimal`. Z tohoto důvodu můžete inicializovat proměnnou desítkového čísla pomocí celočíselného literálu bez přípony, a to následovně:

```csharp
decimal myMoney = 300;
```

Neexistuje žádný implicitní převod mezi ostatní typy s plovoucí desetinnou čárkou a `decimal` typ; proto přetypování musí použít k převodu mezi těmito dvěma typy. Příklad:

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

Můžete také kombinovat `decimal` a numerické integrální typy ve stejném výrazu. Kombinace `decimal` a jiné typy s plovoucí desetinnou čárkou bez přetypování způsobí chybu kompilace.

Další informace o implicitním číselném převodu naleznete v tématu [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).

Další informace o explicitním číselném převodu naleznete v tématu [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).

## <a name="formatting-decimal-output"></a>Formátování desítkového výstupu

Výsledky můžete naformátovat pomocí `String.Format` metodu, nebo prostřednictvím <xref:System.Console.Write%2A?displayProperty=nameWithType> metoda, která volá `String.Format()`. Formát měny je určen pomocí řetězce standardního formátu měny "C" nebo "c", jak je uvedeno v druhém příkladu dále v tomto článku. Další informace o `String.Format` metodu, najdete v článku <xref:System.String.Format%2A?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad způsobí chybu kompilátoru při kompilaci přidáním [double](../../../csharp/language-reference/keywords/double.md) a `decimal` proměnné.

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

Výsledkem je následující chyba:

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

V tomto příkladu `decimal` a [int](../../../csharp/language-reference/keywords/int.md) jsou kombinované ve stejném výrazu. Výsledek je vyhodnocen `decimal` typu.

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a>Příklad

V tomto příkladu je výstup naformátován pomocí řetězce formátu měny. Všimněte si, že `x` je zaokrouhlena, protože desetinná místa překračují hodnotu $0.99. Proměnná `y`, která představuje maximální přesné číslice, se zobrazí přesně ve správném formátu.

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- <xref:System.Decimal>  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)