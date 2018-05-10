---
title: Kolekce (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 85cbabf74a702a4d6442a29c3cf3d7b726ab38da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="collections-c"></a>Kolekce (C#)
Mnoho aplikací budete chtít vytvořit a spravovat skupiny související objekty. Existují dva způsoby do objektů skupiny: vytvořením pole objektů a vytvořením kolekce objektů.  
  
 Pole jsou velmi užitečné pro vytváření a práci s pevný počet objektů se silným typem. Informace o polích najdete v tématu [pole](../../../csharp/programming-guide/arrays/index.md).  
  
 Kolekce poskytují flexibilnější způsob, jak pracovat s skupiny objektů. Na rozdíl od pole skupinu objektů, které pracujete s můžete zvýšit nebo snížit dynamicky potřebám změna aplikace. Pro některé kolekce můžete přiřadit klíč pro libovolný objekt, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.  
  
 Kolekce je třída, takže instance třídy musí deklarovat, než budete moct přidat do této kolekce elementů.  
  
 Pokud kolekce obsahuje prvky pouze jeden datový typ, můžete použít jednu z tříd ve <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecné kolekce vynucuje bezpečnost typů tak, aby žádný datový typ lze přidat do ní. Při načítání element z obecnou kolekci, není nutné určit její datový typ nebo je převeďte.  
  
> [!NOTE]
>  Příklady v tomto tématu, zahrnují [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy pro `System.Collections.Generic` a `System.Linq` obory názvů.  
  
 **V tomto tématu**  
  
-   [Pomocí jednoduchých kolekcí](#BKMK_SimpleCollection)  
  
-   [Typy kolekcí](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic – třídy](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent třídy](#BKMK_Concurrent)  
  
    -   [System.Collections – třídy](#BKMK_Collections)  
  
-   [Implementace kolekci dvojic klíč/hodnota](#BKMK_KeyValuePairs)  
  
-   [Pro přístup k kolekci pomocí LINQ](#BKMK_LINQ)  
  
-   [Řazení kolekce](#BKMK_Sorting)  
  
-   [Definování vlastní kolekce](#BKMK_CustomCollection)  
  
-   [Iterátory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce  
 Příklady v této části použijte Obecné <xref:System.Collections.Generic.List%601> třídy, která umožňuje pracovat s silného typu seznamu objektů.  
  
 Následující příklad vytvoří seznam řetězců a pak iteruje řetězce pomocí nebo [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz.  
  
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
  
 Pokud obsah kolekce jsou známy předem, můžete použít *inicializátoru kolekce* k chybě při inicializaci kolekce. Další informace najdete v tématu [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Následující příklad je stejný jako předchozí příklad, s výjimkou inicializátoru kolekce se používá k přidání prvků do kolekce.  
  
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
  
 Můžete použít [pro](../../../csharp/language-reference/keywords/for.md) příkaz místo `foreach` příkaz k iteraci v rámci kolekce. Můžete dosáhnout díky přístupu k elementy v kolekci podle umístění indexu. Index elementů začíná na 0 a končí na počet elementu minus 1.  
  
 V následujícím příkladu prochází prvků kolekce pomocí `for` místo `foreach`.  
  
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
  
 Následující příklad odebere element z kolekce zadáním objekt, který chcete odebrat.  
  
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
  
 Následující příklad odebere seznam obecné elementy. Místo `foreach` příkaz, [pro](../../../csharp/language-reference/keywords/for.md) se použije příkaz, který iteruje v sestupném pořadí. Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebrané element s nižší hodnotou indexu.  
  
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
  
 Pro typ elementů v <xref:System.Collections.Generic.List%601>, je možné definovat také vlastní třídu. V následujícím příkladu `Galaxy` třídu, která je používána <xref:System.Collections.Generic.List%601> je definována v kódu.  
  
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
 Mnoho běžných kolekcí jsou poskytovány rozhraní .NET Framework. Každý typ kolekce je určená pro konkrétní účel.  
  
 V této části jsou popsány některé běžné třídy kolekce:  
  
-   <xref:System.Collections.Generic> Třídy  
  
-   <xref:System.Collections.Concurrent> Třídy  
  
-   <xref:System.Collections> Třídy  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>Třídy System.Collections.Generic  
 Můžete vytvořit obecnou kolekci pomocí jedné z třídy v <xref:System.Collections.Generic> oboru názvů. Obecné kolekce je užitečné, když každá položka v kolekci má stejný datový typ. Obecné kolekce vynucuje silného typování tím, že se pouze k požadovaným datům typ, který má být přidán.  
  
 Následující tabulka uvádí některé často používané třídy <xref:System.Collections.Generic?displayProperty=nameWithType> obor názvů:  

|Třída|Popis| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Představuje kolekci páry klíč/hodnota, která jsou uspořádána podle klíče.|  
|<xref:System.Collections.Generic.List%601>|Reprezentuje seznam objektů, kterým lze přistupovat pomocí indexu. Poskytuje metody pro vyhledávání, řazení a upravit seznamy.|  
|<xref:System.Collections.Generic.Queue%601>|Představuje první in, out (FIFO) první kolekce objektů.|  
|<xref:System.Collections.Generic.SortedList%602>|Představuje kolekci párů klíč/hodnota, které jsou seřazeny podle klíče na základě přidružené <xref:System.Collections.Generic.IComparer%601> implementace.|  
|<xref:System.Collections.Generic.Stack%601>|Představuje poslední in, out (LIFO) první kolekce objektů.|  
  
 Další informace najdete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md), a <xref:System.Collections.Generic>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>Třídy System.Collections.Concurrent  
 V rozhraní .NET Framework 4 nebo novější, kolekce v <xref:System.Collections.Concurrent> obor názvů poskytují efektivní operace vláken pro přístup k položkám kolekce z více vláken.  
  
 Třídy v <xref:System.Collections.Concurrent> místo odpovídající typy v by použít obor názvů <xref:System.Collections.Generic?displayProperty=nameWithType> a <xref:System.Collections?displayProperty=nameWithType> obory názvů vždy, když přistupují více vláken kolekce souběžně. Další informace najdete v tématu [kolekce se zabezpečenými vlákny](../../../standard/collections/thread-safe/index.md) a <xref:System.Collections.Concurrent>.  
  
 Některé třídy součástí <xref:System.Collections.Concurrent> obor názvů jsou <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections – třídy  
 Třídy v <xref:System.Collections?displayProperty=nameWithType> obor názvů neukládají prvky s konkrétním typem objekty, ale jako objekty typu `Object`.  
  
 Kdykoli je to možné, měli byste použít obecné kolekce z <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> obor názvů místo starší verze typů v `System.Collections` oboru názvů.  
  
 Následující tabulka uvádí některé často používaných tříd v `System.Collections` obor názvů:  
  
|Třída|Popis|  
|---|---|  
|<xref:System.Collections.ArrayList>|Představuje požadované pole objektů, jejichž velikost se dynamicky mění jako.|  
|<xref:System.Collections.Hashtable>|Představuje kolekci páry klíč/hodnota, která jsou uspořádána podle hodnota hash klíče.|  
|<xref:System.Collections.Queue>|Představuje první in, out (FIFO) první kolekce objektů.|  
|<xref:System.Collections.Stack>|Představuje poslední in, out (LIFO) první kolekce objektů.|  
  
 <xref:System.Collections.Specialized> Obor názvů obsahuje třídy specializované a silného typu kolekce, jako je například kolekce pouze pro řetězce a -list a hybridní slovníky.  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota  
 <xref:System.Collections.Generic.Dictionary%602> Obecnou kolekci umožňuje přístup k elementů v kolekci pomocí klíče jednotlivých prvků. Každý přidání do slovníku se skládá z hodnotu a jeho přidružený klíč. Načítání hodnoty pomocí jeho klíče je rychlé, protože `Dictionary` třída je implementovaný jako zatřiďovací tabulku.  
  
 Následující příklad vytvoří `Dictionary` kolekce a iteruje ve slovníku pomocí `foreach` příkaz.  
  
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
  
 Místo toho použít k sestavení inicializátoru kolekce `Dictionary` kolekce, můžete nahradit `BuildDictionary` a `AddToDictionary` metody s následující metodu.  
  
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
  
 Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metoda a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` rychle najít položku podle klíče. `Item` Vlastnost umožňuje přístup k položce v `elements` kolekce pomocí `elements[symbol]` v jazyce C#.  
  
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
  
 Následující příklad používá místo toho <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda rychle najít položka podle klíče.  
  
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
 LINQ (Language-Integrated Query) slouží pro přístup k kolekce. Dotazy LINQ poskytují filtrování, řazení a seskupování schopností. Další informace najdete v tématu [Začínáme s dotazy LINQ v jazyku C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Následující příklad spouští dotaz LINQ obecný `List`. Dotaz LINQ vrátí do jiné kolekce, který obsahuje výsledky.  
  
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
 Následující příklad ukazuje postup pro řazení kolekce. V příkladu seřadí instance `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>. `Car` Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> být implementována metoda.  
  
 Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda umožňuje jedno porovnání, který se používá pro řazení. Uživatel zapsat kód v `CompareTo` metoda vrátí hodnotu pro každou porovnání aktuální objekt s jiným objektem. Hodnota vrácená je menší než nula. Pokud je aktuální objekt menší než druhý objekt, větší než nula. Pokud se aktuální objekt větší než druhý objekt a nula. Pokud jsou stejné. To umožňuje definovat kritéria pro větší než je menší než v kódu a rovnat.  
  
 V `ListCars` metody `cars.Sort()` příkaz Seřadí seznam. Volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda má být automaticky volána pro `Car` objekty v `List`.  
  
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
 Kolekce můžete definovat implementací <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable> rozhraní. Další informace najdete v tématu [postupy: přístup ke třídě kolekce pomocí příkazu foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).  
  
 I když můžete definovat vlastní kolekce, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, která jsou popsaná v [typy kolekcí](#BKMK_KindsOfCollections) výše v tomto tématu.  
  
 Následující příklad definuje třídu vlastní kolekci s názvem `AllColors`. Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> být implementována metoda.  
  
 `GetEnumerator` Metoda vrací instanci třídy `ColorEnumerator` třídy. `ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerator.Current%2A> vlastnost <xref:System.Collections.IEnumerator.MoveNext%2A> metody a <xref:System.Collections.IEnumerator.Reset%2A> být implementována metoda.  
  
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
 *Iterator* se používá k provedení vlastní iteraci přes kolekci. Iterace může být metodou nebo `get` přistupujícího objektu. Používá iterovat [yield vrátit](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit každý prvek kolekce, jeden v čase.  
  
 Volání iterovat pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz. Každé iteraci `foreach` volá iteraci smyčky. Když `yield return` příkaz je dosaženo v iteraci, je vrácen výraz a se uchovávají aktuální umístění v kódu. Provádění restartování z tohoto umístění příštím iteraci je volána.  
  
 Další informace najdete v tématu [iterátory (C#)](../../../csharp/programming-guide/concepts/iterators.md).  
  
 Následující příklad používá metodu iterator. Metoda iterator má `yield return` příkaz, který je uvnitř [pro](../../../csharp/language-reference/keywords/for.md) smyčky. V `ListEvenNumbers` metoda, každé iteraci `foreach` těla příkazu vytvoří volání metody iterator, která bude pokračovat na další `yield return` příkaz.  
  
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
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Programování konceptů (C#)](../../../csharp/programming-guide/concepts/index.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [LINQ na objekty (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [Kolekce a datové struktury](../../../standard/collections/index.md)  
 [Vytváření a manipulace s kolekcí](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)  
 [Porovnávání a řazení v kolekcích](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [Kdy použít generické kolekce](../../../standard/collections/when-to-use-generic-collections.md)  
 [Postupy: Přístup ke třídě kolekce pomocí příkazu foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)
