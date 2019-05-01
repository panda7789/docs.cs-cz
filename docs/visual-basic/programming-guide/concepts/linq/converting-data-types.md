---
title: Převádění datových typů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: ad9594cabe0e2382ae4e19f2541eec4aa74ccd75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968854"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="ae18f-102">Převádění datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae18f-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="ae18f-103">Převod metody změnit typ objektu, vstupu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="ae18f-104">Převod operace v dotazech LINQ jsou užitečné pro různé aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae18f-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="ae18f-105">Toto jsou některé příklady:</span><span class="sxs-lookup"><span data-stu-id="ae18f-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="ae18f-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metodu je možné skrýt vlastní implementaci typu operátoru standardního dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="ae18f-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metody slouží k povolení neparametrizované kolekce pro dotazování na LINQ.</span><span class="sxs-lookup"><span data-stu-id="ae18f-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="ae18f-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody je možné vynutit spuštění dotazu okamžité místo jeho odložit, dokud je vypočten dotaz.</span><span class="sxs-lookup"><span data-stu-id="ae18f-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae18f-109">Metody</span><span class="sxs-lookup"><span data-stu-id="ae18f-109">Methods</span></span>  
 <span data-ttu-id="ae18f-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="ae18f-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="ae18f-111">Převod metody v této tabulce, jejichž názvy začínají písmenem "Jako" Změna statického typu zdrojové kolekce, ale není výčet.</span><span class="sxs-lookup"><span data-stu-id="ae18f-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="ae18f-112">Metody, jejichž názvy začínají písmenem "Do výčet zdrojové kolekce a položky do příslušné kolekce" typu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="ae18f-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="ae18f-113">Method Name</span></span>|<span data-ttu-id="ae18f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ae18f-114">Description</span></span>|<span data-ttu-id="ae18f-115">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae18f-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ae18f-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="ae18f-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ae18f-117">Jako výčet</span><span class="sxs-lookup"><span data-stu-id="ae18f-117">AsEnumerable</span></span>|<span data-ttu-id="ae18f-118">Vrátí zadaný jako vstup <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ae18f-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="ae18f-119">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ae18f-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ae18f-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="ae18f-120">AsQueryable</span></span>|<span data-ttu-id="ae18f-121">Převede (Obecné) <xref:System.Collections.IEnumerable> pro (obecný) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="ae18f-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="ae18f-122">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ae18f-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ae18f-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="ae18f-123">Cast</span></span>|<span data-ttu-id="ae18f-124">Elementy kolekce do zadaného typu přetypování.</span><span class="sxs-lookup"><span data-stu-id="ae18f-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ae18f-125">OfType</span><span class="sxs-lookup"><span data-stu-id="ae18f-125">OfType</span></span>|<span data-ttu-id="ae18f-126">Hodnoty v závislosti na jejich schopnost převést na zadaný typ filtrů.</span><span class="sxs-lookup"><span data-stu-id="ae18f-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="ae18f-127">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ae18f-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ae18f-128">ToArray –</span><span class="sxs-lookup"><span data-stu-id="ae18f-128">ToArray</span></span>|<span data-ttu-id="ae18f-129">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="ae18f-129">Converts a collection to an array.</span></span> <span data-ttu-id="ae18f-130">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-130">This method forces query execution.</span></span>|<span data-ttu-id="ae18f-131">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ae18f-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ae18f-132">Metody ToDictionary</span><span class="sxs-lookup"><span data-stu-id="ae18f-132">ToDictionary</span></span>|<span data-ttu-id="ae18f-133">Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="ae18f-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="ae18f-134">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-134">This method forces query execution.</span></span>|<span data-ttu-id="ae18f-135">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ae18f-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ae18f-136">ToList –</span><span class="sxs-lookup"><span data-stu-id="ae18f-136">ToList</span></span>|<span data-ttu-id="ae18f-137">Převede kolekci <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="ae18f-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ae18f-138">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-138">This method forces query execution.</span></span>|<span data-ttu-id="ae18f-139">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ae18f-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ae18f-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="ae18f-140">ToLookup</span></span>|<span data-ttu-id="ae18f-141">Vloží prvky do <xref:System.Linq.Lookup%602> (jeden na mnoho slovník) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="ae18f-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="ae18f-142">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-142">This method forces query execution.</span></span>|<span data-ttu-id="ae18f-143">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ae18f-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="ae18f-144">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="ae18f-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="ae18f-145">Následující příklad kódu používá `From As` klauzule přetypovat na typ podtyp před přístupem k členu, který je k dispozici pouze na podtyp.</span><span class="sxs-lookup"><span data-stu-id="ae18f-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae18f-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae18f-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ae18f-147">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae18f-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ae18f-148">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="ae18f-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ae18f-149">Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae18f-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
