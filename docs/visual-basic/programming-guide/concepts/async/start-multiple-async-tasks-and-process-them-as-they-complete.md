---
title: Spuštění několika asynchronních úloh a jejich zpracování po dokončení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: 24dbf4904c4e4b479df54d1c663bb4d1256e2ede
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046448"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Spuštění několika asynchronních úloh a jejich zpracování po dokončení (Visual Basic)
Pomocí nástroje <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>můžete spustit více úloh současně a zpracovat je jeden po jednom, protože jsou dokončeny, a nikoli jejich zpracování v pořadí, ve kterém jsou spuštěny.  
  
 Následující příklad používá dotaz k vytvoření kolekce úkolů. Každý úkol stáhne obsah zadaného webu. V každé iteraci smyčky while očekává volání metody `WhenAny` vrácení úlohy v kolekci úkolů, které dokončí stahování jako první. Tato úloha je odebrána z kolekce a zpracována. Smyčka se opakuje, dokud kolekce neobsahuje žádné další úlohy.  
  
> [!NOTE]
> Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Kompletní projekt Windows Presentation Foundation (WPF) si můžete stáhnout z [části Async Sample: Vyladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.  
  
2. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.  
  
3. V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningVB.  
  
4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ProcessTasksAsTheyFinish** a pak zvolte **nastavit jako projekt po spuštění**.  
  
5. Kliknutím na klávesu F5 spusťte projekt.  
  
     Vyberte klávesy CTRL + F5 pro spuštění projektu bez ladění.  
  
6. Spusťte projekt několikrát, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.  
  
 Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow. XAML. vb na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytvoření příkladu  
 Tento příklad přidá do kódu, který je vyvinut v části [zrušení zbývajících asynchronních úloh po dokončení jedné (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) a používá stejné uživatelské rozhraní.  
  
 Chcete-li sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelAfterOneTask** . Přidejte změny v tomto tématu do `AccessTheWebAsync` metody v tomto projektu. Změny jsou označeny hvězdičkami.  
  
 Projekt **CancelAfterOneTask** již obsahuje dotaz, který při spuštění vytvoří kolekci úkolů. Každé volání do `ProcessURLAsync` v následujícím kódu <xref:System.Threading.Tasks.Task%601> vrátí, kde `TResult` je celé číslo.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 V souboru MainWindow. XAML. vb projektu proveďte následující změny `AccessTheWebAsync` metody.  
  
- Spusťte dotaz <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> použitím <xref:System.Linq.Enumerable.ToArray%2A>místo.  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- Přidejte smyčku while, která provede následující kroky pro každý úkol v kolekci.  
  
    1. Očekává volání `WhenAny` k identifikaci prvního úkolu v kolekci, aby bylo možné dokončit stahování.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. Odebere úlohu z kolekce.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. Čeká, který je vrácen `ProcessURLAsync`voláním metody. `firstFinishedTask` Proměnná je, kde`TReturn` je celé číslo. <xref:System.Threading.Tasks.Task%601> `firstFinishedTask` Úkol je již dokončen, ale očekáváte, že bude načtena délka staženého webu, jak ukazuje následující příklad.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Projekt byste měli několikrát spustit, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.  
  
> [!CAUTION]
> Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, pro řešení problémů, které zahrnují malý počet úkolů. Další přístupy jsou ale efektivnější, pokud máte velký počet úkolů, které je potřeba zpracovat. Další informace a příklady najdete v tématu [zpracování úloh po dokončení](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete).  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je úplný text souboru MainWindow. XAML. vb pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad.  
  
 Všimněte si, že je nutné přidat odkaz <xref:System.Net.Http>pro.  
  
 Projekt si můžete stáhnout z [části asynchronní Ukázka: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)  
  
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
- [Vyladění aplikace v asynchronním prostředí (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchronní Ukázka: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
