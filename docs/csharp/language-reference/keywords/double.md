---
title: Double – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 8e3a94bb79d46f2815e46b86f1aca92acc73e5c2
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027847"
---
# <a name="double-c-reference"></a>double (Referenční dokumentace jazyka C#)

`double` – Klíčové slovo označuje jednoduchý typ, který ukládá 64bitové hodnoty s plovoucí desetinnou čárkou. Následující tabulka uvádí přesnost a přibližnou rozsah `double` typu.

|Typ|Přibližná rozsahu|Přesnost|Typ formátu .NET|
|----------|-----------------------|---------------|-------------------------|
|`double`|±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup>|15 až 16 číslic|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Ve výchozím nastavení, je skutečně číselný literál na pravé straně operátoru přiřazení považován za `double`. Ale pokud budete chtít celé číslo považován za `double`, použít přípona d nebo D, například:

```csharp
double x = 3D;
```

## <a name="conversions"></a>Převody

Je možné kombinovat číselné integrální typy a typy s plovoucí desetinnou čárkou ve výrazu. Celočíselné typy v tomto případě se převedou na typy s plovoucí desetinnou čárkou. Vyhodnocení výrazu se provádí podle následujících pravidel:

- Pokud jeden z typů s plovoucí desetinnou čárkou je `double`, výsledkem výrazu `double`, nebo [bool](../../../csharp/language-reference/keywords/bool.md) ve výrazech relační nebo logická hodnota.

- Pokud je žádné `double` typ výrazu, vyhodnotí k [float](../../../csharp/language-reference/keywords/float.md), nebo [bool](../../../csharp/language-reference/keywords/bool.md) ve výrazech relační nebo logická hodnota.

 Výraz s plovoucí desetinnou čárkou mohou obsahovat následující sady hodnot:

- Kladné a záporné nuly.

- Kladné a záporné nekonečno.

- Hodnota not-a-Number (NaN).

- Omezená sada nenulové hodnoty.

Další informace o těchto hodnotách naleznete v tématu Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](https://www.ieee.org) webu.

## <a name="example"></a>Příklad

V následujícím příkladu se [int](../../../csharp/language-reference/keywords/int.md), [krátké](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md)a `double` přidají dohromady `double` výsledek.

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[Tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md)  
[Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[Tabulka typů s plovoucí desetinnou čárkou](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
[Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
