---
title: dotnet – nástroj trasování – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-Trace.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737642"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>dotnet – Nástroj pro analýzu výkonu trasování

**Tento článek se týká:** ✔️ .net Core 3,0 SDK a novějších verzí

## <a name="install-dotnet-trace"></a>Instalace dotnet – trasování

Nainstalujte `dotnet-trace` [balíček NuGet](https://www.nuget.org/packages/dotnet-trace) pomocí příkazu pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Popis

Nástroj `dotnet-trace`:

* Je nástroj .NET Core pro různé platformy.
* Povolí shromažďování trasování .NET Core pro spuštěný proces bez nativního profileru.
* Je postaven kolem `EventPipe` technologie runtime .NET Core v různých platformách.
* Nabízí stejné prostředí jako v systému Windows, Linux nebo macOS.

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazí verzi nástroje dotnet-Counters.

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

## <a name="commands"></a>Příkazy

| Příkaz                                                     |
| ----------------------------------------------------------- |
| [dotnet – shromažďování trasování](#dotnet-trace-collect)               |
| [dotnet – trasovat převod](#dotnet-trace-convert)               |
| [dotnet – trasování PS](#dotnet-trace-ps) |
| [dotnet – seznam trasování – profily](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet – shromažďování trasování

Shromažďuje diagnostické trasování ze spuštěného procesu.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Možnosti

- **`-p|--process-id <PID>`**

  Proces, ze kterého má být trasování shromážděno.

- **`--buffersize <size>`**

  Nastaví velikost cyklické vyrovnávací paměti v paměti (v megabajtech). Výchozí 256 MB.

- **`-o|--output <trace-file-path>`**

  Výstupní cesta pro shromážděná data trasování. Pokud není zadaný, použije se výchozí hodnota `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Seznam poskytovatelů `EventPipe` oddělených čárkami, které se mají povolit. Tito poskytovatelé doplňují všechny poskytovatele implicitně `--profile <profile-name>`. Pokud u konkrétního poskytovatele dojde k nekonzistenci, má tato konfigurace přednost před implicitní konfigurací z profilu.

  Tento seznam zprostředkovatelů je ve formátu:

  - `Provider[,Provider]`
  - `Provider` je ve formátu: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` je ve formátu: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Pojmenovaná předem definovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.

- **`--format {NetTrace|Speedscope}`**

  Nastaví výstupní formát pro převod trasovacího souboru. Výchozí hodnota je `NetTrace`.

## <a name="dotnet-trace-convert"></a>dotnet – trasovat převod

Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Vstupní trasovací soubor, který se má převést. Výchozí hodnota je *Trace. nettrace*.

### <a name="options"></a>Možnosti

- **`--format <NetTrace|Speedscope>`**

  Nastaví výstupní formát pro převod trasovacího souboru.

- **`-o|--output <output-filename>`**

  Název výstupního souboru. Bude přidáno rozšíření cílového formátu.

## <a name="dotnet-trace-ps"></a>dotnet – trasování PS

Obsahuje seznam procesů dotnet, ke kterým lze připojit.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet – seznam trasování – profily

Vypíše předem sestavené trasovací profily s popisem toho, co jsou poskytovatelé a filtry v jednotlivých profilech.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Shromažďování trasování pomocí dotnet – trasování

Shromažďování trasování pomocí `dotnet-trace`:

- Získání identifikátoru procesu (PID) aplikace .NET Core za účelem shromažďování trasování z.

  - V systému Windows můžete použít například Správce úloh nebo příkaz `tasklist`.
  - V systému Linux, například příkaz `ps`.
  - [dotnet – trasování PS](#dotnet-trace-ps)

- Spusťte následující příkaz:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  Předchozí příkaz vygeneruje výstup podobný následujícímu:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Zastavte shromažďování stisknutím klávesy `<Enter>`. `dotnet-trace` se dokončí protokolování událostí do souboru *Trace. nettrace* .

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Zobrazit trasování zachycené z dotnet-Trace

V systému Windows se soubory *. nettrace* dají zobrazit na [PerfView](https://github.com/microsoft/perfview) pro analýzu: pro trasování shromážděná na jiných platformách můžete soubor trasování přesunout na počítač s Windows, aby se mohl zobrazit v PerfView.

V systému Linux lze trasování zobrazit změnou formátu výstupu `dotnet-trace` na `speedscope`. Formát výstupního souboru se dá změnit pomocí možnosti `-f|--format` – `-f speedscope` `dotnet-trace` vytvoří soubor `speedscope`. Můžete si vybrat mezi `nettrace` (výchozí možnost) a `speedscope`. soubory `Speedscope` lze otevřít na <https://www.speedscope.app>.

> [!NOTE]
> Modul runtime .NET Core generuje trasování ve formátu `nettrace`. Trasování jsou po dokončení trasování převedeny na speedscope (Pokud je zadáno). Vzhledem k tomu, že některé převody mohou mít za následek ztrátu dat, původní `nettrace` soubor se zachová vedle převedeného souboru.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Pomocí příkazu dotnet-Trace Shromážděte hodnoty čítačů v čase.

`dotnet-trace` může:

* Použijte `EventCounter` pro základní monitorování stavu v prostředích citlivých na výkon. Například v produkčním prostředí.
* Shromažďovat trasování, aby je nemuseli zobrazovat v reálném čase.

Chcete-li například shromažďovat hodnoty čítače výkonu modulu runtime, použijte následující příkaz:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Předchozí příkaz přikáže čítačům modulu runtime, aby každou sekundu nahlásil pro zjednodušené monitorování stavu. Nahrazení `EventCounterIntervalSec=1` vyšší hodnotou (například 60) umožňuje kolekci menšího trasování s méně členitosti v datech čítače.

Následující příkaz zmenší režijní a velikost trasování větší než předchozí:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Předchozí příkaz zakáže běhové události a spravovaný Profiler zásobníku.

## <a name="net-providers"></a>Poskytovatelé rozhraní .NET

Modul runtime .NET Core podporuje následující poskytovatele rozhraní .NET. .NET Core používá stejná klíčová slova k povolení trasování `Event Tracing for Windows (ETW)` i `EventPipe`.

| Název zprostředkovatele                            | Informace o nástroji |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Zprostředkovatel modulu runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Běhová klíčová slova CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Poskytovatel doběhu](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Doběhuá klíčová slova CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Povolí vzorový Profiler. |
