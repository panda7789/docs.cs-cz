---
title: Kolekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 563cef59c0e52d41dcdeaa51b5bc4d7b8f9554f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="collections-visual-basic"></a><span data-ttu-id="acee1-102">Kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acee1-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="acee1-103">Mnoho aplikací budete chtít vytvořit a spravovat skupiny související objekty.</span><span class="sxs-lookup"><span data-stu-id="acee1-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="acee1-104">Existují dva způsoby do objektů skupiny: vytvořením pole objektů a vytvořením kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="acee1-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="acee1-105">Pole jsou velmi užitečné pro vytváření a práci s pevný počet objektů se silným typem.</span><span class="sxs-lookup"><span data-stu-id="acee1-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="acee1-106">Informace o polích najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="acee1-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="acee1-107">Kolekce poskytují flexibilnější způsob, jak pracovat s skupiny objektů.</span><span class="sxs-lookup"><span data-stu-id="acee1-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="acee1-108">Na rozdíl od pole skupinu objektů, které pracujete s můžete zvýšit nebo snížit dynamicky potřebám změna aplikace.</span><span class="sxs-lookup"><span data-stu-id="acee1-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="acee1-109">Pro některé kolekce můžete přiřadit klíč pro libovolný objekt, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="acee1-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="acee1-110">Kolekce je třída, takže instance třídy musí deklarovat, než budete moct přidat do této kolekce elementů.</span><span class="sxs-lookup"><span data-stu-id="acee1-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="acee1-111">Pokud kolekce obsahuje prvky pouze jeden datový typ, můžete použít jednu z tříd ve <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="acee1-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="acee1-112">Obecné kolekce vynucuje bezpečnost typů tak, aby žádný datový typ lze přidat do ní.</span><span class="sxs-lookup"><span data-stu-id="acee1-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="acee1-113">Při načítání element z obecnou kolekci, není nutné určit její datový typ nebo je převeďte.</span><span class="sxs-lookup"><span data-stu-id="acee1-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acee1-114">Příklady v tomto tématu, zahrnují [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro příkazy `System.Collections.Generic` a `System.Linq` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="acee1-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="acee1-115">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="acee1-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="acee1-116">Pomocí jednoduchých kolekcí</span><span class="sxs-lookup"><span data-stu-id="acee1-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="acee1-117">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="acee1-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="acee1-118">System.Collections.Generic – třídy</span><span class="sxs-lookup"><span data-stu-id="acee1-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="acee1-119">System.Collections.Concurrent třídy</span><span class="sxs-lookup"><span data-stu-id="acee1-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="acee1-120">System.Collections – třídy</span><span class="sxs-lookup"><span data-stu-id="acee1-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="acee1-121">Třída Collection v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acee1-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="acee1-122">Implementace kolekci dvojic klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="acee1-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="acee1-123">Pro přístup k kolekci pomocí LINQ</span><span class="sxs-lookup"><span data-stu-id="acee1-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="acee1-124">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="acee1-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="acee1-125">Definování vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="acee1-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="acee1-126">Iterátory</span><span class="sxs-lookup"><span data-stu-id="acee1-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="acee1-127">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="acee1-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="acee1-128">Příklady v této části použijte Obecné <xref:System.Collections.Generic.List%601> třídy, která umožňuje pracovat s silného typu seznamu objektů.</span><span class="sxs-lookup"><span data-stu-id="acee1-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="acee1-129">Následující příklad vytvoří seznam řetězců a pak iteruje řetězce pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="acee1-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="acee1-130">Pokud obsah kolekce jsou známy předem, můžete použít *inicializátoru kolekce* k chybě při inicializaci kolekce.</span><span class="sxs-lookup"><span data-stu-id="acee1-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="acee1-131">Další informace najdete v tématu [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="acee1-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="acee1-132">Následující příklad je stejný jako předchozí příklad, s výjimkou inicializátoru kolekce se používá k přidání prvků do kolekce.</span><span class="sxs-lookup"><span data-stu-id="acee1-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="acee1-133">Můžete použít [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz místo `For Each` příkaz k iteraci v rámci kolekce.</span><span class="sxs-lookup"><span data-stu-id="acee1-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="acee1-134">Můžete dosáhnout díky přístupu k elementy v kolekci podle umístění indexu.</span><span class="sxs-lookup"><span data-stu-id="acee1-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="acee1-135">Index elementů začíná na 0 a končí na počet elementu minus 1.</span><span class="sxs-lookup"><span data-stu-id="acee1-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="acee1-136">V následujícím příkladu prochází prvků kolekce pomocí `For…Next` místo `For Each`.</span><span class="sxs-lookup"><span data-stu-id="acee1-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="acee1-137">Následující příklad odebere element z kolekce zadáním objekt, který chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="acee1-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="acee1-138">Následující příklad odebere seznam obecné elementy.</span><span class="sxs-lookup"><span data-stu-id="acee1-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="acee1-139">Místo `For Each` příkaz, [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) se použije příkaz, který iteruje v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="acee1-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="acee1-140">Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebrané element s nižší hodnotou indexu.</span><span class="sxs-lookup"><span data-stu-id="acee1-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="acee1-141">Pro typ elementů v <xref:System.Collections.Generic.List%601>, je možné definovat také vlastní třídu.</span><span class="sxs-lookup"><span data-stu-id="acee1-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="acee1-142">V následujícím příkladu `Galaxy` třídu, která je používána <xref:System.Collections.Generic.List%601> je definována v kódu.</span><span class="sxs-lookup"><span data-stu-id="acee1-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="acee1-143">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="acee1-143">Kinds of Collections</span></span>   
 <span data-ttu-id="acee1-144">Mnoho běžných kolekcí jsou poskytovány rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="acee1-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="acee1-145">Každý typ kolekce je určená pro konkrétní účel.</span><span class="sxs-lookup"><span data-stu-id="acee1-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="acee1-146">V této části jsou popsány některé běžné třídy kolekce:</span><span class="sxs-lookup"><span data-stu-id="acee1-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="acee1-147"><xref:System.Collections.Generic> Třídy</span><span class="sxs-lookup"><span data-stu-id="acee1-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="acee1-148"><xref:System.Collections.Concurrent> Třídy</span><span class="sxs-lookup"><span data-stu-id="acee1-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="acee1-149"><xref:System.Collections> Třídy</span><span class="sxs-lookup"><span data-stu-id="acee1-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="acee1-150">Visual Basic `Collection` – třída</span><span class="sxs-lookup"><span data-stu-id="acee1-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="acee1-151">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="acee1-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="acee1-152">Můžete vytvořit obecnou kolekci pomocí jedné z třídy v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="acee1-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="acee1-153">Obecné kolekce je užitečné, když každá položka v kolekci má stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="acee1-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="acee1-154">Obecné kolekce vynucuje silného typování tím, že se pouze k požadovaným datům typ, který má být přidán.</span><span class="sxs-lookup"><span data-stu-id="acee1-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="acee1-155">Následující tabulka uvádí některé často používané třídy <xref:System.Collections.Generic?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="acee1-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="acee1-156">Třída</span><span class="sxs-lookup"><span data-stu-id="acee1-156">Class</span></span>|<span data-ttu-id="acee1-157">Popis</span><span class="sxs-lookup"><span data-stu-id="acee1-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="acee1-158">Představuje kolekci páry klíč/hodnota, která jsou uspořádána podle klíče.</span><span class="sxs-lookup"><span data-stu-id="acee1-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="acee1-159">Reprezentuje seznam objektů, kterým lze přistupovat pomocí indexu.</span><span class="sxs-lookup"><span data-stu-id="acee1-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="acee1-160">Poskytuje metody pro vyhledávání, řazení a upravit seznamy.</span><span class="sxs-lookup"><span data-stu-id="acee1-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="acee1-161">Představuje první in, out (FIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="acee1-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="acee1-162">Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="acee1-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="acee1-163">Představuje poslední in, out (LIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="acee1-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="acee1-164">Další informace najdete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md), a <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="acee1-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="acee1-165">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="acee1-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="acee1-166">V rozhraní .NET Framework 4 nebo novější, kolekce v <xref:System.Collections.Concurrent> obor názvů poskytují efektivní operace vláken pro přístup k položkám kolekce z více vláken.</span><span class="sxs-lookup"><span data-stu-id="acee1-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="acee1-167">Třídy v <xref:System.Collections.Concurrent> místo odpovídající typy v by použít obor názvů <xref:System.Collections.Generic?displayProperty=nameWithType> a <xref:System.Collections?displayProperty=nameWithType> obory názvů vždy, když přistupují více vláken kolekce souběžně.</span><span class="sxs-lookup"><span data-stu-id="acee1-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="acee1-168">Další informace najdete v tématu [kolekce se zabezpečenými vlákny](../../../standard/collections/thread-safe/index.md) a <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="acee1-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="acee1-169">Některé třídy součástí <xref:System.Collections.Concurrent> obor názvů jsou <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, a <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="acee1-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="acee1-170">System.Collections – třídy</span><span class="sxs-lookup"><span data-stu-id="acee1-170">System.Collections Classes</span></span>    
 <span data-ttu-id="acee1-171">Třídy v <xref:System.Collections?displayProperty=nameWithType> obor názvů neukládají prvky s konkrétním typem objekty, ale jako objekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="acee1-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="acee1-172">Kdykoli je to možné, měli byste použít obecné kolekce z <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> obor názvů místo starší verze typů v `System.Collections` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="acee1-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="acee1-173">Následující tabulka uvádí některé často používaných tříd v `System.Collections` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="acee1-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="acee1-174">Třída</span><span class="sxs-lookup"><span data-stu-id="acee1-174">Class</span></span>|<span data-ttu-id="acee1-175">Popis</span><span class="sxs-lookup"><span data-stu-id="acee1-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="acee1-176">Představuje požadované pole objektů, jejichž velikost se dynamicky mění jako.</span><span class="sxs-lookup"><span data-stu-id="acee1-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="acee1-177">Představuje kolekci páry klíč/hodnota, která jsou uspořádána podle hodnota hash klíče.</span><span class="sxs-lookup"><span data-stu-id="acee1-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="acee1-178">Představuje první in, out (FIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="acee1-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="acee1-179">Představuje poslední in, out (LIFO) první kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="acee1-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="acee1-180"><xref:System.Collections.Specialized> Obor názvů obsahuje třídy specializované a silného typu kolekce, jako je například kolekce pouze pro řetězce a -list a hybridní slovníky.</span><span class="sxs-lookup"><span data-stu-id="acee1-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="acee1-181">Třída Collection v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acee1-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="acee1-182">Můžete použít Visual Basicu <xref:Microsoft.VisualBasic.Collection> třídy pro přístup k kolekce položek pomocí číselný index nebo `String` klíč.</span><span class="sxs-lookup"><span data-stu-id="acee1-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="acee1-183">Položky můžete přidat do objektu kolekce s nebo bez zadávání klíče.</span><span class="sxs-lookup"><span data-stu-id="acee1-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="acee1-184">Pokud chcete přidat položku bez klíče, musíte použít jeho číselný index k přístupu.</span><span class="sxs-lookup"><span data-stu-id="acee1-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="acee1-185">Visual Basic `Collection` třída ukládá všechny jeho prvky jako typ `Object`, takže můžete přidat položku jakéhokoli datového typu.</span><span class="sxs-lookup"><span data-stu-id="acee1-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="acee1-186">Neexistuje žádné zajistí ochranu proti přidávané nevhodných datové typy.</span><span class="sxs-lookup"><span data-stu-id="acee1-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="acee1-187">Při použití Visual Basicu `Collection` třída, první položky v kolekci má index 1.</span><span class="sxs-lookup"><span data-stu-id="acee1-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="acee1-188">To se liší od tříd rozhraní .NET Framework kolekce, pro které je počáteční index 0.</span><span class="sxs-lookup"><span data-stu-id="acee1-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="acee1-189">Kdykoli je to možné, měli byste použít obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> obor názvů místo Visual Basicu `Collection` třídy.</span><span class="sxs-lookup"><span data-stu-id="acee1-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="acee1-190">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="acee1-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="acee1-191">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="acee1-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="acee1-192"><xref:System.Collections.Generic.Dictionary%602> Obecnou kolekci umožňuje přístup k elementů v kolekci pomocí klíče jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="acee1-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="acee1-193">Každý přidání do slovníku se skládá z hodnotu a jeho přidružený klíč.</span><span class="sxs-lookup"><span data-stu-id="acee1-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="acee1-194">Načítání hodnoty pomocí jeho klíče je rychlé, protože `Dictionary` třída je implementovaný jako zatřiďovací tabulku.</span><span class="sxs-lookup"><span data-stu-id="acee1-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="acee1-195">Následující příklad vytvoří `Dictionary` kolekce a iteruje ve slovníku pomocí `For Each` příkaz.</span><span class="sxs-lookup"><span data-stu-id="acee1-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
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
  
 <span data-ttu-id="acee1-196">Místo toho použít k sestavení inicializátoru kolekce `Dictionary` kolekce, můžete nahradit `BuildDictionary` a `AddToDictionary` metody s následující metodu.</span><span class="sxs-lookup"><span data-stu-id="acee1-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="acee1-197">Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metoda a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` rychle najít položku podle klíče.</span><span class="sxs-lookup"><span data-stu-id="acee1-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="acee1-198">`Item` Vlastnost umožňuje přístup k položce v `elements` kolekce pomocí `elements(symbol)` kód v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="acee1-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
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
  
 <span data-ttu-id="acee1-199">Následující příklad používá místo toho <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda rychle najít položka podle klíče.</span><span class="sxs-lookup"><span data-stu-id="acee1-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="acee1-200">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="acee1-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="acee1-201">LINQ (Language-Integrated Query) slouží pro přístup k kolekce.</span><span class="sxs-lookup"><span data-stu-id="acee1-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="acee1-202">Dotazy LINQ poskytují filtrování, řazení a seskupování schopností.</span><span class="sxs-lookup"><span data-stu-id="acee1-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="acee1-203">Další informace najdete v tématu [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="acee1-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="acee1-204">Následující příklad spouští dotaz LINQ obecný `List`.</span><span class="sxs-lookup"><span data-stu-id="acee1-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="acee1-205">Dotaz LINQ vrátí do jiné kolekce, který obsahuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="acee1-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="acee1-206">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="acee1-206">Sorting a Collection</span></span>  
 <span data-ttu-id="acee1-207">Následující příklad ukazuje postup pro řazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="acee1-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="acee1-208">V příkladu seřadí instance `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="acee1-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="acee1-209">`Car` Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="acee1-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="acee1-210">Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda umožňuje jedno porovnání, který se používá pro řazení.</span><span class="sxs-lookup"><span data-stu-id="acee1-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="acee1-211">Uživatel zapsat kód v `CompareTo` metoda vrátí hodnotu pro každou porovnání aktuální objekt s jiným objektem.</span><span class="sxs-lookup"><span data-stu-id="acee1-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="acee1-212">Hodnota vrácená je menší než nula. Pokud je aktuální objekt menší než druhý objekt, větší než nula. Pokud se aktuální objekt větší než druhý objekt a nula. Pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="acee1-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="acee1-213">To umožňuje definovat kritéria pro větší než je menší než v kódu a rovnat.</span><span class="sxs-lookup"><span data-stu-id="acee1-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="acee1-214">V `ListCars` metody `cars.Sort()` příkaz Seřadí seznam.</span><span class="sxs-lookup"><span data-stu-id="acee1-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="acee1-215">Volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda má být automaticky volána pro `Car` objekty v `List`.</span><span class="sxs-lookup"><span data-stu-id="acee1-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="acee1-216">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="acee1-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="acee1-217">Kolekce můžete definovat implementací <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="acee1-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="acee1-218">Další informace najdete v tématu [vytváření výčtu kolekce](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="acee1-218">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="acee1-219">I když můžete definovat vlastní kolekce, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, která jsou popsaná v [typy kolekcí](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="acee1-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="acee1-220">Následující příklad definuje třídu vlastní kolekci s názvem `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="acee1-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="acee1-221">Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="acee1-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="acee1-222">`GetEnumerator` Metoda vrací instanci třídy `ColorEnumerator` třídy.</span><span class="sxs-lookup"><span data-stu-id="acee1-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="acee1-223">`ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerator.Current%2A> vlastnost <xref:System.Collections.IEnumerator.MoveNext%2A> metody a <xref:System.Collections.IEnumerator.Reset%2A> být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="acee1-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="acee1-224">Iterátory</span><span class="sxs-lookup"><span data-stu-id="acee1-224">Iterators</span></span>  
 <span data-ttu-id="acee1-225">*Iterator* se používá k provedení vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="acee1-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="acee1-226">Iterace může být metodou nebo `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="acee1-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="acee1-227">Používá iterovat [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý prvek kolekce, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="acee1-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="acee1-228">Volání iterovat pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="acee1-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="acee1-229">Každé iteraci `For Each` volá iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="acee1-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="acee1-230">Když `Yield` příkaz je dosaženo v iteraci, je vrácen výraz a se uchovávají aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="acee1-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="acee1-231">Provádění restartování z tohoto umístění příštím iteraci je volána.</span><span class="sxs-lookup"><span data-stu-id="acee1-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="acee1-232">Další informace najdete v tématu [iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="acee1-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="acee1-233">Následující příklad používá metodu iterator.</span><span class="sxs-lookup"><span data-stu-id="acee1-233">The following example uses an iterator method.</span></span> <span data-ttu-id="acee1-234">Metoda iterator má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="acee1-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="acee1-235">V `ListEvenNumbers` metoda, každé iteraci `For Each` těla příkazu vytvoří volání metody iterator, která bude pokračovat na další `Yield` příkaz.</span><span class="sxs-lookup"><span data-stu-id="acee1-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acee1-236">Viz také</span><span class="sxs-lookup"><span data-stu-id="acee1-236">See Also</span></span>  
 [<span data-ttu-id="acee1-237">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="acee1-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="acee1-238">Programování konceptů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acee1-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="acee1-239">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="acee1-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="acee1-240">LINQ na objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acee1-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="acee1-241">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="acee1-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="acee1-242">Kolekce a datové struktury</span><span class="sxs-lookup"><span data-stu-id="acee1-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="acee1-243">Vytváření a manipulace s kolekcí</span><span class="sxs-lookup"><span data-stu-id="acee1-243">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="acee1-244">Výběr třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="acee1-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="acee1-245">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="acee1-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="acee1-246">Kdy použít generické kolekce</span><span class="sxs-lookup"><span data-stu-id="acee1-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
