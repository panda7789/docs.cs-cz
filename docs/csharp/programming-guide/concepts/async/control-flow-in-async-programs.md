---
title: Řízení toku v asynchronních programech (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 7367b55a665a911a4d94f7b235cdc559a69854cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336619"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="2a8b6-102">Řízení toku v asynchronních programech (C#)</span><span class="sxs-lookup"><span data-stu-id="2a8b6-102">Control Flow in Async Programs (C#)</span></span>
<span data-ttu-id="2a8b6-103">Můžete napsat a udržovat asynchronní programy snadněji pomocí `async` a `await` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="2a8b6-104">Ale výsledky může ať vás překvapí Pokud nevíte, jak funguje vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="2a8b6-105">Toto téma trasování, které toku řízení prostřednictvím programu jednoduché asynchronní tak, aby zobrazovalo při řízení přechází z jedné metody na jiný a jaké informace se přenáší pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a8b6-106">Klíčová slova `async` a `await` byla zavedena v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-106">The `async` and `await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="2a8b6-107">Obecně platí, označit metody, které obsahují asynchronní kódu pomocí [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="2a8b6-108">Metoda, která je označena modifikátorem async, můžete použít [await (C#)](../../../../csharp/language-reference/keywords/await.md) operátor na dobu, kdy metodu pro čekání na dokončení procesu volané asynchronní.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="2a8b6-109">Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a8b6-109">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="2a8b6-110">Následující příklad používá asynchronní metody pro stažení obsahu webu, zadaný jako řetězec a zobrazíte délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="2a8b6-111">V příkladu obsahuje následující dvě metody.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="2a8b6-112">`startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="2a8b6-113">`AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="2a8b6-114">`AccessTheWebAsync` používá asynchronní <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, pro stažení obsahu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="2a8b6-115">Číslované zobrazení řádky se zobrazí v strategické body v rámci programu, které vám pomohou pochopit, jak program se spustí a vysvětlit, co se stane, že v každém bodu, který je označen.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="2a8b6-116">Zobrazení řádků, které jsou označeny "Jeden"pomocí "šest."</span><span class="sxs-lookup"><span data-stu-id="2a8b6-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="2a8b6-117">Popisky jasné, v pořadí, ve kterém program dosáhne tyto řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="2a8b6-118">Následující kód ukazuje přehled programu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-118">The following code shows an outline of the program.</span></span>  
  
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
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
    }  
  
    async Task<int> AccessTheWebAsync()  
    {  
        // TWO  
        HttpClient client = new HttpClient();  
        Task<string> getStringTask =  
            client.GetStringAsync("http://msdn.microsoft.com");  
  
        // THREE                   
        string urlContents = await getStringTask;  
  
        // FIVE  
        return urlContents.Length;  
    }  
}  
```  
  
 <span data-ttu-id="2a8b6-119">Každý místa s popiskem, "Jeden"pomocí "PŮL," zobrazí informace o aktuální stav programu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="2a8b6-120">Následující výsledek.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="2a8b6-121">Vytvoření programu</span><span class="sxs-lookup"><span data-stu-id="2a8b6-121">Set Up the Program</span></span>  
 <span data-ttu-id="2a8b6-122">Kód, který používá v tomto tématu můžete stáhnout z webu MSDN nebo je možné ho vytvořit sami.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a8b6-123">Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="2a8b6-124">Stažení programu</span><span class="sxs-lookup"><span data-stu-id="2a8b6-124">Download the Program</span></span>  
 <span data-ttu-id="2a8b6-125">Si můžete stáhnout aplikaci pro toto téma z [asynchronní ukázka: řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="2a8b6-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="2a8b6-126">Následující kroky otevřete a spusťte program.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="2a8b6-127">Rozbalte stažený soubor a pak spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2a8b6-128">Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="2a8b6-129">Přejděte do složky, která obsahuje rozbalené ukázkový kód, otevřete soubor řešení (.sln) a potom vyberte klávesy F5 sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="2a8b6-130">Vytvoření programu vlastními silami</span><span class="sxs-lookup"><span data-stu-id="2a8b6-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="2a8b6-131">Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="2a8b6-132">Pokud chcete spustit projekt, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="2a8b6-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="2a8b6-133">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2a8b6-134">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="2a8b6-135">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="2a8b6-136">V **nainstalovaných šablonách** podokně vyberte **Visual C#** a potom zvolte **aplikaci WPF** ze seznamu typy projektů.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-136">In the **Installed Templates** pane, choose **Visual C#**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="2a8b6-137">Zadejte `AsyncTracer` jako název projektu a klikněte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="2a8b6-138">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="2a8b6-139">V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="2a8b6-140">Pokud na kartě není zobrazena, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="2a8b6-141">V **XAML** zobrazení MainWindow.xaml, nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="2a8b6-142">Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhu** zobrazení MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="2a8b6-143">Přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="2a8b6-144">V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="2a8b6-145">V MainWindow.xaml.cs nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
  
            async Task<int> AccessTheWebAsync()  
            {  
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";  
  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";  
  
                // GetStringAsync returns a Task<string>.   
                Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
  
10. <span data-ttu-id="2a8b6-146">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="2a8b6-147">By se zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="2a8b6-148">Trasování programu</span><span class="sxs-lookup"><span data-stu-id="2a8b6-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="2a8b6-149">Kroky 1 a 2</span><span class="sxs-lookup"><span data-stu-id="2a8b6-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="2a8b6-150">Zobrazení první dva řádky trasování cesty k `startButton_Click` volání `AccessTheWebAsync`, a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="2a8b6-151">Následující obrázek znázorňuje volání z metoda.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="2a8b6-152">![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="2a8b6-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="2a8b6-153">Návratový typ i `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="2a8b6-154">Pro `AccessTheWebAsync`, TResult je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="2a8b6-155">Pro `GetStringAsync`, TResult je řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="2a8b6-156">Další informace o asynchronní metoda návratové typy najdete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="2a8b6-156">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="2a8b6-157">Asynchronní metody vrácení úkolů vrátí instance úlohy při řízení posune zpět k volajícímu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="2a8b6-158">Vrátí ovládací prvek z asynchronní metody jeho volajícího buď když `await` operátor se vyskytuje v volané metody nebo při ukončení zavolat metodu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="2a8b6-159">Zobrazení řádků, které jsou označeny "Tři"pomocí "PŮL" trasování tuto část procesu.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="2a8b6-160">Krok 3</span><span class="sxs-lookup"><span data-stu-id="2a8b6-160">Step THREE</span></span>  
 <span data-ttu-id="2a8b6-161">V `AccessTheWebAsync`, asynchronní metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> je volána pro stažení obsahu cílové webové stránky.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="2a8b6-162">Vrátí ovládací prvek z `client.GetStringAsync` k `AccessTheWebAsync` při `client.GetStringAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="2a8b6-163">`client.GetStringAsync` Metoda vrátí úlohu, řetězce, který je přiřazen k `getStringTask` proměnné v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="2a8b6-164">Následující řádek v programu příklad ukazuje volání `client.GetStringAsync` a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 <span data-ttu-id="2a8b6-165">Úlohy si můžete představit jako promise podle `client.GetStringAsync` k vytvoření nakonec konkrétní řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="2a8b6-166">Do té doby Pokud `AccessTheWebAsync` má práce uděláte, které nezávisí na přislíbeném řetězec z `client.GetStringAsync`, že můžete pokračovat v práci při `client.GetStringAsync` čeká.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="2a8b6-167">V příkladu představují následující řádky výstupu, které jsou označeny "3", tento krok provést nezávislou práci</span><span class="sxs-lookup"><span data-stu-id="2a8b6-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="2a8b6-168">Následující příkaz pozastaví průběh `AccessTheWebAsync` při `getStringTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 <span data-ttu-id="2a8b6-169">Následující obrázek zobrazuje tok řízení z `client.GetStringAsync` k přiřazení `getStringTask` a od vytvoření `getStringTask` do aplikace operátoru await.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>  
  
 <span data-ttu-id="2a8b6-170">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace tři")</span><span class="sxs-lookup"><span data-stu-id="2a8b6-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="2a8b6-171">Výraz await pozastaví `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="2a8b6-172">Do té doby, vrátí ovládací prvek do volajícího `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a8b6-173">Obvykle můžete await volání asynchronní metodu okamžitě.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="2a8b6-174">Například následující přiřazení může nahradit předchozí kód, který vytvoří a pak čeká `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="2a8b6-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span></span>  
>   
>  <span data-ttu-id="2a8b6-175">V tomto tématu platí operátoru await pro umístění výstupní řádky, které označit toku řízení prostřednictvím programu později.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="2a8b6-176">Krok 4</span><span class="sxs-lookup"><span data-stu-id="2a8b6-176">Step FOUR</span></span>  
 <span data-ttu-id="2a8b6-177">Deklarovaný návratový typ `AccessTheWebAsync` je `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="2a8b6-178">Proto když `AccessTheWebAsync` je pozastavený, vrátí úlohu celého `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="2a8b6-179">Byste měli vědět, že vrácený úloh není `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="2a8b6-180">Vrácená úloha je novou úlohu celé číslo, které představuje, co je ještě provést v metodě pozastavenou `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="2a8b6-181">Tato úloha je promise z `AccessTheWebAsync` k vytvoření celé po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="2a8b6-182">Následující příkaz přiřadí této úlohy můžete `getLengthTask` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 <span data-ttu-id="2a8b6-183">Jako v `AccessTheWebAsync`, `startButton_Click` můžete pokračovat v práci, kterou nezávisí na výsledky asynchronní úlohy (`getLengthTask`) dokud úloha je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="2a8b6-184">Následující výstup řádky představují svou práci.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="2a8b6-185">V průběhu `startButton_Click` je pozastaven, když `getLengthTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="2a8b6-186">Následující příkaz přiřazení pozastaví `startButton_Click` dokud `AccessTheWebAsync` dokončení.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="2a8b6-187">Na následujícím obrázku, šipky zobrazují toku řízení z výrazu await v `AccessTheWebAsync` přiřazení hodnoty k `getLengthTask`, za nímž následují normálním zpracování v `startButton_Click` dokud `getLengthTask` je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="2a8b6-188">![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace ČTYŘMI")</span><span class="sxs-lookup"><span data-stu-id="2a8b6-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="2a8b6-189">Krok 5</span><span class="sxs-lookup"><span data-stu-id="2a8b6-189">Step FIVE</span></span>  
 <span data-ttu-id="2a8b6-190">Když `client.GetStringAsync` signalizuje, že se jedná o dokončení zpracování v `AccessTheWebAsync` vydání z pozastavení a můžete pokračovat přes příkaz await.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="2a8b6-191">Následující řádky výstupu představují obnovení zpracování.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="2a8b6-192">Operand příkaz return `urlContents.Length`, je uložen v úloze, `AccessTheWebAsync` vrátí.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="2a8b6-193">Výraz await načte tuto hodnotu z `getLengthTask` v `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="2a8b6-194">Následující obrázek ukazuje ovládání po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="2a8b6-195">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace PĚT")</span><span class="sxs-lookup"><span data-stu-id="2a8b6-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="2a8b6-196">`AccessTheWebAsync` používá pro dokončení a řízení vrátí do `startButton_Click`, která čeká na dokončení.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="2a8b6-197">Krok 6</span><span class="sxs-lookup"><span data-stu-id="2a8b6-197">Step SIX</span></span>  
 <span data-ttu-id="2a8b6-198">Když `AccessTheWebAsync` signály, které je dokončená, zpracování, můžete pokračovat přes příkaz await v `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="2a8b6-199">Ve skutečnosti program nijak nesouvisí Další.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="2a8b6-200">Následující řádky výstupu představují obnovení zpracování v `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="2a8b6-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="2a8b6-201">Výraz await načte z `getLengthTask` celočíselná hodnota, která je operand příkaz return v `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="2a8b6-202">Tuto hodnotu přiřadí do následujícího příkazu `contentLength` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="2a8b6-203">Následující obrázek ukazuje návratový řízení z `AccessTheWebAsync` k `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="2a8b6-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="2a8b6-204">![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace šest")</span><span class="sxs-lookup"><span data-stu-id="2a8b6-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a8b6-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a8b6-205">See Also</span></span>  
 [<span data-ttu-id="2a8b6-206">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="2a8b6-206">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="2a8b6-207">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="2a8b6-207">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="2a8b6-208">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="2a8b6-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="2a8b6-209">Ukázka asynchronního: Řízení toku v asynchronních programech (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a8b6-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
