---
title: dotnet – nástroj trasování – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-Trace.
ms.date: 11/21/2019
ms.openlocfilehash: 25178a0e59ce9edb69d15ee761c1b9e56aa5eb3a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517305"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="72a8e-103">dotnet – Nástroj pro analýzu výkonu trasování</span><span class="sxs-lookup"><span data-stu-id="72a8e-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="72a8e-104">**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="72a8e-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="72a8e-105">Instalace dotnet – trasování</span><span class="sxs-lookup"><span data-stu-id="72a8e-105">Install dotnet-trace</span></span>

<span data-ttu-id="72a8e-106">Nainstalujte `dotnet-trace` [balíček NuGet](https://www.nuget.org/packages/dotnet-trace) pomocí příkazu pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="72a8e-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="72a8e-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="72a8e-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="72a8e-108">Description</span><span class="sxs-lookup"><span data-stu-id="72a8e-108">Description</span></span>

<span data-ttu-id="72a8e-109">`dotnet-trace`Nástroj:</span><span class="sxs-lookup"><span data-stu-id="72a8e-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="72a8e-110">Je nástroj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="72a8e-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="72a8e-111">Povolí shromažďování trasování .NET Core pro spuštěný proces bez nativního profileru.</span><span class="sxs-lookup"><span data-stu-id="72a8e-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="72a8e-112">Je postaven kolem technologie pro více platforem `EventPipe` modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="72a8e-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="72a8e-113">Nabízí stejné prostředí jako v systému Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="72a8e-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="72a8e-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="72a8e-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="72a8e-115">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="72a8e-115">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="72a8e-116">Zobrazuje verzi nástroje dotnet-Trace.</span><span class="sxs-lookup"><span data-stu-id="72a8e-116">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="72a8e-117">Příkazy</span><span class="sxs-lookup"><span data-stu-id="72a8e-117">Commands</span></span>

| <span data-ttu-id="72a8e-118">Příkaz</span><span class="sxs-lookup"><span data-stu-id="72a8e-118">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="72a8e-119">dotnet – shromažďování trasování</span><span class="sxs-lookup"><span data-stu-id="72a8e-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="72a8e-120">dotnet – trasovat převod</span><span class="sxs-lookup"><span data-stu-id="72a8e-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="72a8e-121">dotnet – trasování PS</span><span class="sxs-lookup"><span data-stu-id="72a8e-121">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="72a8e-122">dotnet – seznam trasování – profily</span><span class="sxs-lookup"><span data-stu-id="72a8e-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="72a8e-123">dotnet – shromažďování trasování</span><span class="sxs-lookup"><span data-stu-id="72a8e-123">dotnet-trace collect</span></span>

<span data-ttu-id="72a8e-124">Shromažďuje diagnostické trasování ze spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="72a8e-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="72a8e-125">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="72a8e-125">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
```

### <a name="options"></a><span data-ttu-id="72a8e-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="72a8e-126">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="72a8e-127">Nastaví velikost cyklické vyrovnávací paměti v paměti (v megabajtech).</span><span class="sxs-lookup"><span data-stu-id="72a8e-127">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="72a8e-128">Výchozí 256 MB.</span><span class="sxs-lookup"><span data-stu-id="72a8e-128">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="72a8e-129">Podrobnosti událostí CLR, které se mají vygenerovat</span><span class="sxs-lookup"><span data-stu-id="72a8e-129">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="72a8e-130">Seznam událostí modulu runtime CLR k vygenerování</span><span class="sxs-lookup"><span data-stu-id="72a8e-130">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="72a8e-131">Nastaví výstupní formát pro převod trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="72a8e-131">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="72a8e-132">Výchozí formát je `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="72a8e-132">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="72a8e-133">Název procesu, ze kterého se má shromáždit trasování.</span><span class="sxs-lookup"><span data-stu-id="72a8e-133">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="72a8e-134">Výstupní cesta pro shromážděná data trasování.</span><span class="sxs-lookup"><span data-stu-id="72a8e-134">The output path for the collected trace data.</span></span> <span data-ttu-id="72a8e-135">Pokud není zadaný, použije se výchozí hodnota `trace.nettrace` .</span><span class="sxs-lookup"><span data-stu-id="72a8e-135">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="72a8e-136">ID procesu, ze kterého se má shromáždit trasování</span><span class="sxs-lookup"><span data-stu-id="72a8e-136">The process id to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="72a8e-137">Pojmenovaná předem definovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.</span><span class="sxs-lookup"><span data-stu-id="72a8e-137">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="72a8e-138">Seznam zprostředkovatelů oddělených čárkami, `EventPipe` které mají být povoleny.</span><span class="sxs-lookup"><span data-stu-id="72a8e-138">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="72a8e-139">Tito poskytovatelé doplňují všechny poskytovatele odvozené `--profile <profile-name>` .</span><span class="sxs-lookup"><span data-stu-id="72a8e-139">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="72a8e-140">Pokud u konkrétního poskytovatele dojde k nekonzistenci, má tato konfigurace přednost před implicitní konfigurací z profilu.</span><span class="sxs-lookup"><span data-stu-id="72a8e-140">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="72a8e-141">Tento seznam zprostředkovatelů je ve formátu:</span><span class="sxs-lookup"><span data-stu-id="72a8e-141">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="72a8e-142">`Provider`má formát: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .</span><span class="sxs-lookup"><span data-stu-id="72a8e-142">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="72a8e-143">`KeyValueArgs`má formát: `[key1=value1][;key2=value2]` .</span><span class="sxs-lookup"><span data-stu-id="72a8e-143">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="72a8e-144">dotnet – trasovat převod</span><span class="sxs-lookup"><span data-stu-id="72a8e-144">dotnet-trace convert</span></span>

<span data-ttu-id="72a8e-145">Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.</span><span class="sxs-lookup"><span data-stu-id="72a8e-145">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="72a8e-146">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="72a8e-146">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="72a8e-147">Arguments</span><span class="sxs-lookup"><span data-stu-id="72a8e-147">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="72a8e-148">Vstupní trasovací soubor, který se má převést.</span><span class="sxs-lookup"><span data-stu-id="72a8e-148">Input trace file to be converted.</span></span> <span data-ttu-id="72a8e-149">Výchozí hodnota je *Trace. nettrace*.</span><span class="sxs-lookup"><span data-stu-id="72a8e-149">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="72a8e-150">Možnosti</span><span class="sxs-lookup"><span data-stu-id="72a8e-150">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="72a8e-151">Nastaví výstupní formát pro převod trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="72a8e-151">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="72a8e-152">Název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="72a8e-152">Output filename.</span></span> <span data-ttu-id="72a8e-153">Bude přidáno rozšíření cílového formátu.</span><span class="sxs-lookup"><span data-stu-id="72a8e-153">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="72a8e-154">dotnet – trasování PS</span><span class="sxs-lookup"><span data-stu-id="72a8e-154">dotnet-trace ps</span></span>

 <span data-ttu-id="72a8e-155">Zobrazuje seznam procesů dotnet, ze kterých lze shromažďovat trasování.</span><span class="sxs-lookup"><span data-stu-id="72a8e-155">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="72a8e-156">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="72a8e-156">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="72a8e-157">dotnet – seznam trasování – profily</span><span class="sxs-lookup"><span data-stu-id="72a8e-157">dotnet-trace list-profiles</span></span>

<span data-ttu-id="72a8e-158">Vypíše předem sestavené trasovací profily s popisem toho, co jsou poskytovatelé a filtry v jednotlivých profilech.</span><span class="sxs-lookup"><span data-stu-id="72a8e-158">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="72a8e-159">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="72a8e-159">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="72a8e-160">Shromažďování trasování pomocí dotnet – trasování</span><span class="sxs-lookup"><span data-stu-id="72a8e-160">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="72a8e-161">Shromažďování trasování pomocí `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="72a8e-161">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="72a8e-162">Získání identifikátoru procesu (PID) aplikace .NET Core za účelem shromažďování trasování z.</span><span class="sxs-lookup"><span data-stu-id="72a8e-162">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="72a8e-163">Ve Windows můžete použít například Správce úloh nebo `tasklist` příkaz.</span><span class="sxs-lookup"><span data-stu-id="72a8e-163">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="72a8e-164">V systému Linux, například `ps` příkaz.</span><span class="sxs-lookup"><span data-stu-id="72a8e-164">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="72a8e-165">dotnet – trasování PS</span><span class="sxs-lookup"><span data-stu-id="72a8e-165">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="72a8e-166">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="72a8e-166">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="72a8e-167">Předchozí příkaz vygeneruje výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="72a8e-167">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="72a8e-168">Zastavte shromažďování stisknutím klávesy `<Enter>` .</span><span class="sxs-lookup"><span data-stu-id="72a8e-168">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="72a8e-169">`dotnet-trace`dokončí protokolování událostí do souboru *Trace. nettrace* .</span><span class="sxs-lookup"><span data-stu-id="72a8e-169">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="72a8e-170">Zobrazit trasování zachycené z dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="72a8e-170">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="72a8e-171">V systému Windows se soubory *. nettrace* dají zobrazit na [PerfView](https://github.com/microsoft/perfview) pro analýzu: pro trasování shromážděná na jiných platformách můžete soubor trasování přesunout na počítač s Windows, aby se mohl zobrazit v PerfView.</span><span class="sxs-lookup"><span data-stu-id="72a8e-171">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="72a8e-172">V systému Linux lze trasování zobrazit změnou formátu výstupu `dotnet-trace` na `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="72a8e-172">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="72a8e-173">Formát výstupního souboru se dá změnit pomocí `-f|--format` Možnosti – vytvoří `-f speedscope` `dotnet-trace` `speedscope` soubor.</span><span class="sxs-lookup"><span data-stu-id="72a8e-173">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="72a8e-174">Můžete si vybrat mezi `nettrace` (výchozí možnost) a `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="72a8e-174">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="72a8e-175">`Speedscope`soubory lze otevřít na adrese <https://www.speedscope.app> .</span><span class="sxs-lookup"><span data-stu-id="72a8e-175">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="72a8e-176">Modul runtime .NET Core generuje trasování ve `nettrace` formátu.</span><span class="sxs-lookup"><span data-stu-id="72a8e-176">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="72a8e-177">Trasování jsou po dokončení trasování převedeny na speedscope (Pokud je zadáno).</span><span class="sxs-lookup"><span data-stu-id="72a8e-177">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="72a8e-178">Vzhledem k tomu, že některé převody můžou způsobit ztrátu dat, původní `nettrace` soubor se zachová vedle převedeného souboru.</span><span class="sxs-lookup"><span data-stu-id="72a8e-178">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="72a8e-179">Pomocí příkazu dotnet-Trace Shromážděte hodnoty čítačů v čase.</span><span class="sxs-lookup"><span data-stu-id="72a8e-179">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="72a8e-180">`dotnet-trace`nemůže</span><span class="sxs-lookup"><span data-stu-id="72a8e-180">`dotnet-trace` can:</span></span>

* <span data-ttu-id="72a8e-181">Používá `EventCounter` se pro základní monitorování stavu v prostředích, která jsou citlivá na výkon.</span><span class="sxs-lookup"><span data-stu-id="72a8e-181">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="72a8e-182">Například v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="72a8e-182">For example, in production.</span></span>
* <span data-ttu-id="72a8e-183">Shromažďovat trasování, aby je nemuseli zobrazovat v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="72a8e-183">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="72a8e-184">Chcete-li například shromažďovat hodnoty čítače výkonu modulu runtime, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="72a8e-184">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="72a8e-185">Předchozí příkaz přikáže čítačům modulu runtime, aby každou sekundu nahlásil pro zjednodušené monitorování stavu.</span><span class="sxs-lookup"><span data-stu-id="72a8e-185">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="72a8e-186">Nahrazení `EventCounterIntervalSec=1` vyšší hodnotou (například 60) umožňuje kolekci menšího trasování s méně členitosti v datech čítače.</span><span class="sxs-lookup"><span data-stu-id="72a8e-186">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="72a8e-187">Následující příkaz zmenší režijní a velikost trasování větší než předchozí:</span><span class="sxs-lookup"><span data-stu-id="72a8e-187">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="72a8e-188">Předchozí příkaz zakáže běhové události a spravovaný Profiler zásobníku.</span><span class="sxs-lookup"><span data-stu-id="72a8e-188">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="72a8e-189">Poskytovatelé rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="72a8e-189">.NET Providers</span></span>

<span data-ttu-id="72a8e-190">Modul runtime .NET Core podporuje následující poskytovatele rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="72a8e-190">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="72a8e-191">.NET Core používá stejná klíčová slova pro povolení `Event Tracing for Windows (ETW)` `EventPipe` trasování a.</span><span class="sxs-lookup"><span data-stu-id="72a8e-191">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="72a8e-192">Název zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="72a8e-192">Provider name</span></span>                            | <span data-ttu-id="72a8e-193">Informace</span><span class="sxs-lookup"><span data-stu-id="72a8e-193">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="72a8e-194">Zprostředkovatel modulu runtime</span><span class="sxs-lookup"><span data-stu-id="72a8e-194">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="72a8e-195">Běhová klíčová slova CLR</span><span class="sxs-lookup"><span data-stu-id="72a8e-195">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="72a8e-196">Poskytovatel doběhu</span><span class="sxs-lookup"><span data-stu-id="72a8e-196">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="72a8e-197">Doběhuá klíčová slova CLR</span><span class="sxs-lookup"><span data-stu-id="72a8e-197">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="72a8e-198">Povolí vzorový Profiler.</span><span class="sxs-lookup"><span data-stu-id="72a8e-198">Enables the sample profiler.</span></span> |
