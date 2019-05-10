---
title: 'Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: e306722fca4e0215cf7b67d85763858d459a171a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642443"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="a686c-102">Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a686c-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="a686c-103">V asynchronní metodě jsou úlohy spuštěny při jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a686c-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="a686c-104">[Await](../../../../visual-basic/language-reference/operators/await-operator.md) operátor je použít pro úlohu v okamžiku v metodě, kdy zpracování nemůže pokračovat, dokud neskončí úloha.</span><span class="sxs-lookup"><span data-stu-id="a686c-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="a686c-105">Úloha je často očekávaná ihned, jakmile se vytvoří, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="a686c-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 <span data-ttu-id="a686c-106">Však můžete oddělit vytvoření úkolu od čekání na úkol, pokud má váš program provádět jinou práci, která nezávisí na dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="a686c-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
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
  
 <span data-ttu-id="a686c-107">Mezi spuštěním úlohy a čekáním na ni, můžete spustit další úkoly.</span><span class="sxs-lookup"><span data-stu-id="a686c-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="a686c-108">Další úkoly jsou implicitně spuštěny paralelně, ale žádná další vlákna nejsou vytvořena.</span><span class="sxs-lookup"><span data-stu-id="a686c-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="a686c-109">Následující program spustí tři asynchronní webové soubory ke stažení a pak je čeká v pořadí, ve kterém jsou volány.</span><span class="sxs-lookup"><span data-stu-id="a686c-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="a686c-110">Všimněte si, když spustíte program, která nejsou úlohy vždy dokončeny v pořadí, ve kterém byly vytvořeny a očekávány.</span><span class="sxs-lookup"><span data-stu-id="a686c-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="a686c-111">Spuštění spustit, když jste vytvořili, a jeden nebo více úkolů může skončit dříve, než metoda dosáhne výrazů await.</span><span class="sxs-lookup"><span data-stu-id="a686c-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a686c-112">Abyste mohli absolvovat tento projekt, musíte mít Visual Studio 2012 nebo novějším a rozhraní .NET Framework 4.5 nebo vyšší v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="a686c-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="a686c-113">Další příklad spuštění více úloh současně, najdete v části [jak: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="a686c-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="a686c-114">Můžete stáhnout kód pro tento příklad z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="a686c-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="a686c-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="a686c-115">To set up the project</span></span>  
  
1. <span data-ttu-id="a686c-116">Chcete-li nastavit aplikaci WPF, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="a686c-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="a686c-117">Můžete najít podrobné pokyny k těmto krokům uvádí [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a686c-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="a686c-118">Vytvoření aplikace WPF, která obsahuje textové pole a tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a686c-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="a686c-119">Pojmenujte tlačítko `startButton`a pojmenujte textového pole `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="a686c-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="a686c-120">Přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="a686c-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="a686c-121">V souboru MainWindow.xaml.vb, přidejte `Imports` příkaz pro `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="a686c-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="a686c-122">Přidání kódu</span><span class="sxs-lookup"><span data-stu-id="a686c-122">To add the code</span></span>  
  
1. <span data-ttu-id="a686c-123">V okně návrhu, MainWindow.xaml, dvakrát klikněte na tlačítko vytvořit `startButton_Click` obslužné rutiny události v souborech MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="a686c-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2. <span data-ttu-id="a686c-124">Zkopírujte následující kód a vložte ho do těla `startButton_Click` v souboru MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="a686c-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     <span data-ttu-id="a686c-125">Kód volá asynchronní metodu, `CreateMultipleTasksAsync`, která řídí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a686c-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="a686c-126">Do projektu přidejte následující metody podpory:</span><span class="sxs-lookup"><span data-stu-id="a686c-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="a686c-127">`ProcessURLAsync` používá <xref:System.Net.Http.HttpClient> metodu pro stažení obsahu webu jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="a686c-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="a686c-128">Podpůrná metoda `ProcessURLAsync` potom zobrazí a vrátí délku pole.</span><span class="sxs-lookup"><span data-stu-id="a686c-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="a686c-129">`DisplayResults` Zobrazí počet bajtů pro každou adresu URL v bajtovém poli.</span><span class="sxs-lookup"><span data-stu-id="a686c-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="a686c-130">Toto zobrazení se ukazuje po dokončení stahování jednotlivých úkolů.</span><span class="sxs-lookup"><span data-stu-id="a686c-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="a686c-131">Následující metody zkopírujte a vložte je za `startButton_Click` obslužné rutiny události v souborech MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="a686c-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
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
  
4. <span data-ttu-id="a686c-132">Nakonec definujte metodu `CreateMultipleTasksAsync`, který provede následující kroky.</span><span class="sxs-lookup"><span data-stu-id="a686c-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="a686c-133">Deklaruje metodu `HttpClient` objekt, který potřebuje získat přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="a686c-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="a686c-134">Metoda vytvoří a spustí tři úkoly typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="a686c-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="a686c-135">Když každý úkol dokončí, `DisplayResults` zobrazí adresu URL úkolu a délku staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="a686c-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="a686c-136">Vzhledem k tomu, že úkoly jsou spouštěny asynchronně, pořadí, ve kterém se zobrazí výsledky mohou lišit od pořadí, ve kterém byly deklarovány.</span><span class="sxs-lookup"><span data-stu-id="a686c-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="a686c-137">Metoda čeká na ukončení každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="a686c-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="a686c-138">Každý `Await` operátor pozastaví provádění `CreateMultipleTasksAsync` dokud nebude dokončena očekávaná úloha.</span><span class="sxs-lookup"><span data-stu-id="a686c-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="a686c-139">Operátor také použije vrácenou hodnotu z volání `ProcessURLAsync` z každého dokončeného úkolu.</span><span class="sxs-lookup"><span data-stu-id="a686c-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="a686c-140">Když byly úlohy dokončeny a celočíselné hodnoty byly načteny, metoda sečte délky webových stránek a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="a686c-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="a686c-141">Následující metodu zkopírujte a vložte ho do vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="a686c-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5. <span data-ttu-id="a686c-142">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a686c-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="a686c-143">Spusťte program několikrát a ověřte, že ve stejném pořadí nejsou vždy dokončeny tři úkoly a pořadí, ve kterém jsou dokončeny není nutně pořadí, ve kterém byly vytvořeny a očekávány.</span><span class="sxs-lookup"><span data-stu-id="a686c-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a686c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="a686c-144">Example</span></span>  
 <span data-ttu-id="a686c-145">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="a686c-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a686c-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a686c-146">See also</span></span>

- [<span data-ttu-id="a686c-147">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a686c-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="a686c-148">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a686c-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="a686c-149">Postupy: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a686c-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
