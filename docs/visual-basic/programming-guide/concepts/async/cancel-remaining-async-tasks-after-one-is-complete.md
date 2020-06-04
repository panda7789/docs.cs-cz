---
title: Zrušení zbývajících úloh s modifikátorem Async po dokončení jedné z nich
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: be716e98263c865adad3c197236467b2f48d7740
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396672"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Zrušení zbývajících asynchronních úloh po dokončení jednoho z nich (Visual Basic)

Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody společně s a <xref:System.Threading.CancellationToken> můžete zrušit všechny zbývající úlohy, když je jeden úkol dokončen. `WhenAny`Metoda přebírá argument, který je kolekcí úkolů. Metoda spustí všechny úlohy a vrátí jeden úkol. Jedna úloha je dokončena, když je dokončen libovolný úkol v kolekci.

Tento příklad ukazuje, jak použít token zrušení ve spojení s `WhenAny` pro uložení na první úkol pro dokončení z kolekce úkolů a zrušení zbývajících úkolů. Každý úkol stáhne obsah webu. V příkladu se zobrazí délka obsahu prvního stažení, která se má dokončit, a ostatní soubory ke stažení se zruší.

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

Příklad v tomto tématu se přidá do projektu, který je vyvíjen v části [zrušení asynchronní úlohy nebo seznamu úloh](cancel-an-async-task-or-a-list-of-tasks.md) pro zrušení seznamu úkolů. V příkladu se používá stejné uživatelské rozhraní, i když se tlačítko **Storno** nepoužívá explicitně.

Chcete-li sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelAListOfTasks** . Přidejte změny v tomto tématu do projektu.

V souboru MainWindow. XAML. vb projektu **CancelAListOfTasks** spusťte přechod přesunutím kroků zpracování pro každý web z smyčky do `AccessTheWebAsync` následující asynchronní metody.

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

V `AccessTheWebAsync` je v tomto příkladu použit dotaz, <xref:System.Linq.Enumerable.ToArray%2A> Metoda a `WhenAny` metoda pro vytvoření a spuštění pole úkolů. Aplikace `WhenAny` do pole vrátí jeden úkol, který je při očekávání vyhodnocen jako první úkol, aby se dosáhlo dokončení v poli úkolů.

Proveďte následující změny v `AccessTheWebAsync` . Hvězdičky označují změny v souboru kódu.

1. Odkomentujte nebo odstraňte smyčku.

2. Vytvoří dotaz, který při spuštění vytvoří kolekci obecných úloh. Každé volání `ProcessURLAsync` vrátí, <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. Zavolejte `ToArray` na příkaz Spustit dotaz a spusťte úkoly. Aplikace `WhenAny` metody v dalším kroku spustí dotaz a spustí úlohy bez použití `ToArray` , ale jiné metody nemusí. Nejbezpečnější praxí je vynutit provádění dotazu explicitně.

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Zavolejte `WhenAny` na kolekci úkolů. `WhenAny`Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>` .  To znamená, že `WhenAny` vrátí úlohu, která se vyhodnotí na jeden nebo v případě, že je `Task(Of Integer)` `Task<int>` očekávána. Tento jeden úkol je prvním úkolem v kolekci, který má být dokončen. Úkol, který byl dokončen jako první, je přiřazen `firstFinishedTask` . Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> `TResult` , kde je celé číslo, protože to je návratový typ `ProcessURLAsync` .

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. V tomto příkladu vás zajímá jenom úkol, který končí jako první. Proto použijte <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> ke zrušení zbývajících úkolů.

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. Nakonec čeká `firstFinishedTask` na načtení délky staženého obsahu.

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

Spusťte program několikrát, abyste ověřili, že se nejdřív dokončily jiné soubory ke stažení.

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný soubor MainWindow. XAML. vb nebo MainWindow.xaml.cs pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad.

Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http> .

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

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Vyladění aplikace v asynchronním prostředí (Visual Basic)](fine-tuning-your-async-application.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](index.md)
- [Asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
