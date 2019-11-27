---
title: Zrušení asynchronní úlohy nebo seznamu úloh
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 2956582cd0c8e044fcd37ffab13686489a7c854c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347970"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>Zrušení asynchronní úlohy nebo seznamu úloh (Visual Basic)

Můžete nastavit tlačítko, které můžete použít k zrušení asynchronní aplikace, pokud nechcete čekat na jeho dokončení. Podle příkladů v tomto tématu můžete přidat tlačítko zrušení do aplikace, která stáhne obsah jednoho webu nebo seznamu webů.

V příkladech se používá uživatelské rozhraní, které vám popíše, jak [vyladit asynchronní aplikaci (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) .

> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

## <a name="BKMK_CancelaTask"></a>Zrušení úlohy

První příklad přidruží tlačítko **Zrušit** k jedné úloze stažení. Pokud zvolíte tlačítko, zatímco aplikace stahuje obsah, stahování se zruší.

### <a name="downloading-the-example"></a>Stažení příkladu

Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

1. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningVB.

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelATask** a pak zvolte **nastavit jako projekt po spuštění**.

5. Kliknutím na klávesu F5 spusťte projekt.

     Vyberte klávesy CTRL + F5 pro spuštění projektu bez ladění.

 Pokud nechcete stáhnout projekt, můžete zkontrolovat soubory MainWindow. XAML. vb na konci tohoto tématu.

### <a name="building-the-example"></a>Vytvoření příkladu

Následující změny přidají tlačítko **Storno** do aplikace, která stáhne Web. Pokud nechcete stáhnout nebo sestavit příklad, můžete si prohlédnout konečný produkt v části "kompletní příklady" na konci tohoto tématu. Hvězdičky označují změny v kódu.

Pokud chcete sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt** vyberte **StarterCode** namísto **CancelATask**.

Pak přidejte následující změny do souboru MainWindow. XAML. vb daného projektu.

1. Deklarujte `CancellationTokenSource` proměnnou `cts`, která je v oboru pro všechny metody, které k ní přistupují.

    ```vb
    Class MainWindow

        ' ***Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. Přidejte následující obslužnou rutinu události pro tlačítko **Storno** . Obslužná rutina události používá metodu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> k upozorňování `cts`, když si uživatel vyžádá zrušení.

    ```vb
    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub
    ```

3. Proveďte následující změny v obslužné rutině události pro tlačítko **Start** `startButton_Click`.

    - Vytvořte instanci `CancellationTokenSource``cts`.

      ```vb
      ' ***Instantiate the CancellationTokenSource.
      cts = New CancellationTokenSource()
      ```

    - V volání `AccessTheWebAsync`, které stahuje obsah zadaného webu, odešlete vlastnost <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> `cts` jako argument. Vlastnost `Token` šíří zprávu, pokud je požadováno zrušení. Přidejte blok catch, který zobrazí zprávu, pokud se uživatel rozhodne zrušit operaci stahování. Následující kód ukazuje změny.

      ```vb
      Try
          ' ***Send a token to carry the message if cancellation is requested.
          Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

          resultsTextBox.Text &=
              vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

          ' *** If cancellation is requested, an OperationCanceledException results.
      Catch ex As OperationCanceledException
          resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

      Catch ex As Exception
          resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
      End Try
      ```

4. V `AccessTheWebAsync`použijte <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> přetížení metody `GetAsync` v <xref:System.Net.Http.HttpClient> typu ke stažení obsahu webu. Předat `ct`<xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako druhý argument. Pokud uživatel klikne na tlačítko **Storno** , tento token zprávu přenese.

    Následující kód ukazuje změny v `AccessTheWebAsync`.

    ```vb
    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &= vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
    ```

5. Pokud program nezrušíte, vytvoří se následující výstup:

    ```console
    Ready to download.
    Length of the downloaded string: 158125.
    ```

    Pokud zvolíte tlačítko **Storno** před tím, než program dokončí stahování obsahu, program vytvoří následující výstup:

    ```console
    Ready to download.
    Download canceled.
    ```

## <a name="BKMK_CancelaListofTasks"></a>Zrušení seznamu úloh

Předchozí příklad můžete roztáhnout tak, aby bylo možné zrušit mnoho úloh přiřazením stejné instance `CancellationTokenSource` k jednotlivým úlohám. Pokud zvolíte tlačítko **Zrušit** , zrušíte tím všechny úlohy, které ještě nebyly dokončeny.

### <a name="downloading-the-example"></a>Stažení příkladu

Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

1. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningVB.

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAListOfTasks** a pak zvolte **nastavit jako projekt po spuštění**.

5. Kliknutím na klávesu F5 spusťte projekt.

     Vyberte klávesy CTRL + F5 pro spuštění projektu bez ladění.

 Pokud nechcete stáhnout projekt, můžete zkontrolovat soubory MainWindow. XAML. vb na konci tohoto tématu.

### <a name="building-the-example"></a>Vytvoření příkladu

Chcete-li tento příklad roztáhnout sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelATask** . Do tohoto projektu přidejte následující změny. Hvězdičky označují změny v programu.

1. Přidejte metodu pro vytvoření seznamu webových adres.

    ```vb
    ' ***Add a method that creates a list of web addresses.
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
    ```

2. Volejte metodu v `AccessTheWebAsync`.

    ```vb
    ' ***Call SetUpURLList to make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()
    ```

3. Přidejte následující smyčku v `AccessTheWebAsync` pro zpracování každé webové adresy v seznamu.

    ```vb
    ' ***Add a loop to process the list of web addresses.
    For Each url In urlList
        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' Argument ct carries the message if the Cancel button is chosen.
        ' ***Note that the Cancel button can cancel all remaining downloads.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        resultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
    Next
    ```

4. Vzhledem k tomu, že `AccessTheWebAsync` zobrazuje délku, metoda nemusí vracet cokoli. Odeberte příkaz return a změňte návratový typ metody na <xref:System.Threading.Tasks.Task> místo <xref:System.Threading.Tasks.Task%601>.

    ```vb
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task
    ```

    Volejte metodu z `startButton_Click` pomocí příkazu namísto výrazu.

    ```vb
    Await AccessTheWebAsync(cts.Token)
    ```

5. Pokud program nezrušíte, vytvoří se následující výstup:

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

    Pokud zvolíte tlačítko **Zrušit** před dokončením stahování, bude výstup obsahovat délky stahování, která byla dokončena před zrušením.

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="BKMK_CompleteExamples"></a>Kompletní příklady

Následující části obsahují kód pro každý z předchozích příkladů. Všimněte si, že je nutné přidat odkaz na <xref:System.Net.Http>.

Projekty si můžete stáhnout z [Async Sample: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="cancel-a-task-example"></a>Příklad zrušení úlohy

Následující kód je úplný soubor MainWindow. XAML. vb pro příklad, který zruší jeden úkol.

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' ***Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)
        ' ***Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Send a token to carry the message if cancellation is requested.
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

            ' *** If cancellation is requested, an OperationCanceledException results.
        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' ***Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &=
            vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
End Class

' Output for a successful download:

' Ready to download.

' Length of the downloaded string: 158125.

' Or, if you cancel:

' Ready to download.

' Download canceled.
```

### <a name="cancel-a-list-of-tasks-example"></a>Příklad zrušení seznamu úloh

Následující kód je úplný soubor MainWindow. XAML. vb pro příklad, který zruší seznam úkolů.

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
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).
            Await AccessTheWebAsync(cts.Token)
            '  ***Small change in the display lines.
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' ***Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' ***Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' ***Add a loop to process the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' ***Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' ***Add a method that creates a list of web addresses.
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

' Output if you do not choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Length of the downloaded string: 158124.

' Length of the downloaded string: 204890.

' Length of the downloaded string: 175488.

' Length of the downloaded string: 145790.

' Downloads complete.

'  Sample output if you choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Downloads canceled.
```

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Vyladění aplikace v asynchronním prostředí (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
