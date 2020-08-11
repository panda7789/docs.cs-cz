---
title: Zápis dotazů LINQ v jazyce C#
description: Naučte se psát dotazy LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: bd7da81f2873c6a25570cab32fafecc66fd98be4
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063442"
---
# <a name="write-linq-queries-in-c"></a>Zápis dotazů LINQ v jazyce C\#

Tento článek ukazuje tři způsoby, jak můžete napsat dotaz LINQ v jazyce C#:

1. Použijte syntaxi dotazu.

2. Použijte syntaxi metody.

3. Použijte kombinaci syntaxe dotazu a syntaxe metody.

Následující příklady ukazují některé jednoduché dotazy LINQ pomocí všech výše uvedených přístupů. Obecně platí, že pravidlo má použít (1), kdykoli je to možné, a použít (2) a (3), kdykoli to bude nutné.

> [!NOTE]
> Tyto dotazy fungují na jednoduchých kolekcích v paměti; základní syntaxe je však shodná s tím, že se používá v LINQ to Entities a LINQ to XML.

## <a name="example---query-syntax"></a>Příklad – syntaxe dotazu

Doporučený způsob psaní většiny dotazů je použití *syntaxe dotazu* k vytváření *výrazů dotazů*. Následující příklad ukazuje tři výrazy dotazu. První výraz dotazu ukazuje, jak filtrovat nebo omezit výsledky použitím podmínek s `where` klauzulí. Vrátí všechny prvky ve zdrojové sekvenci, jejichž hodnoty jsou větší než 7 nebo menší než 3. Druhý výraz ukazuje, jak seřadit vrácené výsledky. Třetí výraz ukazuje, jak seskupit výsledky podle klíče. Tento dotaz vrátí dvě skupiny na základě prvního písmene slova.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Všimněte si, že typ dotazů je <xref:System.Collections.Generic.IEnumerable%601> . Všechny tyto dotazy mohou být vytvořeny pomocí `var` , jak je znázorněno v následujícím příkladu:

`var query = from num in numbers...`

V každém předchozím příkladu dotazy nejsou ve skutečnosti vykonány, dokud neprovedete iteraci nad proměnnou dotazu v `foreach` příkazu nebo jiném příkazu. Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Příklad syntaxe metody

Některé operace dotazu musí být vyjádřeny jako volání metody. Nejběžnější tyto metody jsou ty, které vracejí celočíselné číselné hodnoty, jako například <xref:System.Linq.Enumerable.Sum%2A> , <xref:System.Linq.Enumerable.Max%2A> , <xref:System.Linq.Enumerable.Min%2A> , <xref:System.Linq.Enumerable.Average%2A> a tak dále. Tyto metody musí být vždy volány jako poslední v jakémkoli dotazu, protože představují pouze jednu hodnotu a nemohou sloužit jako zdroj pro další operaci dotazu. Následující příklad ukazuje volání metody ve výrazu dotazu:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Pokud má metoda parametry Action nebo Func, jsou uvedeny ve formě výrazu [lambda](../language-reference/operators/lambda-expressions.md) , jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

V předchozích dotazech se okamžitě spustí dotaz #4. Důvodem je, že vrací jedinou hodnotu, nikoli obecnou <xref:System.Collections.Generic.IEnumerable%601> kolekci. Tato metoda musí být použita, aby bylo `foreach` možné vypočítat její hodnotu.

Každý z předchozích dotazů lze zapsat pomocí implicitního zadání pomocí příkazu [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Příklad – smíšená syntaxe dotazů a metod

Tento příklad ukazuje, jak použít syntaxi metody u výsledků klauzule dotazu. Výraz dotazu uveďte pouze v závorkách a pak použijte operátor tečka a zavolejte metodu. V následujícím příkladu Query #7 vrátí počet čísel, jejichž hodnota je mezi 3 a 7. Obecně je však lepší použít druhou proměnnou k uložení výsledku volání metody. Tímto způsobem je dotaz méně pravděpodobný zaměňovat s výsledky dotazu.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Vzhledem k tomu, že #7 dotazů vrací jedinou hodnotu, nikoli kolekci, dotaz se spustí okamžitě.

Předchozí dotaz lze zapsat pomocí implicitního zápisu s následujícím `var` způsobem:

```csharp
var numCount = (from num in numbers...
```

Lze ji zapsat v syntaxi metody následujícím způsobem:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Dá se zapsat pomocí explicitního psaní, a to takto:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Viz také

- [Návod: zápis dotazů v jazyce C #](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [LINQ (Language Integrated Query)](index.md)
- [where – klauzule](../language-reference/keywords/where-clause.md)
