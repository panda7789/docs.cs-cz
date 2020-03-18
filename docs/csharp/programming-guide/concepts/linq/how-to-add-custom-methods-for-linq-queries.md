---
title: Jak přidat vlastní metody pro dotazy LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141468"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="4565f-102">Jak přidat vlastní metody pro dotazy LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="4565f-102">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="4565f-103">Sadu metod, které můžete použít pro dotazy LINQ, můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> přidáním rozšiřujících metod do rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4565f-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="4565f-104">Kromě standardního průměru nebo maximálních operací můžete například vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z posloupnosti hodnot.</span><span class="sxs-lookup"><span data-stu-id="4565f-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="4565f-105">Můžete také vytvořit metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro posloupnost hodnot a vrátí novou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4565f-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="4565f-106">Příklady takových metod <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Skip%2A>jsou <xref:System.Linq.Enumerable.Reverse%2A>, a .</span><span class="sxs-lookup"><span data-stu-id="4565f-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="4565f-107">Při rozšíření <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít vlastní metody pro libovolný počet početné kolekce.</span><span class="sxs-lookup"><span data-stu-id="4565f-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="4565f-108">Další informace naleznete v [tématu Metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4565f-108">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="4565f-109">Přidání agregační metody</span><span class="sxs-lookup"><span data-stu-id="4565f-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="4565f-110">Agregační metoda vypočítá jednu hodnotu ze sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="4565f-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="4565f-111">LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="4565f-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="4565f-112">Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4565f-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="4565f-113">Následující příklad kódu ukazuje, jak vytvořit `Median` metodu rozšíření volané pro `double`výpočet mediánu pro posloupnost čísel typu .</span><span class="sxs-lookup"><span data-stu-id="4565f-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        if (source.Count() == 0)
        {
            throw new InvalidOperationException("Cannot compute median for an empty set.");
        }

        var sortedList = from number in source
                         orderby number
                         select number;

        int itemIndex = (int)sortedList.Count() / 2;

        if (sortedList.Count() % 2 == 0)
        {
            // Even number of items.
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList.ElementAt(itemIndex);
        }
    }
}
```

<span data-ttu-id="4565f-114">Volání této metody rozšíření pro všechny výčtové kolekce stejným způsobem <xref:System.Collections.Generic.IEnumerable%601> volat jiné agregační metody z rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4565f-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="4565f-115">Následující příklad kódu ukazuje, `Median` jak použít metodu `double`pro pole typu .</span><span class="sxs-lookup"><span data-stu-id="4565f-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="4565f-116">Přetížení agregační metody přijmout různé typy</span><span class="sxs-lookup"><span data-stu-id="4565f-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="4565f-117">Můžete přetížení agregační metody tak, aby přijímá sekvence různých typů.</span><span class="sxs-lookup"><span data-stu-id="4565f-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="4565f-118">Standardní přístup je vytvořit přetížení pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="4565f-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="4565f-119">Jiný přístup je vytvořit přetížení, které bude trvat obecný typ a převést na určitý typ pomocí delegáta.</span><span class="sxs-lookup"><span data-stu-id="4565f-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="4565f-120">Můžete také kombinovat oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="4565f-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="4565f-121">Chcete-li vytvořit přetížení pro každý typ</span><span class="sxs-lookup"><span data-stu-id="4565f-121">To create an overload for each type</span></span>

<span data-ttu-id="4565f-122">Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="4565f-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="4565f-123">Následující příklad kódu ukazuje přetížení `Median` metody `integer` pro typ.</span><span class="sxs-lookup"><span data-stu-id="4565f-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="4565f-124">Nyní můžete volat `Median` přetížení pro `integer` `double` oba typy, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4565f-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="4565f-125">Chcete-li vytvořit obecné přetížení</span><span class="sxs-lookup"><span data-stu-id="4565f-125">To create a generic overload</span></span>

<span data-ttu-id="4565f-126">Můžete také vytvořit přetížení, které přijímá posloupnost obecných objektů.</span><span class="sxs-lookup"><span data-stu-id="4565f-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="4565f-127">Toto přetížení trvá delegát jako parametr a používá jej k převodu posloupnosti objektů obecného typu na určitý typ.</span><span class="sxs-lookup"><span data-stu-id="4565f-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="4565f-128">Následující kód ukazuje přetížení `Median` metody, která <xref:System.Func%602> přebírá delegáta jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4565f-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="4565f-129">Tento delegát převezme objekt obecného typu T `double`a vrátí objekt typu .</span><span class="sxs-lookup"><span data-stu-id="4565f-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="4565f-130">Nyní můžete volat `Median` metodu pro posloupnost objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="4565f-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="4565f-131">Pokud typ nemá vlastní přetížení metody, budete muset předat parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="4565f-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="4565f-132">V c# můžete použít lambda výraz pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="4565f-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="4565f-133">Také pouze v jazyce Visual `Aggregate` Basic, pokud použijete klauzuli or `Group By` namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v oboru této klauzule.</span><span class="sxs-lookup"><span data-stu-id="4565f-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="4565f-134">Následující ukázkový kód ukazuje, `Median` jak volat metodu pro pole celá čísla a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="4565f-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="4565f-135">Pro řetězce se vypočítá medián pro délky řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="4565f-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="4565f-136">Příklad ukazuje, jak <xref:System.Func%602> předat parametr `Median` delegáta metodě pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="4565f-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="4565f-137">Přidání metody, která vrací kolekci</span><span class="sxs-lookup"><span data-stu-id="4565f-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="4565f-138"><xref:System.Collections.Generic.IEnumerable%601> Rozhraní můžete rozšířit o vlastní metodu dotazu, která vrací posloupnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="4565f-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="4565f-139">V tomto případě musí metoda vrátit <xref:System.Collections.Generic.IEnumerable%601>kolekci typu .</span><span class="sxs-lookup"><span data-stu-id="4565f-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="4565f-140">Tyto metody lze použít filtry nebo transformace dat na posloupnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="4565f-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="4565f-141">Následující příklad ukazuje, jak vytvořit `AlternateElements` metodu rozšíření s názvem, která vrací každý další prvek v kolekci, počínaje prvním prvkem.</span><span class="sxs-lookup"><span data-stu-id="4565f-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="4565f-142">Tuto metodu rozšíření můžete volat pro libovolnou početnou kolekci <xref:System.Collections.Generic.IEnumerable%601> stejně jako byste volat jiné metody z rozhraní, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4565f-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4565f-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="4565f-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="4565f-144">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="4565f-144">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
