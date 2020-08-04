---
title: dotnet – nástroj trasování – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-Trace.
ms.date: 11/21/2019
ms.openlocfilehash: 25178a0e59ce9edb69d15ee761c1b9e56aa5eb3a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517305"
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

## <a name="description"></a>Description

`dotnet-trace`Nástroj:

* Je nástroj .NET Core pro různé platformy.
* Povolí shromažďování trasování .NET Core pro spuštěný proces bez nativního profileru.
* Je postaven kolem technologie pro více platforem `EventPipe` modulu runtime .NET Core.
* Nabízí stejné prostředí jako v systému Windows, Linux nebo macOS.

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

- **`--version`**

  Zobrazuje verzi nástroje dotnet-Trace.

## <a name="commands"></a>Příkazy

| Příkaz                                                   |
|-----------------------------------------------------------|
| [dotnet – shromažďování trasování](#dotnet-trace-collect)             |
| [dotnet – trasovat převod](#dotnet-trace-convert)             |
| [dotnet – trasování PS](#dotnet-trace-ps)                       |
| [dotnet – seznam trasování – profily](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a>dotnet – shromažďování trasování

Shromažďuje diagnostické trasování ze spuštěného procesu.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
```

### <a name="options"></a>Možnosti

- **`--buffersize <size>`**

  Nastaví velikost cyklické vyrovnávací paměti v paměti (v megabajtech). Výchozí 256 MB.

- **`--clreventlevel <clreventlevel>`**

  Podrobnosti událostí CLR, které se mají vygenerovat

- **`--clrevents <clrevents>`**

  Seznam událostí modulu runtime CLR k vygenerování

- **`--format {Chromium|NetTrace|Speedscope}`**

  Nastaví výstupní formát pro převod trasovacího souboru. Výchozí formát je `NetTrace`.

- **`-n, --name <name>`**

  Název procesu, ze kterého se má shromáždit trasování.

- **`-o|--output <trace-file-path>`**

  Výstupní cesta pro shromážděná data trasování. Pokud není zadaný, použije se výchozí hodnota `trace.nettrace` .

- **`-p|--process-id <PID>`**

  ID procesu, ze kterého se má shromáždit trasování

- **`--profile <profile-name>`**

  Pojmenovaná předem definovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.

- **`--providers <list-of-comma-separated-providers>`**

  Seznam zprostředkovatelů oddělených čárkami, `EventPipe` které mají být povoleny. Tito poskytovatelé doplňují všechny poskytovatele odvozené `--profile <profile-name>` . Pokud u konkrétního poskytovatele dojde k nekonzistenci, má tato konfigurace přednost před implicitní konfigurací z profilu.

  Tento seznam zprostředkovatelů je ve formátu:

  - `Provider[,Provider]`
  - `Provider`má formát: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .
  - `KeyValueArgs`má formát: `[key1=value1][;key2=value2]` .

## <a name="dotnet-trace-convert"></a>dotnet – trasovat převod

Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Vstupní trasovací soubor, který se má převést. Výchozí hodnota je *Trace. nettrace*.

### <a name="options"></a>Možnosti

- **`--format <Chromium|NetTrace|Speedscope>`**

  Nastaví výstupní formát pro převod trasovacího souboru.

- **`-o|--output <output-filename>`**

  Název výstupního souboru. Bude přidáno rozšíření cílového formátu.

## <a name="dotnet-trace-ps"></a>dotnet – trasování PS

 Zobrazuje seznam procesů dotnet, ze kterých lze shromažďovat trasování.

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

Shromažďování trasování pomocí `dotnet-trace` :

- Získání identifikátoru procesu (PID) aplikace .NET Core za účelem shromažďování trasování z.

  - Ve Windows můžete použít například Správce úloh nebo `tasklist` příkaz.
  - V systému Linux, například `ps` příkaz.
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

- Zastavte shromažďování stisknutím klávesy `<Enter>` . `dotnet-trace`dokončí protokolování událostí do souboru *Trace. nettrace* .

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Zobrazit trasování zachycené z dotnet-Trace

V systému Windows se soubory *. nettrace* dají zobrazit na [PerfView](https://github.com/microsoft/perfview) pro analýzu: pro trasování shromážděná na jiných platformách můžete soubor trasování přesunout na počítač s Windows, aby se mohl zobrazit v PerfView.

V systému Linux lze trasování zobrazit změnou formátu výstupu `dotnet-trace` na `speedscope` . Formát výstupního souboru se dá změnit pomocí `-f|--format` Možnosti – vytvoří `-f speedscope` `dotnet-trace` `speedscope` soubor. Můžete si vybrat mezi `nettrace` (výchozí možnost) a `speedscope` . `Speedscope`soubory lze otevřít na adrese <https://www.speedscope.app> .

> [!NOTE]
> Modul runtime .NET Core generuje trasování ve `nettrace` formátu. Trasování jsou po dokončení trasování převedeny na speedscope (Pokud je zadáno). Vzhledem k tomu, že některé převody můžou způsobit ztrátu dat, původní `nettrace` soubor se zachová vedle převedeného souboru.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Pomocí příkazu dotnet-Trace Shromážděte hodnoty čítačů v čase.

`dotnet-trace`nemůže

* Používá `EventCounter` se pro základní monitorování stavu v prostředích, která jsou citlivá na výkon. Například v produkčním prostředí.
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

Modul runtime .NET Core podporuje následující poskytovatele rozhraní .NET. .NET Core používá stejná klíčová slova pro povolení `Event Tracing for Windows (ETW)` `EventPipe` trasování a.

| Název zprostředkovatele                            | Informace |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Zprostředkovatel modulu runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Běhová klíčová slova CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Poskytovatel doběhu](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Doběhuá klíčová slova CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Povolí vzorový Profiler. |
