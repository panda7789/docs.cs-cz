---
title: Postup přidání vlastních metod pro dotazy LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141468"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Postup přidání vlastních metod pro dotazy LINQ (C#)

Můžete rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do rozhraní <xref:System.Collections.Generic.IEnumerable%601>. Například kromě standardních průměrných nebo maximálních operací můžete vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z sekvence hodnot. Můžete také vytvořit metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro sekvenci hodnot a vrátí novou sekvenci. Příklady takových metod jsou <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>a <xref:System.Linq.Enumerable.Reverse%2A>.

Když rozšíříte rozhraní <xref:System.Collections.Generic.IEnumerable%601>, můžete použít vlastní metody do jakékoli vyčíslitelné kolekce. Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Přidání agregační metody

Agregační metoda vypočítá jednu hodnotu ze sady hodnot. LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>a <xref:System.Linq.Enumerable.Max%2A>. Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do rozhraní <xref:System.Collections.Generic.IEnumerable%601>.

Následující příklad kódu ukazuje, jak vytvořit metodu rozšíření nazvanou `Median` pro výpočet mediánu pro sekvenci čísel typu `double`.

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

Tuto metodu rozšíření pro každou vyčíslitelné kolekci můžete zavolat stejným způsobem jako jiné agregační metody z rozhraní <xref:System.Collections.Generic.IEnumerable%601>.

Následující příklad kódu ukazuje, jak použít metodu `Median` pro pole typu `double`.

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Přetížení agregované metody pro příjem různých typů

Můžete přetížit agregační metodu tak, aby mohla přijímat sekvence různých typů. Standardní přístup je vytvořit přetížení pro každý typ. Další možností je vytvořit přetížení, které bude přebírat obecný typ a převést jej na konkrétní typ pomocí delegáta. Oba přístupy můžete také kombinovat.

#### <a name="to-create-an-overload-for-each-type"></a>Pro vytvoření přetížení pro každý typ

Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat. Následující příklad kódu ukazuje přetížení metody `Median` pro typ `integer`.

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

Nyní můžete volat `Median` přetížení pro typy `integer` a `double`, jak je znázorněno v následujícím kódu:

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

#### <a name="to-create-a-generic-overload"></a>Vytvoření obecného přetížení

Můžete také vytvořit přetížení, které přijímá sekvenci generických objektů. Toto přetížení přebírá jako parametr delegáta a používá ho k převodu sekvence objektů obecného typu na konkrétní typ.

Následující kód ukazuje přetížení metody `Median`, která přebírá <xref:System.Func%602> delegáta jako parametr. Tento delegát přebírá objekt generického typu T a vrátí objekt typu `double`.

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

Nyní můžete zavolat metodu `Median` pro sekvenci objektů libovolného typu. Pokud typ nemá vlastní metodu přetížení, je nutné předat parametr delegáta. V C#aplikaci můžete pro tento účel použít výraz lambda. Také v Visual Basic pouze v případě, že použijete klauzuli `Aggregate` nebo `Group By` namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v rámci této klauzule Scope.

Následující příklad kódu ukazuje, jak zavolat metodu `Median` pro pole celých čísel a pole řetězců. Pro řetězce se počítá medián pro délky řetězců v poli. Příklad ukazuje, jak předat parametr delegáta <xref:System.Func%602> do metody `Median` pro každý případ.

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

Rozhraní <xref:System.Collections.Generic.IEnumerable%601> můžete roztáhnout vlastní metodou dotazu, která vrací sekvenci hodnot. V tomto případě musí metoda vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601>. Tyto metody lze použít k aplikování filtrů nebo transformací dat na sekvenci hodnot.

Následující příklad ukazuje, jak vytvořit metodu rozšíření s názvem `AlternateElements`, která vrátí všechny ostatní prvky v kolekci počínaje prvním prvkem.

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

Tuto metodu rozšíření můžete zavolat pro všechny vyčíslitelné kolekce stejně, jako byste volali jiné metody z rozhraní <xref:System.Collections.Generic.IEnumerable%601>, jak je znázorněno v následujícím kódu:

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
- [Rozšiřující metody](../../classes-and-structs/extension-methods.md)
