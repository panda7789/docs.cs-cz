---
title: 'Postupy: Přidávání vlastních metod do dotazů LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 5aca346c182d63967f02a7f5444c5fd6d86ae3d1
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610896"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="08379-102">Postupy: Přidávání vlastních metod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="08379-102">How to: Add Custom Methods for LINQ Queries (C#)</span></span>

<span data-ttu-id="08379-103">Můžete rozšířit sadu metod, které můžete použít pro LINQ dotazy přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="08379-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="08379-104">Kromě standardní průměr nebo maximální operace, například můžete vytvořit vlastní agregační metody pro výpočet jednu hodnotu ze sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="08379-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="08379-105">Můžete také vytvořit metodu, která funguje jako vlastní filtr a transformovat data specifická pro sekvenci hodnot a vrátí novou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="08379-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="08379-106">Příklady těchto metod jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="08379-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="08379-107">Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, vlastních metod můžete použít na jakékoli vyčíslitelné kolekce.</span><span class="sxs-lookup"><span data-stu-id="08379-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="08379-108">Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="08379-108">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="08379-109">Přidání agregované – metoda</span><span class="sxs-lookup"><span data-stu-id="08379-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="08379-110">Metodu agregace vypočítá jedna hodnota ze sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="08379-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="08379-111">LINQ poskytuje několik metod agregace, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="08379-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="08379-112">Můžete vytvořit vlastní metoda aggregate přidáním metodu rozšíření k <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="08379-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="08379-113">Následující příklad kódu ukazuje, jak vytvořit rozšiřující metoda volá `Median` vypočítat medián pro sekvenci čísel typu `double`.</span><span class="sxs-lookup"><span data-stu-id="08379-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

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

<span data-ttu-id="08379-114">Volání této metody rozšíření pro jakékoli vyčíslitelné kolekce stejným způsobem, volání metod agregační z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="08379-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="08379-115">Následující příklad kódu ukazuje, jak používat `Median` metodu pro pole typu `double`.</span><span class="sxs-lookup"><span data-stu-id="08379-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="08379-116">Přetížení agregační metodu tak, aby přijímal různé typy</span><span class="sxs-lookup"><span data-stu-id="08379-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="08379-117">Můžete použít přetížení agregační metodu tak, aby přijímá pořadí podle různých typů.</span><span class="sxs-lookup"><span data-stu-id="08379-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="08379-118">Standardní přístup je přetížení pro každý typ vytvoření.</span><span class="sxs-lookup"><span data-stu-id="08379-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="08379-119">Další možností je vytvořit přetížení, které bude trvat obecného typu a proveďte převod na určitý typ pomocí delegáta.</span><span class="sxs-lookup"><span data-stu-id="08379-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="08379-120">Oba přístupy můžete také kombinovat.</span><span class="sxs-lookup"><span data-stu-id="08379-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="08379-121">Chcete-li vytvořit přetížení pro každý typ</span><span class="sxs-lookup"><span data-stu-id="08379-121">To create an overload for each type</span></span>

<span data-ttu-id="08379-122">Můžete vytvořit na konkrétní přetížení pro každý typ, který chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="08379-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="08379-123">Následující příklad kódu ukazuje přetížení `Median` metodu `integer` typu.</span><span class="sxs-lookup"><span data-stu-id="08379-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="08379-124">Nyní můžete volat `Median` přetížení pro obě `integer` a `double` typů, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="08379-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="08379-125">Chcete-li vytvořit obecné přetížení</span><span class="sxs-lookup"><span data-stu-id="08379-125">To create a generic overload</span></span>

<span data-ttu-id="08379-126">Můžete také vytvořit přetížení přijímající posloupnost obecných objektů.</span><span class="sxs-lookup"><span data-stu-id="08379-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="08379-127">Toto přetížení přebírá jako parametr delegáta a použije ho k převedení sekvence objektů obecného typu určitého typu.</span><span class="sxs-lookup"><span data-stu-id="08379-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="08379-128">Následující kód ukazuje přetížení `Median` metodu, která přebírá <xref:System.Func%602> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="08379-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="08379-129">Tento delegát přebírá objekt obecný typ a vrátí objekt typu `double`.</span><span class="sxs-lookup"><span data-stu-id="08379-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="08379-130">Nyní můžete volat `Median` metodu pro sekvenci objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="08379-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="08379-131">Pokud typ nemá žádné vlastní přetížení metody, musíte předat parametr delegátu.</span><span class="sxs-lookup"><span data-stu-id="08379-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="08379-132">V jazyce C# můžete použít výraz lambda pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="08379-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="08379-133">Také v jazyce Visual Basic, pouze pokud používáte `Aggregate` nebo `Group By` klauzule namísto volání metody, které můžete předat libovolná hodnota nebo výraz, který je v oboru tuto klauzuli.</span><span class="sxs-lookup"><span data-stu-id="08379-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="08379-134">Následující příklad kódu ukazuje, jak volat `Median` metodu pro pole celých čísel a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="08379-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="08379-135">Pro řetězce se vypočítá Medián pro délky řetězce v poli.</span><span class="sxs-lookup"><span data-stu-id="08379-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="08379-136">Tento příklad ukazuje, jak předat <xref:System.Func%602> parametr do delegáta `Median` metodu pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="08379-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="08379-137">Přidání metody, která vrátí kolekci</span><span class="sxs-lookup"><span data-stu-id="08379-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="08379-138">Můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> rozhraní s metodou vlastního dotazu, která vrátí sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="08379-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="08379-139">V takovém případě metoda musí vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="08379-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="08379-140">Tyto metody slouží k použití filtrů nebo data transformací na sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="08379-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="08379-141">Následující příklad ukazuje, jak vytvořit metodu rozšíření s názvem `AlternateElements` , která vrací každý prvek v kolekci, počínaje prvním prvkem.</span><span class="sxs-lookup"><span data-stu-id="08379-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="08379-142">Lze tuto metodu lze volat rozšíření pro jakékoli vyčíslitelné kolekce stejně, jako by volání z jiné metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="08379-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="08379-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08379-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="08379-144">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="08379-144">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
