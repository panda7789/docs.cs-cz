---
title: Kolekce (C#)
description: Seznamte se s kolekcemi v jazyce C#, které jsou používány pro práci se skupinami objektů. Kolekce lze dynamicky zvětšovat a zmenšovat podle potřeby změny aplikace.
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 2375980e2915d4daa5a221a94eee2aea41959852
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924926"
---
# <a name="collections-c"></a><span data-ttu-id="7c4f4-104">Kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="7c4f4-104">Collections (C#)</span></span>

<span data-ttu-id="7c4f4-105">U mnoha aplikací chcete vytvořit a spravovat skupiny souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-105">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="7c4f4-106">Existují dva způsoby, jak seskupit objekty: vytvořením polí objektů a vytvořením kolekcí objektů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-106">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="7c4f4-107">Pole jsou užitečná pro vytváření a práci s pevným počtem silně typových objektů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-107">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="7c4f4-108">Informace o polích naleznete v tématu [Arrays](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-108">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="7c4f4-109">Kolekce poskytují pružnější způsob práce se skupinami objektů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-109">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="7c4f4-110">Na rozdíl od polí mohou skupiny objektů, se kterými pracujete, dynamicky zvětšovat a zmenšovat podle potřeb změny aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-110">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="7c4f4-111">U některých kolekcí můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, abyste mohli rychle načíst objekt pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-111">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="7c4f4-112">Kolekce je třída, takže před přidáním prvků do této kolekce je nutné deklarovat instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-112">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="7c4f4-113">Pokud kolekce obsahuje prvky pouze jednoho typu dat, můžete použít jednu ze tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-113">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7c4f4-114">Obecná kolekce vynutila bezpečnost typů, takže do ní nelze přidat žádný jiný datový typ.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-114">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="7c4f4-115">Při načítání prvku z obecné kolekce není nutné určit jeho datový typ nebo ho převést.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-115">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="7c4f4-116">Příklady v tomto tématu zahrnují direktivy [using](../../language-reference/keywords/using-directive.md) pro `System.Collections.Generic` `System.Linq` obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-116">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="7c4f4-117">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="7c4f4-117">**In this topic**</span></span>

- [<span data-ttu-id="7c4f4-118">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-118">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="7c4f4-119">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="7c4f4-119">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="7c4f4-120">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="7c4f4-120">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="7c4f4-121">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="7c4f4-121">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="7c4f4-122">Třídy System. Collections</span><span class="sxs-lookup"><span data-stu-id="7c4f4-122">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="7c4f4-123">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="7c4f4-123">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="7c4f4-124">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="7c4f4-124">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="7c4f4-125">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-125">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="7c4f4-126">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-126">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="7c4f4-127">Iterátory</span><span class="sxs-lookup"><span data-stu-id="7c4f4-127">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="7c4f4-128">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-128">Using a Simple Collection</span></span>

<span data-ttu-id="7c4f4-129">Příklady v této části používají obecnou <xref:System.Collections.Generic.List%601> třídu, která umožňuje pracovat se seznamem objektů se silným typem.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-129">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="7c4f4-130">Následující příklad vytvoří seznam řetězců a pak prochází řetězce pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-130">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="7c4f4-131">Pokud je obsah kolekce znám předem, můžete kolekci inicializovat pomocí *inicializátoru kolekce* .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-131">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="7c4f4-132">Další informace naleznete v tématu [Inicializátory objektů a kolekcí](../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-132">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="7c4f4-133">Následující příklad je stejný jako předchozí příklad, s výjimkou, že inicializátor kolekce se používá pro přidání prvků do kolekce.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-133">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="7c4f4-134">Můžete použít příkaz [for](../../language-reference/keywords/for.md) namísto `foreach` příkazu pro iteraci v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-134">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="7c4f4-135">Toho dosáhnete přístupem k prvkům kolekce na pozici indexu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-135">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="7c4f4-136">Index prvků začíná na 0 a končí v počtu elementů minus 1.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-136">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="7c4f4-137">Následující příklad provede iteraci prvků kolekce pomocí `for` místo `foreach` .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-137">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="7c4f4-138">Následující příklad odebere prvek z kolekce zadáním objektu, který chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-138">The following example removes an element from the collection by specifying the object to remove.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

<span data-ttu-id="7c4f4-139">Následující příklad odstraní prvky z obecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-139">The following example removes elements from a generic list.</span></span> <span data-ttu-id="7c4f4-140">Místo příkazu se `foreach` používá příkaz [for](../../language-reference/keywords/for.md) , který iteruje v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-140">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="7c4f4-141">Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-141">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

<span data-ttu-id="7c4f4-142">Pro typ prvků v <xref:System.Collections.Generic.List%601> , můžete také definovat vlastní třídu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-142">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="7c4f4-143">V následujícím příkladu `Galaxy` třída, která je použita v, <xref:System.Collections.Generic.List%601> je definována v kódu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-143">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="7c4f4-144">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="7c4f4-144">Kinds of Collections</span></span>

<span data-ttu-id="7c4f4-145">Rozhraní .NET poskytuje mnoho běžných kolekcí.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-145">Many common collections are provided by .NET.</span></span> <span data-ttu-id="7c4f4-146">Každý typ kolekce je navržený pro konkrétní účel.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-146">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="7c4f4-147">Některé společné třídy kolekcí jsou popsány v této části:</span><span class="sxs-lookup"><span data-stu-id="7c4f4-147">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="7c4f4-148"><xref:System.Collections.Generic> – třídy</span><span class="sxs-lookup"><span data-stu-id="7c4f4-148"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="7c4f4-149"><xref:System.Collections.Concurrent> – třídy</span><span class="sxs-lookup"><span data-stu-id="7c4f4-149"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="7c4f4-150"><xref:System.Collections> – třídy</span><span class="sxs-lookup"><span data-stu-id="7c4f4-150"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="7c4f4-151">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="7c4f4-151">System.Collections.Generic Classes</span></span>

<span data-ttu-id="7c4f4-152">Můžete vytvořit obecnou kolekci pomocí jedné ze tříd v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="7c4f4-153">Obecná kolekce je užitečná, pokud má každá položka v kolekci stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="7c4f4-154">Obecná kolekce vynutila silné typování tím, že umožňuje přidat pouze požadovaný datový typ.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="7c4f4-155">V následující tabulce jsou uvedeny některé z často používaných tříd <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="7c4f4-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="7c4f4-156">Třída</span><span class="sxs-lookup"><span data-stu-id="7c4f4-156">Class</span></span>|<span data-ttu-id="7c4f4-157">Popis</span><span class="sxs-lookup"><span data-stu-id="7c4f4-157">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="7c4f4-158">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě klíče.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="7c4f4-159">Představuje seznam objektů, které mohou být k dispozici v indexu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="7c4f4-160">Poskytuje metody pro hledání, řazení a úpravy seznamů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-160">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="7c4f4-161">Představuje kolekci objektů first in, First out (FIFO).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="7c4f4-162">Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="7c4f4-163">Představuje kolekci objektů Last in, First out (LIFO).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="7c4f4-164">Další informace naleznete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic> .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="7c4f4-165">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="7c4f4-165">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="7c4f4-166">V .NET Framework 4 a novějších verzích kolekce v <xref:System.Collections.Concurrent> oboru názvů poskytují efektivní operace bezpečné pro přístup z více vláken pro přístup k položkám kolekce z více vláken.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-166">In .NET Framework 4 and later versions, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="7c4f4-167">Třídy v <xref:System.Collections.Concurrent> oboru názvů by měly být použity namísto odpovídajících typů v <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections?displayProperty=nameWithType> oborech názvů a pokaždé, když více vláken přistupuje souběžně k kolekci.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="7c4f4-168">Další informace najdete v tématu [kolekce bezpečné](../../../standard/collections/thread-safe/index.md) pro přístup z více vláken a <xref:System.Collections.Concurrent> .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="7c4f4-169">Některé třídy <xref:System.Collections.Concurrent> , které jsou součástí oboru názvů <xref:System.Collections.Concurrent.BlockingCollection%601> , jsou, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601> .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="7c4f4-170">Třídy System. Collections</span><span class="sxs-lookup"><span data-stu-id="7c4f4-170">System.Collections Classes</span></span>

<span data-ttu-id="7c4f4-171">Třídy v <xref:System.Collections?displayProperty=nameWithType> oboru názvů neukládají prvky jako specificky typové objekty, ale jako objekty typu `Object` .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="7c4f4-172">Kdykoli je to možné, použijte obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> obor názvů namísto starších typů v `System.Collections` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="7c4f4-173">Následující tabulka uvádí některé často používané třídy v `System.Collections` oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="7c4f4-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="7c4f4-174">Třída</span><span class="sxs-lookup"><span data-stu-id="7c4f4-174">Class</span></span>|<span data-ttu-id="7c4f4-175">Popis</span><span class="sxs-lookup"><span data-stu-id="7c4f4-175">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="7c4f4-176">Představuje pole objektů, jejichž velikost se dynamicky zvětšuje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="7c4f4-177">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hash klíče.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="7c4f4-178">Představuje kolekci objektů first in, First out (FIFO).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="7c4f4-179">Představuje kolekci objektů Last in, First out (LIFO).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="7c4f4-180"><xref:System.Collections.Specialized>Obor názvů poskytuje specializované třídy kolekcí se silnými typy, jako jsou jenom řetězcové kolekce a propojené seznamy a hybridní slovníky.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="7c4f4-181">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="7c4f4-181">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="7c4f4-182"><xref:System.Collections.Generic.Dictionary%602>Obecná kolekce umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-182">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="7c4f4-183">Každé přidání do slovníku se skládá z hodnoty a jejího přidruženého klíče.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-183">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="7c4f4-184">Načítání hodnoty pomocí klíče je rychlé, protože `Dictionary` Třída je implementována jako zatřiďovací tabulka.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-184">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="7c4f4-185">Následující příklad vytvoří `Dictionary` kolekci a iteruje prostřednictvím slovníku pomocí `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-185">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<span data-ttu-id="7c4f4-186">Chcete-li místo toho použít inicializátor kolekce k sestavení `Dictionary` kolekce, můžete nahradit `BuildDictionary` metody a `AddToDictionary` následující metodou.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-186">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

<span data-ttu-id="7c4f4-187">Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodu a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` pro rychlé vyhledání položky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-187">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="7c4f4-188">`Item`Vlastnost umožňuje přístup k položce v `elements` kolekci pomocí `elements[symbol]` jazyka v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-188">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

<span data-ttu-id="7c4f4-189">Následující příklad místo toho používá <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metodu pro rychlé vyhledání položky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-189">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="7c4f4-190">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="7c4f4-190">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="7c4f4-191">LINQ (jazykově integrovaný dotaz) lze použít pro přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-191">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="7c4f4-192">Dotazy LINQ poskytují možnosti filtrování, řazení a seskupování.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-192">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="7c4f4-193">Další informace naleznete v tématu [Začínáme pomocí LINQ v jazyce C#](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-193">For more information, see [Getting Started with LINQ in C#](linq/index.md).</span></span>

<span data-ttu-id="7c4f4-194">Následující příklad spustí dotaz LINQ na obecné `List` .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-194">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="7c4f4-195">Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-195">The LINQ query returns a different collection that contains the results.</span></span>

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="7c4f4-196">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-196">Sorting a Collection</span></span>

<span data-ttu-id="7c4f4-197">Následující příklad znázorňuje postup pro řazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-197">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="7c4f4-198">Příklad řadí instance `Car` třídy, které jsou uloženy v <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-198">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="7c4f4-199">`Car`Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje <xref:System.IComparable%601.CompareTo%2A> implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-199">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="7c4f4-200">Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá k řazení.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-200">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="7c4f4-201">Uživatelsky psaný kód v `CompareTo` metodě vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-201">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="7c4f4-202">Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula, pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-202">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="7c4f4-203">To umožňuje definovat v kódu kritéria pro větší než, menší než a rovno.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-203">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="7c4f4-204">V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-204">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="7c4f4-205">Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody metody <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` Metoda bude automaticky volána pro `Car` objekty v `List` .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-205">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="7c4f4-206">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-206">Defining a Custom Collection</span></span>

<span data-ttu-id="7c4f4-207">Kolekci můžete definovat implementací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> rozhraní nebo.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-207">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="7c4f4-208">I když můžete definovat vlastní kolekci, je obvykle vhodnější použít kolekce, které jsou součástí rozhraní .NET, které jsou popsány v [části druhy kolekcí](#BKMK_KindsOfCollections) výše v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-208">Although you can define a custom collection, it is usually better to instead use the collections that are included in .NET, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this article.</span></span>

<span data-ttu-id="7c4f4-209">Následující příklad definuje vlastní třídu kolekce s názvem `AllColors` .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-209">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="7c4f4-210">Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-210">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="7c4f4-211">`GetEnumerator`Metoda vrátí instanci `ColorEnumerator` třídy.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-211">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="7c4f4-212">`ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby byla <xref:System.Collections.IEnumerator.Current%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> implementována vlastnost, metoda a <xref:System.Collections.IEnumerator.Reset%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-212">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="7c4f4-213">Iterátory</span><span class="sxs-lookup"><span data-stu-id="7c4f4-213">Iterators</span></span>

<span data-ttu-id="7c4f4-214">*Iterátor* se používá k provedení vlastní iterace v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-214">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="7c4f4-215">Iterátor může být metoda nebo `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-215">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="7c4f4-216">Iterátor používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého prvku kolekce po jednom.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-216">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="7c4f4-217">Zavoláte iterátor pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-217">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="7c4f4-218">Každá iterace `foreach` smyčky volá iterátor.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-218">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="7c4f4-219">Při `yield return` dosažení příkazu v iterátoru je vrácen výraz a aktuální umístění v kódu je uchováno.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-219">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="7c4f4-220">Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-220">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="7c4f4-221">Další informace najdete v tématu [iterátory (C#)](./iterators.md).</span><span class="sxs-lookup"><span data-stu-id="7c4f4-221">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="7c4f4-222">Následující příklad používá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-222">The following example uses an iterator method.</span></span> <span data-ttu-id="7c4f4-223">Metoda iterátoru obsahuje `yield return` příkaz, který je uvnitř smyčky [for](../../language-reference/keywords/for.md) .</span><span class="sxs-lookup"><span data-stu-id="7c4f4-223">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="7c4f4-224">V `ListEvenNumbers` metodě Každá iterace `foreach` těla příkazu vytvoří volání metody iterátoru, která pokračuje k dalšímu `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7c4f4-224">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="7c4f4-225">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c4f4-225">See also</span></span>

- [<span data-ttu-id="7c4f4-226">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-226">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="7c4f4-227">Koncepty programování (C#)</span><span class="sxs-lookup"><span data-stu-id="7c4f4-227">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="7c4f4-228">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="7c4f4-228">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="7c4f4-229">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="7c4f4-229">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="7c4f4-230">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7c4f4-230">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="7c4f4-231">Kolekce a datové struktury</span><span class="sxs-lookup"><span data-stu-id="7c4f4-231">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="7c4f4-232">Výběr třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-232">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="7c4f4-233">Porovnání a řazení v rámci kolekcí</span><span class="sxs-lookup"><span data-stu-id="7c4f4-233">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="7c4f4-234">Kdy použít obecné kolekce</span><span class="sxs-lookup"><span data-stu-id="7c4f4-234">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
