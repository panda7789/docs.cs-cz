---
title: Zrušení zbývajících asynchronních úloh po dokončení jedné z nich
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: e6747f35e665611ac7a48a87f955c8b893ee2b99
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347927"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Zrušení zbývajících asynchronních úloh po dokončení jednoho z nich (Visual Basic)

Pomocí metody <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> spolu s <xref:System.Threading.CancellationToken>můžete zrušit všechny zbývající úlohy, když je jeden úkol dokončený. Metoda `WhenAny` přebírá argument, který je kolekcí úkolů. Metoda spustí všechny úlohy a vrátí jeden úkol. Jedna úloha je dokončena, když je dokončen libovolný úkol v kolekci.

Tento příklad ukazuje, jak použít token zrušení ve spojení s `WhenAny` pro uložení na první úkol pro dokončení z kolekce úloh a zrušení zbývajících úkolů. Každý úkol stáhne obsah webu. V příkladu se zobrazí délka obsahu prvního stažení, která se má dokončit, a ostatní soubory ke stažení se zruší.

> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

## <a name="downloading-the-example"></a>Stažení příkladu

Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

1. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningVB.

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAfterOneTask** a pak zvolte **nastavit jako projekt po spuštění**.

5. Kliknutím na klávesu F5 spusťte projekt.

    Vyberte klávesy CTRL + F5 pro spuštění projektu bez ladění.

6. Spusťte program několikrát, abyste ověřili, že se nejdřív dokončily jiné soubory ke stažení.

Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow. XAML. vb na konci tohoto tématu.

## <a name="building-the-example"></a>Vytvoření příkladu

Příklad v tomto tématu se přidá do projektu, který je vyvíjen v části [zrušení asynchronní úlohy nebo seznamu úloh](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) pro zrušení seznamu úkolů. V příkladu se používá stejné uživatelské rozhraní, i když se tlačítko **Storno** nepoužívá explicitně.

Chcete-li sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelAListOfTasks** . Přidejte změny v tomto tématu do projektu.

V souboru MainWindow. XAML. vb projektu **CancelAListOfTasks** spusťte přechod přesunutím kroků zpracování pro každý web ze smyčky v `AccessTheWebAsync` na následující asynchronní metodu.

```vb
' ***Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

V `AccessTheWebAsync`tento příklad používá dotaz, metodu <xref:System.Linq.Enumerable.ToArray%2A> a metodu `WhenAny` k vytvoření a spuštění pole úkolů. Aplikace `WhenAny` do pole vrací jeden úkol, který, pokud se očekává, se vyhodnotí jako první úkol, aby se dosáhlo dokončení v poli úkolů.

Proveďte následující změny v `AccessTheWebAsync`. Hvězdičky označují změny v souboru kódu.

1. Odkomentujte nebo odstraňte smyčku.

2. Vytvoří dotaz, který při spuštění vytvoří kolekci obecných úloh. Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo.

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. Voláním `ToArray` spusťte dotaz a spusťte úkoly. Při použití metody `WhenAny` v dalším kroku se spustí dotaz a spustí se úlohy bez použití `ToArray`, ale jiné metody nemusí. Nejbezpečnější praxí je vynutit provádění dotazu explicitně.

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Vyvolejte `WhenAny` v kolekci úkolů. `WhenAny` vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.  To znamená, `WhenAny` vrátí úlohu, která se vyhodnotí na jeden `Task(Of Integer)` nebo `Task<int>`, když je očekávána. Tento jeden úkol je prvním úkolem v kolekci, který má být dokončen. Úloha, která byla dokončena jako první, je přiřazena `firstFinishedTask`. Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože to je návratový typ `ProcessURLAsync`.

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. V tomto příkladu vás zajímá jenom úkol, který končí jako první. Proto pomocí <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušit zbývající úkoly.

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. Nakonec očekává `firstFinishedTask` načíst délku staženého obsahu.

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

Spusťte program několikrát, abyste ověřili, že se nejdřív dokončily jiné soubory ke stažení.

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný soubor MainWindow. XAML. vb nebo MainWindow.xaml.cs pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad.

Všimněte si, že je nutné přidat odkaz na <xref:System.Net.Http>.

Projekt si můžete stáhnout z části [Async Sample: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Download complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        '' Comment out or delete the loop.
        ''For Each url In urlList
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).
        ''    ' Argument ct carries the message if the Cancel button is chosen.
        ''    ' Note that the Cancel button can cancel all remaining downloads.
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ''    ' Retrieve the website contents from the HttpResponseMessage.
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ''    resultsTextBox.Text &=
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' ***Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' ***Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' ***Call WhenAny and then await the result. The task that finishes
        ' first is assigned to firstFinishedTask.
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' ***Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' ***Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await firstFinishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' ***Bundle the processing steps for a website into one async method.
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        Return urlContents.Length
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Vyladění aplikace v asynchronním prostředí (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
