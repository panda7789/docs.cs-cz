---
title: "Řazení dat (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f17c6ecad721dd3a48a01c09693b0a1cf723a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="87235-102">Řazení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87235-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="87235-103">Operace řazení řadí elementy pořadí na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="87235-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="87235-104">První kritérium řazení provede primární řazení elementů.</span><span class="sxs-lookup"><span data-stu-id="87235-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="87235-105">Zadáním druhý kritérium řazení lze seřadit elementů v rámci jednotlivých skupin primární řazení.</span><span class="sxs-lookup"><span data-stu-id="87235-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="87235-106">Následující obrázek znázorňuje výsledky operace abecedním řazení na posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="87235-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="87235-107">![LINQ řazení operaci](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="87235-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="87235-108">Operátor metody standardní dotazů, které řazení dat jsou uvedené v následující části.</span><span class="sxs-lookup"><span data-stu-id="87235-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87235-109">Metody</span><span class="sxs-lookup"><span data-stu-id="87235-109">Methods</span></span>  
  
|<span data-ttu-id="87235-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="87235-110">Method Name</span></span>|<span data-ttu-id="87235-111">Popis</span><span class="sxs-lookup"><span data-stu-id="87235-111">Description</span></span>|<span data-ttu-id="87235-112">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87235-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="87235-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="87235-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="87235-114">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="87235-114">OrderBy</span></span>|<span data-ttu-id="87235-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="87235-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="87235-116">OrderByDescending</span></span>|<span data-ttu-id="87235-117">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="87235-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="87235-118">ThenBy</span></span>|<span data-ttu-id="87235-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="87235-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="87235-120">ThenByDescending</span></span>|<span data-ttu-id="87235-121">Provede sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="87235-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="87235-122">Reverse</span></span>|<span data-ttu-id="87235-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="87235-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="87235-124">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="87235-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="87235-125">Příklady syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="87235-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="87235-126">Příklady primární řazení</span><span class="sxs-lookup"><span data-stu-id="87235-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="87235-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="87235-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="87235-128">Následující příklad ukazuje, jak používat `Order By` klauzuli v dotazu LINQ pro řazení řetězců v pole podle délka řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="87235-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="87235-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="87235-130">Další příklad ukazuje, jak používat `Order By Descending` klauzuli v dotazu LINQ řetězce seřadit podle jejich první písmeno v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="87235-131">Příklady sekundární řazení</span><span class="sxs-lookup"><span data-stu-id="87235-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="87235-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="87235-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="87235-133">Následující příklad ukazuje, jak používat `Order By` klauzuli v dotazu LINQ provádět primární a sekundární řazení řetězců v pole.</span><span class="sxs-lookup"><span data-stu-id="87235-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="87235-134">Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce, oba ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="87235-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="87235-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="87235-136">Další příklad ukazuje, jak používat `Order By Descending` klauzuli v dotazu LINQ provést primární řazení ve vzestupném pořadí a sekundární řazení, v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87235-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="87235-137">Řetězce jsou seřazeny primárně podle délky a sekundárně první písmeno řetězce.</span><span class="sxs-lookup"><span data-stu-id="87235-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a><span data-ttu-id="87235-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="87235-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="87235-139">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87235-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="87235-140">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="87235-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="87235-141">Postupy: řazení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="87235-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [<span data-ttu-id="87235-142">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87235-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
