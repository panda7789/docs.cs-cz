---
title: dotnet-trace tool - .NET Core
description: Installing and using the dotnet-trace command-line tool.
author: sdmaclea
ms.author: stmaclea
ms.date: 11/21/2019
ms.openlocfilehash: 07eaec843e27f5d291b6d18fab53c43051794626
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428890"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="8d705-103">dotnet-trace performance analysis utility</span><span class="sxs-lookup"><span data-stu-id="8d705-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="8d705-104">**This article applies to:** ✓ .NET Core 3.0 SDK and later versions</span><span class="sxs-lookup"><span data-stu-id="8d705-104">**This article applies to:** ✓ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="8d705-105">Install dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="8d705-105">Install dotnet-trace</span></span>

<span data-ttu-id="8d705-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span><span class="sxs-lookup"><span data-stu-id="8d705-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="8d705-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8d705-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="8d705-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8d705-108">Description</span></span>

<span data-ttu-id="8d705-109">The `dotnet-trace` tool:</span><span class="sxs-lookup"><span data-stu-id="8d705-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="8d705-110">Is a cross-platform .NET Core tool.</span><span class="sxs-lookup"><span data-stu-id="8d705-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="8d705-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span><span class="sxs-lookup"><span data-stu-id="8d705-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="8d705-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="8d705-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="8d705-113">Delivers the same experience on Windows, Linux, or macOS.</span><span class="sxs-lookup"><span data-stu-id="8d705-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="8d705-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8d705-114">Options</span></span>

- **`--version`**  

  <span data-ttu-id="8d705-115">Displays the version of the dotnet-counters utility.</span><span class="sxs-lookup"><span data-stu-id="8d705-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8d705-116">Shows command-line help.</span><span class="sxs-lookup"><span data-stu-id="8d705-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="8d705-117">Příkazy</span><span class="sxs-lookup"><span data-stu-id="8d705-117">Commands</span></span>

| <span data-ttu-id="8d705-118">Příkaz</span><span class="sxs-lookup"><span data-stu-id="8d705-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="8d705-119">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="8d705-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="8d705-120">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="8d705-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="8d705-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="8d705-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="8d705-122">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="8d705-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="8d705-123">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="8d705-123">dotnet-trace collect</span></span>

<span data-ttu-id="8d705-124">Collects a diagnostic trace from a running process.</span><span class="sxs-lookup"><span data-stu-id="8d705-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8d705-125">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8d705-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="8d705-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8d705-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="8d705-127">The process to collect the trace from.</span><span class="sxs-lookup"><span data-stu-id="8d705-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="8d705-128">Sets the size of the in-memory circular buffer, in megabytes.</span><span class="sxs-lookup"><span data-stu-id="8d705-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="8d705-129">Default 256 MB.</span><span class="sxs-lookup"><span data-stu-id="8d705-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="8d705-130">The output path for the collected trace data.</span><span class="sxs-lookup"><span data-stu-id="8d705-130">The output path for the collected trace data.</span></span> <span data-ttu-id="8d705-131">If not specified it defaults to `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="8d705-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="8d705-132">A comma-separated list of `EventPipe` providers to be enabled.</span><span class="sxs-lookup"><span data-stu-id="8d705-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="8d705-133">These providers supplement any providers implied by `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="8d705-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="8d705-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span><span class="sxs-lookup"><span data-stu-id="8d705-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="8d705-135">This list of providers is in the form:</span><span class="sxs-lookup"><span data-stu-id="8d705-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="8d705-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="8d705-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="8d705-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="8d705-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="8d705-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span><span class="sxs-lookup"><span data-stu-id="8d705-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="8d705-139">Sets the output format for the trace file conversion.</span><span class="sxs-lookup"><span data-stu-id="8d705-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="8d705-140">Výchozí hodnota je `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="8d705-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="8d705-141">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="8d705-141">dotnet-trace convert</span></span>

<span data-ttu-id="8d705-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span><span class="sxs-lookup"><span data-stu-id="8d705-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8d705-143">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8d705-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="8d705-144">Arguments</span><span class="sxs-lookup"><span data-stu-id="8d705-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="8d705-145">Input trace file to be converted.</span><span class="sxs-lookup"><span data-stu-id="8d705-145">Input trace file to be converted.</span></span> <span data-ttu-id="8d705-146">Defaults to *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="8d705-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="8d705-147">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8d705-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="8d705-148">Sets the output format for the trace file conversion.</span><span class="sxs-lookup"><span data-stu-id="8d705-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="8d705-149">Output filename.</span><span class="sxs-lookup"><span data-stu-id="8d705-149">Output filename.</span></span> <span data-ttu-id="8d705-150">Extension of target format will be added.</span><span class="sxs-lookup"><span data-stu-id="8d705-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="8d705-151">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="8d705-151">dotnet-trace ps</span></span>

<span data-ttu-id="8d705-152">Lists dotnet processes that can be attached to.</span><span class="sxs-lookup"><span data-stu-id="8d705-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8d705-153">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8d705-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="8d705-154">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="8d705-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="8d705-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span><span class="sxs-lookup"><span data-stu-id="8d705-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8d705-156">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8d705-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="8d705-157">Collect a trace with dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="8d705-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="8d705-158">To collect traces using `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="8d705-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="8d705-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span><span class="sxs-lookup"><span data-stu-id="8d705-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="8d705-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span><span class="sxs-lookup"><span data-stu-id="8d705-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="8d705-161">On Linux, for example, the `ps` command.</span><span class="sxs-lookup"><span data-stu-id="8d705-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="8d705-162">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="8d705-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="8d705-163">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8d705-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="8d705-164">The preceding command generates output similar to the following:</span><span class="sxs-lookup"><span data-stu-id="8d705-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="8d705-165">Stop collection by pressing the `<Enter>` key.</span><span class="sxs-lookup"><span data-stu-id="8d705-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="8d705-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span><span class="sxs-lookup"><span data-stu-id="8d705-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="8d705-167">View the trace captured from dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="8d705-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="8d705-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span><span class="sxs-lookup"><span data-stu-id="8d705-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="8d705-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="8d705-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="8d705-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span><span class="sxs-lookup"><span data-stu-id="8d705-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="8d705-171">You can choose between `nettrace` (the default option) and `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="8d705-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="8d705-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="8d705-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="8d705-173">The .NET Core runtime generates traces in the `nettrace` format.</span><span class="sxs-lookup"><span data-stu-id="8d705-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="8d705-174">The traces are converted to speedscope (if specified) after the trace is completed.</span><span class="sxs-lookup"><span data-stu-id="8d705-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="8d705-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span><span class="sxs-lookup"><span data-stu-id="8d705-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="8d705-176">Use dotnet-trace to collect counter values over time</span><span class="sxs-lookup"><span data-stu-id="8d705-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="8d705-177">`dotnet-trace` can:</span><span class="sxs-lookup"><span data-stu-id="8d705-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="8d705-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span><span class="sxs-lookup"><span data-stu-id="8d705-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="8d705-179">For example, in production.</span><span class="sxs-lookup"><span data-stu-id="8d705-179">For example, in production.</span></span>
* <span data-ttu-id="8d705-180">Collect traces so they don't need to be viewed in real time.</span><span class="sxs-lookup"><span data-stu-id="8d705-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="8d705-181">For example, to collect runtime performance counter values, use the following command:</span><span class="sxs-lookup"><span data-stu-id="8d705-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="8d705-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span><span class="sxs-lookup"><span data-stu-id="8d705-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="8d705-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span><span class="sxs-lookup"><span data-stu-id="8d705-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="8d705-184">The following command reduces overhead and trace size more than the preceding one:</span><span class="sxs-lookup"><span data-stu-id="8d705-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="8d705-185">The preceding command disables runtime events and the managed stack profiler.</span><span class="sxs-lookup"><span data-stu-id="8d705-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="8d705-186">.NET Providers</span><span class="sxs-lookup"><span data-stu-id="8d705-186">.NET Providers</span></span>

<span data-ttu-id="8d705-187">The .NET Core runtime supports the following .NET providers.</span><span class="sxs-lookup"><span data-stu-id="8d705-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="8d705-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span><span class="sxs-lookup"><span data-stu-id="8d705-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="8d705-189">Provider name</span><span class="sxs-lookup"><span data-stu-id="8d705-189">Provider name</span></span>                            | <span data-ttu-id="8d705-190">Informace o</span><span class="sxs-lookup"><span data-stu-id="8d705-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="8d705-191">The Runtime Provider</span><span class="sxs-lookup"><span data-stu-id="8d705-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="8d705-192">CLR Runtime Keywords</span><span class="sxs-lookup"><span data-stu-id="8d705-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="8d705-193">The Rundown Provider</span><span class="sxs-lookup"><span data-stu-id="8d705-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="8d705-194">CLR Rundown Keywords</span><span class="sxs-lookup"><span data-stu-id="8d705-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="8d705-195">Enables the sample profiler.</span><span class="sxs-lookup"><span data-stu-id="8d705-195">Enables the sample profiler.</span></span> |
