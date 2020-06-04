---
title: Iterátory
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: e638d35aeb86837d91fb14681d300772e3c2375a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410926"
---
# <a name="iterators-visual-basic"></a>Iterátory (Visual Basic)

*Iterátor* se dá použít ke krokování kolekcí, jako jsou seznamy a pole.

Metoda iterátoru nebo `get` přistupující objekt provádí vlastní iteraci v kolekci. Metoda iterátoru používá příkaz [yield](../../language-reference/statements/yield-statement.md) k vrácení každého prvku v jednom okamžiku. Při `Yield` dosažení příkazu je aktuální umístění v kódu zapamatovatelné. Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.

Využijete iterátor z klientského kódu pomocí [pro každý... Další](../../language-reference/statements/for-each-next-statement.md) příkaz nebo pomocí dotazu LINQ.

V následujícím příkladu první iterace smyčky způsobí, že `For Each` provádění pokračuje v `SomeNumbers` metodě iterátoru, dokud `Yield` není dosaženo prvního příkazu. Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru se zachová. Při další iteraci smyčky pokračuje spuštění v metodě iterátoru z místa, kde skončilo, a opětovné zastavení při dosažení `Yield` příkazu. Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru se znovu zachová. Smyčka skončí po dosažení konce metody iterátoru.

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

Návratový typ metody iterátoru nebo `get` přístupového objektu může být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .

`Exit Function` `Return` K ukončení iterace můžete použít příkaz or.

Funkce iterátoru Visual Basic nebo `get` deklarace přístupového objektu obsahuje modifikátor [iterátoru](../../language-reference/modifiers/iterator.md) .

Iterátory byly představeny v Visual Basic v aplikaci Visual Studio 2012.

**V tomto tématu**

- [Jednoduchý iterátor](#BKMK_SimpleIterator)

- [Vytvoření třídy kolekce](#BKMK_CollectionClass)

- [Bloky try](#BKMK_TryBlocks)

- [Anonymní metody](#BKMK_AnonymousMethods)

- [Používání iterátorů v obecných seznamech](#BKMK_GenericList)

- [Informace o syntaxi](#BKMK_SyntaxInformation)

- [Technická implementace](#BKMK_Technical)

- [Používání iterátorů](#BKMK_UseOfIterators)

> [!NOTE]
> Pro všechny příklady v tématu s výjimkou příkladu jednoduchého iterátoru uveďte příkazy [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) pro `System.Collections` `System.Collections.Generic` obory názvů a.

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a>Jednoduchý iterátor

V následujícím příkladu je jeden `Yield` příkaz, který je uvnitř [... Další](../../language-reference/statements/for-next-statement.md) smyčka V `Main` , Každá iterace `For Each` těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `Yield` příkazu.

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

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a>Vytvoření třídy kolekce

V následujícím příkladu `DaysOfTheWeek` Třída implementuje <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu. Kompilátor implicitně volá `GetEnumerator` metodu, která vrací <xref:System.Collections.IEnumerator> .

`GetEnumerator`Metoda vrátí každý řetězec po jednom pomocí `Yield` příkazu a `Iterator` Modifikátor je v deklaraci funkce.

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

Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířat.

`For Each`Příkaz, který odkazuje na instanci třídy ( `theZoo` ) implicitně volá `GetEnumerator` metodu. `For Each`Příkazy, které odkazují na `Birds` vlastnosti a `Mammals` používají `AnimalsForType` metodu s názvem iterátor.

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

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a>Bloky try

Visual Basic povoluje `Yield` příkaz v `Try` bloku [Try... Zachytit... Finally – příkaz](../../language-reference/statements/try-catch-finally-statement.md). `Try`Blok, který má `Yield` příkaz, může mít `Catch` bloky a může mít `Finally` blok.

Následující příklad obsahuje `Try` bloky, `Catch` a `Finally` ve funkci iterátoru. `Finally`Blok ve funkci iterátoru se provede před `For Each` dokončením iterace.

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

`Yield`Příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.

Pokud `For Each` tělo (místo metody iterátoru) vyvolá výjimku, není `Catch` proveden blok ve funkci iterátoru, ale `Finally` je proveden blok ve funkci iterátoru. `Catch`Blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a>Anonymní metody

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

Pokud je ověřování místo v rámci funkce iterátoru, nelze provést ověření až do začátku první iterace `For Each` těla.

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a>Používání iterátorů s obecným seznamem

V následujícím příkladu `Stack(Of T)` Obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> Obecné rozhraní. `Push`Metoda přiřadí hodnoty k poli typu `T` . <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Metoda vrací hodnoty pole pomocí `Yield` příkazu.

Kromě obecné <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody <xref:System.Collections.IEnumerable.GetEnumerator%2A> musí být také implementována neobecná metoda. Důvodem je <xref:System.Collections.Generic.IEnumerable%601> , že dědí z <xref:System.Collections.IEnumerable> . Neobecná implementace se odloží k obecné implementaci.

Tento příklad používá pojmenované iterátory k podpoře různých způsobů iterace v rámci stejné kolekce dat. Tyto pojmenované iterátory jsou `TopToBottom` vlastnosti a `BottomToTop` a `TopN` metoda.

`BottomToTop`Deklarace vlastnosti zahrnuje `Iterator` klíčové slovo.

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

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a>Informace o syntaxi

Iterátor se může vyskytnout jako metoda nebo `get` přistupující objekt. Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.

Implicitní převod musí existovat v typu výrazu v `Yield` příkazu na návratový typ iterátoru.

V Visual Basic metoda iterátoru nemůže mít žádné `ByRef` parametry.

V Visual Basic "yield" není rezervované slovo a má zvláštní význam pouze v případě, že je použit v `Iterator` metodě nebo `get` přístupovém objektu.

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a>Technická implementace

I když zapisujete iterátor jako metodu, kompilátor je převede na vnořenou třídu, která je v podstatě Stavový počítač. Tato třída uchovává informace o poloze iterátoru, dokud `For Each...Next` smyčka v kódu klienta pokračuje.

Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm. exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.

Při vytváření iterátoru pro [třídu](../../language-reference/statements/class-statement.md) nebo [strukturu](../../language-reference/statements/structure-statement.md)není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní. Když kompilátor detekuje iterátor, automaticky generuje `Current` `MoveNext` metody, a `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> rozhraní nebo.

U každé následné iterace `For Each…Next` smyčky (nebo přímého volání `IEnumerator.MoveNext` ) pokračuje další tělo kódu iterátoru za předchozím `Yield` příkazem. Pak pokračuje k dalšímu `Yield` příkazu, dokud není dosaženo konce textu iterátoru nebo dokud se nezjistí `Exit Function` `Return` příkaz or.

Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metodu. Pokud chcete opakovat iteraci od začátku, musíte získat nový iterátor.

Další informace najdete v tématu [specifikace jazyka Visual Basic](../../reference/language-specification/index.md).

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a>Používání iterátorů

Iterátory umožňují udržovat jednoduchost `For Each` smyčky, pokud potřebujete použít složitý kód k naplnění pořadí seznamu. To může být užitečné v případě, že chcete provést následující akce:

- Změňte pořadí seznamu po `For Each` iteraci první smyčky.

- Vyhněte se úplnému načítání velkého seznamu před první iterací `For Each` smyčky. Příkladem stránkovaného načtení je načtení dávky řádků tabulky. Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rámci .NET Framework.

- Zapouzdřit sestavení seznamu v iterátoru. V metodě iterátoru můžete sestavit seznam a pak každý výsledek vracet ve smyčce.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next – příkaz](../../language-reference/statements/for-each-next-statement.md)
- [Yield – příkaz](../../language-reference/statements/yield-statement.md)
- [Iterátor](../../language-reference/modifiers/iterator.md)
