---
title: Řazení dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f8b1734597efa3134c95c9764bad7f79fd3cf1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524079"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="ada66-102">Řazení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ada66-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="ada66-103">Operace řazení řadí prvky sekvence na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="ada66-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="ada66-104">První kritérium řazení provede primární řazení pro prvky.</span><span class="sxs-lookup"><span data-stu-id="ada66-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="ada66-105">Zadáním druhého kritéria řazení můžete prvky seřadit v rámci každé primární skupiny řazení.</span><span class="sxs-lookup"><span data-stu-id="ada66-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="ada66-106">Následující ilustrace znázorňuje výsledky abecední operace řazení na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="ada66-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Obrázek, který zobrazuje abecední operaci řazení.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="ada66-108">Standardní metody operátoru dotazu, které řadí data, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="ada66-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="ada66-109">Metody</span><span class="sxs-lookup"><span data-stu-id="ada66-109">Methods</span></span>

|<span data-ttu-id="ada66-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="ada66-110">Method Name</span></span>|<span data-ttu-id="ada66-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ada66-111">Description</span></span>|<span data-ttu-id="ada66-112">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="ada66-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ada66-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="ada66-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="ada66-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="ada66-114">OrderBy</span></span>|<span data-ttu-id="ada66-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ada66-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="ada66-116">OrderByDescending</span></span>|<span data-ttu-id="ada66-117">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ada66-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="ada66-118">ThenBy</span></span>|<span data-ttu-id="ada66-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ada66-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="ada66-120">ThenByDescending</span></span>|<span data-ttu-id="ada66-121">Provede sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ada66-122">Zpět</span><span class="sxs-lookup"><span data-stu-id="ada66-122">Reverse</span></span>|<span data-ttu-id="ada66-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ada66-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="ada66-124">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="ada66-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ada66-125">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="ada66-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="ada66-126">Primární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="ada66-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="ada66-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ada66-127">Primary Ascending Sort</span></span>

<span data-ttu-id="ada66-128">Následující příklad ukazuje, jak použít klauzuli `Order By` v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

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

#### <a name="primary-descending-sort"></a><span data-ttu-id="ada66-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ada66-129">Primary Descending Sort</span></span>

<span data-ttu-id="ada66-130">Další příklad ukazuje, jak použít klauzuli `Order By Descending` v dotazu LINQ k řazení řetězců podle jejich prvního písmena v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

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

### <a name="secondary-sort-examples"></a><span data-ttu-id="ada66-131">Sekundární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="ada66-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="ada66-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ada66-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="ada66-133">Následující příklad ukazuje, jak použít klauzuli `Order By` v dotazu LINQ k provedení primárního a sekundárního řazení řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="ada66-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="ada66-134">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce, ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

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

#### <a name="secondary-descending-sort"></a><span data-ttu-id="ada66-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="ada66-135">Secondary Descending Sort</span></span>

<span data-ttu-id="ada66-136">Další příklad ukazuje, jak použít klauzuli `Order By Descending` v dotazu LINQ k provedení primárního řazení ve vzestupném pořadí a sekundárního řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ada66-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="ada66-137">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce.</span><span class="sxs-lookup"><span data-stu-id="ada66-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ada66-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ada66-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ada66-139">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ada66-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ada66-140">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="ada66-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="ada66-141">Postupy: řazení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="ada66-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="ada66-142">Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ada66-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
