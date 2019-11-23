---
title: dotnet – trasování – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-Trace.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321580"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a><span data-ttu-id="4e526-103">Trasování pro nástroj Analýza výkonu (`dotnet-trace`)</span><span class="sxs-lookup"><span data-stu-id="4e526-103">Trace for performance analysis utility (`dotnet-trace`)</span></span>

<span data-ttu-id="4e526-104">**Tento článek se týká:** .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="4e526-104">**This article applies to:** .NET Core 3.0 SDK and later versions</span></span>

## <a name="installing-dotnet-trace"></a><span data-ttu-id="4e526-105">Instalace nástroje `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="4e526-105">Installing `dotnet-trace`</span></span>

<span data-ttu-id="4e526-106">Pokud chcete nainstalovat nejnovější verzi `dotnet-trace` [balíčku NuGet](https://www.nuget.org/packages/dotnet-trace), použijte [instalační příkaz nástroje dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="4e526-106">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="4e526-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="4e526-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="4e526-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4e526-108">Description</span></span>

<span data-ttu-id="4e526-109">Nástroj `dotnet-trace` je globální nástroj CLI pro různé platformy, který umožňuje shromažďování trasování .NET Core pro běžící proces bez nutnosti použití nativního profileru.</span><span class="sxs-lookup"><span data-stu-id="4e526-109">The `dotnet-trace` tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process without any native profiler involved.</span></span> <span data-ttu-id="4e526-110">Je postavená na platformě `EventPipe` technologie runtime .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="4e526-110">It's built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span> <span data-ttu-id="4e526-111">`dotnet-trace` přináší stejné prostředí jako v systému Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="4e526-111">`dotnet-trace` delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="4e526-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="4e526-112">Options</span></span>

- **`--version`**

<span data-ttu-id="4e526-113">Zobrazte verzi nástroje dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="4e526-113">Display the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

<span data-ttu-id="4e526-114">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="4e526-114">Show command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="4e526-115">Příkazy</span><span class="sxs-lookup"><span data-stu-id="4e526-115">Commands</span></span>

| <span data-ttu-id="4e526-116">Příkaz</span><span class="sxs-lookup"><span data-stu-id="4e526-116">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="4e526-117">dotnet – shromažďování trasování</span><span class="sxs-lookup"><span data-stu-id="4e526-117">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="4e526-118">dotnet – trasovat převod</span><span class="sxs-lookup"><span data-stu-id="4e526-118">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="4e526-119">dotnet – seznam trasování – procesy</span><span class="sxs-lookup"><span data-stu-id="4e526-119">dotnet-trace list-processes</span></span>](#dotnet-trace-list-processes) |
| [<span data-ttu-id="4e526-120">dotnet – seznam trasování – profily</span><span class="sxs-lookup"><span data-stu-id="4e526-120">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="4e526-121">dotnet – shromažďování trasování</span><span class="sxs-lookup"><span data-stu-id="4e526-121">dotnet-trace collect</span></span>

<span data-ttu-id="4e526-122">Shromažďuje diagnostické trasování ze spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="4e526-122">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4e526-123">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="4e526-123">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="4e526-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="4e526-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="4e526-125">Proces, ze kterého má být trasování shromážděno.</span><span class="sxs-lookup"><span data-stu-id="4e526-125">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="4e526-126">Nastaví velikost cyklické vyrovnávací paměti v paměti v megabajtech.</span><span class="sxs-lookup"><span data-stu-id="4e526-126">Sets the size of the in-memory circular buffer in megabytes.</span></span> <span data-ttu-id="4e526-127">Výchozí 256 MB.</span><span class="sxs-lookup"><span data-stu-id="4e526-127">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="4e526-128">Výstupní cesta pro shromážděná data trasování.</span><span class="sxs-lookup"><span data-stu-id="4e526-128">The output path for the collected trace data.</span></span> <span data-ttu-id="4e526-129">Pokud není zadaný, použije se výchozí hodnota `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="4e526-129">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="4e526-130">Seznam poskytovatelů `EventPipe` oddělených čárkami, které se mají povolit.</span><span class="sxs-lookup"><span data-stu-id="4e526-130">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="4e526-131">Tito poskytovatelé doplňují všechny poskytovatele implicitně `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="4e526-131">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="4e526-132">Pokud u konkrétního poskytovatele dojde k nekonzistenci, konfigurace tohoto nastavení bude mít přednost před implicitní konfigurací z profilu.</span><span class="sxs-lookup"><span data-stu-id="4e526-132">If there's any inconsistency for a particular provider, the configuration here takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="4e526-133">Tento seznam zprostředkovatelů je ve formátu:</span><span class="sxs-lookup"><span data-stu-id="4e526-133">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="4e526-134">`Provider` je ve formátu: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="4e526-134">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="4e526-135">`KeyValueArgs` je ve formátu: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="4e526-135">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="4e526-136">Pojmenovaná předem definovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.</span><span class="sxs-lookup"><span data-stu-id="4e526-136">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="4e526-137">Nastaví výstupní formát pro převod trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="4e526-137">Sets the output format for the trace file conversion.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="4e526-138">dotnet – trasovat převod</span><span class="sxs-lookup"><span data-stu-id="4e526-138">dotnet-trace convert</span></span>

<span data-ttu-id="4e526-139">Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.</span><span class="sxs-lookup"><span data-stu-id="4e526-139">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4e526-140">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="4e526-140">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="4e526-141">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4e526-141">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="4e526-142">Vstupní trasovací soubor, který se má převést.</span><span class="sxs-lookup"><span data-stu-id="4e526-142">Input trace file to be converted.</span></span> <span data-ttu-id="4e526-143">Výchozí hodnota je *Trace. nettrace*.</span><span class="sxs-lookup"><span data-stu-id="4e526-143">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="4e526-144">Možnosti</span><span class="sxs-lookup"><span data-stu-id="4e526-144">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="4e526-145">Nastaví výstupní formát pro převod trasovacího souboru.</span><span class="sxs-lookup"><span data-stu-id="4e526-145">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="4e526-146">Název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="4e526-146">Output filename.</span></span> <span data-ttu-id="4e526-147">Bude přidáno rozšíření cílového formátu.</span><span class="sxs-lookup"><span data-stu-id="4e526-147">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-list-processes"></a><span data-ttu-id="4e526-148">dotnet – seznam trasování – procesy</span><span class="sxs-lookup"><span data-stu-id="4e526-148">dotnet-trace list-processes</span></span>

<span data-ttu-id="4e526-149">Zobrazuje seznam procesů dotnet, které lze trasovat.</span><span class="sxs-lookup"><span data-stu-id="4e526-149">Lists dotnet processes that can be traced.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4e526-150">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="4e526-150">Synopsis</span></span>

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="4e526-151">dotnet – seznam trasování – profily</span><span class="sxs-lookup"><span data-stu-id="4e526-151">dotnet-trace list-profiles</span></span>

<span data-ttu-id="4e526-152">Vypíše předem sestavené trasovací profily s popisem toho, co jsou poskytovatelé a filtry v jednotlivých profilech.</span><span class="sxs-lookup"><span data-stu-id="4e526-152">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4e526-153">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="4e526-153">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="4e526-154">Shromáždění trasování pomocí `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="4e526-154">Collect a trace with `dotnet-trace`</span></span>

- <span data-ttu-id="4e526-155">Abyste mohli shromažďovat trasování pomocí `dotnet-trace`, musíte nejdřív zjistit identifikátor procesu (PID) aplikace .NET Core, abyste mohli shromažďovat trasování z.</span><span class="sxs-lookup"><span data-stu-id="4e526-155">To collect traces using `dotnet-trace`, you'll need to first, find out the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="4e526-156">Ve Windows existují možnosti, jako je například použití Správce úloh nebo příkazu `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="4e526-156">On Windows, there are options such as using the task manager or the `tasklist` command.</span></span>
  - <span data-ttu-id="4e526-157">V systému Linux může použití možnosti triviální `ps` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4e526-157">On Linux, the trivial option could be using `ps` command.</span></span>

<span data-ttu-id="4e526-158">K zjištění, jaké procesy .NET Core jsou spuštěny společně s jejich PID, můžete použít také příkaz [dotnet-Trace list-Process](#dotnet-trace-list-processes) .</span><span class="sxs-lookup"><span data-stu-id="4e526-158">You may also use the [dotnet-trace list-processes](#dotnet-trace-list-processes) command to find out what .NET Core processes are running, along with their PIDs.</span></span>

- <span data-ttu-id="4e526-159">Pak spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4e526-159">Then, run the following command:</span></span>

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- <span data-ttu-id="4e526-160">Nakonec zastavte shromažďování stisknutím klávesy `<Enter>` a `dotnet-trace` dokončí protokolování událostí do souboru `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="4e526-160">Finally, stop collection by pressing the `<Enter>` key, and `dotnet-trace` will finish logging events to `trace.nettrace` file.</span></span>

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="4e526-161">Zobrazení trasování zachyceného z `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="4e526-161">Viewing the trace captured from `dotnet-trace`</span></span>

<span data-ttu-id="4e526-162">V systému Windows je možné `.nettrace` soubory zobrazit na [PerfView](https://github.com/microsoft/perfview) pro účely analýzy, stejně jako trasování shromážděná pomocí trasování událostí pro Windows nebo LTTng.</span><span class="sxs-lookup"><span data-stu-id="4e526-162">On Windows, `.nettrace` files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis, just like traces collected with ETW or LTTng.</span></span> <span data-ttu-id="4e526-163">Pro trasování shromážděná v systému Linux můžete přemístit trasování na počítač s Windows, který se bude zobrazovat na PerfView.</span><span class="sxs-lookup"><span data-stu-id="4e526-163">For traces collected on Linux, you can move the trace to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="4e526-164">Trasování na počítači se systémem Linux můžete zobrazit také tak, že změníte výstupní formát `dotnet-trace` na `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="4e526-164">You may also view the trace on a Linux machine by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="4e526-165">Formát výstupního souboru můžete změnit pomocí možnosti `-f|--format` – `-f speedscope` vytvoří `dotnet-trace` k vytvoření souboru `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="4e526-165">You can change the output file format using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` to produce a `speedscope` file.</span></span> <span data-ttu-id="4e526-166">V současné době si můžete vybrat mezi `nettrace` (výchozí možnost) a `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="4e526-166">You can currently choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="4e526-167">soubory `Speedscope` lze otevřít na <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="4e526-167">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="4e526-168">Modul runtime .NET Core generuje trasování ve formátu `nettrace` a po dokončení trasování se převedou na speedscope (Pokud je zadaný).</span><span class="sxs-lookup"><span data-stu-id="4e526-168">The .NET Core runtime generates traces in the `nettrace` format, and they're converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="4e526-169">Vzhledem k tomu, že některé převody mohou mít za následek ztrátu dat, původní `nettrace` soubor se zachová vedle převedeného souboru.</span><span class="sxs-lookup"><span data-stu-id="4e526-169">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="4e526-170">Shromažďování hodnot čítačů v čase pomocí `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="4e526-170">Using `dotnet-trace` to collect counter values over time</span></span>

<span data-ttu-id="4e526-171">Pokud se pokoušíte použít `EventCounter` pro základní monitorování stavu v nastavení citlivém na výkon, jako jsou produkční prostředí, a chcete shromažďovat trasování místo jejich sledování v reálném čase, můžete to udělat i s `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="4e526-171">If you're trying to use `EventCounter` for basic health monitoring in  performance-sensitive settings like production environments and you want to collect traces instead of watching them in real time, you can do that with `dotnet-trace` as well.</span></span>

<span data-ttu-id="4e526-172">Například pokud chcete shromáždit hodnoty čítače výkonu modulu runtime, můžete použít následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4e526-172">For example, if you want to collect runtime performance counter values, you can use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="4e526-173">Tento příkaz oznamuje čítačům modulu runtime, aby byly pro zjednodušené monitorování stavu hlášeny za každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="4e526-173">This command tells the runtime counters to be reported once every second for lightweight health monitoring.</span></span> <span data-ttu-id="4e526-174">Nahrazení `EventCounterIntervalSec=1` vyšší hodnotou (například 60) umožňuje shromažďovat menší trasování s méně členitými možnostmi v datech čítače.</span><span class="sxs-lookup"><span data-stu-id="4e526-174">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows you to collect a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="4e526-175">Pokud chcete zakázat běhové události pro snížení režie (a velikosti trasování) ještě více, můžete pomocí následujícího příkazu zakázat běhové události a spravovaný Profiler zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4e526-175">If you want to disable runtime events to reduce the overhead (and trace size) even further, you can use the following command to disable runtime events and managed stack profiler.</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a><span data-ttu-id="4e526-176">Poskytovatelé rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="4e526-176">.NET Providers</span></span>

<span data-ttu-id="4e526-177">Modul runtime .NET Core podporuje následující poskytovatele rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="4e526-177">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="4e526-178">.NET Core používá stejná klíčová slova k povolení trasování `Event Tracing for Windows (ETW)` i `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="4e526-178">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="4e526-179">Název zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="4e526-179">Provider name</span></span>                            | <span data-ttu-id="4e526-180">Informace</span><span class="sxs-lookup"><span data-stu-id="4e526-180">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="4e526-181">Zprostředkovatel modulu runtime</span><span class="sxs-lookup"><span data-stu-id="4e526-181">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="4e526-182">Běhová klíčová slova CLR</span><span class="sxs-lookup"><span data-stu-id="4e526-182">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="4e526-183">Poskytovatel doběhu</span><span class="sxs-lookup"><span data-stu-id="4e526-183">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="4e526-184">Doběhuá klíčová slova CLR</span><span class="sxs-lookup"><span data-stu-id="4e526-184">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="4e526-185">Povolí vzorový Profiler.</span><span class="sxs-lookup"><span data-stu-id="4e526-185">Enables the sample profiler.</span></span> |
