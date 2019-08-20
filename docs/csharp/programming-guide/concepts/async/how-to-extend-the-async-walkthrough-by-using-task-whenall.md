---
title: 'Postupy: Rozšíříte asynchronní návod pomocí Task. WhenAll (C#).'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: a2cbff81c07a2be0f66e4d310dd300d646d3256c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595582"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="83f66-102">Postupy: Rozšíříte asynchronní návod pomocí Task. WhenAll (C#).</span><span class="sxs-lookup"><span data-stu-id="83f66-102">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>
<span data-ttu-id="83f66-103">Můžete zvýšit výkon asynchronního řešení v [tomto návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md) await (C#) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="83f66-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="83f66-104">Tato metoda asynchronně očekává více asynchronních operací, které jsou reprezentovány jako kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="83f66-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="83f66-105">Možná jste si všimli v návodu, že se weby stahují různými sazbami.</span><span class="sxs-lookup"><span data-stu-id="83f66-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="83f66-106">Někdy je jeden z webů velmi pomalý, což zpozdí všechna zbývající stahování.</span><span class="sxs-lookup"><span data-stu-id="83f66-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="83f66-107">Při spuštění asynchronních řešení, která sestavíte v tomto návodu, můžete program ukončit, pokud nechcete čekat, ale lepší možností je zahájit všechna stahování ve stejnou dobu a umožnit rychlejší stahování i nadále, aniž byste čekali na to, který z nich je  platba.</span><span class="sxs-lookup"><span data-stu-id="83f66-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="83f66-108">`Task.WhenAll` Metodu použijete pro kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="83f66-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="83f66-109">Aplikace `WhenAll` vrátí jednu úlohu, která není dokončena, dokud není dokončen každý úkol v kolekci.</span><span class="sxs-lookup"><span data-stu-id="83f66-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="83f66-110">Úkoly se zdají běžet paralelně, ale nevytvoří se žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="83f66-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="83f66-111">Úkoly mohou být dokončeny v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="83f66-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83f66-112">Následující postupy popisují rozšíření pro asynchronní aplikace, které jsou vyvíjeny v [návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#).</span><span class="sxs-lookup"><span data-stu-id="83f66-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="83f66-113">Můžete vyvíjet aplikace buď dokončením návodu, nebo stažením kódu z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="83f66-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="83f66-114">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="83f66-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="83f66-115">Přidání metody Task.WhenAll do řešení GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="83f66-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1. <span data-ttu-id="83f66-116">Přidejte metodu do první aplikace, která je vyvíjena v [návodu: `ProcessURLAsync` Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#).</span><span class="sxs-lookup"><span data-stu-id="83f66-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="83f66-117">Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a pak přidejte `ProcessURLAsync` do souboru MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="83f66-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    - <span data-ttu-id="83f66-118">Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která `GetURLContentsAsync` obsahuje metodu.</span><span class="sxs-lookup"><span data-stu-id="83f66-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="83f66-119">Soubor MainWindow.xaml.cs pro tuto aplikaci je prvním příkladem v části kompletní příklady kódu z návodu.</span><span class="sxs-lookup"><span data-stu-id="83f66-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="83f66-120">Metoda slučuje akce v těle `foreach` smyčky v `SumPageSizesAsync` původním návodu. `ProcessURLAsync`</span><span class="sxs-lookup"><span data-stu-id="83f66-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="83f66-121">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="83f66-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. <span data-ttu-id="83f66-122">Odkomentujte nebo odstraňte `foreach` smyčku `SumPageSizesAsync`v, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="83f66-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    byte[] urlContents = await GetURLContentsAsync(url);  
  
    //    // The previous line abbreviates the following two assignment statements.  
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //    //byte[] urlContents = await getContentsTask;  
  
    //    DisplayResults(url, urlContents);  
  
    //    // Update the total.            
    //    total += urlContents.Length;  
    //}  
    ```  
  
3. <span data-ttu-id="83f66-123">Vytvořte kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="83f66-123">Create a collection of tasks.</span></span> <span data-ttu-id="83f66-124">Následující kód definuje [dotaz](../linq/index.md) , který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="83f66-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="83f66-125">Úkoly se spustí, když se dotaz vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="83f66-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="83f66-126">Přidejte následující kód do metody `SumPageSizesAsync` po `urlList`deklaraci.</span><span class="sxs-lookup"><span data-stu-id="83f66-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="83f66-127">Platí `Task.WhenAll` pro kolekci úloh, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="83f66-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="83f66-128">`Task.WhenAll`Vrátí jeden úkol, který skončí po dokončení všech úkolů v kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="83f66-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="83f66-129">V následujícím příkladu `await` výraz čeká na dokončení jedné úlohy, která se `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="83f66-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="83f66-130">Výraz je vyhodnocen jako pole celých čísel, kde každé celé číslo je délka staženého webu.</span><span class="sxs-lookup"><span data-stu-id="83f66-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="83f66-131">Přidejte následující kód do `SumPageSizesAsync`, hned po kódu, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="83f66-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. <span data-ttu-id="83f66-132">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součtu délek všech webů.</span><span class="sxs-lookup"><span data-stu-id="83f66-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="83f66-133">Přidejte následující řádek do `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="83f66-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="83f66-134">Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="83f66-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1. <span data-ttu-id="83f66-135">Přidejte následující verzi `ProcessURLAsync` do druhé aplikace, která je vyvíjena v [návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#).</span><span class="sxs-lookup"><span data-stu-id="83f66-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="83f66-136">Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a pak přidejte `ProcessURLAsync` do souboru MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="83f66-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    - <span data-ttu-id="83f66-137">Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která `HttpClient.GetByteArrayAsync` používá metodu.</span><span class="sxs-lookup"><span data-stu-id="83f66-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="83f66-138">Soubor MainWindow.xaml.cs pro tuto aplikaci je druhým příkladem v části kompletní příklady kódu z návodu.</span><span class="sxs-lookup"><span data-stu-id="83f66-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="83f66-139">Metoda slučuje akce v těle `foreach` smyčky v `SumPageSizesAsync` původním návodu. `ProcessURLAsync`</span><span class="sxs-lookup"><span data-stu-id="83f66-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="83f66-140">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="83f66-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="83f66-141">Jediným rozdílem z `ProcessURLAsync` metody v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client`.</span><span class="sxs-lookup"><span data-stu-id="83f66-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2. <span data-ttu-id="83f66-142">Odkomentujte nebo odstraňte `For Each` smyčku nebo `SumPageSizesAsync` `foreach` v, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="83f66-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
    //    // The previous line abbreviates the following two assignment  
    //    // statements.  
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
    //    byte[] urlContent = await getContentTask;  
  
    //    DisplayResults(url, urlContent);  
  
    //    // Update the total.  
    //    total += urlContent.Length;  
    //}  
    ```  
  
3. <span data-ttu-id="83f66-143">Definujte [dotaz](../linq/index.md) , který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="83f66-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="83f66-144">Úkoly se spustí, když se dotaz vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="83f66-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="83f66-145">Po `SumPageSizesAsync` deklaraci`urlList`apřidejtenásledující kód do metody. `client`</span><span class="sxs-lookup"><span data-stu-id="83f66-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="83f66-146">Dále platí `Task.WhenAll` pro kolekci úkolů, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="83f66-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="83f66-147">`Task.WhenAll`Vrátí jeden úkol, který skončí po dokončení všech úkolů v kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="83f66-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="83f66-148">V následujícím příkladu `await` výraz čeká na dokončení jedné úlohy, která se `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="83f66-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="83f66-149">Po dokončení `await` se výraz vyhodnotí jako pole celých čísel, kde každé celé číslo je délka staženého webu.</span><span class="sxs-lookup"><span data-stu-id="83f66-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="83f66-150">Přidejte následující kód do `SumPageSizesAsync`, hned po kódu, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="83f66-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5. <span data-ttu-id="83f66-151">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu k získání součtu délek všech webů.</span><span class="sxs-lookup"><span data-stu-id="83f66-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="83f66-152">Přidejte následující řádek do `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="83f66-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="83f66-153">Otestování řešení Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="83f66-153">To test the Task.WhenAll solutions</span></span>  
  
- <span data-ttu-id="83f66-154">Pro jedno řešení zvolte klávesu F5 pro spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="83f66-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="83f66-155">Výstup by měl vypadat podobně jako výstup z asynchronních řešení v [návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#).</span><span class="sxs-lookup"><span data-stu-id="83f66-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="83f66-156">Všimněte si ale, že se weby v každé době zobrazují v jiném pořadí.</span><span class="sxs-lookup"><span data-stu-id="83f66-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f66-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="83f66-157">Example</span></span>  
 <span data-ttu-id="83f66-158">Následující kód ukazuje rozšíření pro projekt, který používá `GetURLContentsAsync` metodu ke stažení obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="83f66-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_WhenAll  
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
  
            // Two-step async call.  
            Task sumTask = SumPageSizesAsync();  
            await sumTask;  
  
            // One-step async call.  
            //await SumPageSizesAsync();  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Create a query.   
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    byte[] urlContents = await GetURLContentsAsync(url);  
  
            //    // The previous line abbreviates the following two assignment statements.  
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
            //    //byte[] urlContents = await getContentsTask;  
  
            //    DisplayResults(url, urlContents);  
  
            //    // Update the total.            
            //    total += urlContents.Length;  
            //}  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        private async Task<int> ProcessURLAsync(string url)  
        {  
            var byteArray = await GetURLContentsAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.  
            using (WebResponse response = await webReq.GetResponseAsync())  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    await responseStream.CopyToAsync(content);  
                }  
            }  
  
            // Return the result as a byte array.  
            return content.ToArray();  
  
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
  
## <a name="example"></a><span data-ttu-id="83f66-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="83f66-159">Example</span></span>  
 <span data-ttu-id="83f66-160">Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` ke stažení obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="83f66-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_HttpClient_WhenAll  
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
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create a query.  
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url, client);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
            //    // The previous line abbreviates the following two assignment  
            //    // statements.  
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
            //    byte[] urlContent = await getContentTask;  
  
            //    DisplayResults(url, urlContent);  
  
            //    // Update the total.  
            //    total += urlContent.Length;  
            //}  
  
            // Display the total count for all of the web addresses.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            byte[] byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each web site. The string format   
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
  
## <a name="see-also"></a><span data-ttu-id="83f66-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83f66-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="83f66-162">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="83f66-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
