---
title: Kolekce (C#)
description: Seznamte se s kolekcemi v jazyce C#, které jsou používány pro práci se skupinami objektů. Kolekce lze dynamicky zvětšovat a zmenšovat podle potřeby změny aplikace.
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 2375980e2915d4daa5a221a94eee2aea41959852
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924926"
---
# <a name="collections-c"></a>Kolekce (C#)

U mnoha aplikací chcete vytvořit a spravovat skupiny souvisejících objektů. Existují dva způsoby, jak seskupit objekty: vytvořením polí objektů a vytvořením kolekcí objektů.

Pole jsou užitečná pro vytváření a práci s pevným počtem silně typových objektů. Informace o polích naleznete v tématu [Arrays](../arrays/index.md).

Kolekce poskytují pružnější způsob práce se skupinami objektů. Na rozdíl od polí mohou skupiny objektů, se kterými pracujete, dynamicky zvětšovat a zmenšovat podle potřeb změny aplikace. U některých kolekcí můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, abyste mohli rychle načíst objekt pomocí klíče.

Kolekce je třída, takže před přidáním prvků do této kolekce je nutné deklarovat instanci třídy.

Pokud kolekce obsahuje prvky pouze jednoho typu dat, můžete použít jednu ze tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecná kolekce vynutila bezpečnost typů, takže do ní nelze přidat žádný jiný datový typ. Při načítání prvku z obecné kolekce není nutné určit jeho datový typ nebo ho převést.

> [!NOTE]
> Příklady v tomto tématu zahrnují direktivy [using](../../language-reference/keywords/using-directive.md) pro `System.Collections.Generic` `System.Linq` obory názvů a.

 **V tomto tématu**

- [Používání jednoduché kolekce](#BKMK_SimpleCollection)

- [Typy kolekcí](#BKMK_KindsOfCollections)

  - [Třídy System.Collections.Generic](#BKMK_Generic)

  - [Třídy System.Collections.Concurrent](#BKMK_Concurrent)

  - [Třídy System. Collections](#BKMK_Collections)

- [Implementace kolekce párů klíč/hodnota](#BKMK_KeyValuePairs)

- [Přístup ke kolekci pomocí jazyka LINQ](#BKMK_LINQ)

- [Řazení kolekce](#BKMK_Sorting)

- [Definice vlastní kolekce](#BKMK_CustomCollection)

- [Iterátory](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce

Příklady v této části používají obecnou <xref:System.Collections.Generic.List%601> třídu, která umožňuje pracovat se seznamem objektů se silným typem.

Následující příklad vytvoří seznam řetězců a pak prochází řetězce pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) .

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

Pokud je obsah kolekce znám předem, můžete kolekci inicializovat pomocí *inicializátoru kolekce* . Další informace naleznete v tématu [Inicializátory objektů a kolekcí](../classes-and-structs/object-and-collection-initializers.md).

Následující příklad je stejný jako předchozí příklad, s výjimkou, že inicializátor kolekce se používá pro přidání prvků do kolekce.

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

Můžete použít příkaz [for](../../language-reference/keywords/for.md) namísto `foreach` příkazu pro iteraci v kolekci. Toho dosáhnete přístupem k prvkům kolekce na pozici indexu. Index prvků začíná na 0 a končí v počtu elementů minus 1.

Následující příklad provede iteraci prvků kolekce pomocí `for` místo `foreach` .

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

Následující příklad odebere prvek z kolekce zadáním objektu, který chcete odebrat.

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

Následující příklad odstraní prvky z obecného seznamu. Místo příkazu se `foreach` používá příkaz [for](../../language-reference/keywords/for.md) , který iteruje v sestupném pořadí. Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.

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

Pro typ prvků v <xref:System.Collections.Generic.List%601> , můžete také definovat vlastní třídu. V následujícím příkladu `Galaxy` třída, která je použita v, <xref:System.Collections.Generic.List%601> je definována v kódu.

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

Rozhraní .NET poskytuje mnoho běžných kolekcí. Každý typ kolekce je navržený pro konkrétní účel.

Některé společné třídy kolekcí jsou popsány v této části:

- <xref:System.Collections.Generic> – třídy

- <xref:System.Collections.Concurrent> – třídy

- <xref:System.Collections> – třídy

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a>Třídy System.Collections.Generic

Můžete vytvořit obecnou kolekci pomocí jedné ze tříd v <xref:System.Collections.Generic> oboru názvů. Obecná kolekce je užitečná, pokud má každá položka v kolekci stejný datový typ. Obecná kolekce vynutila silné typování tím, že umožňuje přidat pouze požadovaný datový typ.

V následující tabulce jsou uvedeny některé z často používaných tříd <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů:

|Třída|Popis|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě klíče.|
|<xref:System.Collections.Generic.List%601>|Představuje seznam objektů, které mohou být k dispozici v indexu. Poskytuje metody pro hledání, řazení a úpravy seznamů.|
|<xref:System.Collections.Generic.Queue%601>|Představuje kolekci objektů first in, First out (FIFO).|
|<xref:System.Collections.Generic.SortedList%602>|Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.|
|<xref:System.Collections.Generic.Stack%601>|Představuje kolekci objektů Last in, First out (LIFO).|

Další informace naleznete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic> .

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>Třídy System.Collections.Concurrent

V .NET Framework 4 a novějších verzích kolekce v <xref:System.Collections.Concurrent> oboru názvů poskytují efektivní operace bezpečné pro přístup z více vláken pro přístup k položkám kolekce z více vláken.

Třídy v <xref:System.Collections.Concurrent> oboru názvů by měly být použity namísto odpovídajících typů v <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections?displayProperty=nameWithType> oborech názvů a pokaždé, když více vláken přistupuje souběžně k kolekci. Další informace najdete v tématu [kolekce bezpečné](../../../standard/collections/thread-safe/index.md) pro přístup z více vláken a <xref:System.Collections.Concurrent> .

Některé třídy <xref:System.Collections.Concurrent> , které jsou součástí oboru názvů <xref:System.Collections.Concurrent.BlockingCollection%601> , jsou, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601> .

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a>Třídy System. Collections

Třídy v <xref:System.Collections?displayProperty=nameWithType> oboru názvů neukládají prvky jako specificky typové objekty, ale jako objekty typu `Object` .

Kdykoli je to možné, použijte obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> obor názvů namísto starších typů v `System.Collections` oboru názvů.

Následující tabulka uvádí některé často používané třídy v `System.Collections` oboru názvů:

|Třída|Popis|
|---|---|
|<xref:System.Collections.ArrayList>|Představuje pole objektů, jejichž velikost se dynamicky zvětšuje podle potřeby.|
|<xref:System.Collections.Hashtable>|Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hash klíče.|
|<xref:System.Collections.Queue>|Představuje kolekci objektů first in, First out (FIFO).|
|<xref:System.Collections.Stack>|Představuje kolekci objektů Last in, First out (LIFO).|

<xref:System.Collections.Specialized>Obor názvů poskytuje specializované třídy kolekcí se silnými typy, jako jsou jenom řetězcové kolekce a propojené seznamy a hybridní slovníky.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota

<xref:System.Collections.Generic.Dictionary%602>Obecná kolekce umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku. Každé přidání do slovníku se skládá z hodnoty a jejího přidruženého klíče. Načítání hodnoty pomocí klíče je rychlé, protože `Dictionary` Třída je implementována jako zatřiďovací tabulka.

Následující příklad vytvoří `Dictionary` kolekci a iteruje prostřednictvím slovníku pomocí `foreach` příkazu.

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

Chcete-li místo toho použít inicializátor kolekce k sestavení `Dictionary` kolekce, můžete nahradit `BuildDictionary` metody a `AddToDictionary` následující metodou.

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

Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodu a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` pro rychlé vyhledání položky podle klíče. `Item`Vlastnost umožňuje přístup k položce v `elements` kolekci pomocí `elements[symbol]` jazyka v jazyce C#.

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

Následující příklad místo toho používá <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metodu pro rychlé vyhledání položky podle klíče.

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

LINQ (jazykově integrovaný dotaz) lze použít pro přístup ke kolekcím. Dotazy LINQ poskytují možnosti filtrování, řazení a seskupování. Další informace naleznete v tématu [Začínáme pomocí LINQ v jazyce C#](linq/index.md).

Následující příklad spustí dotaz LINQ na obecné `List` . Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.

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

Následující příklad znázorňuje postup pro řazení kolekce. Příklad řadí instance `Car` třídy, které jsou uloženy v <xref:System.Collections.Generic.List%601> . `Car`Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje <xref:System.IComparable%601.CompareTo%2A> implementaci metody.

Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá k řazení. Uživatelsky psaný kód v `CompareTo` metodě vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula, pokud jsou stejné. To umožňuje definovat v kódu kritéria pro větší než, menší než a rovno.

V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody metody <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` Metoda bude automaticky volána pro `Car` objekty v `List` .

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

Kolekci můžete definovat implementací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> rozhraní nebo.

I když můžete definovat vlastní kolekci, je obvykle vhodnější použít kolekce, které jsou součástí rozhraní .NET, které jsou popsány v [části druhy kolekcí](#BKMK_KindsOfCollections) výše v tomto článku.

Následující příklad definuje vlastní třídu kolekce s názvem `AllColors` . Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> implementaci metody.

`GetEnumerator`Metoda vrátí instanci `ColorEnumerator` třídy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby byla <xref:System.Collections.IEnumerator.Current%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> implementována vlastnost, metoda a <xref:System.Collections.IEnumerator.Reset%2A> metoda.

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

*Iterátor* se používá k provedení vlastní iterace v kolekci. Iterátor může být metoda nebo `get` přistupující objekt. Iterátor používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého prvku kolekce po jednom.

Zavoláte iterátor pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) . Každá iterace `foreach` smyčky volá iterátor. Při `yield return` dosažení příkazu v iterátoru je vrácen výraz a aktuální umístění v kódu je uchováno. Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.

Další informace najdete v tématu [iterátory (C#)](./iterators.md).

Následující příklad používá metodu iterátoru. Metoda iterátoru obsahuje `yield return` příkaz, který je uvnitř smyčky [for](../../language-reference/keywords/for.md) . V `ListEvenNumbers` metodě Každá iterace `foreach` těla příkazu vytvoří volání metody iterátoru, která pokračuje k dalšímu `yield return` příkazu.

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
- [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ to Objects (C#)](./linq/linq-to-objects.md)
- [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/introduction-to-plinq.md)
- [Kolekce a datové struktury](../../../standard/collections/index.md)
- [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)
- [Porovnání a řazení v rámci kolekcí](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kdy použít obecné kolekce](../../../standard/collections/when-to-use-generic-collections.md)
