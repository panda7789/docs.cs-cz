---
title: Řízení toku v asynchronních programech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 74942ec3d293485ea6aae3940d1715af8de67c90
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352114"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="f63e9-102">Řízení toku v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f63e9-102">Control Flow in Async Programs (Visual Basic)</span></span>

<span data-ttu-id="f63e9-103">Pomocí klíčových slov `Async` a `Await` můžete snadno psát a udržovat asynchronní programy.</span><span class="sxs-lookup"><span data-stu-id="f63e9-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="f63e9-104">Pokud ale nerozumíte tomu, jak program funguje, může se stát, že se výsledky neočekávaně neznají.</span><span class="sxs-lookup"><span data-stu-id="f63e9-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="f63e9-105">Toto téma sleduje tok řízení pomocí jednoduchého asynchronního programu, který vám ukáže, kdy se ovládací prvek přesouvá z jedné metody na jinou a jaké informace se přenášejí pokaždé.</span><span class="sxs-lookup"><span data-stu-id="f63e9-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

> [!NOTE]
> <span data-ttu-id="f63e9-106">Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f63e9-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>

<span data-ttu-id="f63e9-107">Obecně je třeba označit metody, které obsahují asynchronní kód, pomocí modifikátoru [Async](../../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="f63e9-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f63e9-108">V metodě, která je označena modifikátorem Async, můžete použít operátor [await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) , chcete-li určit, kde metoda pozastaví čekání na dokončení volaného asynchronního procesu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="f63e9-109">Další informace naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f63e9-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="f63e9-110">Následující příklad používá asynchronní metody ke stažení obsahu zadaného webu jako řetězce a k zobrazení délky řetězce.</span><span class="sxs-lookup"><span data-stu-id="f63e9-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="f63e9-111">Příklad obsahuje následující dvě metody.</span><span class="sxs-lookup"><span data-stu-id="f63e9-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="f63e9-112">`startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="f63e9-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="f63e9-113">`AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="f63e9-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="f63e9-114">`AccessTheWebAsync` používá asynchronní metodu <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> ke stažení obsahu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="f63e9-115">Číslované zobrazené řádky se zobrazí ve strategických bodech v rámci programu, které vám pomůžou pochopit, jak se program spouští, a vysvětlit, co se stane v každém označeném místě.</span><span class="sxs-lookup"><span data-stu-id="f63e9-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="f63e9-116">Zobrazované řádky jsou označeny "ONE" až "šest".</span><span class="sxs-lookup"><span data-stu-id="f63e9-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="f63e9-117">Popisky znázorňují pořadí, ve kterém program dosáhne těchto řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="f63e9-118">Následující kód ukazuje osnovu programu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-118">The following code shows an outline of the program.</span></span>

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

<span data-ttu-id="f63e9-119">Každé z označených umístění, "jedna" až "šest", zobrazí informace o aktuálním stavu programu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="f63e9-120">Vytvoří se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f63e9-120">The following output is produced:</span></span>

```console
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="f63e9-121">Vytvoření programu</span><span class="sxs-lookup"><span data-stu-id="f63e9-121">Set Up the Program</span></span>

<span data-ttu-id="f63e9-122">Můžete si stáhnout kód, který toto téma používá z MSDN, nebo si ho můžete vytvořit sami.</span><span class="sxs-lookup"><span data-stu-id="f63e9-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="f63e9-123">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f63e9-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="f63e9-124">Stažení programu</span><span class="sxs-lookup"><span data-stu-id="f63e9-124">Download the Program</span></span>

<span data-ttu-id="f63e9-125">Aplikaci pro toto téma si můžete stáhnout z ukázky [Async: Řízení toku v asynchronních programech @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="f63e9-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="f63e9-126">Následující kroky otevřete a spusťte v programu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="f63e9-127">Rozbalte stažený soubor a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f63e9-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="f63e9-128">Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="f63e9-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="f63e9-129">Přejděte do složky, která obsahuje vzorový kód Get, otevřete soubor řešení (. sln) a pak zvolte klávesu F5 pro sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>

### <a name="build-the-program-yourself"></a><span data-ttu-id="f63e9-130">Vytvoření programu vlastními silami</span><span class="sxs-lookup"><span data-stu-id="f63e9-130">Build the Program Yourself</span></span>

<span data-ttu-id="f63e9-131">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="f63e9-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="f63e9-132">Chcete-li spustit projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="f63e9-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="f63e9-133">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f63e9-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="f63e9-134">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f63e9-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="f63e9-135">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f63e9-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="f63e9-136">V podokně **Nainstalované šablony** zvolte možnost **Visual Basic**a v seznamu typů projektů zvolte možnost **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="f63e9-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="f63e9-137">Jako název projektu zadejte `AsyncTracer` a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="f63e9-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

    <span data-ttu-id="f63e9-138">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="f63e9-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="f63e9-139">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="f63e9-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

    <span data-ttu-id="f63e9-140">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="f63e9-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="f63e9-141">V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="f63e9-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    <span data-ttu-id="f63e9-142">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="f63e9-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="f63e9-143">Přidejte odkaz na <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f63e9-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="f63e9-144">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="f63e9-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

9. <span data-ttu-id="f63e9-145">V souboru MainWindow. XAML. vb nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="f63e9-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. <span data-ttu-id="f63e9-146">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="f63e9-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="f63e9-147">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f63e9-147">The following output should appear:</span></span>

    ```console
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="f63e9-148">Trasování programu</span><span class="sxs-lookup"><span data-stu-id="f63e9-148">Trace the Program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="f63e9-149">Kroky 1 a 2</span><span class="sxs-lookup"><span data-stu-id="f63e9-149">Steps ONE and TWO</span></span>

<span data-ttu-id="f63e9-150">První dva zobrazené řádky sledují cestu jako `startButton_Click` volání `AccessTheWebAsync` a `AccessTheWebAsync` volá asynchronní metodu <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="f63e9-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="f63e9-151">Následující obrázek znázorňuje volání metody z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="f63e9-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="f63e9-152">![Postup jednoho a dvou](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="f63e9-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="f63e9-153">Návratový typ obou `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f63e9-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f63e9-154">V případě `AccessTheWebAsync` je TResult celé číslo.</span><span class="sxs-lookup"><span data-stu-id="f63e9-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="f63e9-155">V případě `GetStringAsync` je TResult řetězec.</span><span class="sxs-lookup"><span data-stu-id="f63e9-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="f63e9-156">Další informace o návratových typech asynchronní metody naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f63e9-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="f63e9-157">Asynchronní metoda vracející úlohu vrátí instanci úlohy, pokud se ovládací prvek posune zpět na volajícího.</span><span class="sxs-lookup"><span data-stu-id="f63e9-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="f63e9-158">Řízení se vrátí z asynchronní metody volajícímu buď v případě, že se v volané metodě objevil operátor `Await`, nebo když volaná metoda skončí.</span><span class="sxs-lookup"><span data-stu-id="f63e9-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="f63e9-159">V této části procesu jsou zobrazené řádky s označením "tři" až "šest".</span><span class="sxs-lookup"><span data-stu-id="f63e9-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="f63e9-160">Krok 3</span><span class="sxs-lookup"><span data-stu-id="f63e9-160">Step THREE</span></span>

<span data-ttu-id="f63e9-161">V `AccessTheWebAsync` je volána asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> pro stažení obsahu cílové webové stránky.</span><span class="sxs-lookup"><span data-stu-id="f63e9-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="f63e9-162">Řízení se vrátí z `client.GetStringAsync` do `AccessTheWebAsync`, když vrátí `client.GetStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

<span data-ttu-id="f63e9-163">Metoda `client.GetStringAsync` vrátí úlohu typu String, která je přiřazena proměnné `getStringTask` v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="f63e9-164">Následující řádek v ukázkovém programu zobrazuje volání `client.GetStringAsync` a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="f63e9-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

<span data-ttu-id="f63e9-165">Úkol můžete představit jako příslib tím, že `client.GetStringAsync` a nakonec vytvořit skutečný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f63e9-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="f63e9-166">Pokud `AccessTheWebAsync` v tuto chvíli funguje, to nezávisí na přislíbeném řetězci z `client.GetStringAsync`, může tato práce pokračovat, i když `client.GetStringAsync` počká.</span><span class="sxs-lookup"><span data-stu-id="f63e9-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="f63e9-167">V příkladu představují následující řádky výstupu, které jsou označeny "tři", možnost provést nezávislou práci.</span><span class="sxs-lookup"><span data-stu-id="f63e9-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="f63e9-168">Následující příkaz pozastaví průběh `AccessTheWebAsync`, když je očekávána `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```vb
Dim urlContents As String = Await getStringTask
```

<span data-ttu-id="f63e9-169">Následující obrázek ukazuje tok řízení z `client.GetStringAsync` do přiřazení `getStringTask` a od vytvoření `getStringTask` k aplikaci operátoru await.</span><span class="sxs-lookup"><span data-stu-id="f63e9-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>

<span data-ttu-id="f63e9-170">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace – tři")</span><span class="sxs-lookup"><span data-stu-id="f63e9-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

<span data-ttu-id="f63e9-171">Výraz Await pozastaví `AccessTheWebAsync`, dokud nevrátí `client.GetStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="f63e9-172">Mezitím se ovládací prvek vrátí volajícímu `AccessTheWebAsync` `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="f63e9-173">Obvykle očekáváte okamžité volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="f63e9-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="f63e9-174">Například následující přiřazení může nahradit předchozí kód, který vytvoří a potom očekává `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>
>
> <span data-ttu-id="f63e9-175">V tomto tématu se použije operátor await později, aby se vešel na výstupní řádky, které označují tok řízení přes program.</span><span class="sxs-lookup"><span data-stu-id="f63e9-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="f63e9-176">Krok 4</span><span class="sxs-lookup"><span data-stu-id="f63e9-176">Step FOUR</span></span>

<span data-ttu-id="f63e9-177">Deklarovaný návratový typ `AccessTheWebAsync` je `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="f63e9-178">Proto když je `AccessTheWebAsync` pozastaven, vrátí úlohu typu Integer do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="f63e9-179">Měli byste pochopit, že vrácená úloha není `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="f63e9-180">Vrácený úkol je nový úkol na celé číslo, který představuje to, co je potřeba udělat v pozastavené metodě, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="f63e9-181">Úkol je příslib z `AccessTheWebAsync` a vytvořit tak celé číslo po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="f63e9-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="f63e9-182">Následující příkaz přiřadí tuto úlohu proměnné `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

<span data-ttu-id="f63e9-183">Stejně jako v `AccessTheWebAsync` může `startButton_Click` pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`) až do doby, kdy je úloha očekávána.</span><span class="sxs-lookup"><span data-stu-id="f63e9-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="f63e9-184">Následující výstupní řádky označují, že fungují:</span><span class="sxs-lookup"><span data-stu-id="f63e9-184">The following output lines represent that work:</span></span>

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

<span data-ttu-id="f63e9-185">Průběh v `startButton_Click` se pozastaví, když se očekává `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="f63e9-186">Následující příkaz přiřazení pozastaví `startButton_Click`, dokud se nedokončí `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="f63e9-187">Na následujícím obrázku šipky ukazují tok řízení z výrazu await v `AccessTheWebAsync` až po přiřazení hodnoty `getLengthTask`, za nímž následuje normální zpracování v `startButton_Click`, dokud není očekávána hodnota `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

<span data-ttu-id="f63e9-188">![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace – čtyři")</span><span class="sxs-lookup"><span data-stu-id="f63e9-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="f63e9-189">Krok 5</span><span class="sxs-lookup"><span data-stu-id="f63e9-189">Step FIVE</span></span>

<span data-ttu-id="f63e9-190">Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování v `AccessTheWebAsync` je uvolněno z pozastavení a může pokračovat za příkazem await.</span><span class="sxs-lookup"><span data-stu-id="f63e9-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="f63e9-191">Následující řádky výstupu reprezentují pokračování zpracování:</span><span class="sxs-lookup"><span data-stu-id="f63e9-191">The following lines of output represent the resumption of processing:</span></span>

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

<span data-ttu-id="f63e9-192">Operand příkazu return, `urlContents.Length`, je uložen v úkolu, který vrací `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="f63e9-193">Výraz Await načte tuto hodnotu z `getLengthTask` v `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

<span data-ttu-id="f63e9-194">Následující obrázek znázorňuje přenos řízení po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="f63e9-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

<span data-ttu-id="f63e9-195">![5. krok](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-pět")</span><span class="sxs-lookup"><span data-stu-id="f63e9-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

<span data-ttu-id="f63e9-196">`AccessTheWebAsync` se spustí do dokončení a řízení se vrátí do `startButton_Click`, což čeká na dokončení.</span><span class="sxs-lookup"><span data-stu-id="f63e9-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="f63e9-197">Krok 6</span><span class="sxs-lookup"><span data-stu-id="f63e9-197">Step SIX</span></span>

<span data-ttu-id="f63e9-198">Když `AccessTheWebAsync` signalizuje, že je dokončeno, zpracování může pokračovat za příkazem await v `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="f63e9-199">Ve skutečnosti program nemá nic dalšího.</span><span class="sxs-lookup"><span data-stu-id="f63e9-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="f63e9-200">Následující řádky výstupu reprezentují pokračování zpracování v `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="f63e9-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

<span data-ttu-id="f63e9-201">Výraz Await načte z `getLengthTask` celočíselnou hodnotu, která je operandem příkazu return v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="f63e9-202">Následující příkaz přiřadí tuto hodnotu k proměnné `contentLength`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="f63e9-203">Následující obrázek ukazuje vrácení ovládacího prvku z `AccessTheWebAsync` do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f63e9-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

<span data-ttu-id="f63e9-204">![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-šest")</span><span class="sxs-lookup"><span data-stu-id="f63e9-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="f63e9-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f63e9-205">See also</span></span>

- [<span data-ttu-id="f63e9-206">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f63e9-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f63e9-207">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f63e9-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="f63e9-208">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="f63e9-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="f63e9-209">Asynchronní Ukázka: Řízení toku v asynchronních programechC# (a Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="f63e9-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
