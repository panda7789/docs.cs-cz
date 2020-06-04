---
title: Převádění datových typů
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 1394f53923ba850ae11fbc326a25c279589c3be1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410848"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="2f061-102">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f061-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="2f061-103">Metody převodu mění typ vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="2f061-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="2f061-104">Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích.</span><span class="sxs-lookup"><span data-stu-id="2f061-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="2f061-105">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="2f061-105">The following are some examples:</span></span>

- <span data-ttu-id="2f061-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>Metoda může být použita ke skrytí vlastní implementace typu standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="2f061-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="2f061-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Metodu lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.</span><span class="sxs-lookup"><span data-stu-id="2f061-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="2f061-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>Metody, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> , <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení až do vypsání dotazu.</span><span class="sxs-lookup"><span data-stu-id="2f061-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="2f061-109">Metody</span><span class="sxs-lookup"><span data-stu-id="2f061-109">Methods</span></span>

<span data-ttu-id="2f061-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="2f061-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="2f061-111">Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet.</span><span class="sxs-lookup"><span data-stu-id="2f061-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="2f061-112">Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="2f061-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="2f061-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="2f061-113">Method Name</span></span>|<span data-ttu-id="2f061-114">Description</span><span class="sxs-lookup"><span data-stu-id="2f061-114">Description</span></span>|<span data-ttu-id="2f061-115">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="2f061-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="2f061-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="2f061-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="2f061-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="2f061-117">AsEnumerable</span></span>|<span data-ttu-id="2f061-118">Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="2f061-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="2f061-119">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="2f061-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2f061-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="2f061-120">AsQueryable</span></span>|<span data-ttu-id="2f061-121">Převede (Obecné) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="2f061-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="2f061-122">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="2f061-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2f061-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="2f061-123">Cast</span></span>|<span data-ttu-id="2f061-124">Přetypování prvky kolekce na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="2f061-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2f061-125">Only</span><span class="sxs-lookup"><span data-stu-id="2f061-125">OfType</span></span>|<span data-ttu-id="2f061-126">Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="2f061-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="2f061-127">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="2f061-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2f061-128">ToArray –</span><span class="sxs-lookup"><span data-stu-id="2f061-128">ToArray</span></span>|<span data-ttu-id="2f061-129">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="2f061-129">Converts a collection to an array.</span></span> <span data-ttu-id="2f061-130">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="2f061-130">This method forces query execution.</span></span>|<span data-ttu-id="2f061-131">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="2f061-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2f061-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="2f061-132">ToDictionary</span></span>|<span data-ttu-id="2f061-133">Vloží prvky do prvku na <xref:System.Collections.Generic.Dictionary%602> základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="2f061-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="2f061-134">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="2f061-134">This method forces query execution.</span></span>|<span data-ttu-id="2f061-135">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="2f061-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2f061-136">ToList –</span><span class="sxs-lookup"><span data-stu-id="2f061-136">ToList</span></span>|<span data-ttu-id="2f061-137">Převede kolekci na <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="2f061-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="2f061-138">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="2f061-138">This method forces query execution.</span></span>|<span data-ttu-id="2f061-139">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="2f061-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="2f061-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="2f061-140">ToLookup</span></span>|<span data-ttu-id="2f061-141">Vloží prvky do <xref:System.Linq.Lookup%602> slovníku (do slovníku 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="2f061-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="2f061-142">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="2f061-142">This method forces query execution.</span></span>|<span data-ttu-id="2f061-143">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="2f061-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="2f061-144">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="2f061-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="2f061-145">Následující příklad kódu používá `From As` klauzuli pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.</span><span class="sxs-lookup"><span data-stu-id="2f061-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f061-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f061-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="2f061-147">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f061-147">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="2f061-148">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="2f061-148">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="2f061-149">Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f061-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)
