---
title: Řazení dat (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 29a5e3e685bdc73536961b7783f4986796b46bdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167904"
---
# <a name="sorting-data-c"></a><span data-ttu-id="501d1-102">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="501d1-102">Sorting Data (C#)</span></span>
<span data-ttu-id="501d1-103">Operace řazení objednávky prvky sekvence na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="501d1-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="501d1-104">První kritérium řazení provádí primární řazení na prvky.</span><span class="sxs-lookup"><span data-stu-id="501d1-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="501d1-105">Zadáním druhého kritéria řazení můžete třídit prvky v rámci každé primární skupiny řazení.</span><span class="sxs-lookup"><span data-stu-id="501d1-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="501d1-106">Následující obrázek znázorňuje výsledky abecední operace řazení na posloupnost znaků:</span><span class="sxs-lookup"><span data-stu-id="501d1-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Grafika znázorněná abecední řazení.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="501d1-108">Standardní metody operátoru dotazu, které řadí data jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="501d1-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="501d1-109">Metody</span><span class="sxs-lookup"><span data-stu-id="501d1-109">Methods</span></span>  
  
|<span data-ttu-id="501d1-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="501d1-110">Method Name</span></span>|<span data-ttu-id="501d1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="501d1-111">Description</span></span>|<span data-ttu-id="501d1-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="501d1-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="501d1-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="501d1-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="501d1-114">Orderby</span><span class="sxs-lookup"><span data-stu-id="501d1-114">OrderBy</span></span>|<span data-ttu-id="501d1-115">Seřadí hodnoty vzestupně.</span><span class="sxs-lookup"><span data-stu-id="501d1-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="501d1-116">Orderbydescending</span><span class="sxs-lookup"><span data-stu-id="501d1-116">OrderByDescending</span></span>|<span data-ttu-id="501d1-117">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="501d1-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="501d1-118">Thenby</span><span class="sxs-lookup"><span data-stu-id="501d1-118">ThenBy</span></span>|<span data-ttu-id="501d1-119">Provádí sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="501d1-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="501d1-120">Thenbydescending</span><span class="sxs-lookup"><span data-stu-id="501d1-120">ThenByDescending</span></span>|<span data-ttu-id="501d1-121">Provádí sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="501d1-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="501d1-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="501d1-122">Reverse</span></span>|<span data-ttu-id="501d1-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="501d1-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="501d1-124">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="501d1-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="501d1-125">Příklady syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="501d1-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="501d1-126">Příklady primárního řazení</span><span class="sxs-lookup"><span data-stu-id="501d1-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="501d1-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="501d1-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="501d1-128">Následující příklad ukazuje, jak `orderby` použít klauzuli v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="501d1-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="501d1-129">Primární sestupně řazení</span><span class="sxs-lookup"><span data-stu-id="501d1-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="501d1-130">Následující příklad ukazuje, jak `orderby descending` použít klauzuli v dotazu LINQ seřadit řetězce podle jejich první písmeno, v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="501d1-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="501d1-131">Příklady sekundárního řazení</span><span class="sxs-lookup"><span data-stu-id="501d1-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="501d1-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="501d1-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="501d1-133">Následující příklad ukazuje, jak `orderby` použít klauzuli v dotazu LINQ k provedení primárního a sekundárního druhu řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="501d1-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="501d1-134">Řetězce jsou seřazeny především podle délky a sekundárně podle prvního písmene řetězce, a to jak ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="501d1-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="501d1-135">Sekundární sestupně řazení</span><span class="sxs-lookup"><span data-stu-id="501d1-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="501d1-136">Následující příklad ukazuje, jak `orderby descending` použít klauzuli v dotazu LINQ k provedení primárnířazení, vzestupně a sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="501d1-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="501d1-137">Řetězce jsou seřazeny především podle délky a sekundárně podle prvního písmene řetězce.</span><span class="sxs-lookup"><span data-stu-id="501d1-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="501d1-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="501d1-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="501d1-139">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="501d1-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="501d1-140">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="501d1-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="501d1-141">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="501d1-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="501d1-142">Jak řadit nebo filtrovat textová data podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="501d1-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
