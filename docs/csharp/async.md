---
title: Asynchronní programování –C#
description: Seznamte se C# s asynchronním programovacím modelem na úrovni jazyka, který poskytuje .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: 86145e8971d9a59fba17368d9530f40d86bf2858
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037677"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="db601-103">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="db601-103">Asynchronous programming</span></span>

<span data-ttu-id="db601-104">Pokud máte nějaké požadavky na vstupně-výstupní operace (například vyžádání dat ze sítě nebo přístup k databázi), budete chtít využít asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="db601-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="db601-105">Můžete mít také kód vázaný na procesor, jako je například provádění nákladného výpočtu, což je také dobrý scénář pro psaní asynchronního kódu.</span><span class="sxs-lookup"><span data-stu-id="db601-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="db601-106">C#má model asynchronního programování na úrovni jazyka, který umožňuje snadno psát asynchronní kód bez nutnosti juggle zpětná volání nebo odpovídat knihovně, která podporuje asynchronii.</span><span class="sxs-lookup"><span data-stu-id="db601-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="db601-107">Postupuje podle toho, co se říká [asynchronní vzor založený na úlohách (klepněte)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="db601-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="db601-108">Základní přehled asynchronního modelu</span><span class="sxs-lookup"><span data-stu-id="db601-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="db601-109">Základem asynchronního programování jsou objekty `Task` a `Task<T>`, které modelují asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="db601-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="db601-110">Jsou podporovány `async` a `await` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="db601-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="db601-111">Model je ve většině případů velmi jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="db601-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="db601-112">Pro vstupně-výstupní kód s vazbou `await` operace, která vrací `Task` nebo `Task<T>` uvnitř metody `async`.</span><span class="sxs-lookup"><span data-stu-id="db601-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="db601-113">V případě kódu vázaného na procesor `await` operace, která je spuštěna ve vlákně na pozadí s metodou `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="db601-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="db601-114">Klíčovým slovem `await` je místo, kde se Magic stane.</span><span class="sxs-lookup"><span data-stu-id="db601-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="db601-115">Poskytuje řízení volajícímu metody, která provedla `await`, a nakonec umožňuje, aby uživatelské rozhraní mohlo reagovat nebo služba měla být Elasticka.</span><span class="sxs-lookup"><span data-stu-id="db601-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="db601-116">Existují i jiné způsoby, jak přistupovat k asynchronnímu kódu než `async` a `await` popsaný v článku výše, který je uvedený výše. Tento dokument se ale bude soustředit na konstrukty na úrovni jazyka od tohoto okamžiku předem.</span><span class="sxs-lookup"><span data-stu-id="db601-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="db601-117">I/O-vázaný příklad: stahování dat z webové služby</span><span class="sxs-lookup"><span data-stu-id="db601-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="db601-118">Může být nutné stáhnout některá data z webové služby, když je stisknuto tlačítko, ale nechcete zablokovat vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db601-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="db601-119">Můžete to provést jednoduše takto:</span><span class="sxs-lookup"><span data-stu-id="db601-119">It can be accomplished simply like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="db601-120">A je to!</span><span class="sxs-lookup"><span data-stu-id="db601-120">And that’s it!</span></span> <span data-ttu-id="db601-121">Kód vyjadřuje záměr (asynchronně stahovat data), aniž by bylo nutné zabřednete v interakci s objekty Task.</span><span class="sxs-lookup"><span data-stu-id="db601-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="db601-122">Příklad vázaný na procesor: provádění výpočtu hry</span><span class="sxs-lookup"><span data-stu-id="db601-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="db601-123">Řekněme, že píšete mobilní hru, kde stisknutí tlačítka může způsobit poškození mnoha Enemies na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="db601-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="db601-124">Provádění výpočtu škod může být nákladné a jeho provedení na vlákně UI by vedlo k tomu, že se hra po provedení výpočtu zastaví.</span><span class="sxs-lookup"><span data-stu-id="db601-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="db601-125">Nejlepším způsobem, jak to zpracovat, je spustit vlákno na pozadí, které funguje pomocí `Task.Run`a `await` jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="db601-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="db601-126">Tím umožníte, aby uživatelské rozhraní bylo hladké, protože práce se provádí.</span><span class="sxs-lookup"><span data-stu-id="db601-126">This will allow the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="db601-127">A je to!</span><span class="sxs-lookup"><span data-stu-id="db601-127">And that's it!</span></span>  <span data-ttu-id="db601-128">Tento kód čistě vyjadřuje záměr události kliknutí na tlačítko, nevyžaduje ruční správu vlákna na pozadí a je tak neblokujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="db601-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="db601-129">Co se stane v rámci pokrývání</span><span class="sxs-lookup"><span data-stu-id="db601-129">What happens under the covers</span></span>

<span data-ttu-id="db601-130">Existuje velký počet přesunů, ve kterých jsou jednotlivé asynchronní operace obavy.</span><span class="sxs-lookup"><span data-stu-id="db601-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="db601-131">Pokud jste zajímái o tom, co se děje, na základě pokrývání `Task` a `Task<T>`, další informace najdete [v](../standard/async-in-depth.md) podrobném článku.</span><span class="sxs-lookup"><span data-stu-id="db601-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="db601-132">Na C# straně sebe Kompilátor transformuje váš kód do stavového počítače, který uchovává informace o tom, jako je například vrácení spuštění, když je dosaženo`await`a pokračuje v provádění po dokončení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="db601-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="db601-133">Pro teoreticky-skloněnou je to implementace [modelu asynchronii pro příslib](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="db601-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="db601-134">Klíčové kousky, které je potřeba pochopit</span><span class="sxs-lookup"><span data-stu-id="db601-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="db601-135">Asynchronní kód lze použít pro vstupně-výstupní operace i pro kód vázaný na procesor, ale pro každý scénář odlišně.</span><span class="sxs-lookup"><span data-stu-id="db601-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="db601-136">Asynchronní kód používá `Task<T>` a `Task`, které jsou konstrukce používané k modelování práce prováděné na pozadí.</span><span class="sxs-lookup"><span data-stu-id="db601-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="db601-137">Klíčové slovo `async` přepíná metodu do asynchronní metody, která umožňuje použití klíčového slova `await` v těle.</span><span class="sxs-lookup"><span data-stu-id="db601-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="db601-138">Při použití klíčového slova `await` pozastaví volající metodu a vrátí řízení volajícímu, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="db601-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="db601-139">`await` lze použít pouze v asynchronní metodě.</span><span class="sxs-lookup"><span data-stu-id="db601-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="db601-140">Rozpoznání práce vázané na procesor a vstupně-výstupní operace</span><span class="sxs-lookup"><span data-stu-id="db601-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="db601-141">První dva příklady této příručky ukázaly, jak můžete použít `async` a `await` pro vstupně-výstupní operace a práci vázanou na procesor.</span><span class="sxs-lookup"><span data-stu-id="db601-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="db601-142">Je klíč, který můžete identifikovat, když je potřeba udělat úlohu, která je vázaná na vstupně-výstupní operace, nebo na základě procesoru, protože může významně ovlivnit výkon kódu a může potenciálně vést k omylům s některými konstrukcemi.</span><span class="sxs-lookup"><span data-stu-id="db601-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="db601-143">Tady jsou dvě otázky, které byste měli před psaním kódu zeptat:</span><span class="sxs-lookup"><span data-stu-id="db601-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="db601-144">Bude váš kód "čekání" na něco, například data z databáze?</span><span class="sxs-lookup"><span data-stu-id="db601-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="db601-145">Pokud je vaše odpověď "Ano", vaše práce je **vázána na vstup/výstup**.</span><span class="sxs-lookup"><span data-stu-id="db601-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="db601-146">Bude váš kód provádět velmi nákladný výpočet?</span><span class="sxs-lookup"><span data-stu-id="db601-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="db601-147">Pokud jste odpověděli na Ano, vaše práce bude **vázaná na procesor**.</span><span class="sxs-lookup"><span data-stu-id="db601-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="db601-148">Pokud je práce, kterou jste **vázáni na vstup/výstup**, používejte `async` a `await` *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="db601-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="db601-149">*Neměli byste* používat Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="db601-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="db601-150">Důvod tohoto důvodu je popsaný v [článku o Dehloubce Async](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="db601-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="db601-151">Pokud je práce **vázaná na procesor** a Vy zajímáte odezvu, použijte `async` a `await`, ale pracujte na jiném vlákně *s* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="db601-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="db601-152">Pokud je práce vhodná pro souběžnost a paralelismu, měli byste také zvážit použití [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="db601-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="db601-153">Kromě toho byste měli vždy změřit provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="db601-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="db601-154">Například se můžete setkat v situaci, kdy práce vázaná na procesor není ve srovnání s režií kontextových přepínačů v případě multithreadingu dostatečně nákladná.</span><span class="sxs-lookup"><span data-stu-id="db601-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="db601-155">Každá volba má své kompromisy a měli byste si vybrat správné kompromisy pro vaši situaci.</span><span class="sxs-lookup"><span data-stu-id="db601-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="db601-156">Další příklady</span><span class="sxs-lookup"><span data-stu-id="db601-156">More Examples</span></span>

<span data-ttu-id="db601-157">Následující příklady ukazují různé způsoby, jak můžete napsat asynchronní kód v C#.</span><span class="sxs-lookup"><span data-stu-id="db601-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="db601-158">Pokrývají několik různých scénářů, které se mohou nacházet v rámci.</span><span class="sxs-lookup"><span data-stu-id="db601-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="db601-159">Extrakce dat ze sítě</span><span class="sxs-lookup"><span data-stu-id="db601-159">Extracting Data from a Network</span></span>

<span data-ttu-id="db601-160">Tento fragment kódu stáhne kód HTML z domovské stránky na pozici [www.dotnetfoundation.org](https://www.dotnetfoundation.org) a spočítá počet výskytů řetězce ".NET" v HTML.</span><span class="sxs-lookup"><span data-stu-id="db601-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="db601-161">Pomocí ASP.NET MVC definuje metodu webového kontroléru, která provádí tuto úlohu, a vrátí číslo.</span><span class="sxs-lookup"><span data-stu-id="db601-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="db601-162">Pokud plánujete provádění analýzy HTML v produkčním kódu, nepoužívejte regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="db601-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="db601-163">Místo toho použijte analýzu knihovny.</span><span class="sxs-lookup"><span data-stu-id="db601-163">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="db601-164">Tady je stejný scénář, který je napsán pro univerzální aplikaci pro Windows, která při stisknutí tlačítka provede stejnou úlohu:</span><span class="sxs-lookup"><span data-stu-id="db601-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="db601-165">Čeká se na dokončení více úloh.</span><span class="sxs-lookup"><span data-stu-id="db601-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="db601-166">Můžete se setkat v situaci, kdy potřebujete současně načíst více dat.</span><span class="sxs-lookup"><span data-stu-id="db601-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="db601-167">Rozhraní `Task` API obsahuje dvě metody, `Task.WhenAll` a `Task.WhenAny`, které umožňují napsat asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="db601-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="db601-168">Tento příklad ukazuje, jak můžete `User` data pro sadu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="db601-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();

    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="db601-169">Tady je další způsob, jak tento trochu napsat mnohem více, pomocí LINQ:</span><span class="sxs-lookup"><span data-stu-id="db601-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="db601-170">I když je to méně kódu, při kombinování LINQ s asynchronním kódem je potřeba dbát.</span><span class="sxs-lookup"><span data-stu-id="db601-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="db601-171">Vzhledem k tomu, že LINQ používá odložené (opožděné) provádění, asynchronní volání nebudou provedena ihned stejně jako v `foreach()` smyčce, pokud nevynutíte vygenerovanou sekvenci iterací voláním `.ToList()` nebo `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="db601-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="db601-172">Důležité informace a Rady</span><span class="sxs-lookup"><span data-stu-id="db601-172">Important Info and Advice</span></span>

<span data-ttu-id="db601-173">I když je asynchronní programování relativně jednoduché, je třeba mít na paměti několik detailů, které mohou zabránit neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="db601-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="db601-174">`async` **metody musí mít** **v těle klíčové slovo `await`, jinak nebudou nikdy vracet!**</span><span class="sxs-lookup"><span data-stu-id="db601-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="db601-175">To je důležité mít na paměti.</span><span class="sxs-lookup"><span data-stu-id="db601-175">This is important to keep in mind.</span></span>  <span data-ttu-id="db601-176">Pokud se `await` nepoužívá v těle metody `async`, C# kompilátor vygeneruje upozornění, ale kód se zkompiluje a spustí, jako kdyby šlo o běžnou metodu.</span><span class="sxs-lookup"><span data-stu-id="db601-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="db601-177">Všimněte si, že by to bylo také neuvěřitelně neefektivní, protože Stavový počítač generovaný C# kompilátorem pro asynchronní metodu nebude provádět žádné akce.</span><span class="sxs-lookup"><span data-stu-id="db601-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="db601-178">**Jako příponu každého názvu asynchronní metody, kterou píšete, byste měli přidat "Async".**</span><span class="sxs-lookup"><span data-stu-id="db601-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="db601-179">Toto je konvence, která se používá v rozhraní .NET pro snadnější odlišení synchronních a asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="db601-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="db601-180">Všimněte si, že některé metody, které nejsou explicitně volány vaším kódem (například obslužné rutiny událostí nebo metody webového kontroleru), nemusí nutně platit.</span><span class="sxs-lookup"><span data-stu-id="db601-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="db601-181">Vzhledem k tomu, že nejsou explicitně volány vaším kódem, explicitní informace o jejich pojmenování nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="db601-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="db601-182">`async void` **by měla být použita pouze pro obslužné rutiny událostí.**</span><span class="sxs-lookup"><span data-stu-id="db601-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="db601-183">`async void` je jediným způsobem, jak povolit fungování asynchronních obslužných rutin událostí, protože události nemají návratové typy (proto nemohou používat `Task` a `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="db601-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="db601-184">Jakékoli jiné použití `async void` nedodržuje model klepnutí a může být náročné na použití, například:</span><span class="sxs-lookup"><span data-stu-id="db601-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="db601-185">Výjimky vyvolané v metodě `async void` nejde zachytit mimo tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="db601-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="db601-186">metody `async void` jsou velmi obtížné testovat.</span><span class="sxs-lookup"><span data-stu-id="db601-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="db601-187">`async void` metody mohou způsobit špatné vedlejší účinky, pokud volající neočekává, že budou Async.</span><span class="sxs-lookup"><span data-stu-id="db601-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="db601-188">**Při použití asynchronních výrazů lambda ve výrazech LINQ pečlivě běhouny**</span><span class="sxs-lookup"><span data-stu-id="db601-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="db601-189">Výrazy lambda v jazyce LINQ používají odložené provádění, což znamená, že kód může být spuštěn v okamžiku, kdy ho neočekáváte.</span><span class="sxs-lookup"><span data-stu-id="db601-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="db601-190">Zavedení blokujících úloh do této operace může snadno vést k zablokování, pokud není správně napsáno.</span><span class="sxs-lookup"><span data-stu-id="db601-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="db601-191">Kromě toho vnořování asynchronního kódu, jako je, může také ztížit důvod spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="db601-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="db601-192">Asynchronní a LINQ jsou výkonné, ale měly by být používány společně co nejdříve a jasně.</span><span class="sxs-lookup"><span data-stu-id="db601-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="db601-193">**Napsat kód, který čeká na úlohy bez blokování**</span><span class="sxs-lookup"><span data-stu-id="db601-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="db601-194">Blokování aktuálního vlákna jako prostředku pro čekání na dokončení úlohy může způsobit zablokování a blokované kontextová vlákna a může vyžadovat podstatně složitější zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="db601-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="db601-195">V následující tabulce najdete pokyny, jak se zabývat čekáním na úlohy neblokujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="db601-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="db601-196">Použít...</span><span class="sxs-lookup"><span data-stu-id="db601-196">Use this...</span></span> | <span data-ttu-id="db601-197">Místo...</span><span class="sxs-lookup"><span data-stu-id="db601-197">Instead of this...</span></span> | <span data-ttu-id="db601-198">Kdy to chcete udělat</span><span class="sxs-lookup"><span data-stu-id="db601-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="db601-199">`Task.Wait` nebo `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="db601-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="db601-200">Načítání výsledku úlohy na pozadí</span><span class="sxs-lookup"><span data-stu-id="db601-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="db601-201">Čeká se na dokončení všech úloh.</span><span class="sxs-lookup"><span data-stu-id="db601-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="db601-202">Čeká se na dokončení všech úloh.</span><span class="sxs-lookup"><span data-stu-id="db601-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="db601-203">Čekání na časový úsek</span><span class="sxs-lookup"><span data-stu-id="db601-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="db601-204">**Zápis méně stavového kódu**</span><span class="sxs-lookup"><span data-stu-id="db601-204">**Write less stateful code**</span></span>

<span data-ttu-id="db601-205">Nezávisí na stavu globálních objektů nebo provádění určitých metod.</span><span class="sxs-lookup"><span data-stu-id="db601-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="db601-206">Místo toho závisí pouze na vrácených hodnotách metod.</span><span class="sxs-lookup"><span data-stu-id="db601-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="db601-207">Proč?</span><span class="sxs-lookup"><span data-stu-id="db601-207">Why?</span></span>

* <span data-ttu-id="db601-208">Kód bude z důvodu snazší.</span><span class="sxs-lookup"><span data-stu-id="db601-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="db601-209">Testování kódu bude snazší.</span><span class="sxs-lookup"><span data-stu-id="db601-209">Code will be easier to test.</span></span>
* <span data-ttu-id="db601-210">Kombinování asynchronního a synchronního kódu je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="db601-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="db601-211">Konflikty časování se obvykle můžou vyvarovat zcela.</span><span class="sxs-lookup"><span data-stu-id="db601-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="db601-212">V závislosti na vrácených hodnotách je jednodušší koordinovat asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="db601-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="db601-213">(Bonus) funguje ve skutečnosti i při vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="db601-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="db601-214">Doporučeným cílem je dosáhnout úplné nebo téměř úplné [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="db601-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="db601-215">Výsledkem je mimořádně předvídatelný, testovatelné a udržovatelný základ kódu.</span><span class="sxs-lookup"><span data-stu-id="db601-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="db601-216">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="db601-216">Other Resources</span></span>

* <span data-ttu-id="db601-217">[Async-Depth](../standard/async-in-depth.md) poskytuje další informace o práci s úkoly.</span><span class="sxs-lookup"><span data-stu-id="db601-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="db601-218">Asynchronní programování s modifikátorem Async aC#operátoru Await ()</span><span class="sxs-lookup"><span data-stu-id="db601-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="db601-219">[Šest důležitých tipů pro Lucian Wischik pro Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) je vynikajícím prostředkem pro asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="db601-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
