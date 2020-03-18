---
title: Tok řízení v asynchronních programech (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204439"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="3d707-102">Řízení toku v asynchronních programech (C#)</span><span class="sxs-lookup"><span data-stu-id="3d707-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="3d707-103">Asynchronní programy můžete snadněji psát a `async` udržovat `await` pomocí klíčových slov a.</span><span class="sxs-lookup"><span data-stu-id="3d707-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="3d707-104">Výsledky vás však mohou překvapit, pokud nerozumíte tomu, jak váš program funguje.</span><span class="sxs-lookup"><span data-stu-id="3d707-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="3d707-105">Toto téma sleduje tok řízení prostřednictvím jednoduchého asynchronního programu, který vám ukáže, kdy se ovládací prvek přesune z jedné metody do druhé a jaké informace se přenesou pokaždé.</span><span class="sxs-lookup"><span data-stu-id="3d707-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="3d707-106">Obecně lze označit metody, které obsahují asynchronní kód s [asynchronní (C#)](../../../language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="3d707-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="3d707-107">V metodě, která je označena asynchronním modifikátorem, můžete použít operátor [await (C#)](../../../language-reference/operators/await.md) k určení, kde se metoda pozastaví a čeká se na dokončení takzvaného asynchronního procesu.</span><span class="sxs-lookup"><span data-stu-id="3d707-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/operators/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="3d707-108">Další informace naleznete [v tématu Asynchronní programování s asynchronní a await (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="3d707-108">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="3d707-109">Následující příklad používá asynchronní metody ke stažení obsahu zadaného webu jako řetězec a zobrazení délky řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d707-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="3d707-110">Příklad obsahuje následující dvě metody.</span><span class="sxs-lookup"><span data-stu-id="3d707-110">The example contains the following two methods.</span></span>

- <span data-ttu-id="3d707-111">`startButton_Click`, který `AccessTheWebAsync` volá a zobrazuje výsledek.</span><span class="sxs-lookup"><span data-stu-id="3d707-111">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="3d707-112">`AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d707-112">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="3d707-113">`AccessTheWebAsync`používá asynchronní <xref:System.Net.Http.HttpClient> metodu <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, ke stažení obsahu.</span><span class="sxs-lookup"><span data-stu-id="3d707-113">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="3d707-114">Číslované řádky zobrazení se zobrazují ve strategických bodech v celém programu, aby vám pomohly pochopit, jak program běží, a vysvětlit, co se děje v každém označeném bodě.</span><span class="sxs-lookup"><span data-stu-id="3d707-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="3d707-115">Řádky zobrazení jsou označeny jako "ONE" až "SIX".</span><span class="sxs-lookup"><span data-stu-id="3d707-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="3d707-116">Popisky představují pořadí, ve kterém program dosáhne těchto řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="3d707-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="3d707-117">Následující kód ukazuje osnovu programu.</span><span class="sxs-lookup"><span data-stu-id="3d707-117">The following code shows an outline of the program.</span></span>

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

<span data-ttu-id="3d707-118">Každé z označených umístění,"ONE" až "SIX", zobrazuje informace o aktuálním stavu programu.</span><span class="sxs-lookup"><span data-stu-id="3d707-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="3d707-119">Vytvoří se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3d707-119">The following output is produced:</span></span>

```output
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

## <a name="set-up-the-program"></a><span data-ttu-id="3d707-120">Nastavení programu</span><span class="sxs-lookup"><span data-stu-id="3d707-120">Set up the program</span></span>

<span data-ttu-id="3d707-121">Můžete si stáhnout kód, který toto téma používá z MSDN, nebo si můžete vytvořit sami.</span><span class="sxs-lookup"><span data-stu-id="3d707-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="3d707-122">Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="3d707-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="3d707-123">Stáhněte si program</span><span class="sxs-lookup"><span data-stu-id="3d707-123">Download the program</span></span>

<span data-ttu-id="3d707-124">Aplikaci pro toto téma si můžete stáhnout z aplikace [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="3d707-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="3d707-125">Otevřete následující kroky a spusťte program.</span><span class="sxs-lookup"><span data-stu-id="3d707-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="3d707-126">Rozbalte stažený soubor a spusťte visual studio.</span><span class="sxs-lookup"><span data-stu-id="3d707-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="3d707-127">Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="3d707-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="3d707-128">Přejděte do složky, která obsahuje rozbalený ukázkový kód, otevřete soubor řešení (.sln) a pak zvolte klávesu **F5** pro sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="3d707-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="3d707-129">Vytvořte si program sami</span><span class="sxs-lookup"><span data-stu-id="3d707-129">Create the program Yourself</span></span>

<span data-ttu-id="3d707-130">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="3d707-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="3d707-131">Chcete-li projekt spustit, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="3d707-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="3d707-132">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d707-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="3d707-133">Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="3d707-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="3d707-134">Otevře se dialogové okno **Nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="3d707-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="3d707-135">Zvolte **nainstalovaný** > **Visual C#** > Windows**Desktop** kategorie a pak zvolte **WPF App** ze seznamu šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="3d707-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="3d707-136">Zadejte `AsyncTracer` jako název projektu a pak zvolte tlačítko **OK.**</span><span class="sxs-lookup"><span data-stu-id="3d707-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="3d707-137">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="3d707-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="3d707-138">V Editoru kódu Visual Studia zvolte kartu **MainWindow.xaml.**</span><span class="sxs-lookup"><span data-stu-id="3d707-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="3d707-139">Pokud karta není viditelná, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="3d707-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="3d707-140">V zobrazení **XAML** MainWindow.xaml nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="3d707-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="3d707-141">Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhovém** zobrazení MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="3d707-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="3d707-142">Přidejte odkaz <xref:System.Net.Http>pro .</span><span class="sxs-lookup"><span data-stu-id="3d707-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="3d707-143">V **Průzkumníku řešení**otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="3d707-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="3d707-144">V MainWindow.xaml.cs nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="3d707-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

10. <span data-ttu-id="3d707-145">Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="3d707-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="3d707-146">Zobrazí se výstup:</span><span class="sxs-lookup"><span data-stu-id="3d707-146">The following output appears:</span></span>

    ```output
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

## <a name="trace-the-program"></a><span data-ttu-id="3d707-147">Sledování programu</span><span class="sxs-lookup"><span data-stu-id="3d707-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="3d707-148">Kroky 1 a 2</span><span class="sxs-lookup"><span data-stu-id="3d707-148">Steps ONE and TWO</span></span>

<span data-ttu-id="3d707-149">První dvě řádky zobrazení trasují cestu jako `startButton_Click` volání `AccessTheWebAsync` <xref:System.Net.Http.HttpClient> a <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> `AccessTheWebAsync` volají asynchronní metodu .</span><span class="sxs-lookup"><span data-stu-id="3d707-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="3d707-150">Následující obrázek popisuje volání z metody na metodu.</span><span class="sxs-lookup"><span data-stu-id="3d707-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="3d707-151">![Kroky 1 a 2](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="3d707-151">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="3d707-152">Návratový typ `AccessTheWebAsync` obou `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601>a je .</span><span class="sxs-lookup"><span data-stu-id="3d707-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="3d707-153">Pro `AccessTheWebAsync`, TResult je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="3d707-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="3d707-154">Pro `GetStringAsync`, TResult je řetězec.</span><span class="sxs-lookup"><span data-stu-id="3d707-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="3d707-155">Další informace o návratových typech asynchronní metody naleznete [v tématu Asynchronní návratové typy (C#).](./async-return-types.md)</span><span class="sxs-lookup"><span data-stu-id="3d707-155">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="3d707-156">Asynchronní metoda vracející úlohu vrátí instanci úlohy, když se ovládací prvek přesune zpět na volajícího.</span><span class="sxs-lookup"><span data-stu-id="3d707-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="3d707-157">Ovládací prvek vrátí z asynchronní metody `await` jeho volajícímu buď při operátoru je zjištěna v volané metody nebo při ukončení volané metody.</span><span class="sxs-lookup"><span data-stu-id="3d707-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="3d707-158">Řádky zobrazení, které jsou označeny "TŘI" až "ŠEST" sledovat tuto část procesu.</span><span class="sxs-lookup"><span data-stu-id="3d707-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="3d707-159">Krok 3</span><span class="sxs-lookup"><span data-stu-id="3d707-159">Step THREE</span></span>

<span data-ttu-id="3d707-160">V `AccessTheWebAsync`aplikaci je volána asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> ke stažení obsahu cílové webové stránky.</span><span class="sxs-lookup"><span data-stu-id="3d707-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="3d707-161">Ovládací prvek `client.GetStringAsync` `AccessTheWebAsync` se `client.GetStringAsync` vrátí z při vrácení.</span><span class="sxs-lookup"><span data-stu-id="3d707-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="3d707-162">Metoda `client.GetStringAsync` vrátí úlohu řetězce, který je `getStringTask` přiřazen `AccessTheWebAsync`proměnné v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="3d707-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="3d707-163">Následující řádek v ukázkovém programu `client.GetStringAsync` zobrazuje volání a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3d707-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="3d707-164">Úkol si můžete usuzovat `client.GetStringAsync` jako slib tím, že nakonec vytvoříte skutečný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3d707-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="3d707-165">Do té doby, `AccessTheWebAsync` pokud má práci na tom, že `client.GetStringAsync`nezávisí na slíbený řetězec od , že práce může pokračovat při `client.GetStringAsync` čekání.</span><span class="sxs-lookup"><span data-stu-id="3d707-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="3d707-166">V příkladu následující řádky výstupu, které jsou označeny jako "TŘI", představují možnost dělat nezávislou práci</span><span class="sxs-lookup"><span data-stu-id="3d707-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="3d707-167">Následující příkaz pozastaví `AccessTheWebAsync` průběh `getStringTask` v případě, že je očekáván.</span><span class="sxs-lookup"><span data-stu-id="3d707-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="3d707-168">Následující obrázek znázorňuje `client.GetStringAsync` tok řízení `getStringTask` z přiřazení `getStringTask` do a z vytvoření do aplikace operátoru await.</span><span class="sxs-lookup"><span data-stu-id="3d707-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="3d707-169">![Třetí krok](./media/asynctrace-three.png "AsyncTrace-tři")</span><span class="sxs-lookup"><span data-stu-id="3d707-169">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="3d707-170">Await výraz pozastaví, `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="3d707-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="3d707-171">Do té doby ovládací prvek vrátí `AccessTheWebAsync` `startButton_Click`volajícímu , .</span><span class="sxs-lookup"><span data-stu-id="3d707-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="3d707-172">Obvykle čekáte na volání asynchronní metody okamžitě.</span><span class="sxs-lookup"><span data-stu-id="3d707-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="3d707-173">Například následující přiřazení může nahradit předchozí kód, který `getStringTask`vytvoří a pak čeká :`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="3d707-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="3d707-174">V tomto tématu await operátor je použita později přizpůsobit výstupní řádky, které označují tok řízení prostřednictvím programu.</span><span class="sxs-lookup"><span data-stu-id="3d707-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="3d707-175">Krok 4</span><span class="sxs-lookup"><span data-stu-id="3d707-175">Step FOUR</span></span>

<span data-ttu-id="3d707-176">Deklarovaný `AccessTheWebAsync` návratový typ je `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="3d707-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="3d707-177">Proto při `AccessTheWebAsync` pozastavení vrátí úkol celé číslo na `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="3d707-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="3d707-178">Měli byste pochopit, že vrácená úloha není `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="3d707-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="3d707-179">Vrácený úkol je nový úkol celé číslo, který představuje co zbývá `AccessTheWebAsync`udělat v pozastavené metodě .</span><span class="sxs-lookup"><span data-stu-id="3d707-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="3d707-180">Úkol je příslibem `AccessTheWebAsync` z vytvoření celého čísla po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="3d707-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="3d707-181">Následující příkaz přiřadí tento `getLengthTask` úkol proměnné.</span><span class="sxs-lookup"><span data-stu-id="3d707-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="3d707-182">Stejně `AccessTheWebAsync` `startButton_Click` jako v , může pokračovat v práci, která nezávisí`getLengthTask`na výsledcích asynchronní úlohy ( ), dokud nebude úkol očekáván.</span><span class="sxs-lookup"><span data-stu-id="3d707-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="3d707-183">Následující výstupní řádky představují tuto práci.</span><span class="sxs-lookup"><span data-stu-id="3d707-183">The following output lines represent that work.</span></span>

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="3d707-184">Průběh `startButton_Click` v programu `getLengthTask` je pozastaven, když je očekáván.</span><span class="sxs-lookup"><span data-stu-id="3d707-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="3d707-185">Následující příkaz přiřazení `startButton_Click` pozastaví, dokud není `AccessTheWebAsync` dokončena.</span><span class="sxs-lookup"><span data-stu-id="3d707-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="3d707-186">Na následujícím obrázku šipky znázorňují tok `AccessTheWebAsync` ovládacího prvku z `getLengthTask`výrazu await `startButton_Click` do `getLengthTask` přiřazení hodnoty do aplikace , následované normálním zpracováním v aplikaci, dokud není očekáváno.</span><span class="sxs-lookup"><span data-stu-id="3d707-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="3d707-187">![Krok 4](./media/asynctrace-four.png "AsyncTrace-čtyři")</span><span class="sxs-lookup"><span data-stu-id="3d707-187">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="3d707-188">Krok 5</span><span class="sxs-lookup"><span data-stu-id="3d707-188">Step FIVE</span></span>

<span data-ttu-id="3d707-189">Když `client.GetStringAsync` signalizuje, že je `AccessTheWebAsync` kompletní, zpracování v je uvolněna z pozastavení a může pokračovat v minulosti await prohlášení.</span><span class="sxs-lookup"><span data-stu-id="3d707-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="3d707-190">Následující řádky výstupu představují obnovení zpracování.</span><span class="sxs-lookup"><span data-stu-id="3d707-190">The following lines of output represent the resumption of processing.</span></span>

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="3d707-191">Operand příkazu return `urlContents.Length`, je uložen v `AccessTheWebAsync` úloze, která vrátí.</span><span class="sxs-lookup"><span data-stu-id="3d707-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="3d707-192">Await výraz načte tuto `getLengthTask` `startButton_Click`hodnotu z v .</span><span class="sxs-lookup"><span data-stu-id="3d707-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="3d707-193">Následující obrázek znázorňuje `client.GetStringAsync` přenos `getStringTask`ovládacího prvku po (a ) jsou kompletní.</span><span class="sxs-lookup"><span data-stu-id="3d707-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="3d707-194">![Krok 5](./media/asynctrace-five.png "AsyncTrace-pět")</span><span class="sxs-lookup"><span data-stu-id="3d707-194">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="3d707-195">`AccessTheWebAsync`spustí do dokončení a `startButton_Click`řízení se vrátí do , který čeká na dokončení.</span><span class="sxs-lookup"><span data-stu-id="3d707-195">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="3d707-196">Krok 6</span><span class="sxs-lookup"><span data-stu-id="3d707-196">Step SIX</span></span>

<span data-ttu-id="3d707-197">Když `AccessTheWebAsync` signalizuje, že je kompletní, zpracování může `startButton_Async`pokračovat za příkaz učekání v .</span><span class="sxs-lookup"><span data-stu-id="3d707-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="3d707-198">Ve skutečnosti, program nemá nic víc dělat.</span><span class="sxs-lookup"><span data-stu-id="3d707-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="3d707-199">Následující řádky výstupu představují obnovení zpracování `startButton_Async`v :</span><span class="sxs-lookup"><span data-stu-id="3d707-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="3d707-200">Await výraz načte `getLengthTask` z celé hodnoty, která je operand příkazu return v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="3d707-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="3d707-201">Následující příkaz přiřadí tuto `contentLength` hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="3d707-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="3d707-202">Následující obrázek znázorňuje `AccessTheWebAsync` návrat `startButton_Click`ovládacího prvku z do .</span><span class="sxs-lookup"><span data-stu-id="3d707-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="3d707-203">![Krok 6](./media/asynctrace-six.png "AsyncTrace-ŠEST")</span><span class="sxs-lookup"><span data-stu-id="3d707-203">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="3d707-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d707-204">See also</span></span>

- [<span data-ttu-id="3d707-205">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="3d707-205">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="3d707-206">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="3d707-206">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="3d707-207">Návod: Přístup k webu pomocí asynchronní a čeká (C#)</span><span class="sxs-lookup"><span data-stu-id="3d707-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="3d707-208">Ukázka asynchronního řízení: Tok řízení v asynchronních programech (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d707-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
