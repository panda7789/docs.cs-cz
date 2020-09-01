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
# <a name="systemiopipelines-in-net"></a>System. IO. Pipelines v .NET

<xref:System.IO.Pipelines> je nová knihovna, která je navržena tak, aby usnadnila vysoce výkonné vstupně-výstupní operace v rozhraní .NET. Jedná se o knihovnu, která cílí na .NET Standard, která funguje na všech implementacích rozhraní .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Jaký problém řeší System. IO. Pipelines

<!-- corner case doesn't MT (machine translate)   -->
Aplikace, které analyzují streamovaná data, se skládají ze standardizovaného kódu, který má mnoho toků specializovaného a neobvyklého kódu Často používaný kód a zvláštní případ je složitý a obtížně udržovatelný.

`System.IO.Pipelines` bylo navrženo pro:

* Analýza dat streamování je vysoce výkonná.
* Snižte složitost kódu.

Následující kód je typický pro server TCP, který přijímá zprávy oddělené řádky (oddělený od `'\n'` ) od klienta:

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

* V jednom volání metody nemusí být přijata celá zpráva (konce řádku) `ReadAsync` .
* Ignoruje výsledek `stream.ReadAsync` . `stream.ReadAsync` Vrátí, kolik dat bylo přečteno.
* Nezpracovává případ, kdy je více řádků čteno v jednom `ReadAsync` volání.
* Přiděluje `byte` pole s každým čtením.

Chcete-li opravit předchozí problémy, jsou vyžadovány následující změny:

* Ukládat příchozí data do vyrovnávací paměti, dokud se nenajde nový řádek.
* Analyzuje všechny řádky vrácené ve vyrovnávací paměti.
* Je možné, že je řádek větší než 1 KB (1024 bajtů). Kód musí změnit velikost vstupní vyrovnávací paměti, dokud není nalezen oddělovač, aby odpovídal celému řádku uvnitř vyrovnávací paměti.

  * Pokud se změní velikost vyrovnávací paměti, ve vstupu se zobrazí další kopie vyrovnávací paměti, ve kterých se objeví delší řádky.
  * Chcete-li snížit množství nevyužitého místa, Zkomprimujte vyrovnávací paměť použitou pro čtení řádků.

* Zvažte použití sdružování vyrovnávací paměti, abyste se vyhnuli opakovanému přidělování paměti.
* Následující kód řeší některé z těchto problémů:

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

Předchozí kód je složitý a neřeší všechny zjištěné problémy. Vysoce výkonné sítě obvykle znamenají psaní velmi složitého kódu pro maximalizaci výkonu. `System.IO.Pipelines` bylo navrženo tak, aby byl tento typ kódu snazší.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Příkazem

<xref:System.IO.Pipelines.Pipe>Třídu lze použít k vytvoření `PipeWriter/PipeReader` páru. Všechna data zapsaná do nástroje `PipeWriter` jsou k dispozici v `PipeReader` :

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Základní použití kanálu

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

Existují dvě smyčky:

* `FillPipeAsync` čte z `Socket` a zápisy do `PipeWriter` .
* `ReadPipeAsync` čte z `PipeReader` a analyzuje příchozí řádky.

Nejsou přiděleny žádné explicitní vyrovnávací paměti. Veškerá správa vyrovnávací paměti je delegována na `PipeReader` `PipeWriter` implementace a. Delegování správy vyrovnávací paměti usnadňuje využívání kódu pro zaměření pouze na obchodní logiku.

V první smyčce:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> se volá, aby se získala paměť ze základního zapisovače.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> je volána, aby informovala, kolik `PipeWriter` dat bylo zapsáno do vyrovnávací paměti.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> je volána k zpřístupnění dat pro `PipeReader` .

Ve druhé smyčce `PipeReader` využívá vyrovnávací paměti zapsané `PipeWriter` . Vyrovnávací paměti přicházejí ze soketu. Volání na `PipeReader.ReadAsync` :

* Vrátí <xref:System.IO.Pipelines.ReadResult> , který obsahuje dvě důležité informace:

  * Data, která byla načtena ve formě `ReadOnlySequence<byte>` .
  * Logická hodnota `IsCompleted` , která označuje, zda bylo dosaženo konce dat (EOF).

Po nalezení oddělovače na konci řádku (konce řádku) a při analýze řádku:

* Logika zpracuje vyrovnávací paměť a přeskočí, co je již zpracováno.
* `PipeReader.AdvanceTo` je volána, aby informovala, `PipeReader` kolik dat bylo spotřebováno a zkontrolováno.

Smyčka čtečky a zapisovače končí voláním `Complete` . `Complete` umožňuje původnímu kanálu uvolnit přidělenou paměť.

### <a name="backpressure-and-flow-control"></a>Řízení zatížení a tok

V ideálním případě se jedná o společné čtení a analýzu:

* Vlákno zápisu spotřebovává data ze sítě a umístí je do vyrovnávacích pamětí.
* Podproces analýzy zodpovídá za vytváření vhodných datových struktur.

Analýza obvykle trvá více času, než stačí kopírovat bloky dat ze sítě:

* Vlákno čtení získá před vláknem analýzy.
* Vlákno čtení musí buď zpomalit, nebo přidělit více paměti pro uložení dat pro vlákno analýzy.

Pro zajištění optimálního výkonu existuje zůstatek mezi častými pozastavením a přidělením více paměti.

Chcete-li vyřešit předchozí problém, `Pipe` má dvě nastavení pro řízení toku dat:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Určuje, kolik dat by mělo být uloženo do vyrovnávací paměti před voláními pro <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pozastavení.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Určuje, kolik dat musí čtenář sledovat před `PipeWriter.FlushAsync` pokračováním volání.

![Diagram s ResumeWriterThreshold a PauseWriterThreshold](media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Vrátí nedokončenou `ValueTask<FlushResult>` , pokud je množství dat v `Pipe` křížení `PauseWriterThreshold` .
* Dokončí, `ValueTask<FlushResult>` když bude menší než `ResumeWriterThreshold` .

Pomocí dvou hodnot se vyhnete rychlému cyklování, ke kterému může dojít, když se použije jedna hodnota.

### <a name="examples"></a>Příklady

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Obvykle při použití `async` a `await` se asynchronní kód obnovuje buď na, <xref:System.Threading.Tasks.TaskScheduler> nebo v aktuální <xref:System.Threading.SynchronizationContext> .

Při provádění vstupně-výstupních operací je důležité mít detailní kontrolu nad tím, kde se vstupně-výstupní operace provádí. Tento ovládací prvek umožňuje efektivní využití mezipamětí CPU. Efektivní ukládání do mezipaměti je klíčové pro vysoce výkonné aplikace, jako jsou webové servery. <xref:System.IO.Pipelines.PipeScheduler> poskytuje kontrolu nad tím, kde jsou spouštěna asynchronní zpětná volání. Ve výchozím nastavení:

* Používá se aktuální <xref:System.Threading.SynchronizationContext> .
* Pokud je k dispozici `SynchronizationContext` , používá fond vláken ke spouštění zpětných volání.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

[PipeScheduler.](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) Apartment je <xref:System.IO.Pipelines.PipeScheduler> implementace, která zařadí zpětná volání do fondu vláken. `PipeScheduler.ThreadPool` je výchozí a obecně nejlepší volbou. [PipeScheduler. inline](xref:System.IO.Pipelines.PipeScheduler.Inline) může způsobit nezamýšlené důsledky, jako je zablokování.

### <a name="pipe-reset"></a>Resetování kanálu

Je často efektivní použít `Pipe` objekt. Chcete-li obnovit kanál, zavolejte, <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> Když `PipeReader` `PipeWriter` jsou i dokončeny.

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> spravuje paměť jménem volajícího. **Always** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> Po volání vždy volejte <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> . To vám umožní `PipeReader` zjistit, kdy se volající provede s pamětí, aby se mohl sledovat. `ReadOnlySequence<byte>`Vrácená z `PipeReader.ReadAsync` je platná pouze do volání metody `PipeReader.AdvanceTo` . Použití po volání není povoleno `ReadOnlySequence<byte>` `PipeReader.AdvanceTo` .

`PipeReader.AdvanceTo` přebírá dva <xref:System.SequencePosition> argumenty:

* První argument určuje, kolik paměti bylo spotřebováno.
* Druhý argument určuje, kolik paměti bylo pozorováno.

Označení dat jako spotřebované znamená, že kanál může vrátit paměť do podkladového fondu vyrovnávací paměti. Označení dat jako pozorovaných řídí, co dělá další volání `PipeReader.ReadAsync` . Označení všeho jako pozorovaného znamená, že další volání `PipeReader.ReadAsync` nebude vráceno, dokud nebudou do kanálu zapsána další data. Jakákoli jiná hodnota provede další volání `PipeReader.ReadAsync` ihned se zjištěnými *a* nepozorovanými daty, ale ne data, která již byla spotřebována.

### <a name="read-streaming-data-scenarios"></a>Čtení scénářů streamování dat

Při pokusu o čtení dat streamování je k dispozici několik typických vzorů:

* Pokud má datový proud data, analyzujte jednu zprávu.
* Pokud má datový proud data, analyzujte všechny dostupné zprávy.

Následující příklady používají `TryParseMessage` metodu pro analýzu zpráv z `ReadOnlySequence<byte>` . `TryParseMessage` analyzuje jednu zprávu a aktualizuje vstupní vyrovnávací paměť pro oříznutí analyzované zprávy z vyrovnávací paměti. `TryParseMessage` není součástí .NET, je metoda psaná uživatelem, která se používá v následujících oddílech.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Číst jednu zprávu

Následující kód přečte jednu zprávu z `PipeReader` a a vrátí ji volajícímu.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

Předcházející kód:

* Analyzuje jednu zprávu.
* Aktualizuje spotřebované `SequencePosition` a zkoumané, `SequencePosition` aby odkazoval na začátek oříznuté vstupní vyrovnávací paměti.

Tyto dva `SequencePosition` argumenty jsou aktualizovány, protože `TryParseMessage` odebere analyzovanou zprávu ze vstupní vyrovnávací paměti. Obecně platí, že při analýze jedné zprávy z vyrovnávací paměti by měla být prověřená poloha jedna z následujících:

* Konec zprávy
* Konec přijaté vyrovnávací paměti, pokud nebyla nalezena žádná zpráva.

Jeden případ zprávy má nejvíce potenciál pro chyby. Předání špatných hodnot do *prověření* může mít za následek výjimku z důvodu nedostatku paměti nebo nekonečnou smyčku. Další informace najdete v části [běžné problémy PipeReader](#gotchas) v tomto článku.

### <a name="reading-multiple-messages"></a>Čtení více zpráv

Následující kód přečte všechny zprávy z `PipeReader` volání a a `ProcessMessageAsync` každý z nich.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a>Zrušení

`PipeReader.ReadAsync`:

* Podporuje předávání <xref:System.Threading.CancellationToken> .
* Vyvolá výjimku <xref:System.OperationCanceledException> , pokud `CancellationToken` je zrušena, když dojde k nedokončenému čtení.
* Podporuje způsob, jak zrušit aktuální operaci čtení prostřednictvím <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> , která zabraňuje vyvolání výjimky. Volání `PipeReader.CancelPendingRead` způsobí, že aktuální nebo další volání `PipeReader.ReadAsync` vrátí hodnotu <xref:System.IO.Pipelines.ReadResult> s `IsCanceled` nastavenou na `true` . To může být užitečné pro zastavení stávající smyčky čtení v nedestruktivním a nevýjimečném způsobu.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>PipeReader běžné problémy

* Předání nesprávných hodnot do `consumed` nebo `examined` může mít za následek čtení dat již přečtených.
* `buffer.End`Při předávání jako prověření může dojít k následujícím akcím:

  * Data zastavena
  * Možnou výjimku z paměti (OOM), pokud nejsou data spotřebována. Například `PipeReader.AdvanceTo(position, buffer.End)` při zpracování jedné zprávy v čase z vyrovnávací paměti.

* Předání špatných hodnot do `consumed` nebo `examined` může způsobit nekonečnou smyčku. Například pokud se `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` nezměnila, způsobí to, že se další volání `PipeReader.ReadAsync` vrátí hned před přijetím nových dat.
* Předání špatných hodnot do `consumed` nebo `examined` může mít za následek nekonečné ukládání do vyrovnávací paměti (OOM).
* Použití `ReadOnlySequence<byte>` metody po volání `PipeReader.AdvanceTo` může mít za následek poškození paměti (použijte po uvolnění).
* Selhání volání `PipeReader.Complete/CompleteAsync` může způsobit nevracení paměti.
* Kontrola <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> a ukončení logiky čtení před zpracováním vyrovnávací paměti má za následek ztrátu dat. Stav ukončení smyčky musí být založen na `ReadResult.Buffer.IsEmpty` a `ReadResult.IsCompleted` . Tato nesprávně by mohla způsobit nekonečnou smyčku.

#### <a name="problematic-code"></a>Problematický kód

❌**Ztráta dat**

`ReadResult`Může vrátit konečný segment dat, když `IsCompleted` je nastavena na `true` . Tato data nebudou čtena před ukončením smyčky pro čtení. výsledkem bude ztráta dat.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nekonečná smyčka**

Následující logika může mít za následek nekonečnou smyčku, pokud `Result.IsCompleted` není, `true` ale ve vyrovnávací paměti nikdy není úplná zpráva.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Tady je další část kódu se stejným problémem. Před kontrolou se kontroluje, jestli není prázdná vyrovnávací paměť `ReadResult.IsCompleted` . Vzhledem k tomu, že je v `else if` , bude tato smyčka nepřetržitě v případě, že ve vyrovnávací paměti stále není úplná zpráva.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Neočekávané zablokování**

Nepodmíněné volání `PipeReader.AdvanceTo` s `buffer.End` na `examined` pozici může vést k zablokování při analýze jedné zprávy. Následující volání `PipeReader.AdvanceTo` nebude vráceno do:

* Do kanálu se zapisují další data.
* A nová data se předtím nezkoumala.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nedostatek paměti (OOM)**

V následujících podmínkách uchovává následující kód ukládání do vyrovnávací paměti, dokud <xref:System.OutOfMemoryException> nedojde k:

* Není k dispozici žádná maximální velikost zprávy.
* Data vrácená z `PipeReader` nevytvářejí úplnou zprávu. Například neprovádí úplnou zprávu, protože druhá strana zapisuje velkou zprávu (například zpráva o velikosti 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Poškození paměti**

Při psaní pomocníků, které čtou vyrovnávací paměť, je nutné před voláním zkopírovat všechny vrácené datové části `Advance` . Následující příklad vrátí paměť, která `Pipe` byla zahozena a může ji znovu použít pro další operaci (čtení/zápis).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

<xref:System.IO.Pipelines.PipeWriter>Spravuje vyrovnávací paměti pro psaní jménem volajícího. `PipeWriter` implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) . `IBufferWriter<byte>` umožňuje získat přístup k vyrovnávací paměti, aby bylo možné provádět zápisy bez dalších kopií vyrovnávací paměti.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

Předchozí kód:

* Vyžádá vyrovnávací paměť o velikosti alespoň 5 bajtů z s `PipeWriter` použitím <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> .
* Zapíše bajty pro řetězec ASCII `"Hello"` na vrácenou `Memory<byte>` .
* Volání <xref:System.IO.Pipelines.PipeWriter.Advance%2A> indikující, kolik bajtů bylo zapsáno do vyrovnávací paměti.
* Vyprázdní `PipeWriter` , čímž pošle bajty na základní zařízení.

Předchozí metoda zápisu používá vyrovnávací paměti, které poskytuje `PipeWriter` . Alternativně <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> :

* Zkopíruje existující vyrovnávací paměť do `PipeWriter` .
* Volání `GetSpan` `Advance` podle potřeby a volání <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a>Zrušení

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> podporuje předávání <xref:System.Threading.CancellationToken> . Předání `CancellationToken` výsledků v `OperationCanceledException` případě zrušení tokenu v době, kdy dojde k vyprázdnění. `PipeWriter.FlushAsync` podporuje způsob, jak zrušit aktuální operaci vyprázdnění prostřednictvím <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> bez vyvolání výjimky. Volání `PipeWriter.CancelPendingFlush` způsobí, že aktuální nebo další volání `PipeWriter.FlushAsync` nebo `PipeWriter.WriteAsync` vrátí hodnotu <xref:System.IO.Pipelines.FlushResult> s `IsCanceled` nastavenou na `true` . To může být užitečné, pokud chcete zablokovat vyprázdnit vyřazení v nedestruktivním a nevýjimečném způsobu.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter běžné problémy

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> a <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> vrátí vyrovnávací paměť s minimální požadovanou velikostí paměti. **Neberete** přesnou velikost vyrovnávací paměti.
* Není nijak zaručeno, že po sobě jdoucí volání budou vracet stejnou vyrovnávací paměť nebo vyrovnávací paměť se stejnou velikostí.
* Po volání musí být vyžádána nová vyrovnávací paměť, aby bylo možné <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pokračovat v zápisu více dat. Dřív získaná vyrovnávací paměť se nedá zapsat do.
* Volání `GetMemory` nebo `GetSpan` i v případě, že je neúplné volání `FlushAsync` není bezpečné.
* Volání `Complete` nebo `CompleteAsync` i v případě nevyprázdněných dat může mít za následek poškození paměti.

## <a name="iduplexpipe"></a>IDuplexPipe

<xref:System.IO.Pipelines.IDuplexPipe>Je kontrakt pro typy, které podporují čtení i zápis. Například síťové připojení by představovalo `IDuplexPipe` .

 Na rozdíl od `Pipe` , který obsahuje `PipeReader` a a `PipeWriter` , `IDuplexPipe` představuje jednu stranu úplného duplexního připojení. To znamená, že obsah, který se zapisuje do, nebude `PipeWriter` číst z `PipeReader` .

## <a name="streams"></a>Streamy

Při čtení nebo zápisu dat datového proudu obvykle čtete data pomocí rušení serializátoru a zapisují data pomocí serializátoru. Většina těchto rozhraní API pro čtení a zápis streamování má `Stream` parametr. Aby bylo snazší je integrovat s těmito stávajícími rozhraními API, `PipeReader` a `PipeWriter` vystavit <xref:System.IO.Pipelines.PipeReader.AsStream%2A> metodu. <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> vrací `Stream` implementaci kolem `PipeReader` nebo `PipeWriter` .

### <a name="stream-example"></a>Příklad streamu

`PipeReader``PipeWriter`instance a lze vytvořit pomocí statických `Create` metod daného <xref:System.IO.Stream> objektu a volitelných odpovídajících možností vytváření.

<xref:System.IO.Pipelines.StreamPipeReaderOptions>Umožňuje řídit vytvoření `PipeReader` instance s následujícími parametry:

- <xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> je minimální velikost vyrovnávací paměti v bajtech použitých při pronajmutí paměti z fondu a výchozí hodnota `4096` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> příznak určuje, zda je podkladový datový proud ponechán otevřen po `PipeReader` dokončení, a je nastaven na výchozí hodnotu `false` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> představuje prahovou hodnotu zbývajících bajtů ve vyrovnávací paměti před přidělením nové vyrovnávací paměti a výchozí hodnotou `1024` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> je `MemoryPool<byte>` použit při přidělování paměti a výchozí hodnota `null` .

<xref:System.IO.Pipelines.StreamPipeWriterOptions>Umožňuje řídit vytvoření `PipeWriter` instance s následujícími parametry:

- <xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> příznak určuje, zda je podkladový datový proud ponechán otevřen po `PipeWriter` dokončení, a je nastaven na výchozí hodnotu `false` .
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> představuje minimální velikost vyrovnávací paměti, která se má použít při pronajmutí paměti z <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> a ve výchozím nastavení `4096` .
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> je `MemoryPool<byte>` použit při přidělování paměti a výchozí hodnota `null` .

> [!IMPORTANT]
> Při vytváření `PipeReader` `PipeWriter` instancí a instance pomocí `Create` metod je nutné vzít v úvahu `Stream` dobu života objektu. Pokud potřebujete přístup ke streamu i po tom, co se čtenář nebo zapisovač provede, budete muset nastavit `LeaveOpen` příznak `true` na možnosti vytváření. V opačném případě bude datový proud zavřen.

Následující kód demonstruje vytvoření `PipeReader` a `PipeWriter` instance pomocí `Create` metod z datového proudu.

:::code language="csharp" source="snippets/pipelines/Program.cs":::

Aplikace používá <xref:System.IO.StreamReader> ke čtení *lorem-ipsum.txt* souboru jako datového proudu. <xref:System.IO.FileStream>Je předán do <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> , který vytvoří instanci `PipeReader` objektu. Aplikace konzoly pak předá svůj standardní výstupní datový proud <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> pomocí <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> . V příkladu je podporována [zrušení](#cancellation).
