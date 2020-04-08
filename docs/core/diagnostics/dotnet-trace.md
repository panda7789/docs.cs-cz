---
title: dotnet-trace nástroj - .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: 6880c3721e4cab12677bd02c82ca944cc9812670
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888082"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="e5fd9-103">nástroj pro analýzu výkonu dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="e5fd9-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="e5fd9-104">**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="e5fd9-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="e5fd9-105">Instalace dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="e5fd9-105">Install dotnet-trace</span></span>

<span data-ttu-id="e5fd9-106">Nainstalujte `dotnet-trace` [balíček NuGet](https://www.nuget.org/packages/dotnet-trace) pomocí příkazu [instalace nástroje dotnet:](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="e5fd9-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="e5fd9-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="e5fd9-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="e5fd9-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e5fd9-108">Description</span></span>

<span data-ttu-id="e5fd9-109">Nástroj: `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="e5fd9-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="e5fd9-110">Je nástroj .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="e5fd9-111">Umožňuje kolekci trasování jádra .NET spuštěného procesu bez nativního profileru.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="e5fd9-112">Je postaven a postaven `EventPipe` na technologii multiplatformní ho .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="e5fd9-113">Poskytuje stejné prostředí pro Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="e5fd9-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e5fd9-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="e5fd9-115">Zobrazí verzi nástroje dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-115">Displays the version of the dotnet-trace utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e5fd9-116">Zobrazí nápovědu příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="e5fd9-117">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e5fd9-117">Commands</span></span>

| <span data-ttu-id="e5fd9-118">Příkaz</span><span class="sxs-lookup"><span data-stu-id="e5fd9-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="e5fd9-119">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="e5fd9-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="e5fd9-120">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="e5fd9-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="e5fd9-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="e5fd9-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="e5fd9-122">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="e5fd9-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="e5fd9-123">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="e5fd9-123">dotnet-trace collect</span></span>

<span data-ttu-id="e5fd9-124">Shromažďuje diagnostické trasování z spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5fd9-125">Synopse</span><span class="sxs-lookup"><span data-stu-id="e5fd9-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="e5fd9-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e5fd9-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="e5fd9-127">Proces shromažďování trasování z.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="e5fd9-128">Nastaví velikost kruhové vyrovnávací paměti v paměti v megabajtech.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="e5fd9-129">Výchozí 256 MB.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="e5fd9-130">Výstupní cesta pro shromážděná data trasování.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-130">The output path for the collected trace data.</span></span> <span data-ttu-id="e5fd9-131">Pokud není zadán, `trace.nettrace`je výchozí .</span><span class="sxs-lookup"><span data-stu-id="e5fd9-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="e5fd9-132">Seznam zprostředkovatelů oddělených `EventPipe` čárkami, který má být povolen.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="e5fd9-133">Tito poskytovatelé doplňují `--profile <profile-name>`všechny poskytovatele, kteří jsou implicitní .</span><span class="sxs-lookup"><span data-stu-id="e5fd9-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="e5fd9-134">Pokud existuje nějaká nekonzistence pro konkrétního zprostředkovatele, tato konfigurace má přednost před implicitní konfiguraci z profilu.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="e5fd9-135">Tento seznam poskytovatelů je ve formě:</span><span class="sxs-lookup"><span data-stu-id="e5fd9-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="e5fd9-136">`Provider`je ve formě: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="e5fd9-137">`KeyValueArgs`je ve formě: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="e5fd9-138">Pojmenovaná předdefinovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="e5fd9-139">Nastaví výstupní formát pro převod trasovacích souborů.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="e5fd9-140">Výchozí formát je `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="e5fd9-141">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="e5fd9-141">dotnet-trace convert</span></span>

<span data-ttu-id="e5fd9-142">Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5fd9-143">Synopse</span><span class="sxs-lookup"><span data-stu-id="e5fd9-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="e5fd9-144">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e5fd9-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="e5fd9-145">Vstupní trasovací soubor, který má být převeden.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-145">Input trace file to be converted.</span></span> <span data-ttu-id="e5fd9-146">Výchozí hodnota *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="e5fd9-147">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e5fd9-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="e5fd9-148">Nastaví výstupní formát pro převod trasovacích souborů.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="e5fd9-149">Výstupní název souboru.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-149">Output filename.</span></span> <span data-ttu-id="e5fd9-150">Bude přidáno rozšíření cílového formátu.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="e5fd9-151">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="e5fd9-151">dotnet-trace ps</span></span>

<span data-ttu-id="e5fd9-152">Uvádí dotnet ové procesy, ke kterým lze připojit.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5fd9-153">Synopse</span><span class="sxs-lookup"><span data-stu-id="e5fd9-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="e5fd9-154">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="e5fd9-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="e5fd9-155">Zobrazí seznam předem vytvořených profilů trasování s popisem zprostředkovatelů a filtrů v jednotlivých profilech.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5fd9-156">Synopse</span><span class="sxs-lookup"><span data-stu-id="e5fd9-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="e5fd9-157">Shromáždit trasování pomocí dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="e5fd9-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="e5fd9-158">Chcete-li shromažďovat `dotnet-trace`stopy pomocí :</span><span class="sxs-lookup"><span data-stu-id="e5fd9-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="e5fd9-159">Získejte identifikátor procesu (PID) aplikace .NET Core pro shromažďování trasování.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="e5fd9-160">V systému Windows můžete například použít Správce úloh nebo `tasklist` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="e5fd9-161">Na Linuxu, například `ps` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="e5fd9-162">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="e5fd9-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="e5fd9-163">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="e5fd9-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="e5fd9-164">Předchozí příkaz generuje výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="e5fd9-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="e5fd9-165">Zastavení sběru `<Enter>` stisknutím klávesy.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="e5fd9-166">`dotnet-trace`dokončí protokolování událostí do souboru *trace.nettrace.*</span><span class="sxs-lookup"><span data-stu-id="e5fd9-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="e5fd9-167">Zobrazit trasování zachycené z dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="e5fd9-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="e5fd9-168">V systému Windows. *.nettrace* soubory lze zobrazit na [PerfView](https://github.com/microsoft/perfview) pro analýzu: Pro trasování shromážděné na jiných platformách, trasovací soubor lze přesunout do počítače se systémem Windows k zobrazení na PerfView.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="e5fd9-169">V Systému Linux lze trasování zobrazit `dotnet-trace` změnou výstupního formátu funkce `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="e5fd9-170">Formát výstupního souboru lze `-f|--format` změnit `-f speedscope` pomocí `dotnet-trace` volby - vytvoří soubor. `speedscope`</span><span class="sxs-lookup"><span data-stu-id="e5fd9-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="e5fd9-171">Můžete si `nettrace` vybrat mezi (výchozí `speedscope`možností) a .</span><span class="sxs-lookup"><span data-stu-id="e5fd9-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="e5fd9-172">`Speedscope`soubory lze otevřít <https://www.speedscope.app>na adrese .</span><span class="sxs-lookup"><span data-stu-id="e5fd9-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="e5fd9-173">Za běhu .NET Core generuje trasování ve `nettrace` formátu.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="e5fd9-174">Trasování jsou převedeny na speedscope (pokud je zadán) po dokončení trasování.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="e5fd9-175">Vzhledem k tomu, že některé převody mohou mít za následek ztrátu dat, původní `nettrace` soubor je zachován vedle převedeného souboru.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="e5fd9-176">Použití dotnet-trace ke shromažďování hodnot čítačů v čase</span><span class="sxs-lookup"><span data-stu-id="e5fd9-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="e5fd9-177">`dotnet-trace`Cna:</span><span class="sxs-lookup"><span data-stu-id="e5fd9-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="e5fd9-178">Používá `EventCounter` se pro základní monitorování stavu v prostředích citlivých na výkon.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="e5fd9-179">Například ve výrobě.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-179">For example, in production.</span></span>
* <span data-ttu-id="e5fd9-180">Shromážděte stopy, aby je nebylo třeba prohlížet v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="e5fd9-181">Chcete-li například shromažďovat hodnoty čítače výkonu za běhu, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="e5fd9-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="e5fd9-182">Předchozí příkaz říká čítačů runtime sestavy jednou za sekundu pro zjednodušené sledování stavu.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="e5fd9-183">Nahrazení `EventCounterIntervalSec=1` vyšší hodnotou (například 60) umožňuje shromažďování menší trasování s menší rozlišovací schopnost v datech čítače.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="e5fd9-184">Následující příkaz snižuje velikost režie a trasování více než předchozí:</span><span class="sxs-lookup"><span data-stu-id="e5fd9-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="e5fd9-185">Předchozí příkaz zakáže události za běhu a spravovaný profiler zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="e5fd9-186">Zprostředkovatelé rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e5fd9-186">.NET Providers</span></span>

<span data-ttu-id="e5fd9-187">Runtime jádra .NET podporuje následující zprostředkovatele rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="e5fd9-188">.NET Core používá stejná klíčová `Event Tracing for Windows (ETW)` `EventPipe` slova k povolení obou trasování.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="e5fd9-189">Název zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e5fd9-189">Provider name</span></span>                            | <span data-ttu-id="e5fd9-190">Informace</span><span class="sxs-lookup"><span data-stu-id="e5fd9-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="e5fd9-191">Zprostředkovatel runtime</span><span class="sxs-lookup"><span data-stu-id="e5fd9-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="e5fd9-192">Klíčová slova clr runtime</span><span class="sxs-lookup"><span data-stu-id="e5fd9-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="e5fd9-193">Zprostředkovatel rundownu</span><span class="sxs-lookup"><span data-stu-id="e5fd9-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="e5fd9-194">Klíčová slova clr rundown</span><span class="sxs-lookup"><span data-stu-id="e5fd9-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="e5fd9-195">Povolí profilovač vzorku.</span><span class="sxs-lookup"><span data-stu-id="e5fd9-195">Enables the sample profiler.</span></span> |
