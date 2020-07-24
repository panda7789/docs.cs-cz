---
title: Postup přidání vlastních metod pro dotazy LINQ (C#)
description: Naučte se rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do <T> rozhraní IEnumerable v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: fac0eb4e14eb3bb36313232a7d7fa3060c0ac171
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103601"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="930c7-103">Postup přidání vlastních metod pro dotazy LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="930c7-103">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="930c7-104">Můžete rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="930c7-104">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="930c7-105">Například kromě standardních průměrných nebo maximálních operací můžete vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="930c7-105">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="930c7-106">Můžete také vytvořit metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro sekvenci hodnot a vrátí novou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="930c7-106">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="930c7-107">Příklady takových metod jsou <xref:System.Linq.Enumerable.Distinct%2A> , <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="930c7-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="930c7-108">Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít vlastní metody na jakoukoli vyčíslitelné kolekci.</span><span class="sxs-lookup"><span data-stu-id="930c7-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="930c7-109">Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="930c7-109">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="930c7-110">Přidání agregační metody</span><span class="sxs-lookup"><span data-stu-id="930c7-110">Adding an Aggregate Method</span></span>

<span data-ttu-id="930c7-111">Agregační metoda vypočítá jednu hodnotu ze sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="930c7-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="930c7-112">LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Min%2A> a <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="930c7-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="930c7-113">Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="930c7-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="930c7-114">Následující příklad kódu ukazuje, jak vytvořit rozšiřující metodu volanou pro `Median` Výpočet mediánu pro sekvenci čísel typu `double` .</span><span class="sxs-lookup"><span data-stu-id="930c7-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        var countOfElementsInTheSet = source?.Count() ?? 0;

        if (countOfElementsInTheSet == 0)
        {
            throw new InvalidOperationException("Cannot compute median for a null or empty set.");
        }

        var sortedList = (from number in source
                         orderby number
                         select number).ToList();

        int itemIndex = countOfElementsInTheSet / 2;

        if (countOfElementsInTheSet % 2 == 0)
        {
            // Even number of items.
            return (sortedList[itemIndex] + sortedList[itemIndex - 1]) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList[itemIndex];
        }
    }
}
```

<span data-ttu-id="930c7-115">Tuto metodu rozšíření pro každou vyčíslitelné kolekci můžete zavolat stejným způsobem jako jiné agregační metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="930c7-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="930c7-116">Následující příklad kódu ukazuje, jak použít `Median` metodu pro pole typu `double` .</span><span class="sxs-lookup"><span data-stu-id="930c7-116">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="930c7-117">Přetížení agregované metody pro příjem různých typů</span><span class="sxs-lookup"><span data-stu-id="930c7-117">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="930c7-118">Můžete přetížit agregační metodu tak, aby mohla přijímat sekvence různých typů.</span><span class="sxs-lookup"><span data-stu-id="930c7-118">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="930c7-119">Standardní přístup je vytvořit přetížení pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="930c7-119">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="930c7-120">Další možností je vytvořit přetížení, které bude přebírat obecný typ a převést jej na konkrétní typ pomocí delegáta.</span><span class="sxs-lookup"><span data-stu-id="930c7-120">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="930c7-121">Oba přístupy můžete také kombinovat.</span><span class="sxs-lookup"><span data-stu-id="930c7-121">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="930c7-122">Pro vytvoření přetížení pro každý typ</span><span class="sxs-lookup"><span data-stu-id="930c7-122">To create an overload for each type</span></span>

<span data-ttu-id="930c7-123">Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="930c7-123">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="930c7-124">Následující příklad kódu ukazuje přetížení `Median` metody pro daný `integer` typ.</span><span class="sxs-lookup"><span data-stu-id="930c7-124">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="930c7-125">Nyní můžete volat `Median` přetížení pro oba `integer` `double` typy a, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="930c7-125">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="930c7-126">Vytvoření obecného přetížení</span><span class="sxs-lookup"><span data-stu-id="930c7-126">To create a generic overload</span></span>

<span data-ttu-id="930c7-127">Můžete také vytvořit přetížení, které přijímá sekvenci generických objektů.</span><span class="sxs-lookup"><span data-stu-id="930c7-127">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="930c7-128">Toto přetížení přebírá jako parametr delegáta a používá ho k převodu sekvence objektů obecného typu na konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="930c7-128">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="930c7-129">Následující kód ukazuje přetížení `Median` metody, která přebírá <xref:System.Func%602> delegáta jako parametr.</span><span class="sxs-lookup"><span data-stu-id="930c7-129">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="930c7-130">Tento delegát přebírá objekt typu Generic Type T a vrátí objekt typu `double` .</span><span class="sxs-lookup"><span data-stu-id="930c7-130">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="930c7-131">Nyní můžete zavolat `Median` metodu pro sekvenci objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="930c7-131">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="930c7-132">Pokud typ nemá vlastní metodu přetížení, je nutné předat parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="930c7-132">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="930c7-133">V jazyce C# můžete pro tento účel použít výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="930c7-133">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="930c7-134">Také v Visual Basic pouze v případě, že použijete `Aggregate` `Group By` klauzuli OR namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v rozsahu této klauzule.</span><span class="sxs-lookup"><span data-stu-id="930c7-134">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="930c7-135">Následující příklad kódu ukazuje, jak zavolat `Median` metodu pro pole celých čísel a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="930c7-135">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="930c7-136">Pro řetězce se počítá medián pro délky řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="930c7-136">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="930c7-137">Příklad ukazuje, jak předat <xref:System.Func%602> parametr delegáta `Median` metodě pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="930c7-137">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="930c7-138">Přidání metody, která vrátí kolekci</span><span class="sxs-lookup"><span data-stu-id="930c7-138">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="930c7-139">Rozhraní můžete roztáhnout <xref:System.Collections.Generic.IEnumerable%601> vlastní metodou dotazu, která vrací sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="930c7-139">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="930c7-140">V tomto případě musí metoda vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="930c7-140">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="930c7-141">Tyto metody lze použít k aplikování filtrů nebo transformací dat na sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="930c7-141">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="930c7-142">Následující příklad ukazuje, jak vytvořit rozšiřující metodu s názvem `AlternateElements` , která vrátí všechny ostatní prvky v kolekci počínaje prvním prvkem.</span><span class="sxs-lookup"><span data-stu-id="930c7-142">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

<span data-ttu-id="930c7-143">Tuto metodu rozšíření můžete zavolat pro všechny vyčíslitelné kolekce stejně, jako byste volali jiné metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="930c7-143">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a><span data-ttu-id="930c7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="930c7-144">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="930c7-145">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="930c7-145">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
