---
title: Převádění datových typůC#()
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: ddd9407c3b7e25dbfb8fc0bddb5daab7db2e4e53
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418616"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="1079d-102">Převádění datových typůC#()</span><span class="sxs-lookup"><span data-stu-id="1079d-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="1079d-103">Metody převodu mění typ vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="1079d-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="1079d-104">Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích.</span><span class="sxs-lookup"><span data-stu-id="1079d-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="1079d-105">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="1079d-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="1079d-106">Pomocí metody <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> lze skrýt vlastní implementaci standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="1079d-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="1079d-107">Metodu <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.</span><span class="sxs-lookup"><span data-stu-id="1079d-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="1079d-108">Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení, dokud se dotaz nevytvoří.</span><span class="sxs-lookup"><span data-stu-id="1079d-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1079d-109">Metody</span><span class="sxs-lookup"><span data-stu-id="1079d-109">Methods</span></span>  
 <span data-ttu-id="1079d-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="1079d-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="1079d-111">Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet.</span><span class="sxs-lookup"><span data-stu-id="1079d-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="1079d-112">Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="1079d-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="1079d-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="1079d-113">Method Name</span></span>|<span data-ttu-id="1079d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1079d-114">Description</span></span>|<span data-ttu-id="1079d-115">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="1079d-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="1079d-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="1079d-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="1079d-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="1079d-117">AsEnumerable</span></span>|<span data-ttu-id="1079d-118">Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1079d-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="1079d-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1079d-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1079d-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="1079d-120">AsQueryable</span></span>|<span data-ttu-id="1079d-121">Převede (Generic) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="1079d-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="1079d-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1079d-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1079d-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="1079d-123">Cast</span></span>|<span data-ttu-id="1079d-124">Přetypování prvky kolekce na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="1079d-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="1079d-125">Použijte explicitně typovou proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="1079d-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="1079d-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1079d-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1079d-127">Only</span><span class="sxs-lookup"><span data-stu-id="1079d-127">OfType</span></span>|<span data-ttu-id="1079d-128">Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="1079d-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="1079d-129">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1079d-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1079d-130">ToArray –</span><span class="sxs-lookup"><span data-stu-id="1079d-130">ToArray</span></span>|<span data-ttu-id="1079d-131">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="1079d-131">Converts a collection to an array.</span></span> <span data-ttu-id="1079d-132">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="1079d-132">This method forces query execution.</span></span>|<span data-ttu-id="1079d-133">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1079d-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1079d-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="1079d-134">ToDictionary</span></span>|<span data-ttu-id="1079d-135">Vloží prvky do <xref:System.Collections.Generic.Dictionary%602> na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="1079d-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="1079d-136">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="1079d-136">This method forces query execution.</span></span>|<span data-ttu-id="1079d-137">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1079d-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1079d-138">ToList –</span><span class="sxs-lookup"><span data-stu-id="1079d-138">ToList</span></span>|<span data-ttu-id="1079d-139">Převede kolekci na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="1079d-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1079d-140">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="1079d-140">This method forces query execution.</span></span>|<span data-ttu-id="1079d-141">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1079d-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1079d-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="1079d-142">ToLookup</span></span>|<span data-ttu-id="1079d-143">Vloží prvky do <xref:System.Linq.Lookup%602> (slovník 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="1079d-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="1079d-144">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="1079d-144">This method forces query execution.</span></span>|<span data-ttu-id="1079d-145">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1079d-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="1079d-146">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="1079d-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="1079d-147">Následující příklad kódu používá explicitně typovou proměnnou rozsahu pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.</span><span class="sxs-lookup"><span data-stu-id="1079d-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1079d-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1079d-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1079d-149">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="1079d-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="1079d-150">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="1079d-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="1079d-151">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="1079d-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="1079d-152">Postupy: dotazování objektu ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1079d-152">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
