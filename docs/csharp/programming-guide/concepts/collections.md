---
title: Kolekce (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 7400d4eee4df99cb1e255e428f83028fddf481f4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
---
# <a name="collections-c"></a><span data-ttu-id="67660-102">Kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="67660-102">Collections (C#)</span></span>
<span data-ttu-id="67660-103">Mnoho aplikací budete chtít vytvořit a spravovat skupiny související objekty.</span><span class="sxs-lookup"><span data-stu-id="67660-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="67660-104">Existují dva způsoby do objektů skupiny: vytvořením pole objektů a vytvořením kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="67660-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="67660-105">Pole jsou velmi užitečné pro vytváření a práci s pevný počet objektů se silným typem.</span><span class="sxs-lookup"><span data-stu-id="67660-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="67660-106">Informace o polích najdete v tématu [pole](../../../csharp/programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="67660-106">For information about arrays, see [Arrays](../../../csharp/programming-guide/arrays/index.md).</span></span>  
  
 <span data-ttu-id="67660-107">Kolekce poskytují flexibilnější způsob, jak pracovat s skupiny objektů.</span><span class="sxs-lookup"><span data-stu-id="67660-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="67660-108">Na rozdíl od pole skupinu objektů, které pracujete s můžete zvýšit nebo snížit dynamicky potřebám změna aplikace.</span><span class="sxs-lookup"><span data-stu-id="67660-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="67660-109">Pro některé kolekce můžete přiřadit klíč pro libovolný objekt, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="67660-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="67660-110">Kolekce je třída, takže instance třídy musí deklarovat, než budete moct přidat do této kolekce elementů.</span><span class="sxs-lookup"><span data-stu-id="67660-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="67660-111">Pokud kolekce obsahuje prvky pouze jeden datový typ, můžete použít jednu z tříd ve <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="67660-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="67660-112">Obecné kolekce vynucuje bezpečnost typů tak, aby žádný datový typ lze přidat do ní.</span><span class="sxs-lookup"><span data-stu-id="67660-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="67660-113">Při načítání element z obecnou kolekci, není nutné určit její datový typ nebo je převeďte.</span><span class="sxs-lookup"><span data-stu-id="67660-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67660-114">Příklady v tomto tématu, zahrnují [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy pro `System.Collections.Generic` a `System.Linq` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="67660-114">For the examples in this topic, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="67660-115">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="67660-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="67660-116">Pomocí jednoduchých kolekcí</span><span class="sxs-lookup"><span data-stu-id="67660-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="67660-117">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="67660-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="67660-118">System.Collections.Generic – třídy</span><span class="sxs-lookup"><span data-stu-id="67660-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="67660-119">System.Collections.Concurrent třídy</span><span class="sxs-lookup"><span data-stu-id="67660-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="67660-120">System.Collections – třídy</span><span class="sxs-lookup"><span data-stu-id="67660-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
-   [<span data-ttu-id="67660-121">Implementace kolekci dvojic klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="67660-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="67660-122">Pro přístup k kolekci pomocí LINQ</span><span class="sxs-lookup"><span data-stu-id="67660-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="67660-123">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-123">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="67660-124">Definování vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="67660-125">Iterátory</span><span class="sxs-lookup"><span data-stu-id="67660-125">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="67660-126">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-126">Using a Simple Collection</span></span>  
 <span data-ttu-id="67660-127">Příklady v této části použijte Obecné <xref:System.Collections.Generic.List%601> třídy, která umožňuje pracovat s silného typu seznamu objektů.</span><span class="sxs-lookup"><span data-stu-id="67660-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="67660-128">Následující příklad vytvoří seznam řetězců a pak iteruje řetězce pomocí nebo [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="67660-128">The following example creates a list of strings and then iterates through the strings by using a or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="67660-129">Pokud obsah kolekce jsou známy předem, můžete použít *inicializátoru kolekce* k chybě při inicializaci kolekce.</span><span class="sxs-lookup"><span data-stu-id="67660-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="67660-130">Další informace najdete v tématu [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="67660-130">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
 <span data-ttu-id="67660-131">Následující příklad je stejný jako předchozí příklad, s výjimkou inicializátoru kolekce se používá k přidání prvků do kolekce.</span><span class="sxs-lookup"><span data-stu-id="67660-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="67660-132">Můžete použít [pro](../../../csharp/language-reference/keywords/for.md) příkaz místo `foreach` příkaz k iteraci v rámci kolekce.</span><span class="sxs-lookup"><span data-stu-id="67660-132">You can use a [for](../../../csharp/language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="67660-133">Můžete dosáhnout díky přístupu k elementy v kolekci podle umístění indexu.</span><span class="sxs-lookup"><span data-stu-id="67660-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="67660-134">Index elementů začíná na 0 a končí na počet elementu minus 1.</span><span class="sxs-lookup"><span data-stu-id="67660-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="67660-135">V následujícím příkladu prochází prvků kolekce pomocí `for` místo `foreach`.</span><span class="sxs-lookup"><span data-stu-id="67660-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>  
  
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
  
 <span data-ttu-id="67660-136">Následující příklad odebere element z kolekce zadáním objekt, který chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="67660-136">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="67660-137">Následující příklad odebere seznam obecné elementy.</span><span class="sxs-lookup"><span data-stu-id="67660-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="67660-138">Místo `foreach` příkaz, [pro](../../../csharp/language-reference/keywords/for.md) se použije příkaz, který iteruje v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="67660-138">Instead of a `foreach` statement, a [for](../../../csharp/language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="67660-139">Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebrané element s nižší hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="67660-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="67660-140">Pro typ elementů v <xref:System.Collections.Generic.List%601>, je možné definovat také vlastní třídu.</span><span class="sxs-lookup"><span data-stu-id="67660-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="67660-141">V následujícím příkladu `Galaxy` třídu, která je používána <xref:System.Collections.Generic.List%601> je definována v kódu.</span><span class="sxs-lookup"><span data-stu-id="67660-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="67660-142">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="67660-142">Kinds of Collections</span></span> 
 <span data-ttu-id="67660-143">Mnoho běžných kolekcí jsou poskytovány rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67660-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="67660-144">Každý typ kolekce je určená pro konkrétní účel.</span><span class="sxs-lookup"><span data-stu-id="67660-144">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="67660-145">V této části jsou popsány některé běžné třídy kolekce:</span><span class="sxs-lookup"><span data-stu-id="67660-145">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="67660-146"><xref:System.Collections.Generic> Třídy</span><span class="sxs-lookup"><span data-stu-id="67660-146"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="67660-147"><xref:System.Collections.Concurrent> Třídy</span><span class="sxs-lookup"><span data-stu-id="67660-147"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="67660-148"><xref:System.Collections> Třídy</span><span class="sxs-lookup"><span data-stu-id="67660-148"><xref:System.Collections> classes</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="67660-149">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="67660-149">System.Collections.Generic Classes</span></span>  
 <span data-ttu-id="67660-150">Můžete vytvořit obecnou kolekci pomocí jedné z třídy v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="67660-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="67660-151">Obecné kolekce je užitečné, když každá položka v kolekci má stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="67660-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="67660-152">Obecné kolekce vynucuje silného typování tím, že se pouze k požadovaným datům typ, který má být přidán.</span><span class="sxs-lookup"><span data-stu-id="67660-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="67660-153">Následující tabulka uvádí některé často používané třídy <xref:System.Collections.Generic?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="67660-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  

|<span data-ttu-id="67660-154">Třída</span><span class="sxs-lookup"><span data-stu-id="67660-154">Class</span></span>|<span data-ttu-id="67660-155">Popis</span><span class="sxs-lookup"><span data-stu-id="67660-155">Description</span></span>| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="67660-156">Představuje kolekci páry klíč/hodnota, která jsou uspořádána podle klíče.</span><span class="sxs-lookup"><span data-stu-id="67660-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="67660-157">Reprezentuje seznam objektů, kterým lze přistupovat pomocí indexu.</span><span class="sxs-lookup"><span data-stu-id="67660-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="67660-158">Poskytuje metody pro vyhledávání, řazení a upravit seznamy.</span><span class="sxs-lookup"><span data-stu-id="67660-158">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="67660-159">Představuje první in, out (FIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="67660-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="67660-160">Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="67660-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="67660-161">Představuje poslední in, out (LIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="67660-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="67660-162">Další informace najdete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md), a <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="67660-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="67660-163">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="67660-163">System.Collections.Concurrent Classes</span></span>  
 <span data-ttu-id="67660-164">V rozhraní .NET Framework 4 nebo novější, kolekce v <xref:System.Collections.Concurrent> obor názvů poskytují efektivní operace vláken pro přístup k položkám kolekce z více vláken.</span><span class="sxs-lookup"><span data-stu-id="67660-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="67660-165">Třídy v <xref:System.Collections.Concurrent> místo odpovídající typy v by použít obor názvů <xref:System.Collections.Generic?displayProperty=nameWithType> a <xref:System.Collections?displayProperty=nameWithType> obory názvů vždy, když přistupují více vláken kolekce souběžně.</span><span class="sxs-lookup"><span data-stu-id="67660-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="67660-166">Další informace najdete v tématu [kolekce se zabezpečenými vlákny](../../../standard/collections/thread-safe/index.md) a <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="67660-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="67660-167">Některé třídy součástí <xref:System.Collections.Concurrent> obor názvů jsou <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, a <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="67660-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="67660-168">System.Collections – třídy</span><span class="sxs-lookup"><span data-stu-id="67660-168">System.Collections Classes</span></span>  
 <span data-ttu-id="67660-169">Třídy v <xref:System.Collections?displayProperty=nameWithType> obor názvů neukládají prvky s konkrétním typem objekty, ale jako objekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="67660-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="67660-170">Kdykoli je to možné, měli byste použít obecné kolekce z <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> obor názvů místo starší verze typů v `System.Collections` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="67660-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="67660-171">Následující tabulka uvádí některé často používaných tříd v `System.Collections` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="67660-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="67660-172">Třída</span><span class="sxs-lookup"><span data-stu-id="67660-172">Class</span></span>|<span data-ttu-id="67660-173">Popis</span><span class="sxs-lookup"><span data-stu-id="67660-173">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="67660-174">Představuje požadované pole objektů, jejichž velikost se dynamicky mění jako.</span><span class="sxs-lookup"><span data-stu-id="67660-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="67660-175">Představuje kolekci páry klíč/hodnota, která jsou uspořádána podle hodnota hash klíče.</span><span class="sxs-lookup"><span data-stu-id="67660-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="67660-176">Představuje první in, out (FIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="67660-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="67660-177">Představuje poslední in, out (LIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="67660-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="67660-178"><xref:System.Collections.Specialized> Obor názvů obsahuje třídy specializované a silného typu kolekce, jako je například kolekce pouze pro řetězce a -list a hybridní slovníky.</span><span class="sxs-lookup"><span data-stu-id="67660-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="67660-179">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="67660-179">Implementing a Collection of Key/Value Pairs</span></span>  
 <span data-ttu-id="67660-180"><xref:System.Collections.Generic.Dictionary%602> Obecnou kolekci umožňuje přístup k elementů v kolekci pomocí klíče jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="67660-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="67660-181">Každý přidání do slovníku se skládá z hodnotu a jeho přidružený klíč.</span><span class="sxs-lookup"><span data-stu-id="67660-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="67660-182">Načítání hodnoty pomocí jeho klíče je rychlé, protože `Dictionary` třída je implementovaný jako zatřiďovací tabulku.</span><span class="sxs-lookup"><span data-stu-id="67660-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="67660-183">Následující příklad vytvoří `Dictionary` kolekce a iteruje ve slovníku pomocí `foreach` příkaz.</span><span class="sxs-lookup"><span data-stu-id="67660-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="67660-184">Místo toho použít k sestavení inicializátoru kolekce `Dictionary` kolekce, můžete nahradit `BuildDictionary` a `AddToDictionary` metody s následující metodu.</span><span class="sxs-lookup"><span data-stu-id="67660-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="67660-185">Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metoda a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` rychle najít položku podle klíče.</span><span class="sxs-lookup"><span data-stu-id="67660-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="67660-186">`Item` Vlastnost umožňuje přístup k položce v `elements` kolekce pomocí `elements[symbol]` v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="67660-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>  
  
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
  
 <span data-ttu-id="67660-187">Následující příklad používá místo toho <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda rychle najít položka podle klíče.</span><span class="sxs-lookup"><span data-stu-id="67660-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="67660-188">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="67660-188">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="67660-189">LINQ (Language-Integrated Query) slouží pro přístup k kolekce.</span><span class="sxs-lookup"><span data-stu-id="67660-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="67660-190">Dotazy LINQ poskytují filtrování, řazení a seskupování schopností.</span><span class="sxs-lookup"><span data-stu-id="67660-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="67660-191">Další informace najdete v tématu [Začínáme s dotazy LINQ v jazyku C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="67660-191">For more information, see  [Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="67660-192">Následující příklad spouští dotaz LINQ obecný `List`.</span><span class="sxs-lookup"><span data-stu-id="67660-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="67660-193">Dotaz LINQ vrátí do jiné kolekce, který obsahuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="67660-193">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="67660-194">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-194">Sorting a Collection</span></span>  
 <span data-ttu-id="67660-195">Následující příklad ukazuje postup pro řazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="67660-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="67660-196">V příkladu seřadí instance `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="67660-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="67660-197">`Car` Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="67660-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="67660-198">Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda umožňuje jedno porovnání, který se používá pro řazení.</span><span class="sxs-lookup"><span data-stu-id="67660-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="67660-199">Uživatel zapsat kód v `CompareTo` metoda vrátí hodnotu pro každou porovnání aktuální objekt s jiným objektem.</span><span class="sxs-lookup"><span data-stu-id="67660-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="67660-200">Hodnota vrácená je menší než nula. Pokud je aktuální objekt menší než druhý objekt, větší než nula. Pokud se aktuální objekt větší než druhý objekt a nula. Pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="67660-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="67660-201">To umožňuje definovat kritéria pro větší než je menší než v kódu a rovnat.</span><span class="sxs-lookup"><span data-stu-id="67660-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="67660-202">V `ListCars` metody `cars.Sort()` příkaz Seřadí seznam.</span><span class="sxs-lookup"><span data-stu-id="67660-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="67660-203">Volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda má být automaticky volána pro `Car` objekty v `List`.</span><span class="sxs-lookup"><span data-stu-id="67660-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="67660-204">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-204">Defining a Custom Collection</span></span>  
 <span data-ttu-id="67660-205">Kolekce můžete definovat implementací <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67660-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>  
  
 <span data-ttu-id="67660-206">I když můžete definovat vlastní kolekce, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, která jsou popsaná v [typy kolekcí](#BKMK_KindsOfCollections) výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="67660-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="67660-207">Následující příklad definuje třídu vlastní kolekci s názvem `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="67660-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="67660-208">Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="67660-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="67660-209">`GetEnumerator` Metoda vrací instanci třídy `ColorEnumerator` třídy.</span><span class="sxs-lookup"><span data-stu-id="67660-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="67660-210">`ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerator.Current%2A> vlastnost <xref:System.Collections.IEnumerator.MoveNext%2A> metody a <xref:System.Collections.IEnumerator.Reset%2A> být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="67660-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="67660-211">Iterátory</span><span class="sxs-lookup"><span data-stu-id="67660-211">Iterators</span></span>  
 <span data-ttu-id="67660-212">*Iterator* se používá k provedení vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="67660-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="67660-213">Iterace může být metodou nebo `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="67660-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="67660-214">Používá iterovat [yield vrátit](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit každý prvek kolekce, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="67660-214">An iterator uses a [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="67660-215">Volání iterovat pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="67660-215">You call an iterator by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="67660-216">Každé iteraci `foreach` volá iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="67660-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="67660-217">Když `yield return` příkaz je dosaženo v iteraci, je vrácen výraz a se uchovávají aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="67660-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="67660-218">Provádění restartování z tohoto umístění příštím iteraci je volána.</span><span class="sxs-lookup"><span data-stu-id="67660-218">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="67660-219">Další informace najdete v tématu [iterátory (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="67660-219">For more information, see [Iterators (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="67660-220">Následující příklad používá metodu iterator.</span><span class="sxs-lookup"><span data-stu-id="67660-220">The following example uses an iterator method.</span></span> <span data-ttu-id="67660-221">Metoda iterator má `yield return` příkaz, který je uvnitř [pro](../../../csharp/language-reference/keywords/for.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="67660-221">The iterator method has a `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="67660-222">V `ListEvenNumbers` metoda, každé iteraci `foreach` těla příkazu vytvoří volání metody iterator, která bude pokračovat na další `yield return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="67660-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67660-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="67660-223">See Also</span></span>  
 [<span data-ttu-id="67660-224">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-224">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="67660-225">Programování konceptů (C#)</span><span class="sxs-lookup"><span data-stu-id="67660-225">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)  
 [<span data-ttu-id="67660-226">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="67660-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="67660-227">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="67660-227">LINQ to Objects (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="67660-228">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="67660-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="67660-229">Kolekce a datové struktury</span><span class="sxs-lookup"><span data-stu-id="67660-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="67660-230">Vytváření a manipulace s kolekcí</span><span class="sxs-lookup"><span data-stu-id="67660-230">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="67660-231">Výběr třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="67660-232">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="67660-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="67660-233">Kdy použít generické kolekce</span><span class="sxs-lookup"><span data-stu-id="67660-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
