---
title: Zrušit asynchronní úkoly po časovém období (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204345"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="9d11f-102">Zrušení asynchronních úloh po určité době (C#)</span><span class="sxs-lookup"><span data-stu-id="9d11f-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="9d11f-103">Asynchronní operaci můžete po určité době zrušit pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, pokud nechcete čekat na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="9d11f-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="9d11f-104">Tato metoda naplánuje zrušení všech přidružených úkolů, které nejsou dokončeny v `CancelAfter` rámci časového období, které je určeno výrazem.</span><span class="sxs-lookup"><span data-stu-id="9d11f-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="9d11f-105">Tento příklad přidá ke kódu, který je vyvinut v [Zrušit asynchronní úlohu nebo Seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) ke stažení seznamu webů a zobrazit délku obsahu každého z nich.</span><span class="sxs-lookup"><span data-stu-id="9d11f-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="9d11f-106">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="9d11f-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="9d11f-107">Stáhněte si příklad</span><span class="sxs-lookup"><span data-stu-id="9d11f-107">Download the example</span></span>

<span data-ttu-id="9d11f-108">Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="9d11f-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="9d11f-109">Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d11f-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="9d11f-110">Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="9d11f-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="9d11f-111">V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="9d11f-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="9d11f-112">V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelAfterTime** a pak zvolte **Nastavit jako počáteční projekt**.</span><span class="sxs-lookup"><span data-stu-id="9d11f-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="9d11f-113">Zvolte klávesu **F5** pro spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="9d11f-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="9d11f-114">(Nebo stisknutím **klávesy Ctrl**+**F5** spusťte projekt bez ladění).</span><span class="sxs-lookup"><span data-stu-id="9d11f-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="9d11f-115">Spusťte program několikrát a ověřte, zda výstup může zobrazovat výstup pro všechny weby, žádné weby nebo některé webové stránky.</span><span class="sxs-lookup"><span data-stu-id="9d11f-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="9d11f-116">Pokud projekt nechcete stáhnout, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9d11f-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="9d11f-117">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="9d11f-117">Build the example</span></span>

<span data-ttu-id="9d11f-118">Příklad v tomto tématu přidá do projektu, který je vyvinut v [Zrušit asynchronní úkol nebo Seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznam úkolů.</span><span class="sxs-lookup"><span data-stu-id="9d11f-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="9d11f-119">Příklad používá stejné ui, i když **tlačítko Storno** není použit explicitně.</span><span class="sxs-lookup"><span data-stu-id="9d11f-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="9d11f-120">Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v části "Stažení příkladu", ale zvolte **CancelAListOfTasks** jako **projekt StartUp**Project .</span><span class="sxs-lookup"><span data-stu-id="9d11f-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="9d11f-121">Přidejte změny v tomto tématu do tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="9d11f-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="9d11f-122">Chcete-li určit maximální dobu, po jejíž například `CancelAfter` `startButton_Click`jsou úkoly označeny jako zrušené, přidejte volání do , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="9d11f-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="9d11f-123">Přídavek je označen hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="9d11f-123">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
    }
    catch (OperationCanceledException)
    {
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }

    cts = null;
}
```

 <span data-ttu-id="9d11f-124">Spusťte program několikrát a ověřte, zda výstup může zobrazovat výstup pro všechny weby, žádné weby nebo některé webové stránky.</span><span class="sxs-lookup"><span data-stu-id="9d11f-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="9d11f-125">Následující výstup je ukázka.</span><span class="sxs-lookup"><span data-stu-id="9d11f-125">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="9d11f-126">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="9d11f-126">Complete example</span></span>

<span data-ttu-id="9d11f-127">Následující kód je úplný text MainWindow.xaml.cs souboru pro příklad.</span><span class="sxs-lookup"><span data-stu-id="9d11f-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="9d11f-128">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="9d11f-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="9d11f-129">Všimněte si, že <xref:System.Net.Http>je nutné přidat odkaz pro .</span><span class="sxs-lookup"><span data-stu-id="9d11f-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="9d11f-130">Projekt si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="9d11f-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive.
using System.Threading;

namespace CancelAfterTime
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="9d11f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d11f-131">See also</span></span>

- [<span data-ttu-id="9d11f-132">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="9d11f-132">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="9d11f-133">Návod: Přístup k webu pomocí asynchronní a čeká (C#)</span><span class="sxs-lookup"><span data-stu-id="9d11f-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="9d11f-134">Zrušení asynchronní úlohy nebo seznamu úkolů (C#)</span><span class="sxs-lookup"><span data-stu-id="9d11f-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="9d11f-135">Jemné doladění asynchronní aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="9d11f-135">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="9d11f-136">Asynchronní ukázka: Jemné doladění aplikace</span><span class="sxs-lookup"><span data-stu-id="9d11f-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
