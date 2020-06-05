---
title: Await – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 9d55ba82547dfcb0336c3a3fd12521c0dcb3eb58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371827"
---
# <a name="await-operator-visual-basic"></a>Await – operátor (Visual Basic)

Operátor lze použít `Await` pro operand v asynchronní metodě nebo výrazu lambda pro pozastavení provádění metody, dokud není dokončen očekávaný úkol. Úkol představuje probíhající práci.

Metoda, ve které `Await` se používá, musí mít modifikátor [Async](../modifiers/async.md) . Taková metoda, která je definována pomocí `Async` modifikátoru a obvykle obsahuje jeden nebo více `Await` výrazů, je označována jako *asynchronní metoda*.

> [!NOTE]
> Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012. Úvod do asynchronního programování naleznete v tématu [asynchronní programování s Async a await](../../programming-guide/concepts/async/index.md).

Úkol, na který operátor použijete, `Await` je obvykle návratovou hodnotou z volání metody, která implementuje [asynchronní vzor založený na úlohách](https://www.microsoft.com/download/details.aspx?id=19957), to znamená, <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> .

V následujícím kódu <xref:System.Net.Http.HttpClient> Metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí hodnotu `getContentsTask` , `Task(Of Byte())` . Úkol je příslib, který vytvoří skutečné bajtové pole po dokončení operace. `Await`Operátor je použit na `getContentsTask` pro pozastavení provádění v, `SumPageSizesAsync` dokud `getContentsTask` není dokončeno. Mezitím se ovládací prvek vrátí volajícímu `SumPageSizesAsync` . Po `getContentsTask` dokončení se `Await` výraz vyhodnotí jako bajtové pole.

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
> Úplný příklad najdete v tématu [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Ukázku si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu Microsoftu. Příklad je v projektu AsyncWalkthrough_HttpClient.

Pokud `Await` je použita na výsledek volání metody, která vrací `Task(Of TResult)` , je typ `Await` výrazu TResult. Pokud `Await` je použita na výsledek volání metody, která vrací `Task` , `Await` výraz nevrátí hodnotu. Rozdíl je znázorněn v následujícím příkladu.

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

`Await`Výraz nebo příkaz neblokuje vlákno, ve kterém je prováděno. Místo toho způsobí, že kompilátor zaregistruje zbytek asynchronní metody za `Await` výraz, jako pokračování na očekávaném úkolu. Ovládací prvek se pak vrátí volajícímu asynchronní metody. Po dokončení úkolu vyvolá jeho pokračování a spuštění asynchronní metody pokračuje tam, kde skončila.

`Await`Výraz může nastat pouze v těle přímo ohraničující metody nebo lambda výraz, který je označen `Async` modifikátorem. Termín *await* slouží jako klíčové slovo pouze v tomto kontextu. Jinde je interpretován jako identifikátor. V rámci `Async` metody nebo výrazu lambda se `Await` výraz nemůže vyskytovat ve výrazu dotazu v `Catch` `Finally` bloku nebo bloku [Try... Zachytit... Finally](../statements/try-catch-finally-statement.md), ve výrazu řídicí proměnné smyčky `For` smyčky nebo nebo `For Each` v těle [SyncLock](../statements/synclock-statement.md) příkazu.

## <a name="exceptions"></a>Výjimky

Většina asynchronních metod vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> . Vlastnosti vrácené úlohy obsahují informace o jeho stavu a historii, například o tom, zda je úloha dokončena, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek. Tento `Await` operátor přistupuje k těmto vlastnostem.

Pokud očekáváte asynchronní metodu vracející úlohu, která způsobí výjimku, `Await` operátor znovu vyvolá výjimku.

Pokud očekáváte asynchronní metodu vracející úlohu, která je zrušena, operátor znovu `Await` vyvolá <xref:System.OperationCanceledException> .

Jeden úkol, který je v chybovém stavu, může odrážet více výjimek.  Například úloha může být výsledkem volání metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Pokud očekáváte takovou úlohu, operace Await znovu vyvolá pouze jednu výjimku. Nemůžete však odhadnout, které výjimky jsou znovu vyvolány.

Příklady zpracování chyb v asynchronních metodách naleznete v tématu [Try... Zachytit... Finally – příkaz](../statements/try-catch-finally-statement.md).

## <a name="example"></a>Příklad

Následující příklad model Windows Forms ukazuje použití `Await` v asynchronní metodě, `WaitAsynchronouslyAsync` . Kontrast s chováním této metody s chováním `WaitSynchronously` . Bez `Await` operátora `WaitSynchronously` běží synchronně navzdory použití `Async` modifikátoru v definici a volání do <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jeho těla.

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

- [Asynchronní programování s modifikátorem Async a operátoru await](../../programming-guide/concepts/async/index.md)
- [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../modifiers/async.md)
