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
# <a name="dotnet-counters"></a>dotnet-counters

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

## <a name="install-dotnet-counters"></a>Instalace čítačů dotnet

Chcete-li nainstalovat nejnovější `dotnet-counters` verzi [balíčku NuGet](https://www.nuget.org/packages/dotnet-counters), použijte příkaz [instalace nástroje dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Synopse

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Popis

`dotnet-counters`je nástroj pro sledování výkonu ad hoc sledování stavu a šetření výkonu první úrovně. Může sledovat hodnoty čítače výkonu, které jsou publikovány <xref:System.Diagnostics.Tracing.EventCounter> prostřednictvím rozhraní API. Můžete například rychle sledovat věci, jako je využití procesoru nebo rychlost výjimek vymrštěných v aplikaci .NET `PerfView` Core, abyste zjistili, zda je něco podezřelého, než se ponoříte do závažnějšího vyšetřování výkonu pomocí nebo `dotnet-trace`.

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazí verzi nástroje dotnet-counters.

- **`-h|--help`**

  Zobrazí nápovědu příkazového řádku.

## <a name="commands"></a>Příkazy

| Příkaz                                             |
| --------------------------------------------------- |
| [dotnetové čítače sbírají](#dotnet-counters-collect) |
| [seznam čítačů dotnet](#dotnet-counters-list)       |
| [monitor čítačů dotnet](#dotnet-counters-monitor) |
| [dotnet-čítače ps](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>dotnetové čítače sbírají

Pravidelně shromažďujte vybrané hodnoty čítačů a exportujte je do určeného formátu souboru pro následné zpracování.

### <a name="synopsis"></a>Synopse

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>Možnosti

- **`-p|--process-id <PID>`**

  ID procesu, který má být sledován.

- **`--refresh-interval <SECONDS>`**

  Počet sekund zpoždění mezi aktualizací zobrazených čítačů

- **`counter_list <COUNTERS>`**

  Mezera oddělený seznam čítačů. Lze zadat čítače `provider_name[:counter_name]`. Pokud `provider_name` se používá bez `counter_name`kvalifikace , jsou zobrazeny všechny čítače. Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [seznamu čítačů dotnet.](#dotnet-counters-list)

- **`--format <csv|json>`**

  TFormát, který má být exportován. V současné době k dispozici: csv, json.

- **`-o|--output <output>`**

  Název výstupního souboru

### <a name="examples"></a>Příklady

- Shromažďovat všechny čítače v intervalu aktualizace 3 sekundy a generovat csv jako výstup:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>seznam čítačů dotnet

Zobrazí seznam názvů čítačů a popisů seskupených podle zprostředkovatele.

### <a name="synopsis"></a>Synopse

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

## <a name="dotnet-counters-monitor"></a>monitor čítačů dotnet

Zobrazuje pravidelně obnovovat hodnoty vybraných čítačů.

### <a name="synopsis"></a>Synopse

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Možnosti

- **`-p|--process-id <PID>`**

  ID procesu, který má být sledován.

- **`--refresh-interval <SECONDS>`**

  Počet sekund zpoždění mezi aktualizací zobrazených čítačů

- **`counter_list <COUNTERS>`**

  Mezera oddělený seznam čítačů. Lze zadat čítače `provider_name[:counter_name]`. Pokud `provider_name` se používá bez `counter_name`kvalifikace , jsou zobrazeny všechny čítače. Chcete-li zjistit názvy zprostředkovatelů a čítačů, použijte příkaz [seznamu čítačů dotnet.](#dotnet-counters-list)

### <a name="examples"></a>Příklady

- Sledujte všechny `System.Runtime` čítače v intervalu aktualizace 3 sekundy:

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

- Monitorování pouze využití procesoru a `System.Runtime`velikost haldy GC z:

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Sledování `EventCounter` hodnot z `EventSource`uživatelem definovaného . Další informace naleznete [v tématu Návod: Jak měřit výkon pro velmi časté události pomocí EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet-čítače ps

Zobrazení seznamu dotnetových procesů, které lze sledovat.

### <a name="synopsis"></a>Synopse

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Příklad

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
