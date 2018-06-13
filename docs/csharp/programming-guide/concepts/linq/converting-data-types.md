---
title: Převádění datových typů (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 374ce15b8329c02c6b496a276a40fd9a60596e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335819"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="3e6f6-102">Převádění datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="3e6f6-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="3e6f6-103">Převod metody změnit typ vstupní objektů.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="3e6f6-104">Převod operace v dotazech LINQ jsou užitečné v různých aplikací.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="3e6f6-105">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="3e6f6-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="3e6f6-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda slouží ke skrytí vlastní implementaci typ operátoru standardní dotaz.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="3e6f6-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda slouží k povolení-parametry kolekce pro dotazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="3e6f6-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody slouží k vynucení spuštění okamžitou dotazu místo ho odložit, dokud není dotaz zpracován.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e6f6-109">Metody</span><span class="sxs-lookup"><span data-stu-id="3e6f6-109">Methods</span></span>  
 <span data-ttu-id="3e6f6-110">Následující tabulka uvádí metody operátor standardní dotazů, které provádět převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="3e6f6-111">Převod metody v této tabulce, jejichž název začíná "Jako" změnit statický typ kolekce zdroj ale není výčet.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="3e6f6-112">Typ metody, jejichž název začíná "Na výčet zdrojové kolekci a umístí do příslušné kolekce položek".</span><span class="sxs-lookup"><span data-stu-id="3e6f6-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="3e6f6-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="3e6f6-113">Method Name</span></span>|<span data-ttu-id="3e6f6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3e6f6-114">Description</span></span>|<span data-ttu-id="3e6f6-115">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e6f6-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="3e6f6-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="3e6f6-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="3e6f6-117">Jako výčet</span><span class="sxs-lookup"><span data-stu-id="3e6f6-117">AsEnumerable</span></span>|<span data-ttu-id="3e6f6-118">Vrátí zadané jako vstup <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="3e6f6-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e6f6-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="3e6f6-120">AsQueryable</span></span>|<span data-ttu-id="3e6f6-121">Převede (Obecné) <xref:System.Collections.IEnumerable> k (Obecné) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="3e6f6-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e6f6-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="3e6f6-123">Cast</span></span>|<span data-ttu-id="3e6f6-124">Vrhá prvky kolekce do zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="3e6f6-125">Pomocí proměnné explicitně typu rozsah.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="3e6f6-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3e6f6-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e6f6-127">OfType</span><span class="sxs-lookup"><span data-stu-id="3e6f6-127">OfType</span></span>|<span data-ttu-id="3e6f6-128">Hodnoty, v závislosti na jejich schopnost převést na zadaný typ filtrování.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="3e6f6-129">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e6f6-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="3e6f6-130">ToArray</span></span>|<span data-ttu-id="3e6f6-131">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-131">Converts a collection to an array.</span></span> <span data-ttu-id="3e6f6-132">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-132">This method forces query execution.</span></span>|<span data-ttu-id="3e6f6-133">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e6f6-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="3e6f6-134">ToDictionary</span></span>|<span data-ttu-id="3e6f6-135">Vloží elementy do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="3e6f6-136">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-136">This method forces query execution.</span></span>|<span data-ttu-id="3e6f6-137">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e6f6-138">ToList</span><span class="sxs-lookup"><span data-stu-id="3e6f6-138">ToList</span></span>|<span data-ttu-id="3e6f6-139">Převede kolekci na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="3e6f6-140">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-140">This method forces query execution.</span></span>|<span data-ttu-id="3e6f6-141">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e6f6-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="3e6f6-142">ToLookup</span></span>|<span data-ttu-id="3e6f6-143">Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="3e6f6-144">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-144">This method forces query execution.</span></span>|<span data-ttu-id="3e6f6-145">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="3e6f6-146">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="3e6f6-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="3e6f6-147">Následující příklad kódu používá proměnnou rozsahu explicitně typované přetypovat typ k podtypem před přístupem k člena, který je k dispozici pouze na dílčí.</span><span class="sxs-lookup"><span data-stu-id="3e6f6-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e6f6-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e6f6-148">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="3e6f6-149">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="3e6f6-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="3e6f6-150">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="3e6f6-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="3e6f6-151">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="3e6f6-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="3e6f6-152">Postupy: dotazu na ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3e6f6-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
