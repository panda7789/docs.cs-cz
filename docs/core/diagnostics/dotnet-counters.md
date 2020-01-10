---
title: dotnet – čítače – .NET Core
description: Naučte se instalovat a používat nástroj příkazového řádku dotnet-Counter.
ms.date: 10/14/2019
ms.openlocfilehash: 10af451a8b1b4d8b27da1490b99b19a4359c860f
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740800"
---
# <a name="dotnet-counters"></a><span data-ttu-id="79d0e-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="79d0e-103">dotnet-counters</span></span>

<span data-ttu-id="79d0e-104">**Tento článek se týká: ✓** .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="79d0e-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="79d0e-105">Instalace dotnet – čítače</span><span class="sxs-lookup"><span data-stu-id="79d0e-105">Install dotnet-counters</span></span>

<span data-ttu-id="79d0e-106">Pokud chcete nainstalovat nejnovější verzi `dotnet-counters` [balíčku NuGet](https://www.nuget.org/packages/dotnet-counters), použijte [instalační příkaz nástroje dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="79d0e-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="79d0e-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="79d0e-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="79d0e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="79d0e-108">Description</span></span>

<span data-ttu-id="79d0e-109">`dotnet-counters` je nástroj pro monitorování výkonu, který slouží ke sledování stavu ad-hoc a prvotnímu šetření výkonu na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="79d0e-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="79d0e-110">Může sledovat hodnoty čítače výkonu, které jsou publikovány prostřednictvím rozhraní <xref:System.Diagnostics.Tracing.EventCounter> API.</span><span class="sxs-lookup"><span data-stu-id="79d0e-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="79d0e-111">Například můžete rychle monitorovat věci, jako je využití CPU, nebo četnost výjimek vyvolaných v aplikaci .NET Core, abyste viděli, jestli existují nějaké podezřelé před začneteí do závažnějšího šetření výkonu pomocí `PerfView` nebo `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="79d0e-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="79d0e-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="79d0e-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="79d0e-113">Zobrazí verzi nástroje dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="79d0e-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="79d0e-114">Zobrazí pomocníka s příkazovým řádkem.</span><span class="sxs-lookup"><span data-stu-id="79d0e-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="79d0e-115">Příkazy</span><span class="sxs-lookup"><span data-stu-id="79d0e-115">Commands</span></span>

| <span data-ttu-id="79d0e-116">Příkaz</span><span class="sxs-lookup"><span data-stu-id="79d0e-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="79d0e-117">dotnet – seznam čítačů</span><span class="sxs-lookup"><span data-stu-id="79d0e-117">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="79d0e-118">dotnet – monitorování čítačů</span><span class="sxs-lookup"><span data-stu-id="79d0e-118">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a><span data-ttu-id="79d0e-119">dotnet – seznam čítačů</span><span class="sxs-lookup"><span data-stu-id="79d0e-119">dotnet-counters list</span></span>

<span data-ttu-id="79d0e-120">Zobrazí seznam názvů čítačů a popisů seskupených podle poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="79d0e-120">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="79d0e-121">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="79d0e-121">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="79d0e-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="79d0e-122">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="79d0e-123">dotnet – monitorování čítačů</span><span class="sxs-lookup"><span data-stu-id="79d0e-123">dotnet-counters monitor</span></span>

<span data-ttu-id="79d0e-124">Zobrazí pravidelné aktualizace hodnot vybraných čítačů.</span><span class="sxs-lookup"><span data-stu-id="79d0e-124">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="79d0e-125">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="79d0e-125">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="79d0e-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="79d0e-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="79d0e-127">ID procesu, který se má monitorovat</span><span class="sxs-lookup"><span data-stu-id="79d0e-127">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="79d0e-128">Počet sekund prodlevy mezi aktualizací zobrazených čítačů</span><span class="sxs-lookup"><span data-stu-id="79d0e-128">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="79d0e-129">Mezerou oddělený seznam čítačů.</span><span class="sxs-lookup"><span data-stu-id="79d0e-129">A space separated list of counters.</span></span> <span data-ttu-id="79d0e-130">Čítače lze zadat `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="79d0e-130">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="79d0e-131">Pokud se `provider_name` používá bez opravňujícího `counter_name`, zobrazí se všechny čítače.</span><span class="sxs-lookup"><span data-stu-id="79d0e-131">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="79d0e-132">Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [dotnet-Counters list](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="79d0e-132">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="79d0e-133">Příklady</span><span class="sxs-lookup"><span data-stu-id="79d0e-133">Examples</span></span>

- <span data-ttu-id="79d0e-134">Monitorovat všechny čítače z `System.Runtime` v intervalu obnovování po dobu 3 sekund:</span><span class="sxs-lookup"><span data-stu-id="79d0e-134">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="79d0e-135">Monitorovat pouze využití CPU a velikost haldy GC z `System.Runtime`:</span><span class="sxs-lookup"><span data-stu-id="79d0e-135">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="79d0e-136">Monitorujte `EventCounter` hodnoty z uživatelsky definované `EventSource`.</span><span class="sxs-lookup"><span data-stu-id="79d0e-136">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="79d0e-137">Další informace najdete v tématu [kurz: jak změřit výkon pro velmi časté události pomocí EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="79d0e-137">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
