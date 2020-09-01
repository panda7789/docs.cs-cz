---
title: Vstupně-výstupní kanály – .NET
description: Zjistěte, jak efektivně používat kanály v/v v rozhraní .NET a vyhnout se problémům ve vašem kódu.
ms.date: 08/27/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: a24d7f5c22c936cd3fd3fdc51f0f3ace56386574
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271981"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="aa656-103">System. IO. Pipelines v .NET</span><span class="sxs-lookup"><span data-stu-id="aa656-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="aa656-104"><xref:System.IO.Pipelines> je nová knihovna, která je navržena tak, aby usnadnila vysoce výkonné vstupně-výstupní operace v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="aa656-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="aa656-105">Jedná se o knihovnu, která cílí na .NET Standard, která funguje na všech implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="aa656-105">It's a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="aa656-106">Jaký problém řeší System. IO. Pipelines</span><span class="sxs-lookup"><span data-stu-id="aa656-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="aa656-107">Aplikace, které analyzují streamovaná data, se skládají ze standardizovaného kódu, který má mnoho toků specializovaného a neobvyklého kódu</span><span class="sxs-lookup"><span data-stu-id="aa656-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="aa656-108">Často používaný kód a zvláštní případ je složitý a obtížně udržovatelný.</span><span class="sxs-lookup"><span data-stu-id="aa656-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="aa656-109">`System.IO.Pipelines` bylo navrženo pro:</span><span class="sxs-lookup"><span data-stu-id="aa656-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="aa656-110">Analýza dat streamování je vysoce výkonná.</span><span class="sxs-lookup"><span data-stu-id="aa656-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="aa656-111">Snižte složitost kódu.</span><span class="sxs-lookup"><span data-stu-id="aa656-111">Reduce code complexity.</span></span>

<span data-ttu-id="aa656-112">Následující kód je typický pro server TCP, který přijímá zprávy oddělené řádky (oddělený od `'\n'` ) od klienta:</span><span class="sxs-lookup"><span data-stu-id="aa656-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="aa656-113">Předchozí kód má několik problémů:</span><span class="sxs-lookup"><span data-stu-id="aa656-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="aa656-114">V jednom volání metody nemusí být přijata celá zpráva (konce řádku) `ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="aa656-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="aa656-115">Ignoruje výsledek `stream.ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="aa656-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="aa656-116">`stream.ReadAsync` Vrátí, kolik dat bylo přečteno.</span><span class="sxs-lookup"><span data-stu-id="aa656-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="aa656-117">Nezpracovává případ, kdy je více řádků čteno v jednom `ReadAsync` volání.</span><span class="sxs-lookup"><span data-stu-id="aa656-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="aa656-118">Přiděluje `byte` pole s každým čtením.</span><span class="sxs-lookup"><span data-stu-id="aa656-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="aa656-119">Chcete-li opravit předchozí problémy, jsou vyžadovány následující změny:</span><span class="sxs-lookup"><span data-stu-id="aa656-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="aa656-120">Ukládat příchozí data do vyrovnávací paměti, dokud se nenajde nový řádek.</span><span class="sxs-lookup"><span data-stu-id="aa656-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="aa656-121">Analyzuje všechny řádky vrácené ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="aa656-122">Je možné, že je řádek větší než 1 KB (1024 bajtů).</span><span class="sxs-lookup"><span data-stu-id="aa656-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="aa656-123">Kód musí změnit velikost vstupní vyrovnávací paměti, dokud není nalezen oddělovač, aby odpovídal celému řádku uvnitř vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="aa656-124">Pokud se změní velikost vyrovnávací paměti, ve vstupu se zobrazí další kopie vyrovnávací paměti, ve kterých se objeví delší řádky.</span><span class="sxs-lookup"><span data-stu-id="aa656-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="aa656-125">Chcete-li snížit množství nevyužitého místa, Zkomprimujte vyrovnávací paměť použitou pro čtení řádků.</span><span class="sxs-lookup"><span data-stu-id="aa656-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="aa656-126">Zvažte použití sdružování vyrovnávací paměti, abyste se vyhnuli opakovanému přidělování paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="aa656-127">Následující kód řeší některé z těchto problémů:</span><span class="sxs-lookup"><span data-stu-id="aa656-127">The following code addresses some of these problems:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

<span data-ttu-id="aa656-128">Předchozí kód je složitý a neřeší všechny zjištěné problémy.</span><span class="sxs-lookup"><span data-stu-id="aa656-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="aa656-129">Vysoce výkonné sítě obvykle znamenají psaní velmi složitého kódu pro maximalizaci výkonu.</span><span class="sxs-lookup"><span data-stu-id="aa656-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="aa656-130">`System.IO.Pipelines` bylo navrženo tak, aby byl tento typ kódu snazší.</span><span class="sxs-lookup"><span data-stu-id="aa656-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="aa656-131">Příkazem</span><span class="sxs-lookup"><span data-stu-id="aa656-131">Pipe</span></span>

<span data-ttu-id="aa656-132"><xref:System.IO.Pipelines.Pipe>Třídu lze použít k vytvoření `PipeWriter/PipeReader` páru.</span><span class="sxs-lookup"><span data-stu-id="aa656-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="aa656-133">Všechna data zapsaná do nástroje `PipeWriter` jsou k dispozici v `PipeReader` :</span><span class="sxs-lookup"><span data-stu-id="aa656-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="aa656-134">Základní použití kanálu</span><span class="sxs-lookup"><span data-stu-id="aa656-134">Pipe basic usage</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

<span data-ttu-id="aa656-135">Existují dvě smyčky:</span><span class="sxs-lookup"><span data-stu-id="aa656-135">There are two loops:</span></span>

* <span data-ttu-id="aa656-136">`FillPipeAsync` čte z `Socket` a zápisy do `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="aa656-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="aa656-137">`ReadPipeAsync` čte z `PipeReader` a analyzuje příchozí řádky.</span><span class="sxs-lookup"><span data-stu-id="aa656-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="aa656-138">Nejsou přiděleny žádné explicitní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="aa656-139">Veškerá správa vyrovnávací paměti je delegována na `PipeReader` `PipeWriter` implementace a.</span><span class="sxs-lookup"><span data-stu-id="aa656-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="aa656-140">Delegování správy vyrovnávací paměti usnadňuje využívání kódu pro zaměření pouze na obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="aa656-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="aa656-141">V první smyčce:</span><span class="sxs-lookup"><span data-stu-id="aa656-141">In the first loop:</span></span>

* <span data-ttu-id="aa656-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> se volá, aby se získala paměť ze základního zapisovače.</span><span class="sxs-lookup"><span data-stu-id="aa656-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="aa656-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> je volána, aby informovala, kolik `PipeWriter` dat bylo zapsáno do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="aa656-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> je volána k zpřístupnění dat pro `PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="aa656-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="aa656-145">Ve druhé smyčce `PipeReader` využívá vyrovnávací paměti zapsané `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="aa656-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="aa656-146">Vyrovnávací paměti přicházejí ze soketu.</span><span class="sxs-lookup"><span data-stu-id="aa656-146">The buffers come from the socket.</span></span> <span data-ttu-id="aa656-147">Volání na `PipeReader.ReadAsync` :</span><span class="sxs-lookup"><span data-stu-id="aa656-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="aa656-148">Vrátí <xref:System.IO.Pipelines.ReadResult> , který obsahuje dvě důležité informace:</span><span class="sxs-lookup"><span data-stu-id="aa656-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="aa656-149">Data, která byla načtena ve formě `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="aa656-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="aa656-150">Logická hodnota `IsCompleted` , která označuje, zda bylo dosaženo konce dat (EOF).</span><span class="sxs-lookup"><span data-stu-id="aa656-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="aa656-151">Po nalezení oddělovače na konci řádku (konce řádku) a při analýze řádku:</span><span class="sxs-lookup"><span data-stu-id="aa656-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="aa656-152">Logika zpracuje vyrovnávací paměť a přeskočí, co je již zpracováno.</span><span class="sxs-lookup"><span data-stu-id="aa656-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="aa656-153">`PipeReader.AdvanceTo` je volána, aby informovala, `PipeReader` kolik dat bylo spotřebováno a zkontrolováno.</span><span class="sxs-lookup"><span data-stu-id="aa656-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="aa656-154">Smyčka čtečky a zapisovače končí voláním `Complete` .</span><span class="sxs-lookup"><span data-stu-id="aa656-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="aa656-155">`Complete` umožňuje původnímu kanálu uvolnit přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="aa656-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="aa656-156">Řízení zatížení a tok</span><span class="sxs-lookup"><span data-stu-id="aa656-156">Backpressure and flow control</span></span>

<span data-ttu-id="aa656-157">V ideálním případě se jedná o společné čtení a analýzu:</span><span class="sxs-lookup"><span data-stu-id="aa656-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="aa656-158">Vlákno zápisu spotřebovává data ze sítě a umístí je do vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="aa656-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="aa656-159">Podproces analýzy zodpovídá za vytváření vhodných datových struktur.</span><span class="sxs-lookup"><span data-stu-id="aa656-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="aa656-160">Analýza obvykle trvá více času, než stačí kopírovat bloky dat ze sítě:</span><span class="sxs-lookup"><span data-stu-id="aa656-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="aa656-161">Vlákno čtení získá před vláknem analýzy.</span><span class="sxs-lookup"><span data-stu-id="aa656-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="aa656-162">Vlákno čtení musí buď zpomalit, nebo přidělit více paměti pro uložení dat pro vlákno analýzy.</span><span class="sxs-lookup"><span data-stu-id="aa656-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="aa656-163">Pro zajištění optimálního výkonu existuje zůstatek mezi častými pozastavením a přidělením více paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="aa656-164">Chcete-li vyřešit předchozí problém, `Pipe` má dvě nastavení pro řízení toku dat:</span><span class="sxs-lookup"><span data-stu-id="aa656-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="aa656-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Určuje, kolik dat by mělo být uloženo do vyrovnávací paměti před voláními pro <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pozastavení.</span><span class="sxs-lookup"><span data-stu-id="aa656-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="aa656-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Určuje, kolik dat musí čtenář sledovat před `PipeWriter.FlushAsync` pokračováním volání.</span><span class="sxs-lookup"><span data-stu-id="aa656-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagram s ResumeWriterThreshold a PauseWriterThreshold](media/pipelines/resume-pause.png)

<span data-ttu-id="aa656-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="aa656-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="aa656-169">Vrátí nedokončenou `ValueTask<FlushResult>` , pokud je množství dat v `Pipe` křížení `PauseWriterThreshold` .</span><span class="sxs-lookup"><span data-stu-id="aa656-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="aa656-170">Dokončí, `ValueTask<FlushResult>` když bude menší než `ResumeWriterThreshold` .</span><span class="sxs-lookup"><span data-stu-id="aa656-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="aa656-171">Pomocí dvou hodnot se vyhnete rychlému cyklování, ke kterému může dojít, když se použije jedna hodnota.</span><span class="sxs-lookup"><span data-stu-id="aa656-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="aa656-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="aa656-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="aa656-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="aa656-173">PipeScheduler</span></span>

<span data-ttu-id="aa656-174">Obvykle při použití `async` a `await` se asynchronní kód obnovuje buď na, <xref:System.Threading.Tasks.TaskScheduler> nebo v aktuální <xref:System.Threading.SynchronizationContext> .</span><span class="sxs-lookup"><span data-stu-id="aa656-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="aa656-175">Při provádění vstupně-výstupních operací je důležité mít detailní kontrolu nad tím, kde se vstupně-výstupní operace provádí.</span><span class="sxs-lookup"><span data-stu-id="aa656-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="aa656-176">Tento ovládací prvek umožňuje efektivní využití mezipamětí CPU.</span><span class="sxs-lookup"><span data-stu-id="aa656-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="aa656-177">Efektivní ukládání do mezipaměti je klíčové pro vysoce výkonné aplikace, jako jsou webové servery.</span><span class="sxs-lookup"><span data-stu-id="aa656-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="aa656-178"><xref:System.IO.Pipelines.PipeScheduler> poskytuje kontrolu nad tím, kde jsou spouštěna asynchronní zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="aa656-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="aa656-179">Ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="aa656-179">By default:</span></span>

* <span data-ttu-id="aa656-180">Používá se aktuální <xref:System.Threading.SynchronizationContext> .</span><span class="sxs-lookup"><span data-stu-id="aa656-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="aa656-181">Pokud je k dispozici `SynchronizationContext` , používá fond vláken ke spouštění zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="aa656-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

<span data-ttu-id="aa656-182">[PipeScheduler.](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) Apartment je <xref:System.IO.Pipelines.PipeScheduler> implementace, která zařadí zpětná volání do fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="aa656-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="aa656-183">`PipeScheduler.ThreadPool` je výchozí a obecně nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="aa656-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="aa656-184">[PipeScheduler. inline](xref:System.IO.Pipelines.PipeScheduler.Inline) může způsobit nezamýšlené důsledky, jako je zablokování.</span><span class="sxs-lookup"><span data-stu-id="aa656-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="aa656-185">Resetování kanálu</span><span class="sxs-lookup"><span data-stu-id="aa656-185">Pipe reset</span></span>

<span data-ttu-id="aa656-186">Je často efektivní použít `Pipe` objekt.</span><span class="sxs-lookup"><span data-stu-id="aa656-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="aa656-187">Chcete-li obnovit kanál, zavolejte, <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> Když `PipeReader` `PipeWriter` jsou i dokončeny.</span><span class="sxs-lookup"><span data-stu-id="aa656-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="aa656-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="aa656-188">PipeReader</span></span>

<span data-ttu-id="aa656-189"><xref:System.IO.Pipelines.PipeReader> spravuje paměť jménem volajícího.</span><span class="sxs-lookup"><span data-stu-id="aa656-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="aa656-190">**Always** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> Po volání vždy volejte <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aa656-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aa656-191">To vám umožní `PipeReader` zjistit, kdy se volající provede s pamětí, aby se mohl sledovat.</span><span class="sxs-lookup"><span data-stu-id="aa656-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="aa656-192">`ReadOnlySequence<byte>`Vrácená z `PipeReader.ReadAsync` je platná pouze do volání metody `PipeReader.AdvanceTo` .</span><span class="sxs-lookup"><span data-stu-id="aa656-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="aa656-193">Použití po volání není povoleno `ReadOnlySequence<byte>` `PipeReader.AdvanceTo` .</span><span class="sxs-lookup"><span data-stu-id="aa656-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="aa656-194">`PipeReader.AdvanceTo` přebírá dva <xref:System.SequencePosition> argumenty:</span><span class="sxs-lookup"><span data-stu-id="aa656-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="aa656-195">První argument určuje, kolik paměti bylo spotřebováno.</span><span class="sxs-lookup"><span data-stu-id="aa656-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="aa656-196">Druhý argument určuje, kolik paměti bylo pozorováno.</span><span class="sxs-lookup"><span data-stu-id="aa656-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="aa656-197">Označení dat jako spotřebované znamená, že kanál může vrátit paměť do podkladového fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="aa656-198">Označení dat jako pozorovaných řídí, co dělá další volání `PipeReader.ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="aa656-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="aa656-199">Označení všeho jako pozorovaného znamená, že další volání `PipeReader.ReadAsync` nebude vráceno, dokud nebudou do kanálu zapsána další data.</span><span class="sxs-lookup"><span data-stu-id="aa656-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="aa656-200">Jakákoli jiná hodnota provede další volání `PipeReader.ReadAsync` ihned se zjištěnými *a* nepozorovanými daty, ale ne data, která již byla spotřebována.</span><span class="sxs-lookup"><span data-stu-id="aa656-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="aa656-201">Čtení scénářů streamování dat</span><span class="sxs-lookup"><span data-stu-id="aa656-201">Read streaming data scenarios</span></span>

<span data-ttu-id="aa656-202">Při pokusu o čtení dat streamování je k dispozici několik typických vzorů:</span><span class="sxs-lookup"><span data-stu-id="aa656-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="aa656-203">Pokud má datový proud data, analyzujte jednu zprávu.</span><span class="sxs-lookup"><span data-stu-id="aa656-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="aa656-204">Pokud má datový proud data, analyzujte všechny dostupné zprávy.</span><span class="sxs-lookup"><span data-stu-id="aa656-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="aa656-205">Následující příklady používají `TryParseMessage` metodu pro analýzu zpráv z `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="aa656-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="aa656-206">`TryParseMessage` analyzuje jednu zprávu a aktualizuje vstupní vyrovnávací paměť pro oříznutí analyzované zprávy z vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="aa656-207">`TryParseMessage` není součástí .NET, je metoda psaná uživatelem, která se používá v následujících oddílech.</span><span class="sxs-lookup"><span data-stu-id="aa656-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="aa656-208">Číst jednu zprávu</span><span class="sxs-lookup"><span data-stu-id="aa656-208">Read a single message</span></span>

<span data-ttu-id="aa656-209">Následující kód přečte jednu zprávu z `PipeReader` a a vrátí ji volajícímu.</span><span class="sxs-lookup"><span data-stu-id="aa656-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

<span data-ttu-id="aa656-210">Předcházející kód:</span><span class="sxs-lookup"><span data-stu-id="aa656-210">The preceding code:</span></span>

* <span data-ttu-id="aa656-211">Analyzuje jednu zprávu.</span><span class="sxs-lookup"><span data-stu-id="aa656-211">Parses a single message.</span></span>
* <span data-ttu-id="aa656-212">Aktualizuje spotřebované `SequencePosition` a zkoumané, `SequencePosition` aby odkazoval na začátek oříznuté vstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="aa656-213">Tyto dva `SequencePosition` argumenty jsou aktualizovány, protože `TryParseMessage` odebere analyzovanou zprávu ze vstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="aa656-214">Obecně platí, že při analýze jedné zprávy z vyrovnávací paměti by měla být prověřená poloha jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="aa656-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="aa656-215">Konec zprávy</span><span class="sxs-lookup"><span data-stu-id="aa656-215">The end of the message.</span></span>
* <span data-ttu-id="aa656-216">Konec přijaté vyrovnávací paměti, pokud nebyla nalezena žádná zpráva.</span><span class="sxs-lookup"><span data-stu-id="aa656-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="aa656-217">Jeden případ zprávy má nejvíce potenciál pro chyby.</span><span class="sxs-lookup"><span data-stu-id="aa656-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="aa656-218">Předání špatných hodnot do *prověření* může mít za následek výjimku z důvodu nedostatku paměti nebo nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="aa656-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="aa656-219">Další informace najdete v části [běžné problémy PipeReader](#gotchas) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="aa656-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="aa656-220">Čtení více zpráv</span><span class="sxs-lookup"><span data-stu-id="aa656-220">Reading multiple messages</span></span>

<span data-ttu-id="aa656-221">Následující kód přečte všechny zprávy z `PipeReader` volání a a `ProcessMessageAsync` každý z nich.</span><span class="sxs-lookup"><span data-stu-id="aa656-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a><span data-ttu-id="aa656-222">Zrušení</span><span class="sxs-lookup"><span data-stu-id="aa656-222">Cancellation</span></span>

<span data-ttu-id="aa656-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="aa656-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="aa656-224">Podporuje předávání <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="aa656-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="aa656-225">Vyvolá výjimku <xref:System.OperationCanceledException> , pokud `CancellationToken` je zrušena, když dojde k nedokončenému čtení.</span><span class="sxs-lookup"><span data-stu-id="aa656-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="aa656-226">Podporuje způsob, jak zrušit aktuální operaci čtení prostřednictvím <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> , která zabraňuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa656-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="aa656-227">Volání `PipeReader.CancelPendingRead` způsobí, že aktuální nebo další volání `PipeReader.ReadAsync` vrátí hodnotu <xref:System.IO.Pipelines.ReadResult> s `IsCanceled` nastavenou na `true` .</span><span class="sxs-lookup"><span data-stu-id="aa656-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="aa656-228">To může být užitečné pro zastavení stávající smyčky čtení v nedestruktivním a nevýjimečném způsobu.</span><span class="sxs-lookup"><span data-stu-id="aa656-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="aa656-229">PipeReader běžné problémy</span><span class="sxs-lookup"><span data-stu-id="aa656-229">PipeReader common problems</span></span>

* <span data-ttu-id="aa656-230">Předání nesprávných hodnot do `consumed` nebo `examined` může mít za následek čtení dat již přečtených.</span><span class="sxs-lookup"><span data-stu-id="aa656-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="aa656-231">`buffer.End`Při předávání jako prověření může dojít k následujícím akcím:</span><span class="sxs-lookup"><span data-stu-id="aa656-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="aa656-232">Data zastavena</span><span class="sxs-lookup"><span data-stu-id="aa656-232">Stalled data</span></span>
  * <span data-ttu-id="aa656-233">Možnou výjimku z paměti (OOM), pokud nejsou data spotřebována.</span><span class="sxs-lookup"><span data-stu-id="aa656-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="aa656-234">Například `PipeReader.AdvanceTo(position, buffer.End)` při zpracování jedné zprávy v čase z vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="aa656-235">Předání špatných hodnot do `consumed` nebo `examined` může způsobit nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="aa656-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="aa656-236">Například pokud se `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` nezměnila, způsobí to, že se další volání `PipeReader.ReadAsync` vrátí hned před přijetím nových dat.</span><span class="sxs-lookup"><span data-stu-id="aa656-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="aa656-237">Předání špatných hodnot do `consumed` nebo `examined` může mít za následek nekonečné ukládání do vyrovnávací paměti (OOM).</span><span class="sxs-lookup"><span data-stu-id="aa656-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="aa656-238">Použití `ReadOnlySequence<byte>` metody po volání `PipeReader.AdvanceTo` může mít za následek poškození paměti (použijte po uvolnění).</span><span class="sxs-lookup"><span data-stu-id="aa656-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="aa656-239">Selhání volání `PipeReader.Complete/CompleteAsync` může způsobit nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="aa656-240">Kontrola <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> a ukončení logiky čtení před zpracováním vyrovnávací paměti má za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="aa656-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="aa656-241">Stav ukončení smyčky musí být založen na `ReadResult.Buffer.IsEmpty` a `ReadResult.IsCompleted` .</span><span class="sxs-lookup"><span data-stu-id="aa656-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="aa656-242">Tato nesprávně by mohla způsobit nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="aa656-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="aa656-243">Problematický kód</span><span class="sxs-lookup"><span data-stu-id="aa656-243">Problematic code</span></span>

<span data-ttu-id="aa656-244">❌**Ztráta dat**</span><span class="sxs-lookup"><span data-stu-id="aa656-244">❌ **Data loss**</span></span>

<span data-ttu-id="aa656-245">`ReadResult`Může vrátit konečný segment dat, když `IsCompleted` je nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="aa656-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="aa656-246">Tato data nebudou čtena před ukončením smyčky pro čtení. výsledkem bude ztráta dat.</span><span class="sxs-lookup"><span data-stu-id="aa656-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="aa656-247">❌**Nekonečná smyčka**</span><span class="sxs-lookup"><span data-stu-id="aa656-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="aa656-248">Následující logika může mít za následek nekonečnou smyčku, pokud `Result.IsCompleted` není, `true` ale ve vyrovnávací paměti nikdy není úplná zpráva.</span><span class="sxs-lookup"><span data-stu-id="aa656-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="aa656-249">Tady je další část kódu se stejným problémem.</span><span class="sxs-lookup"><span data-stu-id="aa656-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="aa656-250">Před kontrolou se kontroluje, jestli není prázdná vyrovnávací paměť `ReadResult.IsCompleted` .</span><span class="sxs-lookup"><span data-stu-id="aa656-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="aa656-251">Vzhledem k tomu, že je v `else if` , bude tato smyčka nepřetržitě v případě, že ve vyrovnávací paměti stále není úplná zpráva.</span><span class="sxs-lookup"><span data-stu-id="aa656-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="aa656-252">❌**Neočekávané zablokování**</span><span class="sxs-lookup"><span data-stu-id="aa656-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="aa656-253">Nepodmíněné volání `PipeReader.AdvanceTo` s `buffer.End` na `examined` pozici může vést k zablokování při analýze jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="aa656-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="aa656-254">Následující volání `PipeReader.AdvanceTo` nebude vráceno do:</span><span class="sxs-lookup"><span data-stu-id="aa656-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="aa656-255">Do kanálu se zapisují další data.</span><span class="sxs-lookup"><span data-stu-id="aa656-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="aa656-256">A nová data se předtím nezkoumala.</span><span class="sxs-lookup"><span data-stu-id="aa656-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="aa656-257">❌**Nedostatek paměti (OOM)**</span><span class="sxs-lookup"><span data-stu-id="aa656-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="aa656-258">V následujících podmínkách uchovává následující kód ukládání do vyrovnávací paměti, dokud <xref:System.OutOfMemoryException> nedojde k:</span><span class="sxs-lookup"><span data-stu-id="aa656-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="aa656-259">Není k dispozici žádná maximální velikost zprávy.</span><span class="sxs-lookup"><span data-stu-id="aa656-259">There's no maximum message size.</span></span>
* <span data-ttu-id="aa656-260">Data vrácená z `PipeReader` nevytvářejí úplnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="aa656-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="aa656-261">Například neprovádí úplnou zprávu, protože druhá strana zapisuje velkou zprávu (například zpráva o velikosti 4 GB).</span><span class="sxs-lookup"><span data-stu-id="aa656-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="aa656-262">❌**Poškození paměti**</span><span class="sxs-lookup"><span data-stu-id="aa656-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="aa656-263">Při psaní pomocníků, které čtou vyrovnávací paměť, je nutné před voláním zkopírovat všechny vrácené datové části `Advance` .</span><span class="sxs-lookup"><span data-stu-id="aa656-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="aa656-264">Následující příklad vrátí paměť, která `Pipe` byla zahozena a může ji znovu použít pro další operaci (čtení/zápis).</span><span class="sxs-lookup"><span data-stu-id="aa656-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="aa656-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="aa656-265">PipeWriter</span></span>

<span data-ttu-id="aa656-266"><xref:System.IO.Pipelines.PipeWriter>Spravuje vyrovnávací paměti pro psaní jménem volajícího.</span><span class="sxs-lookup"><span data-stu-id="aa656-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="aa656-267">`PipeWriter` implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) .</span><span class="sxs-lookup"><span data-stu-id="aa656-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="aa656-268">`IBufferWriter<byte>` umožňuje získat přístup k vyrovnávací paměti, aby bylo možné provádět zápisy bez dalších kopií vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

<span data-ttu-id="aa656-269">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="aa656-269">The previous code:</span></span>

* <span data-ttu-id="aa656-270">Vyžádá vyrovnávací paměť o velikosti alespoň 5 bajtů z s `PipeWriter` použitím <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> .</span><span class="sxs-lookup"><span data-stu-id="aa656-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="aa656-271">Zapíše bajty pro řetězec ASCII `"Hello"` na vrácenou `Memory<byte>` .</span><span class="sxs-lookup"><span data-stu-id="aa656-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="aa656-272">Volání <xref:System.IO.Pipelines.PipeWriter.Advance%2A> indikující, kolik bajtů bylo zapsáno do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="aa656-273">Vyprázdní `PipeWriter` , čímž pošle bajty na základní zařízení.</span><span class="sxs-lookup"><span data-stu-id="aa656-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="aa656-274">Předchozí metoda zápisu používá vyrovnávací paměti, které poskytuje `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="aa656-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="aa656-275">Alternativně <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="aa656-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="aa656-276">Zkopíruje existující vyrovnávací paměť do `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="aa656-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="aa656-277">Volání `GetSpan` `Advance` podle potřeby a volání <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="aa656-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a><span data-ttu-id="aa656-278">Zrušení</span><span class="sxs-lookup"><span data-stu-id="aa656-278">Cancellation</span></span>

<span data-ttu-id="aa656-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> podporuje předávání <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="aa656-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="aa656-280">Předání `CancellationToken` výsledků v `OperationCanceledException` případě zrušení tokenu v době, kdy dojde k vyprázdnění.</span><span class="sxs-lookup"><span data-stu-id="aa656-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="aa656-281">`PipeWriter.FlushAsync` podporuje způsob, jak zrušit aktuální operaci vyprázdnění prostřednictvím <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="aa656-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="aa656-282">Volání `PipeWriter.CancelPendingFlush` způsobí, že aktuální nebo další volání `PipeWriter.FlushAsync` nebo `PipeWriter.WriteAsync` vrátí hodnotu <xref:System.IO.Pipelines.FlushResult> s `IsCanceled` nastavenou na `true` .</span><span class="sxs-lookup"><span data-stu-id="aa656-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="aa656-283">To může být užitečné, pokud chcete zablokovat vyprázdnit vyřazení v nedestruktivním a nevýjimečném způsobu.</span><span class="sxs-lookup"><span data-stu-id="aa656-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="aa656-284">PipeWriter běžné problémy</span><span class="sxs-lookup"><span data-stu-id="aa656-284">PipeWriter common problems</span></span>

* <span data-ttu-id="aa656-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> a <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> vrátí vyrovnávací paměť s minimální požadovanou velikostí paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="aa656-286">**Neberete** přesnou velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="aa656-287">Není nijak zaručeno, že po sobě jdoucí volání budou vracet stejnou vyrovnávací paměť nebo vyrovnávací paměť se stejnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="aa656-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="aa656-288">Po volání musí být vyžádána nová vyrovnávací paměť, aby bylo možné <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pokračovat v zápisu více dat.</span><span class="sxs-lookup"><span data-stu-id="aa656-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="aa656-289">Dřív získaná vyrovnávací paměť se nedá zapsat do.</span><span class="sxs-lookup"><span data-stu-id="aa656-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="aa656-290">Volání `GetMemory` nebo `GetSpan` i v případě, že je neúplné volání `FlushAsync` není bezpečné.</span><span class="sxs-lookup"><span data-stu-id="aa656-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="aa656-291">Volání `Complete` nebo `CompleteAsync` i v případě nevyprázdněných dat může mít za následek poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="aa656-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="aa656-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="aa656-292">IDuplexPipe</span></span>

<span data-ttu-id="aa656-293"><xref:System.IO.Pipelines.IDuplexPipe>Je kontrakt pro typy, které podporují čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="aa656-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="aa656-294">Například síťové připojení by představovalo `IDuplexPipe` .</span><span class="sxs-lookup"><span data-stu-id="aa656-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="aa656-295">Na rozdíl od `Pipe` , který obsahuje `PipeReader` a a `PipeWriter` , `IDuplexPipe` představuje jednu stranu úplného duplexního připojení.</span><span class="sxs-lookup"><span data-stu-id="aa656-295">Unlike `Pipe`, which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="aa656-296">To znamená, že obsah, který se zapisuje do, nebude `PipeWriter` číst z `PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="aa656-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="aa656-297">Streamy</span><span class="sxs-lookup"><span data-stu-id="aa656-297">Streams</span></span>

<span data-ttu-id="aa656-298">Při čtení nebo zápisu dat datového proudu obvykle čtete data pomocí rušení serializátoru a zapisují data pomocí serializátoru.</span><span class="sxs-lookup"><span data-stu-id="aa656-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="aa656-299">Většina těchto rozhraní API pro čtení a zápis streamování má `Stream` parametr.</span><span class="sxs-lookup"><span data-stu-id="aa656-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="aa656-300">Aby bylo snazší je integrovat s těmito stávajícími rozhraními API, `PipeReader` a `PipeWriter` vystavit <xref:System.IO.Pipelines.PipeReader.AsStream%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="aa656-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A> method.</span></span> <span data-ttu-id="aa656-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> vrací `Stream` implementaci kolem `PipeReader` nebo `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="aa656-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>

### <a name="stream-example"></a><span data-ttu-id="aa656-302">Příklad streamu</span><span class="sxs-lookup"><span data-stu-id="aa656-302">Stream example</span></span>

<span data-ttu-id="aa656-303">`PipeReader``PipeWriter`instance a lze vytvořit pomocí statických `Create` metod daného <xref:System.IO.Stream> objektu a volitelných odpovídajících možností vytváření.</span><span class="sxs-lookup"><span data-stu-id="aa656-303">`PipeReader` and `PipeWriter` instances can be created using the static `Create` methods given a <xref:System.IO.Stream> object and optional corresponding creation options.</span></span>

<span data-ttu-id="aa656-304"><xref:System.IO.Pipelines.StreamPipeReaderOptions>Umožňuje řídit vytvoření `PipeReader` instance s následujícími parametry:</span><span class="sxs-lookup"><span data-stu-id="aa656-304">The <xref:System.IO.Pipelines.StreamPipeReaderOptions> allow for control over the creation of the `PipeReader` instance with the following parameters:</span></span>

- <span data-ttu-id="aa656-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> je minimální velikost vyrovnávací paměti v bajtech použitých při pronajmutí paměti z fondu a výchozí hodnota `4096` .</span><span class="sxs-lookup"><span data-stu-id="aa656-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> is the minimum buffer size in bytes used when renting memory from the pool, and defaults to `4096`.</span></span>
- <span data-ttu-id="aa656-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> příznak určuje, zda je podkladový datový proud ponechán otevřen po `PipeReader` dokončení, a je nastaven na výchozí hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="aa656-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeReader` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="aa656-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> představuje prahovou hodnotu zbývajících bajtů ve vyrovnávací paměti před přidělením nové vyrovnávací paměti a výchozí hodnotou `1024` .</span><span class="sxs-lookup"><span data-stu-id="aa656-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> represents the threshold of remaining bytes in the buffer before a new buffer is allocated, and defaults to `1024`.</span></span>
- <span data-ttu-id="aa656-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> je `MemoryPool<byte>` použit při přidělování paměti a výchozí hodnota `null` .</span><span class="sxs-lookup"><span data-stu-id="aa656-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

<span data-ttu-id="aa656-309"><xref:System.IO.Pipelines.StreamPipeWriterOptions>Umožňuje řídit vytvoření `PipeWriter` instance s následujícími parametry:</span><span class="sxs-lookup"><span data-stu-id="aa656-309">The <xref:System.IO.Pipelines.StreamPipeWriterOptions> allow for control over the creation of the `PipeWriter` instance with the following parameters:</span></span>

- <span data-ttu-id="aa656-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> příznak určuje, zda je podkladový datový proud ponechán otevřen po `PipeWriter` dokončení, a je nastaven na výchozí hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="aa656-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeWriter` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="aa656-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> představuje minimální velikost vyrovnávací paměti, která se má použít při pronajmutí paměti z <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> a ve výchozím nastavení `4096` .</span><span class="sxs-lookup"><span data-stu-id="aa656-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> represents the minimum buffer size to use when renting memory from the <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool>, and defaults to `4096`.</span></span>
- <span data-ttu-id="aa656-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> je `MemoryPool<byte>` použit při přidělování paměti a výchozí hodnota `null` .</span><span class="sxs-lookup"><span data-stu-id="aa656-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa656-313">Při vytváření `PipeReader` `PipeWriter` instancí a instance pomocí `Create` metod je nutné vzít v úvahu `Stream` dobu života objektu.</span><span class="sxs-lookup"><span data-stu-id="aa656-313">When creating `PipeReader` and `PipeWriter` instances using the `Create` methods, you need to consider the `Stream` object lifetime.</span></span> <span data-ttu-id="aa656-314">Pokud potřebujete přístup ke streamu i po tom, co se čtenář nebo zapisovač provede, budete muset nastavit `LeaveOpen` příznak `true` na možnosti vytváření.</span><span class="sxs-lookup"><span data-stu-id="aa656-314">If you need access to the stream after the reader or writer is done with it, you'll need to set the `LeaveOpen` flag to `true` on the creation options.</span></span> <span data-ttu-id="aa656-315">V opačném případě bude datový proud zavřen.</span><span class="sxs-lookup"><span data-stu-id="aa656-315">Otherwise, the stream will be closed.</span></span>

<span data-ttu-id="aa656-316">Následující kód demonstruje vytvoření `PipeReader` a `PipeWriter` instance pomocí `Create` metod z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="aa656-316">The following code demonstrates the creation of `PipeReader` and `PipeWriter` instances using the `Create` methods from a stream.</span></span>

:::code language="csharp" source="snippets/pipelines/Program.cs":::

<span data-ttu-id="aa656-317">Aplikace používá <xref:System.IO.StreamReader> ke čtení *lorem-ipsum.txt* souboru jako datového proudu.</span><span class="sxs-lookup"><span data-stu-id="aa656-317">The application uses a <xref:System.IO.StreamReader> to read the *lorem-ipsum.txt* file as a stream.</span></span> <span data-ttu-id="aa656-318"><xref:System.IO.FileStream>Je předán do <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> , který vytvoří instanci `PipeReader` objektu.</span><span class="sxs-lookup"><span data-stu-id="aa656-318">The <xref:System.IO.FileStream> is passed to <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType>, which instantiates a `PipeReader` object.</span></span> <span data-ttu-id="aa656-319">Aplikace konzoly pak předá svůj standardní výstupní datový proud <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> pomocí <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aa656-319">The console application then passes its standard output stream to <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> using <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aa656-320">V příkladu je podporována [zrušení](#cancellation).</span><span class="sxs-lookup"><span data-stu-id="aa656-320">The example supports [cancellation](#cancellation).</span></span>
