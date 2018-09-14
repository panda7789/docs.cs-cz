---
title: Převádění datových typů (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 54ef612ad4e92058d9af4d96b7b3cde9732b2f9c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585743"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="f4a64-102">Převádění datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="f4a64-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="f4a64-103">Převod metody změnit typ objektu, vstupu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="f4a64-104">Převod operace v dotazech LINQ jsou užitečné pro různé aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4a64-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="f4a64-105">Toto jsou některé příklady:</span><span class="sxs-lookup"><span data-stu-id="f4a64-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="f4a64-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metodu je možné skrýt vlastní implementaci typu operátoru standardního dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="f4a64-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metody slouží k povolení neparametrizované kolekce pro dotazování na LINQ.</span><span class="sxs-lookup"><span data-stu-id="f4a64-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="f4a64-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody je možné vynutit spuštění dotazu okamžité místo jeho odložit, dokud je vypočten dotaz.</span><span class="sxs-lookup"><span data-stu-id="f4a64-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4a64-109">Metody</span><span class="sxs-lookup"><span data-stu-id="f4a64-109">Methods</span></span>  
 <span data-ttu-id="f4a64-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="f4a64-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="f4a64-111">Převod metody v této tabulce, jejichž názvy začínají písmenem "Jako" Změna statického typu zdrojové kolekce, ale není výčet.</span><span class="sxs-lookup"><span data-stu-id="f4a64-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="f4a64-112">Metody, jejichž názvy začínají písmenem "Do výčet zdrojové kolekce a položky do příslušné kolekce" typu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="f4a64-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="f4a64-113">Method Name</span></span>|<span data-ttu-id="f4a64-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f4a64-114">Description</span></span>|<span data-ttu-id="f4a64-115">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4a64-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="f4a64-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="f4a64-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f4a64-117">Jako výčet</span><span class="sxs-lookup"><span data-stu-id="f4a64-117">AsEnumerable</span></span>|<span data-ttu-id="f4a64-118">Vrátí zadaný jako vstup <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f4a64-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="f4a64-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4a64-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a64-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="f4a64-120">AsQueryable</span></span>|<span data-ttu-id="f4a64-121">Převede (Obecné) <xref:System.Collections.IEnumerable> pro (obecný) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="f4a64-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="f4a64-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4a64-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a64-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="f4a64-123">Cast</span></span>|<span data-ttu-id="f4a64-124">Elementy kolekce do zadaného typu přetypování.</span><span class="sxs-lookup"><span data-stu-id="f4a64-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="f4a64-125">Pomocí proměnné explicitně rozsahu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="f4a64-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f4a64-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a64-127">OfType</span><span class="sxs-lookup"><span data-stu-id="f4a64-127">OfType</span></span>|<span data-ttu-id="f4a64-128">Hodnoty v závislosti na jejich schopnost převést na zadaný typ filtrů.</span><span class="sxs-lookup"><span data-stu-id="f4a64-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="f4a64-129">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4a64-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a64-130">ToArray –</span><span class="sxs-lookup"><span data-stu-id="f4a64-130">ToArray</span></span>|<span data-ttu-id="f4a64-131">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="f4a64-131">Converts a collection to an array.</span></span> <span data-ttu-id="f4a64-132">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-132">This method forces query execution.</span></span>|<span data-ttu-id="f4a64-133">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4a64-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a64-134">Metody ToDictionary</span><span class="sxs-lookup"><span data-stu-id="f4a64-134">ToDictionary</span></span>|<span data-ttu-id="f4a64-135">Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="f4a64-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="f4a64-136">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-136">This method forces query execution.</span></span>|<span data-ttu-id="f4a64-137">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4a64-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a64-138">ToList –</span><span class="sxs-lookup"><span data-stu-id="f4a64-138">ToList</span></span>|<span data-ttu-id="f4a64-139">Převede kolekci <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f4a64-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f4a64-140">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-140">This method forces query execution.</span></span>|<span data-ttu-id="f4a64-141">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4a64-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f4a64-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="f4a64-142">ToLookup</span></span>|<span data-ttu-id="f4a64-143">Vloží prvky do <xref:System.Linq.Lookup%602> (jeden na mnoho slovník) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="f4a64-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="f4a64-144">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="f4a64-144">This method forces query execution.</span></span>|<span data-ttu-id="f4a64-145">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4a64-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="f4a64-146">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="f4a64-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="f4a64-147">Následující příklad kódu používá proměnnou rozsahu explicitně zadali přetypovat na typ podtyp před přístupem k členu, který je k dispozici pouze na podtyp.</span><span class="sxs-lookup"><span data-stu-id="f4a64-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4a64-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4a64-148">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="f4a64-149">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="f4a64-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="f4a64-150">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="f4a64-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)  
- [<span data-ttu-id="f4a64-151">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="f4a64-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="f4a64-152">Postupy: vytvoření dotazu na ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="f4a64-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
