---
title: Await – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 8e1462c7e0097bb2f04c6833a1bb279611b24133
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805507"
---
# <a name="await-operator-visual-basic"></a>Await – operátor (Visual Basic)
Můžete použít `Await` operátor a operand ve výrazu asynchronní metody nebo lambda pozastavit provádění metody až do dokončení awaited úloh. Úloha reprezentuje probíhající práce.  
  
 Metoda, ve kterém `Await` slouží musí mít [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor. Tato metoda, definované pomocí `Async` modifikátor a obvykle obsahující jednu nebo více `Await` výrazy, se označuje jako *asynchronní metody*.  
  
> [!NOTE]
>  Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012. Úvod do asynchronního programování, najdete v části [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Obvykle úloh, do které můžete použít `Await` operátor je vrácená hodnota z volání metody, která implementuje [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), která je <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.  
  
 V následujícím kódu <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí `getContentsTask`, `Task(Of Byte())`. Tato úloha je promise k vytvoření skutečné bajtové pole po dokončení operace. `Await` Operátor se použije pro `getContentsTask` pozastavit provádění v `SumPageSizesAsync` dokud `getContentsTask` dokončení. Do té doby ovládací prvek se vrátí do volajícího `SumPageSizesAsync`. Když `getContentsTask` po dokončení, `Await` výraz vyhodnocen jako bajtové pole.  
  
```vb  
Private Async Function SumPageSizesAsync() As Task  
  
    ' To use the HttpClient type in desktop apps, you must include a using directive and add a   
    ' reference for the System.Net.Http namespace.  
    Dim client As HttpClient = New HttpClient()   
    ' . . .   
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
    Dim urlContents As Byte() = Await getContentsTask  
  
    ' Equivalently, now that you see how it works, you can write the same thing in a single line.  
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ' . . .  
End Function  
```  
  
> [!IMPORTANT]
>  Úplný příklad najdete v tématu [návod: přístup k webu pomocí modifikátoru Async a Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Si můžete stáhnout ukázkový z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu společnosti Microsoft. Příkladem je v AsyncWalkthrough_HttpClient projektu.  
  
 Pokud `Await` se použije na výsledek volání metody, která vrátí `Task(Of TResult)`, typ `Await` TResult je výraz. Pokud `Await` se použije na výsledek volání metody, která vrátí `Task`, `Await` výraz nevrací hodnotu. Následující příklad ukazuje rozdíl.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` Výraz nebo příkaz neblokuje vláken, na kterém je prováděna. Místo toho ji způsobí, že kompilátor registrace zbytek asynchronní metody po `Await` výraz. pokračování v awaited úloze. Ovládací prvek pak vrátí volajícímu asynchronní metody. Po dokončení úlohy vyvolá jeho pokračování a spouštění obnoví asynchronní metody, kde bylo přerušeno.  
  
 `Await` Výrazu může dojít pouze v těle okamžitě nadřazených metoda nebo lambda výrazu, která je označena kvalifikátorem `Async` modifikátor. Termín *Await* slouží jako klíčové slovo pouze v tomto kontextu. Jinam je interpretován jako identifikátor. V rámci asynchronní metody nebo lambda výrazu `Await` výraz nemůže proběhnout ve výrazu dotazu v `catch` nebo `finally` blokovat z [zkuste... Catch... Nakonec](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) příkaz, ve smyčce řízení proměnné výrazu `For` nebo `For Each` smyčky, nebo v těle [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) příkaz.  
  
## <a name="exceptions"></a>Výjimky  
 Většina asynchronní metody vrátit <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Vlastnosti vrácený úlohy přenosu informací o jeho stav a historie, například zda byl dokončen, jestli asynchronní metody způsobila výjimku nebo byla zrušena a jaké konečný výsledek je. `Await` Operátor přistupuje k tyto vlastnosti.  
  
 Pokud await vrácení úloh asynchronní metody, které způsobí výjimku, `Await` operátor znovu vyvolá výjimku.  
  
 Pokud await vrácení úloh asynchronní metody, kterou zruší, `Await` znovu vyvolá operátor <xref:System.OperationCanceledException>.  
  
 Jeden úkol, který je v chybovém stavu skutečnost více výjimek.  Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Pokud jste await takové úlohy, znovu vyvolá operaci await pouze jeden z výjimky. Nelze však předpovědi, které výjimky znovu vyvolány.  
  
 Příklady zpracování chyb v asynchronní metody naleznete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Příklad  
 Windows Forms následující příklad ukazuje použití `Await` v použití asynchronní metody `WaitAsynchronouslyAsync`. Kontrastu chováním této metody s chováním `WaitSynchronously`. Bez `Await` operátor, `WaitSynchronously` spouští synchronně navzdory použití `Async` modifikátor v jeho definice a volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> v jeho obsahu.  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Async](../../../visual-basic/language-reference/modifiers/async.md)
