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
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="e34dc-103">Zápis dotazů LINQ v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="e34dc-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="e34dc-104">Tento článek ukazuje tři způsoby, jak můžete napsat dotaz LINQ v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="e34dc-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="e34dc-105">Použijte syntaxi dotazu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-105">Use query syntax.</span></span>

2. <span data-ttu-id="e34dc-106">Použijte syntaxi metody.</span><span class="sxs-lookup"><span data-stu-id="e34dc-106">Use method syntax.</span></span>

3. <span data-ttu-id="e34dc-107">Použijte kombinaci syntaxe dotazu a syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="e34dc-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="e34dc-108">Následující příklady ukazují některé jednoduché dotazy LINQ pomocí všech výše uvedených přístupů.</span><span class="sxs-lookup"><span data-stu-id="e34dc-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="e34dc-109">Obecně platí, že pravidlo má použít (1), kdykoli je to možné, a použít (2) a (3), kdykoli to bude nutné.</span><span class="sxs-lookup"><span data-stu-id="e34dc-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="e34dc-110">Tyto dotazy fungují na jednoduchých kolekcích v paměti; základní syntaxe je však shodná s tím, že se používá v LINQ to Entities a LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="e34dc-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="e34dc-111">Příklad – syntaxe dotazu</span><span class="sxs-lookup"><span data-stu-id="e34dc-111">Example - Query syntax</span></span>

<span data-ttu-id="e34dc-112">Doporučený způsob psaní většiny dotazů je použití *syntaxe dotazu* k vytváření *výrazů dotazů*.</span><span class="sxs-lookup"><span data-stu-id="e34dc-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="e34dc-113">Následující příklad ukazuje tři výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-113">The following example shows three query expressions.</span></span> <span data-ttu-id="e34dc-114">První výraz dotazu ukazuje, jak filtrovat nebo omezit výsledky použitím podmínek s `where` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="e34dc-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="e34dc-115">Vrátí všechny prvky ve zdrojové sekvenci, jejichž hodnoty jsou větší než 7 nebo menší než 3.</span><span class="sxs-lookup"><span data-stu-id="e34dc-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="e34dc-116">Druhý výraz ukazuje, jak seřadit vrácené výsledky.</span><span class="sxs-lookup"><span data-stu-id="e34dc-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="e34dc-117">Třetí výraz ukazuje, jak seskupit výsledky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="e34dc-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="e34dc-118">Tento dotaz vrátí dvě skupiny na základě prvního písmene slova.</span><span class="sxs-lookup"><span data-stu-id="e34dc-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="e34dc-119">Všimněte si, že typ dotazů je <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="e34dc-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e34dc-120">Všechny tyto dotazy mohou být vytvořeny pomocí `var` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e34dc-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="e34dc-121">V každém předchozím příkladu dotazy nejsou ve skutečnosti vykonány, dokud neprovedete iteraci nad proměnnou dotazu v `foreach` příkazu nebo jiném příkazu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="e34dc-122">Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="e34dc-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="e34dc-123">Příklad syntaxe metody</span><span class="sxs-lookup"><span data-stu-id="e34dc-123">Example - Method syntax</span></span>

<span data-ttu-id="e34dc-124">Některé operace dotazu musí být vyjádřeny jako volání metody.</span><span class="sxs-lookup"><span data-stu-id="e34dc-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="e34dc-125">Nejběžnější tyto metody jsou ty, které vracejí celočíselné číselné hodnoty, jako například <xref:System.Linq.Enumerable.Sum%2A> , <xref:System.Linq.Enumerable.Max%2A> , <xref:System.Linq.Enumerable.Min%2A> , <xref:System.Linq.Enumerable.Average%2A> a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e34dc-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="e34dc-126">Tyto metody musí být vždy volány jako poslední v jakémkoli dotazu, protože představují pouze jednu hodnotu a nemohou sloužit jako zdroj pro další operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="e34dc-127">Následující příklad ukazuje volání metody ve výrazu dotazu:</span><span class="sxs-lookup"><span data-stu-id="e34dc-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="e34dc-128">Pokud má metoda parametry Action nebo Func, jsou uvedeny ve formě výrazu [lambda](../language-reference/operators/lambda-expressions.md) , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e34dc-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../language-reference/operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="e34dc-129">V předchozích dotazech se okamžitě spustí dotaz #4.</span><span class="sxs-lookup"><span data-stu-id="e34dc-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="e34dc-130">Důvodem je, že vrací jedinou hodnotu, nikoli obecnou <xref:System.Collections.Generic.IEnumerable%601> kolekci.</span><span class="sxs-lookup"><span data-stu-id="e34dc-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="e34dc-131">Tato metoda musí být použita, aby bylo `foreach` možné vypočítat její hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="e34dc-132">Každý z předchozích dotazů lze zapsat pomocí implicitního zadání pomocí příkazu [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e34dc-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="e34dc-133">Příklad – smíšená syntaxe dotazů a metod</span><span class="sxs-lookup"><span data-stu-id="e34dc-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="e34dc-134">Tento příklad ukazuje, jak použít syntaxi metody u výsledků klauzule dotazu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="e34dc-135">Výraz dotazu uveďte pouze v závorkách a pak použijte operátor tečka a zavolejte metodu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="e34dc-136">V následujícím příkladu Query #7 vrátí počet čísel, jejichž hodnota je mezi 3 a 7.</span><span class="sxs-lookup"><span data-stu-id="e34dc-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="e34dc-137">Obecně je však lepší použít druhou proměnnou k uložení výsledku volání metody.</span><span class="sxs-lookup"><span data-stu-id="e34dc-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="e34dc-138">Tímto způsobem je dotaz méně pravděpodobný zaměňovat s výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="e34dc-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="e34dc-139">Vzhledem k tomu, že #7 dotazů vrací jedinou hodnotu, nikoli kolekci, dotaz se spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="e34dc-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="e34dc-140">Předchozí dotaz lze zapsat pomocí implicitního zápisu s následujícím `var` způsobem:</span><span class="sxs-lookup"><span data-stu-id="e34dc-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="e34dc-141">Lze ji zapsat v syntaxi metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e34dc-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="e34dc-142">Dá se zapsat pomocí explicitního psaní, a to takto:</span><span class="sxs-lookup"><span data-stu-id="e34dc-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="e34dc-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="e34dc-143">See also</span></span>

- [<span data-ttu-id="e34dc-144">Návod: zápis dotazů v jazyce C #</span><span class="sxs-lookup"><span data-stu-id="e34dc-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="e34dc-145">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="e34dc-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="e34dc-146">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="e34dc-146">where clause</span></span>](../language-reference/keywords/where-clause.md)
