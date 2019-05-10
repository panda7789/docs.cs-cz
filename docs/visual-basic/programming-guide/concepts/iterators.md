---
title: Iterátory (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 73561cf5bed583e2dbf853b7771b9e949a5c0267
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642286"
---
# <a name="iterators-visual-basic"></a>Iterátory (Visual Basic)
*Iterátoru* slouží k procházení kolekcí, jako je seznamy a pole.  
  
 Metodu iterátoru nebo `get` přistupující objekt provádí vlastní iterace nad kolekcí. Využívá metoda iterace [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit vždy jeden prvek v čase. Když `Yield` je dosažen příkaz, se uloží aktuální umístění v kódu. Provádění je restartováno z tohoto umístění při příštím je zavolána funkce iterátoru.  
  
 Využívat iterátor z klientského kódu pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkazu, nebo pomocí dotazu LINQ.  
  
 V následujícím příkladu první iterace `For Each` smyčky způsobí, že chcete-li pokračovat v provádění `SomeNumbers` metody iterátoru až do první `Yield` je dosažen příkaz. Tuto iteraci, vrátí hodnotu 3 a je zachováno aktuální umístění v metodě iterátoru. Na další iteraci smyčky v metodě iterátoru pokračuje odkud zastaví se opět tehdy, když se dosáhne `Yield` příkazu. Tuto iteraci, vrátí hodnotu 5 a znovu se uchovávají aktuální umístění v metodě iterátoru. Smyčky dokončí, když je dosaženo konce metody iterátoru.  
  
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
  
 Návratový typ metody iterátoru nebo `get` přistupující objekt může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Můžete použít `Exit Function` nebo `Return` příkaz do konce iterace.  
  
 Funkce iterátorů jazyka Visual Basic nebo `get` deklarace přistupujícího objektu obsahuje [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md) modifikátor.  
  
 Iterátory byly zavedeny v jazyce Visual Basic v sadě Visual Studio 2012.  
  
 **V tomto tématu**  
  
- [Jednoduchý iterátor](#BKMK_SimpleIterator)  
  
- [Vytvoření třídy kolekce](#BKMK_CollectionClass)  
  
- [Bloky try](#BKMK_TryBlocks)  
  
- [Anonymní metody](#BKMK_AnonymousMethods)  
  
- [Používání iterátorů v obecných seznamech](#BKMK_GenericList)  
  
- [Informace o syntaxi](#BKMK_SyntaxInformation)  
  
- [Technická implementace](#BKMK_Technical)  
  
- [Používání iterátorů](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Všechny příklady v tomto tématu, s výjimkou příklad jednoduchý iterátor zahrnují [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) příkazů `System.Collections` a `System.Collections.Generic` obory názvů.  
  
## <a name="BKMK_SimpleIterator"></a> Jednoduchý iterátor  
 V následujícím příkladu má jeden `Yield` , který se nachází uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. V `Main`, každá iterace `For Each` tělo s příkazy vytvoří volání funkce iterátoru, který pokračuje k dalšímu `Yield` příkazu.  
  
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
  
## <a name="BKMK_CollectionClass"></a> Vytvoření třídy kolekce  
 V následujícím příkladu `DaysOfTheWeek` implementuje třída <xref:System.Collections.IEnumerable> rozhraní, které vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. Kompilátor implicitně volá `GetEnumerator` metoda, která vrátí <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Metoda vrátí jednotlivých řetězců, jeden po druhém pomocí `Yield` příkaz a `Iterator` Modifikátor je v deklaraci funkce.  
  
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
  
 Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířata.  
  
 `For Each` Příkaz, který odkazuje na instanci třídy (`theZoo`) implicitně volá `GetEnumerator` metody. `For Each` Příkazů, které odkazují `Birds` a `Mammals` použití vlastnosti `AnimalsForType` s názvem metody iterátoru.  
  
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
  
## <a name="BKMK_TryBlocks"></a> Bloky try  
 Umožňuje Visual Basic `Yield` příkaz v `Try` bloku [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` blok, který má `Yield` může mít příkaz `Catch` a ostatní porty blokuje může mít `Finally` bloku.  
  
 Následující příklad obsahuje `Try`, `Catch`, a `Finally` bloky v funkce iterátoru. `Finally` Blok iterátoru funkce se spustí před `For Each` dokončení iterace.  
  
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
  
 A `Yield` příkaz nejde provést uvnitř `Catch` bloku nebo `Finally` bloku.  
  
 Pokud `For Each` text (namísto metody iterátoru) vyvolá výjimku, `Catch` bloku funkce iterátoru není spuštěn, ale `Finally` je proveden blok v funkce iterátoru. A `Catch` bloku funkce iterátoru zachytává pouze výjimky, ke kterým dochází uvnitř funkce iterátoru.  
  
## <a name="BKMK_AnonymousMethods"></a> Anonymní metody  
 Anonymní funkce v jazyce Visual Basic lze funkce iterátoru. Toto dokládá následující příklad.  
  
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
  
 V následujícím příkladu má jiné iterátoru metodu, která ověřuje argumenty. Metoda vrací výsledek anonymní iterátoru, který popisuje elementy z kolekce.  
  
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
  
 Pokud ověření se místo nachází uvnitř funkce iterátoru, ověření nelze provést, až při spuštění první iterace `For Each` textu.  
  
## <a name="BKMK_GenericList"></a> Používání iterátorů v obecných seznamech  
 V následujícím příkladu `Stack(Of T)` obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> obecného rozhraní. `Push` Metoda přiřadí hodnoty do pole typu `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda vrátí pole hodnot s použitím `Yield` příkazu.  
  
 Kromě obecného <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody, který není obecný <xref:System.Collections.IEnumerable.GetEnumerator%2A> musí také být implementována metoda. Důvodem je, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>. Implementace neobecnou odloží na obecnou implementaci.  
  
 Příklad používá pro podporu různých způsobů iterace v rámci stejné kolekce dat s názvem iterátory. Tyto iterátory s názvem jsou `TopToBottom` a `BottomToTop` vlastnosti a `TopN` metoda.  
  
 `BottomToTop` Obsahuje deklarace vlastnosti `Iterator` – klíčové slovo.  
  
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
  
## <a name="BKMK_SyntaxInformation"></a> Informace o syntaxi  
 Iterátor může dojít, jako metodu nebo `get` přistupujícího objektu. V události, konstruktor instance, statický konstruktor nebo statická destruktor nemůže dojít k iterátoru.  
  
 Musí existovat implicitní převod z typu výrazu v `Yield` příkaz a návratový typ iterátoru.  
  
 V jazyce Visual Basic metodu iterátoru nesmí obsahovat žádné `ByRef` parametry.  
  
 V jazyce Visual Basic "Yield" není vyhrazené slovo a má zvláštní význam pouze v případě, že se používá `Iterator` metoda nebo `get` přistupujícího objektu.  
  
## <a name="BKMK_Technical"></a> Technická implementace  
 I když píšete iterátoru jako metodu, kompilátor přeloží ho do vnořené třídy, který je, v důsledku toho stavového stroje. Tato třída uchovává informace o pozice iterátoru jako dlouho `For Each...Next` pokračuje smyčka v kódu klienta.  
  
 Pokud chcete zobrazit, co dělá kompilátor, můžete nástroj Ildasm.exe zobrazíte kód Microsoft intermediate language, který je generován pro metodu iterátoru.  
  
 Při vytváření iterátor pro [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), není nutné k implementaci celého <xref:System.Collections.IEnumerator> rozhraní. Když kompilátor zjistí iterátoru, automaticky generuje `Current`, `MoveNext`, a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.  
  
 Na každou následnou iterací z `For Each…Next` smyčky (nebo přímého volání `IEnumerator.MoveNext`), další kód tělo iterátoru pokračuje po předchozí `Yield` příkazu. Bude pokračovat na další `Yield` příkaz, dokud je dosaženo konce tělo iterátoru, nebo dokud `Exit Function` nebo `Return` příkaz dochází.  
  
 Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. K iteraci v znovu od začátku, musíte získat nový iterátoru.  
  
 Další informace najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
## <a name="BKMK_UseOfIterators"></a> Používání iterátorů  
 Iterátory umožňují udržovat jednoduchost `For Each` smyčky, když budete chtít použít k naplnění seznamu pořadí složitého kódu. To může být užitečné, pokud chcete provést následující kroky:  
  
- Pořadí seznamu změnit po prvním `For Each` iterace smyčky.  
  
- Vyhněte se plně načítání velkých seznamu před první iteraci `For Each` smyčky. Příkladem je stránkovaného načtení načíst dávku řádků tabulky. Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metodu, která implementuje iterátorů v rámci rozhraní .NET Framework.  
  
- Zapouzdření vytváření seznamu v iterátoru. V metodě iterátoru můžete vytvořit seznam a potom yield každého výsledku ve smyčce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
- [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
