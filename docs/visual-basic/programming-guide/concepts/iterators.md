---
title: Iterátory (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: ecc48ad5bbddc82457a8d6cc8e60ee419fb593fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643923"
---
# <a name="iterators-visual-basic"></a>Iterátory (Visual Basic)
*Iterator* slouží k krok prostřednictvím kolekcí, jako například seznamy a maticových.  
  
 Metodu iterator nebo `get` přistupujícího objektu provede vlastní iteraci přes kolekci. Používá metodu iterator [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý element, jeden v čase. Když `Yield` příkaz je dosaženo, uloží je aktuální umístění v kódu. Provádění restartování z tohoto umístění při příštím iterator funkce je volána.  
  
 Využívat iterovat z klientského kódu pomocí [For Each... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) prohlášení, nebo pomocí dotazu LINQ.  
  
 V následujícím příkladu, první iterace `For Each` smyčky způsobí, že chcete-li pokračovat v provádění `SomeNumbers` iterator – metoda dokud první `Yield` je dosaženo příkaz. Tato iterace vrací hodnotu 3 a aktuální umístění v metodě iterator zůstane. Na další iteraci smyčky, pokračuje spuštění v metodě iterator odkud bylo přerušeno, znovu zastavit při dosažení `Yield` příkaz. Tento iterace vrací hodnotu 5 a opakujte aktuální umístění v metodě iterator zůstane. Když je dosaženo konce iterator metody dokončení smyčky.  
  
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
  
 Návratový typ metody iterator nebo `get` přistupujícího objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Můžete použít `Exit Function` nebo `Return` příkaz k ukončení iterace.  
  
 Iterator funkci jazyka Visual Basic nebo `get` zahrnuje deklaraci přistupujícího objektu [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifikátor.  
  
 Iterátory byly zavedeny v jazyce Visual Basic v sadě Visual Studio 2012.  
  
 **V tomto tématu**  
  
-   [Jednoduché iterátorů](#BKMK_SimpleIterator)  
  
-   [Vytvoření třídy kolekce](#BKMK_CollectionClass)  
  
-   [Try – bloky](#BKMK_TryBlocks)  
  
-   [Anonymní metody](#BKMK_AnonymousMethods)  
  
-   [Pomocí seznamu obecné iterátory](#BKMK_GenericList)  
  
-   [Informace ze syntaxe](#BKMK_SyntaxInformation)  
  
-   [Technická implementace](#BKMK_Technical)  
  
-   [Použití iterátory](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Všechny příklady v tomto tématu, s výjimkou Iterator jednoduchý příklad, zahrnují [importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro příkazy `System.Collections` a `System.Collections.Generic` obory názvů.  
  
##  <a name="BKMK_SimpleIterator"></a> Jednoduché iterátorů  
 V následujícím příkladu má jeden `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. V `Main`, každé iteraci `For Each` těla příkazu vytvoří volání funkce iterator, který bude pokračovat na další `Yield` příkaz.  
  
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
  
##  <a name="BKMK_CollectionClass"></a> Vytvoření třídy kolekce  
 V následujícím příkladu `DaysOfTheWeek` třída implementuje <xref:System.Collections.IEnumerable> rozhraní, což vyžaduje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda. Kompilátor implicitně volá `GetEnumerator` metoda, která vrátí <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Metoda vrátí každý řetězec jeden současně pomocí `Yield` příkaz a `Iterator` se modifikátor v deklaraci funkce.  
  
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
  
 `For Each` Příkaz, který odkazuje na instanci třídy (`theZoo`) implicitně volá `GetEnumerator` metoda. `For Each` Příkazy, které odkazují `Birds` a `Mammals` použití vlastnosti `AnimalsForType` s názvem iterator – metoda.  
  
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
  
##  <a name="BKMK_TryBlocks"></a> Try – bloky  
 Umožňuje jazyka Visual Basic `Yield` příkaz v `Try` blokovat z [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` blok, který má `Yield` příkaz může mít `Catch` blokuje a může mít `Finally` bloku.  
  
 Následující příklad obsahuje `Try`, `Catch`, a `Finally` blokuje v iterator funkci. `Finally` Bloku ve funkci iterator provede před `For Each` iterace dokončení.  
  
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
  
 A `Yield` příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.  
  
 Pokud `For Each` textu (místo metody iterator) vyvolá výjimku, `Catch` bloku ve funkci iterator není proveden, ale `Finally` bloku ve funkci iterator se spustí. A `Catch` bloku uvnitř funkce iterator zachytí pouze výjimky, které nastat uvnitř funkce iterator.  
  
##  <a name="BKMK_AnonymousMethods"></a> Anonymní metody  
 V jazyce Visual Basic může být anonymní funkce iterator funkce. Toto dokládá následující příklad.  
  
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
  
 V následujícím příkladu má jiný iterator metodu, která ověří argumenty. Metoda vrací výsledek anonymní iterator, který popisuje elementy z kolekce.  
  
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
  
 Pokud se ověření místo uvnitř funkce iterator, ověření nelze provést, dokud nebude spuštění první iterace `For Each` textu.  
  
##  <a name="BKMK_GenericList"></a> Pomocí seznamu obecné iterátory  
 V následujícím příkladu `Stack(Of T)` – obecná třída implementuje <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní. `Push` Metoda přiřadí hodnoty do pole typu `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda vrátí pole hodnot pomocí `Yield` příkaz.  
  
 Kromě obecná <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, neobecnou <xref:System.Collections.IEnumerable.GetEnumerator%2A> také musí být implementována metoda. Důvodem je, že <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable>. Implementace neobecnou odkládat údaje pro obecnou implementaci.  
  
 Příklad používá pro podporu různých způsobů iterace v rámci stejné kolekce dat s názvem iterátory. Jsou to s názvem iterátory `TopToBottom` a `BottomToTop` vlastnosti a `TopN` metoda.  
  
 `BottomToTop` Zahrnuje deklarace vlastnosti `Iterator` – klíčové slovo.  
  
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
  
##  <a name="BKMK_SyntaxInformation"></a> Informace ze syntaxe  
 Může dojít iterator jako metodu nebo `get` přistupujícího objektu. Iterátor nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické destruktor.  
  
 Musí existovat implicitní převod z typu výrazu v `Yield` příkaz, který má návratový typ iteraci.  
  
 V jazyce Visual Basic, nemůže obsahovat metodu iterator ani `ByRef` parametry.  
  
 V jazyce Visual Basic "Výnos" není vyhrazené slovo a má zvláštní význam jenom v případě, že je používán `Iterator` metoda nebo `get` přistupujícího objektu.  
  
##  <a name="BKMK_Technical"></a> Technická implementace  
 I když napíšete iterovat jako metodu, kompilátor převede jej do vnořené třídy ve výsledku, který je stav počítače. Tato třída uchovává informace o umístění iterator jako dlouho `For Each...Next` pokračuje smyčky v kódu klienta.  
  
 Pokud chcete zobrazit, jaké kompilátor, můžete nástroj Ildasm.exe zobrazíte kód Microsoft intermediate language, který se vygeneruje pro metodu iterator.  
  
 Při vytváření iterace pro [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), není nutné implementovat celek <xref:System.Collections.IEnumerator> rozhraní. Zjistí-li kompilátor iteraci, automaticky vygeneruje `Current`, `MoveNext`, a `Dispose` metody <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní.  
  
 Při každém opakování následných `For Each…Next` smyčky (nebo přímé volání `IEnumerator.MoveNext`), těle další kód iterator obnoví po předchozí `Yield` příkaz. Bude pokračovat na další `Yield` prohlášení, dokud je dosaženo konce iterator text, nebo dokud se `Exit Function` nebo `Return` příkaz je zjistil.  
  
 Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metoda. Chcete-li procházení znovu od začátku, je nutné získat nové iterator.  
  
 Další informace najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
##  <a name="BKMK_UseOfIterators"></a> Použití iterátory  
 Iterátory umožňují zachovat jednoduchost `For Each` cykly, když potřebujete použít složitý kód pro naplnění seznamu pořadí. To může být užitečné, pokud chcete provést následující akce:  
  
-   Změňte pořadí seznamu po první `For Each` cykly iterací.  
  
-   Vyhněte se plně načítání velkých seznamu před první iterace `For Each` smyčky. Příkladem je stránkové fetch načíst dávku řádků tabulky. Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rozhraní .NET Framework.  
  
-   Zapouzdření vytváření seznamu v iteraci. V metodě iterator můžete sestavit v seznamu a pak yield každý výsledek ve smyčce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Příkaz Yield](../../../visual-basic/language-reference/statements/yield-statement.md)  
 [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
