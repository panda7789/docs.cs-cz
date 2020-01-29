---
title: dotnet – čítače – .NET Core
description: Naučte se instalovat a používat nástroj příkazového řádku dotnet-Counter.
ms.date: 10/14/2019
ms.openlocfilehash: 399d5908e8ac52bcd4a20c1a819fc6c99f4de2f4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737703"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí

## <a name="install-dotnet-counters"></a>Instalace dotnet – čítače

Pokud chcete nainstalovat nejnovější verzi `dotnet-counters` [balíčku NuGet](https://www.nuget.org/packages/dotnet-counters), použijte [instalační příkaz nástroje dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Stručný obsah

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Popis

`dotnet-counters` je nástroj pro monitorování výkonu, který slouží ke sledování stavu ad-hoc a prvotnímu šetření výkonu na nejvyšší úrovni. Může sledovat hodnoty čítače výkonu, které jsou publikovány prostřednictvím rozhraní <xref:System.Diagnostics.Tracing.EventCounter> API. Například můžete rychle monitorovat věci, jako je využití CPU, nebo četnost výjimek vyvolaných v aplikaci .NET Core, abyste viděli, jestli existují nějaké podezřelé před začneteí do závažnějšího šetření výkonu pomocí `PerfView` nebo `dotnet-trace`.

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazí verzi nástroje dotnet-Counters.

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

## <a name="commands"></a>Příkazy

| Příkaz                                             |
| --------------------------------------------------- |
| [dotnet – seznam čítačů](#dotnet-counters-list)       |
| [dotnet – monitorování čítačů](#dotnet-counters-monitor) |

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
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

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

  Mezerou oddělený seznam čítačů. Čítače lze zadat `provider_name[:counter_name]`. Pokud se `provider_name` používá bez opravňujícího `counter_name`, zobrazí se všechny čítače. Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [dotnet-Counters list](#dotnet-counters-list) .

### <a name="examples"></a>Příklady

- Monitorovat všechny čítače z `System.Runtime` v intervalu obnovování po dobu 3 sekund:

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

- Monitorovat pouze využití CPU a velikost haldy GC z `System.Runtime`:

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Monitorujte `EventCounter` hodnoty z uživatelsky definované `EventSource`. Další informace najdete v tématu [kurz: jak změřit výkon pro velmi časté události pomocí EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
