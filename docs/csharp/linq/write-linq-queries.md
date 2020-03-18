---
title: Zápis dotazů LINQ v jazyce C#
description: Naučte se psát dotazy LINQ v c#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: ed32543b0422e0664a8577f2c27f7c7c00a719a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632881"
---
# <a name="write-linq-queries-in-c"></a>Zápis dotazů LINQ v c\#

Tento článek ukazuje tři způsoby, ve kterém můžete napsat dotaz LINQ v C#:

1. Použijte syntaxi dotazu.

2. Použijte syntaxi metody.

3. Použijte kombinaci syntaxe dotazu a syntaxe metody.

Následující příklady ukazují některé jednoduché linq dotazy pomocí každého přístupu uvedeného výše. Obecně platí, že pravidlo je použití (1) kdykoli je to možné, a použití (2) a (3) kdykoli je to nutné.

> [!NOTE]
> Tyto dotazy pracovat na jednoduché kolekce v paměti; základní syntaxe je však shodná se syntaxí použitou v LINQ na entity a LINQ na XML.

## <a name="example---query-syntax"></a>Příklad – syntaxe dotazu

Doporučený způsob, jak psát většinu dotazů, je použít *syntaxi dotazu* k vytvoření *výrazů dotazu*. Následující příklad ukazuje tři výrazy dotazu. První výraz dotazu ukazuje, jak filtrovat nebo `where` omezit výsledky použitím podmínek s klauzulí. Vrátí všechny prvky ve zdrojové sekvenci, jejichž hodnoty jsou větší než 7 nebo menší než 3. Druhý výraz ukazuje, jak objednat vrácené výsledky. Třetí výraz ukazuje, jak seskupit výsledky podle klíče. Tento dotaz vrátí dvě skupiny na základě prvního písmene slova.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Všimněte si, že typ <xref:System.Collections.Generic.IEnumerable%601>dotazů je . Všechny tyto dotazy mohou být `var` zapsány pomocí, jak je znázorněno v následujícím příkladu:

`var query = from num in numbers...`

V každém předchozím příkladu se dotazy ve skutečnosti nespustí, dokud `foreach` itetovat přes proměnnou dotazu v příkazu nebo jiné ho příkazu. Další informace naleznete [v tématu Úvod do linq dotazy](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Příklad - syntaxe metody

Některé operace dotazu musí být vyjádřeny jako volání metody. Nejběžnější takové metody jsou ty, které vracejí číselné <xref:System.Linq.Enumerable.Sum%2A> <xref:System.Linq.Enumerable.Max%2A>hodnoty <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Average%2A>singleton, například , , , a tak dále. Tyto metody musí být vždy volány jako poslední v libovolném dotazu, protože představují pouze jednu hodnotu a nemohou sloužit jako zdroj pro další operaci dotazu. Následující příklad ukazuje volání metody ve výrazu dotazu:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Pokud má metoda action nebo Func parametry, jsou poskytovány ve formě [výrazu lambda,](../programming-guide/statements-expressions-operators/lambda-expressions.md) jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

V předchozích dotazech pouze dotaz #4 spustí okamžitě. Důvodem je, že vrátí jednu <xref:System.Collections.Generic.IEnumerable%601> hodnotu a není obecné kolekce. Samotná metoda musí `foreach` použít k výpočtu jeho hodnotu.

Každý z předchozích dotazů lze zapsat pomocí implicitního psaní s [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Příklad – syntaxe smíšeného dotazu a metody

Tento příklad ukazuje, jak používat syntaxi metody na výsledky klauzule dotazu. Stačí uzavřít výraz dotazu do závorek a potom použít operátor tečky a volat metodu. V následujícím příkladu vrátí dotaz #7 počet čísel, jejichž hodnota je mezi 3 a 7. Obecně je však lepší použít druhou proměnnou k uložení výsledku volání metody. Tímto způsobem dotaz je méně pravděpodobné, že budou zaměňovány s výsledky dotazu.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Vzhledem k tomu, že dotaz #7 vrátí jednu hodnotu a nikoli kolekci, dotaz se spustí okamžitě.

Předchozí dotaz lze zapsat pomocí implicitního psaní s `var`, takto:

```csharp
var numCount = (from num in numbers...
```

To může být napsáno v syntaxi metody takto:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

To může být napsáno pomocí explicitního psaní, takto:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Viz také

- [Návod: Psaní dotazů v C #](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [LINQ (Language Integrated Query)](index.md)
- [where – klauzule](../language-reference/keywords/where-clause.md)
