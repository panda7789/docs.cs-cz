---
title: Převádění datových typů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 9821b2d6caad8feeac856185b92518c25de88da3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643745"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="f26ca-102">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f26ca-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="f26ca-103">Převod metody změnit typ vstupní objektů.</span><span class="sxs-lookup"><span data-stu-id="f26ca-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="f26ca-104">Převod operace v dotazech LINQ jsou užitečné v různých aplikací.</span><span class="sxs-lookup"><span data-stu-id="f26ca-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="f26ca-105">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="f26ca-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="f26ca-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda slouží ke skrytí vlastní implementaci typ operátoru standardní dotaz.</span><span class="sxs-lookup"><span data-stu-id="f26ca-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="f26ca-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda slouží k povolení-parametry kolekce pro dotazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="f26ca-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="f26ca-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody slouží k vynucení spuštění okamžitou dotazu místo ho odložit, dokud není dotaz zpracován.</span><span class="sxs-lookup"><span data-stu-id="f26ca-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f26ca-109">Metody</span><span class="sxs-lookup"><span data-stu-id="f26ca-109">Methods</span></span>  
 <span data-ttu-id="f26ca-110">Následující tabulka uvádí metody operátor standardní dotazů, které provádět převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="f26ca-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="f26ca-111">Převod metody v této tabulce, jejichž název začíná "Jako" změnit statický typ kolekce zdroj ale není výčet.</span><span class="sxs-lookup"><span data-stu-id="f26ca-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="f26ca-112">Typ metody, jejichž název začíná "Na výčet zdrojové kolekci a umístí do příslušné kolekce položek".</span><span class="sxs-lookup"><span data-stu-id="f26ca-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="f26ca-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="f26ca-113">Method Name</span></span>|<span data-ttu-id="f26ca-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f26ca-114">Description</span></span>|<span data-ttu-id="f26ca-115">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f26ca-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f26ca-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="f26ca-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="f26ca-117">Jako výčet</span><span class="sxs-lookup"><span data-stu-id="f26ca-117">AsEnumerable</span></span>|<span data-ttu-id="f26ca-118">Vrátí zadané jako vstup <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f26ca-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="f26ca-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f26ca-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f26ca-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="f26ca-120">AsQueryable</span></span>|<span data-ttu-id="f26ca-121">Převede (Obecné) <xref:System.Collections.IEnumerable> k (Obecné) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="f26ca-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="f26ca-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f26ca-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f26ca-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="f26ca-123">Cast</span></span>|<span data-ttu-id="f26ca-124">Vrhá prvky kolekce do zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="f26ca-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f26ca-125">OfType</span><span class="sxs-lookup"><span data-stu-id="f26ca-125">OfType</span></span>|<span data-ttu-id="f26ca-126">Hodnoty, v závislosti na jejich schopnost převést na zadaný typ filtrování.</span><span class="sxs-lookup"><span data-stu-id="f26ca-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="f26ca-127">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f26ca-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f26ca-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="f26ca-128">ToArray</span></span>|<span data-ttu-id="f26ca-129">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="f26ca-129">Converts a collection to an array.</span></span> <span data-ttu-id="f26ca-130">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f26ca-130">This method forces query execution.</span></span>|<span data-ttu-id="f26ca-131">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f26ca-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f26ca-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="f26ca-132">ToDictionary</span></span>|<span data-ttu-id="f26ca-133">Vloží elementy do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="f26ca-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="f26ca-134">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f26ca-134">This method forces query execution.</span></span>|<span data-ttu-id="f26ca-135">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f26ca-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f26ca-136">ToList</span><span class="sxs-lookup"><span data-stu-id="f26ca-136">ToList</span></span>|<span data-ttu-id="f26ca-137">Převede kolekci na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f26ca-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f26ca-138">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f26ca-138">This method forces query execution.</span></span>|<span data-ttu-id="f26ca-139">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f26ca-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f26ca-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="f26ca-140">ToLookup</span></span>|<span data-ttu-id="f26ca-141">Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="f26ca-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="f26ca-142">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f26ca-142">This method forces query execution.</span></span>|<span data-ttu-id="f26ca-143">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f26ca-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="f26ca-144">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="f26ca-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="f26ca-145">Následující příklad kódu používá `From As` přetypovat typ k podtypem před přístupem k člena, který je dostupná jen pro dílčí klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f26ca-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f26ca-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="f26ca-146">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="f26ca-147">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f26ca-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="f26ca-148">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="f26ca-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="f26ca-149">Postupy: dotazu na ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f26ca-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
