---
title: Kolekce (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: d2996648690fc03b5f1d6a90e0be96155c5a24ed
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645470"
---
# <a name="collections-c"></a><span data-ttu-id="8d671-102">Kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="8d671-102">Collections (C#)</span></span>

<span data-ttu-id="8d671-103">Pro mnoho aplikací chcete vytvořit a spravovat skupiny souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="8d671-104">Existují dva způsoby seskupení objektů: vytvořením polí objektů a vytvořením kolekcí objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="8d671-105">Pole jsou nejužitečnější pro vytváření a práci s pevným počtem objektů silného typu.</span><span class="sxs-lookup"><span data-stu-id="8d671-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="8d671-106">Informace o polích naleznete v [tématu Arrays](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d671-106">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="8d671-107">Kolekce poskytují flexibilnější způsob práce se skupinami objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="8d671-108">Na rozdíl od polí může skupina objektů, se kterými pracujete, dynamicky růst a zmenšovat podle potřeby aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d671-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="8d671-109">Pro některé kolekce můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="8d671-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="8d671-110">Kolekce je třída, takže je nutné deklarovat instanci třídy před přidáním prvků do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d671-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="8d671-111">Pokud vaše kolekce obsahuje prvky pouze jednoho datového typu, <xref:System.Collections.Generic?displayProperty=nameWithType> můžete použít jednu z tříd v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8d671-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8d671-112">Obecná kolekce vynucuje bezpečnost typů tak, aby do ní nebylo možné přidat žádný jiný datový typ.</span><span class="sxs-lookup"><span data-stu-id="8d671-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="8d671-113">Při načtení prvku z obecné kolekce, není nutné určit jeho datový typ nebo převést.</span><span class="sxs-lookup"><span data-stu-id="8d671-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="8d671-114">Příklady v tomto tématu patří [použití](../../language-reference/keywords/using-directive.md) `System.Collections.Generic` direktiv y pro a `System.Linq` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="8d671-114">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="8d671-115">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="8d671-115">**In this topic**</span></span>

- [<span data-ttu-id="8d671-116">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="8d671-117">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="8d671-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="8d671-118">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="8d671-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="8d671-119">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="8d671-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="8d671-120">Třídy System.Collections</span><span class="sxs-lookup"><span data-stu-id="8d671-120">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="8d671-121">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="8d671-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="8d671-122">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="8d671-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="8d671-123">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-123">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="8d671-124">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="8d671-125">Iterátory</span><span class="sxs-lookup"><span data-stu-id="8d671-125">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="8d671-126">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-126">Using a Simple Collection</span></span>

<span data-ttu-id="8d671-127">Příklady v této části <xref:System.Collections.Generic.List%601> používají obecnou třídu, která umožňuje pracovat se silným seznamem objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="8d671-128">Následující příklad vytvoří seznam řetězců a potom iterates prostřednictvím řetězce pomocí [foreach](../../language-reference/keywords/foreach-in.md) prohlášení.</span><span class="sxs-lookup"><span data-stu-id="8d671-128">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

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

<span data-ttu-id="8d671-129">Pokud obsah kolekce jsou známy předem, můžete použít *inicializační kolekce* inicializovat kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d671-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="8d671-130">Další informace naleznete v [tématu Objekt a kolekce Initializers](../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="8d671-130">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="8d671-131">Následující příklad je stejný jako v předchozím příkladu, s výjimkou inicializátor kolekce se používá k přidání prvků do kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d671-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

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

<span data-ttu-id="8d671-132">Můžete použít [for](../../language-reference/keywords/for.md) příkaz namísto příkazu `foreach` iterát prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d671-132">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="8d671-133">Toho lze provést přístupem k prvky kolekce podle pozice indexu.</span><span class="sxs-lookup"><span data-stu-id="8d671-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="8d671-134">Index prvků začíná na 0 a končí na počet prvků minus 1.</span><span class="sxs-lookup"><span data-stu-id="8d671-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="8d671-135">Následující příklad iterates prostřednictvím prvky `for` kolekce `foreach`pomocí místo .</span><span class="sxs-lookup"><span data-stu-id="8d671-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

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

<span data-ttu-id="8d671-136">Následující příklad odebere prvek z kolekce zadáním objektu, který má být odebrán.</span><span class="sxs-lookup"><span data-stu-id="8d671-136">The following example removes an element from the collection by specifying the object to remove.</span></span>

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

<span data-ttu-id="8d671-137">Následující příklad odebere prvky z obecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="8d671-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="8d671-138">Místo příkazu `foreach` se používá [příkaz for,](../../language-reference/keywords/for.md) který itezuje v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8d671-138">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="8d671-139">Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraný prvek mít nižší hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="8d671-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

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

<span data-ttu-id="8d671-140">Pro typ prvků v <xref:System.Collections.Generic.List%601>aplikaci můžete také definovat vlastní třídu.</span><span class="sxs-lookup"><span data-stu-id="8d671-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="8d671-141">V následujícím příkladu `Galaxy` je třída, <xref:System.Collections.Generic.List%601> která je používána, definována v kódu.</span><span class="sxs-lookup"><span data-stu-id="8d671-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

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

## <a name="kinds-of-collections"></a><span data-ttu-id="8d671-142">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="8d671-142">Kinds of Collections</span></span>

<span data-ttu-id="8d671-143">Mnoho běžných kolekcí poskytuje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d671-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="8d671-144">Každý typ kolekce je určen pro konkrétní účel.</span><span class="sxs-lookup"><span data-stu-id="8d671-144">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="8d671-145">Některé běžné třídy kolekce jsou popsány v této části:</span><span class="sxs-lookup"><span data-stu-id="8d671-145">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="8d671-146"><xref:System.Collections.Generic> – třídy</span><span class="sxs-lookup"><span data-stu-id="8d671-146"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="8d671-147"><xref:System.Collections.Concurrent> – třídy</span><span class="sxs-lookup"><span data-stu-id="8d671-147"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="8d671-148"><xref:System.Collections> – třídy</span><span class="sxs-lookup"><span data-stu-id="8d671-148"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="8d671-149">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="8d671-149">System.Collections.Generic Classes</span></span>

<span data-ttu-id="8d671-150">Můžete vytvořit obecnou kolekci pomocí jedné z <xref:System.Collections.Generic> tříd v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8d671-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="8d671-151">Obecná kolekce je užitečná, když každá položka v kolekci má stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="8d671-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="8d671-152">Obecná kolekce vynucuje silné psaní tím, že umožňuje pouze požadovaný datový typ, který má být přidán.</span><span class="sxs-lookup"><span data-stu-id="8d671-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="8d671-153">V následující tabulce jsou uvedeny některé <xref:System.Collections.Generic?displayProperty=nameWithType> často používané třídy oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="8d671-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="8d671-154">Třída</span><span class="sxs-lookup"><span data-stu-id="8d671-154">Class</span></span>|<span data-ttu-id="8d671-155">Popis</span><span class="sxs-lookup"><span data-stu-id="8d671-155">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="8d671-156">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě klíče.</span><span class="sxs-lookup"><span data-stu-id="8d671-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="8d671-157">Představuje seznam objektů, které lze přistupovat index.</span><span class="sxs-lookup"><span data-stu-id="8d671-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="8d671-158">Poskytuje metody pro vyhledávání, řazení a úpravy seznamů.</span><span class="sxs-lookup"><span data-stu-id="8d671-158">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="8d671-159">Představuje první in, first out (FIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="8d671-160">Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="8d671-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="8d671-161">Představuje poslední in, first out (LIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="8d671-162">Další informace naleznete [v tématu Běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="8d671-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="8d671-163">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="8d671-163">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="8d671-164">V rozhraní .NET Framework 4 nebo novější <xref:System.Collections.Concurrent> kolekce v oboru názvů poskytují efektivní operace bezpečné pro přístup k kolekcím z více vláken.</span><span class="sxs-lookup"><span data-stu-id="8d671-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="8d671-165">Třídy v <xref:System.Collections.Concurrent> oboru názvů by měly být <xref:System.Collections.Generic?displayProperty=nameWithType> použity namísto odpovídající typy v a <xref:System.Collections?displayProperty=nameWithType> obory názvů vždy více vláken přístup ke kolekci současně.</span><span class="sxs-lookup"><span data-stu-id="8d671-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="8d671-166">Další informace naleznete v [tématu Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="8d671-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="8d671-167">Některé třídy <xref:System.Collections.Concurrent> zahrnuté <xref:System.Collections.Concurrent.BlockingCollection%601>v <xref:System.Collections.Concurrent.ConcurrentDictionary%602> <xref:System.Collections.Concurrent.ConcurrentQueue%601>oboru <xref:System.Collections.Concurrent.ConcurrentStack%601>názvů jsou , , , a .</span><span class="sxs-lookup"><span data-stu-id="8d671-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="8d671-168">Třídy System.Collections</span><span class="sxs-lookup"><span data-stu-id="8d671-168">System.Collections Classes</span></span>

<span data-ttu-id="8d671-169">Třídy v <xref:System.Collections?displayProperty=nameWithType> oboru názvů neukládají prvky jako specificky `Object`zadané objekty, ale jako objekty typu .</span><span class="sxs-lookup"><span data-stu-id="8d671-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="8d671-170">Kdykoli je to možné, měli byste <xref:System.Collections.Generic?displayProperty=nameWithType> použít obecné <xref:System.Collections.Concurrent> kolekce v oboru názvů `System.Collections` nebo oboru názvů namísto starších typů v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8d671-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="8d671-171">V následující tabulce jsou uvedeny některé `System.Collections` často používané třídy v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="8d671-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="8d671-172">Třída</span><span class="sxs-lookup"><span data-stu-id="8d671-172">Class</span></span>|<span data-ttu-id="8d671-173">Popis</span><span class="sxs-lookup"><span data-stu-id="8d671-173">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="8d671-174">Představuje pole objektů, jejichž velikost je dynamicky zvýšena podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="8d671-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="8d671-175">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hash klíče.</span><span class="sxs-lookup"><span data-stu-id="8d671-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="8d671-176">Představuje první in, first out (FIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="8d671-177">Představuje poslední in, first out (LIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="8d671-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="8d671-178">Obor <xref:System.Collections.Specialized> názvů poskytuje specializované a silné typy tříd kolekce, jako jsou například kolekce pouze řetězce a propojené seznam a hybridní slovníky.</span><span class="sxs-lookup"><span data-stu-id="8d671-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="8d671-179">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="8d671-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="8d671-180">Obecná <xref:System.Collections.Generic.Dictionary%602> kolekce umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku.</span><span class="sxs-lookup"><span data-stu-id="8d671-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="8d671-181">Každý doplněk do slovníku se skládá z hodnoty a jeho přidruženého klíče.</span><span class="sxs-lookup"><span data-stu-id="8d671-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="8d671-182">Načítání hodnoty pomocí jeho klíče je `Dictionary` rychlé, protože třída je implementována jako tabulka hash.</span><span class="sxs-lookup"><span data-stu-id="8d671-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="8d671-183">Následující příklad vytvoří `Dictionary` kolekci a iterates prostřednictvím `foreach` slovníku pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="8d671-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

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

<span data-ttu-id="8d671-184">Chcete-li místo toho použít `Dictionary` inicializátor `BuildDictionary` kolekce `AddToDictionary` k sestavení kolekce, můžete nahradit metody a následující metodou.</span><span class="sxs-lookup"><span data-stu-id="8d671-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

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

<span data-ttu-id="8d671-185">Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodu <xref:System.Collections.Generic.Dictionary%602.Item%2A> a `Dictionary` vlastnost rychle najít položku podle klíče.</span><span class="sxs-lookup"><span data-stu-id="8d671-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="8d671-186">Vlastnost `Item` umožňuje přístup k položce `elements` v kolekci pomocí `elements[symbol]` v C#.</span><span class="sxs-lookup"><span data-stu-id="8d671-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

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

<span data-ttu-id="8d671-187">Následující příklad místo <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> toho používá metodu rychle najít položku podle klíče.</span><span class="sxs-lookup"><span data-stu-id="8d671-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

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

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="8d671-188">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="8d671-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="8d671-189">LINQ (Language-Integrated Query) lze použít pro přístup k kolekcím.</span><span class="sxs-lookup"><span data-stu-id="8d671-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="8d671-190">Linq dotazy poskytují možnosti filtrování, řazení a seskupování.</span><span class="sxs-lookup"><span data-stu-id="8d671-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="8d671-191">Další informace naleznete [v tématu Začínáme s LINQ v C#](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d671-191">For more information, see [Getting Started with LINQ in C#](linq/index.md).</span></span>

<span data-ttu-id="8d671-192">Následující příklad spustí dotaz LINQ `List`proti obecnému .</span><span class="sxs-lookup"><span data-stu-id="8d671-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="8d671-193">Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d671-193">The LINQ query returns a different collection that contains the results.</span></span>

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

## <a name="sorting-a-collection"></a><span data-ttu-id="8d671-194">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-194">Sorting a Collection</span></span>

<span data-ttu-id="8d671-195">Následující příklad ilustruje postup pro řazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d671-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="8d671-196">Příklad seřadí instance `Car` třídy, které <xref:System.Collections.Generic.List%601>jsou uloženy v .</span><span class="sxs-lookup"><span data-stu-id="8d671-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="8d671-197">Třída `Car` implementuje <xref:System.IComparable%601> rozhraní, které <xref:System.IComparable%601.CompareTo%2A> vyžaduje, aby byla metoda implementována.</span><span class="sxs-lookup"><span data-stu-id="8d671-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="8d671-198">Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá pro řazení.</span><span class="sxs-lookup"><span data-stu-id="8d671-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="8d671-199">Kód napsaný uživatelem v metodě `CompareTo` vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem.</span><span class="sxs-lookup"><span data-stu-id="8d671-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="8d671-200">Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt, a nula, pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="8d671-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="8d671-201">To umožňuje definovat v kódu kritéria pro větší než, menší než a rovné.</span><span class="sxs-lookup"><span data-stu-id="8d671-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="8d671-202">V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam.</span><span class="sxs-lookup"><span data-stu-id="8d671-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="8d671-203">Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> způsobí, `CompareTo` že metoda má `Car` být volána automaticky pro objekty v `List`.</span><span class="sxs-lookup"><span data-stu-id="8d671-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

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

## <a name="defining-a-custom-collection"></a><span data-ttu-id="8d671-204">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-204">Defining a Custom Collection</span></span>

<span data-ttu-id="8d671-205">Můžete definovat kolekci <xref:System.Collections.Generic.IEnumerable%601> implementací <xref:System.Collections.IEnumerable> rozhraní nebo.</span><span class="sxs-lookup"><span data-stu-id="8d671-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="8d671-206">I když můžete definovat vlastní kolekci, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, které jsou popsány v [druhy kolekcí](#BKMK_KindsOfCollections) dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8d671-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>

<span data-ttu-id="8d671-207">Následující příklad definuje vlastní třídu `AllColors`kolekce s názvem .</span><span class="sxs-lookup"><span data-stu-id="8d671-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="8d671-208">Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, <xref:System.Collections.IEnumerable.GetEnumerator%2A> které vyžaduje, aby byla metoda implementována.</span><span class="sxs-lookup"><span data-stu-id="8d671-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="8d671-209">Metoda `GetEnumerator` vrátí instanci `ColorEnumerator` třídy.</span><span class="sxs-lookup"><span data-stu-id="8d671-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="8d671-210">`ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které <xref:System.Collections.IEnumerator.Current%2A> vyžaduje, <xref:System.Collections.IEnumerator.MoveNext%2A> aby <xref:System.Collections.IEnumerator.Reset%2A> byla implementována vlastnost, metoda a metoda.</span><span class="sxs-lookup"><span data-stu-id="8d671-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

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

## <a name="iterators"></a><span data-ttu-id="8d671-211">Iterátory</span><span class="sxs-lookup"><span data-stu-id="8d671-211">Iterators</span></span>

<span data-ttu-id="8d671-212">*Iterátor* se používá k provedení vlastní iterace přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="8d671-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="8d671-213">Iterátor může být metoda nebo `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="8d671-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="8d671-214">Iterátor používá yield [return](../../language-reference/keywords/yield.md) prohlášení vrátit každý prvek kolekce jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="8d671-214">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="8d671-215">Volání iterátorpomocí [foreach](../../language-reference/keywords/foreach-in.md) prohlášení.</span><span class="sxs-lookup"><span data-stu-id="8d671-215">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="8d671-216">Každá iterace `foreach` smyčky volá iterátor.</span><span class="sxs-lookup"><span data-stu-id="8d671-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="8d671-217">Když `yield return` je dosaženo příkazu v iterátoru, je vrácen výraz a aktuální umístění v kódu je zachováno.</span><span class="sxs-lookup"><span data-stu-id="8d671-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="8d671-218">Spuštění je restartován z tohoto umístění při příštím volání iterátoru.</span><span class="sxs-lookup"><span data-stu-id="8d671-218">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="8d671-219">Další informace naleznete v tématu [Iterátory (C#)](./iterators.md).</span><span class="sxs-lookup"><span data-stu-id="8d671-219">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="8d671-220">Následující příklad používá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="8d671-220">The following example uses an iterator method.</span></span> <span data-ttu-id="8d671-221">Metoda iterátoru `yield return` má příkaz, který je uvnitř [for](../../language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="8d671-221">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="8d671-222">V `ListEvenNumbers` metodě každá iterace těla příkazu `foreach` vytvoří volání iterátoru `yield return` metody, která pokračuje na další příkaz.</span><span class="sxs-lookup"><span data-stu-id="8d671-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8d671-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d671-223">See also</span></span>

- [<span data-ttu-id="8d671-224">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-224">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="8d671-225">Koncepty programování (C#)</span><span class="sxs-lookup"><span data-stu-id="8d671-225">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="8d671-226">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="8d671-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="8d671-227">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="8d671-227">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="8d671-228">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="8d671-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="8d671-229">Kolekce a datové struktury</span><span class="sxs-lookup"><span data-stu-id="8d671-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="8d671-230">Výběr třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-230">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="8d671-231">Porovnání a řazení v rámci kolekcí</span><span class="sxs-lookup"><span data-stu-id="8d671-231">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="8d671-232">Kdy použít obecné kolekce</span><span class="sxs-lookup"><span data-stu-id="8d671-232">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
