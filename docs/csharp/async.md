---
title: 'Asynchronní programování - C #'
description: Další informace o asynchronním programovacím modelu na úrovni jazyka C# poskytovaného rozhraním .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 38d7c856e9a536db9ef26349175ad440a49f5fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713952"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="16745-103">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="16745-103">Asynchronous programming</span></span>

<span data-ttu-id="16745-104">Pokud máte nějaké potřeby vázané na vstupně-výstupní jednotky (například vyžádání dat ze sítě nebo přístup k databázi), budete chtít využít asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="16745-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="16745-105">Můžete mít také kód vázaný na procesor, jako je například provádění nákladného výpočtu, což je také dobrý scénář pro psaní asynchronního kódu.</span><span class="sxs-lookup"><span data-stu-id="16745-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="16745-106">C# má asynchronní programovací model na úrovni jazyka, který umožňuje snadné psaní asynchronního kódu bez nutnosti žonglovat s zpětná volání nebo v souladu s knihovnou, která podporuje asynchronii.</span><span class="sxs-lookup"><span data-stu-id="16745-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="16745-107">Z vyplývá, co je známé jako [task-based asynchronní vzor (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="16745-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="16745-108">Základní přehled asynchronního modelu</span><span class="sxs-lookup"><span data-stu-id="16745-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="16745-109">Jádrem asynchronního `Task` programování `Task<T>` je a objekty, které modelují asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="16745-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="16745-110">Jsou podporovány `async` a `await` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="16745-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="16745-111">Model je ve většině případů poměrně jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="16745-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="16745-112">Pro vstupně-výstupní kód, `await` operace, která `Task` `Task<T>` vrátí nebo `async` uvnitř metody.</span><span class="sxs-lookup"><span data-stu-id="16745-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="16745-113">Pro kód vázaný na `await` procesor, operace, která je `Task.Run` spuštěna na podprocesu na pozadí s metodou.</span><span class="sxs-lookup"><span data-stu-id="16745-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="16745-114">Klíčové `await` slovo je místo, kde se stane kouzlo.</span><span class="sxs-lookup"><span data-stu-id="16745-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="16745-115">Poskytuje řízení volajícímu metody, která `await`provedla a nakonec umožňuje uživatelské rozhraní reagovat nebo služby být elastické.</span><span class="sxs-lookup"><span data-stu-id="16745-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="16745-116">Existují i jiné způsoby, `async` jak `await` přistupovat k asynchronnímu kódu než a je uvedeno v článku TAP propojeném výše, ale tento dokument se od tohoto okamžiku zaměří na konstrukce na úrovni jazyka.</span><span class="sxs-lookup"><span data-stu-id="16745-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="16745-117">Příklad stahování dat z webové služby</span><span class="sxs-lookup"><span data-stu-id="16745-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="16745-118">Možná budete muset stáhnout některá data z webové služby při stisknutí tlačítka, ale nechcete blokovat vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="16745-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="16745-119">To může být provedeno jednoduše takto:</span><span class="sxs-lookup"><span data-stu-id="16745-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="16745-120">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="16745-120">And that’s it!</span></span> <span data-ttu-id="16745-121">Kód vyjadřuje záměr (stahování některých dat asynchronně) bez zabředne do interakce s task objekty.</span><span class="sxs-lookup"><span data-stu-id="16745-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="16745-122">Příklad vázaný na procesor: Provedení výpočtu pro hru</span><span class="sxs-lookup"><span data-stu-id="16745-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="16745-123">Řekněme, že píšete mobilní hru, kde stisknutí tlačítka může způsobit poškození mnoha nepřátelům na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="16745-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="16745-124">Provedení výpočtu poškození může být nákladné a dělat to na vlákně uživatelského rozhraní by se hra zdála být pozastavena při výpočtu!</span><span class="sxs-lookup"><span data-stu-id="16745-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="16745-125">Nejlepší způsob, jak to zvládnout, je spustit vlákno `Task.Run`na `await` pozadí, které provádí práci pomocí aplikace a jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="16745-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="16745-126">To umožní, aby se uI cítilo hladce, když se práce provádí.</span><span class="sxs-lookup"><span data-stu-id="16745-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="16745-127">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="16745-127">And that's it!</span></span>  <span data-ttu-id="16745-128">Tento kód čistě vyjadřuje záměr události kliknutí na tlačítko, nevyžaduje ruční správu vlákna na pozadí a činí tak neblokujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="16745-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="16745-129">Co se děje pod kryty</span><span class="sxs-lookup"><span data-stu-id="16745-129">What happens under the covers</span></span>

<span data-ttu-id="16745-130">Je tu spousta pohyblivých kusů, pokud jde o asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="16745-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="16745-131">Pokud jste zvědaví, co se děje `Task` pod `Task<T>`kryty a , pokladna [Async in-hloubkový](../standard/async-in-depth.md) článek pro více informací.</span><span class="sxs-lookup"><span data-stu-id="16745-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="16745-132">Na straně C# věcí kompilátor transformuje váš kód do stavu počítače, který `await` udržuje informace o věcech, jako je získávání spuštění při dosažení a obnovení provádění po dokončení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="16745-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="16745-133">Pro teoreticky nakloněné, toto je implementace [Promise Model asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="16745-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="16745-134">Klíčové kousky k pochopení</span><span class="sxs-lookup"><span data-stu-id="16745-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="16745-135">Asynchronní kód lze použít pro vstupně-výstupní a procesorvázaný kód, ale odlišně pro každý scénář.</span><span class="sxs-lookup"><span data-stu-id="16745-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="16745-136">Asynchronní `Task<T>` kód `Task`používá a , které jsou konstrukce používané k modelování práce se provádí na pozadí.</span><span class="sxs-lookup"><span data-stu-id="16745-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="16745-137">Klíčové `async` slovo změní metodu na asynchronní metodu, která vám umožní použít `await` klíčové slovo v jeho těle.</span><span class="sxs-lookup"><span data-stu-id="16745-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="16745-138">Při `await` použití klíčového slova pozastaví volající metodu a vrátí ovládací prvek zpět volajícímu, dokud nebude dokončena očekávaná úloha.</span><span class="sxs-lookup"><span data-stu-id="16745-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="16745-139">`await`lze použít pouze uvnitř asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="16745-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="16745-140">Rozpoznat práci vázanou na procesor a vstupně-výstupní svázané práce</span><span class="sxs-lookup"><span data-stu-id="16745-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="16745-141">První dva příklady této příručky ukázaly, jak můžete použít `async` a `await` pro práci vázanou na vstupně-výstupní a procesorovou.</span><span class="sxs-lookup"><span data-stu-id="16745-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="16745-142">Je to klíč, který můžete identifikovat, když úloha, kterou potřebujete udělat, je I/O-vázaná nebo vázaný na procesor, protože může výrazně ovlivnit výkon kódu a může potenciálně vést ke zneužití určitých konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="16745-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="16745-143">Zde jsou dvě otázky, které byste se měli zeptat, než napíšete nějaký kód:</span><span class="sxs-lookup"><span data-stu-id="16745-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="16745-144">Bude váš kód "čekání" na něco, jako jsou data z databáze?</span><span class="sxs-lookup"><span data-stu-id="16745-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="16745-145">Pokud je vaše odpověď "ano", pak je vaše práce **i/ O-vázána**.</span><span class="sxs-lookup"><span data-stu-id="16745-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="16745-146">Bude váš kód provádět velmi nákladné výpočty?</span><span class="sxs-lookup"><span data-stu-id="16745-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="16745-147">Pokud jste odpověděli "ano", pak je vaše práce **vázána na procesor**.</span><span class="sxs-lookup"><span data-stu-id="16745-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="16745-148">Pokud je práce, kterou **máte, vázána na vstupně-výstupní ,** použijte `async` `await` a *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="16745-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="16745-149">*Neměli* byste používat paralelní knihovnu úloh.</span><span class="sxs-lookup"><span data-stu-id="16745-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="16745-150">Důvod je popsán v [článku Async in Depth](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="16745-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="16745-151">Pokud je práce, kterou **máte, vázána na** `async` procesor `await` a záleží vám na odezvě, použijte a ale zplodíte práci na jiném vlákně *s* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="16745-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="16745-152">Pokud je práce vhodná pro souběžnost a paralelismus, měli byste také zvážit použití [paralelní knihovny úloh](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="16745-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="16745-153">Kromě toho byste měli vždy měřit provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="16745-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="16745-154">Například můžete najít sami sebe v situaci, kdy vaše práce vázaná na procesor není dostatečně nákladné ve srovnání s režií přepnutí kontextu při multithreading.</span><span class="sxs-lookup"><span data-stu-id="16745-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="16745-155">Každá volba má svůj kompromis, a měli byste si vybrat správný kompromis pro vaši situaci.</span><span class="sxs-lookup"><span data-stu-id="16745-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="16745-156">Další příklady</span><span class="sxs-lookup"><span data-stu-id="16745-156">More Examples</span></span>

<span data-ttu-id="16745-157">Následující příklady ukazují různé způsoby, jak můžete psát asynchronní kód v C#.</span><span class="sxs-lookup"><span data-stu-id="16745-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="16745-158">Pokrývají několik různých scénářů, na které se můžete sejít.</span><span class="sxs-lookup"><span data-stu-id="16745-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="16745-159">Extrahování dat ze sítě</span><span class="sxs-lookup"><span data-stu-id="16745-159">Extracting Data from a Network</span></span>

<span data-ttu-id="16745-160">Tento úryvek stáhne HTML z domovské stránky v [www.dotnetfoundation.org](https://www.dotnetfoundation.org) a spočítá, kolikrát se řetězec ".NET" vyskytuje v HTML.</span><span class="sxs-lookup"><span data-stu-id="16745-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="16745-161">Používá ASP.NET MVC k definování metody webového kontroléru, která provádí tento úkol a vrací číslo.</span><span class="sxs-lookup"><span data-stu-id="16745-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="16745-162">Pokud plánujete analýzu HTML v produkčním kódu, nepoužívejte regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="16745-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="16745-163">Místo toho použijte knihovnu analýzy.</span><span class="sxs-lookup"><span data-stu-id="16745-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="16745-164">Tady je stejný scénář napsaný pro univerzální aplikaci pro Windows, která provádí stejnou úlohu při stisknutí tlačítka:</span><span class="sxs-lookup"><span data-stu-id="16745-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="16745-165">Čekání na dokončení více úkolů</span><span class="sxs-lookup"><span data-stu-id="16745-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="16745-166">Můžete se ocitnout v situaci, kdy je třeba načíst více kusů dat současně.</span><span class="sxs-lookup"><span data-stu-id="16745-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="16745-167">Rozhraní `Task` API obsahuje `Task.WhenAll` dvě `Task.WhenAny` metody, které umožňují psát asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="16745-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="16745-168">Tento příklad ukazuje, `User` jak můžete uchopit data pro sadu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="16745-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="16745-169">Zde je další způsob, jak napsat to trochu stručněji, pomocí LINQ:</span><span class="sxs-lookup"><span data-stu-id="16745-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="16745-170">I když je méně kódu, dávejte pozor při míchání LINQ s asynchronním kódem.</span><span class="sxs-lookup"><span data-stu-id="16745-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="16745-171">Protože LINQ používá odložené (opožděné) spuštění, asynchronní volání `foreach()` nedojde okamžitě jako ve smyčce, pokud vynutíte generované sekvence iterovat s voláním `.ToList()` nebo `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="16745-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="16745-172">Důležité informace a rady</span><span class="sxs-lookup"><span data-stu-id="16745-172">Important Info and Advice</span></span>

<span data-ttu-id="16745-173">Přestože asynchronní programování je poměrně jednoduché, existují některé podrobnosti, které je třeba mít na paměti, které mohou zabránit neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="16745-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="16745-174">`async`**metody musí mít** `await` **klíčové slovo ve svém těle, nebo se nikdy výnos!**</span><span class="sxs-lookup"><span data-stu-id="16745-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="16745-175">To je důležité mít na paměti.</span><span class="sxs-lookup"><span data-stu-id="16745-175">This is important to keep in mind.</span></span>  <span data-ttu-id="16745-176">Pokud `await` není použit v těle `async` metody, kompilátor Jazyka C# vygeneruje upozornění, ale kód bude kompilovat a spouštět, jako by to byla normální metoda.</span><span class="sxs-lookup"><span data-stu-id="16745-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="16745-177">Všimněte si, že by to také neuvěřitelně neefektivní, jako stavový počítač generovaný kompilátorem Jazyka C# pro asynchronní metodu by nebylo dosaženo nic.</span><span class="sxs-lookup"><span data-stu-id="16745-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="16745-178">**Měli byste přidat "Async" jako příponu každého názvu asynchronní metody, kterou napíšete.**</span><span class="sxs-lookup"><span data-stu-id="16745-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="16745-179">Toto je konvence používaná v rozhraní .NET pro snadněji rozlišovací synchronní a asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="16745-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="16745-180">Všimněte si, že některé metody, které nejsou explicitně volány vaším kódem (například obslužné rutiny událostí nebo metody webového kontroleru) nemusí nutně platit.</span><span class="sxs-lookup"><span data-stu-id="16745-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="16745-181">Vzhledem k tomu, že tyto nejsou explicitně volány vaším kódem, explicitní o jejich pojmenování není tak důležité.</span><span class="sxs-lookup"><span data-stu-id="16745-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="16745-182">`async void`**by měl být použit pouze pro obslužné rutiny událostí.**</span><span class="sxs-lookup"><span data-stu-id="16745-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="16745-183">`async void`je jediný způsob, jak povolit zpracování obslužných rutin asynchronních událostí, `Task` `Task<T>`protože události nemají návratové typy (proto nelze použít a ).</span><span class="sxs-lookup"><span data-stu-id="16745-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="16745-184">Jakékoli jiné `async void` použití modelu TAP neodpovídá modelu TAP a může být náročné na použití, například:</span><span class="sxs-lookup"><span data-stu-id="16745-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="16745-185">Výjimky vyzdvižené v metodě `async void` nelze zachytit mimo tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="16745-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="16745-186">`async void`metody jsou velmi obtížné testovat.</span><span class="sxs-lookup"><span data-stu-id="16745-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="16745-187">`async void`metody mohou způsobit špatné vedlejší účinky, pokud volající neočekává, že budou asynchronní.</span><span class="sxs-lookup"><span data-stu-id="16745-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="16745-188">**Při použití asynchronních lambdů ve výrazech LINQ opatrně**</span><span class="sxs-lookup"><span data-stu-id="16745-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="16745-189">Lambda výrazy v LINQ použít odložené spuštění, což znamená, že kód může skončit provádění v době, kdy nejste očekávali, že.</span><span class="sxs-lookup"><span data-stu-id="16745-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="16745-190">Zavedení blokování úloh do tohoto může snadno vést k zablokování, pokud není napsánsprávně.</span><span class="sxs-lookup"><span data-stu-id="16745-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="16745-191">Navíc vnoření asynchronního kódu, jako je tento může také ztížit důvod o provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="16745-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="16745-192">Async a LINQ jsou silné, ale měly by být používány společně co nejpečlivěji a nejjasněji.</span><span class="sxs-lookup"><span data-stu-id="16745-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="16745-193">**Napište kód, který čeká úkoly neblokujícím způsobem**</span><span class="sxs-lookup"><span data-stu-id="16745-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="16745-194">Blokování aktuální vlákno jako prostředek čekání na task k dokončení může mít za následek zablokování a blokované podprocesů kontextu a může vyžadovat výrazně složitější zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="16745-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="16745-195">Následující tabulka obsahuje pokyny, jak se vypořádat s čekáním na úkoly neblokujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="16745-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="16745-196">Postup...</span><span class="sxs-lookup"><span data-stu-id="16745-196">Use this...</span></span> | <span data-ttu-id="16745-197">Místo tohohle...</span><span class="sxs-lookup"><span data-stu-id="16745-197">Instead of this...</span></span> | <span data-ttu-id="16745-198">Když si to přejí</span><span class="sxs-lookup"><span data-stu-id="16745-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="16745-199">`Task.Wait` nebo `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="16745-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="16745-200">Načítání výsledku úlohy na pozadí</span><span class="sxs-lookup"><span data-stu-id="16745-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="16745-201">Čekání na dokončení jakékoli úlohy</span><span class="sxs-lookup"><span data-stu-id="16745-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="16745-202">Čekání na dokončení všech úkolů</span><span class="sxs-lookup"><span data-stu-id="16745-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="16745-203">Čekání na určitou dobu</span><span class="sxs-lookup"><span data-stu-id="16745-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="16745-204">**Zápis méně stavového kódu**</span><span class="sxs-lookup"><span data-stu-id="16745-204">**Write less stateful code**</span></span>

<span data-ttu-id="16745-205">Nezávisí na stavu globálních objektů nebo provádění určitých metod.</span><span class="sxs-lookup"><span data-stu-id="16745-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="16745-206">Místo toho závisí pouze na vrácené hodnoty metod.</span><span class="sxs-lookup"><span data-stu-id="16745-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="16745-207">Proč?</span><span class="sxs-lookup"><span data-stu-id="16745-207">Why?</span></span>

* <span data-ttu-id="16745-208">Kód bude snazší důvod.</span><span class="sxs-lookup"><span data-stu-id="16745-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="16745-209">Kód bude snazší testovat.</span><span class="sxs-lookup"><span data-stu-id="16745-209">Code will be easier to test.</span></span>
* <span data-ttu-id="16745-210">Míchání asynchronního a synchronního kódu je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="16745-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="16745-211">Sporičné podmínky lze obvykle zcela vyhnout.</span><span class="sxs-lookup"><span data-stu-id="16745-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="16745-212">V závislosti na návratové hodnoty umožňuje koordinaci asynchronní kód jednoduché.</span><span class="sxs-lookup"><span data-stu-id="16745-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="16745-213">(Bonus) to funguje opravdu dobře s závislostí injekce.</span><span class="sxs-lookup"><span data-stu-id="16745-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="16745-214">Doporučeným cílem je dosáhnout úplné nebo téměř úplné [referenční průhlednosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="16745-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="16745-215">To bude mít za následek velmi předvídatelné, testovatelné a udržovatelné codebase.</span><span class="sxs-lookup"><span data-stu-id="16745-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="16745-216">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="16745-216">Other Resources</span></span>

* <span data-ttu-id="16745-217">[Asynchronní hloubka](../standard/async-in-depth.md) poskytuje další informace o tom, jak úkoly fungují.</span><span class="sxs-lookup"><span data-stu-id="16745-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="16745-218">Asynchronní programování s asynchronní a čekat (C#)</span><span class="sxs-lookup"><span data-stu-id="16745-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="16745-219">Lucian Wischik šest [základních tipů pro Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) jsou skvělý zdroj pro asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="16745-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
