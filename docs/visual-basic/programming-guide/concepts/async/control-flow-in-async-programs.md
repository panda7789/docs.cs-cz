---
title: Řízení toku v asynchronních programech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 265efde93cec87594a0407309b58b6bdf11817af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630606"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="a9360-102">Řízení toku v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9360-102">Control Flow in Async Programs (Visual Basic)</span></span>

<span data-ttu-id="a9360-103">Pomocí `Async` klíčových slov a `Await` můžete snadno psát a spravovat asynchronní programy.</span><span class="sxs-lookup"><span data-stu-id="a9360-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="a9360-104">Pokud ale nerozumíte tomu, jak program funguje, může se stát, že se výsledky neočekávaně neznají.</span><span class="sxs-lookup"><span data-stu-id="a9360-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="a9360-105">Toto téma sleduje tok řízení pomocí jednoduchého asynchronního programu, který vám ukáže, kdy se ovládací prvek přesouvá z jedné metody na jinou a jaké informace se přenášejí pokaždé.</span><span class="sxs-lookup"><span data-stu-id="a9360-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

> [!NOTE]
> <span data-ttu-id="a9360-106">Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a9360-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>

<span data-ttu-id="a9360-107">Obecně je třeba označit metody, které obsahují asynchronní kód, pomocí modifikátoru [Async](../../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="a9360-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="a9360-108">V metodě, která je označena modifikátorem Async, můžete použít operátor [await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) , chcete-li určit, kde metoda pozastaví čekání na dokončení volaného asynchronního procesu.</span><span class="sxs-lookup"><span data-stu-id="a9360-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="a9360-109">Další informace naleznete v tématu [asynchronní programování s Async a await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9360-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="a9360-110">Následující příklad používá asynchronní metody ke stažení obsahu zadaného webu jako řetězce a k zobrazení délky řetězce.</span><span class="sxs-lookup"><span data-stu-id="a9360-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="a9360-111">Příklad obsahuje následující dvě metody.</span><span class="sxs-lookup"><span data-stu-id="a9360-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="a9360-112">`startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="a9360-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="a9360-113">`AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="a9360-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="a9360-114">`AccessTheWebAsync`k stažení obsahu <xref:System.Net.Http.HttpClient> používá asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>metodu.</span><span class="sxs-lookup"><span data-stu-id="a9360-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="a9360-115">Číslované zobrazené řádky se zobrazí ve strategických bodech v rámci programu, které vám pomůžou pochopit, jak se program spouští, a vysvětlit, co se stane v každém označeném místě.</span><span class="sxs-lookup"><span data-stu-id="a9360-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="a9360-116">Zobrazované řádky jsou označeny "ONE" až "šest".</span><span class="sxs-lookup"><span data-stu-id="a9360-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="a9360-117">Popisky znázorňují pořadí, ve kterém program dosáhne těchto řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="a9360-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="a9360-118">Následující kód ukazuje osnovu programu.</span><span class="sxs-lookup"><span data-stu-id="a9360-118">The following code shows an outline of the program.</span></span>

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

<span data-ttu-id="a9360-119">Každé z označených umístění, "jedna" až "šest", zobrazí informace o aktuálním stavu programu.</span><span class="sxs-lookup"><span data-stu-id="a9360-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="a9360-120">Vytvoří se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="a9360-120">The following output is produced.</span></span>

```
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

## <a name="set-up-the-program"></a><span data-ttu-id="a9360-121">Vytvoření programu</span><span class="sxs-lookup"><span data-stu-id="a9360-121">Set Up the Program</span></span>

<span data-ttu-id="a9360-122">Můžete si stáhnout kód, který toto téma používá z MSDN, nebo si ho můžete vytvořit sami.</span><span class="sxs-lookup"><span data-stu-id="a9360-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="a9360-123">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a9360-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="a9360-124">Stažení programu</span><span class="sxs-lookup"><span data-stu-id="a9360-124">Download the Program</span></span>

<span data-ttu-id="a9360-125">Aplikaci pro toto téma si můžete stáhnout z [Async Sample: Řízení toku v asynchronních](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)programech.</span><span class="sxs-lookup"><span data-stu-id="a9360-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="a9360-126">Následující kroky otevřete a spusťte v programu.</span><span class="sxs-lookup"><span data-stu-id="a9360-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="a9360-127">Rozbalte stažený soubor a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9360-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="a9360-128">Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="a9360-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="a9360-129">Přejděte do složky, která obsahuje vzorový kód Get, otevřete soubor řešení (. sln) a pak zvolte klávesu F5 pro sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="a9360-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>

### <a name="build-the-program-yourself"></a><span data-ttu-id="a9360-130">Vytvoření programu vlastními silami</span><span class="sxs-lookup"><span data-stu-id="a9360-130">Build the Program Yourself</span></span>

<span data-ttu-id="a9360-131">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="a9360-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="a9360-132">Chcete-li spustit projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="a9360-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="a9360-133">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9360-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="a9360-134">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a9360-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="a9360-135">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a9360-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="a9360-136">V podokně **Nainstalované šablony** zvolte možnost **Visual Basic**a v seznamu typů projektů zvolte možnost **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="a9360-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="a9360-137">Jako `AsyncTracer` název projektu zadejte a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="a9360-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

    <span data-ttu-id="a9360-138">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="a9360-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="a9360-139">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="a9360-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

    <span data-ttu-id="a9360-140">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a9360-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="a9360-141">V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="a9360-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

    <span data-ttu-id="a9360-142">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="a9360-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="a9360-143">Přidejte odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="a9360-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="a9360-144">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow. XAML. vb a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a9360-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

9. <span data-ttu-id="a9360-145">V souboru MainWindow. XAML. vb nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="a9360-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

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

10. <span data-ttu-id="a9360-146">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="a9360-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="a9360-147">Měl by se zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="a9360-147">The following output should appear.</span></span>

    ```
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

## <a name="trace-the-program"></a><span data-ttu-id="a9360-148">Trasování programu</span><span class="sxs-lookup"><span data-stu-id="a9360-148">Trace the Program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="a9360-149">Kroky 1 a 2</span><span class="sxs-lookup"><span data-stu-id="a9360-149">Steps ONE and TWO</span></span>

<span data-ttu-id="a9360-150">První dva zobrazené řádky `startButton_Click` sledují cestu jako volání `AccessTheWebAsync`a `AccessTheWebAsync` volají asynchronní <xref:System.Net.Http.HttpClient> metodu <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="a9360-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="a9360-151">Následující obrázek znázorňuje volání metody z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="a9360-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="a9360-152">![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace – ONETWO")</span><span class="sxs-lookup"><span data-stu-id="a9360-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="a9360-153">Návratový typ obojí `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="a9360-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a9360-154">Pro `AccessTheWebAsync`TResult je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="a9360-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="a9360-155">V `GetStringAsync`případě je TResult řetězec.</span><span class="sxs-lookup"><span data-stu-id="a9360-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="a9360-156">Další informace o návratových typech asynchronní metody naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="a9360-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="a9360-157">Asynchronní metoda vracející úlohu vrátí instanci úlohy, pokud se ovládací prvek posune zpět na volajícího.</span><span class="sxs-lookup"><span data-stu-id="a9360-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="a9360-158">Řízení se vrátí z asynchronní metody volajícímu buď v případě `Await` , že je v volané metodě zjištěn operátor nebo když volaná metoda končí.</span><span class="sxs-lookup"><span data-stu-id="a9360-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="a9360-159">V této části procesu jsou zobrazené řádky s označením "tři" až "šest".</span><span class="sxs-lookup"><span data-stu-id="a9360-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="a9360-160">Krok 3</span><span class="sxs-lookup"><span data-stu-id="a9360-160">Step THREE</span></span>

<span data-ttu-id="a9360-161">V `AccessTheWebAsync`systému je volána asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> metoda pro stažení obsahu cílové webové stránky.</span><span class="sxs-lookup"><span data-stu-id="a9360-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="a9360-162">Ovládací prvek vrátí `client.GetStringAsync` z `AccessTheWebAsync` na `client.GetStringAsync` hodnotu when.</span><span class="sxs-lookup"><span data-stu-id="a9360-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

<span data-ttu-id="a9360-163">Metoda vrátí úlohu řetězce, který je přiřazen `getStringTask` proměnné v `AccessTheWebAsync`. `client.GetStringAsync`</span><span class="sxs-lookup"><span data-stu-id="a9360-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="a9360-164">Následující řádek v ukázkovém programu zobrazuje volání `client.GetStringAsync` a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a9360-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

<span data-ttu-id="a9360-165">Úkol si můžete představit jako příslib tím, že `client.GetStringAsync` budete chtít vytvořit skutečný řetězec nakonec.</span><span class="sxs-lookup"><span data-stu-id="a9360-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="a9360-166">Pokud `AccessTheWebAsync` v tuto chvíli funguje práce, která nezávisí na přislíbeném řetězci z `client.GetStringAsync`, může tato práce pokračovat během `client.GetStringAsync` čekání.</span><span class="sxs-lookup"><span data-stu-id="a9360-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="a9360-167">V příkladu představují následující řádky výstupu, které jsou označeny "tři", možnost provést nezávislou práci.</span><span class="sxs-lookup"><span data-stu-id="a9360-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="a9360-168">Následující příkaz pozastaví průběh v `AccessTheWebAsync` případě, kdy `getStringTask` je očekáván.</span><span class="sxs-lookup"><span data-stu-id="a9360-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```vb
Dim urlContents As String = Await getStringTask
```

<span data-ttu-id="a9360-169">Následující obrázek ukazuje tok řízení od `client.GetStringAsync` k přiřazení do `getStringTask` `getStringTask` a od vytvoření k aplikaci operátoru await.</span><span class="sxs-lookup"><span data-stu-id="a9360-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>

<span data-ttu-id="a9360-170">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace – tři")</span><span class="sxs-lookup"><span data-stu-id="a9360-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

<span data-ttu-id="a9360-171">Výraz Await se pozastaví `AccessTheWebAsync` , `client.GetStringAsync` dokud se nevrátí.</span><span class="sxs-lookup"><span data-stu-id="a9360-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="a9360-172">Mezitím se ovládací prvek vrátí volajícímu `AccessTheWebAsync`,. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="a9360-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="a9360-173">Obvykle očekáváte okamžité volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="a9360-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="a9360-174">Například následující přiřazení může nahradit předchozí kód, který vytvoří a následně očekává `getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="a9360-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>
>
> <span data-ttu-id="a9360-175">V tomto tématu se použije operátor await později, aby se vešel na výstupní řádky, které označují tok řízení přes program.</span><span class="sxs-lookup"><span data-stu-id="a9360-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="a9360-176">Krok 4</span><span class="sxs-lookup"><span data-stu-id="a9360-176">Step FOUR</span></span>

<span data-ttu-id="a9360-177">Deklarovaný návratový typ `AccessTheWebAsync` je `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="a9360-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="a9360-178">Proto když `AccessTheWebAsync` je pozastaveno, vrátí úlohu typu Integer na `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="a9360-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="a9360-179">Měli byste pochopit, že vrácená úloha není `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="a9360-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="a9360-180">Vrácený úkol je nový úkol na celé číslo, který představuje to, co je potřeba udělat v pozastavené `AccessTheWebAsync`metodě.</span><span class="sxs-lookup"><span data-stu-id="a9360-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="a9360-181">Úkol je příslib z `AccessTheWebAsync` a vytvoří celé číslo po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="a9360-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="a9360-182">Následující příkaz přiřadí tuto úlohu k `getLengthTask` proměnné.</span><span class="sxs-lookup"><span data-stu-id="a9360-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

<span data-ttu-id="a9360-183">Stejně jako `AccessTheWebAsync`v `startButton_Click` aplikaci může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`), dokud není očekávána úloha.</span><span class="sxs-lookup"><span data-stu-id="a9360-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="a9360-184">Následující výstupní řádky označují, že fungují.</span><span class="sxs-lookup"><span data-stu-id="a9360-184">The following output lines represent that work.</span></span>

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

<span data-ttu-id="a9360-185">Průběh je pozastaven, když `getLengthTask` je očekáváno. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="a9360-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="a9360-186">Následující příkaz přiřazení se pozastaví `startButton_Click` , `AccessTheWebAsync` dokud není dokončen.</span><span class="sxs-lookup"><span data-stu-id="a9360-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="a9360-187">Na následujícím obrázku šipky ukazují tok řízení z výrazu await `AccessTheWebAsync` v pro přiřazení hodnoty k `getLengthTask`, následované normálním zpracováním v `startButton_Click` `getLengthTask` případě, že je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="a9360-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

<span data-ttu-id="a9360-188">![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace – čtyři")</span><span class="sxs-lookup"><span data-stu-id="a9360-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="a9360-189">Krok 5</span><span class="sxs-lookup"><span data-stu-id="a9360-189">Step FIVE</span></span>

<span data-ttu-id="a9360-190">Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování `AccessTheWebAsync` v nástroji je uvolněno z pozastavení a může pokračovat za příkazem await.</span><span class="sxs-lookup"><span data-stu-id="a9360-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="a9360-191">Následující řádky výstupu reprezentují pokračování zpracování.</span><span class="sxs-lookup"><span data-stu-id="a9360-191">The following lines of output represent the resumption of processing.</span></span>

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

<span data-ttu-id="a9360-192">Operand příkazu return, `urlContents.Length`, je uložen v úloze, která `AccessTheWebAsync` vrací.</span><span class="sxs-lookup"><span data-stu-id="a9360-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="a9360-193">Výraz Await načte tuto hodnotu z `getLengthTask` v. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="a9360-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

<span data-ttu-id="a9360-194">Následující obrázek znázorňuje přenos řízení po `client.GetStringAsync` dokončení (a `getStringTask`).</span><span class="sxs-lookup"><span data-stu-id="a9360-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

<span data-ttu-id="a9360-195">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace – pět")</span><span class="sxs-lookup"><span data-stu-id="a9360-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

<span data-ttu-id="a9360-196">`AccessTheWebAsync`Spustí se k dokončení a řízení se vrátí `startButton_Click`do, což čeká na dokončení.</span><span class="sxs-lookup"><span data-stu-id="a9360-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="a9360-197">Krok 6</span><span class="sxs-lookup"><span data-stu-id="a9360-197">Step SIX</span></span>

<span data-ttu-id="a9360-198">Když `AccessTheWebAsync` signalizuje, že je dokončeno, zpracování může pokračovat za příkazem await v `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="a9360-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="a9360-199">Ve skutečnosti program nemá nic dalšího.</span><span class="sxs-lookup"><span data-stu-id="a9360-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="a9360-200">Následující řádky výstupu reprezentují pokračování zpracování v `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="a9360-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

<span data-ttu-id="a9360-201">Výraz Await se načte z `getLengthTask` celočíselné hodnoty, která je operandem příkazu return v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="a9360-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="a9360-202">Následující příkaz přiřadí tuto hodnotu k `contentLength` proměnné.</span><span class="sxs-lookup"><span data-stu-id="a9360-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="a9360-203">Následující obrázek ukazuje vrácení ovládacího prvku z `AccessTheWebAsync` na. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="a9360-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

<span data-ttu-id="a9360-204">![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace – šest")</span><span class="sxs-lookup"><span data-stu-id="a9360-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="a9360-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9360-205">See also</span></span>

- [<span data-ttu-id="a9360-206">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9360-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="a9360-207">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9360-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="a9360-208">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9360-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="a9360-209">Asynchronní Ukázka: Řízení toku v asynchronních programechC# (a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9360-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
