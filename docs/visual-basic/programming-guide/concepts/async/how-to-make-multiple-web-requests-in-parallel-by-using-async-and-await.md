---
title: 'Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: c799fa83c0157019961da6adcf89b6ab6f906763
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021996"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)
V asynchronní metodě jsou úlohy spuštěny při jejich vytvoření. [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operátor je použít pro úlohu v okamžiku v metodě, kdy zpracování nemůže pokračovat, dokud neskončí úloha. Úloha je často očekávaná ihned, jakmile se vytvoří, jak ukazuje následující příklad.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 Však můžete oddělit vytvoření úkolu od čekání na úkol, pokud má váš program provádět jinou práci, která nezávisí na dokončení úkolu.  
  
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
  
 Mezi spuštěním úlohy a čekáním na ni, můžete spustit další úkoly. Další úkoly jsou implicitně spuštěny paralelně, ale žádná další vlákna nejsou vytvořena.  
  
 Následující program spustí tři asynchronní webové soubory ke stažení a pak je čeká v pořadí, ve kterém jsou volány. Všimněte si, když spustíte program, která nejsou úlohy vždy dokončeny v pořadí, ve kterém byly vytvořeny a očekávány. Spuštění spustit, když jste vytvořili, a jeden nebo více úkolů může skončit dříve, než metoda dosáhne výrazů await.  
  
> [!NOTE]
>  Abyste mohli absolvovat tento projekt, musíte mít Visual Studio 2012 nebo novějším a rozhraní .NET Framework 4.5 nebo vyšší v počítači nainstalována.  
  
 Další příklad spuštění více úloh současně, najdete v části [jak: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Můžete stáhnout kód pro tento příklad z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Vytvoření projektu  
  
1. Chcete-li nastavit aplikaci WPF, proveďte následující kroky. Můžete najít podrobné pokyny k těmto krokům uvádí [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Vytvoření aplikace WPF, která obsahuje textové pole a tlačítko. Pojmenujte tlačítko `startButton`a pojmenujte textového pole `resultsTextBox`.  
  
    - Přidat odkaz pro <xref:System.Net.Http>.  
  
    - V souboru MainWindow.xaml.vb, přidejte `Imports` příkaz pro `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Přidání kódu  
  
1. V okně návrhu, MainWindow.xaml, dvakrát klikněte na tlačítko vytvořit `startButton_Click` obslužné rutiny události v souborech MainWindow.xaml.vb.  
  
2. Zkopírujte následující kód a vložte ho do těla `startButton_Click` v souboru MainWindow.xaml.vb.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     Kód volá asynchronní metodu, `CreateMultipleTasksAsync`, která řídí aplikaci.  
  
3. Do projektu přidejte následující metody podpory:  
  
    - `ProcessURLAsync` používá <xref:System.Net.Http.HttpClient> metodu pro stažení obsahu webu jako bajtové pole. Podpůrná metoda `ProcessURLAsync` potom zobrazí a vrátí délku pole.  
  
    - `DisplayResults` Zobrazí počet bajtů pro každou adresu URL v bajtovém poli. Toto zobrazení se ukazuje po dokončení stahování jednotlivých úkolů.  
  
     Následující metody zkopírujte a vložte je za `startButton_Click` obslužné rutiny události v souborech MainWindow.xaml.vb.  
  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4. Nakonec definujte metodu `CreateMultipleTasksAsync`, který provede následující kroky.  
  
    - Deklaruje metodu `HttpClient` objekt, který potřebuje získat přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.  
  
    - Metoda vytvoří a spustí tři úkoly typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo. Když každý úkol dokončí, `DisplayResults` zobrazí adresu URL úkolu a délku staženého obsahu. Vzhledem k tomu, že úkoly jsou spouštěny asynchronně, pořadí, ve kterém se zobrazí výsledky mohou lišit od pořadí, ve kterém byly deklarovány.  
  
    - Metoda čeká na ukončení každého úkolu. Každý `Await` operátor pozastaví provádění `CreateMultipleTasksAsync` dokud nebude dokončena očekávaná úloha. Operátor také použije vrácenou hodnotu z volání `ProcessURLAsync` z každého dokončeného úkolu.  
  
    - Když byly úlohy dokončeny a celočíselné hodnoty byly načteny, metoda sečte délky webových stránek a zobrazí výsledek.  
  
     Následující metodu zkopírujte a vložte ho do vašeho řešení.  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
  
5. Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
     Spusťte program několikrát a ověřte, že ve stejném pořadí nejsou vždy dokončeny tři úkoly a pořadí, ve kterém jsou dokončeny není nutně pořadí, ve kterém byly vytvořeny a očekávány.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje úplný příklad.  
  
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
            ProcessURLAsync("https://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Viz také:

- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Postupy: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
