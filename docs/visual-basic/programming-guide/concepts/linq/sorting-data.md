---
title: Řazení dat
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f1d4d8afb9b6e176a7ac048ba3270ecafdce24c9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350590"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="faaff-102">Řazení dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faaff-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="faaff-103">Operace řazení řadí prvky sekvence na základě jednoho nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="faaff-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="faaff-104">První kritérium řazení provede primární řazení pro prvky.</span><span class="sxs-lookup"><span data-stu-id="faaff-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="faaff-105">Zadáním druhého kritéria řazení můžete prvky seřadit v rámci každé primární skupiny řazení.</span><span class="sxs-lookup"><span data-stu-id="faaff-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="faaff-106">Následující ilustrace znázorňuje výsledky abecední operace řazení na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="faaff-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Obrázek, který zobrazuje abecední operaci řazení.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="faaff-108">Standardní metody operátoru dotazu, které řadí data, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="faaff-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="faaff-109">Metody</span><span class="sxs-lookup"><span data-stu-id="faaff-109">Methods</span></span>

|<span data-ttu-id="faaff-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="faaff-110">Method Name</span></span>|<span data-ttu-id="faaff-111">Popis</span><span class="sxs-lookup"><span data-stu-id="faaff-111">Description</span></span>|<span data-ttu-id="faaff-112">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="faaff-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="faaff-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="faaff-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="faaff-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="faaff-114">OrderBy</span></span>|<span data-ttu-id="faaff-115">Seřadí hodnoty ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="faaff-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="faaff-116">OrderByDescending</span></span>|<span data-ttu-id="faaff-117">Seřadí hodnoty v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="faaff-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="faaff-118">ThenBy</span></span>|<span data-ttu-id="faaff-119">Provede sekundární řazení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="faaff-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="faaff-120">ThenByDescending</span></span>|<span data-ttu-id="faaff-121">Provede sekundární řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="faaff-122">Zpět</span><span class="sxs-lookup"><span data-stu-id="faaff-122">Reverse</span></span>|<span data-ttu-id="faaff-123">Obrátí pořadí prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="faaff-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="faaff-124">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="faaff-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="faaff-125">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="faaff-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="faaff-126">Primární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="faaff-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="faaff-127">Primární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="faaff-127">Primary Ascending Sort</span></span>

<span data-ttu-id="faaff-128">Následující příklad ukazuje, jak použít klauzuli `Order By` v dotazu LINQ k řazení řetězců v poli podle délky řetězce ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

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

#### <a name="primary-descending-sort"></a><span data-ttu-id="faaff-129">Primární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="faaff-129">Primary Descending Sort</span></span>

<span data-ttu-id="faaff-130">Další příklad ukazuje, jak použít klauzuli `Order By Descending` v dotazu LINQ k řazení řetězců podle jejich prvního písmena v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

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

### <a name="secondary-sort-examples"></a><span data-ttu-id="faaff-131">Sekundární příklady řazení</span><span class="sxs-lookup"><span data-stu-id="faaff-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="faaff-132">Sekundární vzestupné řazení</span><span class="sxs-lookup"><span data-stu-id="faaff-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="faaff-133">Následující příklad ukazuje, jak použít klauzuli `Order By` v dotazu LINQ k provedení primárního a sekundárního řazení řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="faaff-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="faaff-134">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce, ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

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

#### <a name="secondary-descending-sort"></a><span data-ttu-id="faaff-135">Sekundární sestupné řazení</span><span class="sxs-lookup"><span data-stu-id="faaff-135">Secondary Descending Sort</span></span>

<span data-ttu-id="faaff-136">Další příklad ukazuje, jak použít klauzuli `Order By Descending` v dotazu LINQ k provedení primárního řazení ve vzestupném pořadí a sekundárního řazení v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="faaff-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="faaff-137">Řetězce jsou seřazeny hlavně podle délky a secondarily podle prvního písmene řetězce.</span><span class="sxs-lookup"><span data-stu-id="faaff-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="faaff-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faaff-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="faaff-139">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faaff-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="faaff-140">Klauzule Order By</span><span class="sxs-lookup"><span data-stu-id="faaff-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="faaff-141">Postupy: řazení výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="faaff-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="faaff-142">Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faaff-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
