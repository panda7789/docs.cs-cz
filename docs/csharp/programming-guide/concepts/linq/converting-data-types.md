---
title: "Převádění datových typů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4733694c2a9fd7c83520b0bf2edea6ebffb47041
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="converting-data-types-c"></a><span data-ttu-id="c6e89-102">Převádění datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="c6e89-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="c6e89-103">Převod metody změnit typ vstupní objektů.</span><span class="sxs-lookup"><span data-stu-id="c6e89-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="c6e89-104">Převod operace v dotazech LINQ jsou užitečné v různých aplikací.</span><span class="sxs-lookup"><span data-stu-id="c6e89-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="c6e89-105">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="c6e89-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="c6e89-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda slouží ke skrytí vlastní implementaci typ operátoru standardní dotaz.</span><span class="sxs-lookup"><span data-stu-id="c6e89-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="c6e89-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda slouží k povolení-parametry kolekce pro dotazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="c6e89-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="c6e89-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody slouží k vynucení spuštění okamžitou dotazu místo ho odložit, dokud není dotaz zpracován.</span><span class="sxs-lookup"><span data-stu-id="c6e89-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6e89-109">Metody</span><span class="sxs-lookup"><span data-stu-id="c6e89-109">Methods</span></span>  
 <span data-ttu-id="c6e89-110">Následující tabulka uvádí metody operátor standardní dotazů, které provádět převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="c6e89-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="c6e89-111">Převod metody v této tabulce, jejichž název začíná "Jako" změnit statický typ kolekce zdroj ale není výčet.</span><span class="sxs-lookup"><span data-stu-id="c6e89-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="c6e89-112">Typ metody, jejichž název začíná "Na výčet zdrojové kolekci a umístí do příslušné kolekce položek".</span><span class="sxs-lookup"><span data-stu-id="c6e89-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="c6e89-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="c6e89-113">Method Name</span></span>|<span data-ttu-id="c6e89-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c6e89-114">Description</span></span>|<span data-ttu-id="c6e89-115">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6e89-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="c6e89-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="c6e89-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="c6e89-117">Jako výčet</span><span class="sxs-lookup"><span data-stu-id="c6e89-117">AsEnumerable</span></span>|<span data-ttu-id="c6e89-118">Vrátí zadané jako vstup <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c6e89-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="c6e89-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e89-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6e89-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="c6e89-120">AsQueryable</span></span>|<span data-ttu-id="c6e89-121">Převede (Obecné) <xref:System.Collections.IEnumerable> k (Obecné) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="c6e89-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="c6e89-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e89-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6e89-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="c6e89-123">Cast</span></span>|<span data-ttu-id="c6e89-124">Vrhá prvky kolekce do zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="c6e89-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="c6e89-125">Pomocí proměnné explicitně typu rozsah.</span><span class="sxs-lookup"><span data-stu-id="c6e89-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="c6e89-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c6e89-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6e89-127">OfType</span><span class="sxs-lookup"><span data-stu-id="c6e89-127">OfType</span></span>|<span data-ttu-id="c6e89-128">Hodnoty, v závislosti na jejich schopnost převést na zadaný typ filtrování.</span><span class="sxs-lookup"><span data-stu-id="c6e89-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="c6e89-129">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e89-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6e89-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="c6e89-130">ToArray</span></span>|<span data-ttu-id="c6e89-131">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="c6e89-131">Converts a collection to an array.</span></span> <span data-ttu-id="c6e89-132">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="c6e89-132">This method forces query execution.</span></span>|<span data-ttu-id="c6e89-133">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e89-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6e89-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="c6e89-134">ToDictionary</span></span>|<span data-ttu-id="c6e89-135">Vloží elementy do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="c6e89-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="c6e89-136">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="c6e89-136">This method forces query execution.</span></span>|<span data-ttu-id="c6e89-137">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e89-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6e89-138">ToList</span><span class="sxs-lookup"><span data-stu-id="c6e89-138">ToList</span></span>|<span data-ttu-id="c6e89-139">Převede kolekci na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="c6e89-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="c6e89-140">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="c6e89-140">This method forces query execution.</span></span>|<span data-ttu-id="c6e89-141">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e89-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6e89-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="c6e89-142">ToLookup</span></span>|<span data-ttu-id="c6e89-143">Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="c6e89-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="c6e89-144">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="c6e89-144">This method forces query execution.</span></span>|<span data-ttu-id="c6e89-145">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c6e89-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="c6e89-146">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="c6e89-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="c6e89-147">Následující příklad kódu používá proměnnou rozsahu explicitně typované přetypovat typ k podtypem před přístupem k člena, který je k dispozici pouze na dílčí.</span><span class="sxs-lookup"><span data-stu-id="c6e89-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
```csharp  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6e89-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6e89-148">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="c6e89-149">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="c6e89-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="c6e89-150">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="c6e89-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="c6e89-151">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="c6e89-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="c6e89-152">Postupy: dotazu na ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="c6e89-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
