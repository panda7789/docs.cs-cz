---
title: dotnetové čítače - .NET Core
description: Přečtěte si, jak nainstalovat a používat nástroj příkazového řádku čítova dotnet.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147175"
---
# <a name="dotnet-counters"></a><span data-ttu-id="d78ff-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="d78ff-103">dotnet-counters</span></span>

<span data-ttu-id="d78ff-104">**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="d78ff-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="d78ff-105">Instalace čítačů dotnet</span><span class="sxs-lookup"><span data-stu-id="d78ff-105">Install dotnet-counters</span></span>

<span data-ttu-id="d78ff-106">Chcete-li nainstalovat nejnovější `dotnet-counters` verzi [balíčku NuGet](https://www.nuget.org/packages/dotnet-counters), použijte příkaz [instalace nástroje dotnet:](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="d78ff-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="d78ff-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="d78ff-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="d78ff-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d78ff-108">Description</span></span>

<span data-ttu-id="d78ff-109">`dotnet-counters`je nástroj pro sledování výkonu ad hoc sledování stavu a šetření výkonu první úrovně.</span><span class="sxs-lookup"><span data-stu-id="d78ff-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="d78ff-110">Může sledovat hodnoty čítače výkonu, které jsou publikovány <xref:System.Diagnostics.Tracing.EventCounter> prostřednictvím rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d78ff-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="d78ff-111">Můžete například rychle sledovat věci, jako je využití procesoru nebo rychlost výjimek vymrštěných v aplikaci .NET `PerfView` Core, abyste zjistili, zda je něco podezřelého, než se ponoříte do závažnějšího vyšetřování výkonu pomocí nebo `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="d78ff-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="d78ff-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d78ff-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="d78ff-113">Zobrazí verzi nástroje dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="d78ff-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d78ff-114">Zobrazí nápovědu příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d78ff-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="d78ff-115">Příkazy</span><span class="sxs-lookup"><span data-stu-id="d78ff-115">Commands</span></span>

| <span data-ttu-id="d78ff-116">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d78ff-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="d78ff-117">dotnetové čítače sbírají</span><span class="sxs-lookup"><span data-stu-id="d78ff-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="d78ff-118">seznam čítačů dotnet</span><span class="sxs-lookup"><span data-stu-id="d78ff-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="d78ff-119">monitor čítačů dotnet</span><span class="sxs-lookup"><span data-stu-id="d78ff-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="d78ff-120">dotnet-čítače ps</span><span class="sxs-lookup"><span data-stu-id="d78ff-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="d78ff-121">dotnetové čítače sbírají</span><span class="sxs-lookup"><span data-stu-id="d78ff-121">dotnet-counters collect</span></span>

<span data-ttu-id="d78ff-122">Pravidelně shromažďujte vybrané hodnoty čítačů a exportujte je do určeného formátu souboru pro následné zpracování.</span><span class="sxs-lookup"><span data-stu-id="d78ff-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="d78ff-123">Synopse</span><span class="sxs-lookup"><span data-stu-id="d78ff-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="d78ff-124">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d78ff-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="d78ff-125">ID procesu, který má být sledován.</span><span class="sxs-lookup"><span data-stu-id="d78ff-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="d78ff-126">Počet sekund zpoždění mezi aktualizací zobrazených čítačů</span><span class="sxs-lookup"><span data-stu-id="d78ff-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="d78ff-127">Mezera oddělený seznam čítačů.</span><span class="sxs-lookup"><span data-stu-id="d78ff-127">A space separated list of counters.</span></span> <span data-ttu-id="d78ff-128">Lze zadat čítače `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="d78ff-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="d78ff-129">Pokud `provider_name` se používá bez `counter_name`kvalifikace , jsou zobrazeny všechny čítače.</span><span class="sxs-lookup"><span data-stu-id="d78ff-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="d78ff-130">Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [seznamu čítačů dotnet.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="d78ff-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="d78ff-131">TFormát, který má být exportován.</span><span class="sxs-lookup"><span data-stu-id="d78ff-131">TThe format to be exported.</span></span> <span data-ttu-id="d78ff-132">V současné době k dispozici: csv, json.</span><span class="sxs-lookup"><span data-stu-id="d78ff-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="d78ff-133">Název výstupního souboru</span><span class="sxs-lookup"><span data-stu-id="d78ff-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="d78ff-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="d78ff-134">Examples</span></span>

- <span data-ttu-id="d78ff-135">Shromažďovat všechny čítače v intervalu aktualizace 3 sekundy a generovat csv jako výstup:</span><span class="sxs-lookup"><span data-stu-id="d78ff-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="d78ff-136">seznam čítačů dotnet</span><span class="sxs-lookup"><span data-stu-id="d78ff-136">dotnet-counters list</span></span>

<span data-ttu-id="d78ff-137">Zobrazí seznam názvů čítačů a popisů seskupených podle zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d78ff-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="d78ff-138">Synopse</span><span class="sxs-lookup"><span data-stu-id="d78ff-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="d78ff-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d78ff-139">Example</span></span>

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="d78ff-140">monitor čítačů dotnet</span><span class="sxs-lookup"><span data-stu-id="d78ff-140">dotnet-counters monitor</span></span>

<span data-ttu-id="d78ff-141">Zobrazuje pravidelně obnovovat hodnoty vybraných čítačů.</span><span class="sxs-lookup"><span data-stu-id="d78ff-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="d78ff-142">Synopse</span><span class="sxs-lookup"><span data-stu-id="d78ff-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="d78ff-143">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d78ff-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="d78ff-144">ID procesu, který má být sledován.</span><span class="sxs-lookup"><span data-stu-id="d78ff-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="d78ff-145">Počet sekund zpoždění mezi aktualizací zobrazených čítačů</span><span class="sxs-lookup"><span data-stu-id="d78ff-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="d78ff-146">Mezera oddělený seznam čítačů.</span><span class="sxs-lookup"><span data-stu-id="d78ff-146">A space separated list of counters.</span></span> <span data-ttu-id="d78ff-147">Lze zadat čítače `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="d78ff-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="d78ff-148">Pokud `provider_name` se používá bez `counter_name`kvalifikace , jsou zobrazeny všechny čítače.</span><span class="sxs-lookup"><span data-stu-id="d78ff-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="d78ff-149">Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [seznamu čítačů dotnet.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="d78ff-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="d78ff-150">Příklady</span><span class="sxs-lookup"><span data-stu-id="d78ff-150">Examples</span></span>

- <span data-ttu-id="d78ff-151">Sledujte všechny `System.Runtime` čítače v intervalu aktualizace 3 sekundy:</span><span class="sxs-lookup"><span data-stu-id="d78ff-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="d78ff-152">Monitorování pouze využití procesoru a `System.Runtime`velikost haldy GC z:</span><span class="sxs-lookup"><span data-stu-id="d78ff-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="d78ff-153">Sledování `EventCounter` hodnot z `EventSource`uživatelem definovaného .</span><span class="sxs-lookup"><span data-stu-id="d78ff-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="d78ff-154">Další informace naleznete [v tématu Návod: Jak měřit výkon pro velmi časté události pomocí EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d78ff-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="d78ff-155">dotnet-čítače ps</span><span class="sxs-lookup"><span data-stu-id="d78ff-155">dotnet-counters ps</span></span>

<span data-ttu-id="d78ff-156">Zobrazení seznamu dotnetových procesů, které lze sledovat.</span><span class="sxs-lookup"><span data-stu-id="d78ff-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="d78ff-157">Synopse</span><span class="sxs-lookup"><span data-stu-id="d78ff-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="d78ff-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="d78ff-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
