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
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Jak přidat vlastní metody pro dotazy LINQ (C#)

Sadu metod, které můžete použít pro dotazy LINQ, můžete rozšířit <xref:System.Collections.Generic.IEnumerable%601> přidáním rozšiřujících metod do rozhraní. Kromě standardního průměru nebo maximálních operací můžete například vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z posloupnosti hodnot. Můžete také vytvořit metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro posloupnost hodnot a vrátí novou sekvenci. Příklady takových metod <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Skip%2A>jsou <xref:System.Linq.Enumerable.Reverse%2A>, a .

Při rozšíření <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít vlastní metody pro libovolný počet početné kolekce. Další informace naleznete v [tématu Metody rozšíření](../../classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Přidání agregační metody

Agregační metoda vypočítá jednu hodnotu ze sady hodnot. LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Max%2A>. Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.

Následující příklad kódu ukazuje, jak vytvořit `Median` metodu rozšíření volané pro `double`výpočet mediánu pro posloupnost čísel typu .

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

Volání této metody rozšíření pro všechny výčtové kolekce stejným způsobem <xref:System.Collections.Generic.IEnumerable%601> volat jiné agregační metody z rozhraní.

Následující příklad kódu ukazuje, `Median` jak použít metodu `double`pro pole typu .

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení agregační metody přijmout různé typy

Můžete přetížení agregační metody tak, aby přijímá sekvence různých typů. Standardní přístup je vytvořit přetížení pro každý typ. Jiný přístup je vytvořit přetížení, které bude trvat obecný typ a převést na určitý typ pomocí delegáta. Můžete také kombinovat oba přístupy.

#### <a name="to-create-an-overload-for-each-type"></a>Chcete-li vytvořit přetížení pro každý typ

Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat. Následující příklad kódu ukazuje přetížení `Median` metody `integer` pro typ.

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

Nyní můžete volat `Median` přetížení pro `integer` `double` oba typy, jak je znázorněno v následujícím kódu:

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

Můžete také vytvořit přetížení, které přijímá posloupnost obecných objektů. Toto přetížení trvá delegát jako parametr a používá jej k převodu posloupnosti objektů obecného typu na určitý typ.

Následující kód ukazuje přetížení `Median` metody, která <xref:System.Func%602> přebírá delegáta jako parametr. Tento delegát převezme objekt obecného typu T `double`a vrátí objekt typu .

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

Nyní můžete volat `Median` metodu pro posloupnost objektů libovolného typu. Pokud typ nemá vlastní přetížení metody, budete muset předat parametr delegáta. V c# můžete použít lambda výraz pro tento účel. Také pouze v jazyce Visual `Aggregate` Basic, pokud použijete klauzuli or `Group By` namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v oboru této klauzule.

Následující ukázkový kód ukazuje, `Median` jak volat metodu pro pole celá čísla a pole řetězců. Pro řetězce se vypočítá medián pro délky řetězců v poli. Příklad ukazuje, jak <xref:System.Func%602> předat parametr `Median` delegáta metodě pro každý případ.

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

## <a name="adding-a-method-that-returns-a-collection"></a>Přidání metody, která vrací kolekci

<xref:System.Collections.Generic.IEnumerable%601> Rozhraní můžete rozšířit o vlastní metodu dotazu, která vrací posloupnost hodnot. V tomto případě musí metoda vrátit <xref:System.Collections.Generic.IEnumerable%601>kolekci typu . Tyto metody lze použít filtry nebo transformace dat na posloupnost hodnot.

Následující příklad ukazuje, jak vytvořit `AlternateElements` metodu rozšíření s názvem, která vrací každý další prvek v kolekci, počínaje prvním prvkem.

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

Tuto metodu rozšíření můžete volat pro libovolnou početnou kolekci <xref:System.Collections.Generic.IEnumerable%601> stejně jako byste volat jiné metody z rozhraní, jak je znázorněno v následujícím kódu:

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

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic.IEnumerable%601>
- [Metody rozšíření](../../classes-and-structs/extension-methods.md)
