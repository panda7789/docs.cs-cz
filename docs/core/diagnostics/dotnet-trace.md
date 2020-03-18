---
title: dotnet-trace nástroj - .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737642"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>nástroj pro analýzu výkonu dotnet-trace

**Tento článek se týká:** ✔️ .NET Core 3.0 SDK a novější verze

## <a name="install-dotnet-trace"></a>Instalace dotnet-trace

Nainstalujte `dotnet-trace` [balíček NuGet](https://www.nuget.org/packages/dotnet-trace) pomocí příkazu [instalace nástroje dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Synopse

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Popis

Nástroj: `dotnet-trace`

* Je nástroj .NET Core pro různé platformy.
* Umožňuje kolekci trasování jádra .NET spuštěného procesu bez nativního profileru.
* Je postaven a postaven `EventPipe` na technologii multiplatformní ho .NET Core runtime.
* Poskytuje stejné prostředí pro Windows, Linux nebo macOS.

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazí verzi nástroje dotnet-counters.

- **`-h|--help`**

  Zobrazí nápovědu příkazového řádku.

## <a name="commands"></a>Příkazy

| Příkaz                                                     |
| ----------------------------------------------------------- |
| [dotnet-trace collect](#dotnet-trace-collect)               |
| [dotnet-trace convert](#dotnet-trace-convert)               |
| [dotnet-trace ps](#dotnet-trace-ps) |
| [dotnet-trace list-profiles](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-trace collect

Shromažďuje diagnostické trasování z spuštěného procesu.

### <a name="synopsis"></a>Synopse

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Možnosti

- **`-p|--process-id <PID>`**

  Proces shromažďování trasování z.

- **`--buffersize <size>`**

  Nastaví velikost kruhové vyrovnávací paměti v paměti v megabajtech. Výchozí 256 MB.

- **`-o|--output <trace-file-path>`**

  Výstupní cesta pro shromážděná data trasování. Pokud není zadán, `trace.nettrace`je výchozí .

- **`--providers <list-of-comma-separated-providers>`**

  Seznam zprostředkovatelů oddělených `EventPipe` čárkami, který má být povolen. Tito poskytovatelé doplňují `--profile <profile-name>`všechny poskytovatele, kteří jsou implicitní . Pokud existuje nějaká nekonzistence pro konkrétního zprostředkovatele, tato konfigurace má přednost před implicitní konfiguraci z profilu.

  Tento seznam poskytovatelů je ve formě:

  - `Provider[,Provider]`
  - `Provider`je ve formě: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs`je ve formě: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Pojmenovaná předdefinovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.

- **`--format {NetTrace|Speedscope}`**

  Nastaví výstupní formát pro převod trasovacích souborů. Výchozí formát je `NetTrace`.

## <a name="dotnet-trace-convert"></a>dotnet-trace convert

Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.

### <a name="synopsis"></a>Synopse

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Argumenty

- **`<input-filename>`**

  Vstupní trasovací soubor, který má být převeden. Výchozí hodnota *trace.nettrace*.

### <a name="options"></a>Možnosti

- **`--format <NetTrace|Speedscope>`**

  Nastaví výstupní formát pro převod trasovacích souborů.

- **`-o|--output <output-filename>`**

  Výstupní název souboru. Bude přidáno rozšíření cílového formátu.

## <a name="dotnet-trace-ps"></a>dotnet-trace ps

Uvádí dotnet ové procesy, ke kterým lze připojit.

### <a name="synopsis"></a>Synopse

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-trace list-profiles

Zobrazí seznam předem vytvořených profilů trasování s popisem zprostředkovatelů a filtrů v jednotlivých profilech.

### <a name="synopsis"></a>Synopse

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Shromáždit trasování pomocí dotnet-trace

Chcete-li shromažďovat `dotnet-trace`stopy pomocí :

- Získejte identifikátor procesu (PID) aplikace .NET Core pro shromažďování trasování.

  - V systému Windows můžete například použít Správce úloh nebo `tasklist` příkaz.
  - Na Linuxu, například `ps` příkaz.
  - [dotnet-trace ps](#dotnet-trace-ps)

- Spusťte následující příkaz:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  Předchozí příkaz generuje výstup podobný následujícímu:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Zastavení sběru `<Enter>` stisknutím klávesy. `dotnet-trace`dokončí protokolování událostí do souboru *trace.nettrace.*

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Zobrazit trasování zachycené z dotnet-trace

V systému Windows. *.nettrace* soubory lze zobrazit na [PerfView](https://github.com/microsoft/perfview) pro analýzu: Pro trasování shromážděné na jiných platformách, trasovací soubor lze přesunout do počítače se systémem Windows k zobrazení na PerfView.

V Systému Linux lze trasování zobrazit `dotnet-trace` změnou výstupního formátu funkce `speedscope`. Formát výstupního souboru lze `-f|--format` změnit `-f speedscope` pomocí `dotnet-trace` volby - vytvoří soubor. `speedscope` Můžete si `nettrace` vybrat mezi (výchozí `speedscope`možností) a . `Speedscope`soubory lze otevřít <https://www.speedscope.app>na adrese .

> [!NOTE]
> Za běhu .NET Core generuje trasování ve `nettrace` formátu. Trasování jsou převedeny na speedscope (pokud je zadán) po dokončení trasování. Vzhledem k tomu, že některé převody mohou mít za následek ztrátu dat, původní `nettrace` soubor je zachován vedle převedeného souboru.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Použití dotnet-trace ke shromažďování hodnot čítačů v čase

`dotnet-trace`Cna:

* Používá `EventCounter` se pro základní monitorování stavu v prostředích citlivých na výkon. Například ve výrobě.
* Shromážděte stopy, aby je nebylo třeba prohlížet v reálném čase.

Chcete-li například shromažďovat hodnoty čítače výkonu za běhu, použijte následující příkaz:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Předchozí příkaz říká čítačů runtime sestavy jednou za sekundu pro zjednodušené sledování stavu. Nahrazení `EventCounterIntervalSec=1` vyšší hodnotou (například 60) umožňuje shromažďování menší trasování s menší rozlišovací schopnost v datech čítače.

Následující příkaz snižuje velikost režie a trasování více než předchozí:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Předchozí příkaz zakáže události za běhu a spravovaný profiler zásobníku.

## <a name="net-providers"></a>Zprostředkovatelé rozhraní .NET

Runtime jádra .NET podporuje následující zprostředkovatele rozhraní .NET. .NET Core používá stejná klíčová `Event Tracing for Windows (ETW)` `EventPipe` slova k povolení obou trasování.

| Název zprostředkovatele                            | Informace |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Zprostředkovatel runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Klíčová slova clr runtime](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Zprostředkovatel rundownu](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Klíčová slova clr rundown](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Povolí profilovač vzorku. |
