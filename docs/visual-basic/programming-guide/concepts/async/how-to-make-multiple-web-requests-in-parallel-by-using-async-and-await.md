---
title: 'Postupy: Paralelní provádění vícenásobných webových dotazů pomocí modifikátoru Async a operátoru Await'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 40bab392af94ba941c2562e885a8d2e08aeea5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396581"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Postupy: paralelní provádění více webových požadavků pomocí modifikátoru Async a operátoru Await (Visual Basic)

V asynchronní metodě jsou úlohy spouštěny při jejich vytvoření. Operátor [await](../../../language-reference/operators/await-operator.md) se aplikuje na úkol v místě v metodě, kde zpracování nemůže pokračovat, dokud se úloha nedokončí. Úkol se často očekává ihned po vytvoření, jak ukazuje následující příklad.

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

Můžete ale oddělit vytvoření úlohy z čekání na úkol, pokud má program další práci, která nezávisí na dokončení úkolu.

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

Mezi zahájením úlohy a čekáním na ni můžete spustit další úlohy. Další úkoly jsou implicitně spouštěny paralelně, ale nejsou vytvořeny žádné další podprocesy.

Následující program spustí tři asynchronní webové stahování a pak je očekává v pořadí, ve kterém jsou volány. Všimněte si, že při spuštění programu nejsou úlohy vždy dokončeny v pořadí, ve kterém byly vytvořeny a očekávány. Spouštějí se při jejich vytvoření a jedna nebo více úkolů může skončit předtím, než metoda dosáhne výrazů await.

> [!NOTE]
> Chcete-li dokončit tento projekt, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo vyšší a .NET Framework 4,5 nebo novější.

Další příklad, který spouští více úloh současně, naleznete v tématu [How to: Extending the Async návod pomocí Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

Kód pro tento příklad si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).

### <a name="to-set-up-the-project"></a>Vytvoření projektu

1. Chcete-li nastavit aplikaci WPF, proveďte následující kroky. Podrobné pokyny k těmto krokům najdete v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko. Pojmenujte tlačítko `startButton` a pojmenujte textové pole `resultsTextBox` .

    - Přidejte odkaz pro <xref:System.Net.Http> .

    - V souboru MainWindow. XAML. vb přidejte `Imports` příkaz pro `System.Net.Http` .

### <a name="to-add-the-code"></a>Přidání kódu

1. V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko a vytvořte `startButton_Click` obslužnou rutinu události v souboru MainWindow. XAML. vb.

2. Zkopírujte následující kód a vložte ho do těla `startButton_Click` v souboru MainWindow. XAML. vb.

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     Kód volá asynchronní metodu, `CreateMultipleTasksAsync` která aplikaci zařídí.

3. Do projektu přidejte následující metody podpory:

    - `ProcessURLAsync`používá <xref:System.Net.Http.HttpClient> metodu ke stažení obsahu webu jako bajtového pole. Metoda podpory `ProcessURLAsync` pak zobrazí a vrátí délku pole.

    - `DisplayResults`zobrazí počet bajtů v bajtovém poli pro každou adresu URL. Toto zobrazení ukazuje, kdy se každý úkol dokončí stahováním.

     Zkopírujte následující metody a vložte je po `startButton_Click` obslužné rutině události v souboru MainWindow. XAML. vb.

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

4. Nakonec definujte metodu `CreateMultipleTasksAsync` , která provede následující kroky.

    - Metoda deklaruje `HttpClient` objekt, který je zapotřebí pro přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync` .

    - Metoda vytvoří a spustí tři úkoly typu <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo. Po dokončení každé úlohy se `DisplayResults` zobrazí adresa URL úlohy a délka staženého obsahu. Vzhledem k tomu, že úlohy jsou spuštěny asynchronně, pořadí, ve kterém se výsledky zobrazují, se může lišit od pořadí, ve kterém byly deklarovány.

    - Metoda čeká na dokončení každého úkolu. Každý `Await` operátor pozastaví provádění, `CreateMultipleTasksAsync` dokud není dokončen očekávaný úkol. Operátor také Načte návratovou hodnotu z volání `ProcessURLAsync` z každé dokončené úlohy.

    - Po dokončení úloh a načtení celočíselných hodnot metoda sečte délky webů a zobrazí výsledek.

     Zkopírujte následující metodu a vložte ji do svého řešení.

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .

     Spusťte program několikrát, abyste ověřili, že tři úkoly nejsou vždy dokončeny ve stejném pořadí a že pořadí, ve kterém jsou dokončeny, nemusí být nutně pořadí, ve kterém byly vytvořeny a očekávány.

## <a name="example"></a>Příklad

Následující kód obsahuje úplný příklad.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
End Class
```

## <a name="see-also"></a>Viz také

- [Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](index.md)
- [Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
