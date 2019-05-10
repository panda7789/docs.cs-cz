---
title: Převádění datových typů (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 918a9fbfc523e62c7b4a5d915c28c00ea781d3e4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597714"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="b1386-102">Převádění datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="b1386-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="b1386-103">Převod metody změnit typ objektu, vstupu.</span><span class="sxs-lookup"><span data-stu-id="b1386-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="b1386-104">Převod operace v dotazech LINQ jsou užitečné pro různé aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1386-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="b1386-105">Toto jsou některé příklady:</span><span class="sxs-lookup"><span data-stu-id="b1386-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="b1386-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metodu je možné skrýt vlastní implementaci typu operátoru standardního dotazu.</span><span class="sxs-lookup"><span data-stu-id="b1386-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="b1386-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metody slouží k povolení neparametrizované kolekce pro dotazování na LINQ.</span><span class="sxs-lookup"><span data-stu-id="b1386-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="b1386-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody je možné vynutit spuštění dotazu okamžité místo jeho odložit, dokud je vypočten dotaz.</span><span class="sxs-lookup"><span data-stu-id="b1386-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1386-109">Metody</span><span class="sxs-lookup"><span data-stu-id="b1386-109">Methods</span></span>  
 <span data-ttu-id="b1386-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="b1386-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="b1386-111">Převod metody v této tabulce, jejichž názvy začínají písmenem "Jako" Změna statického typu zdrojové kolekce, ale není výčet.</span><span class="sxs-lookup"><span data-stu-id="b1386-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="b1386-112">Metody, jejichž názvy začínají písmenem "Do výčet zdrojové kolekce a položky do příslušné kolekce" typu.</span><span class="sxs-lookup"><span data-stu-id="b1386-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="b1386-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="b1386-113">Method Name</span></span>|<span data-ttu-id="b1386-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b1386-114">Description</span></span>|<span data-ttu-id="b1386-115">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1386-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="b1386-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="b1386-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b1386-117">Jako výčet</span><span class="sxs-lookup"><span data-stu-id="b1386-117">AsEnumerable</span></span>|<span data-ttu-id="b1386-118">Vrátí zadaný jako vstup <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b1386-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="b1386-119">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1386-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b1386-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="b1386-120">AsQueryable</span></span>|<span data-ttu-id="b1386-121">Převede (Obecné) <xref:System.Collections.IEnumerable> pro (obecný) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="b1386-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="b1386-122">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1386-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b1386-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="b1386-123">Cast</span></span>|<span data-ttu-id="b1386-124">Elementy kolekce do zadaného typu přetypování.</span><span class="sxs-lookup"><span data-stu-id="b1386-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="b1386-125">Pomocí proměnné explicitně rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b1386-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="b1386-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1386-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b1386-127">OfType</span><span class="sxs-lookup"><span data-stu-id="b1386-127">OfType</span></span>|<span data-ttu-id="b1386-128">Hodnoty v závislosti na jejich schopnost převést na zadaný typ filtrů.</span><span class="sxs-lookup"><span data-stu-id="b1386-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="b1386-129">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1386-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b1386-130">ToArray –</span><span class="sxs-lookup"><span data-stu-id="b1386-130">ToArray</span></span>|<span data-ttu-id="b1386-131">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="b1386-131">Converts a collection to an array.</span></span> <span data-ttu-id="b1386-132">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b1386-132">This method forces query execution.</span></span>|<span data-ttu-id="b1386-133">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1386-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b1386-134">Metody ToDictionary</span><span class="sxs-lookup"><span data-stu-id="b1386-134">ToDictionary</span></span>|<span data-ttu-id="b1386-135">Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="b1386-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="b1386-136">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b1386-136">This method forces query execution.</span></span>|<span data-ttu-id="b1386-137">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1386-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b1386-138">ToList –</span><span class="sxs-lookup"><span data-stu-id="b1386-138">ToList</span></span>|<span data-ttu-id="b1386-139">Převede kolekci <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="b1386-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="b1386-140">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b1386-140">This method forces query execution.</span></span>|<span data-ttu-id="b1386-141">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1386-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b1386-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="b1386-142">ToLookup</span></span>|<span data-ttu-id="b1386-143">Vloží prvky do <xref:System.Linq.Lookup%602> (jeden na mnoho slovník) podle funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="b1386-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="b1386-144">Tato metoda donutí provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b1386-144">This method forces query execution.</span></span>|<span data-ttu-id="b1386-145">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b1386-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b1386-146">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="b1386-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b1386-147">Následující příklad kódu používá proměnnou rozsahu explicitně zadali přetypovat na typ podtyp před přístupem k členu, který je k dispozici pouze na podtyp.</span><span class="sxs-lookup"><span data-stu-id="b1386-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1386-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1386-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b1386-149">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="b1386-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b1386-150">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="b1386-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)
- [<span data-ttu-id="b1386-151">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="b1386-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="b1386-152">Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="b1386-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
