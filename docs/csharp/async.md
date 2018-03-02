---
title: "Asynchronní programování"
description: "Další informace o C# úroveň jazyka asynchronní programovací model poskytované .NET Core."
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: d2633bf18fa32adc58dd3f5a2388d11010672da8
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="asynchronous-programming"></a><span data-ttu-id="5bfc5-104">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="5bfc5-104">Asynchronous programming</span></span>

<span data-ttu-id="5bfc5-105">Pokud máte všechny požadavky I/čítači (například požadavek na data v síti nebo přístup k databázi), budete chtít využívat asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-105">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="5bfc5-106">Můžete mít také kód vázané na procesor, například při provádění nákladné výpočtu, která je také funkční scénář pro psaní kódu asynchronní.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-106">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="5bfc5-107">C# má úroveň jazyka asynchronní programovací model, který umožňuje snadno psaní kódu asynchronní bez nutnosti přehlednější zpětná volání nebo do knihovny, která podporuje asynchrony v souladu.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-107">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="5bfc5-108">Vyplývá z toho, která se označuje jako [založený na úlohách asynchronní vzor (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).</span><span class="sxs-lookup"><span data-stu-id="5bfc5-108">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="5bfc5-109">Základní přehled asynchronní modelu</span><span class="sxs-lookup"><span data-stu-id="5bfc5-109">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="5bfc5-110">Základní programování asynchronních jsou `Task` a `Task<T>` objekty, které model asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-110">The core of async programming are the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="5bfc5-111">Jsou podporovány `async` a `await` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-111">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="5bfc5-112">Model je docela jednoduché ve většině případů:</span><span class="sxs-lookup"><span data-stu-id="5bfc5-112">The model is fairly simple in most cases:</span></span> 

<span data-ttu-id="5bfc5-113">Pro kód I/čítači můžete `await` operace, která vrátí hodnotu `Task` nebo `Task<T>` uvnitř `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-113">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="5bfc5-114">Pro kód vázané na procesor můžete `await` operace, který se spouští na vlákna na pozadí s `Task.Run` metoda.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-114">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="5bfc5-115">`await` – Klíčové slovo je, kde se stane magic.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-115">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="5bfc5-116">Ovládací prvek bude vrácen volajícímu metody, která provádí `await`, a nakonec umožňuje uživatelského rozhraní jako odpovídající nebo elastické služby.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-116">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="5bfc5-117">Existují jiné způsoby kódu asynchronní metodu než `async` a `await` uvedených v článku klepněte na uvedený výše, ale tento dokument se soustředí na úrovni jazykové konstrukty od tohoto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-117">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="5bfc5-118">Příklad I/čítači: stahování dat z webové služby</span><span class="sxs-lookup"><span data-stu-id="5bfc5-118">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="5bfc5-119">Budete muset stáhnout některá data z webové služby, při stisknutí tlačítka, ale nechcete, aby k blokování vlákna uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-119">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="5bfc5-120">Dosáhnete jednoduše takto:</span><span class="sxs-lookup"><span data-stu-id="5bfc5-120">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="5bfc5-121">A je to!</span><span class="sxs-lookup"><span data-stu-id="5bfc5-121">And that’s it!</span></span> <span data-ttu-id="5bfc5-122">Kód vyjadřoval záměr (asynchronně stahování některá data), aniž zabřednete v interakci s objekty úloh.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-122">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="5bfc5-123">Příklad vázané na procesor: Provádění výpočtu pro hry</span><span class="sxs-lookup"><span data-stu-id="5bfc5-123">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="5bfc5-124">Řekněme, že píšete mobilní hru kde stisknutím tlačítka může způsobit poškození v mnoha nepřátel na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-124">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="5bfc5-125">Provádění výpočtu poškození může být náročná, a to ve vlákně UI by proveďte hra, zobrazí se pozastavit, jak se provádí výpočet!</span><span class="sxs-lookup"><span data-stu-id="5bfc5-125">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="5bfc5-126">Nejlepší způsob, jak to se dá začít vlákna na pozadí, která zajišťuje pomocí pracovní `Task.Run`, a `await` její výsledek.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-126">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="5bfc5-127">To vám umožní Uživatelském rozhraní působí smooth, jako práce.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-127">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="5bfc5-128">A je to!</span><span class="sxs-lookup"><span data-stu-id="5bfc5-128">And that's it!</span></span>  <span data-ttu-id="5bfc5-129">Tento kód ještě jednou vyjadřoval záměr události kliknutí na tlačítko, není třeba ručně Správa vlákna na pozadí a učiní tak způsobem neblokující.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-129">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="5bfc5-130">Co se stane skrytě</span><span class="sxs-lookup"><span data-stu-id="5bfc5-130">What happens under the covers</span></span>

<span data-ttu-id="5bfc5-131">Existuje mnoho přesunutí částí, kde jsou problémem asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-131">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="5bfc5-132">Pokud se chcete zjistit, co se děje pod zahrnuje z `Task` a `Task<T>`, najdete v článku věnovaném [asynchronní podrobný](../standard/async-in-depth.md) Další informace najdete v článku.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-132">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="5bfc5-133">Na C# straně věcí, kompilátor transformuje na stavu počítače, která uchovává informace o takové věci, jako je spuštění kódu při `await` se dosáhlo maximálního a opětovné spuštění, až se dokončí úlohu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-133">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="5bfc5-134">U teoreticky sklon, je to implementace [Promise Model asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="5bfc5-134">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="5bfc5-135">Důležité pochopit</span><span class="sxs-lookup"><span data-stu-id="5bfc5-135">Key Pieces to Understand</span></span>

*   <span data-ttu-id="5bfc5-136">Asynchronní kódu je možné kódu I/čítači a vázané na procesor, ale jinak pro jednotlivé scénáře.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-136">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
*   <span data-ttu-id="5bfc5-137">Asynchronní kód používá `Task<T>` a `Task`, které jsou konstrukce používané k modelu práci probíhá na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-137">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="5bfc5-138">`async` – Klíčové slovo změní metoda do asynchronní metody, která umožňuje používat `await` – klíčové slovo v jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-138">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
*   <span data-ttu-id="5bfc5-139">Když `await` – klíčové slovo se použije, volání metody pozastaví a vypočítá řízení zpět do jeho volajícího, až do dokončení awaited úloh.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-139">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
*   <span data-ttu-id="5bfc5-140">`await` dá se použít jenom uvnitř asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-140">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="5bfc5-141">Rozpoznat vázané na procesor a I/čítači práce</span><span class="sxs-lookup"><span data-stu-id="5bfc5-141">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="5bfc5-142">První dva příklady Tento průvodce vám ukázal, jak můžete použít `async` a `await` pro pracovní I/čítači a vázané na procesor.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-142">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="5bfc5-143">Jeho klíč, který je možné určit úlohy, je potřeba udělat I/čítači nebo vázané na procesor, protože může výrazně ovlivnit výkon kódu a může potenciálně vést k zneužití určité vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-143">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="5bfc5-144">Zde jsou dva otázek, na které je třeba požádat před psaní jakéhokoli kódu:</span><span class="sxs-lookup"><span data-stu-id="5bfc5-144">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="5bfc5-145">Bude kód "čekat" něco, třeba dat z databáze?</span><span class="sxs-lookup"><span data-stu-id="5bfc5-145">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="5bfc5-146">Pokud je vaše odpověď "Ano", pak je práce **I/čítači**.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-146">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="5bfc5-147">Bude kód provádět velmi náročná výpočet?</span><span class="sxs-lookup"><span data-stu-id="5bfc5-147">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="5bfc5-148">Pokud jste odpověděli "Ano", pak je práce **vázané na procesor**.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-148">If you answered "yes", then your work is **CPU-bound**.</span></span>
    
<span data-ttu-id="5bfc5-149">Pokud je pracovní máte **I/čítači**, použijte `async` a `await` *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-149">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="5bfc5-150">Můžete *neměli* použít Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-150">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="5bfc5-151">Důvodem je uvedené v [asynchronní v článku hloubka](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="5bfc5-151">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="5bfc5-152">Pokud je pracovní máte **vázané na procesor** a kterých vám nejvíc záleží kratší reakční doby, použijte `async` a `await` ale spawn práce vypnout na jiné vlákno *s* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-152">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="5bfc5-153">Pokud je vhodná pro concurrency a paralelismus práce, měli byste také zvážit použití Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-153">If the work is appropriate for concurrency and parallelism, you should also consider using the Task Parallel Library.</span></span>

<span data-ttu-id="5bfc5-154">Kromě toho by měla vždycky měření provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-154">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="5bfc5-155">Například sami zjistíte v situaci, kdy není nákladná práci vázané na procesor dostatečně porovnání s nároky na kontext přepínačů při více vláken.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-155">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="5bfc5-156">Všechny možnosti je jeho kompromis a měli byste vybrat správný kompromis pro vaši situaci.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-156">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="5bfc5-157">Další příklady</span><span class="sxs-lookup"><span data-stu-id="5bfc5-157">More Examples</span></span>

<span data-ttu-id="5bfc5-158">Následující příklady ukazují různé způsoby, můžete napsat kód asynchronní v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-158">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="5bfc5-159">Jejich zahrnují několik různých scénářů, které můžete narazit na.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-159">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="5bfc5-160">Extrakce dat ze sítě</span><span class="sxs-lookup"><span data-stu-id="5bfc5-160">Extracting Data from a Network</span></span>

<span data-ttu-id="5bfc5-161">Tento fragment kódu HTML z www.dotnetfoundation.org a udává počet, kolikrát řetězec ".NET" dochází v kódu HTML.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-161">This snippet downloads the HTML from www.dotnetfoundation.org and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="5bfc5-162">ASP.NET MVC používá k definování webové metody řadiče, který provádí tato úloha vrácení číslo.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-162">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="5bfc5-163">Pokud máte v úmyslu provádět analýzy v produkčním kódu HTML, nepoužívejte regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-163">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="5bfc5-164">Místo toho použijte knihovnu analýzy.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-164">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.DownloadStringAsync("http://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="5bfc5-165">Zde je stejný scénář napsané pro univerzální aplikace pro Windows, který provádí stejnou úlohu při stisknutí tlačítka:</span><span class="sxs-lookup"><span data-stu-id="5bfc5-165">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("http://www.dotnetfoundation.org");

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

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="5bfc5-166">Čekání na dokončení více úloh</span><span class="sxs-lookup"><span data-stu-id="5bfc5-166">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="5bfc5-167">Sami zjistíte v situaci, kdy potřebujete souběžně načtení dat na více místech.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-167">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="5bfc5-168">`Task` Rozhraní API obsahuje dvě metody, `Task.WhenAll` a `Task.WhenAny` které umožňují napsat asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-168">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="5bfc5-169">Tento příklad ukazuje, jak může získat `User` data pro sadu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-169">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="5bfc5-170">Zde je další způsob, jak to trochu více stručně zapsat pomocí LINQ:</span><span class="sxs-lookup"><span data-stu-id="5bfc5-170">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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
<span data-ttu-id="5bfc5-171">Přestože je méně kódu, vezměte v potaz při kombinování LINQ asynchronní kódem.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-171">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="5bfc5-172">Protože LINQ používá odložené provedení (lazy), asynchronní volání nedojde k ní okamžitě nebudou `foreach()` cykly, pokud vynutíte generovaného pořadí k iteraci pomocí volání `.ToList()` nebo `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-172">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="5bfc5-173">Důležité informace a Rady, jak</span><span class="sxs-lookup"><span data-stu-id="5bfc5-173">Important Info and Advice</span></span>

<span data-ttu-id="5bfc5-174">I když je relativně jednoduché asynchronní programování, nejsou některé podrobnosti k mějte na paměti, která může zabránit neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-174">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

*  <span data-ttu-id="5bfc5-175">`async` **metody musí mít** `await` **– klíčové slovo v jejich textu nebo nikdy předá!**</span><span class="sxs-lookup"><span data-stu-id="5bfc5-175">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="5bfc5-176">To je důležité pamatovat.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-176">This is important to keep in mind.</span></span>  <span data-ttu-id="5bfc5-177">Pokud `await` není použit v textu `async` metoda, C# kompilátoru bude generovat upozornění, ale kód bude zkompilování a spuštění, jako kdyby šlo o normální metody.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-177">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="5bfc5-178">Všimněte si, že také bude velmi neefektivní, jako by být splníte stav stavového stroje generované kompilátor jazyka C# pro asynchronní metody, nic.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-178">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

*   <span data-ttu-id="5bfc5-179">**Měli byste přidat "Asynchronní" jako přípona názvů každých asynchronní metoda, kterou píšete.**</span><span class="sxs-lookup"><span data-stu-id="5bfc5-179">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="5bfc5-180">Toto je názvů v rozhraní .NET sloužící k další snadno odlišení synchronní a asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-180">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="5bfc5-181">Všimněte si, že některé metody, které nejsou výslovně volány váš kód (například obslužné rutiny událostí nebo metody kontroleru webového) není nemusí nezbytně vztahovat.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-181">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="5bfc5-182">Protože tyto nejsou ve vašem kódu explicitně volané, probíhá explicitní o jejich názvy není jako důležité.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-182">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

*   <span data-ttu-id="5bfc5-183">`async void` **lze používat pouze pro obslužné rutiny událostí.**</span><span class="sxs-lookup"><span data-stu-id="5bfc5-183">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="5bfc5-184">`async void` je jediný způsob, jak povolit obslužné rutiny událostí asynchronní pracovat, protože události nemají návratové typy (proto nelze provést použití `Task` a `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="5bfc5-184">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="5bfc5-185">Jakékoliv jiné použití `async void` nedodrží klepněte na modelu a může být náročné, pokud chcete použít, například:</span><span class="sxs-lookup"><span data-stu-id="5bfc5-185">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  *   <span data-ttu-id="5bfc5-186">Výjimky vzniklé v `async void` metoda nemůže být zachycena mimo tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-186">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
  *   <span data-ttu-id="5bfc5-187">`async void` metody jsou velmi obtížné otestovat.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-187">`async void` methods are very difficult to test.</span></span>
  *   <span data-ttu-id="5bfc5-188">`async void` metody může způsobit chybný vedlejší účinky, pokud má volající není očekáván mají být asynchronní.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-188">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

*   <span data-ttu-id="5bfc5-189">**Pečlivě běhounu při použití asynchronní lambdas v LINQ – výrazy**</span><span class="sxs-lookup"><span data-stu-id="5bfc5-189">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="5bfc5-190">Výrazy lambda v technologii LINQ použít odložené provedení, může stát, že kód význam provádění v době, kdy neočekáváte jej do.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-190">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="5bfc5-191">Zavedení blokování do této úlohy můžete snadno následek zablokování, pokud není správně zapsaná.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-191">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="5bfc5-192">Kromě toho vnoření asynchronní kódu jako to provést také ho obtížnější důvod o provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-192">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="5bfc5-193">Async a LINQ jsou efektivní, ale má být použit společně jako pečlivě a jasně nejblíže.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-193">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

*   <span data-ttu-id="5bfc5-194">**Napsat kód, který čeká úlohy způsobem neblokující**</span><span class="sxs-lookup"><span data-stu-id="5bfc5-194">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="5bfc5-195">Blokování aktuální vlákno jako prostředek k čekání na dokončení úlohy může způsobit zablokování a blokovaný kontextu vláken a může vyžadovat mnohem složitější zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-195">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="5bfc5-196">Následující tabulka obsahuje pokyny k řešení problémů s čekání úlohy způsobem neblokující:</span><span class="sxs-lookup"><span data-stu-id="5bfc5-196">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="5bfc5-197">Použijte...</span><span class="sxs-lookup"><span data-stu-id="5bfc5-197">Use this...</span></span> | <span data-ttu-id="5bfc5-198">Místo to...</span><span class="sxs-lookup"><span data-stu-id="5bfc5-198">Instead of this...</span></span> | <span data-ttu-id="5bfc5-199">Pokud chtějí tomu</span><span class="sxs-lookup"><span data-stu-id="5bfc5-199">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="5bfc5-200">`Task.Wait` Nebo `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="5bfc5-200">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="5bfc5-201">Načítání výsledek úlohy na pozadí</span><span class="sxs-lookup"><span data-stu-id="5bfc5-201">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="5bfc5-202">Čekání na dokončení žádné úlohy</span><span class="sxs-lookup"><span data-stu-id="5bfc5-202">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="5bfc5-203">Čekání na dokončení všech úloh</span><span class="sxs-lookup"><span data-stu-id="5bfc5-203">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="5bfc5-204">Čekání na v časovém intervalu</span><span class="sxs-lookup"><span data-stu-id="5bfc5-204">Waiting for a period of time</span></span> |

*   <span data-ttu-id="5bfc5-205">**Napsat méně stavový kód**</span><span class="sxs-lookup"><span data-stu-id="5bfc5-205">**Write less stateful code**</span></span>

<span data-ttu-id="5bfc5-206">Nemáte závisí na stavu globální objekty nebo provádění určitých metody.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-206">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="5bfc5-207">Místo toho závisí pouze na vrácených hodnotách metod.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-207">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="5bfc5-208">Proč?</span><span class="sxs-lookup"><span data-stu-id="5bfc5-208">Why?</span></span>

  *   <span data-ttu-id="5bfc5-209">Kód bude jednodušší důvod o.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-209">Code will be easier to reason about.</span></span>
  *   <span data-ttu-id="5bfc5-210">Kód bude jednodušší k testování.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-210">Code will be easier to test.</span></span>
  *   <span data-ttu-id="5bfc5-211">Kombinování asynchronní a synchronní kód je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-211">Mixing async and synchronous code is far simpler.</span></span>
  *   <span data-ttu-id="5bfc5-212">Obvykle se vyhnout zcela časování.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-212">Race conditions can typically be avoided altogether.</span></span>
  *   <span data-ttu-id="5bfc5-213">V závislosti na vrácených hodnotách i koordinující asynchronní kódu.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-213">Depending on return values makes coordinating async code simple.</span></span>
  *   <span data-ttu-id="5bfc5-214">(Bonusové) funguje dobře skutečně s vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-214">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="5bfc5-215">Doporučené cílem je dosáhnout úplné nebo téměř úplné [referenční průhlednost](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-215">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="5bfc5-216">Díky tomu bude výsledkem codebase velmi předvídatelný, možností intenzivního testování a udržovatelný.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-216">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="5bfc5-217">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5bfc5-217">Other Resources</span></span>

* <span data-ttu-id="5bfc5-218">[Asynchronní podrobný](../standard/async-in-depth.md) poskytuje další informace o fungování úlohy.</span><span class="sxs-lookup"><span data-stu-id="5bfc5-218">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="5bfc5-219">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="5bfc5-219">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)
* <span data-ttu-id="5bfc5-220">Lucian Wischik [šesti důležité tipy pro asynchronní](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) jsou vynikající prostředků pro asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="5bfc5-220">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
