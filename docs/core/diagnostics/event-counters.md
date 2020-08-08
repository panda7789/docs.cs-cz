---
title: EventCounters v .NET Core
description: V tomto článku se dozvíte, co EventCounters, jak je implementovat a jak se mají využívat.
ms.date: 08/07/2020
ms.openlocfilehash: 68868ff8b4e1393fc3b23af2bc8eef239ac56975
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024998"
---
# <a name="eventcounters-in-net-core"></a>EventCounters v .NET Core

**Tento článek se týká: ✔️** .net Core 3,0 SDK a novějších verzí

EventCounters jsou rozhraní API .NET Core používaná pro shromažďování metrik výkonu pro odlehčenou, více platforem a téměř v reálném čase. EventCounters byly přidány jako alternativa mezi různými platformami a "čítači výkonu" .NET Framework ve Windows. V tomto článku se dozvíte, co EventCounters, jak je implementovat a jak se mají využívat.

Modul runtime .NET Core a několik knihoven .NET publikují základní diagnostické informace pomocí EventCounters počínaje platformou .NET Core 3,0. Kromě EventCounters, které poskytuje modul runtime .NET, se můžete rozhodnout implementovat vlastní EventCounters. EventCounters lze použít ke sledování různých metrik.

EventCounters živě jako součást <xref:System.Diagnostics.Tracing.EventSource> a automaticky se do nástrojů pro naslouchací procesy přihlásí. Stejně jako všechny ostatní události v <xref:System.Diagnostics.Tracing.EventSource> , mohou být spotřebovány v rámci proc a out-of-proc přes <xref:System.Diagnostics.Tracing.EventListener> a EventPipe. Tento článek se zaměřuje na možnosti více platforem EventCounters a záměrně vylučuje PerfView a ETW (trasování událostí pro Windows), i když je možné oba použít s EventCounters.

![Obrázek diagramu EventCounters in-proc a out-of-proc](media/event-counters.svg)

[!INCLUDE [available-counters](includes/available-counters.md)]

## <a name="eventcounter-api-overview"></a>Přehled rozhraní EventCounter API

Existují dvě primární kategorie čítačů. Některé čítače jsou pro hodnoty "úroková_míra", jako je například celkový počet výjimek, celkový počet GC a celkový počet požadavků. Další čítače jsou hodnoty "snapshot", jako je například využití haldy, využití procesoru a velikost pracovní sady. V každé z těchto kategorií čítačů existují dva typy čítačů, které se liší podle toho, jak získají jejich hodnoty. Čítače cyklického dotazování získávají hodnoty pomocí zpětného volání a čítače bez cyklického dotazování mají své hodnoty přímo nastaveny na instanci čítače.

Čítače jsou reprezentovány následujícími implementacemi:

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

Naslouchací proces události Určuje, jak dlouhé mají být intervaly měření. Na konci každého intervalu se hodnota přenáší do naslouchacího procesu pro každý čítač. Implementace čítače určují, která rozhraní API a výpočty se používají k vytvoření hodnoty v každém intervalu.

1. <xref:System.Diagnostics.Tracing.EventCounter>Zaznamenává sadu hodnot. <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType>Metoda přidá novou hodnotu do sady. U každého intervalu se počítá statistická souhrn pro sadu, jako třeba minimum, maximum a střední hodnota. V nástroji [dotnet-Counters](dotnet-counters.md) se vždy zobrazí střední hodnota. <xref:System.Diagnostics.Tracing.EventCounter>Je užitečné pro popis diskrétní sady operací. Běžné použití může zahrnovat monitorování průměrné velikosti v bajtech nedávných vstupně-výstupních operací nebo průměrné peněžní hodnoty sady finančních transakcí.

1. <xref:System.Diagnostics.Tracing.IncrementingEventCounter>Zaznamenává průběžný součet pro každý časový interval. <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType>Metoda přičítá k celku. Například pokud `Increment()` je zavolána třikrát během jednoho intervalu s hodnotami `1` , a, `2` `5` pak Mezisoučet `8` bude hlášen jako hodnota čítače pro tento interval. Nástroj [dotnet-Counters](dotnet-counters.md) zobrazí sazbu jako zaznamenaný součet/čas. <xref:System.Diagnostics.Tracing.IncrementingEventCounter>Je vhodný k měření, jak často se akce vyskytují, například počet požadavků zpracovaných za sekundu.

1. <xref:System.Diagnostics.Tracing.PollingCounter>Používá zpětné volání k určení hodnoty, která je hlášena. V každém časovém intervalu je vyvolána funkce zpětného volání poskytnuté uživatelem a jako hodnota čítače se použije návratová hodnota. <xref:System.Diagnostics.Tracing.PollingCounter>Lze použít k dotazování metriky z externího zdroje, například získání aktuálních volných bajtů na disku. Dá se použít i k hlášení vlastních statistik, které se dají vypočítávají na vyžádání aplikací. Mezi příklady patří vytváření sestav o 95. percentilu nedávných latencí žádostí nebo aktuální poměr přístupů do mezipaměti.

1. K <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> určení hlášené hodnoty přírůstku používá zpětné volání. V každém časovém intervalu je vyvoláno zpětné volání a potom rozdíl mezi aktuálním voláním a posledním voláním je Hlášená hodnota. Nástroj [dotnet-Counters](dotnet-counters.md) vždy zobrazí rozdíl jako sazbu, hlášené hodnoty a časy. Tento čítač je užitečný, pokud není možné volat rozhraní API u každého výskytu, ale je možné zadat dotaz na celkový počet výskytů. Můžete například ohlásit počet bajtů zapsaných do souboru za sekundu, dokonce i bez oznámení pokaždé, když je bajt napsán.

## <a name="implement-an-eventsource"></a>Implementace EventSource

Následující kód implementuje ukázku <xref:System.Diagnostics.Tracing.EventSource> vystavenou jako pojmenovaný `"Sample.EventCounter.Minimal"` poskytovatel. Tento zdroj obsahuje <xref:System.Diagnostics.Tracing.EventCounter> reprezentaci doby zpracování požadavku. Takový čítač má název (to znamená jeho jedinečné ID ve zdroji) a zobrazované jméno, které používají nástroje pro naslouchací proces, jako je například [dotnet-Counter](dotnet-counters.md).

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

Slouží `dotnet-counters ps` k zobrazení seznamu procesů rozhraní .NET, které lze monitorovat:

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

Předáním <xref:System.Diagnostics.Tracing.EventSource> názvu `counter_list` přepínači můžete začít monitorovat Čítač:

```console
dotnet-counters monitor --process-id 1400180 Sample.EventCounter.Minimal
```

Následující příklad ukazuje výstup monitorování:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

Stisknutím tlačítka <kbd>q</kbd> zastavte příkaz monitorování.

#### <a name="conditional-counters"></a>Podmíněné čítače

Při implementaci <xref:System.Diagnostics.Tracing.EventSource> může být obsahující čítače podmíněně vytvořena při <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> volání metody s <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> hodnotou `EventCommand.Enable` . Chcete-li instanci čítače bezpečně vytvořit pouze v případě, že je `null` použita, použijte [operátor přiřazení s hodnotou null](../../csharp/language-reference/operators/null-coalescing-operator.md). Kromě toho vlastní metody mohou vyhodnotit <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> metodu pro zjištění, zda je povolen aktuální zdroj události.

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> Podmíněné čítače jsou čítače, které jsou podmínečně vytvořeny pomocí architektury, což je mikrooptimalizace. Modul runtime tento model přijme pro scénáře, ve kterých se obvykle nepoužívají čítače, k uložení zlomku milisekund.

### <a name="net-core-runtime-example-counters"></a>Ukázkové čítače .NET Core Runtime

Modul runtime .NET Core obsahuje mnoho skvělých ukázkových implementací. Zde je implementace modulu runtime pro čítač, který sleduje velikost pracovní sady aplikace.

```csharp
var workingSetCounter = new PollingCounter(
    "working-set",
    this,
    () => (double)(Environment.WorkingSet / 1_000_000))
{
    DisplayName = "Working Set",
    DisplayUnits = "MB"
};
```

<xref:System.Diagnostics.Tracing.PollingCounter>Oznamuje aktuální velikost fyzické paměti namapované na proces (pracovní sadu) aplikace, protože zachycuje metriku v okamžiku. Zpětné volání pro cyklické dotazování hodnoty je poskytnutý výraz lambda, který je pouze voláním <xref:System.Environment.WorkingSet?displayProperty=fullName> rozhraní API. <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName>a <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> jsou volitelné vlastnosti, které lze nastavit tak, aby pomohly na straně spotřebitele čítače, aby bylo možné přesnější zobrazení hodnoty. Například [dotnet – čítače](dotnet-counters.md) využívají tyto vlastnosti k zobrazení lépe přívětivých verzí názvů čítačů.

> [!IMPORTANT]
> `DisplayName`Vlastnosti nejsou lokalizovány.

Pro <xref:System.Diagnostics.Tracing.PollingCounter> a <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> není třeba provádět nic jiného. Oba sami dotazují hodnoty v intervalu požadovaném příjemcem.

Tady je příklad čítače modulu runtime implementovaného pomocí <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> .

```csharp
var monitorContentionCounter = new IncrementingPollingCounter(
    "monitor-lock-contention-count",
    this,
    () => Monitor.LockContentionCount
)
{
    DisplayName = "Monitor Lock Contention Count",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

<xref:System.Diagnostics.Tracing.IncrementingPollingCounter> <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> Rozhraní API používá k nahlášení zvýšení celkového počtu kolizí zámků. <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>Vlastnost je volitelná, ale když ji použijete, může poskytnout nápovědu pro časový interval, ve kterém se čítač nejlépe zobrazuje. Například počet kolizí zámků se nejlépe zobrazuje jako _počet za sekundu_, takže jeho <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> hodnota je jedna sekunda. Rychlost zobrazení se dá upravit pro různé typy čítačů sazeb.

> [!NOTE]
> Rozhraní <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> nepoužívá modul [dotnet-Counters](dotnet-counters.md)a naslouchací procesy událostí _nejsou_ pro jeho použití požadovány.

Existuje více implementací čítačů pro použití jako reference v úložišti [.NET runtime](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) .

## <a name="concurrency"></a>Souběžnost

> [!TIP]
> Rozhraní EventCounters API nezaručuje bezpečnost vlákna. Pokud jsou delegáty předané <xref:System.Diagnostics.Tracing.PollingCounter> nebo <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> instance volány více vlákny, je vaše zodpovědnost za zajištění bezpečnosti vláken delegátů.

Zvažte například následující <xref:System.Diagnostics.Tracing.EventSource> postup, který bude sledovat požadavky.

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

`AddRequest()`Metodu lze volat z obslužné rutiny žádosti a `RequestRateCounter` dotazuje hodnotu v intervalu určeném spotřebitelem čítače. Nicméně tuto `AddRequest()` metodu lze volat více vlákny najednou, a to tak, že zadáte podmínku časování `_requestCount` . Alternativní způsob, jak zvýšit `_requestCount` hodnotu k použití, je bezpečný pro přístup z více vláken <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> .

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

## <a name="consume-eventcounters"></a>Využití EventCounters

Existují dva hlavní způsoby využití EventCounters, a to buď v proc, nebo mimo proc. Spotřeba EventCounters se dá odlišit do tří vrstev různých spotřebních technologií.

- Přenos událostí v nezpracovaném datovém proudu prostřednictvím ETW nebo EventPipe:
  - Rozhraní API ETW přicházejí v operačním systému Windows a EventPipe je přístupné jako rozhraní [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)nebo diagnostický [protokol IPC](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).
- Dekódování binárního datového proudu událostí do událostí:
  - [Knihovna TraceEvent](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) zpracovává formáty ETW i EventPipe streamování.
- Nástroje příkazového řádku a grafického uživatelského rozhraní:
  - Nástroje jako PerfView (ETW nebo EventPipe), dotnet-Counters (pouze EventPipe) a dotnet-monitor (pouze EventPipe).

### <a name="consume-out-of-proc"></a>Využití mimo proc

Využití EventCounters mimo proc je velice běžný přístup. Pomocí EventPipe můžete použít [čítače dotnet-Counters](dotnet-counters.md) k jejich využití v různých platformách. `dotnet-counters`Nástroj je globálním nástrojem dotnet pro různé platformy, který se dá použít k monitorování hodnot čítače. Pokud chcete zjistit, jak používat `dotnet-counters` Nástroj k monitorování čítačů, přečtěte si kurz [dotnet-Counters](dotnet-counters.md)nebo pracujte s [měřením výkonu pomocí EventCounters](event-counter-perf.md) .

#### <a name="dotnet-trace"></a>dotnet-trace

`dotnet-trace`Nástroj lze použít ke spotřebě dat čítače prostřednictvím EventPipe. Tady je příklad použití `dotnet-trace` ke shromáždění dat čítače.

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

Další informace o shromažďování hodnot čítačů v průběhu času naleznete v dokumentaci [dotnet-Trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) .

#### <a name="azure-application-insights"></a>Azure Application Insights

EventCounters je možné spotřebovat pomocí Azure Monitor, konkrétně Application Insights Azure. Čítače je možné přidávat a odebírat a vy můžete zadat vlastní čítače nebo známé čítače. Další informace najdete v tématu [přizpůsobení čítačů, které se mají shromažďovat](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).

#### <a name="dotnet-monitor"></a>dotnet – monitorování

`dotnet-monitor`Je experimentální nástroj, který usnadňuje získání přístupu k diagnostickým informacím v procesu .NET. Další informace najdete v tématu [Úvod do příkazu dotnet-monitor, experimentální nástroj](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).

### <a name="consume-in-proc"></a>Využití v proc

Hodnoty čítače můžete využívat prostřednictvím <xref:System.Diagnostics.Tracing.EventListener> rozhraní API. <xref:System.Diagnostics.Tracing.EventListener>Slouží jako procedura pro zpracování jakýchkoli událostí zapsaných všemi instancemi <xref:System.Diagnostics.Tracing.EventSource> ve vaší aplikaci. Další informace o tom, jak používat `EventListener` rozhraní API, najdete v tématu <xref:System.Diagnostics.Tracing.EventListener> .

Nejprve je <xref:System.Diagnostics.Tracing.EventSource> třeba povolit hodnotu čítače, která vytváří hodnotu čítače. Přepsat <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> metodu pro získání oznámení při <xref:System.Diagnostics.Tracing.EventSource> Vytvoření a, pokud je to u <xref:System.Diagnostics.Tracing.EventSource> vašeho EventCounters správné, můžete <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> na něj zavolat. Tady je příklad přepsání:

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="16-27":::

#### <a name="sample-code"></a>Ukázka kódu

Tady je ukázková <xref:System.Diagnostics.Tracing.EventListener> třída, která vytiskne všechny názvy čítačů a hodnoty z modulu runtime .NET <xref:System.Diagnostics.Tracing.EventSource> pro publikování vnitřních čítačů ( `System.Runtime` ) v určitém intervalu.

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

Jak je uvedeno výše, _musíte_ se ujistit, že `"EventCounterIntervalSec"` argument je nastaven v `filterPayload` argumentu při volání <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> . V opačném případě čítače nebudou moci vyprázdnit hodnoty, protože nevědí, jak by měl být vyprázdněn.

## <a name="see-also"></a>Viz také

- [dotnet-counters](dotnet-counters.md)
- [dotnet-trace](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
