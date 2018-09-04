---
title: Await – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 2094ba308ba384feb8542e896cb1eafcf645947c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524463"
---
# <a name="await-operator-visual-basic"></a>Await – operátor (Visual Basic)
Můžete použít `Await` operátor operandem v asynchronní metodě nebo výrazu lambda výraz k pozastavení provádění metody až do dokončení očekávané úlohy. Úloha představuje probíhající práci.  
  
 Metody, ve které `Await` slouží musí mít [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor. Tato metoda, definována pomocí `Async` modifikátor a obvykle obsahuje jeden nebo více `Await` výrazy, se označuje jako *asynchronní metoda*.  
  
> [!NOTE]
>  Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012. Úvod do asynchronního programování naleznete v tématu [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Obvykle, úkol, na který je použit `Await` operátor je návratová hodnota z volání metody, která implementuje [Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=204847), která je <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.  
  
 V následujícím kódu <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí `getContentsTask`, `Task(Of Byte())`. Úkol je příslib z k vytvoření pole bajtů po dokončení operace. `Await` Je použit operátor `getContentsTask` k pozastavení provádění v `SumPageSizesAsync` dokud `getContentsTask` je dokončena. Do té doby se ovládací prvek vrátí volajícímu metody `SumPageSizesAsync`. Když `getContentsTask` dokončení `Await` výraz vyhodnocen jako bajtové pole.  
  
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
>  Kompletní příklad naleznete v tématu [návod: přístup k webu pomocí Async a Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Můžete stáhnout ukázku z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu společnosti Microsoft. V příkladu je v projektu AsyncWalkthrough_HttpClient.  
  
 Pokud `Await` se použije na výsledek volání metody, která vrací `Task(Of TResult)`, typ `Await` výraz je TResult. Pokud `Await` se použije na výsledek volání metody, která vrací `Task`, `Await` výraz nevrací hodnotu. Následující příklad ukazuje rozdíl.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` Výraz nebo příkaz neblokuje vlákno, na kterém je spuštěn. Místo toho to způsobí, že kompilátor zapíše zbytek asynchronní metody po `Await` výraz jako pokračování očekávané úlohy. Ovládací prvek vrátí volajícímu asynchronní metody. Po dokončení úkolu vyvolá jeho pokračování a provádění asynchronní metody pokračuje tam, kde skončila.  
  
 `Await` Výraz může dojít pouze v těle bezprostředně vložená metoda nebo lambda výraz, který je označen `Async` modifikátor. Termín *Await* slouží jako klíčové slovo pouze v tomto kontextu. Jinde je interpretován jako identifikátor. V rámci asynchronní metody nebo lambda výrazu `Await` výraz nemůže nastat ve výrazu dotazu v `catch` nebo `finally` bloku [zkuste... Catch... Nakonec](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) výroky ovládací prvek proměnné výraz smyčky `For` nebo `For Each` smyčku, nebo v těle [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) příkazu.  
  
## <a name="exceptions"></a>Výjimky  
 Většina asynchronních metod vrátí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Vlastnosti vrácené úlohy nesou informaci o jejím stavu a historii, např. Určuje, zda je úkol dokončený, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek je. `Await` Operátor má přístup k těmto vlastnostem.  
  
 Pokud očekáváte vracející úlohy asynchronní metodu, která způsobí výjimku, `Await` operátor znovu vyvolá výjimku.  
  
 Pokud očekáváte vracející úlohy asynchronní metody, která je zrušena, `Await` znovu vyvolá operátor <xref:System.OperationCanceledException>.  
  
 Jeden úkol, který je v chybovém stavu, může odrážet více výjimek.  Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Když budete očekávat takový úkol, operace await vrátí pouze jednu z výjimek. Nelze však předpovědět, které výjimky je znovu vyvolána.  
  
 Příklady zpracování chyb v asynchronních metodách, naleznete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad Windows Forms ukazuje použití `Await` v asynchronní metodě, `WaitAsynchronouslyAsync`. Kontrast v chování dané metody s chováním `WaitSynchronously`. Bez `Await` operátor `WaitSynchronously` pracuje synchronně navzdory použití `Async` modifikátoru v definici a volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> v jeho textu.  
  
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
