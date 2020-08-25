---
title: Asynchronní přístup k souborům (C#)
description: Naučte se používat funkci Async pro přístup k souborům v C#. Můžete volat na asynchronní metody bez použití zpětných volání nebo rozdělení kódu napříč metodami.
ms.date: 08/19/2020
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 9a8db6004e8fff2cb39f0c350b403b56ea619e54
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812039"
---
# <a name="asynchronous-file-access-c"></a><span data-ttu-id="4da5a-104">Asynchronní přístup k souborům (C#)</span><span class="sxs-lookup"><span data-stu-id="4da5a-104">Asynchronous file access (C#)</span></span>

<span data-ttu-id="4da5a-105">K přístupu k souborům můžete použít funkci Async.</span><span class="sxs-lookup"><span data-stu-id="4da5a-105">You can use the async feature to access files.</span></span> <span data-ttu-id="4da5a-106">Pomocí asynchronní funkce můžete zavolat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu napříč více metodami nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="4da5a-106">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="4da5a-107">Chcete-li synchronní asynchronní kód, stačí zavolat asynchronní metodu namísto synchronní metody a přidat k kódu několik klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="4da5a-107">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>

<span data-ttu-id="4da5a-108">Při přidávání asynchronii do volání přístupu k souborům můžete zvážit následující důvody:</span><span class="sxs-lookup"><span data-stu-id="4da5a-108">You might consider the following reasons for adding asynchrony to file access calls:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4da5a-109">Asynchronii umožňuje aplikacím uživatelského rozhraní lépe reagovat, protože vlákno uživatelského rozhraní, které spouští operaci, může provádět i jinou práci.</span><span class="sxs-lookup"><span data-stu-id="4da5a-109">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="4da5a-110">Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), může uživatelské rozhraní zablokovat až do dokončení vstupně-výstupních operací a vlákno uživatelského rozhraní může znovu zpracovat vstupy klávesnice a myši a další události.</span><span class="sxs-lookup"><span data-stu-id="4da5a-110">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>
> - <span data-ttu-id="4da5a-111">Asynchronii zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací tím, že snižuje nutnost vláken.</span><span class="sxs-lookup"><span data-stu-id="4da5a-111">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="4da5a-112">Pokud aplikace používá vyhrazené vlákno na reakci a tisíce požadavků jsou zpracovávány současně, je zapotřebí tisíce vláken.</span><span class="sxs-lookup"><span data-stu-id="4da5a-112">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="4da5a-113">Asynchronní operace často nepotřebují použít vlákno během čekání.</span><span class="sxs-lookup"><span data-stu-id="4da5a-113">Asynchronous operations often don't need to use a thread during the wait.</span></span> <span data-ttu-id="4da5a-114">Na konci se krátce používají existující vlákna dokončení v/v.</span><span class="sxs-lookup"><span data-stu-id="4da5a-114">They use the existing I/O completion thread briefly at the end.</span></span>
> - <span data-ttu-id="4da5a-115">Latence operace přístupu k souboru může být v rámci současných podmínek velmi nízká, ale latence může výrazně zvýšit i v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="4da5a-115">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="4da5a-116">Soubor může být například přesunut na server, který je na celém světě.</span><span class="sxs-lookup"><span data-stu-id="4da5a-116">For example, a file may be moved to a server that's across the world.</span></span>
> - <span data-ttu-id="4da5a-117">Přidaná režie použití asynchronní funkce je malá.</span><span class="sxs-lookup"><span data-stu-id="4da5a-117">The added overhead of using the Async feature is small.</span></span>
> - <span data-ttu-id="4da5a-118">Asynchronní úlohy lze snadno spustit paralelně.</span><span class="sxs-lookup"><span data-stu-id="4da5a-118">Asynchronous tasks can easily be run in parallel.</span></span>

## <a name="use-appropriate-classes"></a><span data-ttu-id="4da5a-119">Použít příslušné třídy</span><span class="sxs-lookup"><span data-stu-id="4da5a-119">Use appropriate classes</span></span>

<span data-ttu-id="4da5a-120">Jednoduché příklady v tomto tématu ukazují <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> a <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4da5a-120">The simple examples in this topic demonstrate <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> and <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4da5a-121">Pro omezenou kontrolu nad vstupně-výstupními operacemi souborů použijte <xref:System.IO.FileStream> třídu, která má možnost, která způsobí, že asynchronní vstupně-výstupní operace proběhne na úrovni operačního systému.</span><span class="sxs-lookup"><span data-stu-id="4da5a-121">For finite control over the file I/O operations, use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="4da5a-122">Pomocí této možnosti se můžete vyhnout blokování vlákna fondu vláken v mnoha případech.</span><span class="sxs-lookup"><span data-stu-id="4da5a-122">By using this option, you can avoid blocking a thread pool thread in many cases.</span></span> <span data-ttu-id="4da5a-123">Chcete-li povolit tuto možnost, zadejte `useAsync=true` `options=FileOptions.Asynchronous` argument nebo ve volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4da5a-123">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>

<span data-ttu-id="4da5a-124">Tuto možnost nemůžete použít s <xref:System.IO.StreamReader> a, <xref:System.IO.StreamWriter> Pokud je otevřete přímo zadáním cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="4da5a-124">You can't use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="4da5a-125">Tuto možnost však můžete použít, pokud jim poskytnete <xref:System.IO.Stream> třídu, kterou <xref:System.IO.FileStream> otevřela.</span><span class="sxs-lookup"><span data-stu-id="4da5a-125">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="4da5a-126">Asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že je vlákno fondu vláken blokované, protože během čekání není zablokované vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4da5a-126">Asynchronous calls are faster in UI apps even if a thread pool thread is blocked, because the UI thread isn't blocked during the wait.</span></span>

## <a name="write-text"></a><span data-ttu-id="4da5a-127">Napsat text</span><span class="sxs-lookup"><span data-stu-id="4da5a-127">Write text</span></span>

<span data-ttu-id="4da5a-128">Následující příklady zapisují text do souboru.</span><span class="sxs-lookup"><span data-stu-id="4da5a-128">The following examples write text to a file.</span></span> <span data-ttu-id="4da5a-129">V každém příkazu await se metoda okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="4da5a-129">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="4da5a-130">Po dokončení vstupně-výstupních operací se metoda obnoví v příkazu, který následuje po příkazu await.</span><span class="sxs-lookup"><span data-stu-id="4da5a-130">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="4da5a-131">Modifikátor Async je v definici metod, které používají příkaz await.</span><span class="sxs-lookup"><span data-stu-id="4da5a-131">The async modifier is in the definition of methods that use the await statement.</span></span>

### <a name="simple-example"></a><span data-ttu-id="4da5a-132">Jednoduchý příklad</span><span class="sxs-lookup"><span data-stu-id="4da5a-132">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleWrite":::

### <a name="finite-control-example"></a><span data-ttu-id="4da5a-133">Příklad omezeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4da5a-133">Finite control example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="WriteText":::

<span data-ttu-id="4da5a-134">Původní příklad obsahuje příkaz `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` , který je kontraktem následujících dvou příkazů:</span><span class="sxs-lookup"><span data-stu-id="4da5a-134">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>

```csharp
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
await theTask;
```

<span data-ttu-id="4da5a-135">První příkaz vrátí úlohu a způsobí, že se zpracování souboru spustí.</span><span class="sxs-lookup"><span data-stu-id="4da5a-135">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="4da5a-136">Druhý příkaz s operátorem await způsobí, že metoda okamžitě ukončí a vrátí jiný úkol.</span><span class="sxs-lookup"><span data-stu-id="4da5a-136">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="4da5a-137">Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za operátorem await.</span><span class="sxs-lookup"><span data-stu-id="4da5a-137">When the file processing later completes, execution returns to the statement that follows the await.</span></span>

## <a name="read-text"></a><span data-ttu-id="4da5a-138">Přečíst text</span><span class="sxs-lookup"><span data-stu-id="4da5a-138">Read text</span></span>

<span data-ttu-id="4da5a-139">Následující příklady čtou text ze souboru.</span><span class="sxs-lookup"><span data-stu-id="4da5a-139">The following examples read text from a file.</span></span>

### <a name="simple-example"></a><span data-ttu-id="4da5a-140">Jednoduchý příklad</span><span class="sxs-lookup"><span data-stu-id="4da5a-140">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleRead":::

### <a name="finite-control-example"></a><span data-ttu-id="4da5a-141">Příklad omezeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4da5a-141">Finite control example</span></span>

<span data-ttu-id="4da5a-142">Text je uložen do vyrovnávací paměti a v tomto případě je umístěn do <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="4da5a-142">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="4da5a-143">Na rozdíl od předchozího příkladu vyhodnocení await vytvoří hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4da5a-143">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="4da5a-144"><xref:System.IO.Stream.ReadAsync%2A>Metoda vrací <xref:System.Threading.Tasks.Task> \<<xref:System.Int32>>, takže vyhodnocení metody await vytvoří `Int32` hodnotu `numRead` po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="4da5a-144">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value `numRead` after the operation completes.</span></span> <span data-ttu-id="4da5a-145">Další informace naleznete v tématu [Asynchronní návratové typy (C#)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4da5a-145">For more information, see [Async Return Types (C#)](async-return-types.md).</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="ReadText":::

## <a name="parallel-asynchronous-io"></a><span data-ttu-id="4da5a-146">Paralelní asynchronní vstupně-výstupní operace</span><span class="sxs-lookup"><span data-stu-id="4da5a-146">Parallel asynchronous I/O</span></span>

<span data-ttu-id="4da5a-147">Následující příklady znázorňují paralelní zpracování zápisem 10 textových souborů.</span><span class="sxs-lookup"><span data-stu-id="4da5a-147">The following examples demonstrate parallel processing by writing 10 text files.</span></span>

### <a name="simple-example"></a><span data-ttu-id="4da5a-148">Jednoduchý příklad</span><span class="sxs-lookup"><span data-stu-id="4da5a-148">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleParallelWrite":::

### <a name="finite-control-example"></a><span data-ttu-id="4da5a-149">Příklad omezeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4da5a-149">Finite control example</span></span>

<span data-ttu-id="4da5a-150">Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> Metoda vrátí úkol, který je poté přidán do seznamu úkolů.</span><span class="sxs-lookup"><span data-stu-id="4da5a-150">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="4da5a-151">`await Task.WhenAll(tasks);`Příkaz ukončí metodu a pokračuje v rámci metody, když je zpracování souborů dokončeno pro všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="4da5a-151">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>

<span data-ttu-id="4da5a-152">Příklad zavře všechny <xref:System.IO.FileStream> instance v `finally` bloku po dokončení úkolů.</span><span class="sxs-lookup"><span data-stu-id="4da5a-152">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="4da5a-153">Pokud byl každý z `FileStream` nich vytvořen v `using` příkazu, `FileStream` může být odstraněn před dokončením úkolu.</span><span class="sxs-lookup"><span data-stu-id="4da5a-153">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>

<span data-ttu-id="4da5a-154">Jakékoli zvýšení výkonu je prakticky zcela úplné od paralelního zpracování, nikoli z asynchronního zpracování.</span><span class="sxs-lookup"><span data-stu-id="4da5a-154">Any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="4da5a-155">Výhody asynchronii jsou, že neodkazují na více vláken a že nevyužívají vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4da5a-155">The advantages of asynchrony are that it doesn't tie up multiple threads, and that it doesn't tie up the user interface thread.</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="ParallelWriteText":::

<span data-ttu-id="4da5a-156">Při použití <xref:System.IO.Stream.WriteAsync%2A> metod a <xref:System.IO.Stream.ReadAsync%2A> můžete zadat <xref:System.Threading.CancellationToken> , které můžete použít k zrušení operace střední-Stream.</span><span class="sxs-lookup"><span data-stu-id="4da5a-156">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="4da5a-157">Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="4da5a-157">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4da5a-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="4da5a-158">See also</span></span>

- [<span data-ttu-id="4da5a-159">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="4da5a-159">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="4da5a-160">Asynchronní návratové typy (C#)</span><span class="sxs-lookup"><span data-stu-id="4da5a-160">Async return types (C#)</span></span>](async-return-types.md)
