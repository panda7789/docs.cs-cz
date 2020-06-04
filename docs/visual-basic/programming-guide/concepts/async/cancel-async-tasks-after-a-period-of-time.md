---
title: Zrušení úloh s modifikátorem Async po uplynutí časového intervalu
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: 048d4c19d459905ea579ede96c69230e718d55aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396685"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="31855-102">Zrušení asynchronních úloh po určitém časovém intervalu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31855-102">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>

<span data-ttu-id="31855-103">Asynchronní operaci můžete zrušit po časovém intervalu pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, pokud nechcete čekat na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="31855-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="31855-104">Tato metoda naplánuje zrušení všech přidružených úloh, které nejsou dokončeny v časovém období určeném `CancelAfter` výrazem.</span><span class="sxs-lookup"><span data-stu-id="31855-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="31855-105">Tento příklad přidá do kódu, který je vyvíjen v rámci [zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) pro stažení seznamu webů a zobrazení délky obsahu každého z nich.</span><span class="sxs-lookup"><span data-stu-id="31855-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="31855-106">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="31855-106">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="31855-107">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="31855-107">Downloading the Example</span></span>

<span data-ttu-id="31855-108">Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="31855-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="31855-109">Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31855-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="31855-110">Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="31855-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="31855-111">V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="31855-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="31855-112">V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAfterTime** a pak zvolte **nastavit jako projekt po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="31855-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="31855-113">Kliknutím na klávesu F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="31855-113">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="31855-114">Vyberte klávesy CTRL + F5 pro spuštění projektu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="31855-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="31855-115">Spusťte program několikrát, abyste ověřili, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby.</span><span class="sxs-lookup"><span data-stu-id="31855-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

 <span data-ttu-id="31855-116">Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow. XAML. vb na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="31855-116">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="31855-117">Vytvoření příkladu</span><span class="sxs-lookup"><span data-stu-id="31855-117">Building the Example</span></span>

<span data-ttu-id="31855-118">Příklad v tomto tématu se přidá do projektu, který je vyvíjen v části [zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) pro zrušení seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="31855-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="31855-119">V příkladu se používá stejné uživatelské rozhraní, i když se tlačítko **Storno** nepoužívá explicitně.</span><span class="sxs-lookup"><span data-stu-id="31855-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="31855-120">Chcete-li sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelAListOfTasks** .</span><span class="sxs-lookup"><span data-stu-id="31855-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="31855-121">Přidejte změny v tomto tématu do projektu.</span><span class="sxs-lookup"><span data-stu-id="31855-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="31855-122">Chcete-li zadat maximální dobu před tím, než jsou úkoly označeny jako zrušené, přidejte volání do `CancelAfter` do `startButton_Click` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="31855-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="31855-123">Sčítání jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="31855-123">The addition is marked with asterisks.</span></span>

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

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
```

<span data-ttu-id="31855-124">Spusťte program několikrát, abyste ověřili, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby.</span><span class="sxs-lookup"><span data-stu-id="31855-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="31855-125">Následující výstup je ukázka:</span><span class="sxs-lookup"><span data-stu-id="31855-125">The following output is a sample:</span></span>

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="31855-126">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="31855-126">Complete Example</span></span>

<span data-ttu-id="31855-127">Následující kód je úplný text souboru MainWindow. XAML. vb pro příklad.</span><span class="sxs-lookup"><span data-stu-id="31855-127">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="31855-128">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="31855-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="31855-129">Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="31855-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="31855-130">Projekt si můžete stáhnout z části [Async Sample: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="31855-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

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

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
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

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="31855-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="31855-131">See also</span></span>

- [<span data-ttu-id="31855-132">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31855-132">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="31855-133">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31855-133">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="31855-134">Zrušení asynchronní úlohy nebo seznamu úloh (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31855-134">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="31855-135">Vyladění aplikace v asynchronním prostředí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31855-135">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="31855-136">Asynchronní vzorek: jemné ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="31855-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
