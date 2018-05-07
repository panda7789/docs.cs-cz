---
title: Zrušení zbývajících asynchronních úloh po jedné z nich dokončení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 86fb56d9a6d6a6c491b35797c7459c701a339341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Zrušení zbývajících asynchronních úloh po jedné z nich dokončení (Visual Basic)
Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda společně s <xref:System.Threading.CancellationToken>, můžete zrušit všechny zbývající úkoly po dokončení úloh. `WhenAny` Metoda přebírá argument, který je kolekce úloh. Metoda spustí všechny úlohy a vrátí jednu úlohu. Jediná úloha je dokončena po dokončení všech úloh v kolekci.  
  
 Tento příklad ukazuje, jak používat token zrušení ve spojení s `WhenAny` k uložení do první úlohy a dokončit z kolekce úloh a zrušit ve zbývajících úkolech. Každý úkol stáhne obsah webu. V příkladu se zobrazí délka obsahu první stahování dokončit a zruší další soubory ke stažení.  
  
> [!NOTE]
>  Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](http://go.microsoft.com/fwlink/?LinkId=255046) a pak postupujte podle těchto kroků.  
  
1.  Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
3.  V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningVB.  
  
4.  V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelAfterOneTask** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
5.  Zvolte klávesu F5 a spusťte projekt.  
  
     Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.  
  
6.  Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.  
  
 Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.vb na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytváření v příkladu  
 V příkladu v tomto tématu přidá do projektu, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) zrušit seznamu úloh. Tento příklad používá stejné uživatelské rozhraní, i když **zrušit** tlačítko nepoužívá explicitně.  
  
 K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**. Do tohoto projektu přidáte změny v tomto tématu.  
  
 V souboru MainWindow.xaml.vb **CancelAListOfTasks** projektu, spusťte přechodu přesunutím zpracování kroky pro každý web smyčky v `AccessTheWebAsync` následující asynchronní metody.  
  
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
  
 V `AccessTheWebAsync`, v tomto příkladu dotaz, <xref:System.Linq.Enumerable.ToArray%2A> metody a `WhenAny` metoda pro vytvoření a spuštění úloh v poli. Použití `WhenAny` do pole vrátí jeden úkol, pokud je očekáváno, vyhodnotí jako první úlohou k dosažení dokončování úloh v poli.  
  
 Proveďte následující změny v `AccessTheWebAsync`. Hvězdičky označit změny v souboru kódu.  
  
1.  Komentář nebo odstranit smyčky.  
  
2.  Vytvořit dotaz, která po provedení vytvoří kolekci obecné úlohy. Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  Volání `ToArray` proveďte dotaz a spusťte úlohy. Použití `WhenAny` metoda v dalším kroku by provést dotaz a spustit úlohy bez použití `ToArray`, ale jiné metody možná není. Nejbezpečnější metodou je explicitně vynutit spuštění dotazu.  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Volání `WhenAny` na kolekci úloh. `WhenAny` Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.  To znamená `WhenAny` vrátí úlohu, která vyhodnotí na jednu `Task(Of Integer)` nebo `Task<int>` Pokud je očekáváno. Tento jeden úkol je první úloha v kolekci ukončíte. Úloha, která nejprve dokončení je přiřazen k `firstFinishedTask`. Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože se jedná návratový typ `ProcessURLAsync`.  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  V tomto příkladu co vás zajímá pouze úloha, která nejprve dokončí. Proto použijte <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušit ve zbývajících úkolech.  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  Nakonec await `firstFinishedTask` načíst délka staženého obsahu.  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 Spusťte program několikrát k ověřte, že nejprve dokončit různé soubory ke stažení.  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je k dokončení souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs pro tento příklad. Hvězdičky označit prvky, které byly přidány v tomto příkladu.  
  
 Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http>.  
  
 Si můžete stáhnout z projektu [asynchronní ukázka: jemné ladění vaše aplikace](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
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
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
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
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Vyladění s modifikátorem Async aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Ukázka asynchronního: Jemnou ladění aplikace](http://go.microsoft.com/fwlink/?LinkId=255046)
