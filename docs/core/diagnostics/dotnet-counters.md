---
title: dotnet – čítače – .NET Core
description: Naučte se instalovat a používat nástroj příkazového řádku dotnet-Counter.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: b2fab239713d9d19c580580496e73a91ceafcc52
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321587"
---
# <a name="dotnet-counters"></a>dotnet – čítače

**Tento článek se týká: ✓** .net Core 3,0 SDK a novějších verzí

## <a name="install-dotnet-counters"></a>Instalace dotnet – čítače

Chcete-li nainstalovat nejnovější vydanou verzi [balíčku NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, použijte příkaz pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Stručný obsah

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Popis

`dotnet-counters` je nástroj pro monitorování výkonu, který slouží ke sledování stavu ad-hoc a prvotnímu šetření výkonu na nejvyšší úrovni. Může sledovat hodnoty čítače výkonu, které jsou publikovány prostřednictvím rozhraní API <xref:System.Diagnostics.Tracing.EventCounter>. Například můžete rychle monitorovat věci, jako je využití CPU, nebo četnost výjimek vyvolaných v aplikaci .NET Core, abyste viděli, jestli existují nějaké podezřelé před začneteí do závažnějšího šetření výkonu pomocí `PerfView` nebo `dotnet-trace`.

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

- Monitoruje všechny čítače z `System.Runtime` v intervalu obnovování po dobu 3 sekund:

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

- Monitoruje hodnoty `EventCounter` od uživatelsky definovaných `EventSource`. Další informace najdete v tématu [kurz: jak změřit výkon pro velmi časté události pomocí EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
