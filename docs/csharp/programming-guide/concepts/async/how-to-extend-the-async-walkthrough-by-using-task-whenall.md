---
title: 'Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 4bdd3f32d2fa502de8ada352c522198a89a17f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339466"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="37e45-102">Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="37e45-102">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>
<span data-ttu-id="37e45-103">Může zvýšit výkon řešení asynchronních v [návod: přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="37e45-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="37e45-104">Tato metoda asynchronně čeká více asynchronních operací, které jsou reprezentovány jako kolekce úloh.</span><span class="sxs-lookup"><span data-stu-id="37e45-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="37e45-105">Možná jste si všimli v návodu, weby, ke stažení různým tempem.</span><span class="sxs-lookup"><span data-stu-id="37e45-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="37e45-106">Někdy jeden z webů je velmi pomalé, což zpozdí všechna zbývající stahování.</span><span class="sxs-lookup"><span data-stu-id="37e45-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="37e45-107">Když spustíte asynchronní řešení, které vytvoříte v návodu, můžete program snadno ukončit, pokud nechcete čekat, ale chcete spustit všechny soubory ke stažení ve stejnou dobu a umožní rychlejší stahování pokračovat bez čekání na ten, který by bylo lepší volbou pro  zpožděno.</span><span class="sxs-lookup"><span data-stu-id="37e45-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="37e45-108">Můžete použít `Task.WhenAll` metodu pro kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="37e45-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="37e45-109">Použití `WhenAll` vrátí jednu úlohu, která není kompletní, dokud se nedokončí každý úkol v kolekci.</span><span class="sxs-lookup"><span data-stu-id="37e45-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="37e45-110">Úkoly zdánlivě spouštějí paralelně, ale jsou vytvořeny žádné další vlákna.</span><span class="sxs-lookup"><span data-stu-id="37e45-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="37e45-111">Úlohy můžete dokončit v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="37e45-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37e45-112">Následující postupy popisují rozšíření pro asynchronní aplikace vyvinuté v [návod: přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="37e45-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="37e45-113">Dokončení průvodce nebo stahování kód můžete vyvíjet aplikace [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="37e45-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="37e45-114">Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo později v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="37e45-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="37e45-115">Přidání metody Task.WhenAll do řešení GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="37e45-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="37e45-116">Přidat `ProcessURLAsync` metoda k první aplikaci, která je vyvinuta v [návod: přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="37e45-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="37e45-117">Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a poté přidejte `ProcessURLAsync` MainWindow.xaml.cs souboru.</span><span class="sxs-lookup"><span data-stu-id="37e45-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="37e45-118">Pokud kód vyvinutými dokončení průvodce, přidejte `ProcessURLAsync` k aplikaci, která zahrnuje `GetURLContentsAsync` metoda.</span><span class="sxs-lookup"><span data-stu-id="37e45-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="37e45-119">Soubor MainWindow.xaml.cs pro tuto aplikaci je v prvním příkladu v části "Kompletní kód příklady z a podrobný postup".</span><span class="sxs-lookup"><span data-stu-id="37e45-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="37e45-120">`ProcessURLAsync` Slučuje metoda akce v textu `foreach` smyčky v `SumPageSizesAsync` v původní návodu.</span><span class="sxs-lookup"><span data-stu-id="37e45-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="37e45-121">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="37e45-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="37e45-122">Komentář nebo odstranění `foreach` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="37e45-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="37e45-123">Vytvořte kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="37e45-123">Create a collection of tasks.</span></span> <span data-ttu-id="37e45-124">Následující kód definuje [dotazu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , když provedený <xref:System.Linq.Enumerable.ToArray%2A> metoda, vytvoří kolekci úloh, které stažení obsahu jednotlivých webů.</span><span class="sxs-lookup"><span data-stu-id="37e45-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="37e45-125">Úkoly jsou spuštěny při vyhodnocování dotazu.</span><span class="sxs-lookup"><span data-stu-id="37e45-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="37e45-126">Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `urlList`.</span><span class="sxs-lookup"><span data-stu-id="37e45-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="37e45-127">Použít `Task.WhenAll` ke kolekci úloh `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="37e45-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="37e45-128">`Task.WhenAll` Vrátí jednu úlohu, která se dokončí po dokončení všech úloh v kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="37e45-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="37e45-129">V následujícím příkladu `await` výraz čeká na dokončení jedné úloha, která `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="37e45-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="37e45-130">Výraz vyhodnocen jako pole celých čísel, kde každý celé číslo je délka stažené webu.</span><span class="sxs-lookup"><span data-stu-id="37e45-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="37e45-131">Přidejte následující kód, který `SumPageSizesAsync`, jednoduše po kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="37e45-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="37e45-132">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součet délek všechny weby.</span><span class="sxs-lookup"><span data-stu-id="37e45-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="37e45-133">Přidejte následující řádek na `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="37e45-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="37e45-134">Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="37e45-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="37e45-135">Přidejte následující verze `ProcessURLAsync` na druhou aplikaci, která je vytvořena v [návod: přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="37e45-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="37e45-136">Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a poté přidejte `ProcessURLAsync` MainWindow.xaml.cs souboru.</span><span class="sxs-lookup"><span data-stu-id="37e45-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="37e45-137">Pokud kód vyvinutými dokončení průvodce, přidejte `ProcessURLAsync` k aplikaci, která používá `HttpClient.GetByteArrayAsync` metoda.</span><span class="sxs-lookup"><span data-stu-id="37e45-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="37e45-138">Soubor MainWindow.xaml.cs pro tuto aplikaci je v druhém příkladu v části "Kompletní kód příklady z a podrobný postup".</span><span class="sxs-lookup"><span data-stu-id="37e45-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="37e45-139">`ProcessURLAsync` Slučuje metoda akce v textu `foreach` smyčky v `SumPageSizesAsync` v původní návodu.</span><span class="sxs-lookup"><span data-stu-id="37e45-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="37e45-140">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="37e45-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="37e45-141">Jediným rozdílem z `ProcessURLAsync` metoda v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client`.</span><span class="sxs-lookup"><span data-stu-id="37e45-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURL(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="37e45-142">Komentář nebo odstranění `For Each` nebo `foreach` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="37e45-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="37e45-143">Definovat [dotazu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , když provedený <xref:System.Linq.Enumerable.ToArray%2A> metoda, vytvoří kolekci úloh, které stažení obsahu jednotlivých webů.</span><span class="sxs-lookup"><span data-stu-id="37e45-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="37e45-144">Úkoly jsou spuštěny při vyhodnocování dotazu.</span><span class="sxs-lookup"><span data-stu-id="37e45-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="37e45-145">Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `client` a `urlList`.</span><span class="sxs-lookup"><span data-stu-id="37e45-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURL(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="37e45-146">V dalším kroku použít `Task.WhenAll` ke kolekci úloh `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="37e45-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="37e45-147">`Task.WhenAll` Vrátí jednu úlohu, která se dokončí po dokončení všech úloh v kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="37e45-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="37e45-148">V následujícím příkladu `await` výraz čeká na dokončení jedné úloha, která `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="37e45-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="37e45-149">Po dokončení `await` výraz vyhodnocen jako pole celých čísel, kde každý celé číslo je délka stažené webu.</span><span class="sxs-lookup"><span data-stu-id="37e45-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="37e45-150">Přidejte následující kód, který `SumPageSizesAsync`, jednoduše po kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="37e45-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="37e45-151">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metoda získat součet délek všechny weby.</span><span class="sxs-lookup"><span data-stu-id="37e45-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="37e45-152">Přidejte následující řádek na `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="37e45-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="37e45-153">Otestování řešení Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="37e45-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="37e45-154">Buď řešení, zvolte klávesu F5 a spusťte program a pak **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="37e45-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="37e45-155">Výstup by měl vypadat výstup z těchto řešení asynchronních v [návod: přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="37e45-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="37e45-156">Všimněte si však, že weby se objeví v jiném pořadí pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="37e45-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37e45-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="37e45-157">Example</span></span>  
 <span data-ttu-id="37e45-158">Následující kód ukazuje rozšíření pro projekt, který používá `GetURLContentsAsync` metodu za účelem stahování obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="37e45-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="37e45-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="37e45-159">Example</span></span>  
 <span data-ttu-id="37e45-160">Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` ke stahování obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="37e45-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
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
                from url in urlList select ProcessURL(url, client);  
  
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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURL(string url, HttpClient client)  
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
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="37e45-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="37e45-161">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="37e45-162">Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="37e45-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
