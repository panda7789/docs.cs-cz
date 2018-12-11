---
title: Asynchronní programování
description: Další informace o jazyce C# úrovni jazyka asynchronní programovací model poskytované .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 12ecadb3fa3c6760af4884626f68b47ead2754d5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126494"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="b1872-103">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="b1872-103">Asynchronous programming</span></span>

<span data-ttu-id="b1872-104">Pokud máte jakékoli vstupně-výstupní požadavky (například požadavek na data ze sítě nebo přístup k databázi), budete chtít využívat asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="b1872-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="b1872-105">Můžete mít také vázané na procesor kódu, jako je například provádění nákladné výpočtu, která je také vhodné scénář pro psaní asynchronního kódu.</span><span class="sxs-lookup"><span data-stu-id="b1872-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="b1872-106">C# má úroveň jazyka asynchronní programovací model, který umožňuje snadno psaní asynchronního kódu bez nutnosti přehlednější zpětná volání nebo do knihovny, která podporuje asynchronii v souladu.</span><span class="sxs-lookup"><span data-stu-id="b1872-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="b1872-107">Vyplývá, která se označuje jako [úkolově orientovanou asynchronní vzor (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="b1872-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="b1872-108">Základní přehled asynchronní Model</span><span class="sxs-lookup"><span data-stu-id="b1872-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="b1872-109">Základem asynchronního programování je `Task` a `Task<T>` objekty, které model asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="b1872-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="b1872-110">Jsou podporovány `async` a `await` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="b1872-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="b1872-111">Model je ve většině případů poměrně jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="b1872-111">The model is fairly simple in most cases:</span></span> 

<span data-ttu-id="b1872-112">Pro vstupně-výstupní kód můžete `await` operace, která vrátí `Task` nebo `Task<T>` uvnitř `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="b1872-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="b1872-113">Pro kód vázané na procesor je `await` operace, která je spuštěna ve vlákně na pozadí s `Task.Run` metody.</span><span class="sxs-lookup"><span data-stu-id="b1872-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="b1872-114">`await` – Klíčové slovo je, kde se to všechno děje.</span><span class="sxs-lookup"><span data-stu-id="b1872-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="b1872-115">Ovládací prvek bude vrácen volajícímu metody, která provádí `await`, a nakonec umožňuje být interaktivní uživatelské rozhraní nebo službu pružný.</span><span class="sxs-lookup"><span data-stu-id="b1872-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="b1872-116">Existují jiné způsoby, jak přístup asynchronní kód než `async` a `await` uvedených v článku TAP propojené výše, ale tento dokument se zaměřuje na úrovni jazyka konstrukce od této chvíle dál.</span><span class="sxs-lookup"><span data-stu-id="b1872-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="b1872-117">Vstupně-výstupní příklad: Stahování dat z webové služby</span><span class="sxs-lookup"><span data-stu-id="b1872-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="b1872-118">Budete muset stáhnout data z webové služby při stisknutí tlačítka, ale nechcete, aby k blokování vlákna uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b1872-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="b1872-119">To lze provést jednoduše takto:</span><span class="sxs-lookup"><span data-stu-id="b1872-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="b1872-120">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="b1872-120">And that’s it!</span></span> <span data-ttu-id="b1872-121">Kód vyjadřují záměr (stahuje se některá data asynchronně) bez získání energií v práci s objekty úloh.</span><span class="sxs-lookup"><span data-stu-id="b1872-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="b1872-122">Příklad vázané na procesor: Výpočty pro hru</span><span class="sxs-lookup"><span data-stu-id="b1872-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="b1872-123">Dejme tomu, že píšete mobilní hru, ve kterém stisknutím tlačítka může způsobit poškození na mnoho nepřátel na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="b1872-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="b1872-124">Výpočty poškození může být nákladné a dělat na vlákně UI by vytvořit hru zobrazí pozastavit, jak se provádí výpočet!</span><span class="sxs-lookup"><span data-stu-id="b1872-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="b1872-125">Nejlepší způsob, jak se o to postarají je spuštění vlákna na pozadí, který provádí práci pomocí `Task.Run`, a `await` jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="b1872-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="b1872-126">To vám umožní uživatelského rozhraní pocit smooth, jak se provádí práci.</span><span class="sxs-lookup"><span data-stu-id="b1872-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="b1872-127">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="b1872-127">And that's it!</span></span>  <span data-ttu-id="b1872-128">Tento kód čistě vyjadřují záměr kliknutím na tlačítko na událost, nevyžaduje ruční správu vlákna na pozadí a dělá to tak neblokující.</span><span class="sxs-lookup"><span data-stu-id="b1872-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="b1872-129">Co se stane, že na pozadí</span><span class="sxs-lookup"><span data-stu-id="b1872-129">What happens under the covers</span></span>

<span data-ttu-id="b1872-130">Je hodně přesouvání položek, kde se týká asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="b1872-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="b1872-131">Pokud vás to zajímá o co se děje na pozadí `Task` a `Task<T>`, rezervace [asynchronní podrobné](../standard/async-in-depth.md) najdete další informace.</span><span class="sxs-lookup"><span data-stu-id="b1872-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="b1872-132">V C# straně věcí, kompilátor transformuje na stavový počítač, který uchovává informace o věci, jako je vracení provádění kódu při `await` je dosaženo a obnovení provádění po dokončení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b1872-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="b1872-133">Pro teoreticky sklon, toto je implementace [Promise modelu asynchronii](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="b1872-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="b1872-134">Důležité porozumět</span><span class="sxs-lookup"><span data-stu-id="b1872-134">Key Pieces to Understand</span></span>

*   <span data-ttu-id="b1872-135">Asynchronní kód můžete použít pro vstupně-výstupní a vázané na procesor kódu, ale jinak pro jednotlivé scénáře.</span><span class="sxs-lookup"><span data-stu-id="b1872-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
*   <span data-ttu-id="b1872-136">Používá asynchronní kód `Task<T>` a `Task`, které jsou objektů, které používá model práce na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b1872-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="b1872-137">`async` – Klíčové slovo změní metodu na asynchronní metodu, která umožňuje používat `await` – klíčové slovo v těle.</span><span class="sxs-lookup"><span data-stu-id="b1872-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
*   <span data-ttu-id="b1872-138">Když `await` – klíčové slovo se použijí, volání metody pozastaví a vrací řízení volajícímu zpět, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="b1872-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
*   <span data-ttu-id="b1872-139">`await` jde použít jenom v asynchronní metodě.</span><span class="sxs-lookup"><span data-stu-id="b1872-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="b1872-140">Rozpoznat vázané na procesor a vstupně-výstupní práce</span><span class="sxs-lookup"><span data-stu-id="b1872-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="b1872-141">První dva příklady Tento průvodce vám ukázal, jak můžete `async` a `await` pro vstupně-výstupní a vázané na procesor práce.</span><span class="sxs-lookup"><span data-stu-id="b1872-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="b1872-142">Jeho klíč, který vám usnadní zjišťování se úlohy, je třeba provést je vstupně-výstupní nebo vázané na procesor, protože může výrazně ovlivnit výkon kódu a může potenciálně vést k zneužití určité vytvoří.</span><span class="sxs-lookup"><span data-stu-id="b1872-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="b1872-143">Tady jsou dva otázek, na které je třeba požádat předtím, než začnete psát kód:</span><span class="sxs-lookup"><span data-stu-id="b1872-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="b1872-144">Bude kód "čekat" něco, jako jsou data z databáze?</span><span class="sxs-lookup"><span data-stu-id="b1872-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="b1872-145">Pokud vaše odpověď je "Ano", pak je práce **vstupně-výstupní**.</span><span class="sxs-lookup"><span data-stu-id="b1872-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="b1872-146">Bude kód provádět velmi náročné výpočty?</span><span class="sxs-lookup"><span data-stu-id="b1872-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="b1872-147">Pokud jste odpověděli "Ano", pak je práce **vázané na procesor**.</span><span class="sxs-lookup"><span data-stu-id="b1872-147">If you answered "yes", then your work is **CPU-bound**.</span></span>
    
<span data-ttu-id="b1872-148">Pokud je pracovní máte **vstupně-výstupní**, použijte `async` a `await` *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="b1872-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="b1872-149">Můžete *by neměla* použít Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="b1872-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="b1872-150">Důvodem je popsaný v [asynchronní v článku hloubky](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="b1872-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="b1872-151">Pokud je pracovní máte **vázané na procesor** a péči o rychlosti odezvy, použijte `async` a `await` ale nejde vytvořit podřízený práce vypnout v jiném vlákně *s* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="b1872-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="b1872-152">Pokud práce je vhodný pro souběžnost a paralelismu, měli byste také zvážit použití [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="b1872-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="b1872-153">Kromě toho by měla vždy měření provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="b1872-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="b1872-154">Například může být pro vás sami v situaci, kdy není nákladné práce vázané na procesor dostatečně ve srovnání s režií přepnutí kontextu při multithreadingu.</span><span class="sxs-lookup"><span data-stu-id="b1872-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="b1872-155">Každý volbou jeho kompromis, a měli byste vybrat správné kompromis pro vaše konkrétní potřeby.</span><span class="sxs-lookup"><span data-stu-id="b1872-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="b1872-156">Další příklady</span><span class="sxs-lookup"><span data-stu-id="b1872-156">More Examples</span></span>

<span data-ttu-id="b1872-157">Následující příklady znázorňují různé způsoby, které můžete psát asynchronní kód v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="b1872-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="b1872-158">Několik různých scénářů, které můžete narazit na pokrývají.</span><span class="sxs-lookup"><span data-stu-id="b1872-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="b1872-159">Extrahování dat ze sítě</span><span class="sxs-lookup"><span data-stu-id="b1872-159">Extracting Data from a Network</span></span>

<span data-ttu-id="b1872-160">Tento fragment kódu HTML z domovské stránky na soubory ke stažení [www.dotnetfoundation.org](https://www.dotnetfoundation.org) a počet, kolikrát řetězec ".NET" vyvolá se v kódu HTML.</span><span class="sxs-lookup"><span data-stu-id="b1872-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="b1872-161">ASP.NET MVC používá k definování webové metody kontroleru, která tuto úlohu, vrací číslo.</span><span class="sxs-lookup"><span data-stu-id="b1872-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="b1872-162">Pokud máte v úmyslu provádět analýza v produkčním kódu HTML, nepoužívejte regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="b1872-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="b1872-163">Místo toho použijte knihovnu analýzy.</span><span class="sxs-lookup"><span data-stu-id="b1872-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="b1872-164">Zde je stejný scénář napsané pro univerzální aplikace pro Windows, který provádí stejnou úlohu, když se stiskne tlačítko:</span><span class="sxs-lookup"><span data-stu-id="b1872-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="b1872-165">Čekání na dokončení více úloh</span><span class="sxs-lookup"><span data-stu-id="b1872-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="b1872-166">Může být pro vás sami v situaci, kde je potřeba načíst data na více místech současně.</span><span class="sxs-lookup"><span data-stu-id="b1872-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="b1872-167">`Task` Rozhraní API obsahuje dvě metody `Task.WhenAll` a `Task.WhenAny` který umožňuje psát asynchronní kód, který provádí čekání bez blokování na víc úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b1872-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="b1872-168">Tento příklad ukazuje, jak může vzít `User` data pro sadu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="b1872-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="b1872-169">Tady je další způsob, jak to trochu více stručně zapsat pomocí jazyka LINQ:</span><span class="sxs-lookup"><span data-stu-id="b1872-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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
<span data-ttu-id="b1872-170">I když je tolik kódu, aby se postaral při kombinování LINQ s asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="b1872-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="b1872-171">Vzhledem k tomu LINQ používá odložené provedení (opožděné), asynchronní volání se neprovede okamžitě stejně jako `foreach()` smyčky není-li vynutit generovaného sekvenčního k iteraci pomocí volání `.ToList()` nebo `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="b1872-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="b1872-172">Důležité informace a Rady</span><span class="sxs-lookup"><span data-stu-id="b1872-172">Important Info and Advice</span></span>

<span data-ttu-id="b1872-173">Přestože je poměrně přímočarý asynchronní programování, existují některé podrobnosti potřeba mít na paměti, což může zabránit neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="b1872-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

*  <span data-ttu-id="b1872-174">`async` **metody musí mít** `await` **– klíčové slovo v jejich obsahu nebo se nikdy yield!**</span><span class="sxs-lookup"><span data-stu-id="b1872-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="b1872-175">To je důležité si pamatovat.</span><span class="sxs-lookup"><span data-stu-id="b1872-175">This is important to keep in mind.</span></span>  <span data-ttu-id="b1872-176">Pokud `await` není použit v těle `async` metoda, C# kompilátor bude generovat upozornění, ale bude kód zkompilovat a spustit jako by šlo normální metody.</span><span class="sxs-lookup"><span data-stu-id="b1872-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="b1872-177">Pamatujte, že to by také být velmi neefektivní, jako by být provádění stavového stroje generovaný kompilátorem jazyka C# pro asynchronní metody, cokoli.</span><span class="sxs-lookup"><span data-stu-id="b1872-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

*   <span data-ttu-id="b1872-178">**Jako přípona názvu každý asynchronní metoda, který napíšete, měli byste přidat "Async".**</span><span class="sxs-lookup"><span data-stu-id="b1872-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="b1872-179">Toto je konvence v rozhraní .NET pro snadněji rozlišit synchronní a asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="b1872-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="b1872-180">Všimněte si, že některé metody, které nejsou explicitně volána ve vašem kódu (například obslužné rutiny událostí nebo metody kontroleru webového) není nemusí nezbytně vztahovat.</span><span class="sxs-lookup"><span data-stu-id="b1872-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="b1872-181">Protože tyto nejsou volány explicitně pomocí kódu, se explicitní o jejich pojmenování není důležité.</span><span class="sxs-lookup"><span data-stu-id="b1872-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

*   <span data-ttu-id="b1872-182">`async void` **by měla sloužit pouze pro obslužné rutiny událostí.**</span><span class="sxs-lookup"><span data-stu-id="b1872-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="b1872-183">`async void` je jediný způsob, jak povolit asynchronní obslužné rutiny pracovat, protože události nemají návratové typy (tedy nemůže provádět využívání `Task` a `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="b1872-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="b1872-184">Jakékoli další použití `async void` nedodržuje vzoru TAP a může být náročné, pokud chcete použít, jako například:</span><span class="sxs-lookup"><span data-stu-id="b1872-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  *   <span data-ttu-id="b1872-185">Výjimky vyvolané `async void` metoda nemůže být zachycena mimo tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="b1872-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
  *   <span data-ttu-id="b1872-186">`async void` metody jsou velmi obtížné testování.</span><span class="sxs-lookup"><span data-stu-id="b1872-186">`async void` methods are very difficult to test.</span></span>
  *   <span data-ttu-id="b1872-187">`async void` metod může způsobit špatné vedlejší účinky, pokud volající není očekáván je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="b1872-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

*   <span data-ttu-id="b1872-188">**Pečlivě běhounu při použití asynchronní výrazy lambda v LINQ – výrazy**</span><span class="sxs-lookup"><span data-stu-id="b1872-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="b1872-189">Výrazy lambda v jazyce LINQ pomocí odloženého provedení, můžou být nakonec význam kódu v době, kdy, jestliže neočekáváte na provádění.</span><span class="sxs-lookup"><span data-stu-id="b1872-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="b1872-190">Po zavedení služby blokování úloh do tohoto může snadno způsobit zablokování Pokud nezapíše se správně.</span><span class="sxs-lookup"><span data-stu-id="b1872-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="b1872-191">Kromě toho vnoření asynchronní kód tímto způsobem můžete také to ztížit argumentovat o provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="b1872-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="b1872-192">Asynchronní a LINQ jsou velmi výkonné, ale má být použit společně jako pečlivě a co je to možné.</span><span class="sxs-lookup"><span data-stu-id="b1872-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

*   <span data-ttu-id="b1872-193">**Napsat kód, který čeká na úkoly způsobem neblokující**</span><span class="sxs-lookup"><span data-stu-id="b1872-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="b1872-194">Blokuje aktuální vlákno jako prostředek k čekání na dokončení úkolu může způsobit zablokování a konflikty blokované kontextu vlákna a můžou vyžadovat, aby výrazně složitějších zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="b1872-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="b1872-195">Následující tabulka obsahuje pokyny k řešení problémů s čekání na neblokující způsobem úkolů:</span><span class="sxs-lookup"><span data-stu-id="b1872-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="b1872-196">Použijte tento...</span><span class="sxs-lookup"><span data-stu-id="b1872-196">Use this...</span></span> | <span data-ttu-id="b1872-197">Místo to...</span><span class="sxs-lookup"><span data-stu-id="b1872-197">Instead of this...</span></span> | <span data-ttu-id="b1872-198">Když chce udělat</span><span class="sxs-lookup"><span data-stu-id="b1872-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="b1872-199">`Task.Wait` Nebo `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="b1872-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="b1872-200">Načítání výsledků úlohy na pozadí</span><span class="sxs-lookup"><span data-stu-id="b1872-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="b1872-201">Čekání na dokončení úkolu</span><span class="sxs-lookup"><span data-stu-id="b1872-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="b1872-202">Čekání na dokončení všech úloh</span><span class="sxs-lookup"><span data-stu-id="b1872-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="b1872-203">Čekání na časový úsek</span><span class="sxs-lookup"><span data-stu-id="b1872-203">Waiting for a period of time</span></span> |

*   <span data-ttu-id="b1872-204">**Zápis méně stavový kód**</span><span class="sxs-lookup"><span data-stu-id="b1872-204">**Write less stateful code**</span></span>

<span data-ttu-id="b1872-205">Nejsou závislé na stavu globálních objektů nebo provádění některých metod.</span><span class="sxs-lookup"><span data-stu-id="b1872-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="b1872-206">Místo toho záviset pouze na návratové hodnoty metod.</span><span class="sxs-lookup"><span data-stu-id="b1872-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="b1872-207">Proč?</span><span class="sxs-lookup"><span data-stu-id="b1872-207">Why?</span></span>

  *   <span data-ttu-id="b1872-208">Kód bude jednodušší argumentovat o.</span><span class="sxs-lookup"><span data-stu-id="b1872-208">Code will be easier to reason about.</span></span>
  *   <span data-ttu-id="b1872-209">Kód bude snazší testování.</span><span class="sxs-lookup"><span data-stu-id="b1872-209">Code will be easier to test.</span></span>
  *   <span data-ttu-id="b1872-210">Kombinace asynchronní a synchronní kód je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="b1872-210">Mixing async and synchronous code is far simpler.</span></span>
  *   <span data-ttu-id="b1872-211">Ke konfliktům časování obvykle vyhnout úplně.</span><span class="sxs-lookup"><span data-stu-id="b1872-211">Race conditions can typically be avoided altogether.</span></span>
  *   <span data-ttu-id="b1872-212">V závislosti na návratové hodnoty zjednodušuje koordinační asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="b1872-212">Depending on return values makes coordinating async code simple.</span></span>
  *   <span data-ttu-id="b1872-213">(Bonusové) je velice dobře funguje pro vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="b1872-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="b1872-214">Doporučené cílem je dosáhnout úplné nebo téměř úplnou [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="b1872-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="b1872-215">To způsobí velmi předvídatelné, možností intenzivního testování a udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="b1872-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b1872-216">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b1872-216">Other Resources</span></span>

* <span data-ttu-id="b1872-217">[Asynchronní podrobné](../standard/async-in-depth.md) poskytuje další informace o tom, jak pracují úkoly.</span><span class="sxs-lookup"><span data-stu-id="b1872-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="b1872-218">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="b1872-218">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)
* <span data-ttu-id="b1872-219">Lucian Wischik [šest důležité tipy pro asynchronní](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) jsou vynikající prostředku pro asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="b1872-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
