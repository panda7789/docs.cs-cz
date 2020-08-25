---
title: Zpracování asynchronních úloh po dokončení
description: Tento příklad ukazuje, jak použít Task. WhenAny v jazyce C# ke spuštění více úkolů a zpracování jejich výsledků při jejich dokončení, místo jejich zpracování v pořadí.
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: c2fe66e865a2c88f4cae50b816f9326614fcbb89
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812026"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="c37b0-103">Zpracování asynchronních úloh po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="c37b0-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="c37b0-104">Pomocí nástroje <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> můžete spustit více úloh současně a zpracovat je jeden po jednom, protože jsou dokončeny, a nikoli jejich zpracování v pořadí, ve kterém jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="c37b0-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="c37b0-105">Následující příklad používá dotaz k vytvoření kolekce úkolů.</span><span class="sxs-lookup"><span data-stu-id="c37b0-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="c37b0-106">Každý úkol stáhne obsah zadaného webu.</span><span class="sxs-lookup"><span data-stu-id="c37b0-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="c37b0-107">V každé iteraci smyčky while očekává volání metody <xref:System.Threading.Tasks.Task.WhenAny%2A> vrácení úlohy v kolekci úkolů, které dokončí stahování jako první.</span><span class="sxs-lookup"><span data-stu-id="c37b0-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="c37b0-108">Tato úloha je odebrána z kolekce a zpracována.</span><span class="sxs-lookup"><span data-stu-id="c37b0-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="c37b0-109">Smyčka se opakuje, dokud kolekce neobsahuje žádné další úlohy.</span><span class="sxs-lookup"><span data-stu-id="c37b0-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="c37b0-110">Vytvořit ukázkovou aplikaci</span><span class="sxs-lookup"><span data-stu-id="c37b0-110">Create example application</span></span>

<span data-ttu-id="c37b0-111">Vytvořte novou konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c37b0-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="c37b0-112">Můžete ho vytvořit pomocí příkazu [dotnet New Console](../../../../core/tools/dotnet-new.md#console) nebo ze sady [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c37b0-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="c37b0-113">Otevřete soubor *program.cs* ve svém oblíbeném editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="c37b0-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="c37b0-114">Nahradit příkazy using</span><span class="sxs-lookup"><span data-stu-id="c37b0-114">Replace using statements</span></span>

<span data-ttu-id="c37b0-115">Nahraďte existující příkazy using těmito deklaracemi:</span><span class="sxs-lookup"><span data-stu-id="c37b0-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="c37b0-116">Přidat pole</span><span class="sxs-lookup"><span data-stu-id="c37b0-116">Add fields</span></span>

<span data-ttu-id="c37b0-117">V `Program` definici třídy přidejte následující dvě pole:</span><span class="sxs-lookup"><span data-stu-id="c37b0-117">In the `Program` class definition, add the following two fields:</span></span>

```csharp
static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

<span data-ttu-id="c37b0-118">`HttpClient`Zpřístupňuje možnost odesílat požadavky HTTP a přijímat odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="c37b0-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="c37b0-119">`s_urlList`Obsahuje všechny adresy URL, které aplikace plánuje zpracovat.</span><span class="sxs-lookup"><span data-stu-id="c37b0-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="c37b0-120">Aktualizovat vstupní bod aplikace</span><span class="sxs-lookup"><span data-stu-id="c37b0-120">Update application entry point</span></span>

<span data-ttu-id="c37b0-121">Hlavní vstupní bod do konzolové aplikace je `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="c37b0-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="c37b0-122">Existující metodu nahraďte následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c37b0-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="c37b0-123">Aktualizovaná `Main` Metoda je nyní považována za [asynchronní hlavní](../../../whats-new/csharp-7-1.md#async-main), což umožňuje asynchronní vstupní bod do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="c37b0-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="c37b0-124">Vyjadřuje volání `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="c37b0-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="c37b0-125">Vytvořit metodu asynchronní velikosti stránek součtu</span><span class="sxs-lookup"><span data-stu-id="c37b0-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="c37b0-126">Pod `Main` metodu přidejte `SumPageSizesAsync` metodu:</span><span class="sxs-lookup"><span data-stu-id="c37b0-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="c37b0-127">Metoda začíná vytvořením instance a spuštěním <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="c37b0-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="c37b0-128">Pak obsahuje dotaz, který při spuštění vytvoří kolekci úkolů.</span><span class="sxs-lookup"><span data-stu-id="c37b0-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="c37b0-129">Každé volání do `ProcessUrlAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo:</span><span class="sxs-lookup"><span data-stu-id="c37b0-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="c37b0-130">Z důvodu [odloženého spuštění](../linq/deferred-execution-example.md) s LINQ se zavoláte <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> na spuštění jednotlivých úloh.</span><span class="sxs-lookup"><span data-stu-id="c37b0-130">Due to [deferred execution](../linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="c37b0-131">`while`Smyčka provádí následující kroky pro každý úkol v kolekci:</span><span class="sxs-lookup"><span data-stu-id="c37b0-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="c37b0-132">Očekává volání `WhenAny` k identifikaci prvního úkolu v kolekci, která dokončila stažení.</span><span class="sxs-lookup"><span data-stu-id="c37b0-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="c37b0-133">Odebere úlohu z kolekce.</span><span class="sxs-lookup"><span data-stu-id="c37b0-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. <span data-ttu-id="c37b0-134">Čeká `finishedTask` , který je vrácen voláním metody `ProcessUrlAsync` .</span><span class="sxs-lookup"><span data-stu-id="c37b0-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="c37b0-135">`finishedTask`Proměnná je <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c37b0-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="c37b0-136">Úkol je již dokončen, ale očekáváte, že bude načtena délka staženého webu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c37b0-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="c37b0-137">Pokud dojde k chybě úlohy, `await` vyvolá první podřízenou výjimku uloženou v objektu `AggregateException` , na rozdíl od čtení <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> vlastnosti, která by vyvolala `AggregateException` .</span><span class="sxs-lookup"><span data-stu-id="c37b0-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="c37b0-138">Přidat metodu procesu</span><span class="sxs-lookup"><span data-stu-id="c37b0-138">Add process method</span></span>

<span data-ttu-id="c37b0-139">Do metody přidejte následující `ProcessUrlAsync` metodu `SumPageSizesAsync` :</span><span class="sxs-lookup"><span data-stu-id="c37b0-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="c37b0-140">Pro všechny zadané adresy URL metoda použije `client` poskytnutou instanci k získání odpovědi jako `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="c37b0-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="c37b0-141">Délka se vrátí po zápisu adresy URL a délky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c37b0-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="c37b0-142">Spusťte program několikrát, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c37b0-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="c37b0-143">Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, pro řešení problémů, které zahrnují malý počet úkolů.</span><span class="sxs-lookup"><span data-stu-id="c37b0-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="c37b0-144">Další přístupy jsou ale efektivnější, pokud máte velký počet úkolů, které je potřeba zpracovat.</span><span class="sxs-lookup"><span data-stu-id="c37b0-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="c37b0-145">Další informace a příklady najdete v tématu [zpracování úloh po dokončení](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span><span class="sxs-lookup"><span data-stu-id="c37b0-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="c37b0-146">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="c37b0-146">Complete example</span></span>

<span data-ttu-id="c37b0-147">Následující kód je úplný text souboru *program.cs* pro příklad.</span><span class="sxs-lookup"><span data-stu-id="c37b0-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="c37b0-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="c37b0-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="c37b0-149">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="c37b0-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
