---
title: 'Postupy: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: fb323852c83b1edf51396a0b800c2d54a833d0c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396620"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="97b91-102">Postupy: roztažení asynchronního návodu pomocí Task. WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97b91-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>

<span data-ttu-id="97b91-103">Můžete zvýšit výkon asynchronního řešení v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) pomocí <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="97b91-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="97b91-104">Tato metoda asynchronně očekává více asynchronních operací, které jsou reprezentovány jako kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="97b91-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="97b91-105">Možná jste si všimli v návodu, že se weby stahují různými sazbami.</span><span class="sxs-lookup"><span data-stu-id="97b91-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="97b91-106">Někdy je jeden z webů velmi pomalý, což zpozdí všechna zbývající stahování.</span><span class="sxs-lookup"><span data-stu-id="97b91-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="97b91-107">Při spuštění asynchronních řešení, která sestavíte v tomto návodu, můžete program ukončit, pokud nechcete čekat, ale lepší možností je zahájit všechna stahování ve stejnou dobu a umožnit rychlejší stahování, aniž byste čekali na zpoždění.</span><span class="sxs-lookup"><span data-stu-id="97b91-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="97b91-108">Metodu použijete `Task.WhenAll` pro kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="97b91-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="97b91-109">Aplikace `WhenAll` vrátí jednu úlohu, která není dokončena, dokud není dokončen každý úkol v kolekci.</span><span class="sxs-lookup"><span data-stu-id="97b91-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="97b91-110">Úkoly se zdají běžet paralelně, ale nevytvoří se žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="97b91-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="97b91-111">Úkoly mohou být dokončeny v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="97b91-111">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97b91-112">Následující postupy popisují rozšíření pro asynchronní aplikace, které jsou vyvíjeny v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="97b91-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="97b91-113">Můžete vyvíjet aplikace buď dokončením návodu, nebo stažením kódu z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="97b91-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="97b91-114">Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="97b91-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="97b91-115">Přidání metody Task.WhenAll do řešení GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="97b91-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="97b91-116">Přidejte `ProcessURLAsync` metodu do první aplikace, která je vyvíjena v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="97b91-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="97b91-117">Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete projekt AsyncWalkthrough a poté přidejte `ProcessURLAsync` do souboru MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="97b91-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="97b91-118">Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která obsahuje `GetURLContentsAsync` metodu.</span><span class="sxs-lookup"><span data-stu-id="97b91-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="97b91-119">Soubor MainWindow. XAML. vb pro tuto aplikaci je prvním příkladem v části kompletní příklady kódu z návodu.</span><span class="sxs-lookup"><span data-stu-id="97b91-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="97b91-120">`ProcessURLAsync`Metoda slučuje akce v těle `For Each` smyčky v `SumPageSizesAsync` původním návodu.</span><span class="sxs-lookup"><span data-stu-id="97b91-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="97b91-121">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="97b91-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="97b91-122">Odkomentujte nebo odstraňte `For Each` smyčku v `SumPageSizesAsync` , jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="97b91-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="97b91-123">Vytvořte kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="97b91-123">Create a collection of tasks.</span></span> <span data-ttu-id="97b91-124">Následující kód definuje [dotaz](../linq/index.md) , který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="97b91-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="97b91-125">Úkoly se spustí, když se dotaz vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="97b91-125">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="97b91-126">Přidejte následující kód do metody `SumPageSizesAsync` po deklaraci `urlList` .</span><span class="sxs-lookup"><span data-stu-id="97b91-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="97b91-127">Platí `Task.WhenAll` pro kolekci úloh, `downloadTasks` .</span><span class="sxs-lookup"><span data-stu-id="97b91-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="97b91-128">`Task.WhenAll`Vrátí jeden úkol, který skončí po dokončení všech úkolů v kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="97b91-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="97b91-129">V následujícím příkladu `Await` výraz čeká na dokončení jedné úlohy, která se `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="97b91-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="97b91-130">Výraz je vyhodnocen jako pole celých čísel, kde každé celé číslo je délka staženého webu.</span><span class="sxs-lookup"><span data-stu-id="97b91-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="97b91-131">Přidejte následující kód do `SumPageSizesAsync` , hned po kódu, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="97b91-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="97b91-132">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu pro výpočet součtu délek všech webů.</span><span class="sxs-lookup"><span data-stu-id="97b91-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="97b91-133">Přidejte následující řádek do `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="97b91-133">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="97b91-134">Přidání metody Task.WhenAll do řešení HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="97b91-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="97b91-135">Přidejte následující verzi `ProcessURLAsync` do druhé aplikace, která je vyvíjena v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="97b91-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="97b91-136">Pokud jste stáhli kód z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otevřete AsyncWalkthrough_HttpClient projekt a pak přidejte `ProcessURLAsync` do souboru MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="97b91-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="97b91-137">Pokud jste kód vyvinuli dokončením návodu, přidejte `ProcessURLAsync` do aplikace, která používá `HttpClient.GetByteArrayAsync` metodu.</span><span class="sxs-lookup"><span data-stu-id="97b91-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="97b91-138">Soubor MainWindow. XAML. vb pro tuto aplikaci je druhým příkladem v části kompletní příklady kódu z návodu.</span><span class="sxs-lookup"><span data-stu-id="97b91-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="97b91-139">`ProcessURLAsync`Metoda slučuje akce v těle `For Each` smyčky v `SumPageSizesAsync` původním návodu.</span><span class="sxs-lookup"><span data-stu-id="97b91-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="97b91-140">Metoda asynchronně stáhne obsah zadaného webu jako bajtové pole a poté zobrazí a vrátí délku bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="97b91-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

     <span data-ttu-id="97b91-141">Jediným rozdílem z `ProcessURLAsync` metody v předchozím postupu je použití <xref:System.Net.Http.HttpClient> instance, `client` .</span><span class="sxs-lookup"><span data-stu-id="97b91-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="97b91-142">Odkomentujte nebo odstraňte `For Each` smyčku v `SumPageSizesAsync` , jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="97b91-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="97b91-143">Definujte [dotaz](../linq/index.md) , který při spuštění <xref:System.Linq.Enumerable.ToArray%2A> metodou vytvoří kolekci úkolů, které stáhnou obsah každého webu.</span><span class="sxs-lookup"><span data-stu-id="97b91-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="97b91-144">Úkoly se spustí, když se dotaz vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="97b91-144">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="97b91-145">`SumPageSizesAsync`Po deklaraci a přidejte následující kód do metody `client` `urlList` .</span><span class="sxs-lookup"><span data-stu-id="97b91-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="97b91-146">Dále platí `Task.WhenAll` pro kolekci úkolů, `downloadTasks` .</span><span class="sxs-lookup"><span data-stu-id="97b91-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="97b91-147">`Task.WhenAll`Vrátí jeden úkol, který skončí po dokončení všech úkolů v kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="97b91-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="97b91-148">V následujícím příkladu `Await` výraz čeká na dokončení jedné úlohy, která se `WhenAll` vrátí.</span><span class="sxs-lookup"><span data-stu-id="97b91-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="97b91-149">Po dokončení se `Await` výraz vyhodnotí jako pole celých čísel, kde každé celé číslo je délka staženého webu.</span><span class="sxs-lookup"><span data-stu-id="97b91-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="97b91-150">Přidejte následující kód do `SumPageSizesAsync` , hned po kódu, který jste přidali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="97b91-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="97b91-151">Nakonec použijte <xref:System.Linq.Enumerable.Sum%2A> metodu k získání součtu délek všech webů.</span><span class="sxs-lookup"><span data-stu-id="97b91-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="97b91-152">Přidejte následující řádek do `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="97b91-152">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="97b91-153">Otestování řešení Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="97b91-153">To test the Task.WhenAll solutions</span></span>

<span data-ttu-id="97b91-154">Pro jedno řešení zvolte klávesu F5 pro spuštění programu a pak klikněte na tlačítko **Start** .</span><span class="sxs-lookup"><span data-stu-id="97b91-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="97b91-155">Výstup by měl vypadat podobně jako výstup z asynchronních řešení v [návodu: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="97b91-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="97b91-156">Všimněte si ale, že se weby v každé době zobrazují v jiném pořadí.</span><span class="sxs-lookup"><span data-stu-id="97b91-156">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="97b91-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="97b91-157">Example</span></span>

<span data-ttu-id="97b91-158">Následující kód ukazuje rozšíření pro projekt, který používá `GetURLContentsAsync` metodu ke stažení obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="97b91-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

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

## <a name="example"></a><span data-ttu-id="97b91-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="97b91-159">Example</span></span>

<span data-ttu-id="97b91-160">Následující kód ukazuje rozšíření pro projekt, který používá metodu `HttpClient.GetByteArrayAsync` ke stažení obsahu z webu.</span><span class="sxs-lookup"><span data-stu-id="97b91-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="97b91-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="97b91-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="97b91-162">Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97b91-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
