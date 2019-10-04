---
title: Převádění datových typů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 4d0658983b5873c635d1926444293b0ddf5b0a87
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835176"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="008a5-102">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="008a5-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="008a5-103">Metody převodu mění typ vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="008a5-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="008a5-104">Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích.</span><span class="sxs-lookup"><span data-stu-id="008a5-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="008a5-105">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="008a5-105">The following are some examples:</span></span>
  
- <span data-ttu-id="008a5-106">Metodu <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> lze použít ke skrytí vlastní implementace typu standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="008a5-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="008a5-107">Metodu <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.</span><span class="sxs-lookup"><span data-stu-id="008a5-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="008a5-108">Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení, dokud se dotaz nevytvoří.</span><span class="sxs-lookup"><span data-stu-id="008a5-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="008a5-109">Metody</span><span class="sxs-lookup"><span data-stu-id="008a5-109">Methods</span></span>  
 <span data-ttu-id="008a5-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="008a5-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="008a5-111">Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet.</span><span class="sxs-lookup"><span data-stu-id="008a5-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="008a5-112">Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="008a5-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="008a5-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="008a5-113">Method Name</span></span>|<span data-ttu-id="008a5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="008a5-114">Description</span></span>|<span data-ttu-id="008a5-115">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="008a5-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="008a5-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="008a5-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="008a5-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="008a5-117">AsEnumerable</span></span>|<span data-ttu-id="008a5-118">Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="008a5-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="008a5-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="008a5-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="008a5-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="008a5-120">AsQueryable</span></span>|<span data-ttu-id="008a5-121">Převede (Generic) <xref:System.Collections.IEnumerable> na (Generic) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="008a5-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="008a5-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="008a5-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="008a5-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="008a5-123">Cast</span></span>|<span data-ttu-id="008a5-124">Přetypování prvky kolekce na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="008a5-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="008a5-125">Only</span><span class="sxs-lookup"><span data-stu-id="008a5-125">OfType</span></span>|<span data-ttu-id="008a5-126">Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="008a5-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="008a5-127">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="008a5-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="008a5-128">ToArray –</span><span class="sxs-lookup"><span data-stu-id="008a5-128">ToArray</span></span>|<span data-ttu-id="008a5-129">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="008a5-129">Converts a collection to an array.</span></span> <span data-ttu-id="008a5-130">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="008a5-130">This method forces query execution.</span></span>|<span data-ttu-id="008a5-131">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="008a5-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="008a5-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="008a5-132">ToDictionary</span></span>|<span data-ttu-id="008a5-133">Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="008a5-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="008a5-134">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="008a5-134">This method forces query execution.</span></span>|<span data-ttu-id="008a5-135">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="008a5-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="008a5-136">ToList –</span><span class="sxs-lookup"><span data-stu-id="008a5-136">ToList</span></span>|<span data-ttu-id="008a5-137">Převede kolekci na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="008a5-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="008a5-138">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="008a5-138">This method forces query execution.</span></span>|<span data-ttu-id="008a5-139">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="008a5-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="008a5-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="008a5-140">ToLookup</span></span>|<span data-ttu-id="008a5-141">Vloží prvky do <xref:System.Linq.Lookup%602> (slovník 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="008a5-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="008a5-142">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="008a5-142">This method forces query execution.</span></span>|<span data-ttu-id="008a5-143">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="008a5-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="008a5-144">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="008a5-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="008a5-145">Následující příklad kódu používá klauzuli `From As` pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.</span><span class="sxs-lookup"><span data-stu-id="008a5-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="008a5-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="008a5-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="008a5-147">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="008a5-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="008a5-148">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="008a5-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="008a5-149">Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="008a5-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
