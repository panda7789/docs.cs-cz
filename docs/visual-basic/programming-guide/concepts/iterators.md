---
title: Iterátory (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: db84e5d7956f0b160520fa831607e3f7548fc976
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913155"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="1ce2f-102">Iterátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce2f-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="1ce2f-103">*Iterátor* se dá použít ke krokování kolekcí, jako jsou seznamy a pole.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="1ce2f-104">Metoda iterátoru nebo `get` přistupující objekt provádí vlastní iteraci v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="1ce2f-105">Metoda iterátoru používá příkaz [yield](../../../visual-basic/language-reference/statements/yield-statement.md) k vrácení každého prvku v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="1ce2f-106">Při dosažení `Yield` příkazu je aktuální umístění v kódu zapamatovatelné.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="1ce2f-107">Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="1ce2f-108">Využijete iterátor z klientského kódu pomocí [pro každý... Další](../../../visual-basic/language-reference/statements/for-each-next-statement.md) příkaz nebo pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="1ce2f-109">V následujícím příkladu první iterace `For Each` smyčky způsobí, že provádění pokračuje `SomeNumbers` v metodě iterátoru, dokud není dosaženo prvního `Yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="1ce2f-110">Tato iterace vrátí hodnotu 3 a aktuální umístění v metodě iterátoru se zachová.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="1ce2f-111">Při další iteraci smyčky pokračuje spuštění v metodě iterátoru z místa, kde skončilo, a opětovné zastavení při dosažení `Yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="1ce2f-112">Tato iterace vrátí hodnotu 5 a aktuální umístění v metodě iterátoru se znovu zachová.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="1ce2f-113">Smyčka skončí po dosažení konce metody iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
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
  
 <span data-ttu-id="1ce2f-114">`get` Návratový typ metody iterátoru nebo přístupového objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="1ce2f-115">K ukončení iterace `Exit Function` můžete `Return` použít příkaz or.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="1ce2f-116">Funkce iterátoru Visual Basic nebo `get` deklarace přístupového objektu obsahuje modifikátor [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md) .</span><span class="sxs-lookup"><span data-stu-id="1ce2f-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="1ce2f-117">Iterátory byly představeny v Visual Basic v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="1ce2f-118">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="1ce2f-118">**In this topic**</span></span>  
  
- [<span data-ttu-id="1ce2f-119">Jednoduchý iterátor</span><span class="sxs-lookup"><span data-stu-id="1ce2f-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
- [<span data-ttu-id="1ce2f-120">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="1ce2f-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
- [<span data-ttu-id="1ce2f-121">Bloky try</span><span class="sxs-lookup"><span data-stu-id="1ce2f-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
- [<span data-ttu-id="1ce2f-122">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="1ce2f-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
- [<span data-ttu-id="1ce2f-123">Používání iterátorů s obecným seznamem</span><span class="sxs-lookup"><span data-stu-id="1ce2f-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
- [<span data-ttu-id="1ce2f-124">Informace o syntaxi</span><span class="sxs-lookup"><span data-stu-id="1ce2f-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
- [<span data-ttu-id="1ce2f-125">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="1ce2f-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
- [<span data-ttu-id="1ce2f-126">Používání iterátorů</span><span class="sxs-lookup"><span data-stu-id="1ce2f-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
> <span data-ttu-id="1ce2f-127">Pro všechny příklady v tématu s výjimkou příkladu jednoduchého iterátoru [](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) uveďte příkazy Imports `System.Collections` pro `System.Collections.Generic` obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
## <a name="BKMK_SimpleIterator"></a><span data-ttu-id="1ce2f-128">Jednoduchý iterátor</span><span class="sxs-lookup"><span data-stu-id="1ce2f-128">Simple Iterator</span></span>  
 <span data-ttu-id="1ce2f-129">V následujícím příkladu je jeden `Yield` příkaz, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka</span><span class="sxs-lookup"><span data-stu-id="1ce2f-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="1ce2f-130">V `Main`, Každá iterace `For Each` těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `Yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="BKMK_CollectionClass"></a><span data-ttu-id="1ce2f-131">Vytvoření třídy kolekce</span><span class="sxs-lookup"><span data-stu-id="1ce2f-131">Creating a Collection Class</span></span>  
 <span data-ttu-id="1ce2f-132">V následujícím příkladu `DaysOfTheWeek` třída <xref:System.Collections.IEnumerable> implementuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> rozhraní, které vyžaduje metodu.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="1ce2f-133">Kompilátor implicitně volá `GetEnumerator` metodu, která <xref:System.Collections.IEnumerator>vrací.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="1ce2f-134">Metoda vrátí každý řetězec po jednom `Yield` pomocí příkazu a `Iterator` modifikátor je v deklaraci funkce. `GetEnumerator`</span><span class="sxs-lookup"><span data-stu-id="1ce2f-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
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
  
 <span data-ttu-id="1ce2f-135">Následující příklad vytvoří `Zoo` třídu, která obsahuje kolekci zvířat.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="1ce2f-136">Příkaz, který odkazuje na instanci třídy (`theZoo` `GetEnumerator` ) implicitně volá metodu. `For Each`</span><span class="sxs-lookup"><span data-stu-id="1ce2f-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="1ce2f-137">Příkazy, které odkazují `Birds` na vlastnosti a `Mammals` používají `AnimalsForType` metodu s názvem iterátor. `For Each`</span><span class="sxs-lookup"><span data-stu-id="1ce2f-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
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
  
## <a name="BKMK_TryBlocks"></a><span data-ttu-id="1ce2f-138">Bloky try</span><span class="sxs-lookup"><span data-stu-id="1ce2f-138">Try Blocks</span></span>  
 <span data-ttu-id="1ce2f-139">Visual Basic povoluje `Yield` příkaz `Try` v bloku [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1ce2f-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="1ce2f-140">Blok, který `Yield` má příkaz, může mít `Catch` bloky a může mít `Finally` blok. `Try`</span><span class="sxs-lookup"><span data-stu-id="1ce2f-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="1ce2f-141">Následující příklad obsahuje `Try`bloky, `Catch`a `Finally` ve funkci iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="1ce2f-142">Blok `Finally` ve funkci iterátoru se provede `For Each` před dokončením iterace.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
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
  
 <span data-ttu-id="1ce2f-143">Příkaz nemůže být `Catch` uvnitř bloku nebo `Finally` bloku. `Yield`</span><span class="sxs-lookup"><span data-stu-id="1ce2f-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="1ce2f-144">Pokud tělo (místo metody iterátoru) vyvolá výjimku `Catch` , není proveden blok ve funkci iterátoru, ale `Finally` je proveden blok ve funkci iterátoru. `For Each`</span><span class="sxs-lookup"><span data-stu-id="1ce2f-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="1ce2f-145">`Catch` Blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="BKMK_AnonymousMethods"></a><span data-ttu-id="1ce2f-146">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="1ce2f-146">Anonymous Methods</span></span>  
 <span data-ttu-id="1ce2f-147">V Visual Basic může být anonymní funkcí funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="1ce2f-148">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-148">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="1ce2f-149">V následujícím příkladu je metoda bez iterátoru, která ověřuje argumenty.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="1ce2f-150">Metoda vrací výsledek anonymního iterátoru, který popisuje prvky kolekce.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
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
  
 <span data-ttu-id="1ce2f-151">Pokud je ověřování místo v rámci funkce iterátoru, nelze provést ověření až do začátku první iterace `For Each` těla.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
## <a name="BKMK_GenericList"></a><span data-ttu-id="1ce2f-152">Používání iterátorů s obecným seznamem</span><span class="sxs-lookup"><span data-stu-id="1ce2f-152">Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="1ce2f-153">V následujícím příkladu `Stack(Of T)` obecná třída <xref:System.Collections.Generic.IEnumerable%601> implementuje obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="1ce2f-154">Metoda přiřadí hodnoty k poli typu `T`. `Push`</span><span class="sxs-lookup"><span data-stu-id="1ce2f-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="1ce2f-155">Metoda vrací hodnoty pole `Yield` pomocí příkazu. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="1ce2f-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="1ce2f-156">Kromě obecné <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody musí být také implementována neobecná <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="1ce2f-157">Důvodem je, <xref:System.Collections.Generic.IEnumerable%601> že dědí <xref:System.Collections.IEnumerable>z.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="1ce2f-158">Neobecná implementace se odloží k obecné implementaci.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="1ce2f-159">Tento příklad používá pojmenované iterátory k podpoře různých způsobů iterace v rámci stejné kolekce dat.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="1ce2f-160">Tyto pojmenované iterátory jsou `TopToBottom` vlastnosti a `BottomToTop` a `TopN` metoda.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="1ce2f-161">Deklarace `BottomToTop` vlastnosti `Iterator` zahrnuje klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
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
  
## <a name="BKMK_SyntaxInformation"></a><span data-ttu-id="1ce2f-162">Informace o syntaxi</span><span class="sxs-lookup"><span data-stu-id="1ce2f-162">Syntax Information</span></span>  
 <span data-ttu-id="1ce2f-163">Iterátor se může vyskytnout jako metoda nebo `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="1ce2f-164">Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="1ce2f-165">Implicitní převod musí existovat v typu výrazu v `Yield` příkazu na návratový typ iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="1ce2f-166">V Visual Basic metoda iterátoru nemůže mít žádné `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="1ce2f-167">V Visual Basic "yield" není rezervované slovo a má zvláštní význam pouze v případě, že je použit v `Iterator` metodě nebo `get` přístupovém objektu.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
## <a name="BKMK_Technical"></a><span data-ttu-id="1ce2f-168">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="1ce2f-168">Technical Implementation</span></span>  
 <span data-ttu-id="1ce2f-169">I když zapisujete iterátor jako metodu, kompilátor je převede na vnořenou třídu, která je v podstatě Stavový počítač.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="1ce2f-170">Tato třída uchovává informace o poloze iterátoru, dokud `For Each...Next` smyčka v kódu klienta pokračuje.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="1ce2f-171">Chcete-li zjistit, co kompilátor dělá, můžete použít nástroj Ildasm. exe k zobrazení kódu zprostředkujícího jazyka společnosti Microsoft, který je generován pro metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="1ce2f-172">Při vytváření iterátoru pro [třídu](../../../csharp/language-reference/keywords/class.md) nebo [strukturu](../../../csharp/language-reference/keywords/struct.md)není nutné implementovat celé <xref:System.Collections.IEnumerator> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="1ce2f-173">Když kompilátor detekuje iterátor, automaticky `Current`generuje metody <xref:System.Collections.IEnumerator> , `MoveNext`a `Dispose` rozhraní nebo <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="1ce2f-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="1ce2f-174">U každé následné iterace `For Each…Next` smyčky (nebo přímého `IEnumerator.MoveNext`volání) pokračuje další tělo kódu iterátoru za předchozím `Yield` příkazem.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="1ce2f-175">Pak pokračuje k dalšímu `Yield` příkazu, dokud není dosaženo konce textu iterátoru nebo `Exit Function` dokud se nezjistí příkaz or `Return` .</span><span class="sxs-lookup"><span data-stu-id="1ce2f-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="1ce2f-176">Iterátory nepodporují <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1ce2f-177">Pokud chcete opakovat iteraci od začátku, musíte získat nový iterátor.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="1ce2f-178">Další informace najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ce2f-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>  
  
## <a name="BKMK_UseOfIterators"></a><span data-ttu-id="1ce2f-179">Používání iterátorů</span><span class="sxs-lookup"><span data-stu-id="1ce2f-179">Use of Iterators</span></span>  
 <span data-ttu-id="1ce2f-180">Iterátory umožňují udržovat jednoduchost `For Each` smyčky, pokud potřebujete použít složitý kód k naplnění pořadí seznamu.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="1ce2f-181">To může být užitečné v případě, že chcete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="1ce2f-181">This can be useful when you want to do the following:</span></span>  
  
- <span data-ttu-id="1ce2f-182">Změňte pořadí seznamu po iteraci první `For Each` smyčky.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
- <span data-ttu-id="1ce2f-183">Vyhněte se úplnému načítání velkého seznamu před první iterací `For Each` smyčky.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="1ce2f-184">Příkladem stránkovaného načtení je načtení dávky řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="1ce2f-185">Dalším příkladem je <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metoda, která implementuje iterátory v rámci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
- <span data-ttu-id="1ce2f-186">Zapouzdřit sestavení seznamu v iterátoru.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="1ce2f-187">V metodě iterátoru můžete sestavit seznam a pak každý výsledek vracet ve smyčce.</span><span class="sxs-lookup"><span data-stu-id="1ce2f-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce2f-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ce2f-188">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="1ce2f-189">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="1ce2f-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="1ce2f-190">Příkaz Yield</span><span class="sxs-lookup"><span data-stu-id="1ce2f-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
- [<span data-ttu-id="1ce2f-191">Iterator</span><span class="sxs-lookup"><span data-stu-id="1ce2f-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)
