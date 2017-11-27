---
title: "Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru Async a operátoru Await (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9b96e8acf9f5453ac035769ea7b279c4fedadfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru Async a operátoru Await (Visual Basic)
V asynchronní metody když vytváří se spustí úlohy. [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operátor se použije pro úlohu v okamžiku v metodě kde zpracování nemůže pokračovat, dokud na dokončení úlohy. Úloha je často očekáváno, jakmile je vytvořen, jako ukazuje následující příklad.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 Můžete však oddělit, vytvoření úlohy z čeká na úlohy, pokud má jinou práci provedete program, který nezávisí na dokončení úlohy.  
  
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
  
 Mezi počáteční úlohu a čeká na jeho, můžete spustit další úlohy. Další úlohy implicitně paralelní spuštění, ale jsou vytvořeny žádné další vlákna.  
  
 Následující program spustí tři asynchronní webové stahování a pak je čeká v pořadí, ve kterém jsou volány. Všimněte si, při spuštění programu, který úlohy není vždy dokončit v pořadí, ve kterém byly vytvořeny nebo očekáváno. Spuštění spustit, když vytvoříte a jeden nebo více úkolů může dokončit před metodu dosáhne await výrazy.  
  
> [!NOTE]
>  K dokončení tohoto projektu, musíte mít Visual Studio 2012 nebo vyšší a rozhraní .NET Framework 4.5 nebo vyšší v počítači nainstalována.  
  
 Další příklad, která se spouští ve stejnou dobu více úloh, najdete v části [postupy: rozšíření návodu asynchronních podle pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Si můžete stáhnout kód v tomto příkladu z [ukázky kódu vývojáře](http://go.microsoft.com/fwlink/?LinkId=254906).  
  
### <a name="to-set-up-the-project"></a>Vytvoření projektu  
  
1.  Pokud chcete nastavit aplikaci WPF, proveďte následující kroky. Najdete podrobné pokyny pro tyto kroky v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko. Název tlačítka `startButton`a název textového pole `resultsTextBox`.  
  
    -   Přidat odkaz pro <xref:System.Net.Http>.  
  
    -   V souboru MainWindow.xaml.vb, přidejte `Imports` příkaz pro `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Přidání kódu  
  
1.  V okně návrhu MainWindow.xaml, dvakrát klikněte na tlačítko vytvořit `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.vb.  
  
2.  Zkopírujte následující kód a vložte jej do textu `startButton_Click` v MainWindow.xaml.vb.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     Kód volá asynchronní metodu, `CreateMultipleTasksAsync`, jednotky, které se aplikace.  
  
3.  Do projektu přidejte následující metody podpory:  
  
    -   `ProcessURLAsync`používá <xref:System.Net.Http.HttpClient> metoda pro stažení obsahu webu, jako bajtové pole. V případě metody podporu `ProcessURLAsync` pak zobrazí a vrátí délku pole.  
  
    -   `DisplayResults`Zobrazí počet bajtů v bajtové pole pro každou adresu URL. Toto zobrazení zobrazí, když každý úkol dokončí stahování.  
  
     Zkopírujte následující metody a vložte je po `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.vb.  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4.  Nakonec zadejte metoda `CreateMultipleTasksAsync`, který provede následující kroky.  
  
    -   Deklaruje metodu `HttpClient` objekt, který potřebujete přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.  
  
    -   Metoda vytvoří a spustí tři úlohy typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo. Když každý úkol dokončí, `DisplayResults` zobrazí adresa URL úkolu a délka stažený obsah. Vzhledem k tomu, že úlohy běží asynchronně, pořadí, ve kterém se zobrazí výsledky se může lišit od pořadí, ve kterém bylo deklarováno.  
  
    -   Metoda čeká na dokončení každé úlohy. Každý `Await` operátor pozastaví spuštění `CreateMultipleTasksAsync` dokončení awaited úloh. Operátor také načte návratová hodnota z volání `ProcessURLAsync` z každé dokončené úlohy.  
  
    -   Když byly dokončeny úlohy a byly získány celočíselné hodnoty, metoda sečte délek weby a zobrazí výsledek.  
  
     Zkopírujte následující metodu a vložte jej do řešení.  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
  
5.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
     Spusťte program pro ověření, že tři úlohy není vždy dokončit ve stejném pořadí a pořadí, ve kterém dokončit není nutně pořadí, ve které jste vytvořili a očekávaná několikrát.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje kompletní příklad.  
  
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
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
