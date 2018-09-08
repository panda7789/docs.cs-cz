---
title: Zápis dotazů LINQ v jazyce C#
description: Zjistěte, jak psát dotazy LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: 2ebba0d2d601932c976a88726fbe3ed37daffdcb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131669"
---
# <a name="write-linq-queries-in-c"></a>Zápis dotazů LINQ v jazyce C# #

Tento článek ukazuje tři způsoby, ve kterých můžete napsat dotaz LINQ v jazyce C#:

1. Použijte syntaxi dotazu.

2. Použití syntaxe využívající metody.

3. Pomocí kombinace syntaxi dotazů a syntaxe využívající metody.

Následující příklady ukazují některé jednoduchých dotazů LINQ pomocí jednotlivým přístupům uvedených výše. Obecně platí je pravidlo k použití (1) pokaždé, když je to možné a použijte (2) a (3), kdykoli je to zapotřebí.

> [!NOTE]
> Tyto dotazy provádět jednoduché kolekce v paměti; Základní syntaxe je však stejný jako, který používá v technologii LINQ to Entities a LINQ to XML.

## <a name="example---query-syntax"></a>Příklad: Syntaxe dotazu

Doporučeným způsobem, jak psát dotazy, většina je použití *syntaxe dotazu* vytvořit *výrazech dotazů*. Následující příklad ukazuje tři výrazy dotazu. První výraz dotazu ukazuje, jak filtrovat nebo omezit výsledky s použitím podmínky `where` klauzuli. Vrátí všechny prvky ze zdrojové sekvence, jejichž hodnoty jsou větší než 7 nebo menší než 3. Druhý výraz ukazuje, jak pořadí vrácených výsledků. Třetí výraz ukazuje, jak seskupení výsledků podle klíče. Tento dotaz vrátí dvě skupiny založené na první písmeno slova.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Všimněte si, že je typ dotazy <xref:System.Collections.Generic.IEnumerable%601>. Všechny tyto dotazy může být napsané s využitím `var` jak je znázorněno v následujícím příkladu:

`var query = from num in numbers...`

V obou příkladech předchozí dotazy neprovádět je ve skutečnosti dokud neprovedete iteraci v proměnné dotazu v `foreach` příkazu nebo další příkaz. Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Příklad – syntaxe využívající metody

Nějakých operací dotazů musí být vyjádřena jako volání metody. Nejběžnější tyto metody jsou ty, které vrátí číselné hodnoty typu singleton, jako například <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, a tak dále. Tyto metody musí být volána vždy poslední každého dotazu protože představují pouze jednu hodnotu a nemůže sloužit jako zdroj dalších dotazů operace. Následující příklad ukazuje volání metody ve výrazu dotazu:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Pokud metoda akce nebo Func parametry, ty jsou k dispozici ve formě [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) výrazu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

V předchozí dotazy okamžitě spustí jenom dotazu č. 4. Důvodem je, že vrátí jednu hodnotu a ne obecný <xref:System.Collections.Generic.IEnumerable%601> kolekce. Metoda sama musí používat `foreach` aby se Dal vypočítat jeho hodnotu.

Každý předchozí dotaz lze zapsat pomocí implicitního zápisu pomocí [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Příklad: smíšené syntaxe dotazu a – metoda

Tento příklad ukazuje způsob použití syntaxe využívající metody na výsledcích klauzule dotazu. Právě uzavřete do závorek výrazu dotazu a pak použijte operátor tečky a volání metody. V následujícím příkladu vrací dotaz #7 Počet čísel, jehož hodnota je dlouhý 3 až 7. Obecně platí ale je vhodnější použít druhé proměnné k ukládání výsledků volání metody. Dotaz tímto způsobem je méně pravděpodobné, že by se zaměňovat s výsledky dotazu.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Protože dotazu č. 7 vrátí jednu hodnotu a není kolekce, okamžitě spustí dotaz.

Předchozí dotaz lze zapsat pomocí implicitního zápisu pomocí `var`, následujícím způsobem:

```csharp
var numCount = (from num in numbers...
```

To je možné psát v syntaxe využívající metody následujícím způsobem:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Můžete je zapsat pomocí explicitní zadání, následujícím způsobem:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Viz také:

- [Návod: Zápis dotazů v jazyce C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [LINQ (Language Integrated Query)](index.md)
- [where – klauzule](../language-reference/keywords/where-clause.md)