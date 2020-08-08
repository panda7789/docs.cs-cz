---
title: dotnet – čítače – .NET Core
description: Naučte se instalovat a používat nástroj příkazového řádku dotnet-Counter.
ms.date: 02/26/2020
ms.openlocfilehash: 71e3c4f0a60960c4e672b95000bc0d67bd427514
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024625"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí

## <a name="install-dotnet-counters"></a>Instalace dotnet – čítače

Chcete-li nainstalovat nejnovější verzi `dotnet-counters` [balíčku NuGet](https://www.nuget.org/packages/dotnet-counters), použijte příkaz pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Stručný obsah

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Popis

`dotnet-counters`je nástroj pro monitorování výkonu, který slouží ke sledování stavu ad-hoc a prvotnímu šetření výkonu na nejvyšší úrovni. Může sledovat hodnoty čítače výkonu, které jsou publikovány prostřednictvím <xref:System.Diagnostics.Tracing.EventCounter> rozhraní API. Například můžete rychle monitorovat věci, jako je využití CPU, nebo četnost výjimek vyvolaných v aplikaci .NET Core, abyste viděli, jestli existují nějaké podezřelé před začnete do závažnějšího šetření výkonu pomocí `PerfView` nebo `dotnet-trace` .

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazí verzi nástroje dotnet-Counters.

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

## <a name="commands"></a>Příkazy

| Příkaz                                             |
|-----------------------------------------------------|
| [dotnet – čítače jsou shromažďovány](#dotnet-counters-collect) |
| [dotnet – seznam čítačů](#dotnet-counters-list)       |
| [dotnet – monitorování čítačů](#dotnet-counters-monitor) |
| [dotnet – čítače PS](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a>dotnet – čítače jsou shromažďovány

Pravidelně shromažďují vybrané hodnoty čítačů a exportují je do určeného formátu souboru pro následné zpracování.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>Možnosti

- **`-p|--process-id <PID>`**

  ID procesu, který se má monitorovat

- **`--refresh-interval <SECONDS>`**

  Počet sekund prodlevy mezi aktualizací zobrazených čítačů

- **`counter_list <COUNTERS>`**

  Mezerou oddělený seznam čítačů. Čítače lze zadat `provider_name[:counter_name]` . Pokud `provider_name` se používá bez opravňujícího `counter_name` , zobrazí se všechny čítače. Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [dotnet-Counters list](#dotnet-counters-list) .

- **`--format <csv|json>`**

  Formát TNelze načíst, který se má exportovat Aktuálně dostupné: CSV, JSON.

- **`-o|--output <output>`**

  Název výstupního souboru

### <a name="examples"></a>Příklady

- Shromáždí všechny čítače v intervalu obnovování 3 sekundy a vygeneruje jako výstup sdílený svazek clusteru:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>dotnet – seznam čítačů

Zobrazí seznam názvů čítačů a popisů seskupených podle poskytovatele.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>Příklad

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
> `Microsoft.AspNetCore.Hosting`Čítače se zobrazí, pokud jsou zjištěny procesy, které podporují tyto čítače, například, když je na hostitelském počítači spuštěna aplikace ASP.NET Core.

## <a name="dotnet-counters-monitor"></a>dotnet – monitorování čítačů

Zobrazí pravidelné aktualizace hodnot vybraných čítačů.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Možnosti

- **`-p|--process-id <PID>`**

  ID procesu, který se má monitorovat

- **`--refresh-interval <SECONDS>`**

  Počet sekund prodlevy mezi aktualizací zobrazených čítačů

- **`counter_list <COUNTERS>`**

  Mezerou oddělený seznam čítačů. Čítače lze zadat `provider_name[:counter_name]` . Pokud `provider_name` se používá bez opravňujícího `counter_name` , zobrazí se všechny čítače. Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [dotnet-Counters list](#dotnet-counters-list) .

### <a name="examples"></a>Příklady

- Monitorovat všechny čítače z `System.Runtime` intervalu aktualizace na 3 sekundy:

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

- Monitorovat pouze využití CPU a velikost haldy GC z `System.Runtime` :

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Monitoruje `EventCounter` hodnoty z uživatelsky definovaného `EventSource` . Další informace najdete v tématu [kurz: měření výkonu pomocí EventCounters v .NET Core](event-counter-perf.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet – čítače PS

Zobrazí seznam procesů dotnet, které lze monitorovat.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Příklad

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
