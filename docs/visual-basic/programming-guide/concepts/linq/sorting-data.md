---
title: Řazení dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: ad39aca6a53221f077a6b8313262d508744ff5ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908103"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="982ee-102">Řazení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ee-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="982ee-103">Operace řazení Seřadí prvky pořadí na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="982ee-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="982ee-104">První kritérium řazení provede primární řazení elementů.</span><span class="sxs-lookup"><span data-stu-id="982ee-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="982ee-105">Zadáním druhý kritérium řazení, lze řazení elementů v rámci jednotlivých skupin primární řazení.</span><span class="sxs-lookup"><span data-stu-id="982ee-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="982ee-106">Následující obrázek znázorňuje výsledky operace abecední řazení na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="982ee-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 ![Obrázek znázorňující, operace abecední řazení.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="982ee-108">Standardní metody operátoru dotazu, které řazení dat jsou uvedené v následující části.</span><span class="sxs-lookup"><span data-stu-id="982ee-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="982ee-109">Metody</span><span class="sxs-lookup"><span data-stu-id="982ee-109">Methods</span></span>  
  
|<span data-ttu-id="982ee-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="982ee-110">Method Name</span></span>|<span data-ttu-id="982ee-111">Popis</span><span class="sxs-lookup"><span data-stu-id="982ee-111">Description</span></span>|<span data-ttu-id="982ee-112">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="982ee-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="982ee-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="982ee-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="982ee-114">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="982ee-114">OrderBy</span></span>|<span data-ttu-id="982ee-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="982ee-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="982ee-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="982ee-116">OrderByDescending</span></span>|<span data-ttu-id="982ee-117">Seřadí v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="982ee-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="982ee-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="982ee-118">ThenBy</span></span>|<span data-ttu-id="982ee-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="982ee-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="982ee-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="982ee-120">ThenByDescending</span></span>|<span data-ttu-id="982ee-121">Provádí sekundární seřadit v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="982ee-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="982ee-122">reverzní</span><span class="sxs-lookup"><span data-stu-id="982ee-122">Reverse</span></span>|<span data-ttu-id="982ee-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="982ee-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="982ee-124">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="982ee-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="982ee-125">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="982ee-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="982ee-126">Příklady primárních řazení</span><span class="sxs-lookup"><span data-stu-id="982ee-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="982ee-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="982ee-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="982ee-128">Následující příklad ukazuje způsob použití `Order By` klauzule v dotazu LINQ a řetězce v poli řadit délka řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="982ee-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="982ee-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="982ee-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="982ee-130">Následující příklad ukazuje, jak používat `Order By Descending` klauzule v dotazu LINQ a řetězce řadit v sestupném pořadí podle jejich první písmeno.</span><span class="sxs-lookup"><span data-stu-id="982ee-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="982ee-131">Příklady sekundární řazení</span><span class="sxs-lookup"><span data-stu-id="982ee-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="982ee-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="982ee-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="982ee-133">Následující příklad ukazuje způsob použití `Order By` klauzule v dotazu LINQ provádět primární a sekundární řazení řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="982ee-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="982ee-134">Řetězce jsou seřazeny podle délky primárně a sekundárně první písmeno řetězce, oba ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="982ee-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="982ee-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="982ee-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="982ee-136">Následující příklad ukazuje, jak používat `Order By Descending` klauzule v dotazu LINQ provádět primární řazení ve vzestupném pořadí a sekundární řazení, v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="982ee-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="982ee-137">Řetězce jsou seřazeny především podle délky a sekundárně první písmeno řetězce.</span><span class="sxs-lookup"><span data-stu-id="982ee-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="982ee-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="982ee-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="982ee-139">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ee-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="982ee-140">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="982ee-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="982ee-141">Postupy: Řazení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="982ee-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="982ee-142">Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ee-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
