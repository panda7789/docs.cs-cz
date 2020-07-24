---
title: Převod datových typů (C#)
description: Metody převodu mění typ vstupních objektů. Viz operace převodu v dotazech LINQ v jazyce C#, jako je například vyčíslitelné. AsEnumerable a vyčíslitelné. OfType.
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 3291690f9aaee945ca7feb04ebbc676db2612894
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105492"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="0762b-104">Převod datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="0762b-104">Converting Data Types (C#)</span></span>
<span data-ttu-id="0762b-105">Metody převodu mění typ vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="0762b-105">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="0762b-106">Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích.</span><span class="sxs-lookup"><span data-stu-id="0762b-106">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="0762b-107">Následuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="0762b-107">Following are some examples:</span></span>

- <span data-ttu-id="0762b-108"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>Metoda může být použita ke skrytí vlastní implementace typu standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="0762b-108">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="0762b-109"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Metodu lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.</span><span class="sxs-lookup"><span data-stu-id="0762b-109">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="0762b-110"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>Metody, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> , <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení až do vypsání dotazu.</span><span class="sxs-lookup"><span data-stu-id="0762b-110">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="0762b-111">Metody</span><span class="sxs-lookup"><span data-stu-id="0762b-111">Methods</span></span>
 <span data-ttu-id="0762b-112">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.</span><span class="sxs-lookup"><span data-stu-id="0762b-112">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="0762b-113">Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet.</span><span class="sxs-lookup"><span data-stu-id="0762b-113">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="0762b-114">Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="0762b-114">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="0762b-115">Název metody</span><span class="sxs-lookup"><span data-stu-id="0762b-115">Method Name</span></span>|<span data-ttu-id="0762b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="0762b-116">Description</span></span>|<span data-ttu-id="0762b-117">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0762b-117">C# Query Expression Syntax</span></span>|<span data-ttu-id="0762b-118">Další informace</span><span class="sxs-lookup"><span data-stu-id="0762b-118">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="0762b-119">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="0762b-119">AsEnumerable</span></span>|<span data-ttu-id="0762b-120">Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="0762b-120">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="0762b-121">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="0762b-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0762b-122">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="0762b-122">AsQueryable</span></span>|<span data-ttu-id="0762b-123">Převede (Obecné) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="0762b-123">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="0762b-124">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="0762b-124">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0762b-125">Změna typu</span><span class="sxs-lookup"><span data-stu-id="0762b-125">Cast</span></span>|<span data-ttu-id="0762b-126">Přetypování prvky kolekce na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="0762b-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="0762b-127">Použijte explicitně typovou proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="0762b-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="0762b-128">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0762b-128">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0762b-129">Only</span><span class="sxs-lookup"><span data-stu-id="0762b-129">OfType</span></span>|<span data-ttu-id="0762b-130">Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="0762b-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="0762b-131">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="0762b-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0762b-132">ToArray –</span><span class="sxs-lookup"><span data-stu-id="0762b-132">ToArray</span></span>|<span data-ttu-id="0762b-133">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="0762b-133">Converts a collection to an array.</span></span> <span data-ttu-id="0762b-134">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="0762b-134">This method forces query execution.</span></span>|<span data-ttu-id="0762b-135">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="0762b-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0762b-136">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="0762b-136">ToDictionary</span></span>|<span data-ttu-id="0762b-137">Vloží prvky do prvku na <xref:System.Collections.Generic.Dictionary%602> základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="0762b-137">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="0762b-138">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="0762b-138">This method forces query execution.</span></span>|<span data-ttu-id="0762b-139">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="0762b-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0762b-140">ToList –</span><span class="sxs-lookup"><span data-stu-id="0762b-140">ToList</span></span>|<span data-ttu-id="0762b-141">Převede kolekci na <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="0762b-141">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="0762b-142">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="0762b-142">This method forces query execution.</span></span>|<span data-ttu-id="0762b-143">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="0762b-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="0762b-144">ToLookup</span><span class="sxs-lookup"><span data-stu-id="0762b-144">ToLookup</span></span>|<span data-ttu-id="0762b-145">Vloží prvky do <xref:System.Linq.Lookup%602> slovníku (do slovníku 1: n) na základě funkce selektoru klíče.</span><span class="sxs-lookup"><span data-stu-id="0762b-145">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="0762b-146">Tato metoda vynutí provedení dotazu.</span><span class="sxs-lookup"><span data-stu-id="0762b-146">This method forces query execution.</span></span>|<span data-ttu-id="0762b-147">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="0762b-147">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="0762b-148">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="0762b-148">Query Expression Syntax Example</span></span>

<span data-ttu-id="0762b-149">Následující příklad kódu používá explicitně typovou proměnnou rozsahu pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.</span><span class="sxs-lookup"><span data-stu-id="0762b-149">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0762b-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="0762b-150">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0762b-151">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="0762b-151">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0762b-152">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="0762b-152">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="0762b-153">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="0762b-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="0762b-154">Postup dotazování objektu ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="0762b-154">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
