---
title: Asynchronní programování pomocí modifikátoru Async a operátoru Await
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: ff028b3cbc00d54d8caf9e727cc487f96505beea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346691"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Asynchronous programming with Async and Await (Visual Basic)

Pomocí asynchronního programování se můžete vyhnout kritickým bodům a zlepšit celkovou rychlost reakce aplikace. Tradiční techniky pro psaní asynchronních aplikací však mohou být složité, takže je obtížné je napsat, ladit a udržovat.

Visual Studio 2012 introduced a simplified approach, async programming, that leverages asynchronous support in the .NET Framework 4.5 and higher as well as  in the Windows Runtime. Kompilátor na sebe přejímá náročnou práci, kterou vykonával vývojář, a vaše aplikace si zachovává logickou strukturu, která se podobá synchronnímu kódu. Výsledkem je, že získáte všechny výhody asynchronního programování při pouhém zlomku úsilí.

Toto téma obsahuje přehled kdy a jak použít asynchronní programování a obsahuje odkazy na témata podpory, která obsahují podrobné informace a příklady.

## <a name="BKMK_WhentoUseAsynchrony"></a> Async improves responsiveness

Asynchronie je nezbytná pro aktivity, které mohou potenciálně blokovat, například pokud vaše aplikace přistupuje na web. Přístup k webovému prostředku je někdy pomalý nebo zpožděný. Pokud je taková činnost blokována v rámci synchronního procesu, musí čekat celá aplikace. U asynchronního procesu může aplikace pokračovat v další práci, která nezávisí na webovém prostředku, dokud neskončí potenciálně blokující úloha.

Následující tabulka ukazuje typické oblasti, kde asynchronní programování zlepšuje rychlost reakce. The listed APIs from the  .NET Framework 4.5 and the Windows Runtime contain methods that support async programming.

|Oblast aplikace|Podpora rozhraní API, která obsahují asynchronní metody|
|----------------------|------------------------------------------------|
|Webový přístup|<xref:System.Net.Http.HttpClient>, <xref:Windows.Web.Syndication.SyndicationClient>|
|Práce se soubory|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|
|Práce s obrázky|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programování WCF|[Synchronní a asynchronní operace](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|
|||

Asynchronie je obzvláště užitečná pro aplikace, které přistupují k vláknu UI, protože všechny aktivity související s uživatelským rozhraním obvykle sdílí jedno vlákno. Pokud je jakýkoli proces blokován v synchronní aplikaci, jsou blokovány všechny. Vaše aplikace přestane reagovat a můžete dojít k závěru, že selhala, i když místo toho čeká.

Při použití asynchronních metod bude aplikace i nadále odpovídat na uživatelské rozhraní. Pokud nechcete čekat na dokončení, můžete změnit velikost nebo minimalizovat okno, například můžete zavřít aplikaci.

Asynchronní přístup přidává ekvivalent automatického přenosu do seznamu možností, z nichž můžete vybírat při vytváření asynchronní operace. To znamená, že získáte všechny výhody tradičního asynchronního programování, ale s mnohem menším úsilím ze strany vývojáře.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a> Async methods are easier to write

The [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await](../../../../visual-basic/language-reference/operators/await-operator.md) keywords in Visual Basic are the heart of async programming. By using those two keywords, you can use resources in the .NET Framework or the Windows Runtime to create an asynchronous method almost as easily as you create a synchronous method. Asynchronous methods that you define by using `Async` and `Await` are referred to as async methods.

Následující příklad ukazuje asynchronní metodu. Téměř vše v rámci kódu by vám mělo být zcela známé. Komentáře volají funkce, které jste přidali při tvorbě asynchronie.

You can find a complete Windows Presentation Foundation (WPF) example file at the end of this topic, and you can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

```vb
' Three things to note about writing an Async Function:
'  - The function has an Async modifier.
'  - Its return type is Task or Task(Of T). (See "Return Types" section.)
'  - As a matter of convention, its name ends in "Async".
Async Function AccessTheWebAsync() As Task(Of Integer)
    Using client As New HttpClient()
        ' Call and await separately.
        '  - AccessTheWebAsync can do other things while GetStringAsync is also running.
        '  - getStringTask stores the task we get from the call to GetStringAsync.
        '  - Task(Of String) means it is a task which returns a String when it is done.
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://docs.microsoft.com/dotnet")
        ' You can do other work here that doesn't rely on the string from GetStringAsync.
        DoIndependentWork()
        ' The Await operator suspends AccessTheWebAsync.
        '  - AccessTheWebAsync does not continue until getStringTask is complete.
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.
        '  - Control resumes here when getStringTask is complete.
        '  - The Await operator then retrieves the String result from getStringTask.
        Dim urlContents As String = Await getStringTask
        ' The Return statement specifies an Integer result.
        ' A method which awaits AccessTheWebAsync receives the Length value.
        Return urlContents.Length

    End Using

End Function
```

If `AccessTheWebAsync` doesn't have any work that it can do between calling `GetStringAsync` and awaiting its completion, you can simplify your code by calling and awaiting in the following single statement.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

The following characteristics summarize what makes the previous example an async method:

- The method signature includes an `Async` modifier.
- Název asynchronní metody končí podle konvence příponou „Async“.
- Návratový typ je jeden z následujících typů:

  - <xref:System.Threading.Tasks.Task%601> if your method has a return statement in which the operand has type TResult.
  - <xref:System.Threading.Tasks.Task> if your method has no return statement or has a return statement with no operand.
  - [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) if you're writing an async event handler.

  Další informace naleznete v části „Návratové typy a parametry“ dále v tomto tématu.

- Metoda obvykle zahrnuje nejméně jeden očekávaný výraz, který označuje bod, kde metoda nemůže pokračovat, dokud očekávaná asynchronní operace nebude dokončena. Během této doby je metoda pozastavena a ovládací prvek se vrátí volajícímu metody. Další část tohoto tématu ukazuje, co se stane v okamžiku pozastavení.

V asynchronních metodách používáte zadaná klíčová slova a typy pro označení, jakou akci chcete provést, a kompilátor udělá zbytek, včetně udržování přehledu o tom, co musí nastat, když se řízení vrátí do bodu „await“ pozastavené metody. Některé běžné procesy, jako je zpracování smyček a výjimek, může být v tradičním asynchronním kódu obtížné zpracovat. V asynchronní metodě zapisujete tyto prvky podobně, jako byste to udělali v synchronním řešení, a problém je vyřešen.

For more information about asynchrony in previous versions of the .NET Framework, see [TPL and Traditional .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> What happens in an Async method

Nejdůležitějším principem, který je třeba pochopit v asynchronním programování, je, jak ovládat přesuny toků od metody k metodě. The following diagram leads you through the process:

![Diagram that shows tracing an async program.](./media/index/navigation-trace-async-program.png)

The numbers in the diagram correspond to the following steps:

1. An event handler calls and awaits the `AccessTheWebAsync` async method.

2. `AccessTheWebAsync` creates an <xref:System.Net.Http.HttpClient> instance and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronous method to download the contents of a website as a string.

3. Something happens in `GetStringAsync` that suspends its progress. Možná je třeba vyčkat na dokončení stahování nebo jiné blokující aktivity na webu. To avoid blocking resources, `GetStringAsync` yields control to its caller, `AccessTheWebAsync`.

     `GetStringAsync` returns a <xref:System.Threading.Tasks.Task%601> where TResult is a string, and `AccessTheWebAsync` assigns the task to the `getStringTask` variable. The task represents the ongoing process for the call to `GetStringAsync`, with a commitment to produce an actual string value when the work is complete.

4. Because `getStringTask` hasn't been awaited yet, `AccessTheWebAsync` can continue with other work that doesn't depend on the final result from `GetStringAsync`. That work is represented by a call to the synchronous method `DoIndependentWork`.

5. `DoIndependentWork` is a synchronous method that does its work and returns to its caller.

6. `AccessTheWebAsync` has run out of work that it can do without a result from `getStringTask`. `AccessTheWebAsync` next wants to calculate and return the length of the downloaded string, but the method can't calculate that value until the method has the string.

     Therefore, `AccessTheWebAsync` uses an await operator to suspend its progress and to yield control to the method that called `AccessTheWebAsync`. `AccessTheWebAsync` returns a `Task<int>` (`Task(Of Integer)` in Visual Basic) to the caller. Úloha představuje slib vyrábět celé číslo výsledku, který má délku staženého řetězce.

    > [!NOTE]
    > If `GetStringAsync` (and therefore `getStringTask`) is complete before `AccessTheWebAsync` awaits it, control remains in `AccessTheWebAsync`. The expense of suspending and then returning to `AccessTheWebAsync` would be wasted if the called asynchronous process (`getStringTask`) has already completed and AccessTheWebSync doesn't have to wait for the final result.

     Uvnitř volajícího (v tomto případě obslužná rutina události) bude vzor zpracování pokračovat. The caller might do other work that doesn't depend on the result from `AccessTheWebAsync` before awaiting that result, or the caller might await immediately.   The event handler is waiting for `AccessTheWebAsync`, and `AccessTheWebAsync` is waiting for `GetStringAsync`.

7. `GetStringAsync` completes and produces a string result. The string result isn't returned by the call to `GetStringAsync` in the way that you might expect. (Remember that the method already returned a task in step 3.) Instead, the string result is stored in the task that represents the completion of the method, `getStringTask`. The await operator retrieves the result from `getStringTask`. The assignment statement assigns the retrieved result to `urlContents`.

8. When `AccessTheWebAsync` has the string result, the method can calculate the length of the string. Then the work of `AccessTheWebAsync` is also complete, and the waiting event handler can resume. V úplném příkladu na konci tématu si můžete potvrdit, že obslužná rutina události načte a vytiskne hodnotu výsledné délky.

Pokud jste v oblasti asynchronního programování nováčky, zvažte rozdíl mezi synchronním a asynchronním chováním. Synchronní metoda je vrácena, jakmile je její práce dokončena (krok 5), ale asynchronní metoda vrátí hodnotu úlohy, když je její práce pozastavena (kroky 3 a 6). Když asynchronní metoda nakonec dokončí svou práci, je úloha označena jako dokončená a výsledek, pokud existuje, je uložen v úloze.

For more information about control flow, see [Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a> API Async Methods

You might be wondering where to find methods such as `GetStringAsync` that support async programming. The .NET Framework 4.5 or higher contains many members that work with `Async` and `Await`. You can recognize these members by the "Async" suffix that's attached to the member name and a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>. For example, the `System.IO.Stream` class contains methods such as <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> alongside the synchronous methods <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, and <xref:System.IO.Stream.Write%2A>.

The Windows Runtime also contains many methods that you can use with `Async` and `Await` in Windows apps. For more information and example methods, see [Call asynchronous APIs in C# or Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [Asynchronous programming (Windows Runtime apps)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)), and [WhenAny: Bridging between the .NET Framework and the Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).

## <a name="BKMK_Threads"></a> Threads

Asynchronní metody mají být neblokující operace. An `Await` expression in an async method doesn't block the current thread while the awaited task is running. Namísto toho se výraz zaregistruje pro zbývající metody jako pokračování a vrátí řízení volajícímu asynchronní metody.

The `Async` and `Await` keywords don't cause additional threads to be created. Async methods don't require multi-threading because an async method doesn't run on its own thread. Metoda pracuje na aktuálním kontextu synchronizace a používá čas ve vlákně pouze v případě, že je metoda aktivní. You can use <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> to move CPU-bound work to a background thread, but a background thread doesn't help with a process that's just waiting for results to become available.

Asynchronní přístup při asynchronním programování se doporučuje v téměř každém případě existujících přístupů. In particular, this approach is better than <xref:System.ComponentModel.BackgroundWorker> for I/O-bound operations because the code is simpler and you don't have to guard against race conditions. In combination with <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, async programming is better than <xref:System.ComponentModel.BackgroundWorker> for CPU-bound operations because async programming separates the coordination details of running your code from the work that `Task.Run` transfers to the threadpool.

## <a name="BKMK_AsyncandAwait"></a> Async and Await

If you specify that a method is an async method by using an [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier, you enable the following two capabilities.

- The marked async method can use [Await](../../../../visual-basic/language-reference/operators/await-operator.md) to designate suspension points. Operátor await sděluje kompilátoru, že s asynchronními metodami nelze za daným bodem pokračovat, dokud nebude dokončen očekávaný asynchronní proces. Během této doby se ovládací prvek vrátí volajícímu asynchronní metody.

  The suspension of an async method at an `Await` expression doesn't constitute an exit from the method, and `Finally` blocks don't run.

- Samotná označená asynchronní metoda může být očekávána metodami, které ji volaly.

An async method typically contains one or more occurrences of an `Await` operator, but the absence of `Await` expressions doesn't cause a compiler error. If an async method doesn't use an `Await` operator to mark a suspension point, the method executes as a synchronous method does, despite the `Async` modifier. Kompilátor u takových metod zahlásí upozornění.

`Async` and `Await` are contextual keywords. Další informace a příklady naleznete v následujících tématech:

- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="BKMK_ReturnTypesandParameters"></a> Return types and parameters

In .NET Framework programming, an async method typically returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>. Inside an async method, an `Await` operator is applied to a task that's returned from a call to another async method.

You specify <xref:System.Threading.Tasks.Task%601> as the return type if the method contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that specifies an operand of type `TResult`.

You use `Task` as the return type if the method has no return statement or has a return statement that doesn't return an operand.

The following example shows how you declare and call a method that returns a <xref:System.Threading.Tasks.Task%601> or a <xref:System.Threading.Tasks.Task>:

```vb
' Signature specifies Task(Of Integer)
Async Function TaskOfTResult_MethodAsync() As Task(Of Integer)

    Dim hours As Integer
    ' . . .
    ' Return statement specifies an integer result.
    Return hours
End Function

' Calls to TaskOfTResult_MethodAsync
Dim returnedTaskTResult As Task(Of Integer) = TaskOfTResult_MethodAsync()
Dim intResult As Integer = Await returnedTaskTResult
' or, in a single statement
Dim intResult As Integer = Await TaskOfTResult_MethodAsync()

' Signature specifies Task
Async Function Task_MethodAsync() As Task

    ' . . .
    ' The method has no return statement.
End Function

' Calls to Task_MethodAsync
Task returnedTask = Task_MethodAsync()
Await returnedTask
' or, in a single statement
Await Task_MethodAsync()
```

Každá vrácená úloha představuje probíhající práci. Úloha zapouzdřuje informace o stavu asynchronního procesu a posléze buď konečný výsledek z procesu, nebo výjimku, kterou proces vyvolá v případě neúspěchu.

An async method can also be a `Sub` method. This return type is used primarily to define event handlers, where a return type is required. Asynchronní obslužné rutiny událostí často slouží jako výchozí bod pro asynchronní programy.

An async method that's a `Sub` procedure can't be awaited, and the caller can't catch any exceptions that the method throws.

An async method can't declare [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parameters, but the method can call methods that have such parameters.

For more information and examples, see [Async Return Types (Visual Basic)](async-return-types.md). For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Asynchronous APIs in Windows Runtime programming have one of the following return types, which are similar to tasks:

- <xref:Windows.Foundation.IAsyncOperation%601>, which corresponds to <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, which corresponds to <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

For more information and an example, see [Call asynchronous APIs in C# or Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="BKMK_NamingConvention"></a> Naming convention

By convention, you append "Async" to the names of methods that have an `Async` modifier.

Můžete ignorovat konvenci, kde událost, základní třída a rozhraní smlouvy navrhují odlišný název. For example, you shouldn't rename common event handlers, such as `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a> Related topics and samples (Visual Studio)

|Název|Popis|Ukázka|
|-----------|-----------------|------------|
|[Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)|Ukazuje, jak převést synchronní řešení WPF na asynchronní řešení WPF. Aplikace stáhne řadu webových stránek.|[Async Sample: Accessing the Web Walkthrough](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Adds <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> to the previous walkthrough. The use of `WhenAll` starts all the downloads at the same time.||
|[How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ukazuje, jak spustit několik úloh současně.|[Async Sample: Make Multiple Web Requests in Parallel](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Async Return Types (Visual Basic)](async-return-types.md)|Znázorňuje typy, které může vrátit asynchronní metoda, a vysvětluje, kdy se každý typ hodí.||
|[Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md)|Podrobně sleduje tok řízení pomocí sledu očekávání výrazů v asynchronním programu.|[Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md)|Ukazuje, jak přidat k asynchronnímu řešení následující funkce:<br /><br /> - [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Cancel Async Tasks after a Period of Time (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)<br />- [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Handling Reentrancy in Async Apps (Visual Basic)](handling-reentrancy-in-async-apps.md)|Shows how to handle cases in which an active asynchronous operation is restarted while it's running.||
|[WhenAny: Bridging between the .NET Framework and the Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the Windows Runtime so that you can use <xref:System.Threading.Tasks.Task.WhenAny%2A> with a Windows Runtime method.|[Async Sample: Bridging between .NET and Windows Runtime (AsTask and WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Asynchronní zrušení: přemostění rozhraní .NET Framework a prostředí Windows Runtime|Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the Windows Runtime so that you can use <xref:System.Threading.CancellationTokenSource> with a Windows Runtime method.|[Async Sample: Bridging between .NET and Windows Runtime (AsTask & Cancellation)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Using Async for File Access (Visual Basic)](using-async-for-file-access.md)|Seznam a ukázka výhod použití operátorů async a await při přístupu k souborům.||
|[Asynchronní vzor založený na úlohách (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Popisuje nový vzor pro asynchronii v rozhraní .NET Framework. The pattern is based on the <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> types.||
|[Async Videos on Channel 9](https://channel9.msdn.com/search?term=async+&type=All)|Poskytuje odkazy na různá videa o asynchronním programování.||

## <a name="BKMK_CompleteExample"></a> Complete Example

The following code is the MainWindow.xaml.vb file from the Windows Presentation Foundation (WPF) application that this topic discusses. You can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-vb/).

[!code-vb[async](~/samples/async/async-and-await/vb/MainWindow.xaml.vb)]

## <a name="see-also"></a>Viz také:

- [Operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
