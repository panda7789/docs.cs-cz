---
title: 'Postupy: Přidávání vlastních metod do dotazů LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 5aca346c182d63967f02a7f5444c5fd6d86ae3d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702227"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Postupy: Přidávání vlastních metod do dotazů LINQ (C#)

Můžete rozšířit sadu metod, které můžete použít pro LINQ dotazy přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Kromě standardní průměr nebo maximální operace, například můžete vytvořit vlastní agregační metody pro výpočet jednu hodnotu ze sekvence hodnot. Můžete také vytvořit metodu, která funguje jako vlastní filtr a transformovat data specifická pro sekvenci hodnot a vrátí novou sekvenci. Příklady těchto metod jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, a <xref:System.Linq.Enumerable.Reverse%2A>.

Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, vlastních metod můžete použít na jakékoli vyčíslitelné kolekce. Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Přidání agregované – metoda

Metodu agregace vypočítá jedna hodnota ze sady hodnot. LINQ poskytuje několik metod agregace, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>. Můžete vytvořit vlastní metoda aggregate přidáním metodu rozšíření k <xref:System.Collections.Generic.IEnumerable%601> rozhraní.

Následující příklad kódu ukazuje, jak vytvořit rozšiřující metoda volá `Median` vypočítat medián pro sekvenci čísel typu `double`.

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

Volání této metody rozšíření pro jakékoli vyčíslitelné kolekce stejným způsobem, volání metod agregační z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.

Následující příklad kódu ukazuje, jak používat `Median` metodu pro pole typu `double`.

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení agregační metodu tak, aby přijímal různé typy

Můžete použít přetížení agregační metodu tak, aby přijímá pořadí podle různých typů. Standardní přístup je přetížení pro každý typ vytvoření. Další možností je vytvořit přetížení, které bude trvat obecného typu a proveďte převod na určitý typ pomocí delegáta. Oba přístupy můžete také kombinovat.

#### <a name="to-create-an-overload-for-each-type"></a>Chcete-li vytvořit přetížení pro každý typ

Můžete vytvořit na konkrétní přetížení pro každý typ, který chcete podporovat. Následující příklad kódu ukazuje přetížení `Median` metodu `integer` typu.

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

Nyní můžete volat `Median` přetížení pro obě `integer` a `double` typů, jak je znázorněno v následujícím kódu:

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

#### <a name="to-create-a-generic-overload"></a>Chcete-li vytvořit obecné přetížení

Můžete také vytvořit přetížení přijímající posloupnost obecných objektů. Toto přetížení přebírá jako parametr delegáta a použije ho k převedení sekvence objektů obecného typu určitého typu.

Následující kód ukazuje přetížení `Median` metodu, která přebírá <xref:System.Func%602> jako parametr. Tento delegát přebírá objekt obecný typ a vrátí objekt typu `double`.

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

Nyní můžete volat `Median` metodu pro sekvenci objektů libovolného typu. Pokud typ nemá žádné vlastní přetížení metody, musíte předat parametr delegátu. V jazyce C# můžete použít výraz lambda pro tento účel. Také v jazyce Visual Basic, pouze pokud používáte `Aggregate` nebo `Group By` klauzule namísto volání metody, které můžete předat libovolná hodnota nebo výraz, který je v oboru tuto klauzuli.

Následující příklad kódu ukazuje, jak volat `Median` metodu pro pole celých čísel a pole řetězců. Pro řetězce se vypočítá Medián pro délky řetězce v poli. Tento příklad ukazuje, jak předat <xref:System.Func%602> parametr do delegáta `Median` metodu pro každý případ.

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

## <a name="adding-a-method-that-returns-a-collection"></a>Přidání metody, která vrátí kolekci

Můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> rozhraní s metodou vlastního dotazu, která vrátí sekvenci hodnot. V takovém případě metoda musí vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>. Tyto metody slouží k použití filtrů nebo data transformací na sekvenci hodnot.

Následující příklad ukazuje, jak vytvořit metodu rozšíření s názvem `AlternateElements` , která vrací každý prvek v kolekci, počínaje prvním prvkem.

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

Lze tuto metodu lze volat rozšíření pro jakékoli vyčíslitelné kolekce stejně, jako by volání z jiné metody <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:

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

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic.IEnumerable%601>
- [Rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
