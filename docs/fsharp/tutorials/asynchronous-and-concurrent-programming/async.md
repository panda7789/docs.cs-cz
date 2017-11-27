---
title: "Asynchronní programování v F #"
description: "Zjistěte, jak se provádí F # – programování asynchronních prostřednictvím úroveň jazyka programovací model, který je snadno použitelný a přirozený jazyk."
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: 23528d84d0f28283868a1ea316953543d0fd566a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="async-programming-in-f"></a><span data-ttu-id="c5771-104">Asynchronní programování v F #</span><span class="sxs-lookup"><span data-stu-id="c5771-104">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="c5771-105">Některé nepřesnosti byly zjištěny v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="c5771-105">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="c5771-106">Je se přepisuje.</span><span class="sxs-lookup"><span data-stu-id="c5771-106">It is being rewritten.</span></span>  <span data-ttu-id="c5771-107">V tématu [problém #666](https://github.com/dotnet/docs/issues/666) Další informace o změnách.</span><span class="sxs-lookup"><span data-stu-id="c5771-107">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="c5771-108">Asynchronní programování v F # lze provést prostřednictvím modelu programovací jazyk úrovni navržený tak, aby se snadno používá a přirozený jazyk.</span><span class="sxs-lookup"><span data-stu-id="c5771-108">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="c5771-109">Základní asynchronní programování v F # je `Async<'T>`, znázornění práce, které se aktivuje spuštění na pozadí, kde `'T` je buď typu vrácen prostřednictvím speciální `return` – klíčové slovo nebo `unit` pokud asynchronní pracovní postup neobsahuje žádné výsledek určený k vrácení.</span><span class="sxs-lookup"><span data-stu-id="c5771-109">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="c5771-110">Klíče koncept pochopit je, že je typ výraz asynchronní `Async<'T>`, která je jenom na _specifikace_ práce v asynchronním kontextu.</span><span class="sxs-lookup"><span data-stu-id="c5771-110">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="c5771-111">Nebude provedena, dokud ji explicitně spustit s jedním z výchozí funkce (například `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="c5771-111">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="c5771-112">Přestože je toto jiný způsob přemýšlení o pracuje, ukončí až se v praxi poměrně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="c5771-112">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="c5771-113">Řekněme například, že chcete stáhnout HTML z dotnetfoundation.org bez blokování hlavního vlákna.</span><span class="sxs-lookup"><span data-stu-id="c5771-113">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="c5771-114">Můžete ji provést takto:</span><span class="sxs-lookup"><span data-stu-id="c5771-114">You can accomplish it like this:</span></span>

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

let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="c5771-115">A je to!</span><span class="sxs-lookup"><span data-stu-id="c5771-115">And that’s it!</span></span> <span data-ttu-id="c5771-116">Kromě zajištění dostatečného použití `async`, `let!`, a `return`, jedná se jenom normální F # – kód.</span><span class="sxs-lookup"><span data-stu-id="c5771-116">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="c5771-117">Existuje několik syntaktické konstrukce, které jsou vhodné poznamenat:</span><span class="sxs-lookup"><span data-stu-id="c5771-117">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="c5771-118">`let!`vytvoří vazbu výsledek asynchronní výrazu (který se spouští v jiném kontextu).</span><span class="sxs-lookup"><span data-stu-id="c5771-118">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="c5771-119">`use!`funguje stejným způsobem jako `let!`, ale uvolní její vázané prostředky, když probíhá mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="c5771-119">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="c5771-120">`do!`počká asynchronní pracovního postupu, které nic nevrací.</span><span class="sxs-lookup"><span data-stu-id="c5771-120">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="c5771-121">`return`jednoduše vrací výsledek z výrazu asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c5771-121">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="c5771-122">`return!`Spustí jiného pracovního postupu asynchronní a v důsledku vrátí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c5771-122">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="c5771-123">Kromě toho normální `let`, `use`, a `do` klíčová slova můžete používat společně se asynchronních verzích, stejně jako v normálním funkce.</span><span class="sxs-lookup"><span data-stu-id="c5771-123">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="c5771-124">Postup spuštění asynchronní kódu v jazyce F #</span><span class="sxs-lookup"><span data-stu-id="c5771-124">How to start Async Code in F#</span></span> #

<span data-ttu-id="c5771-125">Jak už bylo zmíněno dříve, je asynchronní kód specifikace pracovní provést v jiném kontextu, které musí být explicitně spuštěna.</span><span class="sxs-lookup"><span data-stu-id="c5771-125">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="c5771-126">K tomu dva primární způsoby:</span><span class="sxs-lookup"><span data-stu-id="c5771-126">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="c5771-127">`Async.RunSynchronously`bude na jiné vlákno spustit pracovní postup async a operátoru await její výsledek.</span><span class="sxs-lookup"><span data-stu-id="c5771-127">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

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
 let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="c5771-128">`Async.Start`Asynchronní pracovní postup spustit na jiné vlákno a bude **není** await její výsledek.</span><span class="sxs-lookup"><span data-stu-id="c5771-128">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="c5771-129">Spuštění asynchronních workflow, který je k dispozici pro více konkrétních scénářů i jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="c5771-129">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="c5771-130">Které jsou podrobně popsány [v referenci asynchronní](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="c5771-130">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="c5771-131">Poznámka: na vláken</span><span class="sxs-lookup"><span data-stu-id="c5771-131">A Note on Threads</span></span>

<span data-ttu-id="c5771-132">Fráze "na jiné vlákno" uvedená výše, ale je důležité vědět, že **to neznamená, že asynchronní pracovní postupy jsou průčelí za pro multithreading**.</span><span class="sxs-lookup"><span data-stu-id="c5771-132">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="c5771-133">Pracovní postup ve skutečnosti "skáče" mezi vlákny, úvěrové je pro malé množství času užitečné práci.</span><span class="sxs-lookup"><span data-stu-id="c5771-133">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="c5771-134">Když pracovním postupu asynchronní efektivně "čeká" (například čekání na něco vrátit volání sítě), všechny vlákno, byla úvěrové v době uvolněno až přejděte užitečné práce na něco jiného.</span><span class="sxs-lookup"><span data-stu-id="c5771-134">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="c5771-135">To umožňuje použít systém, který běží na co možná nejefektivněji asynchronní pracovní postupy a jsou pak zejména silné pro scénáře vysoký počet vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="c5771-135">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="c5771-136">Postup přidání paralelismus asynchronní kódu</span><span class="sxs-lookup"><span data-stu-id="c5771-136">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="c5771-137">Někdy můžete potřebovat k provedení více asynchronních úloh paralelně, shromažďování jejich výsledky a je interpretovat nějakým způsobem.</span><span class="sxs-lookup"><span data-stu-id="c5771-137">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="c5771-138">`Async.Parallel`Můžete to provést bez nutnosti použít Task Parallel Library, které by zahrnovat museli coerce `Task<'T>` a `Async<'T>` typy.</span><span class="sxs-lookup"><span data-stu-id="c5771-138">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="c5771-139">Následující příklad použije `Async.Parallel` Pokud chcete stáhnout HTML ze čtyř oblíbených lokalit paralelně, počkejte na dokončení těchto úloh a poté vytiskněte HTML, který byl stažen.</span><span class="sxs-lookup"><span data-stu-id="c5771-139">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "http://www.microsoft.com"
      "http://www.google.com"
      "http://www.amazon.com"
      "http://www.facebook.com" ]

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

## <a name="important-info-and-advice"></a><span data-ttu-id="c5771-140">Důležité informace a Rady, jak</span><span class="sxs-lookup"><span data-stu-id="c5771-140">Important Info and Advice</span></span>

*   <span data-ttu-id="c5771-141">Připojte "Asynchronní" konec všechny funkce, které budete používat</span><span class="sxs-lookup"><span data-stu-id="c5771-141">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="c5771-142">I když je to právě zásady vytváření názvů, je snazší takové věci, jako možnosti rozpoznání rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c5771-142">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="c5771-143">Zejména, pokud jsou synchronní a asynchronní verze stejné rutiny, je vhodné explicitně stavu, která je asynchronní prostřednictvím název.</span><span class="sxs-lookup"><span data-stu-id="c5771-143">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="c5771-144">Naslouchání kompilátoru!</span><span class="sxs-lookup"><span data-stu-id="c5771-144">Listen to the compiler!</span></span>

 <span data-ttu-id="c5771-145">Pro kompilátor jazyka F # je velmi přísná, což téměř znemožní dělat něco troubling jako spustit "asynchronní" kód synchronně.</span><span class="sxs-lookup"><span data-stu-id="c5771-145">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="c5771-146">Pokud narazíte na upozornění, která je znak, jak si myslíte, že se bude kód nebude spouštění.</span><span class="sxs-lookup"><span data-stu-id="c5771-146">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="c5771-147">Pokud se vám kompilátor radostí, váš kód bude s největší pravděpodobností spustit podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="c5771-147">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="c5771-148">Pro programátory C# / VB. vyhledávání do F #</span><span class="sxs-lookup"><span data-stu-id="c5771-148">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="c5771-149">V této části se předpokládá, když jste se seznámili s modelem asynchronní v jazyce C# nebo VB.</span><span class="sxs-lookup"><span data-stu-id="c5771-149">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="c5771-150">Pokud nemáte, [asynchronní programování v jazyce C#](../../../csharp/async.md) je výchozím bodem.</span><span class="sxs-lookup"><span data-stu-id="c5771-150">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="c5771-151">Je zásadní rozdíl mezi C# / VB. asynchronní modelu a modelu asynchronní F #.</span><span class="sxs-lookup"><span data-stu-id="c5771-151">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="c5771-152">Při volání funkce, která vrátí hodnotu `Task` nebo `Task<'T>`, této úlohy je již spuštěno provádění.</span><span class="sxs-lookup"><span data-stu-id="c5771-152">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="c5771-153">Vrátí popisovač představuje asynchronní úlohu již spuštěna.</span><span class="sxs-lookup"><span data-stu-id="c5771-153">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="c5771-154">Naproti tomu při volání funkce asynchronní v F # `Async<'a>` vrátil představuje úlohu, u které bude **generované** v určitém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="c5771-154">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="c5771-155">Vysvětlení tohoto modelu je výkonný, protože umožňuje pro asynchronní úlohy v jazyce F # k zřetězen dohromady snadnější, provést podmíněně a spustit s jemnějšího intervalem ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c5771-155">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="c5771-156">Existuje několik podobnosti a rozdíly vhodné poznamenat.</span><span class="sxs-lookup"><span data-stu-id="c5771-156">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="c5771-157">Podobnosti</span><span class="sxs-lookup"><span data-stu-id="c5771-157">Similarities</span></span>

*   <span data-ttu-id="c5771-158">`let!`, `use!`, a `do!` se podobá `await` při volání metody úlohu asynchronní uvnitř `async{ }` bloku.</span><span class="sxs-lookup"><span data-stu-id="c5771-158">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="c5771-159">Tři klíčová slova lze použít pouze v rámci `async { }` bloku, podobně jako postupy `await` jde volat jenom uvnitř `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="c5771-159">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="c5771-160">Stručně řečeno `let!` je pro, když chcete zaznamenat a použít výsledek, `use!` je něco jehož prostředky by měly získat čištění po se používají stejné ale a `do!` je pro, pokud chcete pro čekání asynchronní pracovní postup s žádnou návratovou hodnotu na dokončení než budete pokračovat.</span><span class="sxs-lookup"><span data-stu-id="c5771-160">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="c5771-161">F # podporuje datový paralelismus podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c5771-161">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="c5771-162">I když ho pracuje velmi odlišně `Async.Parallel` odpovídá `Task.WhenAll` pro scénáře podmínka mimo výsledky sadu asynchronních úloh po dokončení se všechny.</span><span class="sxs-lookup"><span data-stu-id="c5771-162">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="c5771-163">Rozdíly</span><span class="sxs-lookup"><span data-stu-id="c5771-163">Differences</span></span>

*   <span data-ttu-id="c5771-164">Vnořené `let!` není povolena, na rozdíl od vnořené`await`</span><span class="sxs-lookup"><span data-stu-id="c5771-164">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="c5771-165">Na rozdíl od `await`, které mohou být použity po neomezenou dobu, `let!` nelze a musíte mít jeho výsledek vázaný před jeho použitím uvnitř jiného `let!`, `do!`, nebo `use!`.</span><span class="sxs-lookup"><span data-stu-id="c5771-165">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="c5771-166">Podpora zrušení je jednodušší v jazyce F # než v jazyce C# nebo VB.</span><span class="sxs-lookup"><span data-stu-id="c5771-166">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="c5771-167">Podpora zrušení úloh polovině prostřednictvím jeho spuštění v C# / VB. vyžaduje kontrolu `IsCancellationRequested` vlastnost nebo volání `ThrowIfCancellationRequested()` na `CancellationToken` objekt, který je předán do asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="c5771-167">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="c5771-168">F # asynchronní pracovní postupy jsou naopak více přirozeně zrušit.</span><span class="sxs-lookup"><span data-stu-id="c5771-168">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="c5771-169">Zrušení je jednoduchý proces třech krocích.</span><span class="sxs-lookup"><span data-stu-id="c5771-169">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="c5771-170">Vytvořte novou `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="c5771-170">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="c5771-171">Předejte ji do počáteční funkce.</span><span class="sxs-lookup"><span data-stu-id="c5771-171">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="c5771-172">Volání `Cancel` na tokenu.</span><span class="sxs-lookup"><span data-stu-id="c5771-172">Call `Cancel` on the token.</span></span>

<span data-ttu-id="c5771-173">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c5771-173">Example:</span></span>

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="c5771-174">A je to!</span><span class="sxs-lookup"><span data-stu-id="c5771-174">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="c5771-175">Další prostředky:</span><span class="sxs-lookup"><span data-stu-id="c5771-175">Further resources:</span></span>

*   [<span data-ttu-id="c5771-176">Asynchronní pracovní postupy na webu MSDN</span><span class="sxs-lookup"><span data-stu-id="c5771-176">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="c5771-177">Asynchronní pořadí pro F #</span><span class="sxs-lookup"><span data-stu-id="c5771-177">Asynchronous Sequences for F#</span></span>](http://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="c5771-178">Nástroje F # dat protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="c5771-178">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
