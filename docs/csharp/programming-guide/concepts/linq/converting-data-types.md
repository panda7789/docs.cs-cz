---
title: Převod datových typů (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347203"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="ff454-102">Převod datových typů (C#)</span><span class="sxs-lookup"><span data-stu-id="ff454-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="ff454-103">Metody převodu mění typ vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="ff454-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="ff454-104">Operace převodu v dotazech LINQ jsou užitečné v různých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="ff454-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="ff454-105">Níže jsou uvedeny některé příklady:</span><span class="sxs-lookup"><span data-stu-id="ff454-105">Following are some examples:</span></span>

- <span data-ttu-id="ff454-106">Metodu <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> lze skrýt vlastní implementaci typu standardního operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="ff454-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="ff454-107">Metodu <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.</span><span class="sxs-lookup"><span data-stu-id="ff454-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="ff454-108">Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> a lze vynutit okamžité spuštění dotazu namísto jeho odložení, dokud není dotaz uveden do výčtu.</span><span class="sxs-lookup"><span data-stu-id="ff454-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="ff454-109">Metody</span><span class="sxs-lookup"><span data-stu-id="ff454-109">Methods</span></span>
 <span data-ttu-id="ff454-110">V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datového typu.</span><span class="sxs-lookup"><span data-stu-id="ff454-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="ff454-111">Metody převodu v této tabulce, jejichž názvy začínají na "As", mění statický typ zdrojové kolekce, ale nepředstavují její výčet.</span><span class="sxs-lookup"><span data-stu-id="ff454-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="ff454-112">Metody, jejichž názvy začínají "Chcete" výčet zdrojové kolekce a umístit položky do odpovídající ho typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="ff454-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="ff454-113">Název metody</span><span class="sxs-lookup"><span data-stu-id="ff454-113">Method Name</span></span>|<span data-ttu-id="ff454-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ff454-114">Description</span></span>|<span data-ttu-id="ff454-115">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff454-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="ff454-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="ff454-116">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="ff454-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="ff454-117">AsEnumerable</span></span>|<span data-ttu-id="ff454-118">Vrátí vstup zadaný <xref:System.Collections.Generic.IEnumerable%601>jako .</span><span class="sxs-lookup"><span data-stu-id="ff454-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="ff454-119">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ff454-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ff454-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="ff454-120">AsQueryable</span></span>|<span data-ttu-id="ff454-121">Převede (obecný) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="ff454-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="ff454-122">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ff454-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ff454-123">Změna typu</span><span class="sxs-lookup"><span data-stu-id="ff454-123">Cast</span></span>|<span data-ttu-id="ff454-124">Předává prvky kolekce na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="ff454-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="ff454-125">Použijte explicitně zadalicí proměnnou rozsahu.</span><span class="sxs-lookup"><span data-stu-id="ff454-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="ff454-126">Například:</span><span class="sxs-lookup"><span data-stu-id="ff454-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ff454-127">Oftype</span><span class="sxs-lookup"><span data-stu-id="ff454-127">OfType</span></span>|<span data-ttu-id="ff454-128">Filtruje hodnoty v závislosti na jejich schopnosti přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="ff454-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="ff454-129">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ff454-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ff454-130">Toarray</span><span class="sxs-lookup"><span data-stu-id="ff454-130">ToArray</span></span>|<span data-ttu-id="ff454-131">Převede kolekci na pole.</span><span class="sxs-lookup"><span data-stu-id="ff454-131">Converts a collection to an array.</span></span> <span data-ttu-id="ff454-132">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ff454-132">This method forces query execution.</span></span>|<span data-ttu-id="ff454-133">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ff454-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ff454-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="ff454-134">ToDictionary</span></span>|<span data-ttu-id="ff454-135">Vloží prvky <xref:System.Collections.Generic.Dictionary%602> do funkce voliče klíčů.</span><span class="sxs-lookup"><span data-stu-id="ff454-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="ff454-136">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ff454-136">This method forces query execution.</span></span>|<span data-ttu-id="ff454-137">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ff454-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ff454-138">Tolist</span><span class="sxs-lookup"><span data-stu-id="ff454-138">ToList</span></span>|<span data-ttu-id="ff454-139">Převede kolekci <xref:System.Collections.Generic.List%601>na .</span><span class="sxs-lookup"><span data-stu-id="ff454-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ff454-140">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ff454-140">This method forces query execution.</span></span>|<span data-ttu-id="ff454-141">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ff454-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ff454-142">Vyhledávání</span><span class="sxs-lookup"><span data-stu-id="ff454-142">ToLookup</span></span>|<span data-ttu-id="ff454-143">Vloží prvky <xref:System.Linq.Lookup%602> do (slovníku 1:N) na základě funkce voliče klíčů.</span><span class="sxs-lookup"><span data-stu-id="ff454-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="ff454-144">Tato metoda vynutí spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="ff454-144">This method forces query execution.</span></span>|<span data-ttu-id="ff454-145">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ff454-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="ff454-146">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="ff454-146">Query Expression Syntax Example</span></span>

<span data-ttu-id="ff454-147">Následující příklad kódu používá explicitně zadaný rozsah proměnné přetypování typu podtypu před přístupem k člen, který je k dispozici pouze na podtypu.</span><span class="sxs-lookup"><span data-stu-id="ff454-147">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ff454-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff454-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ff454-149">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="ff454-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ff454-150">from – klauzule</span><span class="sxs-lookup"><span data-stu-id="ff454-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="ff454-151">Výrazy dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="ff454-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="ff454-152">Jak dotaz ArrayList s LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="ff454-152">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
