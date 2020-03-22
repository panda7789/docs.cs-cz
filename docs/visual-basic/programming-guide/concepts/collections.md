---
title: Kolekce
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: ba16d04e781bcf69356b1f603d92e104816a0860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400825"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="0a484-102">Kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a484-102">Collections (Visual Basic)</span></span>

<span data-ttu-id="0a484-103">Pro mnoho aplikací chcete vytvořit a spravovat skupiny souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="0a484-104">Existují dva způsoby seskupení objektů: vytvořením polí objektů a vytvořením kolekcí objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="0a484-105">Pole jsou nejužitečnější pro vytváření a práci s pevným počtem objektů silného typu.</span><span class="sxs-lookup"><span data-stu-id="0a484-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="0a484-106">Informace o polích naleznete v [tématu Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="0a484-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="0a484-107">Kolekce poskytují flexibilnější způsob práce se skupinami objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="0a484-108">Na rozdíl od polí může skupina objektů, se kterými pracujete, dynamicky růst a zmenšovat podle potřeby aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a484-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="0a484-109">Pro některé kolekce můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="0a484-110">Kolekce je třída, takže je nutné deklarovat instanci třídy před přidáním prvků do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="0a484-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="0a484-111">Pokud vaše kolekce obsahuje prvky pouze jednoho datového typu, <xref:System.Collections.Generic?displayProperty=nameWithType> můžete použít jednu z tříd v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0a484-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="0a484-112">Obecná kolekce vynucuje bezpečnost typů tak, aby do ní nebylo možné přidat žádný jiný datový typ.</span><span class="sxs-lookup"><span data-stu-id="0a484-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="0a484-113">Při načtení prvku z obecné kolekce, není nutné určit jeho datový typ nebo převést.</span><span class="sxs-lookup"><span data-stu-id="0a484-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="0a484-114">Příklady v tomto tématu, zahrnout [Imports příkazy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro `System.Collections.Generic` a `System.Linq` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="0a484-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="0a484-115">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="0a484-115">Using a Simple Collection</span></span>

<span data-ttu-id="0a484-116">Příklady v této části <xref:System.Collections.Generic.List%601> používají obecnou třídu, která umožňuje pracovat se silným seznamem objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-116">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="0a484-117">Následující příklad vytvoří seznam řetězců a potom iterates prostřednictvím řetězce pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) prohlášení.</span><span class="sxs-lookup"><span data-stu-id="0a484-117">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>

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

<span data-ttu-id="0a484-118">Pokud obsah kolekce jsou známy předem, můžete použít *inicializační kolekce* inicializovat kolekce.</span><span class="sxs-lookup"><span data-stu-id="0a484-118">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="0a484-119">Další informace naleznete v [tématu Inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="0a484-119">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

<span data-ttu-id="0a484-120">Následující příklad je stejný jako v předchozím příkladu, s výjimkou inicializátor kolekce se používá k přidání prvků do kolekce.</span><span class="sxs-lookup"><span data-stu-id="0a484-120">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

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

<span data-ttu-id="0a484-121">Můžete použít [For... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz namísto příkazu `For Each` iterát prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="0a484-121">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="0a484-122">Toho lze provést přístupem k prvky kolekce podle pozice indexu.</span><span class="sxs-lookup"><span data-stu-id="0a484-122">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="0a484-123">Index prvků začíná na 0 a končí na počet prvků minus 1.</span><span class="sxs-lookup"><span data-stu-id="0a484-123">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="0a484-124">Následující příklad iterates prostřednictvím prvky `For…Next` kolekce `For Each`pomocí místo .</span><span class="sxs-lookup"><span data-stu-id="0a484-124">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="0a484-125">Následující příklad odebere prvek z kolekce zadáním objektu, který má být odebrán.</span><span class="sxs-lookup"><span data-stu-id="0a484-125">The following example removes an element from the collection by specifying the object to remove.</span></span>

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

<span data-ttu-id="0a484-126">Následující příklad odebere prvky z obecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="0a484-126">The following example removes elements from a generic list.</span></span> <span data-ttu-id="0a484-127">Místo prohlášení, `For Each` [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) prohlášení, že iteráty v sestupném pořadí se používá.</span><span class="sxs-lookup"><span data-stu-id="0a484-127">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="0a484-128">Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraný prvek mít nižší hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="0a484-128">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

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

<span data-ttu-id="0a484-129">Pro typ prvků v <xref:System.Collections.Generic.List%601>aplikaci můžete také definovat vlastní třídu.</span><span class="sxs-lookup"><span data-stu-id="0a484-129">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="0a484-130">V následujícím příkladu `Galaxy` je třída, <xref:System.Collections.Generic.List%601> která je používána, definována v kódu.</span><span class="sxs-lookup"><span data-stu-id="0a484-130">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

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

## <a name="kinds-of-collections"></a><span data-ttu-id="0a484-131">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="0a484-131">Kinds of Collections</span></span>

<span data-ttu-id="0a484-132">Mnoho běžných kolekcí poskytuje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a484-132">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="0a484-133">Každý typ kolekce je určen pro konkrétní účel.</span><span class="sxs-lookup"><span data-stu-id="0a484-133">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="0a484-134">Některé běžné třídy kolekce jsou popsány v této části:</span><span class="sxs-lookup"><span data-stu-id="0a484-134">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="0a484-135"><xref:System.Collections.Generic> – třídy</span><span class="sxs-lookup"><span data-stu-id="0a484-135"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="0a484-136"><xref:System.Collections.Concurrent> – třídy</span><span class="sxs-lookup"><span data-stu-id="0a484-136"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="0a484-137"><xref:System.Collections> – třídy</span><span class="sxs-lookup"><span data-stu-id="0a484-137"><xref:System.Collections> classes</span></span>

- <span data-ttu-id="0a484-138">Třída `Collection` Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a484-138">Visual Basic `Collection` class</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="0a484-139">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="0a484-139">System.Collections.Generic Classes</span></span>

<span data-ttu-id="0a484-140">Můžete vytvořit obecnou kolekci pomocí jedné z <xref:System.Collections.Generic> tříd v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0a484-140">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="0a484-141">Obecná kolekce je užitečná, když každá položka v kolekci má stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="0a484-141">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="0a484-142">Obecná kolekce vynucuje silné psaní tím, že umožňuje pouze požadovaný datový typ, který má být přidán.</span><span class="sxs-lookup"><span data-stu-id="0a484-142">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="0a484-143">V následující tabulce jsou uvedeny některé <xref:System.Collections.Generic?displayProperty=nameWithType> často používané třídy oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="0a484-143">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="0a484-144">Třída</span><span class="sxs-lookup"><span data-stu-id="0a484-144">Class</span></span>|<span data-ttu-id="0a484-145">Popis</span><span class="sxs-lookup"><span data-stu-id="0a484-145">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="0a484-146">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-146">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="0a484-147">Představuje seznam objektů, které lze přistupovat index.</span><span class="sxs-lookup"><span data-stu-id="0a484-147">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="0a484-148">Poskytuje metody pro vyhledávání, řazení a úpravy seznamů.</span><span class="sxs-lookup"><span data-stu-id="0a484-148">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="0a484-149">Představuje první in, first out (FIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-149">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="0a484-150">Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="0a484-150">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="0a484-151">Představuje poslední in, first out (LIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-151">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="0a484-152">Další informace naleznete [v tématu Běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a484-152">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="0a484-153">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="0a484-153">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="0a484-154">V rozhraní .NET Framework 4 nebo novější <xref:System.Collections.Concurrent> kolekce v oboru názvů poskytují efektivní operace bezpečné pro přístup k kolekcím z více vláken.</span><span class="sxs-lookup"><span data-stu-id="0a484-154">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="0a484-155">Třídy v <xref:System.Collections.Concurrent> oboru názvů by měly být <xref:System.Collections.Generic?displayProperty=nameWithType> použity namísto odpovídající typy v a <xref:System.Collections?displayProperty=nameWithType> obory názvů vždy více vláken přístup ke kolekci současně.</span><span class="sxs-lookup"><span data-stu-id="0a484-155">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="0a484-156">Další informace naleznete v [tématu Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="0a484-156">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="0a484-157">Některé třídy <xref:System.Collections.Concurrent> zahrnuté <xref:System.Collections.Concurrent.BlockingCollection%601>v <xref:System.Collections.Concurrent.ConcurrentDictionary%602> <xref:System.Collections.Concurrent.ConcurrentQueue%601>oboru <xref:System.Collections.Concurrent.ConcurrentStack%601>názvů jsou , , , a .</span><span class="sxs-lookup"><span data-stu-id="0a484-157">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="0a484-158">Třídy System.Collections</span><span class="sxs-lookup"><span data-stu-id="0a484-158">System.Collections Classes</span></span>

<span data-ttu-id="0a484-159">Třídy v <xref:System.Collections?displayProperty=nameWithType> oboru názvů neukládají prvky jako specificky `Object`zadané objekty, ale jako objekty typu .</span><span class="sxs-lookup"><span data-stu-id="0a484-159">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="0a484-160">Kdykoli je to možné, měli byste <xref:System.Collections.Generic?displayProperty=nameWithType> použít obecné <xref:System.Collections.Concurrent> kolekce v oboru názvů `System.Collections` nebo oboru názvů namísto starších typů v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0a484-160">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="0a484-161">V následující tabulce jsou uvedeny některé `System.Collections` často používané třídy v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="0a484-161">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="0a484-162">Třída</span><span class="sxs-lookup"><span data-stu-id="0a484-162">Class</span></span>|<span data-ttu-id="0a484-163">Popis</span><span class="sxs-lookup"><span data-stu-id="0a484-163">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="0a484-164">Představuje pole objektů, jejichž velikost je dynamicky zvýšena podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="0a484-164">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="0a484-165">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hash klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-165">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="0a484-166">Představuje první in, first out (FIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-166">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="0a484-167">Představuje poslední in, first out (LIFO) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="0a484-167">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="0a484-168">Obor <xref:System.Collections.Specialized> názvů poskytuje specializované a silné typy tříd kolekce, jako jsou například kolekce pouze řetězce a propojené seznam a hybridní slovníky.</span><span class="sxs-lookup"><span data-stu-id="0a484-168">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a><span data-ttu-id="0a484-169">Třída Collection v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a484-169">Visual Basic Collection Class</span></span>

<span data-ttu-id="0a484-170">Třídu Visual Basic <xref:Microsoft.VisualBasic.Collection> můžete použít pro přístup k položce `String` kolekce pomocí číselného indexu nebo klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-170">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="0a484-171">Můžete přidat položky do objektu kolekce buď s nebo bez zadání klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-171">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="0a484-172">Pokud přidáte položku bez klíče, musíte pro přístup k ní použít její číselný index.</span><span class="sxs-lookup"><span data-stu-id="0a484-172">If you add an item without a key, you must use its numeric index to access it.</span></span>

<span data-ttu-id="0a484-173">Visual Basic `Collection` třída ukládá všechny `Object`jeho prvky jako typ , takže můžete přidat položku libovolného datového typu.</span><span class="sxs-lookup"><span data-stu-id="0a484-173">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="0a484-174">Neexistuje žádná ochrana proti přidávání nevhodných datových typů.</span><span class="sxs-lookup"><span data-stu-id="0a484-174">There is no safeguard against inappropriate data types being added.</span></span>

<span data-ttu-id="0a484-175">Při použití visual `Collection` basic třídy první položka v kolekci má index 1.</span><span class="sxs-lookup"><span data-stu-id="0a484-175">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="0a484-176">To se liší od tříd kolekce rozhraní .NET Framework, pro které počáteční index je 0.</span><span class="sxs-lookup"><span data-stu-id="0a484-176">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>

<span data-ttu-id="0a484-177">Kdykoli je to možné, měli byste <xref:System.Collections.Generic?displayProperty=nameWithType> použít obecné <xref:System.Collections.Concurrent> kolekce v oboru `Collection` názvů nebo oboru názvů namísto třídy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0a484-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>

<span data-ttu-id="0a484-178">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="0a484-178">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="0a484-179">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="0a484-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="0a484-180">Obecná <xref:System.Collections.Generic.Dictionary%602> kolekce umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku.</span><span class="sxs-lookup"><span data-stu-id="0a484-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="0a484-181">Každý doplněk do slovníku se skládá z hodnoty a jeho přidruženého klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="0a484-182">Načítání hodnoty pomocí jeho klíče je `Dictionary` rychlé, protože třída je implementována jako tabulka hash.</span><span class="sxs-lookup"><span data-stu-id="0a484-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="0a484-183">Následující příklad vytvoří `Dictionary` kolekci a iterates prostřednictvím `For Each` slovníku pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="0a484-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>

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

<span data-ttu-id="0a484-184">Chcete-li místo toho použít `Dictionary` inicializátor `BuildDictionary` kolekce `AddToDictionary` k sestavení kolekce, můžete nahradit metody a následující metodou.</span><span class="sxs-lookup"><span data-stu-id="0a484-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

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

<span data-ttu-id="0a484-185">Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodu <xref:System.Collections.Generic.Dictionary%602.Item%2A> a `Dictionary` vlastnost rychle najít položku podle klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="0a484-186">Vlastnost `Item` umožňuje přístup k položce `elements` v kolekci pomocí `elements(symbol)` kódu v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0a484-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>

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

<span data-ttu-id="0a484-187">Následující příklad místo <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> toho používá metodu rychle najít položku podle klíče.</span><span class="sxs-lookup"><span data-stu-id="0a484-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

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

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="0a484-188">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="0a484-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="0a484-189">LINQ (Language-Integrated Query) lze použít pro přístup k kolekcím.</span><span class="sxs-lookup"><span data-stu-id="0a484-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="0a484-190">Linq dotazy poskytují možnosti filtrování, řazení a seskupování.</span><span class="sxs-lookup"><span data-stu-id="0a484-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="0a484-191">Další informace naleznete [v tématu Začínáme s LINQ v jazyce Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="0a484-191">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>

<span data-ttu-id="0a484-192">Následující příklad spustí dotaz LINQ `List`proti obecnému .</span><span class="sxs-lookup"><span data-stu-id="0a484-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="0a484-193">Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="0a484-193">The LINQ query returns a different collection that contains the results.</span></span>

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

## <a name="sorting-a-collection"></a><span data-ttu-id="0a484-194">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="0a484-194">Sorting a Collection</span></span>

<span data-ttu-id="0a484-195">Následující příklad ilustruje postup pro řazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="0a484-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="0a484-196">Příklad seřadí instance `Car` třídy, které <xref:System.Collections.Generic.List%601>jsou uloženy v .</span><span class="sxs-lookup"><span data-stu-id="0a484-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="0a484-197">Třída `Car` implementuje <xref:System.IComparable%601> rozhraní, které <xref:System.IComparable%601.CompareTo%2A> vyžaduje, aby byla metoda implementována.</span><span class="sxs-lookup"><span data-stu-id="0a484-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="0a484-198">Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá pro řazení.</span><span class="sxs-lookup"><span data-stu-id="0a484-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="0a484-199">Kód napsaný uživatelem v metodě `CompareTo` vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem.</span><span class="sxs-lookup"><span data-stu-id="0a484-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="0a484-200">Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt, a nula, pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="0a484-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="0a484-201">To umožňuje definovat v kódu kritéria pro větší než, menší než a rovné.</span><span class="sxs-lookup"><span data-stu-id="0a484-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="0a484-202">V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam.</span><span class="sxs-lookup"><span data-stu-id="0a484-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="0a484-203">Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> způsobí, `CompareTo` že metoda má `Car` být volána automaticky pro objekty v `List`.</span><span class="sxs-lookup"><span data-stu-id="0a484-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

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

## <a name="defining-a-custom-collection"></a><span data-ttu-id="0a484-204">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="0a484-204">Defining a Custom Collection</span></span>

<span data-ttu-id="0a484-205">Můžete definovat kolekci <xref:System.Collections.Generic.IEnumerable%601> implementací <xref:System.Collections.IEnumerable> rozhraní nebo.</span><span class="sxs-lookup"><span data-stu-id="0a484-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="0a484-206">Další informace naleznete [v tématu výčet kolekce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0a484-206">For additional information, see [Enumerating a Collection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span></span>

<span data-ttu-id="0a484-207">I když můžete definovat vlastní kolekci, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, které jsou popsány v [druhy kolekcí](#kinds-of-collections) dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0a484-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>

<span data-ttu-id="0a484-208">Následující příklad definuje vlastní třídu `AllColors`kolekce s názvem .</span><span class="sxs-lookup"><span data-stu-id="0a484-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="0a484-209">Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, <xref:System.Collections.IEnumerable.GetEnumerator%2A> které vyžaduje, aby byla metoda implementována.</span><span class="sxs-lookup"><span data-stu-id="0a484-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="0a484-210">Metoda `GetEnumerator` vrátí instanci `ColorEnumerator` třídy.</span><span class="sxs-lookup"><span data-stu-id="0a484-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="0a484-211">`ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které <xref:System.Collections.IEnumerator.Current%2A> vyžaduje, <xref:System.Collections.IEnumerator.MoveNext%2A> aby <xref:System.Collections.IEnumerator.Reset%2A> byla implementována vlastnost, metoda a metoda.</span><span class="sxs-lookup"><span data-stu-id="0a484-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

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

## <a name="iterators"></a><span data-ttu-id="0a484-212">Iterátory</span><span class="sxs-lookup"><span data-stu-id="0a484-212">Iterators</span></span>

<span data-ttu-id="0a484-213">*Iterátor* se používá k provedení vlastní iterace přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="0a484-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="0a484-214">Iterátor může být metoda nebo `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="0a484-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="0a484-215">Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) prohlášení vrátit každý prvek kolekce jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="0a484-215">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="0a484-216">Zavoláte iterátor pomocí [Pro každý ... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) prohlášení.</span><span class="sxs-lookup"><span data-stu-id="0a484-216">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="0a484-217">Každá iterace `For Each` smyčky volá iterátor.</span><span class="sxs-lookup"><span data-stu-id="0a484-217">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="0a484-218">Když `Yield` je dosaženo příkazu v iterátoru, je vrácen výraz a aktuální umístění v kódu je zachováno.</span><span class="sxs-lookup"><span data-stu-id="0a484-218">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="0a484-219">Spuštění je restartován z tohoto umístění při příštím volání iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a484-219">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="0a484-220">Další informace naleznete v tématu [Iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0a484-220">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>

<span data-ttu-id="0a484-221">Následující příklad používá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a484-221">The following example uses an iterator method.</span></span> <span data-ttu-id="0a484-222">Metoda iterátoru `Yield` má příkaz, který je uvnitř [For... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka.</span><span class="sxs-lookup"><span data-stu-id="0a484-222">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="0a484-223">V `ListEvenNumbers` metodě každá iterace těla příkazu `For Each` vytvoří volání iterátoru `Yield` metody, která pokračuje na další příkaz.</span><span class="sxs-lookup"><span data-stu-id="0a484-223">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0a484-224">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a484-224">See also</span></span>

- [<span data-ttu-id="0a484-225">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="0a484-225">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="0a484-226">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a484-226">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="0a484-227">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="0a484-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="0a484-228">LINQ na objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a484-228">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="0a484-229">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="0a484-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="0a484-230">Kolekce a datové struktury</span><span class="sxs-lookup"><span data-stu-id="0a484-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="0a484-231">Výběr třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="0a484-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="0a484-232">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="0a484-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="0a484-233">Kdy použít generické kolekce</span><span class="sxs-lookup"><span data-stu-id="0a484-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
