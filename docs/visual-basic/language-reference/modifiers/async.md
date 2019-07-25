---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: cf2c62878e8902afa9455c789d41393b73110172
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68434054"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)
Modifikátor označuje, že metoda nebo [výraz lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) , který se upraví, je asynchronní. `Async` Tyto metody jsou označovány jako *asynchronní metody*.  
  
 Asynchronní metoda představuje pohodlný způsob, jak provádět potenciálně dlouhotrvající práci bez blokování vlákna volání. Volající asynchronní metody může pokračovat v práci bez čekání na dokončení metody.  
  
> [!NOTE]
>  Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012. Úvod do asynchronního programování naleznete v tématu [asynchronní programování s Async a await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Následující příklad ukazuje strukturu asynchronní metody. Podle úmluvy názvy asynchronních metod končí slovem „Async“.  
  
```vb  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 Metoda upravená `Async` klíčovým slovem obvykle obsahuje alespoň jeden výraz [await](../../../visual-basic/language-reference/modifiers/async.md) nebo příkaz. Metoda pracuje synchronně, dokud nedosáhne prvního operátoru `Await`. V tomto okamžiku se provádění metody pozastaví až do dokončení očekávané úlohy. Během této doby je řízení předáno zpět volajícímu metody. Pokud metoda neobsahuje výraz nebo příkaz `Await`, není provádění metody pozastaveno a provede se stejně jako synchronní metoda. Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují slovo `Await`, protože tato situace může značit chybu. Další informace naleznete v tématu [Chyba kompilátoru](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 Klíčové slovo `Async` je nerezervované klíčové slovo. Pokud modifikuje metodu nebo výraz lambda, je klíčovým slovem. Ve všech ostatních kontextech je interpretováno jako identifikátor.  
  
## <a name="return-types"></a>Návratové typy  
 Asynchronní metoda je buď procedura [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , nebo procedura [funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) , která má <xref:System.Threading.Tasks.Task> návratový typ nebo. <xref:System.Threading.Tasks.Task%601> Metoda nemůže deklarovat žádné parametry [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .  
  
 Zadáte `Task(Of TResult)` pro návratový typ asynchronní metody, pokud příkaz [return](../../../visual-basic/language-reference/statements/return-statement.md) metody má operand typu TResult. Použijete `Task` , pokud není vrácena žádná smysluplná hodnota po dokončení metody. To znamená, že volání metody vrací typ `Task`, ale když je typ `Task` dokončen, žádný z příkazů `Await` čekajících na tento typ `Task` nevrátí výsledek.  
  
 Asynchronní podprogramy se používají především pro definování obslužných rutin událostí, kde je nutná procedura `Sub`. Volající asynchronního podprogramu ji nemůže očekávat ani zachytávat výjimky, které tato metoda vyvolá.  
  
 Další informace a příklady naleznete v tématu [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují asynchronní obslužnou rutinu události, asynchronní výraz lambda a asynchronní metodu. Úplný příklad, který používá tyto prvky, najdete v [tématu Názorný postup: Přístup k webu pomocí modifikátoru Async a](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)operátoru await Z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)si můžete stáhnout Návodný kód.  
  
```vb  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Operátor Await](../../../visual-basic/language-reference/operators/await-operator.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
