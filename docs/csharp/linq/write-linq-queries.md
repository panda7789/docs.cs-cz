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
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="d39ba-103">Zápis dotazů LINQ v c\#</span><span class="sxs-lookup"><span data-stu-id="d39ba-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="d39ba-104">Tento článek ukazuje tři způsoby, ve kterém můžete napsat dotaz LINQ v C#:</span><span class="sxs-lookup"><span data-stu-id="d39ba-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="d39ba-105">Použijte syntaxi dotazu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-105">Use query syntax.</span></span>

2. <span data-ttu-id="d39ba-106">Použijte syntaxi metody.</span><span class="sxs-lookup"><span data-stu-id="d39ba-106">Use method syntax.</span></span>

3. <span data-ttu-id="d39ba-107">Použijte kombinaci syntaxe dotazu a syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="d39ba-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="d39ba-108">Následující příklady ukazují některé jednoduché linq dotazy pomocí každého přístupu uvedeného výše.</span><span class="sxs-lookup"><span data-stu-id="d39ba-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="d39ba-109">Obecně platí, že pravidlo je použití (1) kdykoli je to možné, a použití (2) a (3) kdykoli je to nutné.</span><span class="sxs-lookup"><span data-stu-id="d39ba-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="d39ba-110">Tyto dotazy pracovat na jednoduché kolekce v paměti; základní syntaxe je však shodná se syntaxí použitou v LINQ na entity a LINQ na XML.</span><span class="sxs-lookup"><span data-stu-id="d39ba-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="d39ba-111">Příklad – syntaxe dotazu</span><span class="sxs-lookup"><span data-stu-id="d39ba-111">Example - Query syntax</span></span>

<span data-ttu-id="d39ba-112">Doporučený způsob, jak psát většinu dotazů, je použít *syntaxi dotazu* k vytvoření *výrazů dotazu*.</span><span class="sxs-lookup"><span data-stu-id="d39ba-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="d39ba-113">Následující příklad ukazuje tři výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-113">The following example shows three query expressions.</span></span> <span data-ttu-id="d39ba-114">První výraz dotazu ukazuje, jak filtrovat nebo `where` omezit výsledky použitím podmínek s klauzulí.</span><span class="sxs-lookup"><span data-stu-id="d39ba-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="d39ba-115">Vrátí všechny prvky ve zdrojové sekvenci, jejichž hodnoty jsou větší než 7 nebo menší než 3.</span><span class="sxs-lookup"><span data-stu-id="d39ba-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="d39ba-116">Druhý výraz ukazuje, jak objednat vrácené výsledky.</span><span class="sxs-lookup"><span data-stu-id="d39ba-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="d39ba-117">Třetí výraz ukazuje, jak seskupit výsledky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="d39ba-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="d39ba-118">Tento dotaz vrátí dvě skupiny na základě prvního písmene slova.</span><span class="sxs-lookup"><span data-stu-id="d39ba-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="d39ba-119">Všimněte si, že typ <xref:System.Collections.Generic.IEnumerable%601>dotazů je .</span><span class="sxs-lookup"><span data-stu-id="d39ba-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d39ba-120">Všechny tyto dotazy mohou být `var` zapsány pomocí, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d39ba-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="d39ba-121">V každém předchozím příkladu se dotazy ve skutečnosti nespustí, dokud `foreach` itetovat přes proměnnou dotazu v příkazu nebo jiné ho příkazu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="d39ba-122">Další informace naleznete [v tématu Úvod do linq dotazy](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d39ba-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="d39ba-123">Příklad - syntaxe metody</span><span class="sxs-lookup"><span data-stu-id="d39ba-123">Example - Method syntax</span></span>

<span data-ttu-id="d39ba-124">Některé operace dotazu musí být vyjádřeny jako volání metody.</span><span class="sxs-lookup"><span data-stu-id="d39ba-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="d39ba-125">Nejběžnější takové metody jsou ty, které vracejí číselné <xref:System.Linq.Enumerable.Sum%2A> <xref:System.Linq.Enumerable.Max%2A>hodnoty <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Average%2A>singleton, například , , , a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d39ba-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="d39ba-126">Tyto metody musí být vždy volány jako poslední v libovolném dotazu, protože představují pouze jednu hodnotu a nemohou sloužit jako zdroj pro další operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="d39ba-127">Následující příklad ukazuje volání metody ve výrazu dotazu:</span><span class="sxs-lookup"><span data-stu-id="d39ba-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="d39ba-128">Pokud má metoda action nebo Func parametry, jsou poskytovány ve formě [výrazu lambda,](../programming-guide/statements-expressions-operators/lambda-expressions.md) jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d39ba-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="d39ba-129">V předchozích dotazech pouze dotaz #4 spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="d39ba-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="d39ba-130">Důvodem je, že vrátí jednu <xref:System.Collections.Generic.IEnumerable%601> hodnotu a není obecné kolekce.</span><span class="sxs-lookup"><span data-stu-id="d39ba-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="d39ba-131">Samotná metoda musí `foreach` použít k výpočtu jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="d39ba-132">Každý z předchozích dotazů lze zapsat pomocí implicitního psaní s [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d39ba-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="d39ba-133">Příklad – syntaxe smíšeného dotazu a metody</span><span class="sxs-lookup"><span data-stu-id="d39ba-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="d39ba-134">Tento příklad ukazuje, jak používat syntaxi metody na výsledky klauzule dotazu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="d39ba-135">Stačí uzavřít výraz dotazu do závorek a potom použít operátor tečky a volat metodu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="d39ba-136">V následujícím příkladu vrátí dotaz #7 počet čísel, jejichž hodnota je mezi 3 a 7.</span><span class="sxs-lookup"><span data-stu-id="d39ba-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="d39ba-137">Obecně je však lepší použít druhou proměnnou k uložení výsledku volání metody.</span><span class="sxs-lookup"><span data-stu-id="d39ba-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="d39ba-138">Tímto způsobem dotaz je méně pravděpodobné, že budou zaměňovány s výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="d39ba-139">Vzhledem k tomu, že dotaz #7 vrátí jednu hodnotu a nikoli kolekci, dotaz se spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="d39ba-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="d39ba-140">Předchozí dotaz lze zapsat pomocí implicitního psaní s `var`, takto:</span><span class="sxs-lookup"><span data-stu-id="d39ba-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="d39ba-141">To může být napsáno v syntaxi metody takto:</span><span class="sxs-lookup"><span data-stu-id="d39ba-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="d39ba-142">To může být napsáno pomocí explicitního psaní, takto:</span><span class="sxs-lookup"><span data-stu-id="d39ba-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="d39ba-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="d39ba-143">See also</span></span>

- [<span data-ttu-id="d39ba-144">Návod: Psaní dotazů v C #</span><span class="sxs-lookup"><span data-stu-id="d39ba-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="d39ba-145">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="d39ba-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="d39ba-146">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="d39ba-146">where clause</span></span>](../language-reference/keywords/where-clause.md)
