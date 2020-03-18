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
ms.openlocfilehash: b18b2bf31787fa58e614cd4f057fba9037fe8ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627549"
---
# <a name="systemiopipelines-in-net"></a>System.IO.Pipelines v rozhraní .NET

<xref:System.IO.Pipelines>je nová knihovna, která je navržena tak, aby usnadnila provádění vysoce výkonných vstupně-va v rozhraní .NET. Je to knihovna zaměřená na standard .NET, která funguje na všech implementacích rozhraní .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Jaký problém řeší System.IO.Pipelines

<!-- corner case doesn't MT (machine translate)   -->
Aplikace, které analyzují streamovaná data, se skládají z často používaného kódu, který má mnoho specializovaných a neobvyklých toků kódu. Často používaný text a speciální kód pouzdra je složitý a obtížně udržovatelná.

`System.IO.Pipelines`byl navržen tak, aby:

* Mají vysoký výkon analýzy dat streamování.
* Snižte složitost kódu.

Následující kód je typický pro server TCP, který přijímá zprávy `'\n'`oddělené linkami (oddělené ) od klienta:

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Předchozí kód má několik problémů:

* Celá zpráva (konec řádku) nemusí být přijata `ReadAsync`v jednom volání .
* Je to ignoruje výsledek `stream.ReadAsync`. `stream.ReadAsync`vrátí, kolik dat bylo přečteno.
* Nezpracovává případ, kdy jsou čteny více `ReadAsync` řádků v jednom volání.
* Přiděluje `byte` pole s každým čtením.

Chcete-li opravit předchozí problémy, jsou požadovány následující změny:

* Utajeno do vyrovnávací paměti příchozí data, dokud není nalezen nový řádek.
* Analyzovat všechny řádky vrácené ve vyrovnávací paměti.
* Je možné, že linka je větší než 1 KB (1024 bajtů). Kód musí změnit velikost vstupní vyrovnávací paměti, dokud není nalezen oddělovač, aby se vešel do úplného řádku uvnitř vyrovnávací paměti.

  * Pokud je velikost vyrovnávací paměti, budou provedeny další kopie vyrovnávací paměti, protože se ve vstupu zobrazí delší řádky.
  * Chcete-li snížit plýtvání místem, komprimte vyrovnávací paměť používanou pro čtení řádků.

* Zvažte použití sdružování vyrovnávací paměti, abyste se vyhnuli opakovanému přidělování paměti.
* Následující kód řeší některé z těchto problémů:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Předchozí kód je složitý a neřeší všechny zjištěné problémy. Vysoce výkonné sítě obvykle znamená psaní velmi složitý kód pro maximalizaci výkonu. `System.IO.Pipelines`byl navržen tak, aby psaní tohoto typu kódu jednodušší.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Potrubí

Třídu <xref:System.IO.Pipelines.Pipe> lze použít k `PipeWriter/PipeReader` vytvoření páru. Všechny údaje zapsané do `PipeWriter` `PipeReader`jsou k dispozici v :

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Základní použití potrubí

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Existují dvě smyčky:

* `FillPipeAsync`čte z `Socket` a zapisuje do `PipeWriter`.
* `ReadPipeAsync`čte z `PipeReader` a analyzuje příchozí řádky.

Nejsou přiděleny žádné explicitní vyrovnávací paměti. Veškerá správa vyrovnávací paměti `PipeReader` je `PipeWriter` delegována na implementace a. Delegování správy vyrovnávací paměti usnadňuje spotřebovávání kódu a zaměřuje se výhradně na obchodní logiku.

V první smyčce:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>je volána získat paměť od základního zapisovače.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>je volána `PipeWriter` sdělit, kolik dat bylo zapsáno do vyrovnávací paměti.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>je volána, aby data `PipeReader`zpřístupnila rozhraní .

Ve druhé smyčce `PipeReader` spotřebovává vyrovnávací paměti `PipeWriter`napsané . Vyrovnávací paměti pocházejí ze soketu. Volání na `PipeReader.ReadAsync`:

* Vrátí <xref:System.IO.Pipelines.ReadResult> hodnotu a, která obsahuje dvě důležité informace:

  * Data, která byla přečtena `ReadOnlySequence<byte>`ve formě .
  * Logická `IsCompleted` hodnota, která označuje, zda bylo dosaženo konce dat (EOF).

Po nalezení konce řádku (EOL) oddělovač a analýzu řádku:

* Logika zpracuje vyrovnávací paměť přeskočit, co je již zpracována.
* `PipeReader.AdvanceTo`je volána `PipeReader` říct, kolik dat bylo spotřebováno a zkoumány.

Smyčky čtečky a zapisovatele končí voláním `Complete`. `Complete`umožňuje podkladové kanálu uvolnit paměť, kterou přidělené.

### <a name="backpressure-and-flow-control"></a>Řízení protitlaku a průtoku

V ideálním případě čtení a analýza spolupracují:

* Vlákno zápisu spotřebovává data ze sítě a umístí je do vyrovnávacích pamětí.
* Analyzační vlákno je zodpovědný za vytváření příslušných datových struktur.

Analýza obvykle trvá déle než pouhé kopírování bloků dat ze sítě:

* Čtecí vlákno získá před analyzující vlákno.
* Čtení vlákno má buď zpomalit nebo přidělit více paměti pro uložení dat pro analyzování podprocesu.

Pro optimální výkon existuje rovnováha mezi častými pauzami a přidělením více paměti.

Chcete-li vyřešit předchozí `Pipe` problém, má dvě nastavení pro řízení toku dat:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Určuje, kolik dat by mělo <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> být uloženo do vyrovnávací paměti před voláním pozastavit.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Určuje, kolik dat musí čtenář sledovat `PipeWriter.FlushAsync` před obnovením volání.

![Diagram s hodnotou ResumeWriterThreshold a PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Vrátí neúplné, `ValueTask<FlushResult>` pokud množství dat `Pipe` v `PauseWriterThreshold`kříže .
* `ValueTask<FlushResult>` Dokončí, když se `ResumeWriterThreshold`stane nižší než .

Dvě hodnoty se používají k zabránění rychlého cyklování, ke kterému může dojít, pokud je použita jedna hodnota.

### <a name="examples"></a>Příklady

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>Pipescheduler

Obvykle při `async` použití `await`a , asynchronní kód pokračuje <xref:System.Threading.Tasks.TaskScheduler> na buď <xref:System.Threading.SynchronizationContext>na nebo na aktuální .

Při provádění vstupně-výkonů je důležité mít jemně odstupňovanou kontrolu nad tím, kde se vstupně-v.v.i. provádí. Tento ovládací prvek umožňuje efektivně využívat mezipaměti procesoru. Efektivní ukládání do mezipaměti je důležité pro vysoce výkonné aplikace, jako jsou webové servery. <xref:System.IO.Pipelines.PipeScheduler>poskytuje kontrolu nad tím, kde se spouštějí asynchronní zpětná volání. Ve výchozím nastavení:

* Použije <xref:System.Threading.SynchronizationContext> se proud.
* Pokud není k `SynchronizationContext`dispozici , používá fond vláken ke spuštění zpětná volání.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) je <xref:System.IO.Pipelines.PipeScheduler> implementace, která zařazuje zpětná volání do fondu vláken. `PipeScheduler.ThreadPool`je výchozí a obecně nejlepší volbou. [PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) může způsobit nežádoucí důsledky, jako je například zablokování.

### <a name="pipe-reset"></a>Obnovení potrubí

Je často efektivní znovu použít `Pipe` objekt. Chcete-li obnovit <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> potrubí, `PipeReader` zavolejte po dokončení i. `PipeWriter`

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader>spravuje paměť jménem volajícího. **Vždy** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> volejte <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>po volání . To umožňuje `PipeReader` vědět, kdy je volající hotová s pamětí tak, aby jej lze sledovat. Vrácené `ReadOnlySequence<byte>` `PipeReader.ReadAsync` z je platný pouze `PipeReader.AdvanceTo`do volání . Je to nezákonné `ReadOnlySequence<byte>` používat `PipeReader.AdvanceTo`po volání .

`PipeReader.AdvanceTo`má <xref:System.SequencePosition> dva argumenty:

* První argument určuje, kolik paměti bylo spotřebováno.
* Druhý argument určuje, jak velká část vyrovnávací paměti byla pozorována.

Označení dat jako spotřebovaných znamená, že potrubí může vrátit paměť do podkladového fondu vyrovnávacích pamětí. Označení dat jako pozorovaných určuje, co `PipeReader.ReadAsync` dělá další volání. Označení všeho jako pozorované znamená, že další volání `PipeReader.ReadAsync` se nevrátí, dokud nebude do kanálu zapsáno více dat. Jakákoli jiná hodnota provede další `PipeReader.ReadAsync` volání okamžitě vrátit s pozorované *a* nepozorované data, ale data, která již byla spotřebována.

### <a name="read-streaming-data-scenarios"></a>Čtení scénářů streamování dat

Existuje několik typických vzorů, které se objevují při pokusu o čtení dat streamování:

* Daný datový proud, analyzovat jednu zprávu.
* Daný datový proud, analyzovat všechny dostupné zprávy.

Následující příklady používají `TryParseMessage` metodu pro analýzu `ReadOnlySequence<byte>`zpráv z . `TryParseMessage`analyzuje jednu zprávu a aktualizuje vstupní vyrovnávací paměť, aby ořízla analyzouženou zprávu z vyrovnávací paměti. `TryParseMessage`není součástí rozhraní .NET, je to metoda napsaná uživatelem použitá v následujících částech.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Přečtení jedné zprávy

Následující kód přečte jednu `PipeReader` zprávu z a vrátí volajícímu.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Předcházející kód:

* Analyzuje jednu zprávu.
* Aktualizuje `SequencePosition` spotřebované `SequencePosition` a zkoumané přejděte na začátek oříznuté vstupní vyrovnávací paměti.

Dva `SequencePosition` argumenty jsou `TryParseMessage` aktualizovány, protože odebere analyzované zprávy ze vstupní vyrovnávací paměti. Obecně platí, že při analýzě jedné zprávy z vyrovnávací paměti by měla být zkoumaná pozice jedna z následujících:

* Konec zprávy.
* Konec přijaté vyrovnávací paměti, pokud nebyla nalezena žádná zpráva.

Případ jedné zprávy má největší potenciál pro chyby. Předání nesprávné hodnoty *zkoumané* může mít za následek výjimku nedostatku paměti nebo nekonečné smyčky. Další informace naleznete v části [PipeReader běžné problémy](#gotchas) v tomto článku.

### <a name="reading-multiple-messages"></a>Čtení více zpráv

Následující kód přečte všechny `PipeReader` zprávy `ProcessMessageAsync` z a volá na každém.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Zrušení

`PipeReader.ReadAsync`:

* Podporuje předávání <xref:System.Threading.CancellationToken>.
* Vyvolá pokud <xref:System.OperationCanceledException> `CancellationToken` je zrušena, zatímco je čekající na čtení.
* Podporuje způsob, jak zrušit aktuální <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>operaci čtení prostřednictvím , který zabraňuje vyvolání výjimky. Volání `PipeReader.CancelPendingRead` způsobí, `PipeReader.ReadAsync` že aktuální nebo <xref:System.IO.Pipelines.ReadResult> další `IsCanceled` volání `true`vrátí s nastavenou na . To může být užitečné pro zastavení existující smyčky pro čtení nedestruktivním a nevýjimečným způsobem.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>PipeReader běžné problémy

* Předání nesprávných `consumed` `examined` hodnot nebo může mít za následek čtení již přečtená data.
* Předání, `buffer.End` jak je zkoumáno, může mít za následek:

  * Pozastavená data
  * Případně případné výjimky nedostatek paměti (OOM), pokud data není spotřebována. Například `PipeReader.AdvanceTo(position, buffer.End)` při zpracování jedné zprávy najednou z vyrovnávací paměti.

* Předání nesprávné hodnoty `consumed` `examined` nebo může mít za následek nekonečnou smyčku. Například `PipeReader.AdvanceTo(buffer.Start)` pokud `buffer.Start` se nezměnila způsobí, že `PipeReader.ReadAsync` další volání vrátit bezprostředně před příchodem nových dat.
* Předání nesprávných `consumed` `examined` hodnot nebo může mít za následek nekonečné ukládání do vyrovnávací paměti (eventuální OOM).
* Použití `ReadOnlySequence<byte>` následného `PipeReader.AdvanceTo` volání může mít za následek poškození paměti (použití po volném).
* Pokud se `PipeReader.Complete/CompleteAsync` nepodaří volání může mít za následek nevracení paměti.
* Kontrola <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> a ukončení logiky čtení před zpracováním vyrovnávací paměti má za následek ztrátu dat. Podmínka ukončení smyčky by `ReadResult.Buffer.IsEmpty` měla `ReadResult.IsCompleted`být založena na a . To nesprávně může mít za následek nekonečnou smyčku.

#### <a name="problematic-code"></a>Problematický kód

❌**Ztráta dat**

Může `ReadResult` vrátit konečný segment dat, `IsCompleted` pokud `true`je nastavena na . Nečtení dat před ukončením smyčky pro čtení bude mít za následek ztrátu dat.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nekonečná smyčka**

Následující logika může mít za `Result.IsCompleted` následek `true` nekonečnou smyčku, pokud je, ale nikdy není úplná zpráva ve vyrovnávací paměti.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Zde je další kus kódu se stejným problémem. Je to kontrola pro non-prázdné vyrovnávací `ReadResult.IsCompleted`paměti před kontrolou . Protože je v `else if`, bude smyčka navždy, pokud nikdy není úplná zpráva ve vyrovnávací paměti.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Neočekávané zablokování**

Bezpodmínečné `PipeReader.AdvanceTo` volání `buffer.End` s `examined` v pozici může mít za následek zablokuje při analýzě jedné zprávy. Další volání `PipeReader.AdvanceTo` se nevrátí, dokud:

* Do potrubí je zapsáno víc dat.
* A nová data nebyla dříve zkoumána.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nedostatek paměti (OOM)**

S následujícími podmínkami následující kód udržuje <xref:System.OutOfMemoryException> ukládání do vyrovnávací paměti, dokud nedojde k:

* Neexistuje žádná maximální velikost zprávy.
* Data vrácená `PipeReader` z nevytváří úplnou zprávu. Například nevytvoří úplnou zprávu, protože druhá strana píše velkou zprávu (například zprávu o velikosti 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Poškození paměti**

Při psaní pomocníků, kteří čtou vyrovnávací paměti, `Advance`všechny vrácené datové části by měly být zkopírovány před voláním . Následující příklad vrátí paměť, `Pipe` která byla zahozena a může jej znovu použít pro další operaci (čtení a zápis).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

Spravuje <xref:System.IO.Pipelines.PipeWriter> vyrovnávací paměti pro zápis jménem volajícího. `PipeWriter`implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601). `IBufferWriter<byte>`umožňuje získat přístup k vyrovnávací paměti provádět zápisy bez dalších kopií vyrovnávací paměti.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Předchozí kód:

* Požaduje vyrovnávací paměť alespoň 5 bajtů `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>z using .
* Zapíše bajty pro řetězec `"Hello"` ASCII `Memory<byte>`do vrácené .
* Volání <xref:System.IO.Pipelines.PipeWriter.Advance%2A> označující, kolik bajtů byly zapsány do vyrovnávací paměti.
* Vyprázdní `PipeWriter`, který odešle bajty do základního zařízení.

Předchozí metoda zápisu používá vyrovnávací paměti `PipeWriter`poskytované . <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>Alternativně:

* Zkopíruje existující vyrovnávací `PipeWriter`paměť do .
* Hovory `GetSpan` `Advance` , podle <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>potřeby a volání .

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Zrušení

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>podporuje předávání <xref:System.Threading.CancellationToken>. Předání `CancellationToken` výsledků v `OperationCanceledException` případě, že token je zrušena, zatímco je vyprázdnění čekající. `PipeWriter.FlushAsync`podporuje způsob, jak zrušit aktuální <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> vyprázdnění operace bez vyvolání výjimky. Volání `PipeWriter.CancelPendingFlush` způsobí, že aktuální `PipeWriter.FlushAsync` `PipeWriter.WriteAsync` nebo další <xref:System.IO.Pipelines.FlushResult> `IsCanceled` volání `true`nebo vrátit s nastavena na . To může být užitečné pro zastavení poddajné flush v nedestruktivní a non-výjimečným způsobem.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter běžné problémy

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>a <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> vrátit vyrovnávací paměť s alespoň požadované množství paměti. **Nepředpokládejte** přesné velikosti vyrovnávací paměti.
* Neexistuje žádná záruka, že po sobě jdoucí volání vrátí stejnou vyrovnávací paměť nebo vyrovnávací paměť stejné velikosti.
* Nová vyrovnávací paměť musí <xref:System.IO.Pipelines.PipeWriter.Advance%2A> být požadována po volání pokračovat v zápisu další data. Dříve získanou vyrovnávací paměť nelze zapsat.
* Volání `GetMemory` `GetSpan` nebo když je neúplné `FlushAsync` volání, není bezpečné.
* Volání `Complete` `CompleteAsync` nebo při nevypláchnutí dat může mít za následek poškození paměti.

## <a name="iduplexpipe"></a>Iduplexpipe

Je <xref:System.IO.Pipelines.IDuplexPipe> smlouva pro typy, které podporují čtení i psaní. Síťové připojení by například reprezentoval `IDuplexPipe`.

 Na `Pipe` rozdíl `PipeReader` od `PipeWriter`který `IDuplexPipe` obsahuje a a , představuje jednu stranu plně duplexní připojení. To znamená, že `PipeWriter` to, co je `PipeReader`zapsáno do vůle nelze číst z .

## <a name="streams"></a>Datové proudy

Při čtení nebo zápisu dat datového proudu obvykle čtete data pomocí deserializátoru a zápisu dat pomocí serializátoru. Většina těchto rozhraní API datového `Stream` proudu pro čtení a zápis má parametr. Chcete-li usnadnit integraci s těmito existujícími api `PipeReader` a `PipeWriter` vystavit . <xref:System.IO.Pipelines.PipeReader.AsStream%2A>  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>vrátí `Stream` implementaci kolem `PipeReader` `PipeWriter`nebo .
