---
title: Await – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d3bfafaa696955422c381aa1c17bc96591b44985
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962001"
---
# <a name="await-operator-visual-basic"></a>Await – operátor (Visual Basic)
`Await` Operátor lze použít pro operand v asynchronní metodě nebo výrazu lambda pro pozastavení provádění metody, dokud není dokončen očekávaný úkol. Úkol představuje probíhající práci.  
  
 Metoda, ve které `Await` se používá, musí mít modifikátor [Async](../../../visual-basic/language-reference/modifiers/async.md) . Taková metoda, která je definována pomocí `Async` modifikátoru a obvykle obsahuje jeden nebo více `Await` výrazů, je označována jako *asynchronní metoda*.  
  
> [!NOTE]
> Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012. Úvod do asynchronního programování naleznete v tématu [asynchronní programování s Async a await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Úkol, na `Await` který operátor použijete, je obvykle návratovou hodnotou z volání metody, která implementuje [asynchronní vzor založený na úlohách](https://go.microsoft.com/fwlink/?LinkId=204847), <xref:System.Threading.Tasks.Task> to znamená <xref:System.Threading.Tasks.Task%601>, nebo.  
  
 V následujícím kódu <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí `getContentsTask`hodnotu, `Task(Of Byte())`. Úkol je příslib, který vytvoří skutečné bajtové pole po dokončení operace. Operátor je použit na `getContentsTask` pro pozastavení provádění v, `SumPageSizesAsync` dokud `getContentsTask` není dokončeno. `Await` Mezitím se ovládací prvek vrátí volajícímu `SumPageSizesAsync`. Po `getContentsTask` dokončení`Await` se výraz vyhodnotí jako bajtové pole.  
  
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
> Úplný příklad najdete v tématu [Návod: Přístup k webu pomocí modifikátoru Async a](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)operátoru await Ukázku si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu Microsoftu. Příklad je v projektu AsyncWalkthrough_HttpClient.  
  
 Pokud `Await` je použita na výsledek volání metody, která `Task(Of TResult)`vrací `Await` , je typ výrazu TResult. Pokud `Await` je použita na výsledek volání metody, která `Task`vrací, `Await` výraz nevrátí hodnotu. Rozdíl je znázorněn v následujícím příkladu.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` Výraz nebo příkaz neblokuje vlákno, ve kterém je prováděno. Místo toho způsobí, že kompilátor zaregistruje zbytek asynchronní metody za `Await` výraz, jako pokračování na očekávaném úkolu. Ovládací prvek se pak vrátí volajícímu asynchronní metody. Po dokončení úkolu vyvolá jeho pokračování a spuštění asynchronní metody pokračuje tam, kde skončila.  
  
 Výraz může nastat pouze v těle přímo ohraničující metody nebo lambda výraz, který je označen `Async` modifikátorem. `Await` Termín *await* slouží jako klíčové slovo pouze v tomto kontextu. Jinde je interpretován jako identifikátor. V rámci asynchronní metody nebo výrazu lambda se `Await` výraz nemůže vyskytovat ve výrazu dotazu `catch` v bloku nebo `finally` bloku [Try... Zachytit... Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) , ve výrazu `For` řídicí proměnné smyčky smyčky nebo `For Each` nebo v těle [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) příkazu.  
  
## <a name="exceptions"></a>Výjimky  
 Většina asynchronních metod vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Vlastnosti vrácené úlohy obsahují informace o jeho stavu a historii, například o tom, zda je úloha dokončena, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek. Tento `Await` operátor přistupuje k těmto vlastnostem.  
  
 Pokud očekáváte asynchronní metodu vracející úlohu, která způsobí výjimku, `Await` operátor znovu vyvolá výjimku.  
  
 Pokud očekáváte asynchronní metodu vracející úlohu, která je zrušena, `Await` operátor znovu vyvolá. <xref:System.OperationCanceledException>  
  
 Jeden úkol, který je v chybovém stavu, může odrážet více výjimek.  Například úloha může být výsledkem volání metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Pokud očekáváte takovou úlohu, operace Await znovu vyvolá pouze jednu výjimku. Nemůžete však odhadnout, které výjimky jsou znovu vyvolány.  
  
 Příklady zpracování chyb v asynchronních metodách naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad model Windows Forms ukazuje použití `Await` v asynchronní metodě,. `WaitAsynchronouslyAsync` Kontrast s chováním této metody s chováním `WaitSynchronously`. `Await` Bez `Async` <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> operátora běžísynchronněnavzdorypoužitímodifikátoruvdefiniciavolání`WaitSynchronously` do jeho těla.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
