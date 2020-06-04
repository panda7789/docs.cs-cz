---
title: Řazení dat
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: a5ccff745995ed7f41731cf98fb7c49d3247d994
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406791"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="40ea8-102">Řazení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40ea8-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="40ea8-103">Operace řazení řadí prvky sekvence na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="40ea8-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="40ea8-104">První kritérium řazení provede primární řazení pro prvky.</span><span class="sxs-lookup"><span data-stu-id="40ea8-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="40ea8-105">Zadáním druhého kritéria řazení můžete prvky seřadit v rámci každé primární skupiny řazení.</span><span class="sxs-lookup"><span data-stu-id="40ea8-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="40ea8-106">Následující ilustrace znázorňuje výsledky abecední operace řazení na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="40ea8-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Obrázek, který zobrazuje abecední operaci řazení.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="40ea8-108">Standardní metody operátoru dotazu, které řadí data, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="40ea8-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="40ea8-109">Metody</span><span class="sxs-lookup"><span data-stu-id="40ea8-109">Methods</span></span>

|<span data-ttu-id="40ea8-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="40ea8-110">Method Name</span></span>|<span data-ttu-id="40ea8-111">Description</span><span class="sxs-lookup"><span data-stu-id="40ea8-111">Description</span></span>|<span data-ttu-id="40ea8-112">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="40ea8-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="40ea8-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="40ea8-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="40ea8-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="40ea8-114">OrderBy</span></span>|<span data-ttu-id="40ea8-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="40ea8-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="40ea8-116">OrderByDescending</span></span>|<span data-ttu-id="40ea8-117">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="40ea8-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="40ea8-118">ThenBy</span></span>|<span data-ttu-id="40ea8-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="40ea8-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="40ea8-120">ThenByDescending</span></span>|<span data-ttu-id="40ea8-121">Provede sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="40ea8-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="40ea8-122">Reverse</span></span>|<span data-ttu-id="40ea8-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="40ea8-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="40ea8-124">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="40ea8-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="40ea8-125">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="40ea8-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="40ea8-126">Primární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="40ea8-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="40ea8-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="40ea8-127">Primary Ascending Sort</span></span>

<span data-ttu-id="40ea8-128">Následující příklad ukazuje, jak použít `Order By` klauzuli v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

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

#### <a name="primary-descending-sort"></a><span data-ttu-id="40ea8-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="40ea8-129">Primary Descending Sort</span></span>

<span data-ttu-id="40ea8-130">Další příklad ukazuje, jak použít `Order By Descending` klauzuli v dotazu LINQ k řazení řetězců podle jejich prvního písmena v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

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

### <a name="secondary-sort-examples"></a><span data-ttu-id="40ea8-131">Sekundární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="40ea8-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="40ea8-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="40ea8-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="40ea8-133">Následující příklad ukazuje, jak použít `Order By` klauzuli v dotazu LINQ k provedení primárního a sekundárního řazení řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="40ea8-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="40ea8-134">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce, ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

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

#### <a name="secondary-descending-sort"></a><span data-ttu-id="40ea8-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="40ea8-135">Secondary Descending Sort</span></span>

<span data-ttu-id="40ea8-136">Další příklad ukazuje, jak použít `Order By Descending` klauzuli v dotazu LINQ k provedení primárního řazení ve vzestupném pořadí a sekundárního řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="40ea8-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="40ea8-137">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce.</span><span class="sxs-lookup"><span data-stu-id="40ea8-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="40ea8-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="40ea8-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="40ea8-139">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40ea8-139">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="40ea8-140">Order By – klauzule</span><span class="sxs-lookup"><span data-stu-id="40ea8-140">Order By Clause</span></span>](../../../language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="40ea8-141">Postupy: řazení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="40ea8-141">How to: Sort Query Results</span></span>](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="40ea8-142">Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40ea8-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
