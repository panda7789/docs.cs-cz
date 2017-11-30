---
title: Kolekce (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: get-started-article
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aac9ed655982ff4618e0bdb7fd2af16aaa546719
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="collections-visual-basic"></a>Kolekce (Visual Basic)
Mnoho aplikací budete chtít vytvořit a spravovat skupiny související objekty. Existují dva způsoby do objektů skupiny: vytvořením pole objektů a vytvořením kolekce objektů.  
  
 Pole jsou velmi užitečné pro vytváření a práci s pevný počet objektů se silným typem. Informace o polích najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Kolekce poskytují flexibilnější způsob, jak pracovat s skupiny objektů. Na rozdíl od pole skupinu objektů, které pracujete s můžete zvýšit nebo snížit dynamicky potřebám změna aplikace. Pro některé kolekce můžete přiřadit klíč pro libovolný objekt, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.  
  
 Kolekce je třída, takže instance třídy musí deklarovat, než budete moct přidat do této kolekce elementů.  
  
 Pokud kolekce obsahuje prvky pouze jeden datový typ, můžete použít jednu z tříd ve <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecné kolekce vynucuje bezpečnost typů tak, aby žádný datový typ lze přidat do ní. Při načítání element z obecnou kolekci, není nutné určit její datový typ nebo je převeďte.  
  
> [!NOTE]
>  Příklady v tomto tématu, zahrnují [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro příkazy `System.Collections.Generic` a `System.Linq` obory názvů.  
  
 **V tomto tématu**  
  
-   [Pomocí jednoduchých kolekcí](#BKMK_SimpleCollection)  
  
-   [Typy kolekcí](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic – třídy](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent třídy](#BKMK_Concurrent)  
  
    -   [System.Collections – třídy](#BKMK_Collections)  
  
    -   [Třída Collection v jazyce Visual Basic](#BKMK_VisualBasic)  
  
-   [Implementace kolekci dvojic klíč/hodnota](#BKMK_KeyValuePairs)  
  
-   [Pro přístup k kolekci pomocí LINQ](#BKMK_LINQ)  
  
-   [Řazení kolekce](#BKMK_Sorting)  
  
-   [Definování vlastní kolekce](#BKMK_CustomCollection)  
  
-   [Iterátory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce  
 Příklady v této části použijte Obecné <xref:System.Collections.Generic.List%601> třídy, která umožňuje pracovat s silného typu seznamu objektů.  
  
 Následující příklad vytvoří seznam řetězců a pak iteruje řetězce pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz.  
  
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
  
 Pokud obsah kolekce jsou známy předem, můžete použít *inicializátoru kolekce* k chybě při inicializaci kolekce. Další informace najdete v tématu [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 Následující příklad je stejný jako předchozí příklad, s výjimkou inicializátoru kolekce se používá k přidání prvků do kolekce.  
  
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
  
 Můžete použít [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz místo `For Each` příkaz k iteraci v rámci kolekce. Můžete dosáhnout díky přístupu k elementy v kolekci podle umístění indexu. Index elementů začíná na 0 a končí na počet elementu minus 1.  
  
 V následujícím příkladu prochází prvků kolekce pomocí `For…Next` místo `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Následující příklad odebere element z kolekce zadáním objekt, který chcete odebrat.  
  
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
  
 Následující příklad odebere seznam obecné elementy. Místo `For Each` příkaz, [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) se použije příkaz, který iteruje v sestupném pořadí. Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebrané element s nižší hodnotou indexu.  
  
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
  
 Pro typ elementů v <xref:System.Collections.Generic.List%601>, je možné definovat také vlastní třídu. V následujícím příkladu `Galaxy` třídu, která je používána <xref:System.Collections.Generic.List%601> je definována v kódu.  
  
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
 Mnoho běžných kolekcí jsou poskytovány rozhraní .NET Framework. Každý typ kolekce je určená pro konkrétní účel.  
  
 V této části jsou popsány některé běžné třídy kolekce:  
  
-   <xref:System.Collections.Generic>třídy  
  
-   <xref:System.Collections.Concurrent>třídy  
  
-   <xref:System.Collections>třídy  
  
-   Visual Basic `Collection` – třída  
  
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
  
 Další informace najdete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md), a <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
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

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Třída Collection v jazyce Visual Basic  
 Můžete použít Visual Basicu <xref:Microsoft.VisualBasic.Collection> třídy pro přístup k kolekce položek pomocí číselný index nebo `String` klíč. Položky můžete přidat do objektu kolekce s nebo bez zadávání klíče. Pokud chcete přidat položku bez klíče, musíte použít jeho číselný index k přístupu.  
  
 Visual Basic `Collection` třída ukládá všechny jeho prvky jako typ `Object`, takže můžete přidat položku jakéhokoli datového typu. Neexistuje žádné zajistí ochranu proti přidávané nevhodných datové typy.  
  
 Při použití Visual Basicu `Collection` třída, první položky v kolekci má index 1. To se liší od tříd rozhraní .NET Framework kolekce, pro které je počáteční index 0.  
  
 Kdykoli je to možné, měli byste použít obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo <xref:System.Collections.Concurrent> obor názvů místo Visual Basicu `Collection` třídy.  
  
 Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Collection>.  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota   
 <xref:System.Collections.Generic.Dictionary%602> Obecnou kolekci umožňuje přístup k elementů v kolekci pomocí klíče jednotlivých prvků. Každý přidání do slovníku se skládá z hodnotu a jeho přidružený klíč. Načítání hodnoty pomocí jeho klíče je rychlé, protože `Dictionary` třída je implementovaný jako zatřiďovací tabulku.  
  
 Následující příklad vytvoří `Dictionary` kolekce a iteruje ve slovníku pomocí `For Each` příkaz.  
  
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
  
 Místo toho použít k sestavení inicializátoru kolekce `Dictionary` kolekce, můžete nahradit `BuildDictionary` a `AddToDictionary` metody s následující metodu.  
  
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
  
 Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metoda a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` rychle najít položku podle klíče. `Item` Vlastnost umožňuje přístup k položce v `elements` kolekce pomocí `elements(symbol)` kód v jazyce Visual Basic.  
  
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
  
 Následující příklad používá místo toho <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda rychle najít položka podle klíče.  
  
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
 LINQ (Language-Integrated Query) slouží pro přístup k kolekce. Dotazy LINQ poskytují filtrování, řazení a seskupování schopností. Další informace najdete v tématu [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Následující příklad spouští dotaz LINQ obecný `List`. Dotaz LINQ vrátí do jiné kolekce, který obsahuje výsledky.  
  
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
 Následující příklad ukazuje postup pro řazení kolekce. V příkladu seřadí instance `Car` třídy, které jsou uložené v <xref:System.Collections.Generic.List%601>. `Car` Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje, aby <xref:System.IComparable%601.CompareTo%2A> být implementována metoda.  
  
 Každé volání <xref:System.IComparable%601.CompareTo%2A> metoda umožňuje jedno porovnání, který se používá pro řazení. Uživatel zapsat kód v `CompareTo` metoda vrátí hodnotu pro každou porovnání aktuální objekt s jiným objektem. Hodnota vrácená je menší než nula. Pokud je aktuální objekt menší než druhý objekt, větší než nula. Pokud se aktuální objekt větší než druhý objekt a nula. Pokud jsou stejné. To umožňuje definovat kritéria pro větší než je menší než v kódu a rovnat.  
  
 V `ListCars` metody `cars.Sort()` příkaz Seřadí seznam. Volání <xref:System.Collections.Generic.List%601.Sort%2A> metodu <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` metoda má být automaticky volána pro `Car` objekty v `List`.  
  
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
 Kolekce můžete definovat implementací <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.IEnumerable> rozhraní. Další informace najdete v tématu [vytváření výčtu kolekce](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 I když můžete definovat vlastní kolekce, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, která jsou popsaná v [typy kolekcí](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) výše v tomto tématu.  
  
 Následující příklad definuje třídu vlastní kolekci s názvem `AllColors`. Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> být implementována metoda.  
  
 `GetEnumerator` Metoda vrací instanci třídy `ColorEnumerator` třídy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby <xref:System.Collections.IEnumerator.Current%2A> vlastnost <xref:System.Collections.IEnumerator.MoveNext%2A> metody a <xref:System.Collections.IEnumerator.Reset%2A> být implementována metoda.  
  
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
 *Iterator* se používá k provedení vlastní iteraci přes kolekci. Iterace může být metodou nebo `get` přistupujícího objektu. Používá iterovat [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý prvek kolekce, jeden v čase.  
  
 Volání iterovat pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz. Každé iteraci `For Each` volá iteraci smyčky. Když `Yield` příkaz je dosaženo v iteraci, je vrácen výraz a se uchovávají aktuální umístění v kódu. Provádění restartování z tohoto umístění příštím iteraci je volána.  
  
 Další informace najdete v tématu [iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 Následující příklad používá metodu iterator. Metoda iterator má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. V `ListEvenNumbers` metoda, každé iteraci `For Each` těla příkazu vytvoří volání metody iterator, která bude pokračovat na další `Yield` příkaz.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Programování konceptů (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)  
 [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [LINQ na objekty (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [Kolekce a datové struktury](../../../standard/collections/index.md)  
 [Vytváření a manipulace s kolekcí](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069)  
 [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)  
 [Porovnávání a řazení v kolekcích](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [Kdy použít generické kolekce](../../../standard/collections/when-to-use-generic-collections.md)
