---
title: 'Postupy: paralelní provádění více webových požadavků pomocí modifikátoru Async a operátoru Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 9241a54b4b0d1a8871ef496d44e1e6db5581af7b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583157"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="f2f53-102">Postupy: paralelní provádění více webových požadavků pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f53-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="f2f53-103">V asynchronní metodě jsou úlohy spouštěny při jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f2f53-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="f2f53-104">Operátor [await](../../../../visual-basic/language-reference/operators/await-operator.md) se aplikuje na úkol v místě v metodě, kde zpracování nemůže pokračovat, dokud se úloha nedokončí.</span><span class="sxs-lookup"><span data-stu-id="f2f53-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="f2f53-105">Úkol se často očekává ihned po vytvoření, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f2f53-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

<span data-ttu-id="f2f53-106">Můžete ale oddělit vytvoření úlohy z čekání na úkol, pokud má program další práci, která nezávisí na dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="f2f53-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>

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

<span data-ttu-id="f2f53-107">Mezi zahájením úlohy a čekáním na ni můžete spustit další úlohy.</span><span class="sxs-lookup"><span data-stu-id="f2f53-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="f2f53-108">Další úkoly jsou implicitně spouštěny paralelně, ale nejsou vytvořeny žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="f2f53-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>

<span data-ttu-id="f2f53-109">Následující program spustí tři asynchronní webové stahování a pak je očekává v pořadí, ve kterém jsou volány.</span><span class="sxs-lookup"><span data-stu-id="f2f53-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="f2f53-110">Všimněte si, že při spuštění programu nejsou úlohy vždy dokončeny v pořadí, ve kterém byly vytvořeny a očekávány.</span><span class="sxs-lookup"><span data-stu-id="f2f53-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="f2f53-111">Spouštějí se při jejich vytvoření a jedna nebo více úkolů může skončit předtím, než metoda dosáhne výrazů await.</span><span class="sxs-lookup"><span data-stu-id="f2f53-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="f2f53-112">Chcete-li dokončit tento projekt, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo vyšší a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f2f53-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>

<span data-ttu-id="f2f53-113">Další příklad, který spouští více úloh současně, naleznete v tématu [How to: Extending the Async návod pomocí Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f2f53-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

<span data-ttu-id="f2f53-114">Kód pro tento příklad si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="f2f53-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>

### <a name="to-set-up-the-project"></a><span data-ttu-id="f2f53-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="f2f53-115">To set up the project</span></span>

1. <span data-ttu-id="f2f53-116">Chcete-li nastavit aplikaci WPF, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="f2f53-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="f2f53-117">Podrobné pokyny k těmto krokům najdete v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="f2f53-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="f2f53-118">Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f2f53-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="f2f53-119">Pojmenujte tlačítko `startButton` a pojmenujte textové pole `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="f2f53-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>

    - <span data-ttu-id="f2f53-120">Přidejte odkaz na <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f2f53-120">Add a reference for <xref:System.Net.Http>.</span></span>

    - <span data-ttu-id="f2f53-121">V souboru MainWindow. XAML. vb přidejte příkaz `Imports` pro `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="f2f53-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>

### <a name="to-add-the-code"></a><span data-ttu-id="f2f53-122">Přidání kódu</span><span class="sxs-lookup"><span data-stu-id="f2f53-122">To add the code</span></span>

1. <span data-ttu-id="f2f53-123">V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko a vytvořte obslužnou rutinu události `startButton_Click` v souboru MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="f2f53-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="f2f53-124">Zkopírujte následující kód a vložte ho do textu `startButton_Click` v souboru MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="f2f53-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     <span data-ttu-id="f2f53-125">Kód volá asynchronní metodu, `CreateMultipleTasksAsync`, která řídí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f2f53-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>

3. <span data-ttu-id="f2f53-126">Do projektu přidejte následující metody podpory:</span><span class="sxs-lookup"><span data-stu-id="f2f53-126">Add the following support methods to the project:</span></span>

    - <span data-ttu-id="f2f53-127">`ProcessURLAsync` používá metodu <xref:System.Net.Http.HttpClient> ke stažení obsahu webu jako bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="f2f53-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="f2f53-128">Metoda podpory `ProcessURLAsync` pak zobrazí a vrátí délku pole.</span><span class="sxs-lookup"><span data-stu-id="f2f53-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>

    - <span data-ttu-id="f2f53-129">`DisplayResults` zobrazuje počet bajtů v bajtovém poli pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="f2f53-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="f2f53-130">Toto zobrazení ukazuje, kdy se každý úkol dokončí stahováním.</span><span class="sxs-lookup"><span data-stu-id="f2f53-130">This display shows when each task has finished downloading.</span></span>

     <span data-ttu-id="f2f53-131">Zkopírujte následující metody a vložte je po `startButton_Click` obslužné rutiny události v souboru MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="f2f53-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

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

4. <span data-ttu-id="f2f53-132">Nakonec definujte metodu `CreateMultipleTasksAsync`, která provede následující kroky.</span><span class="sxs-lookup"><span data-stu-id="f2f53-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>

    - <span data-ttu-id="f2f53-133">Metoda deklaruje objekt `HttpClient`, který vyžaduje přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="f2f53-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>

    - <span data-ttu-id="f2f53-134">Metoda vytvoří a spustí tři úkoly typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="f2f53-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="f2f53-135">Po dokončení jednotlivých úloh `DisplayResults` zobrazí adresu URL úkolu a délku staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="f2f53-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="f2f53-136">Vzhledem k tomu, že úlohy jsou spuštěny asynchronně, pořadí, ve kterém se výsledky zobrazují, se může lišit od pořadí, ve kterém byly deklarovány.</span><span class="sxs-lookup"><span data-stu-id="f2f53-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>

    - <span data-ttu-id="f2f53-137">Metoda čeká na dokončení každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="f2f53-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="f2f53-138">Každý operátor `Await` pozastaví provádění `CreateMultipleTasksAsync`, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="f2f53-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="f2f53-139">Operátor také načítá návratovou hodnotu z volání `ProcessURLAsync` z každé dokončené úlohy.</span><span class="sxs-lookup"><span data-stu-id="f2f53-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>

    - <span data-ttu-id="f2f53-140">Po dokončení úloh a načtení celočíselných hodnot metoda sečte délky webů a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="f2f53-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>

     <span data-ttu-id="f2f53-141">Zkopírujte následující metodu a vložte ji do svého řešení.</span><span class="sxs-lookup"><span data-stu-id="f2f53-141">Copy the following method, and paste it into your solution.</span></span>

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

5. <span data-ttu-id="f2f53-142">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="f2f53-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="f2f53-143">Spusťte program několikrát, abyste ověřili, že tři úkoly nejsou vždy dokončeny ve stejném pořadí a že pořadí, ve kterém jsou dokončeny, nemusí být nutně pořadí, ve kterém byly vytvořeny a očekávány.</span><span class="sxs-lookup"><span data-stu-id="f2f53-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>

## <a name="example"></a><span data-ttu-id="f2f53-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2f53-144">Example</span></span>

<span data-ttu-id="f2f53-145">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="f2f53-145">The following code contains the full example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f2f53-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2f53-146">See also</span></span>

- [<span data-ttu-id="f2f53-147">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f53-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="f2f53-148">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f53-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f2f53-149">Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f53-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
