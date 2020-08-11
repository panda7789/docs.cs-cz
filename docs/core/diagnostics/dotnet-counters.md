---
title: dotnet – čítače – .NET Core
description: Naučte se instalovat a používat nástroj příkazového řádku dotnet-Counter.
ms.date: 02/26/2020
ms.openlocfilehash: 6a4fd92540dbc16173dfa3a10ff9dfaa1f31f7d0
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062896"
---
# <a name="dotnet-counters"></a><span data-ttu-id="c0e6b-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="c0e6b-103">dotnet-counters</span></span>

<span data-ttu-id="c0e6b-104">**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="c0e6b-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="c0e6b-105">Instalace dotnet – čítače</span><span class="sxs-lookup"><span data-stu-id="c0e6b-105">Install dotnet-counters</span></span>

<span data-ttu-id="c0e6b-106">Chcete-li nainstalovat nejnovější verzi `dotnet-counters` [balíčku NuGet](https://www.nuget.org/packages/dotnet-counters), použijte příkaz pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="c0e6b-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="c0e6b-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c0e6b-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="c0e6b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c0e6b-108">Description</span></span>

<span data-ttu-id="c0e6b-109">`dotnet-counters`je nástroj pro monitorování výkonu, který slouží ke sledování stavu ad-hoc a prvotnímu šetření výkonu na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="c0e6b-110">Může sledovat hodnoty čítače výkonu, které jsou publikovány prostřednictvím <xref:System.Diagnostics.Tracing.EventCounter> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="c0e6b-111">Například můžete rychle monitorovat věci, jako je využití CPU, nebo četnost výjimek vyvolaných v aplikaci .NET Core, abyste viděli, jestli existují nějaké podezřelé před začnete do závažnějšího šetření výkonu pomocí `PerfView` nebo `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="c0e6b-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="c0e6b-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c0e6b-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="c0e6b-113">Zobrazí verzi nástroje dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c0e6b-114">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="c0e6b-115">Příkazy</span><span class="sxs-lookup"><span data-stu-id="c0e6b-115">Commands</span></span>

| <span data-ttu-id="c0e6b-116">Příkaz</span><span class="sxs-lookup"><span data-stu-id="c0e6b-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="c0e6b-117">dotnet – čítače jsou shromažďovány</span><span class="sxs-lookup"><span data-stu-id="c0e6b-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="c0e6b-118">dotnet – seznam čítačů</span><span class="sxs-lookup"><span data-stu-id="c0e6b-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="c0e6b-119">dotnet – monitorování čítačů</span><span class="sxs-lookup"><span data-stu-id="c0e6b-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="c0e6b-120">dotnet – čítače PS</span><span class="sxs-lookup"><span data-stu-id="c0e6b-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="c0e6b-121">dotnet – čítače jsou shromažďovány</span><span class="sxs-lookup"><span data-stu-id="c0e6b-121">dotnet-counters collect</span></span>

<span data-ttu-id="c0e6b-122">Pravidelně shromažďují vybrané hodnoty čítačů a exportují je do určeného formátu souboru pro následné zpracování.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c0e6b-123">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c0e6b-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="c0e6b-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c0e6b-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="c0e6b-125">ID procesu, který se má monitorovat</span><span class="sxs-lookup"><span data-stu-id="c0e6b-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="c0e6b-126">Počet sekund prodlevy mezi aktualizací zobrazených čítačů</span><span class="sxs-lookup"><span data-stu-id="c0e6b-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="c0e6b-127">Mezerou oddělený seznam čítačů.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-127">A space separated list of counters.</span></span> <span data-ttu-id="c0e6b-128">Čítače lze zadat `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="c0e6b-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="c0e6b-129">Pokud `provider_name` se používá bez opravňujícího `counter_name` , zobrazí se všechny čítače.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="c0e6b-130">Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [dotnet-Counters list](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="c0e6b-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="c0e6b-131">Formát, který má být exportován.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-131">The format to be exported.</span></span> <span data-ttu-id="c0e6b-132">Aktuálně dostupné: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="c0e6b-133">Název výstupního souboru</span><span class="sxs-lookup"><span data-stu-id="c0e6b-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="c0e6b-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="c0e6b-134">Examples</span></span>

- <span data-ttu-id="c0e6b-135">Shromáždí všechny čítače v intervalu obnovování 3 sekundy a vygeneruje jako výstup sdílený svazek clusteru:</span><span class="sxs-lookup"><span data-stu-id="c0e6b-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="c0e6b-136">dotnet – seznam čítačů</span><span class="sxs-lookup"><span data-stu-id="c0e6b-136">dotnet-counters list</span></span>

<span data-ttu-id="c0e6b-137">Zobrazí seznam názvů čítačů a popisů seskupených podle poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c0e6b-138">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c0e6b-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="c0e6b-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0e6b-139">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="c0e6b-140">`Microsoft.AspNetCore.Hosting`Čítače se zobrazí, pokud jsou zjištěny procesy, které podporují tyto čítače, například, když je na hostitelském počítači spuštěna aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-140">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="c0e6b-141">dotnet – monitorování čítačů</span><span class="sxs-lookup"><span data-stu-id="c0e6b-141">dotnet-counters monitor</span></span>

<span data-ttu-id="c0e6b-142">Zobrazí pravidelné aktualizace hodnot vybraných čítačů.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-142">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c0e6b-143">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c0e6b-143">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="c0e6b-144">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c0e6b-144">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="c0e6b-145">ID procesu, který se má monitorovat</span><span class="sxs-lookup"><span data-stu-id="c0e6b-145">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="c0e6b-146">Počet sekund prodlevy mezi aktualizací zobrazených čítačů</span><span class="sxs-lookup"><span data-stu-id="c0e6b-146">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="c0e6b-147">Mezerou oddělený seznam čítačů.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-147">A space separated list of counters.</span></span> <span data-ttu-id="c0e6b-148">Čítače lze zadat `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="c0e6b-148">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="c0e6b-149">Pokud `provider_name` se používá bez opravňujícího `counter_name` , zobrazí se všechny čítače.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-149">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="c0e6b-150">Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [dotnet-Counters list](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="c0e6b-150">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="c0e6b-151">Příklady</span><span class="sxs-lookup"><span data-stu-id="c0e6b-151">Examples</span></span>

- <span data-ttu-id="c0e6b-152">Monitorovat všechny čítače z `System.Runtime` intervalu aktualizace na 3 sekundy:</span><span class="sxs-lookup"><span data-stu-id="c0e6b-152">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="c0e6b-153">Monitorovat pouze využití CPU a velikost haldy GC z `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="c0e6b-153">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="c0e6b-154">Monitoruje `EventCounter` hodnoty z uživatelsky definovaného `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="c0e6b-154">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="c0e6b-155">Další informace najdete v tématu [kurz: měření výkonu pomocí EventCounters v .NET Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="c0e6b-155">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="c0e6b-156">dotnet – čítače PS</span><span class="sxs-lookup"><span data-stu-id="c0e6b-156">dotnet-counters ps</span></span>

<span data-ttu-id="c0e6b-157">Zobrazí seznam procesů dotnet, které lze monitorovat.</span><span class="sxs-lookup"><span data-stu-id="c0e6b-157">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c0e6b-158">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c0e6b-158">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="c0e6b-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0e6b-159">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
