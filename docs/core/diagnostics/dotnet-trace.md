---
title: dotnet – nástroj trasování – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-Trace.
ms.date: 11/21/2019
ms.openlocfilehash: 64c931db5a18659707e832aaca910cfbbd6823c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714425"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="5b97c-103">dotnet – Nástroj pro analýzu výkonu trasování</span><span class="sxs-lookup"><span data-stu-id="5b97c-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="5b97c-104">**Tento článek se týká:** ✓ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="5b97c-104">**This article applies to:** ✓ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="5b97c-105">Instalace dotnet – trasování</span><span class="sxs-lookup"><span data-stu-id="5b97c-105">Install dotnet-trace</span></span>

<span data-ttu-id="5b97c-106">Nainstalujte `dotnet-trace` [balíček NuGet](https://www.nuget.org/packages/dotnet-trace) pomocí příkazu pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="5b97c-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="5b97c-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5b97c-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="5b97c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5b97c-108">Description</span></span>

<span data-ttu-id="5b97c-109">Nástroj `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="5b97c-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="5b97c-110">Je nástroj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="5b97c-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="5b97c-111">Povolí shromažďování trasování .NET Core pro spuštěný proces bez nativního profileru.</span><span class="sxs-lookup"><span data-stu-id="5b97c-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="5b97c-112">Je postaven kolem `EventPipe` technologie runtime .NET Core v různých platformách.</span><span class="sxs-lookup"><span data-stu-id="5b97c-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="5b97c-113">Nabízí stejné prostředí jako v systému Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="5b97c-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="5b97c-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5b97c-114">Options</span></span>

- **`--version`**  

  <span data-ttu-id="5b97c-115">Zobrazí verzi nástroje dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="5b97c-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5b97c-116">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="5b97c-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="5b97c-117">Příkazy</span><span class="sxs-lookup"><span data-stu-id="5b97c-117">Commands</span></span>

| <span data-ttu-id="5b97c-118">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5b97c-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="5b97c-119">dotnet – shromažďování trasování</span><span class="sxs-lookup"><span data-stu-id="5b97c-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="5b97c-120">dotnet – trasovat převod</span><span class="sxs-lookup"><span data-stu-id="5b97c-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="5b97c-121">dotnet – trasování PS</span><span class="sxs-lookup"><span data-stu-id="5b97c-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="5b97c-122">dotnet – seznam trasování – profily</span><span class="sxs-lookup"><span data-stu-id="5b97c-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="5b97c-123">dotnet – shromažďování trasování</span><span class="sxs-lookup"><span data-stu-id="5b97c-123">dotnet-trace collect</span></span>

<span data-ttu-id="5b97c-124">Shromažďuje diagnostické trasování ze spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="5b97c-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5b97c-125">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5b97c-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="5b97c-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5b97c-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="5b97c-127">Proces, ze kterého má být trasování shromážděno.</span><span class="sxs-lookup"><span data-stu-id="5b97c-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="5b97c-128">Nastaví velikost cyklické vyrovnávací paměti v paměti (v megabajtech).</span><span class="sxs-lookup"><span data-stu-id="5b97c-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="5b97c-129">Výchozí 256 MB.</span><span class="sxs-lookup"><span data-stu-id="5b97c-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="5b97c-130">Výstupní cesta pro shromážděná data trasování.</span><span class="sxs-lookup"><span data-stu-id="5b97c-130">The output path for the collected trace data.</span></span> <span data-ttu-id="5b97c-131">Pokud není zadaný, použije se výchozí hodnota `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="5b97c-132">Seznam poskytovatelů `EventPipe` oddělených čárkami, které se mají povolit.</span><span class="sxs-lookup"><span data-stu-id="5b97c-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="5b97c-133">Tito poskytovatelé doplňují všechny poskytovatele implicitně `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="5b97c-134">Pokud u konkrétního poskytovatele dojde k nekonzistenci, má tato konfigurace přednost před implicitní konfigurací z profilu.</span><span class="sxs-lookup"><span data-stu-id="5b97c-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="5b97c-135">Tento seznam zprostředkovatelů je ve formátu:</span><span class="sxs-lookup"><span data-stu-id="5b97c-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="5b97c-136">`Provider` je ve formátu: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="5b97c-137">`KeyValueArgs` je ve formátu: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="5b97c-138">Pojmenovaná předem definovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.</span><span class="sxs-lookup"><span data-stu-id="5b97c-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="5b97c-139">Nastaví výstupní formát pro převod trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="5b97c-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="5b97c-140">Výchozí hodnota je `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="5b97c-141">dotnet – trasovat převod</span><span class="sxs-lookup"><span data-stu-id="5b97c-141">dotnet-trace convert</span></span>

<span data-ttu-id="5b97c-142">Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.</span><span class="sxs-lookup"><span data-stu-id="5b97c-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5b97c-143">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5b97c-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="5b97c-144">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b97c-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="5b97c-145">Vstupní trasovací soubor, který se má převést.</span><span class="sxs-lookup"><span data-stu-id="5b97c-145">Input trace file to be converted.</span></span> <span data-ttu-id="5b97c-146">Výchozí hodnota je *Trace. nettrace*.</span><span class="sxs-lookup"><span data-stu-id="5b97c-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="5b97c-147">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5b97c-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="5b97c-148">Nastaví výstupní formát pro převod trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="5b97c-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="5b97c-149">Název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="5b97c-149">Output filename.</span></span> <span data-ttu-id="5b97c-150">Bude přidáno rozšíření cílového formátu.</span><span class="sxs-lookup"><span data-stu-id="5b97c-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="5b97c-151">dotnet – trasování PS</span><span class="sxs-lookup"><span data-stu-id="5b97c-151">dotnet-trace ps</span></span>

<span data-ttu-id="5b97c-152">Obsahuje seznam procesů dotnet, ke kterým lze připojit.</span><span class="sxs-lookup"><span data-stu-id="5b97c-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5b97c-153">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5b97c-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="5b97c-154">dotnet – seznam trasování – profily</span><span class="sxs-lookup"><span data-stu-id="5b97c-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="5b97c-155">Vypíše předem sestavené trasovací profily s popisem toho, co jsou poskytovatelé a filtry v jednotlivých profilech.</span><span class="sxs-lookup"><span data-stu-id="5b97c-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5b97c-156">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5b97c-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="5b97c-157">Shromažďování trasování pomocí dotnet – trasování</span><span class="sxs-lookup"><span data-stu-id="5b97c-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="5b97c-158">Shromažďování trasování pomocí `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="5b97c-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="5b97c-159">Získání identifikátoru procesu (PID) aplikace .NET Core za účelem shromažďování trasování z.</span><span class="sxs-lookup"><span data-stu-id="5b97c-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="5b97c-160">V systému Windows můžete použít například Správce úloh nebo příkaz `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="5b97c-161">V systému Linux, například příkaz `ps`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="5b97c-162">dotnet – trasování PS</span><span class="sxs-lookup"><span data-stu-id="5b97c-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="5b97c-163">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5b97c-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="5b97c-164">Předchozí příkaz vygeneruje výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="5b97c-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="5b97c-165">Zastavte shromažďování stisknutím klávesy `<Enter>`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="5b97c-166">`dotnet-trace` se dokončí protokolování událostí do souboru *Trace. nettrace* .</span><span class="sxs-lookup"><span data-stu-id="5b97c-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="5b97c-167">Zobrazit trasování zachycené z dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="5b97c-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="5b97c-168">V systému Windows se soubory *. nettrace* dají zobrazit na [PerfView](https://github.com/microsoft/perfview) pro analýzu: pro trasování shromážděná na jiných platformách můžete soubor trasování přesunout na počítač s Windows, aby se mohl zobrazit v PerfView.</span><span class="sxs-lookup"><span data-stu-id="5b97c-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="5b97c-169">V systému Linux lze trasování zobrazit změnou formátu výstupu `dotnet-trace` na `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="5b97c-170">Formát výstupního souboru se dá změnit pomocí možnosti `-f|--format` – `-f speedscope` `dotnet-trace` vytvoří soubor `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="5b97c-171">Můžete si vybrat mezi `nettrace` (výchozí možnost) a `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="5b97c-172">soubory `Speedscope` lze otevřít na <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="5b97c-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="5b97c-173">Modul runtime .NET Core generuje trasování ve formátu `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="5b97c-174">Trasování jsou po dokončení trasování převedeny na speedscope (Pokud je zadáno).</span><span class="sxs-lookup"><span data-stu-id="5b97c-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="5b97c-175">Vzhledem k tomu, že některé převody mohou mít za následek ztrátu dat, původní `nettrace` soubor se zachová vedle převedeného souboru.</span><span class="sxs-lookup"><span data-stu-id="5b97c-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="5b97c-176">Pomocí příkazu dotnet-Trace Shromážděte hodnoty čítačů v čase.</span><span class="sxs-lookup"><span data-stu-id="5b97c-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="5b97c-177">`dotnet-trace` může:</span><span class="sxs-lookup"><span data-stu-id="5b97c-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="5b97c-178">Použijte `EventCounter` pro základní monitorování stavu v prostředích citlivých na výkon.</span><span class="sxs-lookup"><span data-stu-id="5b97c-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="5b97c-179">Například v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="5b97c-179">For example, in production.</span></span>
* <span data-ttu-id="5b97c-180">Shromažďovat trasování, aby je nemuseli zobrazovat v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="5b97c-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="5b97c-181">Chcete-li například shromažďovat hodnoty čítače výkonu modulu runtime, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5b97c-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="5b97c-182">Předchozí příkaz přikáže čítačům modulu runtime, aby každou sekundu nahlásil pro zjednodušené monitorování stavu.</span><span class="sxs-lookup"><span data-stu-id="5b97c-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="5b97c-183">Nahrazení `EventCounterIntervalSec=1` vyšší hodnotou (například 60) umožňuje kolekci menšího trasování s méně členitosti v datech čítače.</span><span class="sxs-lookup"><span data-stu-id="5b97c-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="5b97c-184">Následující příkaz zmenší režijní a velikost trasování větší než předchozí:</span><span class="sxs-lookup"><span data-stu-id="5b97c-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="5b97c-185">Předchozí příkaz zakáže běhové události a spravovaný Profiler zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5b97c-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="5b97c-186">Poskytovatelé rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="5b97c-186">.NET Providers</span></span>

<span data-ttu-id="5b97c-187">Modul runtime .NET Core podporuje následující poskytovatele rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5b97c-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="5b97c-188">.NET Core používá stejná klíčová slova k povolení trasování `Event Tracing for Windows (ETW)` i `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="5b97c-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="5b97c-189">Název zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="5b97c-189">Provider name</span></span>                            | <span data-ttu-id="5b97c-190">Informace o nástroji</span><span class="sxs-lookup"><span data-stu-id="5b97c-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="5b97c-191">Zprostředkovatel modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5b97c-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="5b97c-192">Běhová klíčová slova CLR</span><span class="sxs-lookup"><span data-stu-id="5b97c-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="5b97c-193">Poskytovatel doběhu</span><span class="sxs-lookup"><span data-stu-id="5b97c-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="5b97c-194">Doběhuá klíčová slova CLR</span><span class="sxs-lookup"><span data-stu-id="5b97c-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="5b97c-195">Povolí vzorový Profiler.</span><span class="sxs-lookup"><span data-stu-id="5b97c-195">Enables the sample profiler.</span></span> |
