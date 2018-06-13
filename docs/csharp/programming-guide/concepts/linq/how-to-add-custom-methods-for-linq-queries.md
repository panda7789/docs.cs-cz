---
title: 'Postupy: Přidání vlastních metod pro dotazů LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: cd282b4b8ee4add759070317d9dbc3f78c07abf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326895"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="6bf8c-102">Postupy: Přidání vlastních metod pro dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="6bf8c-102">How to: Add Custom Methods for LINQ Queries (C#)</span></span>
<span data-ttu-id="6bf8c-103">Můžete rozšířit sadu metody, které můžete použít pro dotazy LINQ přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="6bf8c-104">Kromě standardní průměr nebo maximální operace, například můžete vytvořit vlastní metoda aggregate vypočítat jednu hodnotu z pořadí hodnot.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="6bf8c-105">Můžete také vytvořit metodu, která funguje jako vlastní nebo konkrétní data transformace pro pořadí hodnot a vrátí nové pořadí.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="6bf8c-106">Příkladem takové metody jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="6bf8c-107">Pokud rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít pro jakékoli vyčíslitelná kolekce vlastních metod.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="6bf8c-108">Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="6bf8c-108">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="6bf8c-109">Přidání agregační metoda</span><span class="sxs-lookup"><span data-stu-id="6bf8c-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="6bf8c-110">Agregační metoda vypočítá jednu hodnotu ze sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="6bf8c-111">LINQ poskytuje několik metod agregační, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="6bf8c-112">Přidáním metodu rozšíření k můžete vytvořit vlastní metoda aggregate <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="6bf8c-113">Následující příklad kódu ukazuje, jak vytvořit volat metody rozšíření `Median` vypočítat medián pro pořadí čísel typu `double`.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="6bf8c-114">Volání této metody rozšíření pro jakoukoli kolekci, výčtové stejným způsobem volání z jiné agregační metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="6bf8c-115">Následující příklad kódu ukazuje, jak používat `Median` metodu pro pole typu `double`.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
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
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="6bf8c-116">Přetížení metody agregační tak, aby přijímal různých typů</span><span class="sxs-lookup"><span data-stu-id="6bf8c-116">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="6bf8c-117">Může dojít k přetížení agregační metodu tak, aby přijímá pořadí různých typů.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="6bf8c-118">Standardní přístupu je vytvoření přetížení pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="6bf8c-119">Další možností je vytvořit přetížení, které bude trvat obecného typu a převést jej do konkrétního typu pomocí delegáta.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="6bf8c-120">Můžete také kombinovat obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-120">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="6bf8c-121">Chcete-li vytvořit přetížení pro každý typ</span><span class="sxs-lookup"><span data-stu-id="6bf8c-121">To create an overload for each type</span></span>  
 <span data-ttu-id="6bf8c-122">Můžete vytvořit na konkrétní přetížení pro každý typ, který chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="6bf8c-123">Následující příklad kódu ukazuje přetížení `Median` metodu `integer` typu.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 <span data-ttu-id="6bf8c-124">Nyní můžete volat `Median` přetížení pro obě `integer` a `double` typů, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6bf8c-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="6bf8c-125">Chcete-li vytvořit obecné přetížení</span><span class="sxs-lookup"><span data-stu-id="6bf8c-125">To create a generic overload</span></span>  
 <span data-ttu-id="6bf8c-126">Můžete také vytvořit přetížení, které přijímá pořadí obecné objektů.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="6bf8c-127">Toto přetížení trvá delegáta jako parametr a používá ho převést na určitý typ pořadí objektů obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="6bf8c-128">Následující kód ukazuje přetížení `Median` metody, která přijímá <xref:System.Func%602> delegovat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="6bf8c-129">Tento delegát přebírá objekt obecného typu T a vrátí objekt typu `double`.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 <span data-ttu-id="6bf8c-130">Nyní můžete volat `Median` metoda sekvenci objekty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="6bf8c-131">Pokud není typ vlastního přetížení metody, budete muset předání parametru delegáta.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="6bf8c-132">V jazyce C# můžete pro tento účel výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="6bf8c-133">Také v jazyce Visual Basic, pouze pokud použijete `Aggregate` nebo `Group By` klauzule namísto volání metody, které můžete předat libovolná hodnota nebo výraz, který je v oboru tuto klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="6bf8c-134">Následující příklad kódu ukazuje způsob volání `Median` metodu pro pole celých čísel a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="6bf8c-135">Pro řetězce je vypočítána Medián pro délky v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="6bf8c-136">Příklad ukazuje, jak předat <xref:System.Func%602> delegovat parametru `Median` metoda pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
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
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="6bf8c-137">Přidání metody, která vrátí kolekci</span><span class="sxs-lookup"><span data-stu-id="6bf8c-137">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="6bf8c-138">Můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> rozhraní s vlastního dotazu metodu, která vrátí pořadí hodnot.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="6bf8c-139">V takovém případě metodu musí vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="6bf8c-140">Tyto metody lze použít filtry nebo data transformací pořadí hodnot.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="6bf8c-141">Následující příklad ukazuje, jak vytvořit metody rozšíření s názvem `AlternateElements` , vrátí každý další element v kolekci, od první prvek.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
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
 <span data-ttu-id="6bf8c-142">Můžete tuto metodu lze volat rozšíření pro jakoukoli kolekci, výčtové stejně, jako by volání z jiné metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6bf8c-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6bf8c-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bf8c-143">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="6bf8c-144">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="6bf8c-144">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
