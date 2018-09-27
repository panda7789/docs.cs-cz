---
title: Kolekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 60519de1f580bf1cfa4aa067d4a999b20ea8d54d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399395"
---
# <a name="collections-visual-basic"></a>Kolekce (Visual Basic)
U mnoha aplikací chcete vytvářet a spravovat skupiny souvisejících objektů. Existují dva způsoby, jak seskupit objekty: vytvořením polí objektů a vytvořením kolekcí objektů.  
  
 Pole jsou zvláště užitečná pro vytváření a práci s pevným počtem silně typovaných objektů. Informace o polích naleznete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Kolekce poskytují pružnější způsob práce se skupinami objektů. Na rozdíl od pole skupiny objektů, které při práci s můžete zvětšení a zmenšení dynamicky podle potřeb změn aplikace. Pro některé kolekce můžete přiřadit klíč na libovolný objekt, který vložíte do kolekce, takže můžete snadno obnovit objekt pomocí klíče.  
  
 Kolekce je třída, proto je třeba deklarovat instanci třídy, než budete moct přidat prvky do této kolekce.  
  
 Pokud kolekce obsahuje prvky pouze jednoho datového typu, můžete použít jednu z tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecná kolekce vynucuje bezpečnost typů tak, aby žádný jiný typ dat můžete do ní přidá. Při načítání elementu z obecné kolekce není nutné zjistit jeho typ dat nebo ji převést.  
  
> [!NOTE]
>  Příklady v tomto tématu, zahrnují [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) příkazů `System.Collections.Generic` a `System.Linq` obory názvů.  
  
 **V tomto tématu**  
  
-   [Používání jednoduché kolekce](#BKMK_SimpleCollection)  
  
-   [Typy kolekcí](#BKMK_KindsOfCollections)  
  
    -   [Třídy System.Collections.Generic](#BKMK_Generic)  
  
    -   [Třídy System.Collections.Concurrent](#BKMK_Concurrent)  
  
    -   [Třídy System.Collections](#BKMK_Collections)  
  
    -   [Třídy kolekce jazyka Visual Basic](#BKMK_VisualBasic)  
  
-   [Implementace kolekce párů klíč/hodnota](#BKMK_KeyValuePairs)  
  
-   [Přístup ke kolekci pomocí jazyka LINQ](#BKMK_LINQ)  
  
-   [Řazení kolekce](#BKMK_Sorting)  
  
-   [Definice vlastní kolekce](#BKMK_CustomCollection)  
  
-   [Iterátory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce  
 Příklady v této části použít obecný <xref:System.Collections.Generic.List%601> třídu, která umožňuje pracovat s výrazným seznamem objektů.  
  
 Následující příklad vytvoří seznam řetězců a provede iteraci řetězců pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkazu.  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Pokud obsah kolekce znám předem, můžete použít *inicializátor kolekce* pro inicializace kolekce. Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 Následující příklad je stejný jako předchozí příklad, s výjimkou inicializátoru kolekce je použít k přidání prvků do kolekce.  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Můžete použít [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz místo `For Each` příkaz pro iteraci prostřednictvím kolekce. Toto dokončíte pomocí přístupu k elementům kolekce pomocí indexu umístění. Index prvků začíná hodnotou 0 a končí počtem prvků mínus 1.  
  
 Následující příklad provede iteraci prvků kolekce pomocí `For…Next` místo `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Následující příklad odstraní prvek z kolekce zadáním objektu, který chcete odebrat.  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 Následující příklad odebere prvky z obecného seznamu. Místo `For Each` příkaz, [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) se používá s itinerací v sestupném pořadí. Je to proto, <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 Pro typ prvků v <xref:System.Collections.Generic.List%601>, můžete také definovat své vlastní třídy. V následujícím příkladu `Galaxy` třídu, která se používá <xref:System.Collections.Generic.List%601> je definována v kódu.  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a>Typy kolekcí   
 Mnoho nejběžnějších kolekcí jsou k dispozici v rozhraní .NET Framework. Každý typ kolekce je navržená pro určitý účel.  
  
 V této části jsou popsány některé běžné třídy kolekce:  
  
-   <xref:System.Collections.Generic> Třídy  
  
-   <xref:System.Collections.Concurrent> Třídy  
  
-   <xref:System.Collections> Třídy  
  
-   Visual Basic `Collection` třídy  
  
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
  
 Další informace najdete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md), a <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
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

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Třída Collection v jazyce Visual Basic  
 Můžete použít Visual Basic <xref:Microsoft.VisualBasic.Collection> třídy pro přístup položky kolekce pomocí numerického indexu nebo `String` klíč. Přidat položky do objektu kolekce s nebo bez udání klíče. Pokud chcete přidat položku bez klíče, musíte použít jeho číselný index k němu přistupovat.  
  
 Visual Basic `Collection` třída uchovává všechny prvky jako typ `Object`, takže můžete přidat položky libovolného datového typu. Neexistuje žádná ochrana proti přidání typů nevhodných dat.  
  
 Při použití jazyka Visual Basic `Collection` obsahuje třídy, první položku v kolekci index 1. Tím se liší od kolekcí tříd rozhraní .NET Framework, pro které je počáteční index 0.  
  
 Kdykoli je to možné, použijte obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> místo jazyka Visual Basic `Collection` třídy.  
  
 Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Collection>.  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota   
 <xref:System.Collections.Generic.Dictionary%602> Obecné kolekce umožňuje přístup k prvkům kolekce pomocí klíče každého prvku. Každé přidání do slovníku se skládá z hodnoty a odpovídajícího klíče. Načítání hodnoty pomocí obsaženého klíče je velmi rychle, protože `Dictionary` třídy je implementovaný jako zatřiďovací tabulku.  
  
 Následující příklad vytvoří `Dictionary` kolekce a iteruje ve slovníku s využitím `For Each` příkazu.  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 Místo toho použít inicializátor kolekce k sestavení `Dictionary` kolekci, můžete nahradit `BuildDictionary` a `AddToDictionary` metody pomocí následujících metod.  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 V následujícím příkladu <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metoda a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` pro rychlé vyhledání položky podle klíče. `Item` Vlastnost umožňuje přístup k položce v `elements` kolekce s použitím `elements(symbol)` kód v jazyce Visual Basic.  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 Následující příklad používá místo toho <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda rychlé vyhledání položky podle klíče.  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a>Přístup ke kolekci pomocí jazyka LINQ  
 LINQ (Language-Integrated Query) lze použít pro přístup ke kolekci. Dotazy LINQ poskytují možnost filtrování, řazení a seskupování schopností. Další informace najdete v tématu [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Následující příklad spustí dotaz LINQ v rámci obecného `List`. Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a>Řazení kolekce  
 Následující příklad ukazuje postup při řazení kolekce. Příklad řadí instance třídy `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>. `Car` Implementuje třída <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> implementaci metody.  
  
 Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda provádí jedno porovnání, který se používá pro řazení. Uživatelem zapsaný kód v `CompareTo` metoda vrátí hodnotu pro všechna porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud se aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula jestli jsou shodné. To umožňuje v kódu definovat kritéria pro větší, menší než a rovná.  
  
 V `ListCars` metody, `cars.Sort()` příkaz Seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda bude automaticky volána pro `Car` objekty v `List`.  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a>Definice vlastní kolekce  
 Můžete definovat kolekce implementací <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable> rozhraní. Další informace najdete v tématu [vytvoření výčtu kolekce](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 Přestože můžete definovat vlastní kolekci, je obvykle vhodnější použít namísto toho kolekce, které jsou zahrnuty v rozhraní .NET Framework, které jsou popsány v [typy kolekcí](#kinds-of-collections) výše v tomto tématu.  
  
 Následující příklad definuje vlastní třídu kolekce s názvem `AllColors`. Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> implementaci metody.  
  
 `GetEnumerator` Metoda vrací instanci `ColorEnumerator` třídy. `ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerator.Current%2A> vlastnost <xref:System.Collections.IEnumerator.MoveNext%2A> metoda, a <xref:System.Collections.IEnumerator.Reset%2A> implementaci metody.  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a>Iterátory  
 *Iterátoru* se používá k provedení vlastní iterace nad kolekcí. Iterátor může být metoda nebo `get` přistupujícího objektu. Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz k vrácení každého prvku kolekce jeden po druhém.  
  
 Můžete volat iterátor pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkazu. Každá iterace `For Each` smyčky volá iterátor. Když `Yield` je dosažen příkaz v iterátoru, je vrácen výraz a je zachováno aktuální umístění v kódu. Provádění je restartováno z tohoto umístění při příštím volání iterátoru.  
  
 Další informace najdete v tématu [iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 Následující příklad používá metodu iterátoru. Iterační metoda obsahuje `Yield` , který se nachází uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. V `ListEvenNumbers` metodě, každé iterace `For Each` tělo s příkazy vytvoří volání metody iterátoru, který pokračuje k dalšímu `Yield` příkazu.  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a>Viz také:

- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
- [Koncepty programování (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)  
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
- [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [Kolekce a datové struktury](../../../standard/collections/index.md)  
- [Vytváření a manipulace s kolekcemi](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)  
- [Porovnávání a řazení v kolekcích](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [Kdy použít generické kolekce](../../../standard/collections/when-to-use-generic-collections.md)
