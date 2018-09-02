---
title: Zrušení zbývajících asynchronních úloh po jedné z nich kompletní (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 5dab0c4aa14710fe78d2473675aea8b8c8bb73b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402254"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Zrušení zbývajících asynchronních úloh po jedné z nich kompletní (Visual Basic)
S použitím <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda spolu s <xref:System.Threading.CancellationToken>, můžete po dokončení jednoho úkolu zrušit všechny zbývající úkoly. `WhenAny` Metoda přebírá argument, který je kolekce úkolů. Metoda spustí všechny úlohy a vrátí jeden úkol. Jedna úloha je dokončena po dokončení libovolné úlohy v kolekci.  
  
 Tento příklad ukazuje, jak použít token zrušení společně s `WhenAny` pro udržení prvního úkol k dokončení z kolekce úkolů a zrušení zbývajících úkolů. Každý úkol umožňuje stažení obsahu webu. Příklad zobrazuje délku obsahu prvního stahování pro dokončení a zruší ostatní stahování.  
  
> [!NOTE]
>  Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1.  Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.  
  
2.  V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.  
  
3.  V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningVB.  
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku **CancelAfterOneTask** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
5.  Stiskněte klávesu F5 ke spuštění projektu.  
  
     Stiskněte klávesy Ctrl + F5 ke spuštění projektu bez ladění.  
  
6.  Program několikrát spusťte a tak ověřte, že nejprve dokončit různé soubory ke stažení.  
  
 Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.vb na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Sestavení příkladu  
 V příkladu v tomto tématu se přidá do projektu, který je napsán v jazyce [zrušení asynchronní úlohy nebo seznamu úloh](https://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) zrušení seznamu úloh. V příkladu se používá stejné uživatelské rozhraní, i když **zrušit** tlačítko není použito explicitně.  
  
 Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**. Přidejte změny v tomto tématu do daného projektu.  
  
 V souboru MainWindow.xaml.vb **CancelAListOfTasks** projektu, zahajte přechod přesunutím kroků zpracování pro každý web ze smyčky v `AccessTheWebAsync` do následující asynchronní metody.  
  
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
  
 V `AccessTheWebAsync`, v tomto příkladu dotaz, <xref:System.Linq.Enumerable.ToArray%2A> metody a `WhenAny` metodu pro vytvoření a spuštění úloh v poli. Použití `WhenAny` na pole vrátí jeden úkol, který, když je očekáváno, je vyhodnocen jako první úkol k dosažení dokončení v poli úloh.  
  
 Proveďte následující změny v `AccessTheWebAsync`. Hvězdičky označují změny v souboru kódu.  
  
1.  Okomentujte nebo odstraňte smyčku.  
  
2.  Vytvoření dotazu, který při spuštění vytvoří kolekci obecných úkolů. Každé volání `ProcessURLAsync` vrátí <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo.  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  Volání `ToArray` spustit dotaz a spustilo úlohu. Použití `WhenAny` metoda v dalším kroku by spustilo dotaz a spustilo úlohu bez použití `ToArray`, ale jiné metody nemusí. Nejbezpečnější metodou je vynutit spuštění dotazu explicitně.  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Volání `WhenAny` na kolekci úloh. `WhenAny` Vrátí `Task(Of Task(Of Integer))` nebo `Task<Task<int>>`.  To znamená `WhenAny` vrátí úkol, který se vyhodnocuje do jediné `Task(Of Integer)` nebo `Task<int>` pokus je očekáváno. Jeden úkol je první úkol v kolekci pro dokončení. Někdo přiřadí úkol, který skončil první `firstFinishedTask`. Typ `firstFinishedTask` je <xref:System.Threading.Tasks.Task%601> kde `TResult` je celé číslo, protože to je návratový typ `ProcessURLAsync`.  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  V tomto příkladu se zajímáte pouze úloha, která skončí jako první. Proto použít <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> zrušení zbývajících úkolů.  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  Nakonec vyčkejte, než `firstFinishedTask` načte délku stahovaného obsahu.  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 Program několikrát spusťte a tak ověřte, že nejprve dokončit různé soubory ke stažení.  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je celý soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs pro příklad. Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu.  
  
 Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.  
  
 Stáhnete projekt z [asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
 [Doladění aplikace s modifikátorem Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
