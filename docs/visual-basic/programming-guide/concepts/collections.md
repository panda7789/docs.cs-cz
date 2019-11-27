---
title: Kolekce
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: ba16d04e781bcf69356b1f603d92e104816a0860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347097"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="495d6-102">Kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="495d6-102">Collections (Visual Basic)</span></span>

<span data-ttu-id="495d6-103">U mnoha aplikací chcete vytvořit a spravovat skupiny souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="495d6-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="495d6-104">Existují dva způsoby, jak seskupit objekty: vytvořením polí objektů a vytvořením kolekcí objektů.</span><span class="sxs-lookup"><span data-stu-id="495d6-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="495d6-105">Pole jsou užitečná pro vytváření a práci s pevným počtem silně typových objektů.</span><span class="sxs-lookup"><span data-stu-id="495d6-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="495d6-106">Informace o polích naleznete v tématu [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="495d6-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="495d6-107">Kolekce poskytují pružnější způsob práce se skupinami objektů.</span><span class="sxs-lookup"><span data-stu-id="495d6-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="495d6-108">Na rozdíl od polí mohou skupiny objektů, se kterými pracujete, dynamicky zvětšovat a zmenšovat podle potřeb změny aplikace.</span><span class="sxs-lookup"><span data-stu-id="495d6-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="495d6-109">U některých kolekcí můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, abyste mohli rychle načíst objekt pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="495d6-110">Kolekce je třída, takže před přidáním prvků do této kolekce je nutné deklarovat instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="495d6-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="495d6-111">Pokud kolekce obsahuje prvky pouze jednoho typu dat, můžete použít jednu ze tříd v oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="495d6-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="495d6-112">Obecná kolekce vynutila bezpečnost typů, takže do ní nelze přidat žádný jiný datový typ.</span><span class="sxs-lookup"><span data-stu-id="495d6-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="495d6-113">Při načítání prvku z obecné kolekce není nutné určit jeho datový typ nebo ho převést.</span><span class="sxs-lookup"><span data-stu-id="495d6-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="495d6-114">Příklady v tomto tématu zahrnují příkazy [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro obory názvů `System.Collections.Generic` a `System.Linq`.</span><span class="sxs-lookup"><span data-stu-id="495d6-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="495d6-115">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="495d6-115">Using a Simple Collection</span></span>

<span data-ttu-id="495d6-116">Příklady v této části používají obecnou <xref:System.Collections.Generic.List%601> třídu, která umožňuje pracovat se seznamem objektů se silným typem.</span><span class="sxs-lookup"><span data-stu-id="495d6-116">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="495d6-117">Následující příklad vytvoří seznam řetězců a pak projde řetězcem pomocí [pro každý z nich... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="495d6-117">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>

```vb
' Create a list of strings.
Dim salmons As New List(Of String)
salmons.Add("chinook")
salmons.Add("coho")
salmons.Add("pink")
salmons.Add("sockeye")

' Iterate through the list.
For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="495d6-118">Pokud je obsah kolekce znám předem, můžete kolekci inicializovat pomocí *inicializátoru kolekce* .</span><span class="sxs-lookup"><span data-stu-id="495d6-118">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="495d6-119">Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="495d6-119">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

<span data-ttu-id="495d6-120">Následující příklad je stejný jako předchozí příklad, s výjimkou, že inicializátor kolekce se používá pro přidání prvků do kolekce.</span><span class="sxs-lookup"><span data-stu-id="495d6-120">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="495d6-121">Můžete použít [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz místo příkazu `For Each` pro iteraci v kolekci.</span><span class="sxs-lookup"><span data-stu-id="495d6-121">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="495d6-122">Toho dosáhnete přístupem k prvkům kolekce na pozici indexu.</span><span class="sxs-lookup"><span data-stu-id="495d6-122">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="495d6-123">Index prvků začíná na 0 a končí v počtu elementů minus 1.</span><span class="sxs-lookup"><span data-stu-id="495d6-123">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="495d6-124">Následující příklad provede iteraci prvků kolekce pomocí `For…Next` místo `For Each`.</span><span class="sxs-lookup"><span data-stu-id="495d6-124">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="495d6-125">Následující příklad odebere prvek z kolekce zadáním objektu, který chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="495d6-125">The following example removes an element from the collection by specifying the object to remove.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

' Remove an element in the list by specifying
' the object.
salmons.Remove("coho")

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook pink sockeye
```

<span data-ttu-id="495d6-126">Následující příklad odstraní prvky z obecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="495d6-126">The following example removes elements from a generic list.</span></span> <span data-ttu-id="495d6-127">Místo příkazu `For Each`, [pro... ](../../../visual-basic/language-reference/statements/for-next-statement.md)Použije se další příkaz, který provede iterace v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="495d6-127">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="495d6-128">Důvodem je, že metoda <xref:System.Collections.Generic.List%601.RemoveAt%2A> způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="495d6-128">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```vb
Dim numbers As New List(Of Integer) From
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}

' Remove odd numbers.
For index As Integer = numbers.Count - 1 To 0 Step -1
    If numbers(index) Mod 2 = 1 Then
        ' Remove the element by specifying
        ' the zero-based index in the list.
        numbers.RemoveAt(index)
    End If
Next

' Iterate through the list.
' A lambda expression is placed in the ForEach method
' of the List(T) object.
numbers.ForEach(
    Sub(number) Console.Write(number & " "))
' Output: 0 2 4 6 8
```

<span data-ttu-id="495d6-129">Pro typ prvků v <xref:System.Collections.Generic.List%601>můžete také definovat vlastní třídu.</span><span class="sxs-lookup"><span data-stu-id="495d6-129">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="495d6-130">V následujícím příkladu je třída `Galaxy` používaná <xref:System.Collections.Generic.List%601> definována v kódu.</span><span class="sxs-lookup"><span data-stu-id="495d6-130">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```vb
Private Sub IterateThroughList()
    Dim theGalaxies As New List(Of Galaxy) From
        {
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}
        }

    For Each theGalaxy In theGalaxies
        With theGalaxy
            Console.WriteLine(.Name & "  " & .MegaLightYears)
        End With
    Next

    ' Output:
    '  Tadpole  400
    '  Pinwheel  25
    '  Milky Way  0
    '  Andromeda  3
End Sub

Public Class Galaxy
    Public Property Name As String
    Public Property MegaLightYears As Integer
End Class
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="495d6-131">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="495d6-131">Kinds of Collections</span></span>

<span data-ttu-id="495d6-132">K dispozici je mnoho běžných kolekcí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="495d6-132">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="495d6-133">Každý typ kolekce je navržený pro konkrétní účel.</span><span class="sxs-lookup"><span data-stu-id="495d6-133">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="495d6-134">Některé společné třídy kolekcí jsou popsány v této části:</span><span class="sxs-lookup"><span data-stu-id="495d6-134">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="495d6-135"><xref:System.Collections.Generic> – třídy</span><span class="sxs-lookup"><span data-stu-id="495d6-135"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="495d6-136"><xref:System.Collections.Concurrent> – třídy</span><span class="sxs-lookup"><span data-stu-id="495d6-136"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="495d6-137"><xref:System.Collections> – třídy</span><span class="sxs-lookup"><span data-stu-id="495d6-137"><xref:System.Collections> classes</span></span>

- <span data-ttu-id="495d6-138">Třída Visual Basic `Collection`</span><span class="sxs-lookup"><span data-stu-id="495d6-138">Visual Basic `Collection` class</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="495d6-139">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="495d6-139">System.Collections.Generic Classes</span></span>

<span data-ttu-id="495d6-140">Můžete vytvořit obecnou kolekci pomocí jedné ze tříd v oboru názvů <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="495d6-140">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="495d6-141">Obecná kolekce je užitečná, pokud má každá položka v kolekci stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="495d6-141">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="495d6-142">Obecná kolekce vynutila silné typování tím, že umožňuje přidat pouze požadovaný datový typ.</span><span class="sxs-lookup"><span data-stu-id="495d6-142">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="495d6-143">V následující tabulce jsou uvedeny některé z často používaných tříd oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="495d6-143">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="495d6-144">Třída</span><span class="sxs-lookup"><span data-stu-id="495d6-144">Class</span></span>|<span data-ttu-id="495d6-145">Popis</span><span class="sxs-lookup"><span data-stu-id="495d6-145">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="495d6-146">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-146">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="495d6-147">Představuje seznam objektů, které mohou být k dispozici v indexu.</span><span class="sxs-lookup"><span data-stu-id="495d6-147">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="495d6-148">Poskytuje metody pro hledání, řazení a úpravy seznamů.</span><span class="sxs-lookup"><span data-stu-id="495d6-148">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="495d6-149">Představuje kolekci objektů first in, First out (FIFO).</span><span class="sxs-lookup"><span data-stu-id="495d6-149">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="495d6-150">Představuje kolekci párů klíč/hodnota, které jsou řazeny podle klíče na základě příslušné implementace <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="495d6-150">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="495d6-151">Představuje kolekci objektů Last in, First out (LIFO).</span><span class="sxs-lookup"><span data-stu-id="495d6-151">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="495d6-152">Další informace naleznete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="495d6-152">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="495d6-153">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="495d6-153">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="495d6-154">V .NET Framework 4 nebo novějších představují kolekce v oboru názvů <xref:System.Collections.Concurrent> efektivní operace bezpečné pro přístup z více vláken pro přístup k položkám kolekce z více vláken.</span><span class="sxs-lookup"><span data-stu-id="495d6-154">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="495d6-155">Třídy v oboru názvů <xref:System.Collections.Concurrent> by měly být použity namísto odpovídajících typů v oborech názvů <xref:System.Collections.Generic?displayProperty=nameWithType> a <xref:System.Collections?displayProperty=nameWithType> vždy, když je souběžně přistupováno k kolekci více vláken.</span><span class="sxs-lookup"><span data-stu-id="495d6-155">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="495d6-156">Další informace najdete v tématu kolekce a <xref:System.Collections.Concurrent>bezpečné pro přístup z [více vláken](../../../standard/collections/thread-safe/index.md) .</span><span class="sxs-lookup"><span data-stu-id="495d6-156">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="495d6-157">Některé třídy, které jsou zahrnuté v oboru názvů <xref:System.Collections.Concurrent>, jsou <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>a <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="495d6-157">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="495d6-158">Třídy System. Collections</span><span class="sxs-lookup"><span data-stu-id="495d6-158">System.Collections Classes</span></span>

<span data-ttu-id="495d6-159">Třídy v oboru názvů <xref:System.Collections?displayProperty=nameWithType> neukládají prvky jako objekty, které jsou specificky typované, ale jako objekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="495d6-159">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="495d6-160">Kdykoli je to možné, měli byste použít obecné kolekce v oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType> nebo obor názvů <xref:System.Collections.Concurrent> namísto starších typů v oboru názvů `System.Collections`.</span><span class="sxs-lookup"><span data-stu-id="495d6-160">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="495d6-161">Následující tabulka uvádí některé často používané třídy v oboru názvů `System.Collections`:</span><span class="sxs-lookup"><span data-stu-id="495d6-161">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="495d6-162">Třída</span><span class="sxs-lookup"><span data-stu-id="495d6-162">Class</span></span>|<span data-ttu-id="495d6-163">Popis</span><span class="sxs-lookup"><span data-stu-id="495d6-163">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="495d6-164">Představuje pole objektů, jejichž velikost se dynamicky zvětšuje podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="495d6-164">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="495d6-165">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hash klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-165">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="495d6-166">Představuje kolekci objektů first in, First out (FIFO).</span><span class="sxs-lookup"><span data-stu-id="495d6-166">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="495d6-167">Představuje kolekci objektů Last in, First out (LIFO).</span><span class="sxs-lookup"><span data-stu-id="495d6-167">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="495d6-168">Obor názvů <xref:System.Collections.Specialized> poskytuje specializované třídy kolekcí se silnými typy, jako jsou jenom řetězcové kolekce a propojené seznamy a hybridní slovníky.</span><span class="sxs-lookup"><span data-stu-id="495d6-168">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a><span data-ttu-id="495d6-169">Třída Collection v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="495d6-169">Visual Basic Collection Class</span></span>

<span data-ttu-id="495d6-170">Třídu Visual Basic <xref:Microsoft.VisualBasic.Collection> můžete použít pro přístup k položce kolekce pomocí číselného indexu nebo `String` klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-170">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="495d6-171">Můžete přidat položky do objektu kolekce buď s nebo bez zadání klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-171">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="495d6-172">Pokud přidáte položku bez klíče, je nutné k ní přistupovat pomocí jejího číselného indexu.</span><span class="sxs-lookup"><span data-stu-id="495d6-172">If you add an item without a key, you must use its numeric index to access it.</span></span>

<span data-ttu-id="495d6-173">Třída Visual Basic `Collection` ukládá všechny své prvky jako typ `Object`, takže můžete přidat položku libovolného datového typu.</span><span class="sxs-lookup"><span data-stu-id="495d6-173">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="495d6-174">Neexistují žádné záruky proti přidávání nevhodných datových typů.</span><span class="sxs-lookup"><span data-stu-id="495d6-174">There is no safeguard against inappropriate data types being added.</span></span>

<span data-ttu-id="495d6-175">Když použijete třídu Visual Basic `Collection`, první položka v kolekci má index 1.</span><span class="sxs-lookup"><span data-stu-id="495d6-175">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="495d6-176">To se liší od tříd kolekce .NET Framework, pro které je počáteční index 0.</span><span class="sxs-lookup"><span data-stu-id="495d6-176">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>

<span data-ttu-id="495d6-177">Kdykoli je to možné, měli byste použít obecné kolekce v oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType> nebo obor názvů <xref:System.Collections.Concurrent> namísto třídy `Collection` Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="495d6-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>

<span data-ttu-id="495d6-178">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="495d6-178">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="495d6-179">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="495d6-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="495d6-180">Obecná kolekce <xref:System.Collections.Generic.Dictionary%602> umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku.</span><span class="sxs-lookup"><span data-stu-id="495d6-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="495d6-181">Každé přidání do slovníku se skládá z hodnoty a jejího přidruženého klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="495d6-182">Načítání hodnoty pomocí klíče je rychlé, protože třída `Dictionary` je implementována jako zatřiďovací tabulka.</span><span class="sxs-lookup"><span data-stu-id="495d6-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="495d6-183">Následující příklad vytvoří kolekci `Dictionary` a provede iteraci pomocí příkazu `For Each`.</span><span class="sxs-lookup"><span data-stu-id="495d6-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>

```vb
Private Sub IterateThroughDictionary()
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    For Each kvp As KeyValuePair(Of String, Element) In elements
        Dim theElement As Element = kvp.Value

        Console.WriteLine("key: " & kvp.Key)
        With theElement
            Console.WriteLine("values: " & .Symbol & " " &
                .Name & " " & .AtomicNumber)
        End With
    Next
End Sub

Private Function BuildDictionary() As Dictionary(Of String, Element)
    Dim elements As New Dictionary(Of String, Element)

    AddToDictionary(elements, "K", "Potassium", 19)
    AddToDictionary(elements, "Ca", "Calcium", 20)
    AddToDictionary(elements, "Sc", "Scandium", 21)
    AddToDictionary(elements, "Ti", "Titanium", 22)

    Return elements
End Function

Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)
    Dim theElement As New Element

    theElement.Symbol = symbol
    theElement.Name = name
    theElement.AtomicNumber = atomicNumber

    elements.Add(Key:=theElement.Symbol, value:=theElement)
End Sub

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<span data-ttu-id="495d6-184">Chcete-li místo toho použít inicializátor kolekce k sestavení kolekce `Dictionary`, můžete nahradit metody `BuildDictionary` a `AddToDictionary` následující metodou.</span><span class="sxs-lookup"><span data-stu-id="495d6-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```vb
Private Function BuildDictionary2() As Dictionary(Of String, Element)
    Return New Dictionary(Of String, Element) From
        {
            {"K", New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {"Ca", New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {"Sc", New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {"Ti", New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function
```

<span data-ttu-id="495d6-185">Následující příklad používá metodu <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> a vlastnost <xref:System.Collections.Generic.Dictionary%602.Item%2A> `Dictionary` pro rychlé vyhledání položky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="495d6-186">Vlastnost `Item` umožňuje přístup k položce v kolekci `elements` pomocí kódu `elements(symbol)` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="495d6-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>

```vb
Private Sub FindInDictionary(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    If elements.ContainsKey(symbol) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Dim theElement = elements(symbol)
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<span data-ttu-id="495d6-187">Následující příklad místo toho používá metodu <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> k rychlému vyhledání položky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="495d6-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```vb
Private Sub FindInDictionary2(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    Dim theElement As Element = Nothing
    If elements.TryGetValue(symbol, theElement) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="495d6-188">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="495d6-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="495d6-189">LINQ (jazykově integrovaný dotaz) lze použít pro přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="495d6-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="495d6-190">Dotazy LINQ poskytují možnosti filtrování, řazení a seskupování.</span><span class="sxs-lookup"><span data-stu-id="495d6-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="495d6-191">Další informace najdete v tématu [Začínáme s LINQ v Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="495d6-191">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>

<span data-ttu-id="495d6-192">Následující příklad spustí dotaz LINQ na obecné `List`.</span><span class="sxs-lookup"><span data-stu-id="495d6-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="495d6-193">Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="495d6-193">The LINQ query returns a different collection that contains the results.</span></span>

```vb
Private Sub ShowLINQ()
    Dim elements As List(Of Element) = BuildList()

    ' LINQ Query.
    Dim subset = From theElement In elements
                  Where theElement.AtomicNumber < 22
                  Order By theElement.Name

    For Each theElement In subset
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)
    Next

    ' Output:
    '  Calcium 20
    '  Potassium 19
    '  Scandium 21
End Sub

Private Function BuildList() As List(Of Element)
    Return New List(Of Element) From
        {
            {New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="495d6-194">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="495d6-194">Sorting a Collection</span></span>

<span data-ttu-id="495d6-195">Následující příklad znázorňuje postup pro řazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="495d6-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="495d6-196">Příklad řadí instance `Car` třídy, které jsou uloženy v <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="495d6-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="495d6-197">Třída `Car` implementuje rozhraní <xref:System.IComparable%601>, které vyžaduje, aby byla metoda <xref:System.IComparable%601.CompareTo%2A> implementovaná.</span><span class="sxs-lookup"><span data-stu-id="495d6-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="495d6-198">Každé volání metody <xref:System.IComparable%601.CompareTo%2A> provede jedno porovnání, které se používá k řazení.</span><span class="sxs-lookup"><span data-stu-id="495d6-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="495d6-199">Uživatelsky psaný kód v metodě `CompareTo` vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem.</span><span class="sxs-lookup"><span data-stu-id="495d6-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="495d6-200">Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula, pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="495d6-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="495d6-201">To umožňuje definovat v kódu kritéria pro větší než, menší než a rovno.</span><span class="sxs-lookup"><span data-stu-id="495d6-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="495d6-202">V metodě `ListCars` seřadí příkaz `cars.Sort()` seznam.</span><span class="sxs-lookup"><span data-stu-id="495d6-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="495d6-203">Toto volání metody <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.List%601> způsobí, že metoda `CompareTo` bude automaticky volána pro objekty `Car` v `List`.</span><span class="sxs-lookup"><span data-stu-id="495d6-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```vb
Public Sub ListCars()

    ' Create some new cars.
    Dim cars As New List(Of Car) From
    {
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}
    }

    ' Sort the cars by color alphabetically, and then by speed
    ' in descending order.
    cars.Sort()

    ' View all of the cars.
    For Each thisCar As Car In cars
        Console.Write(thisCar.Color.PadRight(5) & " ")
        Console.Write(thisCar.Speed.ToString & " ")
        Console.Write(thisCar.Name)
        Console.WriteLine()
    Next

    ' Output:
    '  blue  50 car4
    '  blue  30 car5
    '  blue  20 car1
    '  green 50 car7
    '  green 10 car3
    '  red   60 car6
    '  red   50 car2
End Sub

Public Class Car
    Implements IComparable(Of Car)

    Public Property Name As String
    Public Property Speed As Integer
    Public Property Color As String

    Public Function CompareTo(ByVal other As Car) As Integer _
        Implements System.IComparable(Of Car).CompareTo
        ' A call to this method makes a single comparison that is
        ' used for sorting.

        ' Determine the relative order of the objects being compared.
        ' Sort by color alphabetically, and then by speed in
        ' descending order.

        ' Compare the colors.
        Dim compare As Integer
        compare = String.Compare(Me.Color, other.Color, True)

        ' If the colors are the same, compare the speeds.
        If compare = 0 Then
            compare = Me.Speed.CompareTo(other.Speed)

            ' Use descending order for speed.
            compare = -compare
        End If

        Return compare
    End Function
End Class
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="495d6-204">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="495d6-204">Defining a Custom Collection</span></span>

<span data-ttu-id="495d6-205">Můžete definovat kolekci implementací rozhraní <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="495d6-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="495d6-206">Další informace najdete v tématu [výčet kolekce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="495d6-206">For additional information, see [Enumerating a Collection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span></span>

<span data-ttu-id="495d6-207">I když můžete definovat vlastní kolekci, je obvykle vhodnější použít kolekce, které jsou součástí .NET Framework, které jsou popsány v části [druhy kolekcí](#kinds-of-collections) výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="495d6-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>

<span data-ttu-id="495d6-208">Následující příklad definuje vlastní třídu kolekce s názvem `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="495d6-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="495d6-209">Tato třída implementuje rozhraní <xref:System.Collections.IEnumerable>, které vyžaduje implementaci <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="495d6-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="495d6-210">Metoda `GetEnumerator` vrací instanci `ColorEnumerator` třídy.</span><span class="sxs-lookup"><span data-stu-id="495d6-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="495d6-211">`ColorEnumerator` implementuje rozhraní <xref:System.Collections.IEnumerator>, které vyžaduje, aby byla implementována vlastnost <xref:System.Collections.IEnumerator.Current%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda a <xref:System.Collections.IEnumerator.Reset%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="495d6-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```vb
Public Sub ListColors()
    Dim colors As New AllColors()

    For Each theColor As Color In colors
        Console.Write(theColor.Name & " ")
    Next
    Console.WriteLine()
    ' Output: red blue green
End Sub

' Collection class.
Public Class AllColors
    Implements System.Collections.IEnumerable

    Private _colors() As Color =
    {
        New Color With {.Name = "red"},
        New Color With {.Name = "blue"},
        New Color With {.Name = "green"}
    }

    Public Function GetEnumerator() As System.Collections.IEnumerator _
        Implements System.Collections.IEnumerable.GetEnumerator

        Return New ColorEnumerator(_colors)

        ' Instead of creating a custom enumerator, you could
        ' use the GetEnumerator of the array.
        'Return _colors.GetEnumerator
    End Function

    ' Custom enumerator.
    Private Class ColorEnumerator
        Implements System.Collections.IEnumerator

        Private _colors() As Color
        Private _position As Integer = -1

        Public Sub New(ByVal colors() As Color)
            _colors = colors
        End Sub

        Public ReadOnly Property Current() As Object _
            Implements System.Collections.IEnumerator.Current
            Get
                Return _colors(_position)
            End Get
        End Property

        Public Function MoveNext() As Boolean _
            Implements System.Collections.IEnumerator.MoveNext
            _position += 1
            Return (_position < _colors.Length)
        End Function

        Public Sub Reset() Implements System.Collections.IEnumerator.Reset
            _position = -1
        End Sub
    End Class
End Class

' Element class.
Public Class Color
    Public Property Name As String
End Class
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="495d6-212">Iterátory</span><span class="sxs-lookup"><span data-stu-id="495d6-212">Iterators</span></span>

<span data-ttu-id="495d6-213">*Iterátor* se používá k provedení vlastní iterace v kolekci.</span><span class="sxs-lookup"><span data-stu-id="495d6-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="495d6-214">Iterátor může být metoda nebo přistupující objekt `get`.</span><span class="sxs-lookup"><span data-stu-id="495d6-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="495d6-215">Iterátor používá příkaz [yield](../../../visual-basic/language-reference/statements/yield-statement.md) k vrácení každého prvku kolekce v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="495d6-215">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="495d6-216">Zavoláte iterátor pomocí a [pro každou z nich... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="495d6-216">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="495d6-217">Každá iterace `For Each` smyčky volá iterátor.</span><span class="sxs-lookup"><span data-stu-id="495d6-217">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="495d6-218">Když je v iterátoru dosaženo příkazu `Yield`, je vrácen výraz a aktuální umístění v kódu je uchováno.</span><span class="sxs-lookup"><span data-stu-id="495d6-218">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="495d6-219">Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.</span><span class="sxs-lookup"><span data-stu-id="495d6-219">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="495d6-220">Další informace najdete v tématu [iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="495d6-220">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>

<span data-ttu-id="495d6-221">Následující příklad používá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="495d6-221">The following example uses an iterator method.</span></span> <span data-ttu-id="495d6-222">Metoda iterátoru má příkaz `Yield`, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka</span><span class="sxs-lookup"><span data-stu-id="495d6-222">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="495d6-223">V metodě `ListEvenNumbers` Každá iterace těla příkazu `For Each` vytvoří volání metody iterátoru, která pokračuje k dalšímu příkazu `Yield`.</span><span class="sxs-lookup"><span data-stu-id="495d6-223">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>

```vb
Public Sub ListEvenNumbers()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    Console.WriteLine()
    ' Output: 6 8 10 12 14 16 18
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As IEnumerable(Of Integer)

' Yield even numbers in the range.
    For number = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="see-also"></a><span data-ttu-id="495d6-224">Viz také:</span><span class="sxs-lookup"><span data-stu-id="495d6-224">See also</span></span>

- [<span data-ttu-id="495d6-225">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="495d6-225">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="495d6-226">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="495d6-226">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="495d6-227">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="495d6-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="495d6-228">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="495d6-228">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="495d6-229">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="495d6-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="495d6-230">Kolekce a datové struktury</span><span class="sxs-lookup"><span data-stu-id="495d6-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="495d6-231">Výběr třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="495d6-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="495d6-232">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="495d6-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="495d6-233">Kdy použít generické kolekce</span><span class="sxs-lookup"><span data-stu-id="495d6-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
