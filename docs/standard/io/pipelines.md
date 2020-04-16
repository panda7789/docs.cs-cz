---
title: Vstupně-no kanály - .NET
description: Zjistěte, jak efektivně používat vstupně-v kanály v rozhraní .NET a vyhnout se problémům ve vašem kódu.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 8822e731ae805e83d4072c5bd78dff3fcf9a31a1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81462512"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="d0212-103">System.IO.Pipelines v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d0212-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="d0212-104"><xref:System.IO.Pipelines>je nová knihovna, která je navržena tak, aby usnadnila provádění vysoce výkonných vstupně-va v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d0212-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="d0212-105">Je to knihovna zaměřená na standard .NET, která funguje na všech implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d0212-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="d0212-106">Jaký problém řeší System.IO.Pipelines</span><span class="sxs-lookup"><span data-stu-id="d0212-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="d0212-107">Aplikace, které analyzují streamovaná data, se skládají z často používaného kódu, který má mnoho specializovaných a neobvyklých toků kódu.</span><span class="sxs-lookup"><span data-stu-id="d0212-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="d0212-108">Často používaný text a speciální kód pouzdra je složitý a obtížně udržovatelná.</span><span class="sxs-lookup"><span data-stu-id="d0212-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="d0212-109">`System.IO.Pipelines`byl navržen tak, aby:</span><span class="sxs-lookup"><span data-stu-id="d0212-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="d0212-110">Mají vysoký výkon analýzy dat streamování.</span><span class="sxs-lookup"><span data-stu-id="d0212-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="d0212-111">Snižte složitost kódu.</span><span class="sxs-lookup"><span data-stu-id="d0212-111">Reduce code complexity.</span></span>

<span data-ttu-id="d0212-112">Následující kód je typický pro server TCP, který přijímá zprávy `'\n'`oddělené linkami (oddělené ) od klienta:</span><span class="sxs-lookup"><span data-stu-id="d0212-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="d0212-113">Předchozí kód má několik problémů:</span><span class="sxs-lookup"><span data-stu-id="d0212-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="d0212-114">Celá zpráva (konec řádku) nemusí být přijata `ReadAsync`v jednom volání .</span><span class="sxs-lookup"><span data-stu-id="d0212-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="d0212-115">Je to ignoruje výsledek `stream.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="d0212-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="d0212-116">`stream.ReadAsync`vrátí, kolik dat bylo přečteno.</span><span class="sxs-lookup"><span data-stu-id="d0212-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="d0212-117">Nezpracovává případ, kdy jsou čteny více `ReadAsync` řádků v jednom volání.</span><span class="sxs-lookup"><span data-stu-id="d0212-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="d0212-118">Přiděluje `byte` pole s každým čtením.</span><span class="sxs-lookup"><span data-stu-id="d0212-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="d0212-119">Chcete-li opravit předchozí problémy, jsou požadovány následující změny:</span><span class="sxs-lookup"><span data-stu-id="d0212-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="d0212-120">Utajeno do vyrovnávací paměti příchozí data, dokud není nalezen nový řádek.</span><span class="sxs-lookup"><span data-stu-id="d0212-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="d0212-121">Analyzovat všechny řádky vrácené ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="d0212-122">Je možné, že linka je větší než 1 KB (1024 bajtů).</span><span class="sxs-lookup"><span data-stu-id="d0212-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="d0212-123">Kód musí změnit velikost vstupní vyrovnávací paměti, dokud není nalezen oddělovač, aby se vešel do úplného řádku uvnitř vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="d0212-124">Pokud je velikost vyrovnávací paměti, budou provedeny další kopie vyrovnávací paměti, protože se ve vstupu zobrazí delší řádky.</span><span class="sxs-lookup"><span data-stu-id="d0212-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="d0212-125">Chcete-li snížit plýtvání místem, komprimte vyrovnávací paměť používanou pro čtení řádků.</span><span class="sxs-lookup"><span data-stu-id="d0212-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="d0212-126">Zvažte použití sdružování vyrovnávací paměti, abyste se vyhnuli opakovanému přidělování paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="d0212-127">Následující kód řeší některé z těchto problémů:</span><span class="sxs-lookup"><span data-stu-id="d0212-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="d0212-128">Předchozí kód je složitý a neřeší všechny zjištěné problémy.</span><span class="sxs-lookup"><span data-stu-id="d0212-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="d0212-129">Vysoce výkonné sítě obvykle znamená psaní velmi složitý kód pro maximalizaci výkonu.</span><span class="sxs-lookup"><span data-stu-id="d0212-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="d0212-130">`System.IO.Pipelines`byl navržen tak, aby psaní tohoto typu kódu jednodušší.</span><span class="sxs-lookup"><span data-stu-id="d0212-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="d0212-131">Potrubí</span><span class="sxs-lookup"><span data-stu-id="d0212-131">Pipe</span></span>

<span data-ttu-id="d0212-132">Třídu <xref:System.IO.Pipelines.Pipe> lze použít k `PipeWriter/PipeReader` vytvoření páru.</span><span class="sxs-lookup"><span data-stu-id="d0212-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="d0212-133">Všechny údaje zapsané do `PipeWriter` `PipeReader`jsou k dispozici v :</span><span class="sxs-lookup"><span data-stu-id="d0212-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="d0212-134">Základní použití potrubí</span><span class="sxs-lookup"><span data-stu-id="d0212-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="d0212-135">Existují dvě smyčky:</span><span class="sxs-lookup"><span data-stu-id="d0212-135">There are two loops:</span></span>

* <span data-ttu-id="d0212-136">`FillPipeAsync`čte z `Socket` a zapisuje do `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="d0212-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="d0212-137">`ReadPipeAsync`čte z `PipeReader` a analyzuje příchozí řádky.</span><span class="sxs-lookup"><span data-stu-id="d0212-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="d0212-138">Nejsou přiděleny žádné explicitní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="d0212-139">Veškerá správa vyrovnávací paměti `PipeReader` je `PipeWriter` delegována na implementace a.</span><span class="sxs-lookup"><span data-stu-id="d0212-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="d0212-140">Delegování správy vyrovnávací paměti usnadňuje spotřebovávání kódu a zaměřuje se výhradně na obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="d0212-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="d0212-141">V první smyčce:</span><span class="sxs-lookup"><span data-stu-id="d0212-141">In the first loop:</span></span>

* <span data-ttu-id="d0212-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>je volána získat paměť od základního zapisovače.</span><span class="sxs-lookup"><span data-stu-id="d0212-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="d0212-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>je volána `PipeWriter` sdělit, kolik dat bylo zapsáno do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="d0212-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>je volána, aby data `PipeReader`zpřístupnila rozhraní .</span><span class="sxs-lookup"><span data-stu-id="d0212-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="d0212-145">Ve druhé smyčce `PipeReader` spotřebovává vyrovnávací paměti `PipeWriter`napsané .</span><span class="sxs-lookup"><span data-stu-id="d0212-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="d0212-146">Vyrovnávací paměti pocházejí ze soketu.</span><span class="sxs-lookup"><span data-stu-id="d0212-146">The buffers come from the socket.</span></span> <span data-ttu-id="d0212-147">Volání na `PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="d0212-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="d0212-148">Vrátí <xref:System.IO.Pipelines.ReadResult> hodnotu a, která obsahuje dvě důležité informace:</span><span class="sxs-lookup"><span data-stu-id="d0212-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="d0212-149">Data, která byla přečtena `ReadOnlySequence<byte>`ve formě .</span><span class="sxs-lookup"><span data-stu-id="d0212-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="d0212-150">Logická `IsCompleted` hodnota, která označuje, zda bylo dosaženo konce dat (EOF).</span><span class="sxs-lookup"><span data-stu-id="d0212-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="d0212-151">Po nalezení konce řádku (EOL) oddělovač a analýzu řádku:</span><span class="sxs-lookup"><span data-stu-id="d0212-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="d0212-152">Logika zpracuje vyrovnávací paměť přeskočit, co je již zpracována.</span><span class="sxs-lookup"><span data-stu-id="d0212-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="d0212-153">`PipeReader.AdvanceTo`je volána `PipeReader` říct, kolik dat bylo spotřebováno a zkoumány.</span><span class="sxs-lookup"><span data-stu-id="d0212-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="d0212-154">Smyčky čtečky a zapisovatele končí voláním `Complete`.</span><span class="sxs-lookup"><span data-stu-id="d0212-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="d0212-155">`Complete`umožňuje podkladové kanálu uvolnit paměť, kterou přidělené.</span><span class="sxs-lookup"><span data-stu-id="d0212-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="d0212-156">Řízení protitlaku a průtoku</span><span class="sxs-lookup"><span data-stu-id="d0212-156">Backpressure and flow control</span></span>

<span data-ttu-id="d0212-157">V ideálním případě čtení a analýza spolupracují:</span><span class="sxs-lookup"><span data-stu-id="d0212-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="d0212-158">Vlákno zápisu spotřebovává data ze sítě a umístí je do vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="d0212-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="d0212-159">Analyzační vlákno je zodpovědný za vytváření příslušných datových struktur.</span><span class="sxs-lookup"><span data-stu-id="d0212-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="d0212-160">Analýza obvykle trvá déle než pouhé kopírování bloků dat ze sítě:</span><span class="sxs-lookup"><span data-stu-id="d0212-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="d0212-161">Čtecí vlákno získá před analyzující vlákno.</span><span class="sxs-lookup"><span data-stu-id="d0212-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="d0212-162">Čtení vlákno má buď zpomalit nebo přidělit více paměti pro uložení dat pro analyzování podprocesu.</span><span class="sxs-lookup"><span data-stu-id="d0212-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="d0212-163">Pro optimální výkon existuje rovnováha mezi častými pauzami a přidělením více paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="d0212-164">Chcete-li vyřešit předchozí `Pipe` problém, má dvě nastavení pro řízení toku dat:</span><span class="sxs-lookup"><span data-stu-id="d0212-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="d0212-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Určuje, kolik dat by mělo <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> být uloženo do vyrovnávací paměti před voláním pozastavit.</span><span class="sxs-lookup"><span data-stu-id="d0212-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="d0212-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Určuje, kolik dat musí čtenář sledovat `PipeWriter.FlushAsync` před obnovením volání.</span><span class="sxs-lookup"><span data-stu-id="d0212-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagram s hodnotou ResumeWriterThreshold a PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="d0212-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="d0212-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="d0212-169">Vrátí neúplné, `ValueTask<FlushResult>` pokud množství dat `Pipe` v `PauseWriterThreshold`kříže .</span><span class="sxs-lookup"><span data-stu-id="d0212-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="d0212-170">`ValueTask<FlushResult>` Dokončí, když se `ResumeWriterThreshold`stane nižší než .</span><span class="sxs-lookup"><span data-stu-id="d0212-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="d0212-171">Dvě hodnoty se používají k zabránění rychlého cyklování, ke kterému může dojít, pokud je použita jedna hodnota.</span><span class="sxs-lookup"><span data-stu-id="d0212-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="d0212-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="d0212-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="d0212-173">Pipescheduler</span><span class="sxs-lookup"><span data-stu-id="d0212-173">PipeScheduler</span></span>

<span data-ttu-id="d0212-174">Obvykle při `async` použití `await`a , asynchronní kód pokračuje <xref:System.Threading.Tasks.TaskScheduler> na buď <xref:System.Threading.SynchronizationContext>na nebo na aktuální .</span><span class="sxs-lookup"><span data-stu-id="d0212-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="d0212-175">Při provádění vstupně-výkonů je důležité mít jemně odstupňovanou kontrolu nad tím, kde se vstupně-v.v.i. provádí.</span><span class="sxs-lookup"><span data-stu-id="d0212-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="d0212-176">Tento ovládací prvek umožňuje efektivně využívat mezipaměti procesoru.</span><span class="sxs-lookup"><span data-stu-id="d0212-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="d0212-177">Efektivní ukládání do mezipaměti je důležité pro vysoce výkonné aplikace, jako jsou webové servery.</span><span class="sxs-lookup"><span data-stu-id="d0212-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="d0212-178"><xref:System.IO.Pipelines.PipeScheduler>poskytuje kontrolu nad tím, kde se spouštějí asynchronní zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="d0212-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="d0212-179">Ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="d0212-179">By default:</span></span>

* <span data-ttu-id="d0212-180">Použije <xref:System.Threading.SynchronizationContext> se proud.</span><span class="sxs-lookup"><span data-stu-id="d0212-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="d0212-181">Pokud není k `SynchronizationContext`dispozici , používá fond vláken ke spuštění zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="d0212-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="d0212-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) je <xref:System.IO.Pipelines.PipeScheduler> implementace, která zařazuje zpětná volání do fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="d0212-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="d0212-183">`PipeScheduler.ThreadPool`je výchozí a obecně nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="d0212-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="d0212-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) může způsobit nežádoucí důsledky, jako je například zablokování.</span><span class="sxs-lookup"><span data-stu-id="d0212-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="d0212-185">Obnovení potrubí</span><span class="sxs-lookup"><span data-stu-id="d0212-185">Pipe reset</span></span>

<span data-ttu-id="d0212-186">Je často efektivní znovu použít `Pipe` objekt.</span><span class="sxs-lookup"><span data-stu-id="d0212-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="d0212-187">Chcete-li obnovit <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> potrubí, `PipeReader` zavolejte po dokončení i. `PipeWriter`</span><span class="sxs-lookup"><span data-stu-id="d0212-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="d0212-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="d0212-188">PipeReader</span></span>

<span data-ttu-id="d0212-189"><xref:System.IO.Pipelines.PipeReader>spravuje paměť jménem volajícího.</span><span class="sxs-lookup"><span data-stu-id="d0212-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="d0212-190">**Vždy** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> volejte <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>po volání .</span><span class="sxs-lookup"><span data-stu-id="d0212-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d0212-191">To umožňuje `PipeReader` vědět, kdy je volající hotová s pamětí tak, aby jej lze sledovat.</span><span class="sxs-lookup"><span data-stu-id="d0212-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="d0212-192">Vrácené `ReadOnlySequence<byte>` `PipeReader.ReadAsync` z je platný pouze `PipeReader.AdvanceTo`do volání .</span><span class="sxs-lookup"><span data-stu-id="d0212-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="d0212-193">Je to nezákonné `ReadOnlySequence<byte>` používat `PipeReader.AdvanceTo`po volání .</span><span class="sxs-lookup"><span data-stu-id="d0212-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="d0212-194">`PipeReader.AdvanceTo`má <xref:System.SequencePosition> dva argumenty:</span><span class="sxs-lookup"><span data-stu-id="d0212-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="d0212-195">První argument určuje, kolik paměti bylo spotřebováno.</span><span class="sxs-lookup"><span data-stu-id="d0212-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="d0212-196">Druhý argument určuje, jak velká část vyrovnávací paměti byla pozorována.</span><span class="sxs-lookup"><span data-stu-id="d0212-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="d0212-197">Označení dat jako spotřebovaných znamená, že potrubí může vrátit paměť do podkladového fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="d0212-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="d0212-198">Označení dat jako pozorovaných určuje, co `PipeReader.ReadAsync` dělá další volání.</span><span class="sxs-lookup"><span data-stu-id="d0212-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="d0212-199">Označení všeho jako pozorované znamená, že další volání `PipeReader.ReadAsync` se nevrátí, dokud nebude do kanálu zapsáno více dat.</span><span class="sxs-lookup"><span data-stu-id="d0212-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="d0212-200">Jakákoli jiná hodnota provede další `PipeReader.ReadAsync` volání okamžitě vrátit s pozorované *a* nepozorované data, ale ne data, která již byla spotřebována.</span><span class="sxs-lookup"><span data-stu-id="d0212-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="d0212-201">Čtení scénářů streamování dat</span><span class="sxs-lookup"><span data-stu-id="d0212-201">Read streaming data scenarios</span></span>

<span data-ttu-id="d0212-202">Existuje několik typických vzorů, které se objevují při pokusu o čtení dat streamování:</span><span class="sxs-lookup"><span data-stu-id="d0212-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="d0212-203">Daný datový proud, analyzovat jednu zprávu.</span><span class="sxs-lookup"><span data-stu-id="d0212-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="d0212-204">Daný datový proud, analyzovat všechny dostupné zprávy.</span><span class="sxs-lookup"><span data-stu-id="d0212-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="d0212-205">Následující příklady používají `TryParseMessage` metodu pro analýzu `ReadOnlySequence<byte>`zpráv z .</span><span class="sxs-lookup"><span data-stu-id="d0212-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="d0212-206">`TryParseMessage`analyzuje jednu zprávu a aktualizuje vstupní vyrovnávací paměť, aby ořízla analyzouženou zprávu z vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="d0212-207">`TryParseMessage`není součástí rozhraní .NET, je to metoda napsaná uživatelem použitá v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="d0212-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="d0212-208">Přečtení jedné zprávy</span><span class="sxs-lookup"><span data-stu-id="d0212-208">Read a single message</span></span>

<span data-ttu-id="d0212-209">Následující kód přečte jednu `PipeReader` zprávu z a vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="d0212-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="d0212-210">Předcházející kód:</span><span class="sxs-lookup"><span data-stu-id="d0212-210">The preceding code:</span></span>

* <span data-ttu-id="d0212-211">Analyzuje jednu zprávu.</span><span class="sxs-lookup"><span data-stu-id="d0212-211">Parses a single message.</span></span>
* <span data-ttu-id="d0212-212">Aktualizuje `SequencePosition` spotřebované `SequencePosition` a zkoumané přejděte na začátek oříznuté vstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="d0212-213">Dva `SequencePosition` argumenty jsou `TryParseMessage` aktualizovány, protože odebere analyzované zprávy ze vstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="d0212-214">Obecně platí, že při analýzě jedné zprávy z vyrovnávací paměti by měla být zkoumaná pozice jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="d0212-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="d0212-215">Konec zprávy.</span><span class="sxs-lookup"><span data-stu-id="d0212-215">The end of the message.</span></span>
* <span data-ttu-id="d0212-216">Konec přijaté vyrovnávací paměti, pokud nebyla nalezena žádná zpráva.</span><span class="sxs-lookup"><span data-stu-id="d0212-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="d0212-217">Případ jedné zprávy má největší potenciál pro chyby.</span><span class="sxs-lookup"><span data-stu-id="d0212-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="d0212-218">Předání nesprávné hodnoty *zkoumané* může mít za následek výjimku nedostatku paměti nebo nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="d0212-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="d0212-219">Další informace naleznete v části [PipeReader běžné problémy](#gotchas) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="d0212-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="d0212-220">Čtení více zpráv</span><span class="sxs-lookup"><span data-stu-id="d0212-220">Reading multiple messages</span></span>

<span data-ttu-id="d0212-221">Následující kód přečte všechny `PipeReader` zprávy `ProcessMessageAsync` z a volá na každém.</span><span class="sxs-lookup"><span data-stu-id="d0212-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="d0212-222">Zrušení</span><span class="sxs-lookup"><span data-stu-id="d0212-222">Cancellation</span></span>

<span data-ttu-id="d0212-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="d0212-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="d0212-224">Podporuje předávání <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="d0212-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="d0212-225">Vyvolá pokud <xref:System.OperationCanceledException> `CancellationToken` je zrušena, zatímco je čekající na čtení.</span><span class="sxs-lookup"><span data-stu-id="d0212-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="d0212-226">Podporuje způsob, jak zrušit aktuální <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>operaci čtení prostřednictvím , který zabraňuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d0212-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="d0212-227">Volání `PipeReader.CancelPendingRead` způsobí, `PipeReader.ReadAsync` že aktuální nebo <xref:System.IO.Pipelines.ReadResult> další `IsCanceled` volání `true`vrátí s nastavenou na .</span><span class="sxs-lookup"><span data-stu-id="d0212-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="d0212-228">To může být užitečné pro zastavení existující smyčky pro čtení nedestruktivním a nevýjimečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d0212-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="d0212-229">PipeReader běžné problémy</span><span class="sxs-lookup"><span data-stu-id="d0212-229">PipeReader common problems</span></span>

* <span data-ttu-id="d0212-230">Předání nesprávných `consumed` `examined` hodnot nebo může mít za následek čtení již přečtená data.</span><span class="sxs-lookup"><span data-stu-id="d0212-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="d0212-231">Předání, `buffer.End` jak je zkoumáno, může mít za následek:</span><span class="sxs-lookup"><span data-stu-id="d0212-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="d0212-232">Pozastavená data</span><span class="sxs-lookup"><span data-stu-id="d0212-232">Stalled data</span></span>
  * <span data-ttu-id="d0212-233">Případně případné výjimky nedostatek paměti (OOM), pokud data není spotřebována.</span><span class="sxs-lookup"><span data-stu-id="d0212-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="d0212-234">Například `PipeReader.AdvanceTo(position, buffer.End)` při zpracování jedné zprávy najednou z vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="d0212-235">Předání nesprávné hodnoty `consumed` `examined` nebo může mít za následek nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="d0212-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="d0212-236">Například `PipeReader.AdvanceTo(buffer.Start)` pokud `buffer.Start` se nezměnila způsobí, že `PipeReader.ReadAsync` další volání vrátit bezprostředně před příchodem nových dat.</span><span class="sxs-lookup"><span data-stu-id="d0212-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="d0212-237">Předání nesprávných `consumed` `examined` hodnot nebo může mít za následek nekonečné ukládání do vyrovnávací paměti (eventuální OOM).</span><span class="sxs-lookup"><span data-stu-id="d0212-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="d0212-238">Použití `ReadOnlySequence<byte>` následného `PipeReader.AdvanceTo` volání může mít za následek poškození paměti (použití po volném).</span><span class="sxs-lookup"><span data-stu-id="d0212-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="d0212-239">Pokud se `PipeReader.Complete/CompleteAsync` nepodaří volání může mít za následek nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="d0212-240">Kontrola <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> a ukončení logiky čtení před zpracováním vyrovnávací paměti má za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="d0212-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="d0212-241">Podmínka ukončení smyčky by `ReadResult.Buffer.IsEmpty` měla `ReadResult.IsCompleted`být založena na a .</span><span class="sxs-lookup"><span data-stu-id="d0212-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="d0212-242">To nesprávně může mít za následek nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="d0212-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="d0212-243">Problematický kód</span><span class="sxs-lookup"><span data-stu-id="d0212-243">Problematic code</span></span>

<span data-ttu-id="d0212-244">❌**Ztráta dat**</span><span class="sxs-lookup"><span data-stu-id="d0212-244">❌ **Data loss**</span></span>

<span data-ttu-id="d0212-245">Může `ReadResult` vrátit konečný segment dat, `IsCompleted` pokud `true`je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="d0212-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="d0212-246">Nečtení dat před ukončením smyčky pro čtení bude mít za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="d0212-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d0212-247">❌**Nekonečná smyčka**</span><span class="sxs-lookup"><span data-stu-id="d0212-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="d0212-248">Následující logika může mít za `Result.IsCompleted` následek `true` nekonečnou smyčku, pokud je, ale nikdy není úplná zpráva ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d0212-249">Zde je další kus kódu se stejným problémem.</span><span class="sxs-lookup"><span data-stu-id="d0212-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="d0212-250">Je to kontrola pro non-prázdné vyrovnávací `ReadResult.IsCompleted`paměti před kontrolou .</span><span class="sxs-lookup"><span data-stu-id="d0212-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="d0212-251">Protože je v `else if`, bude smyčka navždy, pokud nikdy není úplná zpráva ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d0212-252">❌**Neočekávané zablokování**</span><span class="sxs-lookup"><span data-stu-id="d0212-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="d0212-253">Bezpodmínečné `PipeReader.AdvanceTo` volání `buffer.End` s `examined` v pozici může mít za následek zablokuje při analýzě jedné zprávy.</span><span class="sxs-lookup"><span data-stu-id="d0212-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="d0212-254">Další volání `PipeReader.AdvanceTo` se nevrátí, dokud:</span><span class="sxs-lookup"><span data-stu-id="d0212-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="d0212-255">Do potrubí je zapsáno víc dat.</span><span class="sxs-lookup"><span data-stu-id="d0212-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="d0212-256">A nová data nebyla dříve zkoumána.</span><span class="sxs-lookup"><span data-stu-id="d0212-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d0212-257">❌**Nedostatek paměti (OOM)**</span><span class="sxs-lookup"><span data-stu-id="d0212-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="d0212-258">S následujícími podmínkami následující kód udržuje <xref:System.OutOfMemoryException> ukládání do vyrovnávací paměti, dokud nedojde k:</span><span class="sxs-lookup"><span data-stu-id="d0212-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="d0212-259">Neexistuje žádná maximální velikost zprávy.</span><span class="sxs-lookup"><span data-stu-id="d0212-259">There's no maximum message size.</span></span>
* <span data-ttu-id="d0212-260">Data vrácená `PipeReader` z nevytváří úplnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="d0212-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="d0212-261">Například nevytvoří úplnou zprávu, protože druhá strana píše velkou zprávu (například zprávu o velikosti 4 GB).</span><span class="sxs-lookup"><span data-stu-id="d0212-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d0212-262">❌**Poškození paměti**</span><span class="sxs-lookup"><span data-stu-id="d0212-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="d0212-263">Při psaní pomocníků, kteří čtou vyrovnávací paměti, `Advance`všechny vrácené datové části by měly být zkopírovány před voláním .</span><span class="sxs-lookup"><span data-stu-id="d0212-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="d0212-264">Následující příklad vrátí paměť, `Pipe` která byla zahozena a může jej znovu použít pro další operaci (čtení a zápis).</span><span class="sxs-lookup"><span data-stu-id="d0212-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="d0212-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="d0212-265">PipeWriter</span></span>

<span data-ttu-id="d0212-266">Spravuje <xref:System.IO.Pipelines.PipeWriter> vyrovnávací paměti pro zápis jménem volajícího.</span><span class="sxs-lookup"><span data-stu-id="d0212-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="d0212-267">`PipeWriter`implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span><span class="sxs-lookup"><span data-stu-id="d0212-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="d0212-268">`IBufferWriter<byte>`umožňuje získat přístup k vyrovnávací paměti provádět zápisy bez dalších kopií vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="d0212-269">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="d0212-269">The previous code:</span></span>

* <span data-ttu-id="d0212-270">Požaduje vyrovnávací paměť alespoň 5 bajtů `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>z using .</span><span class="sxs-lookup"><span data-stu-id="d0212-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="d0212-271">Zapíše bajty pro řetězec `"Hello"` ASCII `Memory<byte>`do vrácené .</span><span class="sxs-lookup"><span data-stu-id="d0212-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="d0212-272">Volání <xref:System.IO.Pipelines.PipeWriter.Advance%2A> označující, kolik bajtů byly zapsány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="d0212-273">Vyprázdní `PipeWriter`, který odešle bajty do základního zařízení.</span><span class="sxs-lookup"><span data-stu-id="d0212-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="d0212-274">Předchozí metoda zápisu používá vyrovnávací paměti `PipeWriter`poskytované .</span><span class="sxs-lookup"><span data-stu-id="d0212-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="d0212-275"><xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>Alternativně:</span><span class="sxs-lookup"><span data-stu-id="d0212-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="d0212-276">Zkopíruje existující vyrovnávací `PipeWriter`paměť do .</span><span class="sxs-lookup"><span data-stu-id="d0212-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="d0212-277">Hovory `GetSpan` `Advance` , podle <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>potřeby a volání .</span><span class="sxs-lookup"><span data-stu-id="d0212-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="d0212-278">Zrušení</span><span class="sxs-lookup"><span data-stu-id="d0212-278">Cancellation</span></span>

<span data-ttu-id="d0212-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>podporuje předávání <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="d0212-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="d0212-280">Předání `CancellationToken` výsledků v `OperationCanceledException` případě, že token je zrušena, zatímco je vyprázdnění čekající.</span><span class="sxs-lookup"><span data-stu-id="d0212-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="d0212-281">`PipeWriter.FlushAsync`podporuje způsob, jak zrušit aktuální <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> vyprázdnění operace bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d0212-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="d0212-282">Volání `PipeWriter.CancelPendingFlush` způsobí, že aktuální `PipeWriter.FlushAsync` `PipeWriter.WriteAsync` nebo další <xref:System.IO.Pipelines.FlushResult> `IsCanceled` volání `true`nebo vrátit s nastavena na .</span><span class="sxs-lookup"><span data-stu-id="d0212-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="d0212-283">To může být užitečné pro zastavení poddajné flush v nedestruktivní a non-výjimečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d0212-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="d0212-284">PipeWriter běžné problémy</span><span class="sxs-lookup"><span data-stu-id="d0212-284">PipeWriter common problems</span></span>

* <span data-ttu-id="d0212-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>a <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> vrátit vyrovnávací paměť s alespoň požadované množství paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="d0212-286">**Nepředpokládejte** přesné velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="d0212-287">Neexistuje žádná záruka, že po sobě jdoucí volání vrátí stejnou vyrovnávací paměť nebo vyrovnávací paměť stejné velikosti.</span><span class="sxs-lookup"><span data-stu-id="d0212-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="d0212-288">Nová vyrovnávací paměť musí <xref:System.IO.Pipelines.PipeWriter.Advance%2A> být požadována po volání pokračovat v zápisu další data.</span><span class="sxs-lookup"><span data-stu-id="d0212-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="d0212-289">Dříve získanou vyrovnávací paměť nelze zapsat.</span><span class="sxs-lookup"><span data-stu-id="d0212-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="d0212-290">Volání `GetMemory` `GetSpan` nebo když je neúplné `FlushAsync` volání, není bezpečné.</span><span class="sxs-lookup"><span data-stu-id="d0212-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="d0212-291">Volání `Complete` `CompleteAsync` nebo při nevypláchnutí dat může mít za následek poškození paměti.</span><span class="sxs-lookup"><span data-stu-id="d0212-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="d0212-292">Iduplexpipe</span><span class="sxs-lookup"><span data-stu-id="d0212-292">IDuplexPipe</span></span>

<span data-ttu-id="d0212-293">Je <xref:System.IO.Pipelines.IDuplexPipe> smlouva pro typy, které podporují čtení i psaní.</span><span class="sxs-lookup"><span data-stu-id="d0212-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="d0212-294">Síťové připojení by například reprezentoval `IDuplexPipe`.</span><span class="sxs-lookup"><span data-stu-id="d0212-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="d0212-295">Na `Pipe` rozdíl `PipeReader` od `PipeWriter`který `IDuplexPipe` obsahuje a a , představuje jednu stranu plně duplexní připojení.</span><span class="sxs-lookup"><span data-stu-id="d0212-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="d0212-296">To znamená, že `PipeWriter` to, co je `PipeReader`zapsáno do vůle nelze číst z .</span><span class="sxs-lookup"><span data-stu-id="d0212-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="d0212-297">Datové proudy</span><span class="sxs-lookup"><span data-stu-id="d0212-297">Streams</span></span>

<span data-ttu-id="d0212-298">Při čtení nebo zápisu dat datového proudu obvykle čtete data pomocí deserializátoru a zápisu dat pomocí serializátoru.</span><span class="sxs-lookup"><span data-stu-id="d0212-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="d0212-299">Většina těchto rozhraní API datového `Stream` proudu pro čtení a zápis má parametr.</span><span class="sxs-lookup"><span data-stu-id="d0212-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="d0212-300">Chcete-li usnadnit integraci s těmito existujícími api `PipeReader` a `PipeWriter` vystavit . <xref:System.IO.Pipelines.PipeReader.AsStream%2A></span><span class="sxs-lookup"><span data-stu-id="d0212-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="d0212-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>vrátí `Stream` implementaci kolem `PipeReader` `PipeWriter`nebo .</span><span class="sxs-lookup"><span data-stu-id="d0212-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
