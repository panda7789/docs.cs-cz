---
title: Double – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 50e11e8547c2887ace677d2c86dcf055326ff9a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708152"
---
# <a name="double-c-reference"></a>double (Referenční dokumentace jazyka C#)

`double` – Klíčové slovo znamená jednoduchý typ, který ukládá 64bitové hodnoty s plovoucí desetinnou čárkou. V následující tabulce jsou uvedeny přesnosti a rozsahu pro `double` typu.

|Typ|Přibližný rozsah|Přesnost|Typ formátu .NET|
|----------|-----------------------|---------------|-------------------------|
|`double`|±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup>|~ 15-17 číslic|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Ve výchozím nastavení, skutečné číselný literál na pravé straně operátoru přiřazení je považován za `double`. Nicméně pokud chcete, aby celé číslo považován za `double`, použijte příponu d nebo D, například:

```csharp
double x = 3D;
```

## <a name="conversions"></a>Převody

Integrální číselné typy a typy s plovoucí desetinnou čárkou ve výrazu můžete kombinovat. V takovém případě integrální typy jsou převedeny na typy s plovoucí desetinnou čárkou. Vyhodnocení výrazu se provádí dle následujících pravidel:

- Pokud jeden z typů s plovoucí desetinnou čárkou je `double`, je výraz vyhodnocen `double`, nebo [bool](../../../csharp/language-reference/keywords/bool.md) v relačních porovnání a porovnání rovnosti.

- Pokud neexistuje žádné `double` typu ve výrazu, je vyhodnocen jako [float](../../../csharp/language-reference/keywords/float.md), nebo [bool](../../../csharp/language-reference/keywords/bool.md) v relačních porovnání a porovnání rovnosti.

 Výraz s plovoucí desetinnou čárkou může obsahovat následující sady hodnot:

- Kladnou a zápornou nulou.

- Kladné a záporné nekonečno.

- Hodnota not-a-Number (NaN).

- Konečná sada nenulové hodnoty.

Další informace o těchto hodnotách naleznete v části Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](https://www.ieee.org) webu.

## <a name="example"></a>Příklad

V následujícím příkladu [int](../../../csharp/language-reference/keywords/int.md), [krátký](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md)a `double` přidají dohromady `double` výsledek.

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [Tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md)
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tabulka typů s plovoucí desetinnou čárkou](../../../csharp/language-reference/keywords/floating-point-types-table.md)
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
