---
title: Převádění datových typů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 866b30d3d65add8714f2088169b0769c340f264e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641971"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="cf44b-102">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf44b-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="cf44b-103">Převod metody změnit typ objektu, vstupu.</span><span class="sxs-lookup"><span data-stu-id="cf44b-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="cf44b-104">Převod operace v dotazech LINQ jsou užitečné pro různé aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf44b-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="cf44b-105">Toto jsou některé příklady:</span><span class="sxs-lookup"><span data-stu-id="cf44b-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="cf44b-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metodu je možné skrýt vlastní implementaci typu operátoru standardního dotazu.</span><span class="sxs-lookup"><span data-stu-id="cf44b-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="cf44b-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metody slouží k povolení neparametrizované kolekce pro dotazování na LINQ.</span><span class="sxs-lookup"><span data-stu-id="cf44b-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="cf44b-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody je možné vynutit spuštění dotazu okamžité místo jeho odložit, dokud je vypočten dotaz.</span><span class="sxs-lookup"><span data-stu-id="cf44b-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf44b-109">Metody</span><span class="sxs-lookup"><span data-stu-id="cf44b-109">Methods</span></span>  
 <span data-ttu-id="cf44b-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="cf44b-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="cf44b-111">Převod metody v této tabulce, jejichž názvy začínají písmenem "Jako" Změna statického typu zdrojové kolekce, ale není výčet.</span><span class="sxs-lookup"><span data-stu-id="cf44b-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="cf44b-112">Metody, jejichž názvy začínají písmenem "Do výčet zdrojové kolekce a položky do příslušné kolekce" typu.</span><span class="sxs-lookup"><span data-stu-id="cf44b-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="cf44b-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="cf44b-113">Method Name</span></span>|<span data-ttu-id="cf44b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cf44b-114">Description</span></span>|<span data-ttu-id="cf44b-115">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf44b-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="cf44b-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="cf44b-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="cf44b-117">Jako výčet</span><span class="sxs-lookup"><span data-stu-id="cf44b-117">AsEnumerable</span></span>|<span data-ttu-id="cf44b-118">Vrátí zadaný jako vstup <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="cf44b-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="cf44b-119">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf44b-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf44b-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="cf44b-120">AsQueryable</span></span>|<span data-ttu-id="cf44b-121">Převede (Obecné) <xref:System.Collections.IEnumerable> pro (obecný) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="cf44b-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="cf44b-122">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf44b-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf44b-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="cf44b-123">Cast</span></span>|<span data-ttu-id="cf44b-124">Elementy kolekce do zadaného typu přetypování.</span><span class="sxs-lookup"><span data-stu-id="cf44b-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf44b-125">OfType</span><span class="sxs-lookup"><span data-stu-id="cf44b-125">OfType</span></span>|<span data-ttu-id="cf44b-126">Hodnoty v závislosti na jejich schopnost převést na zadaný typ filtrů.</span><span class="sxs-lookup"><span data-stu-id="cf44b-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="cf44b-127">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf44b-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf44b-128">ToArray –</span><span class="sxs-lookup"><span data-stu-id="cf44b-128">ToArray</span></span>|<span data-ttu-id="cf44b-129">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="cf44b-129">Converts a collection to an array.</span></span> <span data-ttu-id="cf44b-130">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="cf44b-130">This method forces query execution.</span></span>|<span data-ttu-id="cf44b-131">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf44b-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf44b-132">Metody ToDictionary</span><span class="sxs-lookup"><span data-stu-id="cf44b-132">ToDictionary</span></span>|<span data-ttu-id="cf44b-133">Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="cf44b-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="cf44b-134">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="cf44b-134">This method forces query execution.</span></span>|<span data-ttu-id="cf44b-135">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf44b-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf44b-136">ToList –</span><span class="sxs-lookup"><span data-stu-id="cf44b-136">ToList</span></span>|<span data-ttu-id="cf44b-137">Převede kolekci <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="cf44b-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="cf44b-138">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="cf44b-138">This method forces query execution.</span></span>|<span data-ttu-id="cf44b-139">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf44b-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf44b-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="cf44b-140">ToLookup</span></span>|<span data-ttu-id="cf44b-141">Vloží prvky do <xref:System.Linq.Lookup%602> (jeden na mnoho slovník) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="cf44b-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="cf44b-142">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="cf44b-142">This method forces query execution.</span></span>|<span data-ttu-id="cf44b-143">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cf44b-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="cf44b-144">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="cf44b-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="cf44b-145">Následující příklad kódu používá `From As` klauzule přetypovat na typ podtyp před přístupem k členu, který je k dispozici pouze na podtyp.</span><span class="sxs-lookup"><span data-stu-id="cf44b-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf44b-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf44b-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="cf44b-147">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf44b-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="cf44b-148">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="cf44b-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="cf44b-149">Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf44b-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
