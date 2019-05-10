---
title: 'Postupy: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 9020f09e5e72e5620e954c3a6f9aa1e5a0d4f545
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626478"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="4bf5d-102">Postupy: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bf5d-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="4bf5d-103">Můžete zvýšit výkon asynchronního řešení v [názorný postup: Přístup k webu pomocí Async a Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4bf5d-104">Tato metoda asynchronně čeká na více asynchronních operací, které jsou reprezentovány ve formě kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="4bf5d-105">Možná jste si všimli v návodu, že se weby stahují různými rychlostmi.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="4bf5d-106">Někdy jedna z webových stránek je velmi pomalé, což způsobuje zpoždění všech zbývajících stahování.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="4bf5d-107">Když spustíte asynchronní řešení, které vytvoříte v tomto návodu, můžete můžete ukončit program snadno, pokud nechcete čekat, ale vhodnější by bylo začít všechna stahování současně a nechat pokračovat bez čekání na je rychlejší stahování.  zpožděné.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="4bf5d-108">Můžete použít `Task.WhenAll` metody na kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="4bf5d-109">Použití `WhenAll` vrátí jeden úkol, který není kompletní až do dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="4bf5d-110">Úkoly se zobrazují při paralelním spuštění, ale žádná další vlákna nejsou vytvořena.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="4bf5d-111">Úkoly lze provést v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4bf5d-112">Následující postupy popisují rozšíření pro asynchronní aplikace, které jsou vyvíjeny v [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4bf5d-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="4bf5d-113">Můžete vyvíjet aplikace dokončením návodu nebo stažením kódu z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="4bf5d-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="4bf5d-114">Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="4bf5d-115">Přidání metody Task.WhenAll do řešení GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="4bf5d-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1. <span data-ttu-id="4bf5d-116">Přidat `ProcessURLAsync` metoda k první aplikaci, která je napsán v jazyce [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4bf5d-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="4bf5d-117">Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a přidejte `ProcessURLAsync` do souboru MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    - <span data-ttu-id="4bf5d-118">Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` aplikace, která zahrnuje `GetURLContentsAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="4bf5d-119">Soubor MainWindow.xaml.vb pro tuto aplikaci je první příklad v části "Kompletní kód příkladů z návodu".</span><span class="sxs-lookup"><span data-stu-id="4bf5d-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="4bf5d-120">`ProcessURLAsync` Spojuje akce v těle metody `For Each` smyčky v `SumPageSizesAsync` v původním návodu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="4bf5d-121">Metody asynchronně stáhnou obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. <span data-ttu-id="4bf5d-122">Okomentujte nebo odstraňte `For Each` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3. <span data-ttu-id="4bf5d-123">Vytvořte kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-123">Create a collection of tasks.</span></span> <span data-ttu-id="4bf5d-124">Následující kód definuje [dotazu](../../../../visual-basic/programming-guide/concepts/linq/index.md) , při spuštění metodou <xref:System.Linq.Enumerable.ToArray%2A> vytvoří kolekci úkolů, které stáhnou obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-124">The following code defines a [query](../../../../visual-basic/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="4bf5d-125">Úkoly jsou spuštěny, když je vyhodnocen dotaz.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="4bf5d-126">Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `urlList`.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. <span data-ttu-id="4bf5d-127">Použít `Task.WhenAll` na kolekci úloh, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="4bf5d-128">`Task.WhenAll` Vrátí jeden úkol, který je dokončen po dokončení všech úloh v kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="4bf5d-129">V následujícím příkladu `Await` výraz čeká na dokončení jedné úlohy, které `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="4bf5d-130">Výraz vyhodnocen jako pole celých čísel, kde každé celé číslo je délka stahování webu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="4bf5d-131">Přidejte následující kód, který `SumPageSizesAsync`, za kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. <span data-ttu-id="4bf5d-132">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součtu délek všech webových stránek.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="4bf5d-133">Přidejte následující řádek, který `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="4bf5d-134">Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="4bf5d-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1. <span data-ttu-id="4bf5d-135">Přidejte následující verzi `ProcessURLAsync` do druhé aplikace, který byl vyvinut v [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4bf5d-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="4bf5d-136">Pokud jste stáhli kód z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough_HttpClient a přidejte `ProcessURLAsync` do souboru MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    - <span data-ttu-id="4bf5d-137">Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` aplikace, která se používá `HttpClient.GetByteArrayAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="4bf5d-138">Soubor MainWindow.xaml.vb pro tuto aplikaci je druhý příklad v části "Kompletní kód příkladů z návodu".</span><span class="sxs-lookup"><span data-stu-id="4bf5d-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="4bf5d-139">`ProcessURLAsync` Spojuje akce v těle metody `For Each` smyčky v `SumPageSizesAsync` v původním návodu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="4bf5d-140">Metody asynchronně stáhnou obsah zadaného webu jako bajtové pole a potom zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="4bf5d-141">Jediný rozdíl oproti `ProcessURLAsync` metoda v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client`.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. <span data-ttu-id="4bf5d-142">Okomentujte nebo odstraňte `For Each` smyčky v `SumPageSizesAsync`, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3. <span data-ttu-id="4bf5d-143">Definování [dotazu](../../../../visual-basic/programming-guide/concepts/linq/index.md) , při spuštění metodou <xref:System.Linq.Enumerable.ToArray%2A> vytvoří kolekci úkolů, které stáhnou obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-143">Define a [query](../../../../visual-basic/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="4bf5d-144">Úkoly jsou spuštěny, když je vyhodnocen dotaz.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="4bf5d-145">Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `client` a `urlList`.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. <span data-ttu-id="4bf5d-146">Dále použijte `Task.WhenAll` na kolekci úloh, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="4bf5d-147">`Task.WhenAll` Vrátí jeden úkol, který je dokončen po dokončení všech úloh v kolekci úloh.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="4bf5d-148">V následujícím příkladu `Await` výraz čeká na dokončení jedné úlohy, které `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="4bf5d-149">Jakmile budete hotovi, `Await` výraz vyhodnocen jako pole celých čísel, kde každé celé číslo je délka stahování webu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="4bf5d-150">Přidejte následující kód, který `SumPageSizesAsync`, za kód, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. <span data-ttu-id="4bf5d-151">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu k získání součtu délek všech webových stránek.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="4bf5d-152">Přidejte následující řádek, který `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="4bf5d-153">Otestování řešení Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="4bf5d-153">To test the Task.WhenAll solutions</span></span>  
  
- <span data-ttu-id="4bf5d-154">Pro kteréhokoli řešení, zvolte klávesu F5 ke spuštění programu a klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="4bf5d-155">Výstup by měl vypadat jako výstup asynchronních řešení v [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4bf5d-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="4bf5d-156">Všimněte si však, že jsou weby zobrazeny v jiném pořadí pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bf5d-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf5d-157">Example</span></span>  
 <span data-ttu-id="4bf5d-158">Následující kód ukazuje rozšíření pro projekt, který se používá `GetURLContentsAsync` metoda stahovat obsah z webu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
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
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a><span data-ttu-id="4bf5d-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bf5d-159">Example</span></span>  
 <span data-ttu-id="4bf5d-160">Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` stahovat obsah z webu.</span><span class="sxs-lookup"><span data-stu-id="4bf5d-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
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
                "https://www.msdn.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bf5d-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bf5d-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4bf5d-162">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bf5d-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
