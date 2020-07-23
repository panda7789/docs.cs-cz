---
title: Jak zajistit paralelní více webových požadavků pomocí modifikátoru Async a operátoru Await (C#)
description: Naučte se, jak oddělit vytváření úkolů pomocí operátoru await v jazyce C# namísto použití při vytvoření úkolu.
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 899dfd9165d199a67a5178bb351081ee544b231f
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925160"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="38e2b-103">Jak zajistit paralelní více webových požadavků pomocí modifikátoru Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="38e2b-103">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="38e2b-104">V asynchronní metodě jsou úlohy spouštěny při jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="38e2b-104">In an async method, tasks are started when they're created.</span></span> <span data-ttu-id="38e2b-105">Operátor [await](../../../language-reference/operators/await.md) se aplikuje na úkol v místě v metodě, kde zpracování nemůže pokračovat, dokud se úloha nedokončí.</span><span class="sxs-lookup"><span data-stu-id="38e2b-105">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can't continue until the task finishes.</span></span> <span data-ttu-id="38e2b-106">Úkol se často očekává ihned po vytvoření, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="38e2b-106">Often a task is awaited as soon as it's created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="38e2b-107">Můžete ale oddělit vytvoření úlohy z čekání na úkol, pokud má program další práci, která nezávisí na dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="38e2b-107">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn't depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="38e2b-108">Mezi zahájením úlohy a čekáním na ni můžete spustit další úlohy.</span><span class="sxs-lookup"><span data-stu-id="38e2b-108">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="38e2b-109">Další úkoly jsou implicitně spouštěny paralelně, ale nejsou vytvořeny žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="38e2b-109">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="38e2b-110">Následující program spustí tři asynchronní webové stahování a pak je očekává v pořadí, ve kterém jsou volány.</span><span class="sxs-lookup"><span data-stu-id="38e2b-110">The following program starts three asynchronous web downloads and then awaits them in the order in which they're called.</span></span> <span data-ttu-id="38e2b-111">Všimněte si, že při spuštění programu nejsou úlohy vždy dokončeny v pořadí, ve kterém byly vytvořeny a očekávány.</span><span class="sxs-lookup"><span data-stu-id="38e2b-111">Notice, when you run the program, that the tasks don't always finish in the order in which they're created and awaited.</span></span> <span data-ttu-id="38e2b-112">Spouštějí se při jejich vytvoření a jedna nebo více úkolů může skončit předtím, než metoda dosáhne výrazů await.</span><span class="sxs-lookup"><span data-stu-id="38e2b-112">They start to run when they're created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38e2b-113">Chcete-li dokončit tento projekt, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo vyšší a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="38e2b-113">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="38e2b-114">Další příklad, který spouští více úloh současně, naleznete v tématu [How to Extending the Async průvodce pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="38e2b-114">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="38e2b-115">Kód pro tento příklad si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="38e2b-115">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="38e2b-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="38e2b-116">To set up the project</span></span>  
  
1. <span data-ttu-id="38e2b-117">Chcete-li nastavit aplikaci WPF, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="38e2b-117">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="38e2b-118">Podrobné pokyny k těmto krokům najdete v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="38e2b-118">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="38e2b-119">Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko.</span><span class="sxs-lookup"><span data-stu-id="38e2b-119">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="38e2b-120">Pojmenujte tlačítko `startButton` a pojmenujte textové pole `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="38e2b-120">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="38e2b-121">Přidejte odkaz pro <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="38e2b-121">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="38e2b-122">Do souboru MainWindow.xaml.cs přidejte `using` direktivu pro `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="38e2b-122">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="38e2b-123">Přidání kódu</span><span class="sxs-lookup"><span data-stu-id="38e2b-123">To add the code</span></span>  
  
1. <span data-ttu-id="38e2b-124">V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko a vytvořte `startButton_Click` obslužnou rutinu události v MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="38e2b-124">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="38e2b-125">Zkopírujte následující kód a vložte ho do textu `startButton_Click` v MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="38e2b-125">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="38e2b-126">Kód volá asynchronní metodu, `CreateMultipleTasksAsync` která aplikaci zařídí.</span><span class="sxs-lookup"><span data-stu-id="38e2b-126">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="38e2b-127">Do projektu přidejte následující metody podpory:</span><span class="sxs-lookup"><span data-stu-id="38e2b-127">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="38e2b-128">`ProcessURLAsync`používá <xref:System.Net.Http.HttpClient> metodu ke stažení obsahu webu jako bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="38e2b-128">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="38e2b-129">Metoda podpory `ProcessURLAsync` pak zobrazí a vrátí délku pole.</span><span class="sxs-lookup"><span data-stu-id="38e2b-129">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="38e2b-130">`DisplayResults`zobrazí počet bajtů v bajtovém poli pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="38e2b-130">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="38e2b-131">Toto zobrazení ukazuje, kdy se každý úkol dokončí stahováním.</span><span class="sxs-lookup"><span data-stu-id="38e2b-131">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="38e2b-132">Zkopírujte následující metody a vložte je po `startButton_Click` obslužné rutině události v MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="38e2b-132">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. <span data-ttu-id="38e2b-133">Nakonec definujte metodu `CreateMultipleTasksAsync` , která provede následující kroky.</span><span class="sxs-lookup"><span data-stu-id="38e2b-133">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="38e2b-134">Metoda deklaruje `HttpClient` objekt, který je zapotřebí pro přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="38e2b-134">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="38e2b-135">Metoda vytvoří a spustí tři úkoly typu <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="38e2b-135">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="38e2b-136">Po dokončení každé úlohy se `DisplayResults` zobrazí adresa URL úlohy a délka staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="38e2b-136">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="38e2b-137">Vzhledem k tomu, že úlohy jsou spuštěny asynchronně, pořadí, ve kterém se výsledky zobrazují, se může lišit od pořadí, ve kterém byly deklarovány.</span><span class="sxs-lookup"><span data-stu-id="38e2b-137">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="38e2b-138">Metoda čeká na dokončení každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="38e2b-138">The method awaits the completion of each task.</span></span> <span data-ttu-id="38e2b-139">Každý `await` operátor pozastaví provádění, `CreateMultipleTasksAsync` dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="38e2b-139">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="38e2b-140">Operátor také Načte návratovou hodnotu z volání `ProcessURLAsync` z každé dokončené úlohy.</span><span class="sxs-lookup"><span data-stu-id="38e2b-140">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="38e2b-141">Po dokončení úloh a načtení celočíselných hodnot metoda sečte délky webů a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="38e2b-141">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="38e2b-142">Zkopírujte následující metodu a vložte ji do svého řešení.</span><span class="sxs-lookup"><span data-stu-id="38e2b-142">Copy the following method, and paste it into your solution.</span></span>  
  
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
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="38e2b-143">Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="38e2b-143">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="38e2b-144">Spusťte program několikrát, abyste ověřili, že tři úkoly nejsou vždy dokončeny ve stejném pořadí a že pořadí, ve kterém jsou dokončeny, nemusí být nutně pořadí, ve kterém byly vytvořeny a očekávány.</span><span class="sxs-lookup"><span data-stu-id="38e2b-144">Run the program several times to verify that the three tasks don't always finish in the same order and that the order in which they finish isn't necessarily the order in which they're created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38e2b-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="38e2b-145">Example</span></span>  
 <span data-ttu-id="38e2b-146">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="38e2b-146">The following code contains the full example.</span></span>  
  
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
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
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
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="38e2b-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="38e2b-147">See also</span></span>

- [<span data-ttu-id="38e2b-148">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="38e2b-148">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="38e2b-149">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="38e2b-149">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="38e2b-150">Postup rozšiřování asynchronního návodu pomocí Task. WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="38e2b-150">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
