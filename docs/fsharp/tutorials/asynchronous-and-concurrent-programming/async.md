---
title: Asynchronní programování v jazyce F#
description: Zjistěte, jak F# asynchronního programování se provádí prostřednictvím programovací model na úrovni jazyka, který se snadno používá a je přirozený jazyk.
ms.date: 06/20/2016
ms.openlocfilehash: de07f1252df56e3dfec5ea7a34a283b1c9508523
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50195057"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="efe49-103">Asynchronní programování v jazyce F#</span><span class="sxs-lookup"><span data-stu-id="efe49-103">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="efe49-104">Některé nepřesnosti byly zjištěny v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="efe49-104">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="efe49-105">Je právě přepsán.</span><span class="sxs-lookup"><span data-stu-id="efe49-105">It is being rewritten.</span></span>  <span data-ttu-id="efe49-106">Zobrazit [problém #666](https://github.com/dotnet/docs/issues/666) Další informace o změnách.</span><span class="sxs-lookup"><span data-stu-id="efe49-106">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="efe49-107">Asynchronní programování v F# je možné provádět prostřednictvím úrovni jazyka programovací model navržené tak, aby se snadno používá a přirozený jazyk.</span><span class="sxs-lookup"><span data-stu-id="efe49-107">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="efe49-108">Základní asynchronní programování v F# je `Async<'T>`, reprezentace práci, která se dá spouštět na spuštěný na pozadí, kde `'T` se vrátí buď typ prostřednictvím speciální `return` – klíčové slovo nebo `unit` Pokud asynchronního pracovního postupu nemá žádný výsledek určený k vrácení.</span><span class="sxs-lookup"><span data-stu-id="efe49-108">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="efe49-109">Klíčovým konceptem pochopit je, že je typ výrazu asynchronní `Async<'T>`, což je pouze na _specifikace_ práce udělat v asynchronním kontextu.</span><span class="sxs-lookup"><span data-stu-id="efe49-109">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="efe49-110">Není spuštěn, dokud ho explicitně spustit s jednou počáteční funkcí (jako například `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="efe49-110">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="efe49-111">Přestože je toto různých způsobu přemýšlení o tom, jak pracovní, ukončí nebuďte úplně jednoduché v praxi.</span><span class="sxs-lookup"><span data-stu-id="efe49-111">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="efe49-112">Řekněme například, že chcete stáhnout kód HTML z dotnetfoundation.org bez blokování hlavního vlákna.</span><span class="sxs-lookup"><span data-stu-id="efe49-112">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="efe49-113">Můžete provést to takto:</span><span class="sxs-lookup"><span data-stu-id="efe49-113">You can accomplish it like this:</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="efe49-114">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="efe49-114">And that’s it!</span></span> <span data-ttu-id="efe49-115">Kromě použití `async`, `let!`, a `return`, to je jenom normální F# kódu.</span><span class="sxs-lookup"><span data-stu-id="efe49-115">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="efe49-116">Existuje několik syntaktické konstrukce, které stojí za zmínku:</span><span class="sxs-lookup"><span data-stu-id="efe49-116">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="efe49-117">`let!` vytvoří vazbu výsledek výrazu asynchronní (který se spouští v jiném kontextu).</span><span class="sxs-lookup"><span data-stu-id="efe49-117">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="efe49-118">`use!` funguje stejně jako `let!`, ale uvolní prostředky jeho vazby, když dostane mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="efe49-118">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="efe49-119">`do!` počká na asynchronní pracovní postup, který nic nevrací.</span><span class="sxs-lookup"><span data-stu-id="efe49-119">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="efe49-120">`return` jednoduše vrací výsledek z asynchronní výraz.</span><span class="sxs-lookup"><span data-stu-id="efe49-120">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="efe49-121">`return!` spustí jiný pracovní postup asynchronního a vrátí jeho návratovou hodnotu ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="efe49-121">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="efe49-122">Kromě toho normální `let`, `use`, a `do` klíčová slova můžete používat společně se asynchronní verze, stejně jako normální funkce.</span><span class="sxs-lookup"><span data-stu-id="efe49-122">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="efe49-123">Jak můžete začít asynchronní kódF#</span><span class="sxs-lookup"><span data-stu-id="efe49-123">How to start Async Code in F#</span></span> #

<span data-ttu-id="efe49-124">Jak už bylo zmíněno dříve, asynchronní kód je specifikace práce udělat v jiném kontextu, který musí být explicitně spuštěna.</span><span class="sxs-lookup"><span data-stu-id="efe49-124">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="efe49-125">Tady jsou dva základní způsoby, jak toho dosáhnout:</span><span class="sxs-lookup"><span data-stu-id="efe49-125">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="efe49-126">`Async.RunSynchronously` Asynchronní pracovní postup spustit v jiném vlákně, který se await jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="efe49-126">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="efe49-127">`Async.Start` Asynchronní pracovní postup spustit v jiném vlákně a bude **není** await jeho výsledek.</span><span class="sxs-lookup"><span data-stu-id="efe49-127">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="efe49-128">Existují jiné způsoby, jak začít asynchronní workflowu, který je k dispozici pro konkrétnější scénáře.</span><span class="sxs-lookup"><span data-stu-id="efe49-128">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="efe49-129">Jsou podrobně popsány [v odkazu asynchronní](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="efe49-129">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="efe49-130">Poznámka: na vláknech</span><span class="sxs-lookup"><span data-stu-id="efe49-130">A Note on Threads</span></span>

<span data-ttu-id="efe49-131">Fráze "v jiném vlákně" je uvedeno výše, ale je důležité vědět, že **to neznamená, že asynchronní pracovní postupy jsou průčelím pro multithreading**.</span><span class="sxs-lookup"><span data-stu-id="efe49-131">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="efe49-132">Pracovní postup ve skutečnosti "přejde" mezi vlákny vypůjčení pro malé množství času dělat užitečnou práci.</span><span class="sxs-lookup"><span data-stu-id="efe49-132">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="efe49-133">Když pracovním postupu asynchronní efektivně "čeká" (např. čekání na síť volání vracely něco), žádné vlákno, byla půjčky v době je uvolněna až přejděte užitečnou práci na něco jiného.</span><span class="sxs-lookup"><span data-stu-id="efe49-133">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="efe49-134">Tato možnost povoluje asynchronní pracovní postupy pro využití systému, ve kterém jsou spuštěné na co možná nejefektivněji a je mezi nimi vlastně hlavně silným pro scénáře vysoký počet vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="efe49-134">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="efe49-135">Postup přidání paralelismu asynchronní kód</span><span class="sxs-lookup"><span data-stu-id="efe49-135">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="efe49-136">Někdy můžete potřebovat provádět více asynchronních úloh paralelně, shromažďovat jejich výsledky a interpretovat nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="efe49-136">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="efe49-137">`Async.Parallel` Umožňuje provést bez nutnosti použít Task Parallel Library, což by vyžadovalo museli vynucení `Task<'T>` a `Async<'T>` typy.</span><span class="sxs-lookup"><span data-stu-id="efe49-137">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="efe49-138">Následující příklad použije `Async.Parallel` si Pokud chcete stáhnout kód HTML z oblíbených lokalit čtyři paralelně, počkejte na dokončení těchto úloh a poté vytiskněte HTML, který byl stažen.</span><span class="sxs-lookup"><span data-stu-id="efe49-138">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a><span data-ttu-id="efe49-139">Důležité informace a Rady</span><span class="sxs-lookup"><span data-stu-id="efe49-139">Important Info and Advice</span></span>

*   <span data-ttu-id="efe49-140">Připojte "Async" za účelem všechny funkce, které budete používat</span><span class="sxs-lookup"><span data-stu-id="efe49-140">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="efe49-141">I když je to jenom zásady vytváření názvů, je usnadnit věci jako rozhraní API zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="efe49-141">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="efe49-142">Zejména v případě, že existují synchronní a asynchronní verze stejné rutiny, je vhodné k výslovnému, což je asynchronní prostřednictvím názvu.</span><span class="sxs-lookup"><span data-stu-id="efe49-142">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="efe49-143">Naslouchání kompilátoru!</span><span class="sxs-lookup"><span data-stu-id="efe49-143">Listen to the compiler!</span></span>

 <span data-ttu-id="efe49-144">F#pro kompilátor je velmi přísná, díky tomu je téměř nemožné něco jako je zneklidňují nové spuštění kódu "async" synchronně.</span><span class="sxs-lookup"><span data-stu-id="efe49-144">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="efe49-145">Pokud narazíte na upozornění, který je znak, jak si myslíte, že bude kód nebude spuštěno.</span><span class="sxs-lookup"><span data-stu-id="efe49-145">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="efe49-146">Pokud se vás kompilátor šťastný, váš kód spustí pravděpodobně podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="efe49-146">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="efe49-147">Pro C#podívat na programátorovi /VBF#</span><span class="sxs-lookup"><span data-stu-id="efe49-147">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="efe49-148">V této části se předpokládá, seznamte se s asynchronní model v C#/VB.</span><span class="sxs-lookup"><span data-stu-id="efe49-148">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="efe49-149">Pokud nemáte, [asynchronní programování v C# ](../../../csharp/async.md) je výchozím bodem.</span><span class="sxs-lookup"><span data-stu-id="efe49-149">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="efe49-150">Je zásadní rozdíl mezi C#/VB asynchronní model a F# asynchronní model.</span><span class="sxs-lookup"><span data-stu-id="efe49-150">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="efe49-151">Při volání funkce, která vrátí `Task` nebo `Task<'T>`, tato úloha už začala spuštění.</span><span class="sxs-lookup"><span data-stu-id="efe49-151">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="efe49-152">Popisovač vrácený představuje asynchronní úlohu již spuštěná.</span><span class="sxs-lookup"><span data-stu-id="efe49-152">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="efe49-153">Naproti tomu při volání asynchronní funkce F#, `Async<'a>` vrátil představuje úlohu, která bude **generované** v určitém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="efe49-153">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="efe49-154">Vysvětlení tohoto modelu je efektivní, protože to umožňuje asynchronní úlohy v F# se seskupují klidní, provádí podmíněně a pracovat s lepší intervalem ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="efe49-154">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="efe49-155">Existuje několik dalších podobnosti a rozdíly za zmínku.</span><span class="sxs-lookup"><span data-stu-id="efe49-155">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="efe49-156">Podobnosti</span><span class="sxs-lookup"><span data-stu-id="efe49-156">Similarities</span></span>

*   <span data-ttu-id="efe49-157">`let!`, `use!`, a `do!` jsou podobná `await` při volání metody na asynchronní úlohy v rámci `async{ }` bloku.</span><span class="sxs-lookup"><span data-stu-id="efe49-157">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="efe49-158">Tři klíčová slova jde použít jenom v rámci `async { }` bloku, podobný postup `await` lze vyvolat pouze uvnitř `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="efe49-158">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="efe49-159">Stručně řečeno `let!` je pro, pokud chcete zachytit a používat výsledku `use!` je stejný ale něco jehož prostředky by měl získat čištění po se používá, a `do!` je pro, pokud chcete čekat pro asynchronní pracovní postup s žádnou návratovou hodnotu pro dokončení než budete pokračovat.</span><span class="sxs-lookup"><span data-stu-id="efe49-159">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="efe49-160">F#Datový paralelismus podporuje podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="efe49-160">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="efe49-161">I když to vše je přístupné nějak významně odlišně `Async.Parallel` odpovídá `Task.WhenAll` pro scénář záhlaví výsledky sadu asynchronních úloh po dokončení činnosti všech.</span><span class="sxs-lookup"><span data-stu-id="efe49-161">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="efe49-162">Rozdíly</span><span class="sxs-lookup"><span data-stu-id="efe49-162">Differences</span></span>

*   <span data-ttu-id="efe49-163">Vnořené `let!` není povolené, na rozdíl od vnořené `await`</span><span class="sxs-lookup"><span data-stu-id="efe49-163">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="efe49-164">Na rozdíl od `await`, které mohou být vnořené po neomezenou dobu, `let!` nelze a musíte mít jeho výsledek vázán před jeho použitím do druhého `let!`, `do!`, nebo `use!`.</span><span class="sxs-lookup"><span data-stu-id="efe49-164">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="efe49-165">Podporu zrušení je jednodušší v F# než C#/VB.</span><span class="sxs-lookup"><span data-stu-id="efe49-165">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="efe49-166">Podpora zrušení úlohy polovině během C#/VB vyžaduje kontrolu `IsCancellationRequested` vlastností nebo volání `ThrowIfCancellationRequested()` na `CancellationToken` objektu, který je předán do asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="efe49-166">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="efe49-167">Naproti tomu F# asynchronními pracovními postupy jsou přirozeněji zrušit.</span><span class="sxs-lookup"><span data-stu-id="efe49-167">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="efe49-168">Zrušení je jednoduchý proces třech krocích.</span><span class="sxs-lookup"><span data-stu-id="efe49-168">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="efe49-169">Vytvořte nový `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="efe49-169">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="efe49-170">Předejte ho do výchozí funkce.</span><span class="sxs-lookup"><span data-stu-id="efe49-170">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="efe49-171">Volání `Cancel` na tokenu.</span><span class="sxs-lookup"><span data-stu-id="efe49-171">Call `Cancel` on the token.</span></span>

<span data-ttu-id="efe49-172">Příklad:</span><span class="sxs-lookup"><span data-stu-id="efe49-172">Example:</span></span>

```fsharp
open System
open System.Net
open System.Threading

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token.Token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="efe49-173">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="efe49-173">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="efe49-174">Další materiály:</span><span class="sxs-lookup"><span data-stu-id="efe49-174">Further resources:</span></span>

*   [<span data-ttu-id="efe49-175">Asynchronní pracovní postupy na webu MSDN</span><span class="sxs-lookup"><span data-stu-id="efe49-175">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="efe49-176">Asynchronní pořadí proF#</span><span class="sxs-lookup"><span data-stu-id="efe49-176">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="efe49-177">F#Nástroje data protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="efe49-177">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
