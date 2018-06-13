---
title: Zápis dotazů LINQ v C#
description: Tom, jak psát dotazy.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: a9683dbf3c4101829054477824ccc7135f20f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288834"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="90860-103">Zápis dotazů LINQ v C#</span><span class="sxs-lookup"><span data-stu-id="90860-103">Write LINQ queries in C#</span></span>

<span data-ttu-id="90860-104">Toto téma ukazuje tři způsoby, ve kterých můžete napsat dotaz LINQ v jazyku C#:</span><span class="sxs-lookup"><span data-stu-id="90860-104">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="90860-105">Použijte syntaxi dotazu.</span><span class="sxs-lookup"><span data-stu-id="90860-105">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="90860-106">Pomocí syntaxe využívající metody.</span><span class="sxs-lookup"><span data-stu-id="90860-106">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="90860-107">Použijte kombinaci syntaxe dotazů a syntaxe využívající metody.</span><span class="sxs-lookup"><span data-stu-id="90860-107">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="90860-108">Následující příklady ukazují několik jednoduchých dotazů LINQ s použitím každý přístup uvedených výše.</span><span class="sxs-lookup"><span data-stu-id="90860-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="90860-109">Obecně platí je pravidlo k použití (1) Pokud je to možné a použijte (2) a (3), kdykoli je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="90860-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90860-110">Tyto dotazy pracovat na kolekce v paměti jednoduchých; Základní syntaxe je ale stejná jako v technologii LINQ to Entities a technologie LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="90860-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90860-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="90860-111">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="90860-112">Syntaxe dotazu</span><span class="sxs-lookup"><span data-stu-id="90860-112">Query syntax</span></span>  
 <span data-ttu-id="90860-113">Doporučeným způsobem, jak psát dotazy většina je použití *syntaxe dotazu* k vytvoření *dotaz výrazy*.</span><span class="sxs-lookup"><span data-stu-id="90860-113">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="90860-114">Následující příklad ukazuje tři výrazy dotazů.</span><span class="sxs-lookup"><span data-stu-id="90860-114">The following example shows three query expressions.</span></span> <span data-ttu-id="90860-115">První výraz dotazu, který ukazuje, jak filtrovat nebo omezit použitím podmínky s výsledky `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="90860-115">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="90860-116">Vrátí všechny elementy ve zdrojové sekvence, jejichž hodnoty jsou větší než 7 nebo menší než 3.</span><span class="sxs-lookup"><span data-stu-id="90860-116">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="90860-117">Výraz druhé, který ukazuje, jak pořadí vrácených výsledků.</span><span class="sxs-lookup"><span data-stu-id="90860-117">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="90860-118">Třetí výraz ukazuje, jak seskupení výsledků podle klíče.</span><span class="sxs-lookup"><span data-stu-id="90860-118">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="90860-119">Tento dotaz vrací dvě skupiny založené na první písmeno aplikace word.</span><span class="sxs-lookup"><span data-stu-id="90860-119">This query returns two groups based on the first letter of the word.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 <span data-ttu-id="90860-120">Všimněte si, že je typ dotazy <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="90860-120">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="90860-121">Všechny tyto dotazy lze zapsat pomocí `var` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90860-121">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="90860-122">V každé předchozí příklad, dotazy se neprovedou ve skutečnosti dokud iterace v proměnné dotazu v `foreach` nebo jiných příkaz.</span><span class="sxs-lookup"><span data-stu-id="90860-122">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="90860-123">Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="90860-123">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90860-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="90860-124">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="90860-125">Syntaxe využívající metody</span><span class="sxs-lookup"><span data-stu-id="90860-125">Method syntax</span></span>  
 <span data-ttu-id="90860-126">Některé operace dotazů musí být vyjádřena jako volání metody.</span><span class="sxs-lookup"><span data-stu-id="90860-126">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="90860-127">Nejběžnější tyto metody jsou ty, které vracejí číselné hodnoty typu singleton, jako například <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>a tak dále.</span><span class="sxs-lookup"><span data-stu-id="90860-127">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="90860-128">Tyto metody musí vždy volat poslední v jakýkoli dotaz proto, že představují pouze jednu hodnotu a nemůže sloužit jako zdroj pro operace další dotaz.</span><span class="sxs-lookup"><span data-stu-id="90860-128">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="90860-129">Následující příklad ukazuje volání metody ve výrazu dotazu:</span><span class="sxs-lookup"><span data-stu-id="90860-129">The following example shows a method call in a query expression:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="90860-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="90860-130">Example</span></span>  
 <span data-ttu-id="90860-131">Pokud metoda akce nebo Func parametry, tyto položky jsou poskytovány ve formě [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) výrazu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90860-131">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 <span data-ttu-id="90860-132">V předchozí dotazy okamžitě spustí jenom dotazu č. 4.</span><span class="sxs-lookup"><span data-stu-id="90860-132">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="90860-133">Důvodem je, že vrátí jednu hodnotu a ne obecný <xref:System.Collections.Generic.IEnumerable%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="90860-133">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="90860-134">Metoda sama musí používat `foreach` aby se Dal vypočítat jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90860-134">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="90860-135">Každý dotaz na předchozí můžete zapsat pomocí implicitní zadáním s [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90860-135">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="90860-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="90860-136">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="90860-137">Smíšená syntaxe dotazů a – metoda</span><span class="sxs-lookup"><span data-stu-id="90860-137">Mixed query and method syntax</span></span>  
 <span data-ttu-id="90860-138">Tento příklad ukazuje způsob použití syntaxe využívající metody na výsledky dotazu klauzule.</span><span class="sxs-lookup"><span data-stu-id="90860-138">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="90860-139">Právě uzavřete výrazu dotazu v závorkách a pak použít operátor tečky a volat metodu.</span><span class="sxs-lookup"><span data-stu-id="90860-139">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="90860-140">V následujícím příkladu vrací dotaz #7 počet čísla, jehož hodnota je 3 až 7.</span><span class="sxs-lookup"><span data-stu-id="90860-140">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="90860-141">Obecně platí ale je lepší ukládat výsledek volání metody do druhé proměnné.</span><span class="sxs-lookup"><span data-stu-id="90860-141">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="90860-142">Tímto způsobem dotaz je méně pravděpodobné, že nelze zaměňovat s výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="90860-142">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 <span data-ttu-id="90860-143">Protože 7 dotaz vrátí jednu hodnotu a není kolekce, dotaz se spustí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="90860-143">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="90860-144">Předchozí dotaz můžete zapsat pomocí implicitní zadáním s `var`, a to takto:</span><span class="sxs-lookup"><span data-stu-id="90860-144">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="90860-145">Ho může být napsán v syntaxe využívající metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="90860-145">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="90860-146">Může být napsán pomocí explicitní zadáte, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="90860-146">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="90860-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="90860-147">See Also</span></span>  
  <span data-ttu-id="90860-148">[Návod: Zápis dotazů v C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="90860-148">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 [<span data-ttu-id="90860-149">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="90860-149">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="90860-150">where – klauzule</span><span class="sxs-lookup"><span data-stu-id="90860-150">where clause</span></span>](../language-reference/keywords/where-clause.md)
