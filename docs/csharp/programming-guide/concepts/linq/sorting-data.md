---
title: Řazení dat (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: bceb599d9e8eb3c51c07526b9ad22d3d4206efdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711939"
---
# <a name="sorting-data-c"></a><span data-ttu-id="fdc82-102">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="fdc82-102">Sorting Data (C#)</span></span>
<span data-ttu-id="fdc82-103">Operace řazení Seřadí prvky pořadí na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="fdc82-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="fdc82-104">První kritérium řazení provede primární řazení elementů.</span><span class="sxs-lookup"><span data-stu-id="fdc82-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="fdc82-105">Zadáním druhý kritérium řazení, lze řazení elementů v rámci jednotlivých skupin primární řazení.</span><span class="sxs-lookup"><span data-stu-id="fdc82-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="fdc82-106">Následující obrázek znázorňuje výsledky operace abecední řazení na sekvenci znaků:</span><span class="sxs-lookup"><span data-stu-id="fdc82-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![Obrázek znázorňující, operace abecední řazení.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="fdc82-108">Standardní metody operátoru dotazu, které řazení dat jsou uvedené v následující části.</span><span class="sxs-lookup"><span data-stu-id="fdc82-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdc82-109">Metody</span><span class="sxs-lookup"><span data-stu-id="fdc82-109">Methods</span></span>  
  
|<span data-ttu-id="fdc82-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="fdc82-110">Method Name</span></span>|<span data-ttu-id="fdc82-111">Popis</span><span class="sxs-lookup"><span data-stu-id="fdc82-111">Description</span></span>|<span data-ttu-id="fdc82-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fdc82-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="fdc82-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="fdc82-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="fdc82-114">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="fdc82-114">OrderBy</span></span>|<span data-ttu-id="fdc82-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdc82-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fdc82-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="fdc82-116">OrderByDescending</span></span>|<span data-ttu-id="fdc82-117">Seřadí v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdc82-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fdc82-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="fdc82-118">ThenBy</span></span>|<span data-ttu-id="fdc82-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdc82-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fdc82-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="fdc82-120">ThenByDescending</span></span>|<span data-ttu-id="fdc82-121">Provádí sekundární seřadit v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdc82-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fdc82-122">reverzní</span><span class="sxs-lookup"><span data-stu-id="fdc82-122">Reverse</span></span>|<span data-ttu-id="fdc82-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="fdc82-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="fdc82-124">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fdc82-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="fdc82-125">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="fdc82-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="fdc82-126">Příklady primárních řazení</span><span class="sxs-lookup"><span data-stu-id="fdc82-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="fdc82-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="fdc82-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="fdc82-128">Následující příklad ukazuje způsob použití `orderby` klauzule v dotazu LINQ a řetězce v poli řadit délka řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdc82-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="fdc82-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="fdc82-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="fdc82-130">Následující příklad ukazuje, jak používat `orderby descending` klauzule v dotazu LINQ a řetězce řadit v sestupném pořadí podle jejich první písmeno.</span><span class="sxs-lookup"><span data-stu-id="fdc82-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="fdc82-131">Příklady sekundární řazení</span><span class="sxs-lookup"><span data-stu-id="fdc82-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="fdc82-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="fdc82-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="fdc82-133">Následující příklad ukazuje způsob použití `orderby` klauzule v dotazu LINQ provádět primární a sekundární řazení řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="fdc82-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="fdc82-134">Řetězce jsou seřazeny podle délky primárně a sekundárně první písmeno řetězce, oba ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdc82-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="fdc82-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="fdc82-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="fdc82-136">Následující příklad ukazuje, jak používat `orderby descending` klauzule v dotazu LINQ provádět primární řazení ve vzestupném pořadí a sekundární řazení, v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdc82-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="fdc82-137">Řetězce jsou seřazeny především podle délky a sekundárně první písmeno řetězce.</span><span class="sxs-lookup"><span data-stu-id="fdc82-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fdc82-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdc82-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fdc82-139">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="fdc82-139">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="fdc82-140">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="fdc82-140">orderby clause</span></span>](../../../../csharp/language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="fdc82-141">Postupy: Řazení výsledků Klauzule Join</span><span class="sxs-lookup"><span data-stu-id="fdc82-141">How to: Order the Results of a Join Clause</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="fdc82-142">Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fdc82-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
