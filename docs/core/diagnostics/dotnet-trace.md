---
title: dotnet – trasování – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-Trace.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321580"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a>Trasování pro nástroj Analýza výkonu (`dotnet-trace`)

**Tento článek se týká:** .net Core 3,0 SDK a novějších verzí

## <a name="installing-dotnet-trace"></a>Instalace nástroje `dotnet-trace`

Pokud chcete nainstalovat nejnovější verzi `dotnet-trace` [balíčku NuGet](https://www.nuget.org/packages/dotnet-trace), použijte [instalační příkaz nástroje dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Popis

Nástroj `dotnet-trace` je globální nástroj CLI pro různé platformy, který umožňuje shromažďování trasování .NET Core pro běžící proces bez nutnosti použití nativního profileru. Je postavená na platformě `EventPipe` technologie runtime .NET Core pro různé platformy. `dotnet-trace` přináší stejné prostředí jako v systému Windows, Linux nebo macOS.

## <a name="options"></a>Možnosti

- **`--version`**

Zobrazte verzi nástroje dotnet-Counters.

- **`-h|--help`**

Zobrazí pomocníka s příkazovým řádkem.

## <a name="commands"></a>Příkazy

| Příkaz                                                     |
| ----------------------------------------------------------- |
| [dotnet – shromažďování trasování](#dotnet-trace-collect)               |
| [dotnet – trasovat převod](#dotnet-trace-convert)               |
| [dotnet – seznam trasování – procesy](#dotnet-trace-list-processes) |
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

  Nastaví velikost cyklické vyrovnávací paměti v paměti v megabajtech. Výchozí 256 MB.

- **`-o|--output <trace-file-path>`**

  Výstupní cesta pro shromážděná data trasování. Pokud není zadaný, použije se výchozí hodnota `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Seznam poskytovatelů `EventPipe` oddělených čárkami, které se mají povolit. Tito poskytovatelé doplňují všechny poskytovatele implicitně `--profile <profile-name>`. Pokud u konkrétního poskytovatele dojde k nekonzistenci, konfigurace tohoto nastavení bude mít přednost před implicitní konfigurací z profilu.

  Tento seznam zprostředkovatelů je ve formátu:

  - `Provider[,Provider]`
  - `Provider` je ve formátu: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` je ve formátu: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Pojmenovaná předem definovaná sada konfigurací zprostředkovatele, která umožňuje stručně zadat běžné scénáře trasování.

- **`--format <NetTrace|Speedscope>`**

  Nastaví výstupní formát pro převod trasovacího souboru.

## <a name="dotnet-trace-convert"></a>dotnet – trasovat převod

Převede `nettrace` trasování na alternativní formáty pro použití s alternativními nástroji pro analýzu trasování.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Argumenty

- **`<input-filename>`**

  Vstupní trasovací soubor, který se má převést. Výchozí hodnota je *Trace. nettrace*.

### <a name="options"></a>Možnosti

- **`--format <NetTrace|Speedscope>`**

  Nastaví výstupní formát pro převod trasovacího souboru.

- **`-o|--output <output-filename>`**

  Název výstupního souboru. Bude přidáno rozšíření cílového formátu.

## <a name="dotnet-trace-list-processes"></a>dotnet – seznam trasování – procesy

Zobrazuje seznam procesů dotnet, které lze trasovat.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet – seznam trasování – profily

Vypíše předem sestavené trasovací profily s popisem toho, co jsou poskytovatelé a filtry v jednotlivých profilech.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Shromáždění trasování pomocí `dotnet-trace`

- Abyste mohli shromažďovat trasování pomocí `dotnet-trace`, musíte nejdřív zjistit identifikátor procesu (PID) aplikace .NET Core, abyste mohli shromažďovat trasování z.

  - Ve Windows existují možnosti, jako je například použití Správce úloh nebo příkazu `tasklist`.
  - V systému Linux může použití možnosti triviální `ps` příkaz.

K zjištění, jaké procesy .NET Core jsou spuštěny společně s jejich PID, můžete použít také příkaz [dotnet-Trace list-Process](#dotnet-trace-list-processes) .

- Pak spusťte následující příkaz:

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- Nakonec zastavte shromažďování stisknutím klávesy `<Enter>` a `dotnet-trace` dokončí protokolování událostí do souboru `trace.nettrace`.

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a>Zobrazení trasování zachyceného z `dotnet-trace`

V systému Windows je možné `.nettrace` soubory zobrazit na [PerfView](https://github.com/microsoft/perfview) pro účely analýzy, stejně jako trasování shromážděná pomocí trasování událostí pro Windows nebo LTTng. Pro trasování shromážděná v systému Linux můžete přemístit trasování na počítač s Windows, který se bude zobrazovat na PerfView.

Trasování na počítači se systémem Linux můžete zobrazit také tak, že změníte výstupní formát `dotnet-trace` na `speedscope`. Formát výstupního souboru můžete změnit pomocí možnosti `-f|--format` – `-f speedscope` vytvoří `dotnet-trace` k vytvoření souboru `speedscope`. V současné době si můžete vybrat mezi `nettrace` (výchozí možnost) a `speedscope`. soubory `Speedscope` lze otevřít na <https://www.speedscope.app>.

> [!NOTE]
> Modul runtime .NET Core generuje trasování ve formátu `nettrace` a po dokončení trasování se převedou na speedscope (Pokud je zadaný). Vzhledem k tomu, že některé převody mohou mít za následek ztrátu dat, původní `nettrace` soubor se zachová vedle převedeného souboru.

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a>Shromažďování hodnot čítačů v čase pomocí `dotnet-trace`

Pokud se pokoušíte použít `EventCounter` pro základní monitorování stavu v nastavení citlivém na výkon, jako jsou produkční prostředí, a chcete shromažďovat trasování místo jejich sledování v reálném čase, můžete to udělat i s `dotnet-trace`.

Například pokud chcete shromáždit hodnoty čítače výkonu modulu runtime, můžete použít následující příkaz:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Tento příkaz oznamuje čítačům modulu runtime, aby byly pro zjednodušené monitorování stavu hlášeny za každou sekundu. Nahrazení `EventCounterIntervalSec=1` vyšší hodnotou (například 60) umožňuje shromažďovat menší trasování s méně členitými možnostmi v datech čítače.

Pokud chcete zakázat běhové události pro snížení režie (a velikosti trasování) ještě více, můžete pomocí následujícího příkazu zakázat běhové události a spravovaný Profiler zásobníku.

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a>Poskytovatelé rozhraní .NET

Modul runtime .NET Core podporuje následující poskytovatele rozhraní .NET. .NET Core používá stejná klíčová slova k povolení trasování `Event Tracing for Windows (ETW)` i `EventPipe`.

| Název zprostředkovatele                            | Informace |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Zprostředkovatel modulu runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Běhová klíčová slova CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Poskytovatel doběhu](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Doběhuá klíčová slova CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Povolí vzorový Profiler. |
