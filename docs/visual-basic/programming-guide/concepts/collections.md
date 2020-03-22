---
title: Kolekce
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: ba16d04e781bcf69356b1f603d92e104816a0860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400825"
---
# <a name="collections-visual-basic"></a>Kolekce (Visual Basic)

Pro mnoho aplikací chcete vytvořit a spravovat skupiny souvisejících objektů. Existují dva způsoby seskupení objektů: vytvořením polí objektů a vytvořením kolekcí objektů.

Pole jsou nejužitečnější pro vytváření a práci s pevným počtem objektů silného typu. Informace o polích naleznete v [tématu Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Kolekce poskytují flexibilnější způsob práce se skupinami objektů. Na rozdíl od polí může skupina objektů, se kterými pracujete, dynamicky růst a zmenšovat podle potřeby aplikace. Pro některé kolekce můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, takže můžete rychle načíst objekt pomocí klíče.

Kolekce je třída, takže je nutné deklarovat instanci třídy před přidáním prvků do této kolekce.

Pokud vaše kolekce obsahuje prvky pouze jednoho datového typu, <xref:System.Collections.Generic?displayProperty=nameWithType> můžete použít jednu z tříd v oboru názvů. Obecná kolekce vynucuje bezpečnost typů tak, aby do ní nebylo možné přidat žádný jiný datový typ. Při načtení prvku z obecné kolekce, není nutné určit jeho datový typ nebo převést.

> [!NOTE]
> Příklady v tomto tématu, zahrnout [Imports příkazy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro `System.Collections.Generic` a `System.Linq` obory názvů.

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce

Příklady v této části <xref:System.Collections.Generic.List%601> používají obecnou třídu, která umožňuje pracovat se silným seznamem objektů.

Následující příklad vytvoří seznam řetězců a potom iterates prostřednictvím řetězce pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) prohlášení.

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

Pokud obsah kolekce jsou známy předem, můžete použít *inicializační kolekce* inicializovat kolekce. Další informace naleznete v [tématu Inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

Následující příklad je stejný jako v předchozím příkladu, s výjimkou inicializátor kolekce se používá k přidání prvků do kolekce.

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

Můžete použít [For... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz namísto příkazu `For Each` iterát prostřednictvím kolekce. Toho lze provést přístupem k prvky kolekce podle pozice indexu. Index prvků začíná na 0 a končí na počet prvků minus 1.

Následující příklad iterates prostřednictvím prvky `For…Next` kolekce `For Each`pomocí místo .

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

Následující příklad odebere prvek z kolekce zadáním objektu, který má být odebrán.

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

Následující příklad odebere prvky z obecného seznamu. Místo prohlášení, `For Each` [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) prohlášení, že iteráty v sestupném pořadí se používá. Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraný prvek mít nižší hodnotu indexu.

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

Pro typ prvků v <xref:System.Collections.Generic.List%601>aplikaci můžete také definovat vlastní třídu. V následujícím příkladu `Galaxy` je třída, <xref:System.Collections.Generic.List%601> která je používána, definována v kódu.

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

Mnoho běžných kolekcí poskytuje rozhraní .NET Framework. Každý typ kolekce je určen pro konkrétní účel.

Některé běžné třídy kolekce jsou popsány v této části:

- <xref:System.Collections.Generic> – třídy

- <xref:System.Collections.Concurrent> – třídy

- <xref:System.Collections> – třídy

- Třída `Collection` Visual Basic

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

Další informace naleznete [v tématu Běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic?displayProperty=nameWithType>.

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

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a>Třída Collection v jazyce Visual Basic

Třídu Visual Basic <xref:Microsoft.VisualBasic.Collection> můžete použít pro přístup k položce `String` kolekce pomocí číselného indexu nebo klíče. Můžete přidat položky do objektu kolekce buď s nebo bez zadání klíče. Pokud přidáte položku bez klíče, musíte pro přístup k ní použít její číselný index.

Visual Basic `Collection` třída ukládá všechny `Object`jeho prvky jako typ , takže můžete přidat položku libovolného datového typu. Neexistuje žádná ochrana proti přidávání nevhodných datových typů.

Při použití visual `Collection` basic třídy první položka v kolekci má index 1. To se liší od tříd kolekce rozhraní .NET Framework, pro které počáteční index je 0.

Kdykoli je to možné, měli byste <xref:System.Collections.Generic?displayProperty=nameWithType> použít obecné <xref:System.Collections.Concurrent> kolekce v oboru `Collection` názvů nebo oboru názvů namísto třídy jazyka Visual Basic.

Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Collection>.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota

Obecná <xref:System.Collections.Generic.Dictionary%602> kolekce umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku. Každý doplněk do slovníku se skládá z hodnoty a jeho přidruženého klíče. Načítání hodnoty pomocí jeho klíče je `Dictionary` rychlé, protože třída je implementována jako tabulka hash.

Následující příklad vytvoří `Dictionary` kolekci a iterates prostřednictvím `For Each` slovníku pomocí příkazu.

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

Chcete-li místo toho použít `Dictionary` inicializátor `BuildDictionary` kolekce `AddToDictionary` k sestavení kolekce, můžete nahradit metody a následující metodou.

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

Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodu <xref:System.Collections.Generic.Dictionary%602.Item%2A> a `Dictionary` vlastnost rychle najít položku podle klíče. Vlastnost `Item` umožňuje přístup k položce `elements` v kolekci pomocí `elements(symbol)` kódu v jazyce Visual Basic.

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

Následující příklad místo <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> toho používá metodu rychle najít položku podle klíče.

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

## <a name="using-linq-to-access-a-collection"></a>Přístup ke kolekci pomocí jazyka LINQ

LINQ (Language-Integrated Query) lze použít pro přístup k kolekcím. Linq dotazy poskytují možnosti filtrování, řazení a seskupování. Další informace naleznete [v tématu Začínáme s LINQ v jazyce Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).

Následující příklad spustí dotaz LINQ `List`proti obecnému . Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.

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

Následující příklad ilustruje postup pro řazení kolekce. Příklad seřadí instance `Car` třídy, které <xref:System.Collections.Generic.List%601>jsou uloženy v . Třída `Car` implementuje <xref:System.IComparable%601> rozhraní, které <xref:System.IComparable%601.CompareTo%2A> vyžaduje, aby byla metoda implementována.

Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá pro řazení. Kód napsaný uživatelem v metodě `CompareTo` vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt, a nula, pokud jsou stejné. To umožňuje definovat v kódu kritéria pro větší než, menší než a rovné.

V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> způsobí, `CompareTo` že metoda má `Car` být volána automaticky pro objekty v `List`.

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

Můžete definovat kolekci <xref:System.Collections.Generic.IEnumerable%601> implementací <xref:System.Collections.IEnumerable> rozhraní nebo. Další informace naleznete [v tématu výčet kolekce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).

I když můžete definovat vlastní kolekci, je obvykle lepší místo toho použít kolekce, které jsou zahrnuty v rozhraní .NET Framework, které jsou popsány v [druhy kolekcí](#kinds-of-collections) dříve v tomto tématu.

Následující příklad definuje vlastní třídu `AllColors`kolekce s názvem . Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, <xref:System.Collections.IEnumerable.GetEnumerator%2A> které vyžaduje, aby byla metoda implementována.

Metoda `GetEnumerator` vrátí instanci `ColorEnumerator` třídy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které <xref:System.Collections.IEnumerator.Current%2A> vyžaduje, <xref:System.Collections.IEnumerator.MoveNext%2A> aby <xref:System.Collections.IEnumerator.Reset%2A> byla implementována vlastnost, metoda a metoda.

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

## <a name="iterators"></a>Iterátory

*Iterátor* se používá k provedení vlastní iterace přes kolekci. Iterátor může být metoda nebo `get` přistupující objekt. Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) prohlášení vrátit každý prvek kolekce jeden po druhém.

Zavoláte iterátor pomocí [Pro každý ... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) prohlášení. Každá iterace `For Each` smyčky volá iterátor. Když `Yield` je dosaženo příkazu v iterátoru, je vrácen výraz a aktuální umístění v kódu je zachováno. Spuštění je restartován z tohoto umístění při příštím volání iterátoru.

Další informace naleznete v tématu [Iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).

Následující příklad používá metodu iterátoru. Metoda iterátoru `Yield` má příkaz, který je uvnitř [For... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka. V `ListEvenNumbers` metodě každá iterace těla příkazu `For Each` vytvoří volání iterátoru `Yield` metody, která pokračuje na další příkaz.

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

- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Koncepty programování (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ na objekty (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [Kolekce a datové struktury](../../../standard/collections/index.md)
- [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)
- [Porovnávání a řazení v kolekcích](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kdy použít generické kolekce](../../../standard/collections/when-to-use-generic-collections.md)
