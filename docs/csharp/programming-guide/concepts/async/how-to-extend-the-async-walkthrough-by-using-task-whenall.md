---
title: Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970026"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="42f79-102">Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="42f79-102">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>

<span data-ttu-id="42f79-103">Můžete zlepšit výkon asynchronní řešení v [návodu: Přístup k webu pomocí asynchronní a čekat (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="42f79-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42f79-104">Tato metoda asynchronně čeká na více asynchronních operací, které jsou reprezentovány jako kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="42f79-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="42f79-105">Možná jste si v návodu všimli, že se webové stránky stahují různými rychlostmi.</span><span class="sxs-lookup"><span data-stu-id="42f79-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="42f79-106">Někdy je jedna z webových stránek velmi pomalá, což zpožďuje všechny zbývající soubory ke stažení.</span><span class="sxs-lookup"><span data-stu-id="42f79-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="42f79-107">Když spustíte asynchronní řešení, která vytvoříte v návodu, můžete program snadno ukončit, pokud nechcete čekat, ale lepší možností by bylo spustit všechny stahování současně a nechat rychlejší stahování pokračovat bez čekání na ten, který je Zpoždění.</span><span class="sxs-lookup"><span data-stu-id="42f79-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="42f79-108">Metodu `Task.WhenAll` použijete na kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="42f79-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="42f79-109">Aplikace `WhenAll` vrátí jeden úkol, který není dokončen, dokud není dokončena každá úloha v kolekci.</span><span class="sxs-lookup"><span data-stu-id="42f79-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="42f79-110">Zdá se, že úlohy běží paralelně, ale jsou vytvořeny žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="42f79-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="42f79-111">Úkoly lze dokončit v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="42f79-111">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42f79-112">Následující postupy popisují rozšíření asynchronních aplikací, které jsou vyvinuty v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="42f79-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="42f79-113">Aplikace můžete vyvinout buď vyplněním návodu nebo stažením kódu z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="42f79-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="42f79-114">Chcete-li spustit příklad, musíte mít v počítači nainstalovanou visual studio 2012 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="42f79-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="42f79-115">Přidání metody Task.WhenAll do řešení GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="42f79-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="42f79-116">Přidejte `ProcessURLAsync` metodu do první aplikace, která je vyvinuta v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="42f79-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="42f79-117">Pokud jste stáhli kód z [ukázky kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), `ProcessURLAsync` otevřete projekt AsyncWalkthrough a přidejte do MainWindow.xaml.cs souboru.</span><span class="sxs-lookup"><span data-stu-id="42f79-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="42f79-118">Pokud jste vyvinuli kód vyplněním návodu, přidejte `ProcessURLAsync` `GetURLContentsAsync` do aplikace, která obsahuje metodu.</span><span class="sxs-lookup"><span data-stu-id="42f79-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="42f79-119">Soubor MainWindow.xaml.cs pro tuto aplikaci je prvním příkladem v části "Kompletní příklady kódu z návodu".</span><span class="sxs-lookup"><span data-stu-id="42f79-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="42f79-120">Metoda `ProcessURLAsync` konsoliduje akce v `foreach` těle `SumPageSizesAsync` smyčky v původním návodu.</span><span class="sxs-lookup"><span data-stu-id="42f79-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="42f79-121">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="42f79-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="42f79-122">Zakomentujte `foreach` nebo `SumPageSizesAsync`odstraňte smyčku v , jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="42f79-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="42f79-123">Vytvořte kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="42f79-123">Create a collection of tasks.</span></span> <span data-ttu-id="42f79-124">Následující kód definuje [dotaz,](../linq/index.md) který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stahují obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="42f79-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="42f79-125">Úkoly jsou spuštěny při vyhodnocení dotazu.</span><span class="sxs-lookup"><span data-stu-id="42f79-125">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="42f79-126">Přidejte následující kód `SumPageSizesAsync` metody po `urlList`deklaraci .</span><span class="sxs-lookup"><span data-stu-id="42f79-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="42f79-127">Platí `Task.WhenAll` pro shromažďování úkolů `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="42f79-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="42f79-128">`Task.WhenAll`vrátí jeden úkol, který bude dokončen po dokončení všech úkolů v kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="42f79-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="42f79-129">V následujícím příkladu `await` výraz čeká na dokončení jednoho `WhenAll` úkolu, který vrátí.</span><span class="sxs-lookup"><span data-stu-id="42f79-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="42f79-130">Výraz je vyhodnocen jako pole celých čísel, kde každé celé číslo je délka staženého webu.</span><span class="sxs-lookup"><span data-stu-id="42f79-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="42f79-131">Přidejte následující `SumPageSizesAsync`kód do , těsně za kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="42f79-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="42f79-132">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součtu délek všech webových stránek.</span><span class="sxs-lookup"><span data-stu-id="42f79-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="42f79-133">Do této části `SumPageSizesAsync`přidejte následující řádek.</span><span class="sxs-lookup"><span data-stu-id="42f79-133">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="42f79-134">Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="42f79-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="42f79-135">Přidejte následující `ProcessURLAsync` verzi druhé aplikace, která je vyvinutá v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="42f79-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="42f79-136">Pokud jste stáhli kód z [ukázky kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a přidejte `ProcessURLAsync` do souboru MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="42f79-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="42f79-137">Pokud jste vyvinuli kód vyplněním návodu, přidejte `ProcessURLAsync` `HttpClient.GetByteArrayAsync` do aplikace, která používá metodu.</span><span class="sxs-lookup"><span data-stu-id="42f79-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="42f79-138">Soubor MainWindow.xaml.cs pro tuto aplikaci je druhým příkladem v části "Kompletní příklady kódu z návodu".</span><span class="sxs-lookup"><span data-stu-id="42f79-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="42f79-139">Metoda `ProcessURLAsync` konsoliduje akce v `foreach` těle `SumPageSizesAsync` smyčky v původním návodu.</span><span class="sxs-lookup"><span data-stu-id="42f79-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="42f79-140">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="42f79-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    <span data-ttu-id="42f79-141">Jediný rozdíl od `ProcessURLAsync` metody v předchozím postupu je <xref:System.Net.Http.HttpClient> použití `client`instance , .</span><span class="sxs-lookup"><span data-stu-id="42f79-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="42f79-142">Zakomentujte `For Each` nebo `foreach` odstraňte smyčku nebo v `SumPageSizesAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="42f79-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="42f79-143">Definujte [dotaz,](../linq/index.md) který při <xref:System.Linq.Enumerable.ToArray%2A> spuštění metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="42f79-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="42f79-144">Úkoly jsou spuštěny při vyhodnocení dotazu.</span><span class="sxs-lookup"><span data-stu-id="42f79-144">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="42f79-145">Přidejte následující kód `SumPageSizesAsync` metody po `client` `urlList`deklaraci a .</span><span class="sxs-lookup"><span data-stu-id="42f79-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="42f79-146">Dále platí `Task.WhenAll` pro shromažďování úkolů `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="42f79-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="42f79-147">`Task.WhenAll`vrátí jeden úkol, který bude dokončen po dokončení všech úkolů v kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="42f79-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="42f79-148">V následujícím příkladu `await` výraz čeká na dokončení jednoho `WhenAll` úkolu, který vrátí.</span><span class="sxs-lookup"><span data-stu-id="42f79-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="42f79-149">Po dokončení `await` výraz vyhodnotí pole celých čísel, kde každé celé číslo je délka staženého webu.</span><span class="sxs-lookup"><span data-stu-id="42f79-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="42f79-150">Přidejte následující `SumPageSizesAsync`kód do , těsně za kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="42f79-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="42f79-151">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu, abyste získali součet délek všech webových stránek.</span><span class="sxs-lookup"><span data-stu-id="42f79-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="42f79-152">Do této části `SumPageSizesAsync`přidejte následující řádek.</span><span class="sxs-lookup"><span data-stu-id="42f79-152">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="42f79-153">Otestování řešení Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="42f79-153">To test the Task.WhenAll solutions</span></span>

- <span data-ttu-id="42f79-154">Pro obě řešení zvolte klávesu F5 pro spuštění programu a pak zvolte tlačítko **Start.**</span><span class="sxs-lookup"><span data-stu-id="42f79-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="42f79-155">Výstup by se měl podobat výstupu z asynchronních řešení v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="42f79-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="42f79-156">Všimněte si však, že webové stránky se pokaždé zobrazují v jiném pořadí.</span><span class="sxs-lookup"><span data-stu-id="42f79-156">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="42f79-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="42f79-157">Example</span></span>

<span data-ttu-id="42f79-158">Následující kód ukazuje rozšíření projektu, který `GetURLContentsAsync` používá metodu ke stažení obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="42f79-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

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

## <a name="example"></a><span data-ttu-id="42f79-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="42f79-159">Example</span></span>

<span data-ttu-id="42f79-160">Následující kód ukazuje rozšíření projektu, který `HttpClient.GetByteArrayAsync` používá metodu ke stažení obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="42f79-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="42f79-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="42f79-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="42f79-162">Návod: Přístup k webu pomocí asynchronní a čeká (C#)</span><span class="sxs-lookup"><span data-stu-id="42f79-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
