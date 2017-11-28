---
title: "Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 49cca45336cb25850c888e3389e97b323c70d89d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)
Může zvýšit výkon řešení asynchronních v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metoda. Tato metoda asynchronně čeká více asynchronních operací, které jsou reprezentovány jako kolekce úloh.  
  
 Možná jste si všimli v návodu, weby, ke stažení různým tempem. Někdy jeden z webů je velmi pomalé, což zpozdí všechna zbývající stahování. Když spustíte asynchronní řešení, které vytvoříte v návodu, můžete program snadno ukončit, pokud nechcete čekat, ale chcete spustit všechny soubory ke stažení ve stejnou dobu a umožní rychlejší stahování pokračovat bez čekání na ten, který by bylo lepší volbou pro  zpožděno.  
  
 Můžete použít `Task.WhenAll` metodu pro kolekci úloh. Použití `WhenAll` vrátí jednu úlohu, která není kompletní, dokud se nedokončí každý úkol v kolekci. Úkoly zdánlivě spouštějí paralelně, ale jsou vytvořeny žádné další vlákna. Úlohy můžete dokončit v libovolném pořadí.  
  
> [!IMPORTANT]
>  Následující postupy popisují rozšíření pro asynchronní aplikace vyvinuté v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Dokončení průvodce nebo stahování kód můžete vyvíjet aplikace [ukázky kódu vývojáře](http://go.microsoft.com/fwlink/?LinkId=255191).  
>   
>  Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo později v počítači nainstalována.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Přidání metody Task.WhenAll do řešení GetURLContentsAsync  
  
1.  Přidat `ProcessURLAsync` metoda k první aplikaci, která je vyvinuta v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Pokud jste stáhli kód z [ukázky kódu vývojáře](http://go.microsoft.com/fwlink/?LinkId=255191), otevřete projekt AsyncWalkthrough a poté přidejte `ProcessURLAsync` MainWindow.xaml.vb souboru.  
  
    -   Pokud kód vyvinutými dokončení průvodce, přidejte `ProcessURLAsync` k aplikaci, která zahrnuje `GetURLContentsAsync` metoda. Soubor MainWindow.xaml.vb pro tuto aplikaci je v prvním příkladu v části "Kompletní kód příklady z a podrobný postup".  
  
     `ProcessURLAsync` Slučuje metoda akce v textu `For Each` smyčky v `SumPageSizesAsync` v původní návodu. Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku pole bajtů.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Komentář nebo odstranění `For Each` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  Vytvořte kolekci úloh. Následující kód definuje [dotazu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , když provedený <xref:System.Linq.Enumerable.ToArray%2A> metoda, vytvoří kolekci úloh, které stažení obsahu jednotlivých webů. Úkoly jsou spuštěny při vyhodnocování dotazu.  
  
     Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `urlList`.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Použít `Task.WhenAll` ke kolekci úloh `downloadTasks`. `Task.WhenAll`Vrátí jednu úlohu, která se dokončí po dokončení všech úloh v kolekci úloh.  
  
     V následujícím příkladu `Await` výraz čeká na dokončení jedné úloha, která `WhenAll` vrátí. Výraz vyhodnocen jako pole celých čísel, kde každý celé číslo je délka stažené webu. Přidejte následující kód, který `SumPageSizesAsync`, jednoduše po kód, který jste přidali v předchozím kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součet délek všechny weby. Přidejte následující řádek na `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync  
  
1.  Přidejte následující verze `ProcessURLAsync` na druhou aplikaci, která je vytvořena v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Pokud jste stáhli kód z [ukázky kódu vývojáře](http://go.microsoft.com/fwlink/?LinkId=255191), otevřete projekt AsyncWalkthrough_HttpClient a poté přidejte `ProcessURLAsync` MainWindow.xaml.vb souboru.  
  
    -   Pokud kód vyvinutými dokončení průvodce, přidejte `ProcessURLAsync` k aplikaci, která používá `HttpClient.GetByteArrayAsync` metoda. Soubor MainWindow.xaml.vb pro tuto aplikaci je v druhém příkladu v části "Kompletní kód příklady z a podrobný postup".  
  
     `ProcessURLAsync` Slučuje metoda akce v textu `For Each` smyčky v `SumPageSizesAsync` v původní návodu. Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku pole bajtů.  
  
     Jediným rozdílem z `ProcessURLAsync` metoda v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client`.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Komentář nebo odstranění `For Each` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
    ```  
  
3.  Definovat [dotazu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , když provedený <xref:System.Linq.Enumerable.ToArray%2A> metoda, vytvoří kolekci úloh, které stažení obsahu jednotlivých webů. Úkoly jsou spuštěny při vyhodnocování dotazu.  
  
     Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `client` a `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  V dalším kroku použít `Task.WhenAll` ke kolekci úloh `downloadTasks`. `Task.WhenAll`Vrátí jednu úlohu, která se dokončí po dokončení všech úloh v kolekci úloh.  
  
     V následujícím příkladu `Await` výraz čeká na dokončení jedné úloha, která `WhenAll` vrátí. Po dokončení `Await` výraz vyhodnocen jako pole celých čísel, kde každý celé číslo je délka stažené webu. Přidejte následující kód, který `SumPageSizesAsync`, jednoduše po kód, který jste přidali v předchozím kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metoda získat součet délek všechny weby. Přidejte následující řádek na `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Otestování řešení Task.WhenAll  
  
-   Buď řešení, zvolte klávesu F5 a spusťte program a pak **spustit** tlačítko. Výstup by měl vypadat výstup z těchto řešení asynchronních v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Všimněte si však, že weby se objeví v jiném pořadí pokaždé, když.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje rozšíření pro projekt, který používá `GetURLContentsAsync` metodu za účelem stahování obsahu z webu.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                ' CopyToAsync returns a Task, not a Task<T>.  
                Await responseStream.CopyToAsync(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` ke stahování obsahu z webu.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
