---
title: 'Postupy: Přidávání vlastních metod do dotazů v jazyce LINQ'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 55004441d2d1d74556da6841f28d113b876d1048
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400601"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="4dbbb-102">Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dbbb-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>

<span data-ttu-id="4dbbb-103">Můžete rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="4dbbb-104">Například kromě standardních průměrných nebo maximálních operací můžete vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="4dbbb-105">Můžete také vytvořit metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro sekvenci hodnot a vrátí novou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="4dbbb-106">Příklady takových metod jsou <xref:System.Linq.Enumerable.Distinct%2A> , <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="4dbbb-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="4dbbb-107">Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít vlastní metody na jakoukoli vyčíslitelné kolekci.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="4dbbb-108">Další informace naleznete v tématu [metody rozšíření](../../language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4dbbb-108">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="4dbbb-109">Přidání agregační metody</span><span class="sxs-lookup"><span data-stu-id="4dbbb-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="4dbbb-110">Agregační metoda vypočítá jednu hodnotu ze sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="4dbbb-111">LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Min%2A> a <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="4dbbb-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="4dbbb-112">Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="4dbbb-113">Následující příklad kódu ukazuje, jak vytvořit rozšiřující metodu volanou pro `Median` Výpočet mediánu pro sekvenci čísel typu `double` .</span><span class="sxs-lookup"><span data-stu-id="4dbbb-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module LINQExtension

    ' Extension method for the IEnumerable(of T) interface.
    ' The method accepts only values of the Double type.
    <Extension()>
    Function Median(ByVal source As IEnumerable(Of Double)) As Double
        If source.Count = 0 Then
            Throw New InvalidOperationException("Cannot compute median for an empty set.")
        End If

        Dim sortedSource = From number In source
                           Order By number

        Dim itemIndex = sortedSource.Count \ 2

        If sortedSource.Count Mod 2 = 0 Then
            ' Even number of items in list.
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2
        Else
            ' Odd number of items in list.
            Return sortedSource(itemIndex)
        End If
    End Function
End Module
```

<span data-ttu-id="4dbbb-114">Tuto metodu rozšíření pro každou vyčíslitelné kolekci můžete zavolat stejným způsobem jako jiné agregační metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="4dbbb-115">V Visual Basic můžete buď použít volání metody, nebo standardní syntaxi dotazu pro `Aggregate` `Group By` klauzuli OR.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="4dbbb-116">Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md) a [klauzule GROUP by](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4dbbb-116">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="4dbbb-117">Následující příklad kódu ukazuje, jak použít `Median` metodu pro pole typu `double` .</span><span class="sxs-lookup"><span data-stu-id="4dbbb-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="4dbbb-118">Přetížení agregované metody pro příjem různých typů</span><span class="sxs-lookup"><span data-stu-id="4dbbb-118">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="4dbbb-119">Můžete přetížit agregační metodu tak, aby mohla přijímat sekvence různých typů.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="4dbbb-120">Standardní přístup je vytvořit přetížení pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="4dbbb-121">Další možností je vytvořit přetížení, které bude přebírat obecný typ a převést jej na konkrétní typ pomocí delegáta.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="4dbbb-122">Oba přístupy můžete také kombinovat.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="4dbbb-123">Pro vytvoření přetížení pro každý typ</span><span class="sxs-lookup"><span data-stu-id="4dbbb-123">To create an overload for each type</span></span>

<span data-ttu-id="4dbbb-124">Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="4dbbb-125">Následující příklad kódu ukazuje přetížení `Median` metody pro daný `integer` typ.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

<span data-ttu-id="4dbbb-126">Nyní můžete volat `Median` přetížení pro oba `integer` `double` typy a, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4dbbb-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
Dim numbers2() As Integer = {1, 2, 3, 4, 5}

Dim query2 = Aggregate num In numbers2 Into Median()

Console.WriteLine("Integer: Median = " & query2)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
' Integer: Median = 3
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="4dbbb-127">Vytvoření obecného přetížení</span><span class="sxs-lookup"><span data-stu-id="4dbbb-127">To create a generic overload</span></span>

<span data-ttu-id="4dbbb-128">Můžete také vytvořit přetížení, které přijímá sekvenci generických objektů.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="4dbbb-129">Toto přetížení přebírá jako parametr delegáta a používá ho k převodu sekvence objektů obecného typu na konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="4dbbb-130">Následující kód ukazuje přetížení `Median` metody, která přebírá <xref:System.Func%602> delegáta jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="4dbbb-131">Tento delegát přebírá objekt typu Generic Type T a vrátí objekt typu `double` .</span><span class="sxs-lookup"><span data-stu-id="4dbbb-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

<span data-ttu-id="4dbbb-132">Nyní můžete zavolat `Median` metodu pro sekvenci objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="4dbbb-133">Pokud typ nemá vlastní metodu přetížení, je nutné předat parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="4dbbb-134">V Visual Basic můžete pro tento účel použít výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="4dbbb-135">Také Pokud použijete `Aggregate` `Group By` klauzuli OR namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v rámci této klauzule Scope.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="4dbbb-136">Následující příklad kódu ukazuje, jak zavolat `Median` metodu pro pole celých čísel a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="4dbbb-137">Pro řetězce se počítá medián pro délky řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="4dbbb-138">Příklad ukazuje, jak předat <xref:System.Func%602> parametr delegáta `Median` metodě pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```vb
Dim numbers3() As Integer = {1, 2, 3, 4, 5}

' You can use num as a parameter for the Median method
' so that the compiler will implicitly convert its value to double.
' If there is no implicit conversion, the compiler will
' display an error message.

Dim query3 = Aggregate num In numbers3 Into Median(num)

Console.WriteLine("Integer: Median = " & query3)

Dim numbers4() As String = {"one", "two", "three", "four", "five"}

' With the generic overload, you can also use numeric properties of objects.

Dim query4 = Aggregate str In numbers4 Into Median(str.Length)

Console.WriteLine("String: Median = " & query4)

' This code produces the following output:
'
' Integer: Median = 3
' String: Median = 4
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="4dbbb-139">Přidání metody, která vrátí kolekci</span><span class="sxs-lookup"><span data-stu-id="4dbbb-139">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="4dbbb-140">Rozhraní můžete roztáhnout <xref:System.Collections.Generic.IEnumerable%601> vlastní metodou dotazu, která vrací sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="4dbbb-141">V tomto případě musí metoda vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="4dbbb-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="4dbbb-142">Tyto metody lze použít k aplikování filtrů nebo transformací dat na sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="4dbbb-143">Následující příklad ukazuje, jak vytvořit rozšiřující metodu s názvem `AlternateElements` , která vrátí všechny ostatní prvky v kolekci počínaje prvním prvkem.</span><span class="sxs-lookup"><span data-stu-id="4dbbb-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```vb
' Extension method for the IEnumerable(of T) interface.
' The method returns every other element of a sequence.

<Extension()>
Function AlternateElements(Of T)(
    ByVal source As IEnumerable(Of T)
    ) As IEnumerable(Of T)

    Dim list As New List(Of T)
    Dim i = 0
    For Each element In source
        If (i Mod 2 = 0) Then
            list.Add(element)
        End If
        i = i + 1
    Next
    Return list
End Function
```

<span data-ttu-id="4dbbb-144">Tuto metodu rozšíření můžete zavolat pro všechny vyčíslitelné kolekce stejně, jako byste volali jiné metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4dbbb-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```vb
Dim strings() As String = {"a", "b", "c", "d", "e"}

Dim query = strings.AlternateElements()

For Each element In query
    Console.WriteLine(element)
Next

' This code produces the following output:
'
' a
' c
' e
```

## <a name="see-also"></a><span data-ttu-id="4dbbb-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dbbb-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="4dbbb-146">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="4dbbb-146">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
