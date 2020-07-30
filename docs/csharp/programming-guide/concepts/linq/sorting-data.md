---
title: Řazení dat (C#)
description: Přečtěte si o operacích řazení a metodách standardního operátoru dotazu, které provádějí operace řazení v LINQ v jazyce C#.
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 5feeb0e2229fc370fdcb9608817f41832bffd7cc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302331"
---
# <a name="sorting-data-c"></a><span data-ttu-id="ad82a-103">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="ad82a-103">Sorting Data (C#)</span></span>
<span data-ttu-id="ad82a-104">Operace řazení řadí prvky sekvence na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="ad82a-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="ad82a-105">První kritérium řazení provede primární řazení pro prvky.</span><span class="sxs-lookup"><span data-stu-id="ad82a-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="ad82a-106">Zadáním druhého kritéria řazení můžete prvky seřadit v rámci každé primární skupiny řazení.</span><span class="sxs-lookup"><span data-stu-id="ad82a-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="ad82a-107">Následující ilustrace znázorňuje výsledky abecední operace řazení na sekvenci znaků:</span><span class="sxs-lookup"><span data-stu-id="ad82a-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Obrázek, který zobrazuje abecední operaci řazení.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="ad82a-109">Standardní metody operátoru dotazu, které řadí data, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="ad82a-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad82a-110">Metody</span><span class="sxs-lookup"><span data-stu-id="ad82a-110">Methods</span></span>  
  
|<span data-ttu-id="ad82a-111">Název metody</span><span class="sxs-lookup"><span data-stu-id="ad82a-111">Method Name</span></span>|<span data-ttu-id="ad82a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ad82a-112">Description</span></span>|<span data-ttu-id="ad82a-113">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ad82a-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="ad82a-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="ad82a-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ad82a-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="ad82a-115">OrderBy</span></span>|<span data-ttu-id="ad82a-116">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ad82a-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="ad82a-117">OrderByDescending</span></span>|<span data-ttu-id="ad82a-118">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ad82a-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="ad82a-119">ThenBy</span></span>|<span data-ttu-id="ad82a-120">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ad82a-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="ad82a-121">ThenByDescending</span></span>|<span data-ttu-id="ad82a-122">Provede sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ad82a-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="ad82a-123">Reverse</span></span>|<span data-ttu-id="ad82a-124">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ad82a-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="ad82a-125">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ad82a-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ad82a-126">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="ad82a-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="ad82a-127">Primární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="ad82a-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="ad82a-128">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ad82a-128">Primary Ascending Sort</span></span>  
 <span data-ttu-id="ad82a-129">Následující příklad ukazuje, jak použít `orderby` klauzuli v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="ad82a-130">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ad82a-130">Primary Descending Sort</span></span>  
 <span data-ttu-id="ad82a-131">Další příklad ukazuje, jak použít `orderby descending` klauzuli v dotazu LINQ k řazení řetězců podle jejich prvního písmena v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="ad82a-132">Sekundární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="ad82a-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="ad82a-133">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ad82a-133">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="ad82a-134">Následující příklad ukazuje, jak použít `orderby` klauzuli v dotazu LINQ k provedení primárního a sekundárního řazení řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="ad82a-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="ad82a-135">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce, ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="ad82a-136">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ad82a-136">Secondary Descending Sort</span></span>  
 <span data-ttu-id="ad82a-137">Další příklad ukazuje, jak použít `orderby descending` klauzuli v dotazu LINQ k provedení primárního řazení ve vzestupném pořadí a sekundárního řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ad82a-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="ad82a-138">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce.</span><span class="sxs-lookup"><span data-stu-id="ad82a-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad82a-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad82a-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ad82a-140">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="ad82a-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ad82a-141">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="ad82a-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="ad82a-142">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="ad82a-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="ad82a-143">Postup řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ad82a-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
