---
title: "Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 509f9e690a5157c2d80ba9726354ce57a9d7ff26
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="83c79-102">Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="83c79-102">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>
<span data-ttu-id="83c79-103">V asynchronní metody když vytváří se spustí úlohy.</span><span class="sxs-lookup"><span data-stu-id="83c79-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="83c79-104">[Await](../../../../csharp/language-reference/keywords/await.md) operátor se použije pro úlohu v okamžiku v metodě kde zpracování nemůže pokračovat, dokud na dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="83c79-104">The [await](../../../../csharp/language-reference/keywords/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="83c79-105">Úloha je často očekáváno, jakmile je vytvořen, jako ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="83c79-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="83c79-106">Můžete však oddělit, vytvoření úlohy z čeká na úlohy, pokud má jinou práci provedete program, který nezávisí na dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="83c79-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="83c79-107">Mezi počáteční úlohu a čeká na jeho, můžete spustit další úlohy.</span><span class="sxs-lookup"><span data-stu-id="83c79-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="83c79-108">Další úlohy implicitně paralelní spuštění, ale jsou vytvořeny žádné další vlákna.</span><span class="sxs-lookup"><span data-stu-id="83c79-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="83c79-109">Následující program spustí tři asynchronní webové stahování a pak je čeká v pořadí, ve kterém jsou volány.</span><span class="sxs-lookup"><span data-stu-id="83c79-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="83c79-110">Všimněte si, při spuštění programu, který úlohy není vždy dokončit v pořadí, ve kterém byly vytvořeny nebo očekáváno.</span><span class="sxs-lookup"><span data-stu-id="83c79-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="83c79-111">Spuštění spustit, když vytvoříte a jeden nebo více úkolů může dokončit před metodu dosáhne await výrazy.</span><span class="sxs-lookup"><span data-stu-id="83c79-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83c79-112">K dokončení tohoto projektu, musíte mít Visual Studio 2012 nebo vyšší a rozhraní .NET Framework 4.5 nebo vyšší v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="83c79-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="83c79-113">Další příklad, která se spouští ve stejnou dobu více úloh, najdete v části [postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="83c79-113">For another example that starts multiple tasks at the same time, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="83c79-114">Si můžete stáhnout kód v tomto příkladu z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="83c79-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="83c79-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="83c79-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="83c79-116">Pokud chcete nastavit aplikaci WPF, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="83c79-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="83c79-117">Najdete podrobné pokyny pro tyto kroky v [návod: přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="83c79-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="83c79-118">Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko.</span><span class="sxs-lookup"><span data-stu-id="83c79-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="83c79-119">Název tlačítka `startButton`a název textového pole `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="83c79-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="83c79-120">Přidat odkaz pro <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="83c79-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="83c79-121">V souboru MainWindow.xaml.cs přidat `using` direktivy pro `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="83c79-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="83c79-122">Přidání kódu</span><span class="sxs-lookup"><span data-stu-id="83c79-122">To add the code</span></span>  
  
1.  <span data-ttu-id="83c79-123">V okně návrhu MainWindow.xaml, dvakrát klikněte na tlačítko vytvořit `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="83c79-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="83c79-124">Zkopírujte následující kód a vložte jej do textu `startButton_Click` v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="83c79-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="83c79-125">Kód volá asynchronní metodu, `CreateMultipleTasksAsync`, jednotky, které se aplikace.</span><span class="sxs-lookup"><span data-stu-id="83c79-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="83c79-126">Do projektu přidejte následující metody podpory:</span><span class="sxs-lookup"><span data-stu-id="83c79-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="83c79-127">`ProcessURLAsync` používá <xref:System.Net.Http.HttpClient> metoda pro stažení obsahu webu, jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="83c79-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="83c79-128">V případě metody podporu `ProcessURLAsync` pak zobrazí a vrátí délku pole.</span><span class="sxs-lookup"><span data-stu-id="83c79-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="83c79-129">`DisplayResults` Zobrazí počet bajtů v bajtové pole pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="83c79-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="83c79-130">Toto zobrazení zobrazí, když každý úkol dokončí stahování.</span><span class="sxs-lookup"><span data-stu-id="83c79-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="83c79-131">Zkopírujte následující metody a vložte je po `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="83c79-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
4.  <span data-ttu-id="83c79-132">Nakonec zadejte metoda `CreateMultipleTasksAsync`, který provede následující kroky.</span><span class="sxs-lookup"><span data-stu-id="83c79-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="83c79-133">Deklaruje metodu `HttpClient` objekt, který potřebujete přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="83c79-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="83c79-134">Metoda vytvoří a spustí tři úlohy typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="83c79-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="83c79-135">Když každý úkol dokončí, `DisplayResults` zobrazí adresa URL úkolu a délka stažený obsah.</span><span class="sxs-lookup"><span data-stu-id="83c79-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="83c79-136">Vzhledem k tomu, že úlohy běží asynchronně, pořadí, ve kterém se zobrazí výsledky se může lišit od pořadí, ve kterém bylo deklarováno.</span><span class="sxs-lookup"><span data-stu-id="83c79-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="83c79-137">Metoda čeká na dokončení každé úlohy.</span><span class="sxs-lookup"><span data-stu-id="83c79-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="83c79-138">Každý `await` operátor pozastaví spuštění `CreateMultipleTasksAsync` dokončení awaited úloh.</span><span class="sxs-lookup"><span data-stu-id="83c79-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="83c79-139">Operátor také načte návratová hodnota z volání `ProcessURLAsync` z každé dokončené úlohy.</span><span class="sxs-lookup"><span data-stu-id="83c79-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="83c79-140">Když byly dokončeny úlohy a byly získány celočíselné hodnoty, metoda sečte délek weby a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="83c79-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="83c79-141">Zkopírujte následující metodu a vložte jej do řešení.</span><span class="sxs-lookup"><span data-stu-id="83c79-141">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults   
        // displays its length.  
        Task<int> download1 =   
            ProcessURLAsync("http://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text +=  
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
    ```  
  
5.  <span data-ttu-id="83c79-142">Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="83c79-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="83c79-143">Spusťte program pro ověření, že tři úlohy není vždy dokončit ve stejném pořadí a pořadí, ve kterém dokončit není nutně pořadí, ve které jste vytvořili a očekávaná několikrát.</span><span class="sxs-lookup"><span data-stu-id="83c79-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83c79-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="83c79-144">Example</span></span>  
 <span data-ttu-id="83c79-145">Následující kód obsahuje kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="83c79-145">The following code contains the full example.</span></span>  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults   
            // displays its length.  
            Task<int> download1 =   
                ProcessURLAsync("http://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="83c79-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="83c79-146">See Also</span></span>  
 [<span data-ttu-id="83c79-147">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="83c79-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="83c79-148">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="83c79-148">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="83c79-149">Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="83c79-149">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
