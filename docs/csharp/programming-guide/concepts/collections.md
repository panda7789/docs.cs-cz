---
title: Kolekce (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: a560155b936aef7a4a346d39eaed75e0a85c1a73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169880"
---
# <a name="collections-c"></a>Kolekce (C#)

Pro mnoho aplikací chcete vytvořit a spravovat skupiny souvisejících objektů. Existují dva způsoby seskupení objektů: vytvořením polí objektů a vytvořením kolekcí objektů.

Pole jsou nejužitečnější pro vytváření a práci s pevným počtem objektů silného typu. Informace o polích naleznete v [tématu Arrays](../arrays/index.md).

Kolekce poskytují flexibilnější způsob práce se skupinami objektů. Na rozdíl od polí může skupina objektů, se kterými pracujete, dynamicky růst a zmenšovat podle potřeby aplikace. Pro některé kolekce můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.

Kolekce je třída, takže je nutné deklarovat instanci třídy před přidáním prvků do této kolekce.

Pokud vaše kolekce obsahuje prvky pouze jednoho datového typu, <xref:System.Collections.Generic?displayProperty=nameWithType> můžete použít jednu z tříd v oboru názvů. Obecná kolekce vynucuje bezpečnost typů tak, aby do ní nebylo možné přidat žádný jiný datový typ. Při načtení prvku z obecné kolekce, není nutné určit jeho datový typ nebo převést.

> [!NOTE]
> Příklady v tomto tématu patří [použití](../../language-reference/keywords/using-directive.md) `System.Collections.Generic` direktiv y pro a `System.Linq` obory názvů.

 **V tomto tématu**

- [Používání jednoduché kolekce](#BKMK_SimpleCollection)

- [Typy kolekcí](#BKMK_KindsOfCollections)

  - [Třídy System.Collections.Generic](#BKMK_Generic)

  - [Třídy System.Collections.Concurrent](#BKMK_Concurrent)

  - [Třídy System.Collections](#BKMK_Collections)

- [Implementace kolekce párů klíč/hodnota](#BKMK_KeyValuePairs)

- [Přístup ke kolekci pomocí jazyka LINQ](#BKMK_LINQ)

- [Řazení kolekce](#BKMK_Sorting)

- [Definice vlastní kolekce](#BKMK_CustomCollection)

- [Iterátory](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce

Příklady v této části <xref:System.Collections.Generic.List%601> používají obecnou třídu, která umožňuje pracovat se silným seznamem objektů.

Následující příklad vytvoří seznam řetězců a potom iterates prostřednictvím řetězce pomocí [foreach](../../language-reference/keywords/foreach-in.md) prohlášení.

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

Pokud obsah kolekce jsou známy předem, můžete použít *inicializační kolekce* inicializovat kolekce. Další informace naleznete v [tématu Objekt a kolekce Initializers](../classes-and-structs/object-and-collection-initializers.md).

Následující příklad je stejný jako v předchozím příkladu, s výjimkou inicializátor kolekce se používá k přidání prvků do kolekce.

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

Můžete použít [for](../../language-reference/keywords/for.md) příkaz namísto příkazu `foreach` iterát prostřednictvím kolekce. Toho lze provést přístupem k prvky kolekce podle pozice indexu. Index prvků začíná na 0 a končí na počet prvků minus 1.

Následující příklad iterates prostřednictvím prvky `for` kolekce `foreach`pomocí místo .

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

Následující příklad odebere prvek z kolekce zadáním objektu, který má být odebrán.

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

Následující příklad odebere prvky z obecného seznamu. Místo příkazu `foreach` se používá [příkaz for,](../../language-reference/keywords/for.md) který itezuje v sestupném pořadí. Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraný prvek mít nižší hodnotu indexu.

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

Pro typ prvků v <xref:System.Collections.Generic.List%601>aplikaci můžete také definovat vlastní třídu. V následujícím příkladu `Galaxy` je třída, <xref:System.Collections.Generic.List%601> která je používána, definována v kódu.

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a>Typy kolekcí

Mnoho běžných kolekcí poskytuje rozhraní .NET Framework. Každý typ kolekce je určen pro konkrétní účel.

Některé běžné třídy kolekce jsou popsány v této části:

- <xref:System.Collections.Generic> – třídy

- <xref:System.Collections.Concurrent> – třídy

- <xref:System.Collections> – třídy

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a>Třídy System.Collections.Generic

Můžete vytvořit obecnou kolekci pomocí jedné z <xref:System.Collections.Generic> tříd v oboru názvů. Obecná kolekce je užitečná, když každá položka v kolekci má stejný datový typ. Obecná kolekce vynucuje silné psaní tím, že umožňuje pouze požadovaný datový typ, který má být přidán.

V následující tabulce jsou uvedeny některé <xref:System.Collections.Generic?displayProperty=nameWithType> často používané třídy oboru názvů:

|Třída|Popis|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě klíče.|
|<xref:System.Collections.Generic.List%601>|Představuje seznam objektů, které lze přistupovat index. Poskytuje metody pro vyhledávání, řazení a úpravy seznamů.|
|<xref:System.Collections.Generic.Queue%601>|Představuje první in, first out (FIFO) kolekce objektů.|
|<xref:System.Collections.Generic.SortedList%602>|Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.|
|<xref:System.Collections.Generic.Stack%601>|Představuje poslední in, first out (LIFO) kolekce objektů.|

Další informace naleznete [v tématu Běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic>.

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>Třídy System.Collections.Concurrent

V rozhraní .NET Framework 4 nebo novější <xref:System.Collections.Concurrent> kolekce v oboru názvů poskytují efektivní operace bezpečné pro přístup k kolekcím z více vláken.

Třídy v <xref:System.Collections.Concurrent> oboru názvů by měly být <xref:System.Collections.Generic?displayProperty=nameWithType> použity namísto odpovídající typy v a <xref:System.Collections?displayProperty=nameWithType> obory názvů vždy více vláken přístup ke kolekci současně. Další informace naleznete v [tématu Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.

Některé třídy <xref:System.Collections.Concurrent> zahrnuté <xref:System.Collections.Concurrent.BlockingCollection%601>v <xref:System.Collections.Concurrent.ConcurrentDictionary%602> <xref:System.Collections.Concurrent.ConcurrentQueue%601>oboru <xref:System.Collections.Concurrent.ConcurrentStack%601>názvů jsou , , , a .

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a>Třídy System.Collections

Třídy v <xref:System.Collections?displayProperty=nameWithType> oboru názvů neukládají prvky jako specificky `Object`zadané objekty, ale jako objekty typu .

Kdykoli je to možné, měli byste <xref:System.Collections.Generic?displayProperty=nameWithType> použít obecné <xref:System.Collections.Concurrent> kolekce v oboru názvů `System.Collections` nebo oboru názvů namísto starších typů v oboru názvů.

V následující tabulce jsou uvedeny některé `System.Collections` často používané třídy v oboru názvů:

|Třída|Popis|
|---|---|
|<xref:System.Collections.ArrayList>|Představuje pole objektů, jejichž velikost je dynamicky zvýšena podle potřeby.|
|<xref:System.Collections.Hashtable>|Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hash klíče.|
|<xref:System.Collections.Queue>|Představuje první in, first out (FIFO) kolekce objektů.|
|<xref:System.Collections.Stack>|Představuje poslední in, first out (LIFO) kolekce objektů.|

Obor <xref:System.Collections.Specialized> názvů poskytuje specializované a silné typy tříd kolekce, jako jsou například kolekce pouze řetězce a propojené seznam a hybridní slovníky.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota

Obecná <xref:System.Collections.Generic.Dictionary%602> kolekce umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku. Každý doplněk do slovníku se skládá z hodnoty a jeho přidruženého klíče. Načítání hodnoty pomocí jeho klíče je `Dictionary` rychlé, protože třída je implementována jako tabulka hash.

Následující příklad vytvoří `Dictionary` kolekci a iterates prostřednictvím `foreach` slovníku pomocí příkazu.

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

Chcete-li místo toho použít `Dictionary` inicializátor `BuildDictionary` kolekce `AddToDictionary` k sestavení kolekce, můžete nahradit metody a následující metodou.

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodu <xref:System.Collections.Generic.Dictionary%602.Item%2A> a `Dictionary` vlastnost rychle najít položku podle klíče. Vlastnost `Item` umožňuje přístup k položce `elements` v kolekci pomocí `elements[symbol]` v C#.

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

Následující příklad místo <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> toho používá metodu rychle najít položku podle klíče.

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a>Přístup ke kolekci pomocí jazyka LINQ

LINQ (Language-Integrated Query) lze použít pro přístup k kolekcím. Linq dotazy poskytují možnosti filtrování, řazení a seskupování. Další informace naleznete [v tématu Začínáme s LINQ v C#](linq/index.md).

Následující příklad spustí dotaz LINQ `List`proti obecnému . Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a>Řazení kolekce

Následující příklad ilustruje postup pro řazení kolekce. Příklad seřadí instance `Car` třídy, které <xref:System.Collections.Generic.List%601>jsou uloženy v . Třída `Car` implementuje <xref:System.IComparable%601> rozhraní, které <xref:System.IComparable%601.CompareTo%2A> vyžaduje, aby byla metoda implementována.

Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá pro řazení. Kód napsaný uživatelem v metodě `CompareTo` vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt, a nula, pokud jsou stejné. To umožňuje definovat v kódu kritéria pro větší než, menší než a rovné.

V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> způsobí, `CompareTo` že metoda má `Car` být volána automaticky pro objekty v `List`.

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a>Definice vlastní kolekce

Můžete definovat kolekci <xref:System.Collections.Generic.IEnumerable%601> implementací <xref:System.Collections.IEnumerable> rozhraní nebo.

I když můžete definovat vlastní kolekci, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, které jsou popsány v [druhy kolekcí](#BKMK_KindsOfCollections) dříve v tomto tématu.

Následující příklad definuje vlastní třídu `AllColors`kolekce s názvem . Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, <xref:System.Collections.IEnumerable.GetEnumerator%2A> které vyžaduje, aby byla metoda implementována.

Metoda `GetEnumerator` vrátí instanci `ColorEnumerator` třídy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které <xref:System.Collections.IEnumerator.Current%2A> vyžaduje, <xref:System.Collections.IEnumerator.MoveNext%2A> aby <xref:System.Collections.IEnumerator.Reset%2A> byla implementována vlastnost, metoda a metoda.

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a>Iterátory

*Iterátor* se používá k provedení vlastní iterace přes kolekci. Iterátor může být metoda nebo `get` přistupující objekt. Iterátor používá yield [return](../../language-reference/keywords/yield.md) prohlášení vrátit každý prvek kolekce jeden po druhém.

Volání iterátorpomocí [foreach](../../language-reference/keywords/foreach-in.md) prohlášení. Každá iterace `foreach` smyčky volá iterátor. Když `yield return` je dosaženo příkazu v iterátoru, je vrácen výraz a aktuální umístění v kódu je zachováno. Spuštění je restartován z tohoto umístění při příštím volání iterátoru.

Další informace naleznete v tématu [Iterátory (C#)](./iterators.md).

Následující příklad používá metodu iterátoru. Metoda iterátoru `yield return` má příkaz, který je uvnitř [for](../../language-reference/keywords/for.md) smyčky. V `ListEvenNumbers` metodě každá iterace těla příkazu `foreach` vytvoří volání iterátoru `yield return` metody, která pokračuje na další příkaz.

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a>Viz také

- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)
- [Koncepty programování (C#)](./index.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ na objekty (C#)](./linq/linq-to-objects.md)
- [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [Kolekce a datové struktury](../../../standard/collections/index.md)
- [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)
- [Porovnávání a řazení v kolekcích](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kdy použít generické kolekce](../../../standard/collections/when-to-use-generic-collections.md)
