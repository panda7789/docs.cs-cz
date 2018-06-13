---
title: Zrušení asynchronních úloh po uplynutí časového intervalu (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 55cf6b960752b36a1bfbd8ede25d7693225fbb20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325705"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="f7bfe-102">Zrušení asynchronních úloh po uplynutí časového intervalu (C#)</span><span class="sxs-lookup"><span data-stu-id="f7bfe-102">Cancel Async Tasks after a Period of Time (C#)</span></span>
<span data-ttu-id="f7bfe-103">Asynchronní operaci po určitou dobu můžete zrušit pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metoda, pokud nechcete čekat na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="f7bfe-104">Tato metoda plány zrušení všechny přidružené úlohy, které nejsou v rámci časový interval, který je určen podle dokončení `CancelAfter` výraz.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="f7bfe-105">Tento příklad přidá do kód, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) stáhnout seznam webů a zobrazit je délka obsahu z každé z nich.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7bfe-106">Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="f7bfe-107">Stažení příkladu</span><span class="sxs-lookup"><span data-stu-id="f7bfe-107">Downloading the Example</span></span>  
 <span data-ttu-id="f7bfe-108">Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="f7bfe-109">Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f7bfe-110">Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="f7bfe-111">V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="f7bfe-112">V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelAfterTime** projektu a potom vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="f7bfe-113">Zvolte klávesu F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="f7bfe-114">Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="f7bfe-115">Chcete-li ověřit, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby spuste program několikrát.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="f7bfe-116">Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="f7bfe-117">Vytváření v příkladu</span><span class="sxs-lookup"><span data-stu-id="f7bfe-117">Building the Example</span></span>  
 <span data-ttu-id="f7bfe-118">V příkladu v tomto tématu přidá do projektu, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznamu úloh.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="f7bfe-119">Tento příklad používá stejné uživatelské rozhraní, i když **zrušit** tlačítko nepoužívá explicitně.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="f7bfe-120">K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="f7bfe-121">Do tohoto projektu přidáte změny v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="f7bfe-122">Chcete-li určit maximální dobu, než úlohy jsou označeny jako zrušená, přidejte volání `CancelAfter` k `startButton_Click`, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="f7bfe-123">Přidání je označena pomocí hvězdiček.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-123">The addition is marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="f7bfe-124">Chcete-li ověřit, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby spuste program několikrát.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="f7bfe-125">Tento výstup je ukázka.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="f7bfe-126">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="f7bfe-126">Complete Example</span></span>  
 <span data-ttu-id="f7bfe-127">Následující kód je úplný text souboru MainWindow.xaml.cs pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="f7bfe-128">Hvězdičky označit prvky, které byly přidány v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="f7bfe-129">Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f7bfe-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="f7bfe-130">Si můžete stáhnout z projektu [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="f7bfe-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a><span data-ttu-id="f7bfe-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7bfe-131">See Also</span></span>  
 [<span data-ttu-id="f7bfe-132">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="f7bfe-132">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="f7bfe-133">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="f7bfe-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="f7bfe-134">Zrušení asynchronní úlohy nebo seznamu úloh (C#)</span><span class="sxs-lookup"><span data-stu-id="f7bfe-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [<span data-ttu-id="f7bfe-135">Vyladění s modifikátorem Async aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="f7bfe-135">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="f7bfe-136">Ukázka asynchronního: Jemnou ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="f7bfe-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
