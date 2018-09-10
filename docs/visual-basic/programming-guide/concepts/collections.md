---
title: Kolekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 60519de1f580bf1cfa4aa067d4a999b20ea8d54d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210365"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="48895-102">Kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48895-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="48895-103">U mnoha aplikací chcete vytvářet a spravovat skupiny souvisejících objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="48895-104">Existují dva způsoby, jak seskupit objekty: vytvořením polí objektů a vytvořením kolekcí objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="48895-105">Pole jsou zvláště užitečná pro vytváření a práci s pevným počtem silně typovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="48895-106">Informace o polích naleznete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="48895-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="48895-107">Kolekce poskytují pružnější způsob práce se skupinami objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="48895-108">Na rozdíl od pole skupiny objektů, které při práci s můžete zvětšení a zmenšení dynamicky podle potřeb změn aplikace.</span><span class="sxs-lookup"><span data-stu-id="48895-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="48895-109">Pro některé kolekce můžete přiřadit klíč na libovolný objekt, který vložíte do kolekce, takže můžete snadno obnovit objekt pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="48895-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="48895-110">Kolekce je třída, proto je třeba deklarovat instanci třídy, než budete moct přidat prvky do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="48895-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="48895-111">Pokud kolekce obsahuje prvky pouze jednoho datového typu, můžete použít jednu z tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="48895-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="48895-112">Obecná kolekce vynucuje bezpečnost typů tak, aby žádný jiný typ dat můžete do ní přidá.</span><span class="sxs-lookup"><span data-stu-id="48895-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="48895-113">Při načítání elementu z obecné kolekce není nutné zjistit jeho typ dat nebo ji převést.</span><span class="sxs-lookup"><span data-stu-id="48895-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48895-114">Příklady v tomto tématu, zahrnují [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) příkazů `System.Collections.Generic` a `System.Linq` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="48895-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="48895-115">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="48895-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="48895-116">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="48895-117">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="48895-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="48895-118">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="48895-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="48895-119">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="48895-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="48895-120">Třídy System.Collections</span><span class="sxs-lookup"><span data-stu-id="48895-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="48895-121">Třídy kolekce jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48895-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="48895-122">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="48895-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="48895-123">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="48895-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="48895-124">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="48895-125">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="48895-126">Iterátory</span><span class="sxs-lookup"><span data-stu-id="48895-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="48895-127">Používání jednoduché kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="48895-128">Příklady v této části použít obecný <xref:System.Collections.Generic.List%601> třídu, která umožňuje pracovat s výrazným seznamem objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="48895-129">Následující příklad vytvoří seznam řetězců a provede iteraci řetězců pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="48895-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="48895-130">Pokud obsah kolekce znám předem, můžete použít *inicializátor kolekce* pro inicializace kolekce.</span><span class="sxs-lookup"><span data-stu-id="48895-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="48895-131">Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="48895-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="48895-132">Následující příklad je stejný jako předchozí příklad, s výjimkou inicializátoru kolekce je použít k přidání prvků do kolekce.</span><span class="sxs-lookup"><span data-stu-id="48895-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="48895-133">Můžete použít [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz místo `For Each` příkaz pro iteraci prostřednictvím kolekce.</span><span class="sxs-lookup"><span data-stu-id="48895-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="48895-134">Toto dokončíte pomocí přístupu k elementům kolekce pomocí indexu umístění.</span><span class="sxs-lookup"><span data-stu-id="48895-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="48895-135">Index prvků začíná hodnotou 0 a končí počtem prvků mínus 1.</span><span class="sxs-lookup"><span data-stu-id="48895-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="48895-136">Následující příklad provede iteraci prvků kolekce pomocí `For…Next` místo `For Each`.</span><span class="sxs-lookup"><span data-stu-id="48895-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="48895-137">Následující příklad odstraní prvek z kolekce zadáním objektu, který chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="48895-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="48895-138">Následující příklad odebere prvky z obecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="48895-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="48895-139">Místo `For Each` příkaz, [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) se používá s itinerací v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="48895-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="48895-140">Je to proto, <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="48895-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="48895-141">Pro typ prvků v <xref:System.Collections.Generic.List%601>, můžete také definovat své vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="48895-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="48895-142">V následujícím příkladu `Galaxy` třídu, která se používá <xref:System.Collections.Generic.List%601> je definována v kódu.</span><span class="sxs-lookup"><span data-stu-id="48895-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="48895-143">Typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="48895-143">Kinds of Collections</span></span>   
 <span data-ttu-id="48895-144">Mnoho nejběžnějších kolekcí jsou k dispozici v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48895-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="48895-145">Každý typ kolekce je navržená pro určitý účel.</span><span class="sxs-lookup"><span data-stu-id="48895-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="48895-146">V této části jsou popsány některé běžné třídy kolekce:</span><span class="sxs-lookup"><span data-stu-id="48895-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="48895-147"><xref:System.Collections.Generic> Třídy</span><span class="sxs-lookup"><span data-stu-id="48895-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="48895-148"><xref:System.Collections.Concurrent> Třídy</span><span class="sxs-lookup"><span data-stu-id="48895-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="48895-149"><xref:System.Collections> Třídy</span><span class="sxs-lookup"><span data-stu-id="48895-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="48895-150">Visual Basic `Collection` třídy</span><span class="sxs-lookup"><span data-stu-id="48895-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="48895-151">Třídy System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="48895-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="48895-152">Obecnou kolekci můžete vytvořit pomocí jedné ze tříd v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="48895-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="48895-153">Obecná kolekce je užitečná, když má každá položka v kolekci stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="48895-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="48895-154">Obecná kolekce vynucuje silné typování tím, že pouze žádaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="48895-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="48895-155">Následující tabulka uvádí některé často používané třídy <xref:System.Collections.Generic?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="48895-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="48895-156">Třída</span><span class="sxs-lookup"><span data-stu-id="48895-156">Class</span></span>|<span data-ttu-id="48895-157">Popis</span><span class="sxs-lookup"><span data-stu-id="48895-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="48895-158">Představuje kolekci dvojic klíč/hodnota, které jsou uspořádány na základě klíče.</span><span class="sxs-lookup"><span data-stu-id="48895-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="48895-159">Reprezentuje seznam objektů, které lze využívat pomocí indexu.</span><span class="sxs-lookup"><span data-stu-id="48895-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="48895-160">Poskytuje metody pro vyhledávání, řazení a úpravu seznamů.</span><span class="sxs-lookup"><span data-stu-id="48895-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="48895-161">Představuje first-in-first-out (FIFO) kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="48895-162">Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="48895-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="48895-163">Představuje last-in-first-out (LIFO) kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="48895-164">Další informace najdete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md), a <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="48895-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="48895-165">Třídy System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="48895-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="48895-166">V rozhraní .NET Framework 4 nebo novější, kolekce v <xref:System.Collections.Concurrent> obor názvů poskytují efektivní operace bezpečné pro vlákna pro přístup položky kolekce z více vláken.</span><span class="sxs-lookup"><span data-stu-id="48895-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="48895-167">Třídy v <xref:System.Collections.Concurrent> oboru názvů by měl použít namísto odpovídajících typů v <xref:System.Collections.Generic?displayProperty=nameWithType> a <xref:System.Collections?displayProperty=nameWithType> obory názvů pokaždé, když přistupuje více podprocesů kolekci současně.</span><span class="sxs-lookup"><span data-stu-id="48895-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="48895-168">Další informace najdete v tématu [kolekce bezpečné pro vlákna](../../../standard/collections/thread-safe/index.md) a <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="48895-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="48895-169">Některé třídy v <xref:System.Collections.Concurrent> obor názvů jsou <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, a <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="48895-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="48895-170">Třídy System.Collections</span><span class="sxs-lookup"><span data-stu-id="48895-170">System.Collections Classes</span></span>    
 <span data-ttu-id="48895-171">Třídy v <xref:System.Collections?displayProperty=nameWithType> obor názvů neukládají prvky jako objekty s konkrétním typem, ale jako objekty typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="48895-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="48895-172">Kdykoli je to možné, použijte obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> místo třídy zastaralých typů v `System.Collections` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="48895-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="48895-173">Následující tabulka uvádí některé často používané třídy v `System.Collections` obor názvů:</span><span class="sxs-lookup"><span data-stu-id="48895-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="48895-174">Třída</span><span class="sxs-lookup"><span data-stu-id="48895-174">Class</span></span>|<span data-ttu-id="48895-175">Popis</span><span class="sxs-lookup"><span data-stu-id="48895-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="48895-176">Představuje pole objektů, jejichž velikost se dynamicky mění jako povinné.</span><span class="sxs-lookup"><span data-stu-id="48895-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="48895-177">Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hodnoty hash klíče.</span><span class="sxs-lookup"><span data-stu-id="48895-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="48895-178">Představuje first-in-first-out (FIFO) kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="48895-179">Představuje last-in-first-out (LIFO) kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="48895-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="48895-180"><xref:System.Collections.Specialized> Obor názvů obsahuje třídy specializované a typově silné kolekcí, jako je například kolekce pouze pro řetězce a propojené seznamy a hybridní slovníky.</span><span class="sxs-lookup"><span data-stu-id="48895-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="48895-181">Třída Collection v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48895-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="48895-182">Můžete použít Visual Basic <xref:Microsoft.VisualBasic.Collection> třídy pro přístup položky kolekce pomocí numerického indexu nebo `String` klíč.</span><span class="sxs-lookup"><span data-stu-id="48895-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="48895-183">Přidat položky do objektu kolekce s nebo bez udání klíče.</span><span class="sxs-lookup"><span data-stu-id="48895-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="48895-184">Pokud chcete přidat položku bez klíče, musíte použít jeho číselný index k němu přistupovat.</span><span class="sxs-lookup"><span data-stu-id="48895-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="48895-185">Visual Basic `Collection` třída uchovává všechny prvky jako typ `Object`, takže můžete přidat položky libovolného datového typu.</span><span class="sxs-lookup"><span data-stu-id="48895-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="48895-186">Neexistuje žádná ochrana proti přidání typů nevhodných dat.</span><span class="sxs-lookup"><span data-stu-id="48895-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="48895-187">Při použití jazyka Visual Basic `Collection` obsahuje třídy, první položku v kolekci index 1.</span><span class="sxs-lookup"><span data-stu-id="48895-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="48895-188">Tím se liší od kolekcí tříd rozhraní .NET Framework, pro které je počáteční index 0.</span><span class="sxs-lookup"><span data-stu-id="48895-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="48895-189">Kdykoli je to možné, použijte obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> místo jazyka Visual Basic `Collection` třídy.</span><span class="sxs-lookup"><span data-stu-id="48895-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="48895-190">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="48895-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="48895-191">Implementace kolekce párů klíč/hodnota</span><span class="sxs-lookup"><span data-stu-id="48895-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="48895-192"><xref:System.Collections.Generic.Dictionary%602> Obecné kolekce umožňuje přístup k prvkům kolekce pomocí klíče každého prvku.</span><span class="sxs-lookup"><span data-stu-id="48895-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="48895-193">Každé přidání do slovníku se skládá z hodnoty a odpovídajícího klíče.</span><span class="sxs-lookup"><span data-stu-id="48895-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="48895-194">Načítání hodnoty pomocí obsaženého klíče je velmi rychle, protože `Dictionary` třídy je implementovaný jako zatřiďovací tabulku.</span><span class="sxs-lookup"><span data-stu-id="48895-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="48895-195">Následující příklad vytvoří `Dictionary` kolekce a iteruje ve slovníku s využitím `For Each` příkazu.</span><span class="sxs-lookup"><span data-stu-id="48895-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
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
  
 <span data-ttu-id="48895-196">Místo toho použít inicializátor kolekce k sestavení `Dictionary` kolekci, můžete nahradit `BuildDictionary` a `AddToDictionary` metody pomocí následujících metod.</span><span class="sxs-lookup"><span data-stu-id="48895-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="48895-197">V následujícím příkladu <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metoda a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` pro rychlé vyhledání položky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="48895-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="48895-198">`Item` Vlastnost umožňuje přístup k položce v `elements` kolekce s použitím `elements(symbol)` kód v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="48895-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
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
  
 <span data-ttu-id="48895-199">Následující příklad používá místo toho <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda rychlé vyhledání položky podle klíče.</span><span class="sxs-lookup"><span data-stu-id="48895-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="48895-200">Přístup ke kolekci pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="48895-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="48895-201">LINQ (Language-Integrated Query) lze použít pro přístup ke kolekci.</span><span class="sxs-lookup"><span data-stu-id="48895-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="48895-202">Dotazy LINQ poskytují možnost filtrování, řazení a seskupování schopností.</span><span class="sxs-lookup"><span data-stu-id="48895-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="48895-203">Další informace najdete v tématu [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="48895-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="48895-204">Následující příklad spustí dotaz LINQ v rámci obecného `List`.</span><span class="sxs-lookup"><span data-stu-id="48895-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="48895-205">Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="48895-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="48895-206">Řazení kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-206">Sorting a Collection</span></span>  
 <span data-ttu-id="48895-207">Následující příklad ukazuje postup při řazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="48895-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="48895-208">Příklad řadí instance třídy `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="48895-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="48895-209">`Car` Implementuje třída <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="48895-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="48895-210">Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda provádí jedno porovnání, který se používá pro řazení.</span><span class="sxs-lookup"><span data-stu-id="48895-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="48895-211">Uživatelem zapsaný kód v `CompareTo` metoda vrátí hodnotu pro všechna porovnání aktuálního objektu s jiným objektem.</span><span class="sxs-lookup"><span data-stu-id="48895-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="48895-212">Vrácená hodnota je menší než nula, pokud se aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula jestli jsou shodné.</span><span class="sxs-lookup"><span data-stu-id="48895-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="48895-213">To umožňuje v kódu definovat kritéria pro větší, menší než a rovná.</span><span class="sxs-lookup"><span data-stu-id="48895-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="48895-214">V `ListCars` metody, `cars.Sort()` příkaz Seřadí seznam.</span><span class="sxs-lookup"><span data-stu-id="48895-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="48895-215">Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda bude automaticky volána pro `Car` objekty v `List`.</span><span class="sxs-lookup"><span data-stu-id="48895-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="48895-216">Definice vlastní kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="48895-217">Můžete definovat kolekce implementací <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="48895-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="48895-218">Další informace najdete v tématu [vytvoření výčtu kolekce](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="48895-218">For additional information, see [Enumerating a Collection](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="48895-219">Přestože můžete definovat vlastní kolekci, je obvykle vhodnější použít namísto toho kolekce, které jsou zahrnuty v rozhraní .NET Framework, které jsou popsány v [typy kolekcí](#kinds-of-collections) výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="48895-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="48895-220">Následující příklad definuje vlastní třídu kolekce s názvem `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="48895-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="48895-221">Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="48895-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="48895-222">`GetEnumerator` Metoda vrací instanci `ColorEnumerator` třídy.</span><span class="sxs-lookup"><span data-stu-id="48895-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="48895-223">`ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerator.Current%2A> vlastnost <xref:System.Collections.IEnumerator.MoveNext%2A> metoda, a <xref:System.Collections.IEnumerator.Reset%2A> implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="48895-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="48895-224">Iterátory</span><span class="sxs-lookup"><span data-stu-id="48895-224">Iterators</span></span>  
 <span data-ttu-id="48895-225">*Iterátoru* se používá k provedení vlastní iterace nad kolekcí.</span><span class="sxs-lookup"><span data-stu-id="48895-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="48895-226">Iterátor může být metoda nebo `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="48895-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="48895-227">Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz k vrácení každého prvku kolekce jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="48895-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="48895-228">Můžete volat iterátor pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="48895-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="48895-229">Každá iterace `For Each` smyčky volá iterátor.</span><span class="sxs-lookup"><span data-stu-id="48895-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="48895-230">Když `Yield` je dosažen příkaz v iterátoru, je vrácen výraz a je zachováno aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="48895-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="48895-231">Provádění je restartováno z tohoto umístění při příštím volání iterátoru.</span><span class="sxs-lookup"><span data-stu-id="48895-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="48895-232">Další informace najdete v tématu [iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="48895-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="48895-233">Následující příklad používá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="48895-233">The following example uses an iterator method.</span></span> <span data-ttu-id="48895-234">Iterační metoda obsahuje `Yield` , který se nachází uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="48895-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="48895-235">V `ListEvenNumbers` metodě, každé iterace `For Each` tělo s příkazy vytvoří volání metody iterátoru, který pokračuje k dalšímu `Yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="48895-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48895-236">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48895-236">See also</span></span>

- [<span data-ttu-id="48895-237">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="48895-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
- [<span data-ttu-id="48895-238">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48895-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)  
- [<span data-ttu-id="48895-239">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="48895-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [<span data-ttu-id="48895-240">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48895-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="48895-241">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="48895-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [<span data-ttu-id="48895-242">Kolekce a datové struktury</span><span class="sxs-lookup"><span data-stu-id="48895-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
- [<span data-ttu-id="48895-243">Vytváření a manipulace s kolekcemi</span><span class="sxs-lookup"><span data-stu-id="48895-243">Creating and Manipulating Collections</span></span>](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [<span data-ttu-id="48895-244">Výběr třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
- [<span data-ttu-id="48895-245">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="48895-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [<span data-ttu-id="48895-246">Kdy použít generické kolekce</span><span class="sxs-lookup"><span data-stu-id="48895-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
