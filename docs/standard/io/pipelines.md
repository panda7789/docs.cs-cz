---
title: Vstupně-výstupní kanály – .NET
description: Zjistěte, jak efektivně používat kanály v/v v rozhraní .NET a vyhnout se problémům ve vašem kódu.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 54b5f97aca131f52b9b5d9f54d7fa5ec00ba3d5b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423679"
---
# <a name="systemiopipelines-in-net"></a>System. IO. Pipelines v .NET

<xref:System.IO.Pipelines> je nová knihovna, která je navržena tak, aby usnadnila vysoce výkonné vstupně-výstupní operace v rozhraní .NET. Jedná se o knihovnu, která cílí na .NET Standard, která funguje na všech implementacích rozhraní .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Jaký problém řeší System. IO. Pipelines

<!-- corner case doesn't MT (machine translate)   -->
Aplikace, které analyzují streamovaná data, se skládají ze standardizovaného kódu, který má mnoho toků specializovaného a neobvyklého kódu Často používaný kód a zvláštní případ je složitý a obtížně udržovatelný.

`System.IO.Pipelines` bylo navrženo na:

* Analýza dat streamování je vysoce výkonná.
* Snižte složitost kódu.

Následující kód je typický pro server TCP, který přijímá zprávy oddělené řádky (oddělený `'\n'`) od klienta:

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

* V jednom volání `ReadAsync` nemusí být přijata celá zpráva (konce řádku).
* Ignoruje výsledek `stream.ReadAsync`. `stream.ReadAsync` vrátí, kolik dat bylo přečteno.
* Nezpracovává případ, kdy je více řádků čteno v jednom volání `ReadAsync`.
* Přiděluje pole `byte` s každým čtením.

Chcete-li opravit předchozí problémy, jsou vyžadovány následující změny:

* Ukládat příchozí data do vyrovnávací paměti, dokud se nenajde nový řádek.
* Analyzuje všechny řádky vrácené ve vyrovnávací paměti.
* Je možné, že je řádek větší než 1 KB (1024 bajtů). Kód musí změnit velikost vstupní vyrovnávací paměti, dokud není nalezen oddělovač, aby odpovídal celému řádku uvnitř vyrovnávací paměti.

  * Pokud se změní velikost vyrovnávací paměti, ve vstupu se zobrazí další kopie vyrovnávací paměti, ve kterých se objeví delší řádky.
  * Chcete-li snížit množství nevyužitého místa, Zkomprimujte vyrovnávací paměť použitou pro čtení řádků.

* Zvažte použití sdružování vyrovnávací paměti, abyste se vyhnuli opakovanému přidělování paměti.
* Následující kód řeší některé z těchto problémů:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Předchozí kód je složitý a neřeší všechny zjištěné problémy. Vysoce výkonné sítě obvykle znamenají psaní velmi složitého kódu pro maximalizaci výkonu. `System.IO.Pipelines` bylo navrženo tak, aby byl tento typ kódu snazší.

## <a name="pipe"></a>Příkazem

Třídu <xref:System.IO.Pipelines.Pipe> lze použít k vytvoření dvojice `PipeWriter/PipeReader`. Všechna data zapsaná do `PipeWriter` jsou k dispozici v `PipeReader`:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Základní použití kanálu

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Existují dvě smyčky:

* `FillPipeAsync` čte z `Socket` a zapisuje do `PipeWriter`.
* `ReadPipeAsync` čte z `PipeReader` a analyzuje příchozí řádky.

Nejsou přiděleny žádné explicitní vyrovnávací paměti. Veškerá správa vyrovnávací paměti je delegovaná na implementace `PipeReader` a `PipeWriter`. Delegování správy vyrovnávací paměti usnadňuje využívání kódu pro zaměření pouze na obchodní logiku.

V první smyčce:

* je volána hodnota <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> pro získání paměti ze základního zapisovače.
* je volána hodnota <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>, která sděluje `PipeWriter`, kolik dat bylo zapsáno do vyrovnávací paměti.
* k zpřístupnění dat pro `PipeReader`je volána <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>.

Ve druhé smyčce `PipeReader` spotřebovává vyrovnávací paměti napsané `PipeWriter`. Vyrovnávací paměti přicházejí ze soketu. Volání `PipeReader.ReadAsync`:

* Vrátí <xref:System.IO.Pipelines.ReadResult>, která obsahuje dvě důležité informace:

  * Data, která byla načtena ve formě `ReadOnlySequence<byte>`.
  * Logická hodnota `IsCompleted`, která označuje, zda byl dosažen konec dat (EOF).

Po nalezení oddělovače na konci řádku (konce řádku) a při analýze řádku:

* Logika zpracuje vyrovnávací paměť a přeskočí, co je již zpracováno.
* je volána hodnota `PipeReader.AdvanceTo`, která sděluje `PipeReader`, kolik dat bylo spotřebováno a zkontrolováno.

Smyčka čtečky a zapisovače končí voláním `Complete`. `Complete` umožňuje podkladové kanálu uvolnit přidělenou paměť.

### <a name="backpressure-and-flow-control"></a>Řízení zatížení a tok

V ideálním případě se jedná o společné čtení a analýzu:

* Vlákno zápisu spotřebovává data ze sítě a umístí je do vyrovnávacích pamětí.
* Podproces analýzy zodpovídá za vytváření vhodných datových struktur.

Analýza obvykle trvá více času, než stačí kopírovat bloky dat ze sítě:

* Vlákno čtení získá před vláknem analýzy.
* Vlákno čtení musí buď zpomalit, nebo přidělit více paměti pro uložení dat pro vlákno analýzy.

Pro zajištění optimálního výkonu existuje zůstatek mezi častými pozastavením a přidělením více paměti.

Pro vyřešení předchozího problému má `Pipe` dvě nastavení pro řízení toku dat:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Určuje, kolik dat by mělo být uloženo do vyrovnávací paměti před voláním <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pozastavení.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Určuje, kolik dat musí čtenář sledovat před voláním `PipeWriter.FlushAsync` obnovení.

![Diagram s ResumeWriterThreshold a PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Vrátí nekompletní `ValueTask<FlushResult>`, pokud množství dat v `Pipe` kříže `PauseWriterThreshold`.
* Dokončí `ValueTask<FlushResult>`, když se změní na nižší než `ResumeWriterThreshold`.

Pomocí dvou hodnot se vyhnete rychlému cyklování, ke kterému může dojít, když se použije jedna hodnota.

### <a name="examples"></a>Příklady

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Typicky při použití `async` a `await` se asynchronní kód obnoví buď na <xref:System.Threading.Tasks.TaskScheduler> nebo v aktuálním <xref:System.Threading.SynchronizationContext>.

Při provádění vstupně-výstupních operací je důležité mít detailní kontrolu nad tím, kde se vstupně-výstupní operace provádí. Tento ovládací prvek umožňuje efektivní využití mezipamětí CPU. Efektivní ukládání do mezipaměti je klíčové pro vysoce výkonné aplikace, jako jsou webové servery. <xref:System.IO.Pipelines.PipeScheduler> poskytuje kontrolu nad tím, kde se spouštějí asynchronní zpětná volání. Ve výchozím nastavení:

* Používá se aktuální <xref:System.Threading.SynchronizationContext>.
* Pokud není `SynchronizationContext`, používá fond vláken ke spouštění zpětných volání.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) Apartment je implementace <xref:System.IO.Pipelines.PipeScheduler>, která zařadí zpětná volání do fondu vláken. `PipeScheduler.ThreadPool` je výchozí a obecně nejlepší volbou. [PipeScheduler. inline](xref:System.IO.Pipelines.PipeScheduler.Inline) může způsobit nezamýšlené důsledky, jako je zablokování.

### <a name="pipe-reset"></a>Resetování kanálu

Opakované použití objektu `Pipe` je často efektivní. Chcete-li obnovit kanál, zavolejte <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A>, pokud jsou dokončeny `PipeReader` i `PipeWriter`.

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> spravuje paměť jménem volajícího. Po volání <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>**vždy** volat <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType>. To umožňuje `PipeReader` ví, kdy se volající provede s pamětí, aby se mohl sledovat. `ReadOnlySequence<byte>` vrácená z `PipeReader.ReadAsync` je platná pouze do chvíle, kdy volání `PipeReader.AdvanceTo`. Po volání `PipeReader.AdvanceTo` není povoleno použít `ReadOnlySequence<byte>`.

`PipeReader.AdvanceTo` přebírá dva argumenty <xref:System.SequencePosition>:

* První argument určuje, kolik paměti bylo spotřebováno.
* Druhý argument určuje, kolik paměti bylo pozorováno.

Označení dat jako spotřebované znamená, že kanál může vrátit paměť do podkladového fondu vyrovnávací paměti. Označení dat jako pozorovaných ovládacích prvků řídí, co je další volání `PipeReader.ReadAsync`. Označení všeho jako pozorovaného znamená, že další volání `PipeReader.ReadAsync` nebude vráceno, dokud nebudou do kanálu zapsána další data. Jakákoli jiná hodnota provede další volání `PipeReader.ReadAsync` okamžitě se zjištěnými *a* nepozorovanými daty, ale data, která již byla spotřebována.

### <a name="read-streaming-data-scenarios"></a>Čtení scénářů streamování dat

Při pokusu o čtení dat streamování je k dispozici několik typických vzorů:

* Pokud má datový proud data, analyzujte jednu zprávu.
* Pokud má datový proud data, analyzujte všechny dostupné zprávy.

V následujících příkladech se k analýze zpráv z `ReadOnlySequence<byte>` používá metoda `TryParseMessage`. `TryParseMessage` analyzuje jednu zprávu a aktualizuje vstupní vyrovnávací paměť pro oříznutí analyzované zprávy z vyrovnávací paměti. `TryParseMessage` není součástí .NET, jedná se o metodu psanou uživatelem, která se používá v následujících oddílech.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Číst jednu zprávu

Následující kód přečte jednu zprávu z `PipeReader` a vrátí ji volajícímu.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Předchozí kód:

* Analyzuje jednu zprávu.
* Aktualizuje spotřebované `SequencePosition` a zkontrolovala `SequencePosition`, aby odkazovala na začátek oříznuté vstupní vyrovnávací paměti.

Dva argumenty `SequencePosition` jsou aktualizovány, protože `TryParseMessage` odebere analyzovanou zprávu ze vstupní vyrovnávací paměti. Obecně platí, že při analýze jedné zprávy z vyrovnávací paměti by měla být prověřená poloha jedna z následujících:

* Konec zprávy
* Konec přijaté vyrovnávací paměti, pokud nebyla nalezena žádná zpráva.

Jeden případ zprávy má nejvíce potenciál pro chyby. Předání špatných hodnot do *prověření* může mít za následek výjimku z důvodu nedostatku paměti nebo nekonečnou smyčku. Další informace najdete v části [běžné problémy PipeReader](#gotchas) v tomto článku.

### <a name="reading-multiple-messages"></a>Čtení více zpráv

Následující kód přečte všechny zprávy z `PipeReader` a volá `ProcessMessageAsync` na každé.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Zrušení

`PipeReader.ReadAsync`:

* Podporuje předávání <xref:System.Threading.CancellationToken>.
* Vyvolá <xref:System.OperationCanceledException>, pokud je `CancellationToken` zrušen, zatímco existuje nevyřízená událost čtení.
* Podporuje způsob, jak zrušit aktuální operaci čtení prostřednictvím <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, což zabrání vyvolání výjimky. Volání `PipeReader.CancelPendingRead` způsobí, že aktuální nebo druhé volání `PipeReader.ReadAsync` vrátí <xref:System.IO.Pipelines.ReadResult> s `IsCanceled` nastavenou na `true`. To může být užitečné pro zastavení stávající smyčky čtení v nedestruktivním a nevýjimečném způsobu.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>PipeReader běžné problémy

* Předání špatných hodnot do `consumed` nebo `examined` může vést k tomu, že se už čtou data.
* Předání `buffer.End` jako prověření může mít za následek:

  * Data zastavena
  * Možnou výjimku z paměti (OOM), pokud nejsou data spotřebována. Například `PipeReader.AdvanceTo(position, buffer.End)` při zpracování jedné zprávy v čase z vyrovnávací paměti.

* Předání špatných hodnot do `consumed` nebo `examined` může způsobit nekonečnou smyčku. Například `PipeReader.AdvanceTo(buffer.Start)` Pokud se `buffer.Start` nezměnil, způsobí to, že se další volání `PipeReader.ReadAsync` vrátí hned před přijetím nových dat.
* Předání špatných hodnot do `consumed` nebo `examined` může mít za následek nekonečné ukládání do vyrovnávací paměti (OOM).
* Použití `ReadOnlySequence<byte>` po volání `PipeReader.AdvanceTo` může mít za následek poškození paměti (po zadarmo se používá).
* Selhání volání `PipeReader.Complete/CompleteAsync` může způsobit nevracení paměti.
* Kontrola <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> a před zpracováním vyrovnávací paměti za běhu dojde k úniku informací. Stav ukončení smyčky by měl být založený na `ReadResult.Buffer.IsEmpty` a `ReadResult.IsCompleted`. Tato nesprávně by mohla způsobit nekonečnou smyčku.

#### <a name="problematic-code"></a>Problematický kód

❌ **ztráta dat**

`ReadResult` může vrátit konečný segment dat, když je `IsCompleted` nastaven na `true`. Tato data nebudou čtena před ukončením smyčky pro čtení. výsledkem bude ztráta dat.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **nekonečné smyčka**

Následující logika může způsobit nekonečnou smyčku, pokud `Result.IsCompleted` je `true`, ale ve vyrovnávací paměti není nikdy úplná zpráva.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Tady je další část kódu se stejným problémem. Před zaškrtnutím `ReadResult.IsCompleted` se kontroluje, jestli není prázdná vyrovnávací paměť. Protože je v `else if`, zacykluje se trvale, pokud ve vyrovnávací paměti nikdy není úplná zpráva.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**neočekávané Zablokování** ❌

Nepodmíněné volání `PipeReader.AdvanceTo` s `buffer.End` v pozici `examined` může způsobit zablokování při analýze jedné zprávy. Další volání `PipeReader.AdvanceTo` se vrátí do:

* Do kanálu se zapisují další data.
* A nová data se předtím nezkoumala.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **nedostatek paměti (OOM)**

V následujících podmínkách uchovává následující kód ukládání do vyrovnávací paměti, dokud nedojde k <xref:System.OutOfMemoryException>:

* Není k dispozici žádná maximální velikost zprávy.
* Data vrácená z `PipeReader` nevytvářejí úplnou zprávu. Například neprovádí úplnou zprávu, protože druhá strana zapisuje velkou zprávu (například zpráva o velikosti 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**poškození ❌ paměti**

Při psaní pomocníků, které čtou vyrovnávací paměť, je nutné před voláním `Advance` zkopírovat všechny vrácené datové části. Následující příklad vrátí paměť, kterou `Pipe` zahodila, a může ji znovu použít pro další operaci (čtení/zápis).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

<xref:System.IO.Pipelines.PipeWriter> spravuje vyrovnávací paměti pro psaní jménem volajícího. `PipeWriter` implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601). `IBufferWriter<byte>` umožňuje získat přístup k vyrovnávací paměti, aby bylo možné provádět zápisy bez dalších kopií vyrovnávací paměti.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Předchozí kód:

* Vyžádá vyrovnávací paměť o velikosti alespoň 5 bajtů z `PipeWriter` pomocí <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.
* Zapisuje bajty pro řetězec ASCII `"Hello"` do vráceného `Memory<byte>`.
* Volá <xref:System.IO.Pipelines.PipeWriter.Advance%2A> k určení, kolik bajtů bylo zapsáno do vyrovnávací paměti.
* Vyprázdní `PipeWriter`, což pošle bajty na příslušné zařízení.

Předchozí metoda zápisu používá vyrovnávací paměti poskytované `PipeWriter`. Případně <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Zkopíruje existující vyrovnávací paměť do `PipeWriter`.
* Volá `GetSpan`, `Advance` podle potřeby a volá <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Zrušení

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> podporuje předávání <xref:System.Threading.CancellationToken>. Předání `CancellationToken` má za následek `OperationCanceledException`, pokud je token zrušený, dokud je Nevyřízeno vyprázdnění. `PipeWriter.FlushAsync` podporuje způsob, jak zrušit aktuální operaci vyprázdnění prostřednictvím <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> bez vyvolání výjimky. Volání `PipeWriter.CancelPendingFlush` způsobí, že aktuální nebo druhé volání `PipeWriter.FlushAsync` nebo `PipeWriter.WriteAsync` vrátí <xref:System.IO.Pipelines.FlushResult> s `IsCanceled` nastavenou na `true`. To může být užitečné, pokud chcete zablokovat vyprázdnit vyřazení v nedestruktivním a nevýjimečném způsobu.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter běžné problémy

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> a <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> vrátí vyrovnávací paměť s minimální požadovanou velikostí paměti. **Neberete** přesnou velikost vyrovnávací paměti.
* Není nijak zaručeno, že po sobě jdoucí volání budou vracet stejnou vyrovnávací paměť nebo vyrovnávací paměť se stejnou velikostí.
* Po volání <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pro pokračování v zápisu dalších dat je nutné požádat o novou vyrovnávací paměť. Dřív získaná vyrovnávací paměť se nedá zapsat do.
* Volání `GetMemory` nebo `GetSpan`, zatímco existuje neúplné volání `FlushAsync` není bezpečné.
* Volání `Complete` nebo `CompleteAsync`, zatímco existují nevyprázdněná data, mohou způsobit poškození paměti.

## <a name="iduplexpipe"></a>IDuplexPipe

<xref:System.IO.Pipelines.IDuplexPipe> je kontrakt pro typy, které podporují čtení i zápis. Například síťové připojení by představovalo `IDuplexPipe`.

 Na rozdíl od `Pipe`, který obsahuje `PipeReader` a `PipeWriter`, `IDuplexPipe` představuje jednu stranu úplného duplexního připojení. To znamená, že obsah zapsaný do `PipeWriter` nebude načten z `PipeReader`.

## <a name="streams"></a>Datové proudy

Při čtení nebo zápisu dat datového proudu obvykle čtete data pomocí rušení serializátoru a zapisují data pomocí serializátoru. Většina těchto rozhraní API pro čtení a zápis datového proudu má parametr `Stream`. Pro snazší integraci s těmito stávajícími rozhraními API `PipeReader` a `PipeWriter` vystavovat <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> vrací implementaci `Stream` kolem `PipeReader` nebo `PipeWriter`.
