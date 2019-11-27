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
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="8bf27-102">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf27-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="8bf27-103">Metody převodu mění typ vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="8bf27-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="8bf27-104">Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích.</span><span class="sxs-lookup"><span data-stu-id="8bf27-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="8bf27-105">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="8bf27-105">The following are some examples:</span></span>

- <span data-ttu-id="8bf27-106">Pomocí metody <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> lze skrýt vlastní implementaci standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="8bf27-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="8bf27-107">Metodu <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.</span><span class="sxs-lookup"><span data-stu-id="8bf27-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="8bf27-108">Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení, dokud se dotaz nevytvoří.</span><span class="sxs-lookup"><span data-stu-id="8bf27-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="8bf27-109">Metody</span><span class="sxs-lookup"><span data-stu-id="8bf27-109">Methods</span></span>

<span data-ttu-id="8bf27-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="8bf27-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="8bf27-111">Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet.</span><span class="sxs-lookup"><span data-stu-id="8bf27-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="8bf27-112">Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="8bf27-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="8bf27-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="8bf27-113">Method Name</span></span>|<span data-ttu-id="8bf27-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8bf27-114">Description</span></span>|<span data-ttu-id="8bf27-115">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="8bf27-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8bf27-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="8bf27-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="8bf27-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="8bf27-117">AsEnumerable</span></span>|<span data-ttu-id="8bf27-118">Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="8bf27-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="8bf27-119">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8bf27-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8bf27-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="8bf27-120">AsQueryable</span></span>|<span data-ttu-id="8bf27-121">Převede (Generic) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="8bf27-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="8bf27-122">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8bf27-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8bf27-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="8bf27-123">Cast</span></span>|<span data-ttu-id="8bf27-124">Přetypování prvky kolekce na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="8bf27-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8bf27-125">Only</span><span class="sxs-lookup"><span data-stu-id="8bf27-125">OfType</span></span>|<span data-ttu-id="8bf27-126">Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="8bf27-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="8bf27-127">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8bf27-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8bf27-128">ToArray –</span><span class="sxs-lookup"><span data-stu-id="8bf27-128">ToArray</span></span>|<span data-ttu-id="8bf27-129">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="8bf27-129">Converts a collection to an array.</span></span> <span data-ttu-id="8bf27-130">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="8bf27-130">This method forces query execution.</span></span>|<span data-ttu-id="8bf27-131">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8bf27-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8bf27-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="8bf27-132">ToDictionary</span></span>|<span data-ttu-id="8bf27-133">Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="8bf27-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="8bf27-134">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="8bf27-134">This method forces query execution.</span></span>|<span data-ttu-id="8bf27-135">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8bf27-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8bf27-136">ToList –</span><span class="sxs-lookup"><span data-stu-id="8bf27-136">ToList</span></span>|<span data-ttu-id="8bf27-137">Převede kolekci na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="8bf27-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="8bf27-138">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="8bf27-138">This method forces query execution.</span></span>|<span data-ttu-id="8bf27-139">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8bf27-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8bf27-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="8bf27-140">ToLookup</span></span>|<span data-ttu-id="8bf27-141">Vloží prvky do <xref:System.Linq.Lookup%602> (slovník 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="8bf27-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="8bf27-142">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="8bf27-142">This method forces query execution.</span></span>|<span data-ttu-id="8bf27-143">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8bf27-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="8bf27-144">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="8bf27-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="8bf27-145">Následující příklad kódu používá klauzuli `From As` pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.</span><span class="sxs-lookup"><span data-stu-id="8bf27-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8bf27-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bf27-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8bf27-147">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf27-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8bf27-148">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="8bf27-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="8bf27-149">Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf27-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
