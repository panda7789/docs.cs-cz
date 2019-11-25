---
title: Převádění datových typů
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 25d21954f0bb7555f1f5666f83fb37f4f73e2a60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354260"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="2e838-102">Converting Data Types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e838-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="2e838-103">Conversion methods change the type of input objects.</span><span class="sxs-lookup"><span data-stu-id="2e838-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="2e838-104">Conversion operations in LINQ queries are useful in a variety of applications.</span><span class="sxs-lookup"><span data-stu-id="2e838-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="2e838-105">The following are some examples:</span><span class="sxs-lookup"><span data-stu-id="2e838-105">The following are some examples:</span></span>

- <span data-ttu-id="2e838-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span><span class="sxs-lookup"><span data-stu-id="2e838-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="2e838-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span><span class="sxs-lookup"><span data-stu-id="2e838-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="2e838-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span><span class="sxs-lookup"><span data-stu-id="2e838-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="2e838-109">Metody</span><span class="sxs-lookup"><span data-stu-id="2e838-109">Methods</span></span>

<span data-ttu-id="2e838-110">The following table lists the standard query operator methods that perform data-type conversions.</span><span class="sxs-lookup"><span data-stu-id="2e838-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="2e838-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span><span class="sxs-lookup"><span data-stu-id="2e838-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="2e838-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span><span class="sxs-lookup"><span data-stu-id="2e838-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="2e838-113">Method Name</span><span class="sxs-lookup"><span data-stu-id="2e838-113">Method Name</span></span>|<span data-ttu-id="2e838-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2e838-114">Description</span></span>|<span data-ttu-id="2e838-115">Visual Basic Query Expression Syntax</span><span class="sxs-lookup"><span data-stu-id="2e838-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="2e838-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="2e838-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="2e838-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="2e838-117">AsEnumerable</span></span>|<span data-ttu-id="2e838-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="2e838-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="2e838-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="2e838-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2e838-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="2e838-120">AsQueryable</span></span>|<span data-ttu-id="2e838-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="2e838-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="2e838-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="2e838-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2e838-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="2e838-123">Cast</span></span>|<span data-ttu-id="2e838-124">Casts the elements of a collection to a specified type.</span><span class="sxs-lookup"><span data-stu-id="2e838-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2e838-125">OfType</span><span class="sxs-lookup"><span data-stu-id="2e838-125">OfType</span></span>|<span data-ttu-id="2e838-126">Filters values, depending on their ability to be cast to a specified type.</span><span class="sxs-lookup"><span data-stu-id="2e838-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="2e838-127">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="2e838-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2e838-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="2e838-128">ToArray</span></span>|<span data-ttu-id="2e838-129">Converts a collection to an array.</span><span class="sxs-lookup"><span data-stu-id="2e838-129">Converts a collection to an array.</span></span> <span data-ttu-id="2e838-130">This method forces query execution.</span><span class="sxs-lookup"><span data-stu-id="2e838-130">This method forces query execution.</span></span>|<span data-ttu-id="2e838-131">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="2e838-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2e838-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="2e838-132">ToDictionary</span></span>|<span data-ttu-id="2e838-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span><span class="sxs-lookup"><span data-stu-id="2e838-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="2e838-134">This method forces query execution.</span><span class="sxs-lookup"><span data-stu-id="2e838-134">This method forces query execution.</span></span>|<span data-ttu-id="2e838-135">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="2e838-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2e838-136">ToList</span><span class="sxs-lookup"><span data-stu-id="2e838-136">ToList</span></span>|<span data-ttu-id="2e838-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="2e838-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="2e838-138">This method forces query execution.</span><span class="sxs-lookup"><span data-stu-id="2e838-138">This method forces query execution.</span></span>|<span data-ttu-id="2e838-139">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="2e838-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2e838-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="2e838-140">ToLookup</span></span>|<span data-ttu-id="2e838-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span><span class="sxs-lookup"><span data-stu-id="2e838-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="2e838-142">This method forces query execution.</span><span class="sxs-lookup"><span data-stu-id="2e838-142">This method forces query execution.</span></span>|<span data-ttu-id="2e838-143">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="2e838-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="2e838-144">Query Expression Syntax Example</span><span class="sxs-lookup"><span data-stu-id="2e838-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="2e838-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span><span class="sxs-lookup"><span data-stu-id="2e838-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```vb
Class Plant
    Public Property Name As String
End Class

Class CarnivorousPlant
    Inherits Plant
    Public Property TrapType As String
End Class

Sub Cast()

    Dim plants() As Plant = {
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}

    Dim query = From plant As CarnivorousPlant In plants
                Where plant.TrapType = "Snap Trap"
                Select plant

    Dim sb As New System.Text.StringBuilder()
    For Each plant In query
        sb.AppendLine(plant.Name)
    Next

    ' Display the results.
    MsgBox(sb.ToString())

    ' This code produces the following output:

    ' Venus Fly Trap
    ' Waterwheel Plant

End Sub
```

## <a name="see-also"></a><span data-ttu-id="2e838-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e838-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="2e838-147">Standard Query Operators Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e838-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="2e838-148">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="2e838-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="2e838-149">How to: Query an ArrayList with LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e838-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
