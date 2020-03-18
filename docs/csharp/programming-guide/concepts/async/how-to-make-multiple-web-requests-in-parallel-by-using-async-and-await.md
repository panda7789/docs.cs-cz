---
title: Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 9f7420113d4af83d7d057b772af307bd8d4bcc00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169946"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="d9d6f-102">Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)</span><span class="sxs-lookup"><span data-stu-id="d9d6f-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="d9d6f-103">V asynchronní metodě jsou úlohy spuštěny při jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="d9d6f-104">Operátor [await](../../../language-reference/operators/await.md) je použit na úlohu v bodě metody, kde zpracování nemůže pokračovat, dokud úkol neskončí.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="d9d6f-105">Často je úkol očekáván, jakmile je vytvořen, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="d9d6f-106">Pokud však program má k dokončení jiné práce, která nezávisí na dokončení úkolu, můžete vytvořit úlohu od čekání na úkol.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="d9d6f-107">Mezi zahájením úkolu a čekáním na něj můžete spustit další úkoly.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="d9d6f-108">Další úlohy implicitně spustit paralelně, ale jsou vytvořeny žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="d9d6f-109">Následující program spustí tři asynchronní webové soubory ke stažení a pak je čeká v pořadí, ve kterém jsou volány.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="d9d6f-110">Všimněte si, při spuštění programu, že úkoly nejsou vždy dokončeny v pořadí, ve kterém jsou vytvořeny a čekal.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="d9d6f-111">Začnou běžet, když jsou vytvořeny a jeden nebo více úkolů může být dokončena dříve, než metoda dosáhne await výrazy.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9d6f-112">K dokončení tohoto projektu musíte mít v počítači nainstalovanou visual studio 2012 nebo vyšší a rozhraní .NET Framework 4.5 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="d9d6f-113">Další příklad, který spouští více úkolů současně, naleznete v [tématu Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="d9d6f-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="d9d6f-114">Kód pro tento příklad si můžete stáhnout z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="d9d6f-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="d9d6f-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="d9d6f-115">To set up the project</span></span>  
  
1. <span data-ttu-id="d9d6f-116">Chcete-li nastavit aplikaci WPF, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="d9d6f-117">Podrobné pokyny k těmto krokům najdete v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="d9d6f-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="d9d6f-118">Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="d9d6f-119">Pojmenujte `startButton`tlačítko a pojmenujte textové pole `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="d9d6f-120">Přidejte odkaz <xref:System.Net.Http>pro .</span><span class="sxs-lookup"><span data-stu-id="d9d6f-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="d9d6f-121">V souboru MainWindow.xaml.cs `using` přidejte `System.Net.Http`direktivu pro .</span><span class="sxs-lookup"><span data-stu-id="d9d6f-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="d9d6f-122">Přidání kódu</span><span class="sxs-lookup"><span data-stu-id="d9d6f-122">To add the code</span></span>  
  
1. <span data-ttu-id="d9d6f-123">V okně návrhu MainWindow.xaml poklepejte na `startButton_Click` tlačítko a vytvořte obslužnou rutinu události v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="d9d6f-124">Zkopírujte následující kód a vložte `startButton_Click` jej do těla v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="d9d6f-125">Kód volá asynchronní metodu `CreateMultipleTasksAsync`, která řídí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="d9d6f-126">Do projektu přidejte následující metody podpory:</span><span class="sxs-lookup"><span data-stu-id="d9d6f-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="d9d6f-127">`ProcessURLAsync`používá <xref:System.Net.Http.HttpClient> metodu ke stažení obsahu webu jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="d9d6f-128">Metoda podpory `ProcessURLAsync` pak zobrazí a vrátí délku pole.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="d9d6f-129">`DisplayResults`zobrazí počet bajtů v bajtovém poli pro každou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="d9d6f-130">Tento displej se zobrazí po dokončení stahování jednotlivých úkolů.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="d9d6f-131">Zkopírujte následující metody a vložte je za obslužnou rutinu `startButton_Click` události v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
  
4. <span data-ttu-id="d9d6f-132">Nakonec definujte `CreateMultipleTasksAsync`metodu , která provádí následující kroky.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="d9d6f-133">Metoda deklaruje `HttpClient` objekt,který je <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> `ProcessURLAsync`třeba získat přístup k metodě v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="d9d6f-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="d9d6f-134">Metoda vytvoří a spustí tři <xref:System.Threading.Tasks.Task%601>úkoly typu , kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="d9d6f-135">Po dokončení každého `DisplayResults` úkolu se zobrazí adresa URL úkolu a délka staženého obsahu.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="d9d6f-136">Vzhledem k tomu, že úlohy jsou spuštěny asynchronně, pořadí, ve kterém se zobrazí výsledky se může lišit od pořadí, ve kterém byly deklarovány.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="d9d6f-137">Metoda čeká na dokončení každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="d9d6f-138">Každý `await` operátor pozastaví `CreateMultipleTasksAsync` provádění, dokud není dokončena očekávaná úloha.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="d9d6f-139">Operátor také načte vrácenou hodnotu `ProcessURLAsync` z volání z každého dokončeného úkolu.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="d9d6f-140">Po dokončení úkolů a byly načteny celé hodnoty, metoda sečte délky webových stránek a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="d9d6f-141">Zkopírujte následující metodu a vložte ji do řešení.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5. <span data-ttu-id="d9d6f-142">Zvolte klávesu F5 pro spuštění programu a pak zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="d9d6f-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="d9d6f-143">Spusťte program několikrát ověřit, že tři úkoly nejsou vždy dokončeny ve stejném pořadí a že pořadí, ve kterém dokončení není nutně pořadí, ve kterém jsou vytvořeny a čekal.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9d6f-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9d6f-144">Example</span></span>  
 <span data-ttu-id="d9d6f-145">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="d9d6f-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9d6f-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9d6f-146">See also</span></span>

- [<span data-ttu-id="d9d6f-147">Návod: Přístup k webu pomocí asynchronní a čeká (C#)</span><span class="sxs-lookup"><span data-stu-id="d9d6f-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="d9d6f-148">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="d9d6f-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="d9d6f-149">Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="d9d6f-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
