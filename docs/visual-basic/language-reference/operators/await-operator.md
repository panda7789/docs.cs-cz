---
title: Await – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: c2389ff0c94afc2156e594f5d93535d1ed0107a8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336267"
---
# <a name="await-operator-visual-basic"></a>Await – operátor (Visual Basic)

Operátor `Await` použijete pro operand v asynchronní metodě nebo výrazu lambda pro pozastavení provádění metody, dokud není dokončen očekávaný úkol. Úkol představuje probíhající práci.

Metoda, ve které je použit `Await`, musí mít modifikátor [Async](../../../visual-basic/language-reference/modifiers/async.md) . Taková metoda, definovaná pomocí modifikátoru `Async` a obvykle obsahující jeden nebo více `Await` výrazů, je označována jako *asynchronní metoda*.

> [!NOTE]
> Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012. Úvod do asynchronního programování naleznete v tématu [asynchronní programování s Async a await](../../../visual-basic/programming-guide/concepts/async/index.md).

Úkol, pro který použijete operátor `Await`, je obvykle návratovou hodnotou z volání metody, která implementuje [asynchronní vzor založený na úlohách](https://go.microsoft.com/fwlink/?LinkId=204847), to znamená <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.

V následujícím kódu metoda <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> vrátí `getContentsTask`, `Task(Of Byte())`. Úkol je příslib, který vytvoří skutečné bajtové pole po dokončení operace. Operátor `Await` se použije pro `getContentsTask` k pozastavení provádění v `SumPageSizesAsync`, dokud `getContentsTask` nedokončí. Mezitím se ovládací prvek vrátí volajícímu `SumPageSizesAsync`. Po dokončení `getContentsTask` se výraz `Await` vyhodnotí jako bajtové pole.

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
> Úplný příklad najdete v tématu [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Ukázku si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu Microsoftu. Příklad je v projektu AsyncWalkthrough_HttpClient.

Pokud je použita `Await` pro výsledek volání metody, která vrací `Task(Of TResult)`, je typ `Await`ho výrazu TResult. Pokud je použita `Await` pro výsledek volání metody, která vrací `Task`, výraz `Await` nevrátí hodnotu. Rozdíl je znázorněn v následujícím příkladu.

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

Výraz `Await` nebo příkaz neblokuje vlákno, ve kterém se provádí. Místo toho způsobí, že kompilátor zaregistruje zbytek asynchronní metody za výraz `Await` jako pokračování na očekávaném úkolu. Ovládací prvek se pak vrátí volajícímu asynchronní metody. Po dokončení úkolu vyvolá jeho pokračování a spuštění asynchronní metody pokračuje tam, kde skončila.

Výraz `Await` může nastat pouze v těle bezprostředně ohraničující metody nebo lambda výrazu, který je označen modifikátorem `Async`. Termín *await* slouží jako klíčové slovo pouze v tomto kontextu. Jinde je interpretován jako identifikátor. V rámci asynchronní metody nebo výrazu lambda se nemůže výraz `Await` ve výrazu dotazu vyskytovat v bloku `catch` nebo `finally` [Try... Zachytit... Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) , ve výrazu řídicí proměnné smyčky `For` nebo `For Each` smyčky nebo v těle příkazu [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) .

## <a name="exceptions"></a>Výjimky

Většina asynchronních metod vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Vlastnosti vrácené úlohy obsahují informace o jeho stavu a historii, například o tom, zda je úloha dokončena, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek. Operátor `Await` přistupuje k těmto vlastnostem.

Pokud očekáváte asynchronní metodu vracející úlohu, která způsobí výjimku, operátor `Await` znovu vyvolá výjimku.

Očekáváte-li asynchronní metodu vracející úlohu, která je zrušena, operátor `Await` znovu vyvolá <xref:System.OperationCanceledException>.

Jeden úkol, který je v chybovém stavu, může odrážet více výjimek.  Například úloha může být výsledkem volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Pokud očekáváte takovou úlohu, operace Await znovu vyvolá pouze jednu výjimku. Nemůžete však odhadnout, které výjimky jsou znovu vyvolány.

Příklady zpracování chyb v asynchronních metodách naleznete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

## <a name="example"></a>Příklad

Následující příklad model Windows Forms ukazuje použití `Await` v asynchronní metodě, `WaitAsynchronouslyAsync`. Kontrast s chováním této metody s chováním `WaitSynchronously`. Bez operátoru `Await` `WaitSynchronously` spouští synchronně bez ohledu na použití modifikátoru `Async` v definici a volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> v jeho těle.

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
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
