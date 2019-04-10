---
title: Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: a9a41c354993e0d362c344d523d6c4c4b6f61f10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309651"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)
S použitím <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, můžete spustit více úkolů současně a zpracovat je postupně tak, jak jsou dokončeny namísto zpracování v pořadí, ve kterém se spouští.  
  
 Následující příklad používá dotaz k vytvoření kolekce úkolů. Každý úkol umožňuje stažení obsahu zadaného webu. V každé iteraci nějakou smyčky, očekávané volání metody `WhenAny` vrátí úkol v kolekci úkolů, která dokončí stahování jako první. Tento úkol je odebrán z kolekce a zpracování. Smyčka se opakuje dokud kolekce neobsahuje žádné další úlohy.  
  
> [!NOTE]
>  Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1. Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.  
  
2. V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.  
  
3. V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningVB.  
  
4. V **Průzkumníka řešení**, otevřete místní nabídku **ProcessTasksAsTheyFinish** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
5. Stiskněte klávesu F5 ke spuštění projektu.  
  
     Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.  
  
6. Projekt několikrát spusťte a tak ověřte, že stažené délky se vždy nezobrazí ve stejném pořadí.  
  
 Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.vb na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Sestavení příkladu  
 V tomto příkladu přidá do kódu, který je napsán v jazyce [zrušení zbývajících asynchronních úloh po jeden je úplná (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) a používá stejné uživatelské rozhraní.  
  
 Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelAfterOneTask** jako **spouštěný projekt**. Přidejte změny v tomto tématu a `AccessTheWebAsync` metody v daném projektu. Změny jsou označeny hvězdičkami.  
  
 **CancelAfterOneTask** projekt již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů. Každé volání `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 V souboru MainWindow.xaml.vb nebo projektu, proveďte následující změny `AccessTheWebAsync` metody.  
  
-   Spusťte dotaz s použitím <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
-   Přidat nějakou smyčku, která provede následující kroky pro každý úkol v kolekci.  
  
    1.  Čeká volání `WhenAny` identifikovat první úkol v kolekci, která se dokončí stažení.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2.  Odebere tento úkol z kolekce.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3.  Čeká `firstFinishedTask`, který je vrácen voláním `ProcessURLAsync`. `firstFinishedTask` Proměnná je <xref:System.Threading.Tasks.Task%601> kde `TReturn` je celé číslo. Úloha je již dokončena, ale můžete od něj načte délku staženého webu, jak ukazuje následující příklad očekávat.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Projekt by měl spustit několikrát k ověření, že stažené délky se vždy nezobrazí ve stejném pořadí.  
  
> [!CAUTION]
>  Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, k řešení problémů, které se týkají malého počtu úkolů. Další postupy jsou však efektivnější, pokud máte velký počet úkolů ke zpracování. Další informace a příklady najdete v tématu [zpracování úkolů při jejich dokončování](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete).  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je celý text souboru MainWindow.xaml.vb pro příklad. Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu.  
  
 Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.  
  
 Stáhnete projekt z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.   
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Doladění aplikace s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Ukázka asynchronní metody: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
