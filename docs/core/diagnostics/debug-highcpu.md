---
title: Ladění vysokého využití procesoru – .NET Core
description: Kurz vás provede laděním vysokého využití procesoru v .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 93076bbce3baf3a219b25c927d2aba3d2d57456f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557799"
---
# <a name="debug-high-cpu-usage-in-net-core"></a>Ladění vysokého využití procesoru v .NET Core

**Tento článek se týká: ✔️** .net Core 3,1 SDK a novějších verzí

V tomto kurzu se naučíte ladit scénář nadměrného využití procesoru. Pomocí poskytnutého příkladu ASP.NET Core úložiště zdrojového kódu [webové aplikace](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) můžete způsobit úmyslné zablokování. Koncový bod se bude nacházet v zablokování a akumulaci vláken. Naučíte se, jak můžete pomocí různých nástrojů diagnostikovat tento scénář pomocí několika klíčových částí diagnostických dat.

V tomto kurzu provedete následující:

> [!div class="checklist"]
>
> - Prozkoumat vysoké využití procesoru
> - Zjištění využití procesoru pomocí [dotnet-Counters](dotnet-counters.md)
> - Použití [dotnet-Trace](dotnet-trace.md) pro generování trasování
> - Profilování výkonu v PerfView
> - Diagnostika a řešení nadměrného využití procesoru

## <a name="prerequisites"></a>Požadavky

V tomto kurzu se používá:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.
- [Ukázka cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pro aktivaci scénáře.
- [dotnet – trasování](dotnet-trace.md) pro výpis procesů a generování profilu.
- [dotnet – čítače](dotnet-counters.md) pro monitorování využití procesoru

## <a name="cpu-counters"></a>Čítače procesoru

Před pokusem o shromažďování diagnostických dat je potřeba sledovat vysoký stav procesoru. Spusťte [ukázkovou aplikaci](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pomocí následujícího příkazu z kořenového adresáře projektu.

```dotnetcli
dotnet run
```

ID procesu zjistíte pomocí následujícího příkazu:

```dotnetcli
dotnet-trace ps
```

Poznamenejte si ID procesu z výstupu příkazu. Naše ID procesu bylo `22884` , ale bude se lišit. Chcete-li zjistit aktuální využití procesoru, použijte příkaz [dotnet-Counters](dotnet-counters.md) Tool:

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

`refresh-interval`Je počet sekund mezi hodnotami procesoru v čítači cyklického dotazování. Výstup by měl vypadat přibližně takto:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

Po spuštění webové aplikace, která je spuštěná ihned po spuštění, se procesor nespotřebovává vůbec a oznamuje se na adrese `0%` . Přejděte do `api/diagscenario/highcpu` trasy s `60000` parametrem Route:

`https://localhost:5001/api/diagscenario/highcpu/60000`

Teď znovu spusťte příkaz [dotnet-Counters](dotnet-counters.md) . Chcete-li monitorovat pouze `cpu-usage` , zadejte `System.Runtime[cpu-usage]` jako součást příkazu.

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

Mělo by se zobrazit zvýšení využití procesoru, jak je znázorněno níže:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

Po celou dobu trvání žádosti se využití CPU dokončí kolem 25%. V závislosti na hostitelském počítači je očekáváno proměnlivé využití procesoru.

> [!TIP]
> K vizualizaci ještě většího využití procesoru můžete tento koncový bod uplatnit současně na více kartách prohlížeče.

V tomto okamžiku můžete bezpečně vyslovit, že procesor je spuštěný víc, než očekáváte.

## <a name="trace-generation"></a>Generování trasování

Při analýze pomalého požadavku potřebujete diagnostický nástroj, který vám poskytne přehled o tom, co kód dělá. Obvyklá volba je profiler a existují různé možnosti profileru, ze kterých si můžete vybrat.

### <a name="linux"></a>[Linux](#tab/linux)

`perf`Nástroj lze použít ke generování profilů aplikací .NET Core. Ukončí předchozí instanci [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios).

Nastavte `COMPlus_PerfMapEnabled` proměnnou prostředí, která způsobí, že aplikace .NET Core vytvoří `map` soubor v `/tmp` adresáři. Tento `map` soubor je používán nástrojem `perf` k mapování adresy CPU na funkce generované JIT podle názvu. Další informace najdete v tématu [zapsat mapu výkonu](../run-time-config/debugging-profiling.md#write-perf-map).

Spusťte [vzorový cíl ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) ve stejné relaci terminálu.

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

Vyzkoušejte znovu koncový bod rozhraní API procesoru ( `https://localhost:5001/api/diagscenario/highcpu/60000` ). I když je spuštěný v rámci žádosti o 1 minutu, spusťte `perf` příkaz s ID procesu:

```bash
sudo perf record -p 2266 -g
```

`perf`Příkaz spustí proces shromažďování výkonu. Nechte běžet po dobu přibližně 20-30 sekund a potom stisknutím <kbd>kombinace kláves CTRL + C</kbd> ukončete proces shromažďování. Stejný příkaz můžete použít `perf` k zobrazení výstupu trasování.

```bash
sudo perf report -f
```

Pomocí následujících příkazů můžete také vygenerovat _Plamenový graf_ :

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

Tento příkaz vygeneruje `flamegraph.svg` , který můžete zobrazit v prohlížeči a prozkoumat problém s výkonem:

[![Obrázek SVG plamenového grafu](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)

### <a name="windows"></a>[Windows](#tab/windows)

Ve Windows můžete použít nástroj [dotnet-Trace](dotnet-trace.md) jako profiler. Pomocí předchozího [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)vykonáte znovu vysoký koncový bod procesoru ( `https://localhost:5001/api/diagscenario/highcpu/60000` ). I když je spuštěný v rámci žádosti o 1 minutu, použijte `collect` příkaz následujícím způsobem:

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

Let [dotnet – spuštění trasování](dotnet-trace.md) po dobu přibližně 20-30 sekund a potom stiskněte klávesu <kbd>ENTER</kbd> pro ukončení shromažďování. Výsledkem je `nettrace` soubor umístěný ve stejné složce. `nettrace`Soubory jsou skvělým způsobem, jak používat existující analytické nástroje ve Windows.

Otevřete okno `nettrace` s [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) , jak je uvedeno níže.

[![Obrázek PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)

---

## <a name="see-also"></a>Viz také

- [dotnet – trasování](dotnet-trace.md) pro výpis procesů
- [dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti
- [dotnet – vystavení](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti
- [dotnet/Diagnostika](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Ladění zablokování v .NET Core](debug-deadlock.md)
