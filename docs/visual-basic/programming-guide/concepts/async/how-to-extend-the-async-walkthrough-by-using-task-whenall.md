---
title: 'Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 12d195caa11cd33b4e450e5a57699da4037ed4a2
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696348"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="5197b-102">Postupy: rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5197b-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="5197b-103">Může zvýšit výkon řešení asynchronních v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="5197b-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5197b-104">Tato metoda asynchronně čeká více asynchronních operací, které jsou reprezentovány jako kolekce úloh.</span><span class="sxs-lookup"><span data-stu-id="5197b-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="5197b-105">Možná jste si všimli v návodu, weby, ke stažení různým tempem.</span><span class="sxs-lookup"><span data-stu-id="5197b-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="5197b-106">Někdy jeden z webů je velmi pomalé, což zpozdí všechna zbývající stahování.</span><span class="sxs-lookup"><span data-stu-id="5197b-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="5197b-107">Když spustíte asynchronní řešení, které vytvoříte v návodu, můžete program snadno ukončit, pokud nechcete čekat, ale chcete spustit všechny soubory ke stažení ve stejnou dobu a umožní rychlejší stahování pokračovat bez čekání na ten, který by bylo lepší volbou pro  zpožděno.</span><span class="sxs-lookup"><span data-stu-id="5197b-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="5197b-108">Můžete použít `Task.WhenAll` metodu pro kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="5197b-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="5197b-109">Použití `WhenAll` vrátí jednu úlohu, která není kompletní, dokud se nedokončí každý úkol v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5197b-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="5197b-110">Úkoly zdánlivě spouštějí paralelně, ale jsou vytvořeny žádné další vlákna.</span><span class="sxs-lookup"><span data-stu-id="5197b-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="5197b-111">Úlohy můžete dokončit v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5197b-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5197b-112">Následující postupy popisují rozšíření pro asynchronní aplikace vyvinuté v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5197b-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="5197b-113">Dokončení průvodce nebo stahování kód můžete vyvíjet aplikace [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="5197b-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="5197b-114">Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo později v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="5197b-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="5197b-115">Přidání metody Task.WhenAll do řešení GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="5197b-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="5197b-116">Přidat `ProcessURLAsync` metoda k první aplikaci, která je vyvinuta v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5197b-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="5197b-117">Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a poté přidejte `ProcessURLAsync` MainWindow.xaml.vb souboru.</span><span class="sxs-lookup"><span data-stu-id="5197b-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="5197b-118">Pokud kód vyvinutými dokončení průvodce, přidejte `ProcessURLAsync` k aplikaci, která zahrnuje `GetURLContentsAsync` metoda.</span><span class="sxs-lookup"><span data-stu-id="5197b-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="5197b-119">Soubor MainWindow.xaml.vb pro tuto aplikaci je v prvním příkladu v části "Kompletní kód příklady z a podrobný postup".</span><span class="sxs-lookup"><span data-stu-id="5197b-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="5197b-120">`ProcessURLAsync` Slučuje metoda akce v textu `For Each` smyčky v `SumPageSizesAsync` v původní návodu.</span><span class="sxs-lookup"><span data-stu-id="5197b-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="5197b-121">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="5197b-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="5197b-122">Komentář nebo odstranění `For Each` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="5197b-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  <span data-ttu-id="5197b-123">Vytvořte kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="5197b-123">Create a collection of tasks.</span></span> <span data-ttu-id="5197b-124">Následující kód definuje [dotazu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , když provedený <xref:System.Linq.Enumerable.ToArray%2A> metoda, vytvoří kolekci úloh, které stažení obsahu jednotlivých webů.</span><span class="sxs-lookup"><span data-stu-id="5197b-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="5197b-125">Úkoly jsou spuštěny při vyhodnocování dotazu.</span><span class="sxs-lookup"><span data-stu-id="5197b-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="5197b-126">Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `urlList`.</span><span class="sxs-lookup"><span data-stu-id="5197b-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="5197b-127">Použít `Task.WhenAll` ke kolekci úloh `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="5197b-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="5197b-128">`Task.WhenAll` Vrátí jednu úlohu, která se dokončí po dokončení všech úloh v kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="5197b-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="5197b-129">V následujícím příkladu `Await` výraz čeká na dokončení jedné úloha, která `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="5197b-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="5197b-130">Výraz vyhodnocen jako pole celých čísel, kde každý celé číslo je délka stažené webu.</span><span class="sxs-lookup"><span data-stu-id="5197b-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="5197b-131">Přidejte následující kód, který `SumPageSizesAsync`, jednoduše po kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="5197b-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="5197b-132">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součet délek všechny weby.</span><span class="sxs-lookup"><span data-stu-id="5197b-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="5197b-133">Přidejte následující řádek na `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="5197b-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="5197b-134">Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="5197b-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="5197b-135">Přidejte následující verze `ProcessURLAsync` na druhou aplikaci, která je vytvořena v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5197b-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="5197b-136">Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a poté přidejte `ProcessURLAsync` MainWindow.xaml.vb souboru.</span><span class="sxs-lookup"><span data-stu-id="5197b-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="5197b-137">Pokud kód vyvinutými dokončení průvodce, přidejte `ProcessURLAsync` k aplikaci, která používá `HttpClient.GetByteArrayAsync` metoda.</span><span class="sxs-lookup"><span data-stu-id="5197b-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="5197b-138">Soubor MainWindow.xaml.vb pro tuto aplikaci je v druhém příkladu v části "Kompletní kód příklady z a podrobný postup".</span><span class="sxs-lookup"><span data-stu-id="5197b-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="5197b-139">`ProcessURLAsync` Slučuje metoda akce v textu `For Each` smyčky v `SumPageSizesAsync` v původní návodu.</span><span class="sxs-lookup"><span data-stu-id="5197b-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="5197b-140">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="5197b-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="5197b-141">Jediným rozdílem z `ProcessURLAsync` metoda v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client`.</span><span class="sxs-lookup"><span data-stu-id="5197b-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="5197b-142">Komentář nebo odstranění `For Each` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="5197b-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
    ```  
  
3.  <span data-ttu-id="5197b-143">Definovat [dotazu](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , když provedený <xref:System.Linq.Enumerable.ToArray%2A> metoda, vytvoří kolekci úloh, které stažení obsahu jednotlivých webů.</span><span class="sxs-lookup"><span data-stu-id="5197b-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="5197b-144">Úkoly jsou spuštěny při vyhodnocování dotazu.</span><span class="sxs-lookup"><span data-stu-id="5197b-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="5197b-145">Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `client` a `urlList`.</span><span class="sxs-lookup"><span data-stu-id="5197b-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="5197b-146">V dalším kroku použít `Task.WhenAll` ke kolekci úloh `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="5197b-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="5197b-147">`Task.WhenAll` Vrátí jednu úlohu, která se dokončí po dokončení všech úloh v kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="5197b-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="5197b-148">V následujícím příkladu `Await` výraz čeká na dokončení jedné úloha, která `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="5197b-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="5197b-149">Po dokončení `Await` výraz vyhodnocen jako pole celých čísel, kde každý celé číslo je délka stažené webu.</span><span class="sxs-lookup"><span data-stu-id="5197b-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="5197b-150">Přidejte následující kód, který `SumPageSizesAsync`, jednoduše po kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="5197b-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="5197b-151">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metoda získat součet délek všechny weby.</span><span class="sxs-lookup"><span data-stu-id="5197b-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="5197b-152">Přidejte následující řádek na `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="5197b-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="5197b-153">Otestování řešení Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="5197b-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="5197b-154">Buď řešení, zvolte klávesu F5 a spusťte program a pak **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="5197b-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="5197b-155">Výstup by měl vypadat výstup z těchto řešení asynchronních v [návod: přístup k webu pomocí modifikátoru Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5197b-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="5197b-156">Všimněte si však, že weby se objeví v jiném pořadí pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="5197b-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5197b-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="5197b-157">Example</span></span>  
 <span data-ttu-id="5197b-158">Následující kód ukazuje rozšíření pro projekt, který používá `GetURLContentsAsync` metodu za účelem stahování obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="5197b-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                ' CopyToAsync returns a Task, not a Task<T>.  
                Await responseStream.CopyToAsync(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a><span data-ttu-id="5197b-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="5197b-159">Example</span></span>  
 <span data-ttu-id="5197b-160">Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` ke stahování obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="5197b-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="5197b-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="5197b-161">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5197b-162">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5197b-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
