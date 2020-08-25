---
title: Zrušení seznamu úkolů (C#)
description: Naučte se používat tokeny zrušení k signalizaci žádosti o zrušení seznamu úkolů.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 000b6a89a9240344508a5ae6b248572c8a2177dc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811480"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="ddf56-103">Zrušení seznamu úkolů (C#)</span><span class="sxs-lookup"><span data-stu-id="ddf56-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="ddf56-104">Můžete zrušit asynchronní konzolovou aplikaci, pokud nechcete čekat na její dokončení.</span><span class="sxs-lookup"><span data-stu-id="ddf56-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="ddf56-105">Podle následujícího příkladu v tomto tématu můžete přidat zrušení do aplikace, která stáhne obsah seznamu webů.</span><span class="sxs-lookup"><span data-stu-id="ddf56-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="ddf56-106">Přiřazením <xref:System.Threading.CancellationTokenSource> instance ke každému úkolu můžete zrušit mnoho úloh.</span><span class="sxs-lookup"><span data-stu-id="ddf56-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="ddf56-107">Pokud vyberete klávesu <kbd>ENTER</kbd> , zrušíte všechny úlohy, které ještě nebyly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="ddf56-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="ddf56-108">Tento kurz zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="ddf56-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ddf56-109">Vytvoření konzolové aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="ddf56-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="ddf56-110">Zápis asynchronní aplikace, která podporuje zrušení</span><span class="sxs-lookup"><span data-stu-id="ddf56-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="ddf56-111">Demonstrace zrušení signalizace</span><span class="sxs-lookup"><span data-stu-id="ddf56-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ddf56-112">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="ddf56-112">Prerequisites</span></span>

<span data-ttu-id="ddf56-113">V tomto kurzu budete potřebovat následující:</span><span class="sxs-lookup"><span data-stu-id="ddf56-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="ddf56-114">.NET 5,0 nebo novější SDK</span><span class="sxs-lookup"><span data-stu-id="ddf56-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="ddf56-115">Integrované vývojové prostředí (IDE)</span><span class="sxs-lookup"><span data-stu-id="ddf56-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="ddf56-116">Doporučujeme Visual Studio, Visual Studio Code nebo Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="ddf56-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="ddf56-117">Vytvořit ukázkovou aplikaci</span><span class="sxs-lookup"><span data-stu-id="ddf56-117">Create example application</span></span>

<span data-ttu-id="ddf56-118">Vytvořte novou konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddf56-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="ddf56-119">Můžete ho vytvořit pomocí příkazu [dotnet New Console](../../../../core/tools/dotnet-new.md#console) nebo ze sady [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ddf56-119">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="ddf56-120">Otevřete soubor *program.cs* ve svém oblíbeném editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ddf56-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="ddf56-121">Nahradit příkazy using</span><span class="sxs-lookup"><span data-stu-id="ddf56-121">Replace using statements</span></span>

<span data-ttu-id="ddf56-122">Nahraďte existující příkazy using těmito deklaracemi:</span><span class="sxs-lookup"><span data-stu-id="ddf56-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="ddf56-123">Přidat pole</span><span class="sxs-lookup"><span data-stu-id="ddf56-123">Add fields</span></span>

<span data-ttu-id="ddf56-124">Do `Program` definice třídy přidejte tato tři pole:</span><span class="sxs-lookup"><span data-stu-id="ddf56-124">In the `Program` class definition, add these three fields:</span></span>

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

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

<span data-ttu-id="ddf56-125"><xref:System.Threading.CancellationTokenSource>Slouží k signalizaci požadovaného zrušení na <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="ddf56-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="ddf56-126">`HttpClient`Zpřístupňuje možnost odesílat požadavky HTTP a přijímat odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="ddf56-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="ddf56-127">`s_urlList`Obsahuje všechny adresy URL, které aplikace plánuje zpracovat.</span><span class="sxs-lookup"><span data-stu-id="ddf56-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="ddf56-128">Aktualizovat vstupní bod aplikace</span><span class="sxs-lookup"><span data-stu-id="ddf56-128">Update application entry point</span></span>

<span data-ttu-id="ddf56-129">Hlavní vstupní bod do konzolové aplikace je `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="ddf56-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="ddf56-130">Existující metodu nahraďte následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ddf56-130">Replace the existing method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="ddf56-131">Aktualizovaná `Main` Metoda je nyní považována za [asynchronní hlavní](../../../whats-new/csharp-7-1.md#async-main), což umožňuje asynchronní vstupní bod do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="ddf56-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="ddf56-132">Zapisuje do konzoly několik pokynů a pak deklaruje <xref:System.Threading.Tasks.Task> instanci nazvanou `cancelTask` , která načte tahy kláves konzoly.</span><span class="sxs-lookup"><span data-stu-id="ddf56-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="ddf56-133">Při stisknutí klávesy <kbd>ENTER</kbd> se <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> provede volání.</span><span class="sxs-lookup"><span data-stu-id="ddf56-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="ddf56-134">Tato akce zruší zrušení signálu.</span><span class="sxs-lookup"><span data-stu-id="ddf56-134">This will signal cancellation.</span></span> <span data-ttu-id="ddf56-135">Dále `sumPageSizesTask` je proměnná přiřazena z `SumPageSizesAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="ddf56-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="ddf56-136">Oba úkoly jsou následně předány do <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> , což bude pokračovat po dokončení kterékoli ze dvou úloh.</span><span class="sxs-lookup"><span data-stu-id="ddf56-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="ddf56-137">Vytvořit metodu asynchronní velikosti stránek součtu</span><span class="sxs-lookup"><span data-stu-id="ddf56-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="ddf56-138">Pod `Main` metodu přidejte `SumPageSizesAsync` metodu:</span><span class="sxs-lookup"><span data-stu-id="ddf56-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="ddf56-139">Metoda začíná vytvořením instance a spuštěním <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="ddf56-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="ddf56-140">Pak projde každou adresu URL v `s_urlList` voláních a `ProcessUrlAsync` .</span><span class="sxs-lookup"><span data-stu-id="ddf56-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="ddf56-141">Při každé iteraci se `s_cts.Token` předává do `ProcessUrlAsync` metody a kód vrátí <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo:</span><span class="sxs-lookup"><span data-stu-id="ddf56-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="ddf56-142">Přidat metodu procesu</span><span class="sxs-lookup"><span data-stu-id="ddf56-142">Add process method</span></span>

<span data-ttu-id="ddf56-143">Do metody přidejte následující `ProcessUrlAsync` metodu `SumPageSizesAsync` :</span><span class="sxs-lookup"><span data-stu-id="ddf56-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="ddf56-144">Pro všechny zadané adresy URL metoda použije `client` poskytnutou instanci k získání odpovědi jako `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="ddf56-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="ddf56-145"><xref:System.Threading.CancellationToken>Instance je předána do <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> metod a <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ddf56-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="ddf56-146">`token`Slouží k registraci k požadovanému zrušení.</span><span class="sxs-lookup"><span data-stu-id="ddf56-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="ddf56-147">Délka se vrátí po zápisu adresy URL a délky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="ddf56-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="ddf56-148">Příklad výstupu aplikace</span><span class="sxs-lookup"><span data-stu-id="ddf56-148">Example application output</span></span>

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="ddf56-149">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="ddf56-149">Complete example</span></span>

<span data-ttu-id="ddf56-150">Následující kód je úplný text souboru *program.cs* pro příklad.</span><span class="sxs-lookup"><span data-stu-id="ddf56-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="ddf56-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddf56-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="ddf56-152">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="ddf56-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="ddf56-153">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ddf56-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ddf56-154">Zrušení asynchronních úloh po určitém časovém intervalu (C#)</span><span class="sxs-lookup"><span data-stu-id="ddf56-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
