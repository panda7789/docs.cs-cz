---
title: Iterátory
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 2789ac66690ebfd472b9bae5ccf08b1bdfaa0922
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628732"
---
# <a name="iterators-visual-basic"></a>Iterátory (Visual Basic)

*Iterátor* se dá použít ke krokování kolekcí, jako jsou seznamy a pole.

Metoda iterátoru nebo přistupující objekt `get` provádí vlastní iteraci v kolekci. Metoda iterátoru používá příkaz [yield](../../../visual-basic/language-reference/statements/yield-statement.md) k vrácení každého prvku v jednom okamžiku. Když je dosaženo příkazu `Yield`, aktuální umístění v kódu je zapamatovatelné. Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.

Využijete iterátor z klientského kódu pomocí [pro každý... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz nebo pomocí dotazu LINQ.

V následujícím příkladu první iterace smyčky `For Each` způsobí, že spuštění pokračuje v metodě `SomeNumbers` iterátoru, dokud se nedosáhne prvního příkazu `Yield`. Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru se zachová. Při další iteraci smyčky pokračuje spuštění v metodě iterátoru tam, kde skončila, a znovu se zastaví, jakmile dosáhne `Yield`ho příkazu. Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru se znovu zachová. Smyčka skončí po dosažení konce metody iterátoru.

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

Návratový typ metody iterátoru nebo přístupového objektu `get` může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.

Chcete-li ukončit iteraci, můžete použít příkaz `Exit Function` nebo `Return`.

Funkce iterátoru Visual Basic nebo deklarace přístupového objektu `get` obsahuje modifikátor [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md) .

Iterátory byly představeny v Visual Basic v aplikaci Visual Studio 2012.

**V tomto tématu**

- [Jednoduchý iterátor](#BKMK_SimpleIterator)

- [Vytvoření třídy kolekce](#BKMK_CollectionClass)

- [Bloky try](#BKMK_TryBlocks)

- [Anonymní metody](#BKMK_AnonymousMethods)

- [Používání iterátorů s obecným seznamem](#BKMK_GenericList)

- [Informace o syntaxi](#BKMK_SyntaxInformation)

- [Technická implementace](#BKMK_Technical)

- [Používání iterátorů](#BKMK_UseOfIterators)

> [!NOTE]
> Pro všechny příklady v tématu s výjimkou příkladu jednoduchého iterátoru uveďte příkazy [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro obory názvů `System.Collections` a `System.Collections.Generic`.

## <a name="BKMK_SimpleIterator"></a>Jednoduchý iterátor

V následujícím příkladu je jeden příkaz `Yield`, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka V `Main`Každá iterace těla příkazu `For Each` vytvoří volání funkce iterátoru, které pokračuje k dalšímu příkazu `Yield`.

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="BKMK_CollectionClass"></a>Vytvoření třídy kolekce

V následujícím příkladu třída `DaysOfTheWeek` implementuje rozhraní <xref:System.Collections.IEnumerable>, které vyžaduje metodu <xref:System.Collections.IEnumerable.GetEnumerator%2A>. Kompilátor implicitně volá metodu `GetEnumerator`, která vrací <xref:System.Collections.IEnumerator>.

Metoda `GetEnumerator` vrátí každý řetězec po jednom pomocí příkazu `Yield` a modifikátor `Iterator` je v deklaraci funkce.

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

Následující příklad vytvoří třídu `Zoo`, která obsahuje kolekci zvířat.

Příkaz `For Each`, který odkazuje na instanci třídy (`theZoo`), implicitně volá metodu `GetEnumerator`. Příkazy `For Each`, které odkazují na vlastnosti `Birds` a `Mammals`, používají `AnimalsForType` s názvem iterátor.

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="BKMK_TryBlocks"></a>Bloky try

Visual Basic povoluje příkaz `Yield` v bloku `Try` [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Blok `Try`, který má příkaz `Yield`, může mít `Catch` bloky a může mít `Finally` blok.

Následující příklad obsahuje `Try`, `Catch`a `Finally` bloky ve funkci iterátoru. Blok `Finally` ve funkci iterátoru se spustí před dokončením `For Each` iterace.

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

Příkaz `Yield` nemůže být uvnitř bloku `Catch` nebo bloku `Finally`.

Pokud `For Each` tělo (místo iterátoru) vyvolá výjimku, není proveden blok `Catch` ve funkci iterátoru, ale je spuštěn blok `Finally` ve funkci iterátoru. `Catch` blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.

## <a name="BKMK_AnonymousMethods"></a>Anonymní metody

V Visual Basic může být anonymní funkcí funkce iterátoru. Toto dokládá následující příklad.

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

V následujícím příkladu je metoda bez iterátoru, která ověřuje argumenty. Metoda vrací výsledek anonymního iterátoru, který popisuje prvky kolekce.

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

Pokud je ověřování místo v rámci funkce iterátoru, nelze provést ověření až do začátku první iterace těla `For Each`.

## <a name="BKMK_GenericList"></a>Používání iterátorů s obecným seznamem

V následujícím příkladu `Stack(Of T)` obecná třída implementuje obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601>. Metoda `Push` přiřadí hodnoty k poli typu `T`. Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> vrací hodnoty pole pomocí příkazu `Yield`.

Kromě obecných <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda musí být také implementována neobecná <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda. Důvodem je to, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>. Neobecná implementace se odloží k obecné implementaci.

Tento příklad používá pojmenované iterátory k podpoře různých způsobů iterace v rámci stejné kolekce dat. Tyto pojmenované iterátory jsou vlastnosti `TopToBottom` a `BottomToTop` a metoda `TopN`.

Deklarace vlastnosti `BottomToTop` zahrnuje klíčové slovo `Iterator`.

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="BKMK_SyntaxInformation"></a>Informace o syntaxi

Iterátor se může vyskytnout jako metoda nebo přistupující objekt `get`. Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.

Implicitní převod musí existovat v typu výrazu v příkazu `Yield` do návratového typu iterátoru.

V Visual Basic metoda iterátoru nemůže mít žádné parametry `ByRef`.

V Visual Basic "yield" není rezervované slovo a má zvláštní význam pouze v případě, že se používá v metodě `Iterator` nebo přístupovém objektu `get`.

## <a name="BKMK_Technical"></a>Technická implementace

I když zapisujete iterátor jako metodu, kompilátor je převede na vnořenou třídu, která je v podstatě Stavový počítač. Tato třída uchovává informace o poloze iterátoru, pokud bude `For Each...Next` smyčka v kódu klienta pokračovat.

Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm. exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.

Při vytváření iterátoru pro [třídu](../../language-reference/statements/class-statement.md) nebo [strukturu](../../language-reference/statements/structure-statement.md)není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní. Když kompilátor detekuje iterátor, automaticky generuje `Current`, `MoveNext`a `Dispose` metody rozhraní <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601>.

U každého následného opakování smyčky `For Each…Next` (nebo přímého volání `IEnumerator.MoveNext`) pokračuje další tělo kódu iterátoru po předchozím příkazu `Yield`. Pak pokračuje dalším příkazem `Yield` až do chvíle, kdy se dosáhne konce textu iterátoru, nebo dokud se nezjistí `Exit Function` nebo `Return` příkaz.

Iterátory nepodporují metodu <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>. Pokud chcete opakovat iteraci od začátku, musíte získat nový iterátor.

Další informace najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).

## <a name="BKMK_UseOfIterators"></a>Používání iterátorů

Iterátory umožňují udržovat jednoduchost smyčky `For Each`, když potřebujete použít složitý kód k naplnění pořadí seznamu. To může být užitečné v případě, že chcete provést následující akce:

- Upravte pořadí seznamu po první iteraci `For Each` smyčky.

- Vyhněte se úplnému načítání velkého seznamu před první iterací `For Each` smyčky. Příkladem stránkovaného načtení je načtení dávky řádků tabulky. Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rámci .NET Framework.

- Zapouzdřit sestavení seznamu v iterátoru. V metodě iterátoru můžete sestavit seznam a pak každý výsledek vracet ve smyčce.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
- [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
