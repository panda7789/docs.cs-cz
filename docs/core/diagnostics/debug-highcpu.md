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
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="fff3f-103">Ladění vysokého využití procesoru v .NET Core</span><span class="sxs-lookup"><span data-stu-id="fff3f-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="fff3f-104">**Tento článek se týká: ✔️** .net Core 3,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="fff3f-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="fff3f-105">V tomto kurzu se naučíte ladit scénář nadměrného využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="fff3f-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="fff3f-106">Pomocí poskytnutého příkladu ASP.NET Core úložiště zdrojového kódu [webové aplikace](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) můžete způsobit úmyslné zablokování.</span><span class="sxs-lookup"><span data-stu-id="fff3f-106">Using the provided example [ASP.NET Core web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="fff3f-107">Koncový bod se bude nacházet v zablokování a akumulaci vláken.</span><span class="sxs-lookup"><span data-stu-id="fff3f-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="fff3f-108">Naučíte se, jak můžete pomocí různých nástrojů diagnostikovat tento scénář pomocí několika klíčových částí diagnostických dat.</span><span class="sxs-lookup"><span data-stu-id="fff3f-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="fff3f-109">V tomto kurzu provedete následující:</span><span class="sxs-lookup"><span data-stu-id="fff3f-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="fff3f-110">Prozkoumat vysoké využití procesoru</span><span class="sxs-lookup"><span data-stu-id="fff3f-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="fff3f-111">Zjištění využití procesoru pomocí [dotnet-Counters](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="fff3f-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="fff3f-112">Použití [dotnet-Trace](dotnet-trace.md) pro generování trasování</span><span class="sxs-lookup"><span data-stu-id="fff3f-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="fff3f-113">Profilování výkonu v PerfView</span><span class="sxs-lookup"><span data-stu-id="fff3f-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="fff3f-114">Diagnostika a řešení nadměrného využití procesoru</span><span class="sxs-lookup"><span data-stu-id="fff3f-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fff3f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fff3f-115">Prerequisites</span></span>

<span data-ttu-id="fff3f-116">V tomto kurzu se používá:</span><span class="sxs-lookup"><span data-stu-id="fff3f-116">The tutorial uses:</span></span>

- <span data-ttu-id="fff3f-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="fff3f-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="fff3f-118">[Ukázka cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pro aktivaci scénáře.</span><span class="sxs-lookup"><span data-stu-id="fff3f-118">[Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="fff3f-119">[dotnet – trasování](dotnet-trace.md) pro výpis procesů a generování profilu.</span><span class="sxs-lookup"><span data-stu-id="fff3f-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="fff3f-120">[dotnet – čítače](dotnet-counters.md) pro monitorování využití procesoru</span><span class="sxs-lookup"><span data-stu-id="fff3f-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="fff3f-121">Čítače procesoru</span><span class="sxs-lookup"><span data-stu-id="fff3f-121">CPU counters</span></span>

<span data-ttu-id="fff3f-122">Před pokusem o shromažďování diagnostických dat je potřeba sledovat vysoký stav procesoru.</span><span class="sxs-lookup"><span data-stu-id="fff3f-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="fff3f-123">Spusťte [ukázkovou aplikaci](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pomocí následujícího příkazu z kořenového adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="fff3f-123">Run the [sample application](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="fff3f-124">ID procesu zjistíte pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="fff3f-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="fff3f-125">Poznamenejte si ID procesu z výstupu příkazu.</span><span class="sxs-lookup"><span data-stu-id="fff3f-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="fff3f-126">Naše ID procesu bylo `22884` , ale bude se lišit.</span><span class="sxs-lookup"><span data-stu-id="fff3f-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="fff3f-127">Chcete-li zjistit aktuální využití procesoru, použijte příkaz [dotnet-Counters](dotnet-counters.md) Tool:</span><span class="sxs-lookup"><span data-stu-id="fff3f-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="fff3f-128">`refresh-interval`Je počet sekund mezi hodnotami procesoru v čítači cyklického dotazování.</span><span class="sxs-lookup"><span data-stu-id="fff3f-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="fff3f-129">Výstup by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="fff3f-129">The output should be similar to the following:</span></span>

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

<span data-ttu-id="fff3f-130">Po spuštění webové aplikace, která je spuštěná ihned po spuštění, se procesor nespotřebovává vůbec a oznamuje se na adrese `0%` .</span><span class="sxs-lookup"><span data-stu-id="fff3f-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="fff3f-131">Přejděte do `api/diagscenario/highcpu` trasy s `60000` parametrem Route:</span><span class="sxs-lookup"><span data-stu-id="fff3f-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

`https://localhost:5001/api/diagscenario/highcpu/60000`

<span data-ttu-id="fff3f-132">Teď znovu spusťte příkaz [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="fff3f-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="fff3f-133">Chcete-li monitorovat pouze `cpu-usage` , zadejte `System.Runtime[cpu-usage]` jako součást příkazu.</span><span class="sxs-lookup"><span data-stu-id="fff3f-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="fff3f-134">Mělo by se zobrazit zvýšení využití procesoru, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="fff3f-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="fff3f-135">Po celou dobu trvání žádosti se využití CPU dokončí kolem 25%.</span><span class="sxs-lookup"><span data-stu-id="fff3f-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="fff3f-136">V závislosti na hostitelském počítači je očekáváno proměnlivé využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="fff3f-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="fff3f-137">K vizualizaci ještě většího využití procesoru můžete tento koncový bod uplatnit současně na více kartách prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="fff3f-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="fff3f-138">V tomto okamžiku můžete bezpečně vyslovit, že procesor je spuštěný víc, než očekáváte.</span><span class="sxs-lookup"><span data-stu-id="fff3f-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="fff3f-139">Generování trasování</span><span class="sxs-lookup"><span data-stu-id="fff3f-139">Trace generation</span></span>

<span data-ttu-id="fff3f-140">Při analýze pomalého požadavku potřebujete diagnostický nástroj, který vám poskytne přehled o tom, co kód dělá.</span><span class="sxs-lookup"><span data-stu-id="fff3f-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="fff3f-141">Obvyklá volba je profiler a existují různé možnosti profileru, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="fff3f-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="fff3f-142">Linux</span><span class="sxs-lookup"><span data-stu-id="fff3f-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="fff3f-143">`perf`Nástroj lze použít ke generování profilů aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fff3f-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="fff3f-144">Ukončí předchozí instanci [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios).</span><span class="sxs-lookup"><span data-stu-id="fff3f-144">Exit the previous instance of the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="fff3f-145">Nastavte `COMPlus_PerfMapEnabled` proměnnou prostředí, která způsobí, že aplikace .NET Core vytvoří `map` soubor v `/tmp` adresáři.</span><span class="sxs-lookup"><span data-stu-id="fff3f-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="fff3f-146">Tento `map` soubor je používán nástrojem `perf` k mapování adresy CPU na funkce generované JIT podle názvu.</span><span class="sxs-lookup"><span data-stu-id="fff3f-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="fff3f-147">Další informace najdete v tématu [zapsat mapu výkonu](../run-time-config/debugging-profiling.md#write-perf-map).</span><span class="sxs-lookup"><span data-stu-id="fff3f-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="fff3f-148">Spusťte [vzorový cíl ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) ve stejné relaci terminálu.</span><span class="sxs-lookup"><span data-stu-id="fff3f-148">Run the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="fff3f-149">Vyzkoušejte znovu koncový bod rozhraní API procesoru ( `https://localhost:5001/api/diagscenario/highcpu/60000` ).</span><span class="sxs-lookup"><span data-stu-id="fff3f-149">Exercise the high CPU API endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="fff3f-150">I když je spuštěný v rámci žádosti o 1 minutu, spusťte `perf` příkaz s ID procesu:</span><span class="sxs-lookup"><span data-stu-id="fff3f-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="fff3f-151">`perf`Příkaz spustí proces shromažďování výkonu.</span><span class="sxs-lookup"><span data-stu-id="fff3f-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="fff3f-152">Nechte běžet po dobu přibližně 20-30 sekund a potom stisknutím <kbd>kombinace kláves CTRL + C</kbd> ukončete proces shromažďování.</span><span class="sxs-lookup"><span data-stu-id="fff3f-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="fff3f-153">Stejný příkaz můžete použít `perf` k zobrazení výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="fff3f-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="fff3f-154">Pomocí následujících příkazů můžete také vygenerovat _Plamenový graf_ :</span><span class="sxs-lookup"><span data-stu-id="fff3f-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="fff3f-155">Tento příkaz vygeneruje `flamegraph.svg` , který můžete zobrazit v prohlížeči a prozkoumat problém s výkonem:</span><span class="sxs-lookup"><span data-stu-id="fff3f-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="fff3f-156">[![Obrázek SVG plamenového grafu](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="fff3f-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="fff3f-157">Windows</span><span class="sxs-lookup"><span data-stu-id="fff3f-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="fff3f-158">Ve Windows můžete použít nástroj [dotnet-Trace](dotnet-trace.md) jako profiler.</span><span class="sxs-lookup"><span data-stu-id="fff3f-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="fff3f-159">Pomocí předchozího [ukázkového cíle ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)vykonáte znovu vysoký koncový bod procesoru ( `https://localhost:5001/api/diagscenario/highcpu/60000` ).</span><span class="sxs-lookup"><span data-stu-id="fff3f-159">Using the previous [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="fff3f-160">I když je spuštěný v rámci žádosti o 1 minutu, použijte `collect` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fff3f-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="fff3f-161">Let [dotnet – spuštění trasování](dotnet-trace.md) po dobu přibližně 20-30 sekund a potom stiskněte klávesu <kbd>ENTER</kbd> pro ukončení shromažďování.</span><span class="sxs-lookup"><span data-stu-id="fff3f-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="fff3f-162">Výsledkem je `nettrace` soubor umístěný ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="fff3f-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="fff3f-163">`nettrace`Soubory jsou skvělým způsobem, jak používat existující analytické nástroje ve Windows.</span><span class="sxs-lookup"><span data-stu-id="fff3f-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="fff3f-164">Otevřete okno `nettrace` s [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) , jak je uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="fff3f-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="fff3f-165">[![Obrázek PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="fff3f-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="fff3f-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="fff3f-166">See also</span></span>

- <span data-ttu-id="fff3f-167">[dotnet – trasování](dotnet-trace.md) pro výpis procesů</span><span class="sxs-lookup"><span data-stu-id="fff3f-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="fff3f-168">[dotnet – čítače](dotnet-counters.md) pro kontrolu využití spravované paměti</span><span class="sxs-lookup"><span data-stu-id="fff3f-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="fff3f-169">[dotnet – vystavení](dotnet-dump.md) pro shromáždění a analýzu souboru s výpisem paměti</span><span class="sxs-lookup"><span data-stu-id="fff3f-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="fff3f-170">dotnet/Diagnostika</span><span class="sxs-lookup"><span data-stu-id="fff3f-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="fff3f-171">Další kroky</span><span class="sxs-lookup"><span data-stu-id="fff3f-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fff3f-172">Ladění zablokování v .NET Core</span><span class="sxs-lookup"><span data-stu-id="fff3f-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
