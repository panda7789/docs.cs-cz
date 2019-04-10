---
title: Tok řízení v asynchronních programech (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: ed993943bcf7341f900c575744a1faa53a4a8a2e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300928"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="caf3c-102">Tok řízení v asynchronních programech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caf3c-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="caf3c-103">Můžete napsat a snadněji udržovat asynchronní programy pomocí `Async` a `Await` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="caf3c-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="caf3c-104">Ale výsledků možná vás překvapí Pokud nevíte, jak program pracuje.</span><span class="sxs-lookup"><span data-stu-id="caf3c-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="caf3c-105">Toto téma sleduje tok řízení prostřednictvím jednoduchého asynchronního programu k zobrazení, když se ovládací prvek přesune z jedné metody na jinou a jaké informace jsou pokaždé přeneseny.</span><span class="sxs-lookup"><span data-stu-id="caf3c-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caf3c-106">Klíčová slova `Async` a `Await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="caf3c-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="caf3c-107">Obecně označujete metody, které obsahují asynchronní kód s [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="caf3c-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="caf3c-108">V metodě, která je označena asynchronním modifikátorem, můžete použít [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operátor k určení, kde Metoda počká na dokončení volaného asynchronního procesu.</span><span class="sxs-lookup"><span data-stu-id="caf3c-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="caf3c-109">Další informace najdete v tématu [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="caf3c-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="caf3c-110">Následující příklad používá asynchronní metody ke stahování obsahu zadaného webu jako řetězec a zobrazí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="caf3c-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="caf3c-111">Tento příklad obsahuje následující dvě metody.</span><span class="sxs-lookup"><span data-stu-id="caf3c-111">The example contains the following two methods.</span></span>  
  
-   `startButton_Click`<span data-ttu-id="caf3c-112">, který volá `AccessTheWebAsync` a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="caf3c-112">, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   `AccessTheWebAsync`<span data-ttu-id="caf3c-113">, který stáhne obsah webu jako řetězec a vrátí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="caf3c-113">, which downloads the contents of a website as a string and returns the length of the string.</span></span> `AccessTheWebAsync` <span data-ttu-id="caf3c-114">používá asynchronní <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, chcete-li stáhnout obsah.</span><span class="sxs-lookup"><span data-stu-id="caf3c-114">uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="caf3c-115">Číslované řádky se zobrazí strategická místa v celém programu, které vám pomohou pochopit, jak program funguje a co se stane v každém bodu, který je označen jako zobrazení.</span><span class="sxs-lookup"><span data-stu-id="caf3c-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="caf3c-116">Zobrazené řádky jsou označeny "Jedna"až "šest."</span><span class="sxs-lookup"><span data-stu-id="caf3c-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="caf3c-117">Popisky představují pořadí, ve kterém dosáhne program tyto řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="caf3c-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="caf3c-118">Následující kód ukazuje osnovu třídy program.</span><span class="sxs-lookup"><span data-stu-id="caf3c-118">The following code shows an outline of the program.</span></span>  
  
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
  
 <span data-ttu-id="caf3c-119">Každé z označených míst "Jedna"až "šest" zobrazí informace o aktuálním stavu programu.</span><span class="sxs-lookup"><span data-stu-id="caf3c-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="caf3c-120">Následující výstup je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="caf3c-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="caf3c-121">Vytvoření programu</span><span class="sxs-lookup"><span data-stu-id="caf3c-121">Set Up the Program</span></span>  
 <span data-ttu-id="caf3c-122">Kód, který se používá v tomto tématu si můžete stáhnout z webu MSDN nebo si ho můžete vytvořit sami.</span><span class="sxs-lookup"><span data-stu-id="caf3c-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caf3c-123">Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="caf3c-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="caf3c-124">Stažení programu</span><span class="sxs-lookup"><span data-stu-id="caf3c-124">Download the Program</span></span>  
 <span data-ttu-id="caf3c-125">Můžete stáhnout aplikaci pro toto téma z [asynchronní vzorek: Řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="caf3c-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="caf3c-126">Následující postup otevře a spustí program.</span><span class="sxs-lookup"><span data-stu-id="caf3c-126">The following steps open and run the program.</span></span>  
  
1. <span data-ttu-id="caf3c-127">Rozbalte stažený soubor a poté spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="caf3c-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="caf3c-128">V panelu nabídky zvolte **souboru**, **otevřít**, **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="caf3c-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="caf3c-129">Přejděte do složky obsahující dekomprimovaný ukázkový kód, otevřete soubor řešení (.sln) a pak zvolte klávesu F5 sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="caf3c-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="caf3c-130">Vytvoření programu vlastními silami</span><span class="sxs-lookup"><span data-stu-id="caf3c-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="caf3c-131">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="caf3c-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="caf3c-132">Spusťte projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="caf3c-132">To run the project, perform the following steps:</span></span>  
  
1. <span data-ttu-id="caf3c-133">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="caf3c-133">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="caf3c-134">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="caf3c-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="caf3c-135">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="caf3c-135">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="caf3c-136">V **nainstalované šablony** podokně zvolte **jazyka Visual Basic**a klikněte na tlačítko **aplikace WPF** ze seznamu typů projektů.</span><span class="sxs-lookup"><span data-stu-id="caf3c-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4. <span data-ttu-id="caf3c-137">Zadejte `AsyncTracer` jako název projektu a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="caf3c-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="caf3c-138">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="caf3c-138">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="caf3c-139">V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.</span><span class="sxs-lookup"><span data-stu-id="caf3c-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="caf3c-140">Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="caf3c-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6. <span data-ttu-id="caf3c-141">V **XAML** zobrazení souboru mainwindow.XAML, nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="caf3c-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="caf3c-142">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** zobrazení souboru MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="caf3c-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7. <span data-ttu-id="caf3c-143">Přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="caf3c-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8. <span data-ttu-id="caf3c-144">V **Průzkumníka řešení**, otevřete místní nabídku pro soubor MainWindow.xaml.vb a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="caf3c-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="caf3c-145">V souboru MainWindow.xaml.vb nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="caf3c-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
  
10. <span data-ttu-id="caf3c-146">Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="caf3c-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="caf3c-147">By se zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="caf3c-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="caf3c-148">Trasování programu</span><span class="sxs-lookup"><span data-stu-id="caf3c-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="caf3c-149">Kroky 1 a 2</span><span class="sxs-lookup"><span data-stu-id="caf3c-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="caf3c-150">První dva zobrazené řádky sledují cestu jako `startButton_Click` volání `AccessTheWebAsync`, a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="caf3c-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="caf3c-151">Následující obrázek popisuje volání z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="caf3c-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="caf3c-152">![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="caf3c-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="caf3c-153">Návratový typ obou `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="caf3c-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="caf3c-154">Pro `AccessTheWebAsync`, je TResult celé číslo.</span><span class="sxs-lookup"><span data-stu-id="caf3c-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="caf3c-155">Pro `GetStringAsync`, TResult je řetězec.</span><span class="sxs-lookup"><span data-stu-id="caf3c-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="caf3c-156">Další informace o asynchronních návratových typech metod naleznete v tématu [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="caf3c-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="caf3c-157">Asynchronní metody vracející úlohy vrátí instance úlohy, když ovládací prvek přepne zpět do volajícího.</span><span class="sxs-lookup"><span data-stu-id="caf3c-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="caf3c-158">Se řízení vrací z asynchronní metodu jeho volajícímu buď pokud `Await` se střetne s operátorem ve volané metodě, nebo po ukončení volané metody.</span><span class="sxs-lookup"><span data-stu-id="caf3c-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="caf3c-159">Zobrazené řádky, které jsou označeny jako "Tři"až "šest" trasují tuto část procesu.</span><span class="sxs-lookup"><span data-stu-id="caf3c-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="caf3c-160">Krok 3</span><span class="sxs-lookup"><span data-stu-id="caf3c-160">Step THREE</span></span>  
 <span data-ttu-id="caf3c-161">V `AccessTheWebAsync`, asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> volána ke stažení obsahu cílové webové stránky.</span><span class="sxs-lookup"><span data-stu-id="caf3c-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="caf3c-162">Ovládací prvek vrátí `client.GetStringAsync` k `AccessTheWebAsync` při `client.GetStringAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="caf3c-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="caf3c-163">`client.GetStringAsync` Metoda vrátí úlohu řetězce, který je přiřazen `getStringTask` proměnné v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="caf3c-164">Následující řádek v příkladu programu ukazuje volání do `client.GetStringAsync` a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="caf3c-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
```  
  
 <span data-ttu-id="caf3c-165">Úlohy si můžete představit jako za příslib od `client.GetStringAsync` nakonec vytvoří vytvoření skutečného řetězce.</span><span class="sxs-lookup"><span data-stu-id="caf3c-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="caf3c-166">Do té doby Pokud `AccessTheWebAsync` má pracovní postup, která není závislá na přislíbeném řetězci z `client.GetStringAsync`, této práci pokračovat během `client.GetStringAsync` čeká.</span><span class="sxs-lookup"><span data-stu-id="caf3c-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="caf3c-167">V tomto příkladu představují následující řádky výstupu, které nesou označení "Tři", příležitost k nezávislé práci.</span><span class="sxs-lookup"><span data-stu-id="caf3c-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="caf3c-168">Následující příkaz pozastaví průběh `AccessTheWebAsync` při `getStringTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="caf3c-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 <span data-ttu-id="caf3c-169">Následující obrázek znázorňuje tok řízení z `client.GetStringAsync` k přiřazení na `getStringTask` a od vytvoření `getStringTask` k použití operátoru Await.</span><span class="sxs-lookup"><span data-stu-id="caf3c-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="caf3c-170">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace tři")</span><span class="sxs-lookup"><span data-stu-id="caf3c-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="caf3c-171">Výraz await pozastaví `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="caf3c-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="caf3c-172">Do té doby se ovládací prvek vrátí volajícímu metody `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caf3c-173">Obvykle můžete očekávat volání asynchronní metody okamžitě.</span><span class="sxs-lookup"><span data-stu-id="caf3c-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="caf3c-174">Například následující přiřazení může nahradit předchozí kód, který vytvoří a poté očekává `getStringTask`:</span><span class="sxs-lookup"><span data-stu-id="caf3c-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`:</span></span> `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`  
>   
>  <span data-ttu-id="caf3c-175">V tomto tématu je později použit operátor await pro výstupní řádky, které označí tok řízení programem.</span><span class="sxs-lookup"><span data-stu-id="caf3c-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="caf3c-176">Krok 4</span><span class="sxs-lookup"><span data-stu-id="caf3c-176">Step FOUR</span></span>  
 <span data-ttu-id="caf3c-177">Deklarovaný návratový typ `AccessTheWebAsync` je `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="caf3c-178">Proto když `AccessTheWebAsync` je pozastaven, vrátí úkol čísla do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="caf3c-179">Měli byste pochopit, že vrácená úloha není `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="caf3c-180">Vrácený úkol je nový úkol celého čísla, která představuje, co je ještě třeba provést v pozastavené metodě `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="caf3c-181">Úkol je příslib z `AccessTheWebAsync` k vytvoření celého čísla po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="caf3c-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="caf3c-182">Následující příkaz přiřadí tuto úlohu `getLengthTask` proměnné.</span><span class="sxs-lookup"><span data-stu-id="caf3c-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 <span data-ttu-id="caf3c-183">Stejně jako v `AccessTheWebAsync`, `startButton_Click` může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`) dokud je na úkol čekáno.</span><span class="sxs-lookup"><span data-stu-id="caf3c-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="caf3c-184">Následující řádky výstupu představují tuto práci.</span><span class="sxs-lookup"><span data-stu-id="caf3c-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="caf3c-185">V průběhu `startButton_Click` se pozastavuje, když `getLengthTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="caf3c-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="caf3c-186">Přiřazovací příkaz pozastaví `startButton_Click` dokud `AccessTheWebAsync` je dokončena.</span><span class="sxs-lookup"><span data-stu-id="caf3c-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="caf3c-187">Na následujícím obrázku šipky zobrazují tok řízení z výrazu await v metodě `AccessTheWebAsync` k přiřazení hodnoty ke `getLengthTask`, následované běžným zpracováním v `startButton_Click` dokud `getLengthTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="caf3c-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="caf3c-188">![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace čtyři")</span><span class="sxs-lookup"><span data-stu-id="caf3c-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="caf3c-189">Krok 5</span><span class="sxs-lookup"><span data-stu-id="caf3c-189">Step FIVE</span></span>  
 <span data-ttu-id="caf3c-190">Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování v `AccessTheWebAsync` je uvolněno z pozastavení a může pokračovat po příkazu await.</span><span class="sxs-lookup"><span data-stu-id="caf3c-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="caf3c-191">Následující řádky výstupu představují opětovné zpracování.</span><span class="sxs-lookup"><span data-stu-id="caf3c-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="caf3c-192">Operanda příkazu return, `urlContents.Length`, je uložen v úloze, která `AccessTheWebAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="caf3c-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="caf3c-193">Výraz await získá tuto hodnotu z `getLengthTask` v `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="caf3c-194">Následující obrázek znázorňuje přenos ovládání po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="caf3c-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="caf3c-195">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace pěti")</span><span class="sxs-lookup"><span data-stu-id="caf3c-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 `AccessTheWebAsync` <span data-ttu-id="caf3c-196">spuštění a dokončení, ovládací prvek vrátí na `startButton_Click`, který čeká na dokončení.</span><span class="sxs-lookup"><span data-stu-id="caf3c-196">runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="caf3c-197">Krok 6</span><span class="sxs-lookup"><span data-stu-id="caf3c-197">Step SIX</span></span>  
 <span data-ttu-id="caf3c-198">Když `AccessTheWebAsync` oznamuje, že je dokončeno, zpracování může pokračovat po příkazu await v `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="caf3c-199">Program ve skutečnosti nemá žádnou další akci nelze provést.</span><span class="sxs-lookup"><span data-stu-id="caf3c-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="caf3c-200">Následující řádky výstupu představují opětovné zpracování ve službě `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="caf3c-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="caf3c-201">Výraz await získá z `getLengthTask` celočíselnou hodnotu, která je operandou příkazu return v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="caf3c-202">Následující příkaz přiřadí tuto hodnotu `contentLength` proměnné.</span><span class="sxs-lookup"><span data-stu-id="caf3c-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="caf3c-203">Následující obrázek znázorňuje návrat ovládacího prvku z `AccessTheWebAsync` k `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="caf3c-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="caf3c-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="caf3c-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf3c-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caf3c-205">See also</span></span>

- [<span data-ttu-id="caf3c-206">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caf3c-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="caf3c-207">Asynchronní návratové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caf3c-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="caf3c-208">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caf3c-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="caf3c-209">Ukázka asynchronní metody: Řízení toku v asynchronních programech (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caf3c-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
