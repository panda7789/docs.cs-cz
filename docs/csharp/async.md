---
title: 'Asynchronní programování – C #'
description: Přečtěte si o asynchronním programovacím modelu C#, který poskytuje .NET Core, na úrovni jazyka C#.
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: ee5edc80d9c020dbbeced3fc36d3ff273036d7b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761886"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="b12d1-103">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="b12d1-103">Asynchronous programming</span></span>

<span data-ttu-id="b12d1-104">Pokud máte nějaké požadavky na vstupně-výstupní operace (například vyžádání dat ze sítě, přístup k databázi nebo čtení a zápis do systému souborů), budete chtít využít asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="b12d1-104">If you have any I/O-bound needs (such as requesting data from a network, accessing a database, or reading and writing to a file system), you'll want to utilize asynchronous programming.</span></span> <span data-ttu-id="b12d1-105">Můžete mít také kód vázaný na procesor, jako je například provádění nákladného výpočtu, což je také dobrý scénář pro psaní asynchronního kódu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="b12d1-106">Jazyk C# má model asynchronního programování na úrovni jazyka, který umožňuje snadné psaní asynchronního kódu bez nutnosti juggle zpětná volání nebo odpovídat knihovně, která podporuje asynchronii.</span><span class="sxs-lookup"><span data-stu-id="b12d1-106">C# has a language-level asynchronous programming model, which allows for easily writing asynchronous code, without having to juggle callbacks or conform to a library that supports asynchrony.</span></span> <span data-ttu-id="b12d1-107">Postupuje podle toho, co se říká [asynchronní vzor založený na úlohách (klepněte)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="b12d1-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="overview-of-the-asynchronous-model"></a><span data-ttu-id="b12d1-108">Přehled asynchronního modelu</span><span class="sxs-lookup"><span data-stu-id="b12d1-108">Overview of the asynchronous model</span></span>

<span data-ttu-id="b12d1-109">Základem asynchronního programování jsou `Task` `Task<T>` objekty a, které modelují asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="b12d1-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span> <span data-ttu-id="b12d1-110">Jsou podporovány pomocí `async` `await` klíčových slov a.</span><span class="sxs-lookup"><span data-stu-id="b12d1-110">They are supported by the `async` and `await` keywords.</span></span> <span data-ttu-id="b12d1-111">Model je ve většině případů velmi jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="b12d1-111">The model is fairly simple in most cases:</span></span>

- <span data-ttu-id="b12d1-112">Pro kód vázaný na vstupně-výstupní operace očekáváte operaci, která vrací `Task` nebo `Task<T>` uvnitř `async` metody.</span><span class="sxs-lookup"><span data-stu-id="b12d1-112">For I/O-bound code, you await an operation that returns a `Task` or `Task<T>` inside of an `async` method.</span></span>
- <span data-ttu-id="b12d1-113">Pro kód vázaný na procesor očekáváte operaci, která je spuštěna ve vlákně na pozadí s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="b12d1-113">For CPU-bound code, you await an operation that is started on a background thread with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b12d1-114">`await`Klíčové slovo je místo, kde dojde k Magic.</span><span class="sxs-lookup"><span data-stu-id="b12d1-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="b12d1-115">Poskytuje řízení volajícímu metody, kterou provedl `await` , a nakonec umožňuje, aby uživatelské rozhraní mohlo reagovat nebo služba měla být Elasticka.</span><span class="sxs-lookup"><span data-stu-id="b12d1-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span> <span data-ttu-id="b12d1-116">I když [existují způsoby](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) přístupu k asynchronnímu kódu, který je jiný než `async` a `await` , Tento článek se zaměřuje na konstrukce na úrovni jazyka.</span><span class="sxs-lookup"><span data-stu-id="b12d1-116">While [there are ways](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) to approach async code other than `async` and `await`, this article focuses on the language-level constructs.</span></span>

### <a name="io-bound-example-download-data-from-a-web-service"></a><span data-ttu-id="b12d1-117">Vstup/výstup – příklad vazby: stažení dat z webové služby</span><span class="sxs-lookup"><span data-stu-id="b12d1-117">I/O-bound example: Download data from a web service</span></span>

<span data-ttu-id="b12d1-118">Může být nutné stáhnout některá data z webové služby, když je stisknuto tlačítko, ale nechcete zablokovat vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b12d1-118">You may need to download some data from a web service when a button is pressed, but don't want to block the UI thread.</span></span> <span data-ttu-id="b12d1-119">Můžete to provést takto:</span><span class="sxs-lookup"><span data-stu-id="b12d1-119">It can be accomplished like this:</span></span>

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

<span data-ttu-id="b12d1-120">Kód vyjadřuje záměr (asynchronní stahování dat) bez nutnosti zabřednete v interakci s `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="b12d1-120">The code expresses the intent (downloading data asynchronously) without getting bogged down in interacting with `Task` objects.</span></span>

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a><span data-ttu-id="b12d1-121">Příklad vázaný na procesor: provedení výpočtu pro hru</span><span class="sxs-lookup"><span data-stu-id="b12d1-121">CPU-bound example: Perform a calculation for a game</span></span>

<span data-ttu-id="b12d1-122">Řekněme, že píšete mobilní hru, kde stisknutí tlačítka může způsobit poškození mnoha Enemies na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="b12d1-122">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span> <span data-ttu-id="b12d1-123">Provádění výpočtu škod může být nákladné a jeho provedení na vlákně UI by vedlo k tomu, že se hra po provedení výpočtu zastaví.</span><span class="sxs-lookup"><span data-stu-id="b12d1-123">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="b12d1-124">Nejlepším způsobem, jak to zpracovat, je spustit vlákno na pozadí, které funguje pomocí `Task.Run` a očekávat jeho výsledek pomocí `await` .</span><span class="sxs-lookup"><span data-stu-id="b12d1-124">The best way to handle this is to start a background thread, which does the work using `Task.Run`, and await its result using `await`.</span></span> <span data-ttu-id="b12d1-125">Díky tomu může uživatelské rozhraní cítit plynulé fungování práce.</span><span class="sxs-lookup"><span data-stu-id="b12d1-125">This allows the UI to feel smooth as the work is being done.</span></span>

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
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="b12d1-126">Tento kód čistě vyjadřuje záměr události kliknutí na tlačítko, nevyžaduje ruční správu vlákna na pozadí a je tak neblokujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b12d1-126">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="b12d1-127">Co se stane v rámci pokrývání</span><span class="sxs-lookup"><span data-stu-id="b12d1-127">What happens under the covers</span></span>

<span data-ttu-id="b12d1-128">Existuje mnoho pohybujících se částí, ve kterých se jedná o asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="b12d1-128">There are many moving pieces where asynchronous operations are concerned.</span></span> <span data-ttu-id="b12d1-129">Pokud jste zajímái o tom, co se děje `Task` `Task<T>` , a další informace najdete [v](../standard/async-in-depth.md) podrobném článku.</span><span class="sxs-lookup"><span data-stu-id="b12d1-129">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, see the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="b12d1-130">Na straně jazyka C# kompilátor transformuje váš kód do stavového počítače, který uchovává informace o tom, jako je například vracení provádění při `await` dosažení a obnovení spuštění po dokončení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b12d1-130">On the C# side of things, the compiler transforms your code into a state machine that keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="b12d1-131">Pro teoreticky-skloněnou je to implementace [modelu asynchronii pro příslib](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="b12d1-131">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="b12d1-132">Klíčové kousky, které je potřeba pochopit</span><span class="sxs-lookup"><span data-stu-id="b12d1-132">Key pieces to understand</span></span>

* <span data-ttu-id="b12d1-133">Asynchronní kód lze použít pro vstupně-výstupní operace i pro kód vázaný na procesor, ale pro každý scénář odlišně.</span><span class="sxs-lookup"><span data-stu-id="b12d1-133">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="b12d1-134">Asynchronní kód používá `Task<T>` a `Task` , které jsou konstrukce používané k modelování práce prováděné na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b12d1-134">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="b12d1-135">`async`Klíčové slovo převede metodu do asynchronní metody, která umožňuje použití `await` klíčového slova v těle.</span><span class="sxs-lookup"><span data-stu-id="b12d1-135">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="b12d1-136">Při `await` použití klíčového slova pozastaví volající metodu a vrátí řízení volajícímu, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="b12d1-136">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="b12d1-137">`await`dá se použít jenom uvnitř asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="b12d1-137">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="b12d1-138">Rozpoznání práce vázané na procesor a vstupně-výstupní operace</span><span class="sxs-lookup"><span data-stu-id="b12d1-138">Recognize CPU-bound and I/O-bound work</span></span>

<span data-ttu-id="b12d1-139">První dva příklady této příručky ukázaly, jak můžete použít `async` a `await` pro vstupně-výstupní operace a práci vázané na procesor.</span><span class="sxs-lookup"><span data-stu-id="b12d1-139">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span> <span data-ttu-id="b12d1-140">Je klíč, který můžete identifikovat, když je potřeba udělat úlohu, která je vázaná na vstupně-výstupní operace, nebo na základě procesoru, protože může významně ovlivnit výkon kódu a může potenciálně vést k omylům s některými konstrukcemi.</span><span class="sxs-lookup"><span data-stu-id="b12d1-140">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="b12d1-141">Tady jsou dvě otázky, které byste měli před psaním kódu zeptat:</span><span class="sxs-lookup"><span data-stu-id="b12d1-141">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="b12d1-142">Bude váš kód "čekání" na něco, například data z databáze?</span><span class="sxs-lookup"><span data-stu-id="b12d1-142">Will your code be "waiting" for something, such as data from a database?</span></span>

   <span data-ttu-id="b12d1-143">Pokud je vaše odpověď "Ano", vaše práce je **vázána na vstup/výstup**.</span><span class="sxs-lookup"><span data-stu-id="b12d1-143">If your answer is "yes", then your work is **I/O-bound**.</span></span>

1. <span data-ttu-id="b12d1-144">Bude váš kód provádět nákladný výpočet?</span><span class="sxs-lookup"><span data-stu-id="b12d1-144">Will your code be performing an expensive computation?</span></span>

   <span data-ttu-id="b12d1-145">Pokud jste odpověděli na Ano, vaše práce bude **vázaná na procesor**.</span><span class="sxs-lookup"><span data-stu-id="b12d1-145">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="b12d1-146">Pokud je práce, kterou jste **vázáni na vstup/výstup**, použijte `async` a `await` *bez* `Task.Run` .</span><span class="sxs-lookup"><span data-stu-id="b12d1-146">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span> <span data-ttu-id="b12d1-147">*Neměli byste* používat Task Parallel Library.</span><span class="sxs-lookup"><span data-stu-id="b12d1-147">You *should not* use the Task Parallel Library.</span></span> <span data-ttu-id="b12d1-148">Důvod je popsaný v části Async v rámci [hloubky](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="b12d1-148">The reason for this is outlined in [Async in Depth](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="b12d1-149">Pokud je práce **vázaná na procesor** a Vy se zajímáte o odezvu, použijte `async` a `await` , ale zapněte práci na jiném vlákně *with* `Task.Run` .</span><span class="sxs-lookup"><span data-stu-id="b12d1-149">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await`, but spawn off the work on another thread *with* `Task.Run`.</span></span> <span data-ttu-id="b12d1-150">Pokud je práce vhodná pro souběžnost a paralelismu, zvažte také použití [paralelní knihovny Task](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="b12d1-150">If the work is appropriate for concurrency and parallelism, also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="b12d1-151">Kromě toho byste měli vždy změřit provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-151">Additionally, you should always measure the execution of your code.</span></span> <span data-ttu-id="b12d1-152">Například se můžete setkat v situaci, kdy práce vázaná na procesor není ve srovnání s režií kontextových přepínačů v případě multithreadingu dostatečně nákladná.</span><span class="sxs-lookup"><span data-stu-id="b12d1-152">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span> <span data-ttu-id="b12d1-153">Každá volba má své kompromisy a měli byste si vybrat správné kompromisy pro vaši situaci.</span><span class="sxs-lookup"><span data-stu-id="b12d1-153">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="b12d1-154">Další příklady</span><span class="sxs-lookup"><span data-stu-id="b12d1-154">More examples</span></span>

<span data-ttu-id="b12d1-155">Následující příklady ukazují různé způsoby, jak lze v jazyce C# napsat asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="b12d1-155">The following examples demonstrate various ways you can write async code in C#.</span></span> <span data-ttu-id="b12d1-156">Pokrývají několik různých scénářů, které se mohou nacházet v rámci.</span><span class="sxs-lookup"><span data-stu-id="b12d1-156">They cover a few different scenarios you may come across.</span></span>

### <a name="extract-data-from-a-network"></a><span data-ttu-id="b12d1-157">Extrakce dat ze sítě</span><span class="sxs-lookup"><span data-stu-id="b12d1-157">Extract data from a network</span></span>

<span data-ttu-id="b12d1-158">Tento fragment kódu stáhne kód HTML z domovské stránky <https://dotnetfoundation.org> a spočítá počet výskytů řetězce ".NET" v HTML.</span><span class="sxs-lookup"><span data-stu-id="b12d1-158">This snippet downloads the HTML from the homepage at <https://dotnetfoundation.org> and counts the number of times the string ".NET" occurs in the HTML.</span></span> <span data-ttu-id="b12d1-159">Používá ASP.NET k definování metody kontroleru webového rozhraní API, která provádí tuto úlohu a vrací číslo.</span><span class="sxs-lookup"><span data-stu-id="b12d1-159">It uses ASP.NET to define a Web API controller method, which performs this task and returns the number.</span></span>

> [!NOTE]
> <span data-ttu-id="b12d1-160">Pokud plánujete provádění analýzy HTML v produkčním kódu, nepoužívejte regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="b12d1-160">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="b12d1-161">Místo toho použijte analýzu knihovny.</span><span class="sxs-lookup"><span data-stu-id="b12d1-161">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="b12d1-162">Tady je stejný scénář, který je napsán pro univerzální aplikaci pro Windows, která při stisknutí tlačítka provede stejnou úlohu:</span><span class="sxs-lookup"><span data-stu-id="b12d1-162">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

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

### <a name="wait-for-multiple-tasks-to-complete"></a><span data-ttu-id="b12d1-163">Počkejte na dokončení více úloh.</span><span class="sxs-lookup"><span data-stu-id="b12d1-163">Wait for multiple tasks to complete</span></span>

<span data-ttu-id="b12d1-164">Můžete se setkat v situaci, kdy potřebujete současně načíst více dat.</span><span class="sxs-lookup"><span data-stu-id="b12d1-164">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span> <span data-ttu-id="b12d1-165">`Task`Rozhraní API obsahuje dvě metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , které umožňují napsat asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b12d1-165">The `Task` API contains two methods, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, that allow you to write asynchronous code that performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="b12d1-166">Tento příklad ukazuje, jak můžete vyjímat `User` data pro sadu `userId` s.</span><span class="sxs-lookup"><span data-stu-id="b12d1-166">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="b12d1-167">Tady je další způsob, jak tento příklad napsat stručně pomocí LINQ:</span><span class="sxs-lookup"><span data-stu-id="b12d1-167">Here's another way to write this more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="b12d1-168">I když je to méně kódu, při kombinování LINQ s asynchronním kódem je potřeba dbát.</span><span class="sxs-lookup"><span data-stu-id="b12d1-168">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span> <span data-ttu-id="b12d1-169">Vzhledem k tomu, že LINQ používá odložené (opožděné) provádění, asynchronní volání nebudou provedena ihned stejně jako ve `foreach` smyčce, pokud vynutíte vygenerování sekvence pro iteraci voláním `.ToList()` nebo `.ToArray()` .</span><span class="sxs-lookup"><span data-stu-id="b12d1-169">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="b12d1-170">Důležité informace a Rady</span><span class="sxs-lookup"><span data-stu-id="b12d1-170">Important info and advice</span></span>

<span data-ttu-id="b12d1-171">V případě asynchronního programování jsou k dispozici nějaké podrobnosti, které vám pomůžou zabránit neočekávanému chování.</span><span class="sxs-lookup"><span data-stu-id="b12d1-171">With async programming there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="b12d1-172">`async`**metody musí mít** `await` **klíčové slovo ve svém těle, nebo nikdy nebude vracet!**</span><span class="sxs-lookup"><span data-stu-id="b12d1-172">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

  <span data-ttu-id="b12d1-173">To je důležité mít na paměti.</span><span class="sxs-lookup"><span data-stu-id="b12d1-173">This is important to keep in mind.</span></span> <span data-ttu-id="b12d1-174">Pokud `await` se v těle metody nepoužívá `async` , kompilátor C# vygeneruje upozornění, ale kód se zkompiluje a spustí, jako kdyby šlo o běžnou metodu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-174">If `await` is not used in the body of an `async` method, the C# compiler generates a warning, but the code compiles and runs as if it were a normal method.</span></span> <span data-ttu-id="b12d1-175">To je neuvěřitelně neefektivní, protože Stavový počítač generovaný kompilátorem jazyka C# pro asynchronní metodu neprovádí žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="b12d1-175">This is incredibly inefficient, as the state machine generated by the C# compiler for the async method is not accomplishing anything.</span></span>

* <span data-ttu-id="b12d1-176">**Jako příponu každého názvu asynchronní metody, kterou píšete, byste měli přidat "Async".**</span><span class="sxs-lookup"><span data-stu-id="b12d1-176">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="b12d1-177">Toto je konvence, která se používá v rozhraní .NET k jednoduššímu odlišení synchronních a asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="b12d1-177">This is the convention used in .NET to more easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="b12d1-178">Některé metody, které nejsou explicitně volány vaším kódem (například obslužné rutiny událostí nebo metody webového kontroleru), nemusí nutně platit.</span><span class="sxs-lookup"><span data-stu-id="b12d1-178">Certain methods that aren't explicitly called by your code (such as event handlers or web controller methods) don't necessarily apply.</span></span> <span data-ttu-id="b12d1-179">Vzhledem k tomu, že nejsou explicitně volány vaším kódem, je explicitní informace o jejich pojmenování nevýznamná.</span><span class="sxs-lookup"><span data-stu-id="b12d1-179">Because they are not explicitly called by your code, being explicit about their naming isn't as important.</span></span>

* <span data-ttu-id="b12d1-180">`async void`**by mělo být použito pouze pro obslužné rutiny událostí.**</span><span class="sxs-lookup"><span data-stu-id="b12d1-180">`async void` **should only to be used for event handlers.**</span></span>

<span data-ttu-id="b12d1-181">`async void`je jediným způsobem, jak povolit fungování asynchronních obslužných rutin událostí, protože události nemají návratové typy (proto nemohou použít `Task` a `Task<T>` ).</span><span class="sxs-lookup"><span data-stu-id="b12d1-181">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="b12d1-182">Jakékoli jiné použití se `async void` neřídí modelem klepnutí a může být náročné na použití, například:</span><span class="sxs-lookup"><span data-stu-id="b12d1-182">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="b12d1-183">Výjimky vyvolané v `async void` metodě nejde zachytit mimo tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-183">Exceptions thrown in an `async void` method can't be caught outside of that method.</span></span>
* <span data-ttu-id="b12d1-184">`async void`metody jsou obtížné testovat.</span><span class="sxs-lookup"><span data-stu-id="b12d1-184">`async void` methods are difficult to test.</span></span>
* <span data-ttu-id="b12d1-185">`async void`metody mohou způsobit špatné vedlejší účinky, pokud volající neočekává, že budou Async.</span><span class="sxs-lookup"><span data-stu-id="b12d1-185">`async void` methods can cause bad side effects if the caller isn't expecting them to be async.</span></span>

* <span data-ttu-id="b12d1-186">**Při použití asynchronních výrazů lambda ve výrazech LINQ pečlivě běhouny**</span><span class="sxs-lookup"><span data-stu-id="b12d1-186">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="b12d1-187">Výrazy lambda v jazyce LINQ používají odložené provádění, což znamená, že kód může být spuštěn v okamžiku, kdy ho neočekáváte.</span><span class="sxs-lookup"><span data-stu-id="b12d1-187">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you're not expecting it to.</span></span> <span data-ttu-id="b12d1-188">Zavedení blokujících úloh do této operace může snadno vést k zablokování, pokud není správně napsáno.</span><span class="sxs-lookup"><span data-stu-id="b12d1-188">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="b12d1-189">Kromě toho vnořování asynchronního kódu, jako je, může také ztížit důvod spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-189">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="b12d1-190">Asynchronní a LINQ jsou výkonné, ale měly by být používány společně co nejdříve a jasně.</span><span class="sxs-lookup"><span data-stu-id="b12d1-190">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="b12d1-191">**Napsat kód, který čeká na úlohy bez blokování**</span><span class="sxs-lookup"><span data-stu-id="b12d1-191">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="b12d1-192">Blokování aktuálního vlákna jako prostředku pro čekání `Task` na dokončení může způsobit zablokování a blokované kontextová vlákna a může vyžadovat složitější zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="b12d1-192">Blocking the current thread as a means to wait for a `Task` to complete can result in deadlocks and blocked context threads, and can require more complex error-handling.</span></span> <span data-ttu-id="b12d1-193">V následující tabulce najdete pokyny, jak se zabývat čekáním na úlohy neblokujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b12d1-193">The following table provides guidance on how to deal with waiting for tasks in a non-blocking way:</span></span>

| <span data-ttu-id="b12d1-194">Postup...</span><span class="sxs-lookup"><span data-stu-id="b12d1-194">Use this...</span></span>          | <span data-ttu-id="b12d1-195">Místo...</span><span class="sxs-lookup"><span data-stu-id="b12d1-195">Instead of this...</span></span>           | <span data-ttu-id="b12d1-196">Kdy to chcete udělat...</span><span class="sxs-lookup"><span data-stu-id="b12d1-196">When wishing to do this...</span></span>                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | <span data-ttu-id="b12d1-197">`Task.Wait` nebo `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="b12d1-197">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="b12d1-198">Načítání výsledku úlohy na pozadí</span><span class="sxs-lookup"><span data-stu-id="b12d1-198">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny`               | <span data-ttu-id="b12d1-199">Čeká se na dokončení všech úloh.</span><span class="sxs-lookup"><span data-stu-id="b12d1-199">Waiting for any task to complete</span></span>           |
| `await Task.WhenAll` | `Task.WaitAll`               | <span data-ttu-id="b12d1-200">Čeká se na dokončení všech úloh.</span><span class="sxs-lookup"><span data-stu-id="b12d1-200">Waiting for all tasks to complete</span></span>          |
| `await Task.Delay`   | `Thread.Sleep`               | <span data-ttu-id="b12d1-201">Čekání na časový úsek</span><span class="sxs-lookup"><span data-stu-id="b12d1-201">Waiting for a period of time</span></span>               |

* <span data-ttu-id="b12d1-202">**Zvažte použití** `ValueTask` **Pokud je to možné**</span><span class="sxs-lookup"><span data-stu-id="b12d1-202">**Consider using** `ValueTask` **where possible**</span></span>

<span data-ttu-id="b12d1-203">Vrácení `Task` objektu z asynchronních metod může způsobit kritické body výkonu v určitých cestách.</span><span class="sxs-lookup"><span data-stu-id="b12d1-203">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="b12d1-204">`Task`je odkazový typ, takže jeho použití znamená přidělení objektu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-204">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="b12d1-205">V případech, kdy metoda deklarovaná s `async` modifikátorem vrací výsledek uložený v mezipaměti nebo se dokončí synchronně, se další přidělení můžou stát značnými náklady v částech kritického výkonu v kódu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-205">In cases where a method declared with the `async` modifier returns a cached result or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="b12d1-206">Pokud dojde k přidělení v těsných smyčkách, může to být nákladné.</span><span class="sxs-lookup"><span data-stu-id="b12d1-206">It can become costly if those allocations occur in tight loops.</span></span> <span data-ttu-id="b12d1-207">Další informace naleznete v tématu [generalizované asynchronní návratové typy](whats-new/csharp-7.md#generalized-async-return-types).</span><span class="sxs-lookup"><span data-stu-id="b12d1-207">For more information, see [generalized async return types](whats-new/csharp-7.md#generalized-async-return-types).</span></span>

* <span data-ttu-id="b12d1-208">**Zvažte použití**`ConfigureAwait(false)`</span><span class="sxs-lookup"><span data-stu-id="b12d1-208">**Consider using** `ConfigureAwait(false)`</span></span>

<span data-ttu-id="b12d1-209">Běžnou otázkou je, "kdy mám použít <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> metodu?".</span><span class="sxs-lookup"><span data-stu-id="b12d1-209">A common question is, "when should I use the <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> method?".</span></span> <span data-ttu-id="b12d1-210">Metoda umožňuje `Task` instanci nakonfigurovat svůj operátor await.</span><span class="sxs-lookup"><span data-stu-id="b12d1-210">The method allows for a `Task` instance to configure its awaiter.</span></span> <span data-ttu-id="b12d1-211">To je důležitý aspekt a jeho nesprávné nastavení by mohlo mít dopad na výkon a dokonce i zablokování.</span><span class="sxs-lookup"><span data-stu-id="b12d1-211">This is an important consideration and setting it incorrectly could potentially have performance implications and even deadlocks.</span></span> <span data-ttu-id="b12d1-212">Další informace o najdete v `ConfigureAwait` tématu [ConfigureAwait – Nejčastější dotazy](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span><span class="sxs-lookup"><span data-stu-id="b12d1-212">For more information on `ConfigureAwait`, see the [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span></span>

* <span data-ttu-id="b12d1-213">**Zápis méně stavového kódu**</span><span class="sxs-lookup"><span data-stu-id="b12d1-213">**Write less stateful code**</span></span>

<span data-ttu-id="b12d1-214">Nezávisí na stavu globálních objektů nebo provádění určitých metod.</span><span class="sxs-lookup"><span data-stu-id="b12d1-214">Don't depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="b12d1-215">Místo toho závisí pouze na vrácených hodnotách metod.</span><span class="sxs-lookup"><span data-stu-id="b12d1-215">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="b12d1-216">Proč?</span><span class="sxs-lookup"><span data-stu-id="b12d1-216">Why?</span></span>

* <span data-ttu-id="b12d1-217">Kód bude z důvodu snazší.</span><span class="sxs-lookup"><span data-stu-id="b12d1-217">Code will be easier to reason about.</span></span>
* <span data-ttu-id="b12d1-218">Testování kódu bude snazší.</span><span class="sxs-lookup"><span data-stu-id="b12d1-218">Code will be easier to test.</span></span>
* <span data-ttu-id="b12d1-219">Kombinování asynchronního a synchronního kódu je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="b12d1-219">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="b12d1-220">Konflikty časování se obvykle můžou vyvarovat zcela.</span><span class="sxs-lookup"><span data-stu-id="b12d1-220">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="b12d1-221">V závislosti na vrácených hodnotách je jednodušší koordinovat asynchronní kód.</span><span class="sxs-lookup"><span data-stu-id="b12d1-221">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="b12d1-222">(Bonus) funguje ve skutečnosti i při vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="b12d1-222">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="b12d1-223">Doporučeným cílem je dosáhnout úplné nebo téměř úplné [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-223">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="b12d1-224">Výsledkem je mimořádně předvídatelný, testovatelné a udržovatelný základ kódu.</span><span class="sxs-lookup"><span data-stu-id="b12d1-224">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b12d1-225">Další prostředky</span><span class="sxs-lookup"><span data-stu-id="b12d1-225">Other resources</span></span>

* <span data-ttu-id="b12d1-226">[Async-Depth](../standard/async-in-depth.md) poskytuje další informace o práci s úkoly.</span><span class="sxs-lookup"><span data-stu-id="b12d1-226">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="b12d1-227">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="b12d1-227">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="b12d1-228">[Šest důležitých tipů pro Lucian Wischik pro Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) je vynikajícím prostředkem pro asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="b12d1-228">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
