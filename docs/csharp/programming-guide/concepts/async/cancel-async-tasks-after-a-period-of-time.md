---
title: Zrušení asynchronních úloh po určitém časovém intervalu (C#)
description: Použijte metodu CancellationTokenSource. CancelAfter v jazyce C# k naplánování zrušení všech přidružených úloh, které nejsou dokončeny v rámci období v tomto příkladu.
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: f32af1d893c60ac17648f60fa3aa90adaa0383e8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925289"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="3757b-103">Zrušení asynchronních úloh po určitém časovém intervalu (C#)</span><span class="sxs-lookup"><span data-stu-id="3757b-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="3757b-104">Asynchronní operaci můžete zrušit po časovém intervalu pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, pokud nechcete čekat na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="3757b-104">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="3757b-105">Tato metoda naplánuje zrušení všech přidružených úloh, které nejsou dokončeny v časovém období určeném `CancelAfter` výrazem.</span><span class="sxs-lookup"><span data-stu-id="3757b-105">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="3757b-106">Tento příklad přidá do kódu, který je vyvíjen v rámci [zrušení asynchronní úlohy nebo seznamu úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) pro stažení seznamu webů a zobrazení délky obsahu každého z nich.</span><span class="sxs-lookup"><span data-stu-id="3757b-106">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="3757b-107">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="3757b-107">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="3757b-108">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="3757b-108">Download the example</span></span>

<span data-ttu-id="3757b-109">Z Async Sample si můžete stáhnout dokončený projekt Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="3757b-109">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="3757b-110">Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3757b-110">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="3757b-111">Na panelu nabídek vyberte **soubor**  >  **otevřít**  >  **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="3757b-111">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="3757b-112">V dialogovém okně **Otevřít projekt** otevřete složku, která obsahuje ukázkový kód, který jste dekomprimujei, a poté otevřete soubor řešení (. sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="3757b-112">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="3757b-113">V **Průzkumník řešení**otevřete místní nabídku pro projekt **CancelAfterTime** a pak zvolte **nastavit jako projekt po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="3757b-113">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="3757b-114">Kliknutím na klávesu **F5** spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="3757b-114">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="3757b-115">(Nebo, stiskněte klávesu **CTRL** + **F5** pro spuštění projektu bez ladění).</span><span class="sxs-lookup"><span data-stu-id="3757b-115">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="3757b-116">Spusťte program několikrát, abyste ověřili, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby.</span><span class="sxs-lookup"><span data-stu-id="3757b-116">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="3757b-117">Pokud nechcete stáhnout projekt, můžete si prohlédnout soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3757b-117">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="3757b-118">Sestavení příkladu</span><span class="sxs-lookup"><span data-stu-id="3757b-118">Build the example</span></span>

<span data-ttu-id="3757b-119">Příklad v tomto tématu se přidá do projektu, který je vyvíjen v části [zrušení asynchronní úlohy nebo seznamu úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) pro zrušení seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="3757b-119">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="3757b-120">V příkladu se používá stejné uživatelské rozhraní, i když se tlačítko **Storno** nepoužívá explicitně.</span><span class="sxs-lookup"><span data-stu-id="3757b-120">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="3757b-121">Chcete-li sestavit příklad sami, postupujte podle pokynů v části "stažení příkladu", ale jako **spouštěný projekt**vyberte **CancelAListOfTasks** .</span><span class="sxs-lookup"><span data-stu-id="3757b-121">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="3757b-122">Přidejte změny v tomto tématu do projektu.</span><span class="sxs-lookup"><span data-stu-id="3757b-122">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="3757b-123">Chcete-li zadat maximální dobu před tím, než jsou úkoly označeny jako zrušené, přidejte volání do `CancelAfter` do `startButton_Click` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3757b-123">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="3757b-124">Sčítání jsou označeny hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="3757b-124">The addition is marked with asterisks.</span></span>

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

 <span data-ttu-id="3757b-125">Spusťte program několikrát, abyste ověřili, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby.</span><span class="sxs-lookup"><span data-stu-id="3757b-125">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="3757b-126">Následující výstup je ukázka.</span><span class="sxs-lookup"><span data-stu-id="3757b-126">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="3757b-127">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="3757b-127">Complete example</span></span>

<span data-ttu-id="3757b-128">Následující kód je úplný text souboru MainWindow.xaml.cs pro příklad.</span><span class="sxs-lookup"><span data-stu-id="3757b-128">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="3757b-129">Hvězdičky označují prvky, které byly přidány pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="3757b-129">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="3757b-130">Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="3757b-130">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="3757b-131">Projekt si můžete stáhnout z části [Async Sample: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="3757b-131">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3757b-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3757b-132">See also</span></span>

- [<span data-ttu-id="3757b-133">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="3757b-133">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="3757b-134">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="3757b-134">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="3757b-135">Zrušení asynchronní úlohy nebo seznamu úloh (C#)</span><span class="sxs-lookup"><span data-stu-id="3757b-135">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="3757b-136">Vyladění aplikace s modifikátorem Async (C#)</span><span class="sxs-lookup"><span data-stu-id="3757b-136">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="3757b-137">Asynchronní vzorek: jemné ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="3757b-137">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
