---
title: Zápis dotazů LINQ v jazyce C#
description: Zjistěte, jak psát dotazy LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: 5003d1a5e15e17bea4204941d1c43895e3fb91f4
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403931"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="15319-103">Zápis dotazů LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="15319-103">Write LINQ queries in C#</span></span> #

<span data-ttu-id="15319-104">Tento článek ukazuje tři způsoby, ve kterých můžete napsat dotaz LINQ v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="15319-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="15319-105">Použijte syntaxi dotazu.</span><span class="sxs-lookup"><span data-stu-id="15319-105">Use query syntax.</span></span>

2. <span data-ttu-id="15319-106">Použití syntaxe využívající metody.</span><span class="sxs-lookup"><span data-stu-id="15319-106">Use method syntax.</span></span>

3. <span data-ttu-id="15319-107">Pomocí kombinace syntaxi dotazů a syntaxe využívající metody.</span><span class="sxs-lookup"><span data-stu-id="15319-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="15319-108">Následující příklady ukazují některé jednoduchých dotazů LINQ pomocí jednotlivým přístupům uvedených výše.</span><span class="sxs-lookup"><span data-stu-id="15319-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="15319-109">Obecně platí je pravidlo k použití (1) pokaždé, když je to možné a použijte (2) a (3), kdykoli je to zapotřebí.</span><span class="sxs-lookup"><span data-stu-id="15319-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="15319-110">Tyto dotazy provádět jednoduché kolekce v paměti; Základní syntaxe je však stejný jako, který používá v technologii LINQ to Entities a LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="15319-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="15319-111">Příklad: Syntaxe dotazu</span><span class="sxs-lookup"><span data-stu-id="15319-111">Example - Query syntax</span></span>

<span data-ttu-id="15319-112">Doporučeným způsobem, jak psát dotazy, většina je použití *syntaxe dotazu* vytvořit *výrazech dotazů*.</span><span class="sxs-lookup"><span data-stu-id="15319-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="15319-113">Následující příklad ukazuje tři výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="15319-113">The following example shows three query expressions.</span></span> <span data-ttu-id="15319-114">První výraz dotazu ukazuje, jak filtrovat nebo omezit výsledky s použitím podmínky `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="15319-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="15319-115">Vrátí všechny prvky ze zdrojové sekvence, jejichž hodnoty jsou větší než 7 nebo menší než 3.</span><span class="sxs-lookup"><span data-stu-id="15319-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="15319-116">Druhý výraz ukazuje, jak pořadí vrácených výsledků.</span><span class="sxs-lookup"><span data-stu-id="15319-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="15319-117">Třetí výraz ukazuje, jak seskupení výsledků podle klíče.</span><span class="sxs-lookup"><span data-stu-id="15319-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="15319-118">Tento dotaz vrátí dvě skupiny založené na první písmeno slova.</span><span class="sxs-lookup"><span data-stu-id="15319-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="15319-119">Všimněte si, že je typ dotazy <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="15319-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="15319-120">Všechny tyto dotazy může být napsané s využitím `var` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15319-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="15319-121">V obou příkladech předchozí dotazy neprovádět je ve skutečnosti dokud neprovedete iteraci v proměnné dotazu v `foreach` příkazu nebo další příkaz.</span><span class="sxs-lookup"><span data-stu-id="15319-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="15319-122">Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="15319-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="15319-123">Příklad – syntaxe využívající metody</span><span class="sxs-lookup"><span data-stu-id="15319-123">Example - Method syntax</span></span>

<span data-ttu-id="15319-124">Nějakých operací dotazů musí být vyjádřena jako volání metody.</span><span class="sxs-lookup"><span data-stu-id="15319-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="15319-125">Nejběžnější tyto metody jsou ty, které vrátí číselné hodnoty typu singleton, jako například <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="15319-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="15319-126">Tyto metody musí být volána vždy poslední každého dotazu protože představují pouze jednu hodnotu a nemůže sloužit jako zdroj dalších dotazů operace.</span><span class="sxs-lookup"><span data-stu-id="15319-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="15319-127">Následující příklad ukazuje volání metody ve výrazu dotazu:</span><span class="sxs-lookup"><span data-stu-id="15319-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="15319-128">Pokud metoda akce nebo Func parametry, ty jsou k dispozici ve formě [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) výrazu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15319-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="15319-129">V předchozí dotazy okamžitě spustí jenom dotazu č. 4.</span><span class="sxs-lookup"><span data-stu-id="15319-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="15319-130">Důvodem je, že vrátí jednu hodnotu a ne obecný <xref:System.Collections.Generic.IEnumerable%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="15319-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="15319-131">Metoda sama musí používat `foreach` aby se Dal vypočítat jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15319-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="15319-132">Každý předchozí dotaz lze zapsat pomocí implicitního zápisu pomocí [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15319-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="15319-133">Příklad: smíšené syntaxe dotazu a – metoda</span><span class="sxs-lookup"><span data-stu-id="15319-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="15319-134">Tento příklad ukazuje způsob použití syntaxe využívající metody na výsledcích klauzule dotazu.</span><span class="sxs-lookup"><span data-stu-id="15319-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="15319-135">Právě uzavřete do závorek výrazu dotazu a pak použijte operátor tečky a volání metody.</span><span class="sxs-lookup"><span data-stu-id="15319-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="15319-136">V následujícím příkladu vrací dotaz #7 Počet čísel, jehož hodnota je dlouhý 3 až 7.</span><span class="sxs-lookup"><span data-stu-id="15319-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="15319-137">Obecně platí ale je vhodnější použít druhé proměnné k ukládání výsledků volání metody.</span><span class="sxs-lookup"><span data-stu-id="15319-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="15319-138">Dotaz tímto způsobem je méně pravděpodobné, že by se zaměňovat s výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="15319-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="15319-139">Protože dotazu č. 7 vrátí jednu hodnotu a není kolekce, okamžitě spustí dotaz.</span><span class="sxs-lookup"><span data-stu-id="15319-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="15319-140">Předchozí dotaz lze zapsat pomocí implicitního zápisu pomocí `var`, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15319-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="15319-141">To je možné psát v syntaxe využívající metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15319-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="15319-142">Můžete je zapsat pomocí explicitní zadání, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15319-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="15319-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15319-143">See also</span></span>

<span data-ttu-id="15319-144">[Návod: Zápis dotazů v jazyce C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
[Language Integrated Query (LINQ)](index.md)
[kde – klauzule](../language-reference/keywords/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="15319-144">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
[Language Integrated Query (LINQ)](index.md)
[where clause](../language-reference/keywords/where-clause.md)</span></span>