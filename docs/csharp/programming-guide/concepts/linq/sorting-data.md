---
title: "Řazení dat (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f5756c87f50e759542d0d1ccbb71710ad9eb6e27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-c"></a><span data-ttu-id="55589-102">Řazení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="55589-102">Sorting Data (C#)</span></span>
<span data-ttu-id="55589-103">Operace řazení řadí elementy pořadí na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="55589-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="55589-104">První kritérium řazení provede primární řazení elementů.</span><span class="sxs-lookup"><span data-stu-id="55589-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="55589-105">Zadáním druhý kritérium řazení lze seřadit elementů v rámci jednotlivých skupin primární řazení.</span><span class="sxs-lookup"><span data-stu-id="55589-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="55589-106">Následující obrázek znázorňuje výsledky operace abecedním řazení na posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="55589-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="55589-107">![LINQ řazení operaci](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="55589-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="55589-108">Operátor metody standardní dotazů, které řazení dat jsou uvedené v následující části.</span><span class="sxs-lookup"><span data-stu-id="55589-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55589-109">Metody</span><span class="sxs-lookup"><span data-stu-id="55589-109">Methods</span></span>  
  
|<span data-ttu-id="55589-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="55589-110">Method Name</span></span>|<span data-ttu-id="55589-111">Popis</span><span class="sxs-lookup"><span data-stu-id="55589-111">Description</span></span>|<span data-ttu-id="55589-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55589-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="55589-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="55589-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="55589-114">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="55589-114">OrderBy</span></span>|<span data-ttu-id="55589-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="55589-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="55589-116">OrderByDescending</span></span>|<span data-ttu-id="55589-117">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="55589-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="55589-118">ThenBy</span></span>|<span data-ttu-id="55589-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="55589-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="55589-120">ThenByDescending</span></span>|<span data-ttu-id="55589-121">Provede sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="55589-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="55589-122">Reverse</span></span>|<span data-ttu-id="55589-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="55589-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="55589-124">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="55589-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="55589-125">Příklady syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="55589-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="55589-126">Příklady primární řazení</span><span class="sxs-lookup"><span data-stu-id="55589-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="55589-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="55589-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="55589-128">Následující příklad ukazuje, jak používat `orderby` klauzuli v dotazu LINQ pro řazení řetězců v pole podle délka řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="55589-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="55589-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="55589-130">Další příklad ukazuje, jak používat `orderby``descending` klauzuli v dotazu LINQ řetězce seřadit podle jejich první písmeno v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-130">The next example demonstrates how to use the `orderby``descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="55589-131">Příklady sekundární řazení</span><span class="sxs-lookup"><span data-stu-id="55589-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="55589-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="55589-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="55589-133">Následující příklad ukazuje, jak používat `orderby` klauzuli v dotazu LINQ provádět primární a sekundární řazení řetězců v pole.</span><span class="sxs-lookup"><span data-stu-id="55589-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="55589-134">Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce, oba ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="55589-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="55589-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="55589-136">Další příklad ukazuje, jak používat `orderby``descending` klauzuli v dotazu LINQ provést primární řazení ve vzestupném pořadí a sekundární řazení, v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55589-136">The next example demonstrates how to use the `orderby``descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="55589-137">Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce.</span><span class="sxs-lookup"><span data-stu-id="55589-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55589-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="55589-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="55589-139">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="55589-139">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="55589-140">OrderBy – klauzule</span><span class="sxs-lookup"><span data-stu-id="55589-140">orderby clause</span></span>](../../../../csharp/language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="55589-141">Postupy: řazení výsledků Klauzule Join</span><span class="sxs-lookup"><span data-stu-id="55589-141">How to: Order the Results of a Join Clause</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [<span data-ttu-id="55589-142">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="55589-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
