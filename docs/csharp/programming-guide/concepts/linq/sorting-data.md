---
title: Řazení dat (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 78b263c384895b736b11cc524befa42b4a896380
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418192"
---
# <a name="sorting-data-c"></a><span data-ttu-id="d36eb-102">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="d36eb-102">Sorting Data (C#)</span></span>
<span data-ttu-id="d36eb-103">Operace řazení řadí prvky sekvence na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="d36eb-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="d36eb-104">První kritérium řazení provede primární řazení pro prvky.</span><span class="sxs-lookup"><span data-stu-id="d36eb-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="d36eb-105">Zadáním druhého kritéria řazení můžete prvky seřadit v rámci každé primární skupiny řazení.</span><span class="sxs-lookup"><span data-stu-id="d36eb-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="d36eb-106">Následující ilustrace znázorňuje výsledky abecední operace řazení na sekvenci znaků:</span><span class="sxs-lookup"><span data-stu-id="d36eb-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![Obrázek, který zobrazuje abecední operaci řazení.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="d36eb-108">Standardní metody operátoru dotazu, které řadí data, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="d36eb-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d36eb-109">Metody</span><span class="sxs-lookup"><span data-stu-id="d36eb-109">Methods</span></span>  
  
|<span data-ttu-id="d36eb-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="d36eb-110">Method Name</span></span>|<span data-ttu-id="d36eb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d36eb-111">Description</span></span>|<span data-ttu-id="d36eb-112">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="d36eb-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="d36eb-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="d36eb-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d36eb-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="d36eb-114">OrderBy</span></span>|<span data-ttu-id="d36eb-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d36eb-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="d36eb-116">OrderByDescending</span></span>|<span data-ttu-id="d36eb-117">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d36eb-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="d36eb-118">ThenBy</span></span>|<span data-ttu-id="d36eb-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d36eb-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="d36eb-120">ThenByDescending</span></span>|<span data-ttu-id="d36eb-121">Provede sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d36eb-122">Zpět</span><span class="sxs-lookup"><span data-stu-id="d36eb-122">Reverse</span></span>|<span data-ttu-id="d36eb-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d36eb-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="d36eb-124">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="d36eb-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d36eb-125">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="d36eb-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="d36eb-126">Primární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="d36eb-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="d36eb-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="d36eb-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="d36eb-128">Následující příklad ukazuje, jak použít klauzuli `orderby` v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="d36eb-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="d36eb-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="d36eb-130">Další příklad ukazuje, jak použít klauzuli `orderby descending` v dotazu LINQ k řazení řetězců podle jejich prvního písmena v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="d36eb-131">Sekundární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="d36eb-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="d36eb-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="d36eb-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="d36eb-133">Následující příklad ukazuje, jak použít klauzuli `orderby` v dotazu LINQ k provedení primárního a sekundárního řazení řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="d36eb-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="d36eb-134">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce, ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="d36eb-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="d36eb-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="d36eb-136">Další příklad ukazuje, jak použít klauzuli `orderby descending` v dotazu LINQ k provedení primárního řazení ve vzestupném pořadí a sekundárního řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d36eb-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="d36eb-137">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce.</span><span class="sxs-lookup"><span data-stu-id="d36eb-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d36eb-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d36eb-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d36eb-139">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="d36eb-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d36eb-140">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="d36eb-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="d36eb-141">Postupy: řazení výsledků klauzule JOIN</span><span class="sxs-lookup"><span data-stu-id="d36eb-141">How to: Order the Results of a Join Clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="d36eb-142">Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d36eb-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
