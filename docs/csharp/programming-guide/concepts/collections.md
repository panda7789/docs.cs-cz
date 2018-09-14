---
title: Kolekce (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 24b2155c07b6b66820d373d6310ff6b1c6ab224f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527444"
---
# <a name="collections-c"></a>Kolekce (C#)
U mnoha aplikací chcete vytvářet a spravovat skupiny souvisejících objektů. Existují dva způsoby, jak seskupit objekty: vytvořením polí objektů a vytvořením kolekcí objektů.  
  
 Pole jsou zvláště užitečná pro vytváření a práci s pevným počtem silně typovaných objektů. Informace o polích naleznete v tématu [pole](../../../csharp/programming-guide/arrays/index.md).  
  
 Kolekce poskytují pružnější způsob práce se skupinami objektů. Na rozdíl od pole skupiny objektů, které při práci s můžete zvětšení a zmenšení dynamicky podle potřeb změn aplikace. Pro některé kolekce můžete přiřadit klíč na libovolný objekt, který vložíte do kolekce, takže můžete snadno obnovit objekt pomocí klíče.  
  
 Kolekce je třída, proto je třeba deklarovat instanci třídy, než budete moct přidat prvky do této kolekce.  
  
 Pokud kolekce obsahuje prvky pouze jednoho datového typu, můžete použít jednu z tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecná kolekce vynucuje bezpečnost typů tak, aby žádný jiný typ dat můžete do ní přidá. Při načítání elementu z obecné kolekce není nutné zjistit jeho typ dat nebo ji převést.  
  
> [!NOTE]
>  U příkladů v tomto tématu, zahrnují [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy pro `System.Collections.Generic` a `System.Linq` obory názvů.  
  
 **V tomto tématu**  
  
-   [Používání jednoduché kolekce](#BKMK_SimpleCollection)  
  
-   [Typy kolekcí](#BKMK_KindsOfCollections)  
  
    -   [Třídy System.Collections.Generic](#BKMK_Generic)  
  
    -   [Třídy System.Collections.Concurrent](#BKMK_Concurrent)  
  
    -   [Třídy System.Collections](#BKMK_Collections)  
  
-   [Implementace kolekce párů klíč/hodnota](#BKMK_KeyValuePairs)  
  
-   [Přístup ke kolekci pomocí jazyka LINQ](#BKMK_LINQ)  
  
-   [Řazení kolekce](#BKMK_Sorting)  
  
-   [Definice vlastní kolekce](#BKMK_CustomCollection)  
  
-   [Iterátory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce  
 Příklady v této části použít obecný <xref:System.Collections.Generic.List%601> třídu, která umožňuje pracovat s výrazným seznamem objektů.  
  
 Následující příklad vytvoří seznam řetězců a provede iteraci řetězců pomocí nebo [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkazu.  
  
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
  
 Pokud obsah kolekce znám předem, můžete použít *inicializátor kolekce* pro inicializace kolekce. Další informace najdete v tématu [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Následující příklad je stejný jako předchozí příklad, s výjimkou inicializátoru kolekce je použít k přidání prvků do kolekce.  
  
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
  
 Můžete použít [pro](../../../csharp/language-reference/keywords/for.md) příkaz místo `foreach` příkaz pro iteraci prostřednictvím kolekce. Toto dokončíte pomocí přístupu k elementům kolekce pomocí indexu umístění. Index prvků začíná hodnotou 0 a končí počtem prvků mínus 1.  
  
 Následující příklad provede iteraci prvků kolekce pomocí `for` místo `foreach`.  
  
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
  
 Následující příklad odstraní prvek z kolekce zadáním objektu, který chcete odebrat.  
  
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
  
 Následující příklad odebere prvky z obecného seznamu. Místo `foreach` příkaz, [pro](../../../csharp/language-reference/keywords/for.md) se používá s itinerací v sestupném pořadí. Je to proto, <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.  
  
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
  
 Pro typ prvků v <xref:System.Collections.Generic.List%601>, můžete také definovat své vlastní třídy. V následujícím příkladu `Galaxy` třídu, která se používá <xref:System.Collections.Generic.List%601> je definována v kódu.  
  
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
 Mnoho nejběžnějších kolekcí jsou k dispozici v rozhraní .NET Framework. Každý typ kolekce je navržená pro určitý účel.  
  
 V této části jsou popsány některé běžné třídy kolekce:  
  
-   <xref:System.Collections.Generic> Třídy  
  
-   <xref:System.Collections.Concurrent> Třídy  
  
-   <xref:System.Collections> Třídy  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>Třídy System.Collections.Generic  
 Obecnou kolekci můžete vytvořit pomocí jedné ze tříd v <xref:System.Collections.Generic> oboru názvů. Obecná kolekce je užitečná, když má každá položka v kolekci stejný datový typ. Obecná kolekce vynucuje silné typování tím, že pouze žádaného datového typu.  
  
 Následující tabulka uvádí některé často používané třídy <xref:System.Collections.Generic?displayProperty=nameWithType> obor názvů:  

|Třída|Popis| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Představuje kolekci dvojic klíč/hodnota, které jsou uspořádány na základě klíče.|  
|<xref:System.Collections.Generic.List%601>|Reprezentuje seznam objektů, které lze využívat pomocí indexu. Poskytuje metody pro vyhledávání, řazení a úpravu seznamů.|  
|<xref:System.Collections.Generic.Queue%601>|Představuje first-in-first-out (FIFO) kolekci objektů.|  
|<xref:System.Collections.Generic.SortedList%602>|Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.|  
|<xref:System.Collections.Generic.Stack%601>|Představuje last-in-first-out (LIFO) kolekci objektů.|  
  
 Další informace najdete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md), a <xref:System.Collections.Generic>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>Třídy System.Collections.Concurrent  
 V rozhraní .NET Framework 4 nebo novější, kolekce v <xref:System.Collections.Concurrent> obor názvů poskytují efektivní operace bezpečné pro vlákna pro přístup položky kolekce z více vláken.  
  
 Třídy v <xref:System.Collections.Concurrent> oboru názvů by měl použít namísto odpovídajících typů v <xref:System.Collections.Generic?displayProperty=nameWithType> a <xref:System.Collections?displayProperty=nameWithType> obory názvů pokaždé, když přistupuje více podprocesů kolekci současně. Další informace najdete v tématu [kolekce bezpečné pro vlákna](../../../standard/collections/thread-safe/index.md) a <xref:System.Collections.Concurrent>.  
  
 Některé třídy v <xref:System.Collections.Concurrent> obor názvů jsou <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>Třídy System.Collections  
 Třídy v <xref:System.Collections?displayProperty=nameWithType> obor názvů neukládají prvky jako objekty s konkrétním typem, ale jako objekty typu `Object`.  
  
 Kdykoli je to možné, použijte obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> místo třídy zastaralých typů v `System.Collections` oboru názvů.  
  
 Následující tabulka uvádí některé často používané třídy v `System.Collections` obor názvů:  
  
|Třída|Popis|  
|---|---|  
|<xref:System.Collections.ArrayList>|Představuje pole objektů, jejichž velikost se dynamicky mění jako povinné.|  
|<xref:System.Collections.Hashtable>|Představuje kolekci párů klíč/hodnota, které jsou uspořádány na základě kódu hodnoty hash klíče.|  
|<xref:System.Collections.Queue>|Představuje first-in-first-out (FIFO) kolekci objektů.|  
|<xref:System.Collections.Stack>|Představuje last-in-first-out (LIFO) kolekci objektů.|  
  
 <xref:System.Collections.Specialized> Obor názvů obsahuje třídy specializované a typově silné kolekcí, jako je například kolekce pouze pro řetězce a propojené seznamy a hybridní slovníky.  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota  
 <xref:System.Collections.Generic.Dictionary%602> Obecné kolekce umožňuje přístup k prvkům kolekce pomocí klíče každého prvku. Každé přidání do slovníku se skládá z hodnoty a odpovídajícího klíče. Načítání hodnoty pomocí obsaženého klíče je velmi rychle, protože `Dictionary` třídy je implementovaný jako zatřiďovací tabulku.  
  
 Následující příklad vytvoří `Dictionary` kolekce a iteruje ve slovníku s využitím `foreach` příkazu.  
  
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
  
 Místo toho použít inicializátor kolekce k sestavení `Dictionary` kolekci, můžete nahradit `BuildDictionary` a `AddToDictionary` metody pomocí následujících metod.  
  
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
  
 V následujícím příkladu <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metoda a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` pro rychlé vyhledání položky podle klíče. `Item` Vlastnost umožňuje přístup k položce v `elements` kolekce s použitím `elements[symbol]` v jazyce C#.  
  
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
  
 Následující příklad používá místo toho <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda rychlé vyhledání položky podle klíče.  
  
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
 LINQ (Language-Integrated Query) lze použít pro přístup ke kolekci. Dotazy LINQ poskytují možnost filtrování, řazení a seskupování schopností. Další informace najdete v tématu [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Následující příklad spustí dotaz LINQ v rámci obecného `List`. Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.  
  
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
 Následující příklad ukazuje postup při řazení kolekce. Příklad řadí instance třídy `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>. `Car` Implementuje třída <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> implementaci metody.  
  
 Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda provádí jedno porovnání, který se používá pro řazení. Uživatelem zapsaný kód v `CompareTo` metoda vrátí hodnotu pro všechna porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud se aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula jestli jsou shodné. To umožňuje v kódu definovat kritéria pro větší, menší než a rovná.  
  
 V `ListCars` metody, `cars.Sort()` příkaz Seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda bude automaticky volána pro `Car` objekty v `List`.  
  
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
 Můžete definovat kolekce implementací <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable> rozhraní.  
  
 Přestože můžete definovat vlastní kolekci, je obvykle vhodnější použít namísto toho kolekce, které jsou zahrnuty v rozhraní .NET Framework, které jsou popsány v [typy kolekcí](#BKMK_KindsOfCollections) výše v tomto tématu.  
  
 Následující příklad definuje vlastní třídu kolekce s názvem `AllColors`. Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> implementaci metody.  
  
 `GetEnumerator` Metoda vrací instanci `ColorEnumerator` třídy. `ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerator.Current%2A> vlastnost <xref:System.Collections.IEnumerator.MoveNext%2A> metoda, a <xref:System.Collections.IEnumerator.Reset%2A> implementaci metody.  
  
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
##  <a name="iterators"></a>Iterátory  
 *Iterátoru* se používá k provedení vlastní iterace nad kolekcí. Iterátor může být metoda nebo `get` přistupujícího objektu. Iterátor používá [yield return](../../../csharp/language-reference/keywords/yield.md) příkaz k vrácení každého prvku kolekce jeden po druhém.  
  
 Můžete volat iterátor pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkazu. Každá iterace `foreach` smyčky volá iterátor. Když `yield return` je dosažen příkaz v iterátoru, je vrácen výraz a je zachováno aktuální umístění v kódu. Provádění je restartováno z tohoto umístění při příštím volání iterátoru.  
  
 Další informace najdete v tématu [iterátory (C#)](../../../csharp/programming-guide/concepts/iterators.md).  
  
 Následující příklad používá metodu iterátoru. Iterační metoda obsahuje `yield return` , který se nachází uvnitř [pro](../../../csharp/language-reference/keywords/for.md) smyčky. V `ListEvenNumbers` metodě, každé iterace `foreach` tělo s příkazy vytvoří volání metody iterátoru, který pokračuje k dalšímu `yield return` příkazu.  
  
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

- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [Koncepty programování (C#)](../../../csharp/programming-guide/concepts/index.md)  
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [LINQ to Objects (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [Kolekce a datové struktury](../../../standard/collections/index.md)  
- [Vytváření a manipulace s kolekcemi](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)  
- [Porovnávání a řazení v kolekcích](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [Kdy použít generické kolekce](../../../standard/collections/when-to-use-generic-collections.md)  
