---
title: Kolekce
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: d27761ba7a955d1dc8843ad168a82a9c9c27a6f6
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202450"
---
# <a name="collections-visual-basic"></a>Kolekce (Visual Basic)

U mnoha aplikací chcete vytvořit a spravovat skupiny souvisejících objektů. Existují dva způsoby, jak seskupit objekty: vytvořením polí objektů a vytvořením kolekcí objektů.

Pole jsou užitečná pro vytváření a práci s pevným počtem silně typových objektů. Informace o polích naleznete v tématu [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Kolekce poskytují pružnější způsob práce se skupinami objektů. Na rozdíl od polí mohou skupiny objektů, se kterými pracujete, dynamicky zvětšovat a zmenšovat podle potřeb změny aplikace. U některých kolekcí můžete přiřadit klíč k libovolnému objektu, který vložíte do kolekce, abyste mohli rychle načíst objekt pomocí klíče.

Kolekce je třída, takže před přidáním prvků do této kolekce je nutné deklarovat instanci třídy.

Pokud kolekce obsahuje prvky pouze jednoho typu dat, můžete použít jednu ze tříd v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Obecná kolekce vynutila bezpečnost typů, takže do ní nelze přidat žádný jiný datový typ. Při načítání prvku z obecné kolekce není nutné určit jeho datový typ nebo ho převést.

> [!NOTE]
> Příklady v tomto tématu zahrnují příkazy [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro `System.Collections.Generic` `System.Linq` obory názvů a.

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Používání jednoduché kolekce

Příklady v této části používají obecnou <xref:System.Collections.Generic.List%601> třídu, která umožňuje pracovat se seznamem objektů se silným typem.

Následující příklad vytvoří seznam řetězců a pak projde řetězcem pomocí [pro každý z nich... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz.

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

Pokud je obsah kolekce znám předem, můžete kolekci inicializovat pomocí *inicializátoru kolekce* . Další informace najdete v tématu [inicializátory kolekce](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

Následující příklad je stejný jako předchozí příklad, s výjimkou, že inicializátor kolekce se používá pro přidání prvků do kolekce.

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

Můžete použít [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) příkaz místo `For Each` příkazu pro iteraci v kolekci. Toho dosáhnete přístupem k prvkům kolekce na pozici indexu. Index prvků začíná na 0 a končí v počtu elementů minus 1.

Následující příklad provede iteraci prvků kolekce pomocí `For…Next` místo `For Each` .

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

Následující příklad odebere prvek z kolekce zadáním objektu, který chcete odebrat.

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

Následující příklad odstraní prvky z obecného seznamu. Místo `For Each` příkazu, [pro... ](../../../visual-basic/language-reference/statements/for-next-statement.md)Použije se další příkaz, který provede iterace v sestupném pořadí. Důvodem je, že <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.

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

Pro typ prvků v <xref:System.Collections.Generic.List%601> , můžete také definovat vlastní třídu. V následujícím příkladu `Galaxy` třída, která je použita v, <xref:System.Collections.Generic.List%601> je definována v kódu.

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

K dispozici je mnoho běžných kolekcí .NET Framework. Každý typ kolekce je navržený pro konkrétní účel.

Některé společné třídy kolekcí jsou popsány v této části:

- <xref:System.Collections.Generic> – třídy

- <xref:System.Collections.Concurrent> – třídy

- <xref:System.Collections> – třídy

- Visual Basic – `Collection` Třída

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

Další informace naleznete v tématu [běžně používané typy kolekcí](../../../standard/collections/commonly-used-collection-types.md), [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)a <xref:System.Collections.Generic?displayProperty=nameWithType> .

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>Třídy System.Collections.Concurrent

V .NET Framework 4 nebo novějších kolekce v <xref:System.Collections.Concurrent> oboru názvů poskytují efektivní operace bezpečné pro přístup z více vláken pro přístup k položkám kolekce z více vláken.

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

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a>Třída Collection v jazyce Visual Basic

Třídu Visual Basic lze použít <xref:Microsoft.VisualBasic.Collection> pro přístup k položce kolekce pomocí číselného indexu nebo `String` klíče. Můžete přidat položky do objektu kolekce buď s nebo bez zadání klíče. Pokud přidáte položku bez klíče, je nutné k ní přistupovat pomocí jejího číselného indexu.

Třída Visual Basic `Collection` ukládá všechny své prvky jako typ `Object` , takže můžete přidat položku libovolného datového typu. Neexistují žádné záruky proti přidávání nevhodných datových typů.

Když použijete třídu Visual Basic `Collection` , první položka v kolekci má index 1. To se liší od tříd kolekce .NET Framework, pro které je počáteční index 0.

Kdykoli je to možné, použijte obecné kolekce v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů nebo v <xref:System.Collections.Concurrent> oboru názvů namísto `Collection` třídy Visual Basic.

Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Collection>.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementace kolekce párů klíč/hodnota

<xref:System.Collections.Generic.Dictionary%602>Obecná kolekce umožňuje přístup k prvkům v kolekci pomocí klíče každého prvku. Každé přidání do slovníku se skládá z hodnoty a jejího přidruženého klíče. Načítání hodnoty pomocí klíče je rychlé, protože `Dictionary` Třída je implementována jako zatřiďovací tabulka.

Následující příklad vytvoří `Dictionary` kolekci a iteruje prostřednictvím slovníku pomocí `For Each` příkazu.

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

Chcete-li místo toho použít inicializátor kolekce k sestavení `Dictionary` kolekce, můžete nahradit `BuildDictionary` metody a `AddToDictionary` následující metodou.

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

Následující příklad používá <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metodu a <xref:System.Collections.Generic.Dictionary%602.Item%2A> vlastnost `Dictionary` pro rychlé vyhledání položky podle klíče. `Item`Vlastnost umožňuje přístup k položce v `elements` kolekci pomocí `elements(symbol)` kódu v Visual Basic.

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

Následující příklad místo toho používá <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metodu pro rychlé vyhledání položky podle klíče.

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

LINQ (jazykově integrovaný dotaz) lze použít pro přístup ke kolekcím. Dotazy LINQ poskytují možnosti filtrování, řazení a seskupování. Další informace najdete v tématu [Začínáme s LINQ v Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).

Následující příklad spustí dotaz LINQ na obecné `List` . Dotaz LINQ vrátí jinou kolekci, která obsahuje výsledky.

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

Následující příklad znázorňuje postup pro řazení kolekce. Příklad řadí instance `Car` třídy, které jsou uloženy v <xref:System.Collections.Generic.List%601> . `Car`Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje <xref:System.IComparable%601.CompareTo%2A> implementaci metody.

Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá k řazení. Uživatelsky psaný kód v `CompareTo` metodě vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula, pokud jsou stejné. To umožňuje definovat v kódu kritéria pro větší než, menší než a rovno.

V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody metody <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` Metoda bude automaticky volána pro `Car` objekty v `List` .

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

Kolekci můžete definovat implementací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> rozhraní nebo. Další informace najdete v tématu [výčet kolekce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).

I když můžete definovat vlastní kolekci, je obvykle vhodnější použít kolekce, které jsou součástí .NET Framework, které jsou popsány v části [druhy kolekcí](#kinds-of-collections) výše v tomto tématu.

Následující příklad definuje vlastní třídu kolekce s názvem `AllColors` . Tato třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> implementaci metody.

`GetEnumerator`Metoda vrátí instanci `ColorEnumerator` třídy. `ColorEnumerator`implementuje <xref:System.Collections.IEnumerator> rozhraní, které vyžaduje, aby byla <xref:System.Collections.IEnumerator.Current%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> implementována vlastnost, metoda a <xref:System.Collections.IEnumerator.Reset%2A> metoda.

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

*Iterátor* se používá k provedení vlastní iterace v kolekci. Iterátor může být metoda nebo `get` přistupující objekt. Iterátor používá příkaz [yield](../../../visual-basic/language-reference/statements/yield-statement.md) k vrácení každého prvku kolekce v jednom okamžiku.

Zavoláte iterátor pomocí a [pro každou z nich... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz. Každá iterace `For Each` smyčky volá iterátor. Při `Yield` dosažení příkazu v iterátoru je vrácen výraz a aktuální umístění v kódu je uchováno. Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.

Další informace najdete v tématu [iterátory (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).

Následující příklad používá metodu iterátoru. Metoda iterátoru má `Yield` příkaz, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka V `ListEvenNumbers` metodě Každá iterace `For Each` těla příkazu vytvoří volání metody iterátoru, která pokračuje k dalšímu `Yield` příkazu.

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
- [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Paralelní LINQ (PLINQ)](../../../standard/parallel-programming/introduction-to-plinq.md)
- [Kolekce a datové struktury](../../../standard/collections/index.md)
- [Výběr třídy kolekce](../../../standard/collections/selecting-a-collection-class.md)
- [Porovnání a řazení v rámci kolekcí](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kdy použít obecné kolekce](../../../standard/collections/when-to-use-generic-collections.md)
