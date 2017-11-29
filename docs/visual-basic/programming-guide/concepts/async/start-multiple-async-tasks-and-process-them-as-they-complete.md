---
title: "Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dfabe4619e5d73b554d91edb137ae1ce7d34b5ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)
Pomocí <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, můžete současně spustit více úloh a zpracování jednotlivých jejich jste dokončit, nikoli jejich zpracování v pořadí, ve kterém se spouští.  
  
 Následující příklad používá dotaz k vytvoření kolekce úloh. Každý úkol stáhne obsah zadaného webu. V každé iteraci chvíli cykly, awaited volání `WhenAny` vrátí úlohu v kolekci úloh, které nejprve dokončí jeho stažení. Tuto úlohu je z kolekce odebrán a zpracovat. Smyčky se opakuje, dokud kolekce obsahuje žádné další úlohy.  
  
> [!NOTE]
>  Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](http://go.microsoft.com/fwlink/?LinkId=255046) a pak postupujte podle těchto kroků.  
  
1.  Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
3.  V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningVB.  
  
4.  V **Průzkumníku řešení**, otevřete místní nabídku pro **ProcessTasksAsTheyFinish** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
5.  Zvolte klávesu F5 a spusťte projekt.  
  
     Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.  
  
6.  Spusťte projekt několikrát k ověření, že staženou délky nezobrazí vždy ve stejném pořadí.  
  
 Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.vb na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytváření v příkladu  
 Tento příklad přidá do kód, který je vyvinuta v [zrušení zbývajících asynchronních úloh po jedné je úplná (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) a používá stejné uživatelské rozhraní.  
  
 K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAfterOneTask** jako **spouštěný projekt**. Přidat změny v tomto tématu `AccessTheWebAsync` metoda v tomto projektu. Změny jsou označené hvězdičky.  
  
 **CancelAfterOneTask** projekt už zahrnuje dotaz, který při spuštění vytvoří kolekci úloh. Každé volání `ProcessURLAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 V souboru MainWindow.xaml.vb projektu, proveďte následující změny `AccessTheWebAsync` metoda.  
  
-   Spusťte dotaz tak, že použití <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> místo <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
-   Přidat chvíli smyčky, která provede následující kroky pro každý úkol v kolekci.  
  
    1.  Čeká volání `WhenAny` k identifikaci první úloha v kolekci ukončíte jeho stažení.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2.  Tento úkol odstraní z kolekce.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3.  Čeká `firstFinishedTask`, který se vrátí po volání `ProcessURLAsync`. `firstFinishedTask` Proměnná <xref:System.Threading.Tasks.Task%601> kde `TReturn` je celé číslo. Úloha je již dokončena, ale můžete ji načíst délka stažené web, jak ukazuje následující příklad await.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Byste měli spustit projekt několikrát k ověření, že staženou délky nezobrazí vždy ve stejném pořadí.  
  
> [!CAUTION]
>  Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu k řešení problémů, které zahrnují malý počet úloh. Jiné postupy jsou však efektivnější, pokud máte velký počet úloh ke zpracování. Další informace a příklady naleznete v tématu [zpracování úloh jako jejich dokončení](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je úplný text souboru MainWindow.xaml.vb pro tento příklad. Hvězdičky označit prvky, které byly přidány v tomto příkladu.  
  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Vyladění s modifikátorem Async aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Ukázka asynchronního: Jemnou ladění aplikace](http://go.microsoft.com/fwlink/?LinkId=255046)
