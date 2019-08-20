---
title: Řízení toku v asynchronních programechC#()
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 8adf4bcf193d9fa8d7335996539933ce71282bac
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595845"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="53a57-102">Řízení toku v asynchronních programechC#()</span><span class="sxs-lookup"><span data-stu-id="53a57-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="53a57-103">Pomocí `async` klíčových slov a `await` můžete snadno psát a spravovat asynchronní programy.</span><span class="sxs-lookup"><span data-stu-id="53a57-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="53a57-104">Pokud ale nerozumíte tomu, jak program funguje, může se stát, že se výsledky neočekávaně neznají.</span><span class="sxs-lookup"><span data-stu-id="53a57-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="53a57-105">Toto téma sleduje tok řízení pomocí jednoduchého asynchronního programu, který vám ukáže, kdy se ovládací prvek přesouvá z jedné metody na jinou a jaké informace se přenášejí pokaždé.</span><span class="sxs-lookup"><span data-stu-id="53a57-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="53a57-106">Obecně je třeba označit metody, které obsahují asynchronní kód, pomocí modifikátoru [Async (C#)](../../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="53a57-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="53a57-107">V metodě, která je označena modifikátorem Async, můžete použít operátor [await (C#)](../../../language-reference/keywords/await.md) k určení, kde metoda pozastaví čekání na dokončení volaného asynchronního procesu.</span><span class="sxs-lookup"><span data-stu-id="53a57-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="53a57-108">Další informace naleznete v tématu [asynchronní programování s Async a await (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="53a57-108">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="53a57-109">Následující příklad používá asynchronní metody ke stažení obsahu zadaného webu jako řetězce a k zobrazení délky řetězce.</span><span class="sxs-lookup"><span data-stu-id="53a57-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="53a57-110">Příklad obsahuje následující dvě metody.</span><span class="sxs-lookup"><span data-stu-id="53a57-110">The example contains the following two methods.</span></span>

- <span data-ttu-id="53a57-111">`startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="53a57-111">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="53a57-112">`AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="53a57-112">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="53a57-113">`AccessTheWebAsync`k stažení obsahu <xref:System.Net.Http.HttpClient> používá asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>metodu.</span><span class="sxs-lookup"><span data-stu-id="53a57-113">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="53a57-114">Číslované zobrazené řádky se zobrazí ve strategických bodech v rámci programu, které vám pomůžou pochopit, jak se program spouští, a vysvětlit, co se stane v každém označeném místě.</span><span class="sxs-lookup"><span data-stu-id="53a57-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="53a57-115">Zobrazované řádky jsou označeny "ONE" až "šest".</span><span class="sxs-lookup"><span data-stu-id="53a57-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="53a57-116">Popisky znázorňují pořadí, ve kterém program dosáhne těchto řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="53a57-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="53a57-117">Následující kód ukazuje osnovu programu.</span><span class="sxs-lookup"><span data-stu-id="53a57-117">The following code shows an outline of the program.</span></span>

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

<span data-ttu-id="53a57-118">Každé z označených umístění, "jedna" až "šest", zobrazí informace o aktuálním stavu programu.</span><span class="sxs-lookup"><span data-stu-id="53a57-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="53a57-119">Vytvoří se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a57-119">The following output is produced:</span></span>

```text
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

## <a name="set-up-the-program"></a><span data-ttu-id="53a57-120">Nastavení programu</span><span class="sxs-lookup"><span data-stu-id="53a57-120">Set up the program</span></span>

<span data-ttu-id="53a57-121">Můžete si stáhnout kód, který toto téma používá z MSDN, nebo si ho můžete vytvořit sami.</span><span class="sxs-lookup"><span data-stu-id="53a57-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="53a57-122">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="53a57-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="53a57-123">Stažení programu</span><span class="sxs-lookup"><span data-stu-id="53a57-123">Download the program</span></span>

<span data-ttu-id="53a57-124">Aplikaci pro toto téma si můžete stáhnout z [Async Sample: Řízení toku v asynchronních](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)programech.</span><span class="sxs-lookup"><span data-stu-id="53a57-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="53a57-125">Následující kroky otevřete a spusťte v programu.</span><span class="sxs-lookup"><span data-stu-id="53a57-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="53a57-126">Rozbalte stažený soubor a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53a57-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="53a57-127">Na panelu nabídek vyberte **soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="53a57-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="53a57-128">Přejděte do složky, která obsahuje vzorový kód Get, otevřete soubor řešení (. sln) a pak zvolte klávesu **F5** pro sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="53a57-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="53a57-129">Vytvoření programu sami</span><span class="sxs-lookup"><span data-stu-id="53a57-129">Create the program Yourself</span></span>

<span data-ttu-id="53a57-130">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="53a57-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="53a57-131">Chcete-li spustit projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="53a57-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="53a57-132">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53a57-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="53a57-133">V panelu nabídky zvolte **souboru** > **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="53a57-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="53a57-134">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="53a57-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="53a57-135">Zvolte kategorii **nainstalovaného** > **vizuálu C#**   >  **desktopu Windows** a pak v seznamu šablon projektů vyberte možnost **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="53a57-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="53a57-136">Jako `AsyncTracer` název projektu zadejte a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="53a57-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="53a57-137">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="53a57-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="53a57-138">V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="53a57-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="53a57-139">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="53a57-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="53a57-140">V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="53a57-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="53a57-141">Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="53a57-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="53a57-142">Přidejte odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="53a57-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="53a57-143">V **Průzkumník řešení**otevřete místní nabídku pro MainWindow.XAML.cs a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="53a57-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="53a57-144">V MainWindow.xaml.cs nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="53a57-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Data;
    using System.Windows.Documents;
    using System.Windows.Input;
    using System.Windows.Media;
    using System.Windows.Media.Imaging;
    using System.Windows.Navigation;
    using System.Windows.Shapes;

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. <span data-ttu-id="53a57-145">Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="53a57-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="53a57-146">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53a57-146">The following output appears:</span></span>

    ```text
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

## <a name="trace-the-program"></a><span data-ttu-id="53a57-147">Trasování programu</span><span class="sxs-lookup"><span data-stu-id="53a57-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="53a57-148">Kroky 1 a 2</span><span class="sxs-lookup"><span data-stu-id="53a57-148">Steps ONE and TWO</span></span>

<span data-ttu-id="53a57-149">První dva zobrazené řádky `startButton_Click` sledují cestu jako volání `AccessTheWebAsync`a `AccessTheWebAsync` volají asynchronní <xref:System.Net.Http.HttpClient> metodu <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="53a57-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="53a57-150">Následující obrázek znázorňuje volání metody z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="53a57-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="53a57-151">![Kroky 1 a 2](./media/asynctrace-onetwo.png "AsyncTrace – ONETWO")</span><span class="sxs-lookup"><span data-stu-id="53a57-151">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="53a57-152">Návratový typ obojí `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="53a57-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="53a57-153">Pro `AccessTheWebAsync`TResult je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="53a57-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="53a57-154">V `GetStringAsync`případě je TResult řetězec.</span><span class="sxs-lookup"><span data-stu-id="53a57-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="53a57-155">Další informace o návratových typech asynchronní metody naleznete v tématu [Async Return TypesC#()](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="53a57-155">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="53a57-156">Asynchronní metoda vracející úlohu vrátí instanci úlohy, pokud se ovládací prvek posune zpět na volajícího.</span><span class="sxs-lookup"><span data-stu-id="53a57-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="53a57-157">Řízení se vrátí z asynchronní metody volajícímu buď v případě `await` , že je v volané metodě zjištěn operátor nebo když volaná metoda končí.</span><span class="sxs-lookup"><span data-stu-id="53a57-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="53a57-158">V této části procesu jsou zobrazené řádky s označením "tři" až "šest".</span><span class="sxs-lookup"><span data-stu-id="53a57-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="53a57-159">Krok 3</span><span class="sxs-lookup"><span data-stu-id="53a57-159">Step THREE</span></span>

<span data-ttu-id="53a57-160">V `AccessTheWebAsync`systému je volána asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> metoda pro stažení obsahu cílové webové stránky.</span><span class="sxs-lookup"><span data-stu-id="53a57-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="53a57-161">Ovládací prvek vrátí `client.GetStringAsync` z `AccessTheWebAsync` na `client.GetStringAsync` hodnotu when.</span><span class="sxs-lookup"><span data-stu-id="53a57-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="53a57-162">Metoda vrátí úlohu řetězce, který je přiřazen `getStringTask` proměnné v `AccessTheWebAsync`. `client.GetStringAsync`</span><span class="sxs-lookup"><span data-stu-id="53a57-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="53a57-163">Následující řádek v ukázkovém programu zobrazuje volání `client.GetStringAsync` a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="53a57-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="53a57-164">Úkol si můžete představit jako příslib tím, že `client.GetStringAsync` budete chtít vytvořit skutečný řetězec nakonec.</span><span class="sxs-lookup"><span data-stu-id="53a57-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="53a57-165">Pokud `AccessTheWebAsync` v tuto chvíli funguje práce, která nezávisí na přislíbeném řetězci z `client.GetStringAsync`, může tato práce pokračovat během `client.GetStringAsync` čekání.</span><span class="sxs-lookup"><span data-stu-id="53a57-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="53a57-166">V příkladu představují následující řádky výstupu, které jsou označeny "tři", možnost provést nezávislou práci.</span><span class="sxs-lookup"><span data-stu-id="53a57-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="53a57-167">Následující příkaz pozastaví průběh v `AccessTheWebAsync` případě, kdy `getStringTask` je očekáván.</span><span class="sxs-lookup"><span data-stu-id="53a57-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="53a57-168">Následující obrázek ukazuje tok řízení od `client.GetStringAsync` k přiřazení do `getStringTask` `getStringTask` a od vytvoření k aplikaci operátoru await.</span><span class="sxs-lookup"><span data-stu-id="53a57-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="53a57-169">![Krok 3](./media/asynctrace-three.png "AsyncTrace – tři")</span><span class="sxs-lookup"><span data-stu-id="53a57-169">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="53a57-170">Výraz Await se pozastaví `AccessTheWebAsync` , `client.GetStringAsync` dokud se nevrátí.</span><span class="sxs-lookup"><span data-stu-id="53a57-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="53a57-171">Mezitím se ovládací prvek vrátí volajícímu `AccessTheWebAsync`,. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="53a57-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="53a57-172">Obvykle očekáváte okamžité volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="53a57-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="53a57-173">Například následující přiřazení může nahradit předchozí kód, který vytvoří a následně očekává `getStringTask`:`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="53a57-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="53a57-174">V tomto tématu se použije operátor await později, aby se vešel na výstupní řádky, které označují tok řízení přes program.</span><span class="sxs-lookup"><span data-stu-id="53a57-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="53a57-175">Krok 4</span><span class="sxs-lookup"><span data-stu-id="53a57-175">Step FOUR</span></span>

<span data-ttu-id="53a57-176">Deklarovaný návratový typ `AccessTheWebAsync` je `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="53a57-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="53a57-177">Proto když `AccessTheWebAsync` je pozastaveno, vrátí úlohu typu Integer na `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="53a57-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="53a57-178">Měli byste pochopit, že vrácená úloha není `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="53a57-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="53a57-179">Vrácený úkol je nový úkol na celé číslo, který představuje to, co je potřeba udělat v pozastavené `AccessTheWebAsync`metodě.</span><span class="sxs-lookup"><span data-stu-id="53a57-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="53a57-180">Úkol je příslib z `AccessTheWebAsync` a vytvoří celé číslo po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="53a57-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="53a57-181">Následující příkaz přiřadí tuto úlohu k `getLengthTask` proměnné.</span><span class="sxs-lookup"><span data-stu-id="53a57-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="53a57-182">Stejně jako `AccessTheWebAsync`v `startButton_Click` aplikaci může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`), dokud není očekávána úloha.</span><span class="sxs-lookup"><span data-stu-id="53a57-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="53a57-183">Následující výstupní řádky označují, že fungují.</span><span class="sxs-lookup"><span data-stu-id="53a57-183">The following output lines represent that work.</span></span>

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="53a57-184">Průběh je pozastaven, když `getLengthTask` je očekáváno. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="53a57-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="53a57-185">Následující příkaz přiřazení se pozastaví `startButton_Click` , `AccessTheWebAsync` dokud není dokončen.</span><span class="sxs-lookup"><span data-stu-id="53a57-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="53a57-186">Na následujícím obrázku šipky ukazují tok řízení z výrazu await `AccessTheWebAsync` v pro přiřazení hodnoty k `getLengthTask`, následované normálním zpracováním v `startButton_Click` `getLengthTask` případě, že je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="53a57-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="53a57-187">![Krok 4](./media/asynctrace-four.png "AsyncTrace – čtyři")</span><span class="sxs-lookup"><span data-stu-id="53a57-187">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="53a57-188">Krok 5</span><span class="sxs-lookup"><span data-stu-id="53a57-188">Step FIVE</span></span>

<span data-ttu-id="53a57-189">Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování `AccessTheWebAsync` v nástroji je uvolněno z pozastavení a může pokračovat za příkazem await.</span><span class="sxs-lookup"><span data-stu-id="53a57-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="53a57-190">Následující řádky výstupu reprezentují pokračování zpracování.</span><span class="sxs-lookup"><span data-stu-id="53a57-190">The following lines of output represent the resumption of processing.</span></span>

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="53a57-191">Operand příkazu return, `urlContents.Length`, je uložen v úloze, která `AccessTheWebAsync` vrací.</span><span class="sxs-lookup"><span data-stu-id="53a57-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="53a57-192">Výraz Await načte tuto hodnotu z `getLengthTask` v. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="53a57-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="53a57-193">Následující obrázek znázorňuje přenos řízení po `client.GetStringAsync` dokončení (a `getStringTask`).</span><span class="sxs-lookup"><span data-stu-id="53a57-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="53a57-194">![Krok 5](./media/asynctrace-five.png "AsyncTrace – pět")</span><span class="sxs-lookup"><span data-stu-id="53a57-194">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="53a57-195">`AccessTheWebAsync`Spustí se k dokončení a řízení se vrátí `startButton_Click`do, což čeká na dokončení.</span><span class="sxs-lookup"><span data-stu-id="53a57-195">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="53a57-196">Krok 6</span><span class="sxs-lookup"><span data-stu-id="53a57-196">Step SIX</span></span>

<span data-ttu-id="53a57-197">Když `AccessTheWebAsync` signalizuje, že je dokončeno, zpracování může pokračovat za příkazem await v `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="53a57-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="53a57-198">Ve skutečnosti program nemá nic dalšího.</span><span class="sxs-lookup"><span data-stu-id="53a57-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="53a57-199">Následující řádky výstupu reprezentují pokračování zpracování v `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="53a57-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="53a57-200">Výraz Await se načte z `getLengthTask` celočíselné hodnoty, která je operandem příkazu return v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="53a57-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="53a57-201">Následující příkaz přiřadí tuto hodnotu k `contentLength` proměnné.</span><span class="sxs-lookup"><span data-stu-id="53a57-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="53a57-202">Následující obrázek ukazuje vrácení ovládacího prvku z `AccessTheWebAsync` na. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="53a57-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="53a57-203">![Krok 6](./media/asynctrace-six.png "AsyncTrace – šest")</span><span class="sxs-lookup"><span data-stu-id="53a57-203">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="53a57-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53a57-204">See also</span></span>

- [<span data-ttu-id="53a57-205">Asynchronní programování s modifikátorem Async aC#operátoru Await ()</span><span class="sxs-lookup"><span data-stu-id="53a57-205">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="53a57-206">Asynchronní návratové typyC#()</span><span class="sxs-lookup"><span data-stu-id="53a57-206">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="53a57-207">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="53a57-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="53a57-208">Asynchronní Ukázka: Řízení toku v asynchronních programechC# (a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53a57-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
