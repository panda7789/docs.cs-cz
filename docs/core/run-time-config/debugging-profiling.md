---
title: Ladění nastavení konfigurace profilování
description: Přečtěte si o nastavení za běhu, které konfigurují ladění a profilování pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802797"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Možnosti konfigurace za běhu pro ladění a profilování

## <a name="enable-diagnostics"></a>Povolení diagnostiky

- Konfiguruje, zda ladicí program, profiler a diagnostika EventPipe jsou povoleny nebo zakázány.
- Výchozí hodnota:`1`Povoleno ( ).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | Není dostupné. | Není dostupné. |
| **Proměnná prostředí** | `COMPlus_EnableDiagnostics` | `1`- povoleno<br/>`0`- zakázáno |

## <a name="enable-profiling"></a>Povolit profilování

- Konfiguruje, zda je profilování povoleno pro aktuálně spuštěný proces.
- Výchozí: Zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | Není dostupné. | Není dostupné. |
| **Proměnná prostředí** | `CORECLR_ENABLE_PROFILING` | `0`- zakázáno<br/>`1`- povoleno |

## <a name="profiler-guid"></a>Identifikátor GUID profileru

- Určuje identifikátor GUID profileru, který se má načíst do aktuálně spuštěného procesu.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | Není dostupné. | Není dostupné. |
| **Proměnná prostředí** | `CORECLR_PROFILER` | *řetězec-guid* |

## <a name="profiler-location"></a>Umístění profileru

- Určuje cestu k dll profileru, která se má načíst do aktuálně spuštěného procesu (nebo 32bitového nebo 64bitového procesu).
- Pokud je nastavena více než jedna proměnná, mají přednost proměnné specifické pro bitness. Určují, jakou bitovou vlastnost profileru má být načíst.
- Další informace naleznete [v tématu Hledání knihovny profileru](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Název nastavení | Hodnoty |
| - | - | - |
| **Proměnná prostředí** | `CORECLR_PROFILER_PATH` | *cesta řetězce* |
| **Proměnná prostředí** | `CORECLR_PROFILER_PATH_32` | *cesta řetězce* |
| **Proměnná prostředí** | `CORECLR_PROFILER_PATH_64` | *cesta řetězce* |

## <a name="write-perf-map"></a>Napsat perf mapu

- Povolí nebo zakáže zápis */tmp/perf-$pid.map* na linuxové systémy.
- Výchozí: Zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | Není dostupné. | Není dostupné. |
| **Proměnná prostředí** | `COMPlus_PerfMapEnabled` | `0`- zakázáno<br/>`1`- povoleno |

## <a name="perf-log-markers"></a>Značky protokolu Perf

- Pokud `COMPlus_PerfMapEnabled` je `1`nastavena na , umožňuje nebo zakáže zadaný signál, které mají být přijaty a ignorovány jako značka v perf protokoly.
- Výchozí: Zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | Není dostupné. | Není dostupné. |
| **Proměnná prostředí** | `COMPlus_PerfMapIgnoreSignal` | `0`- zakázáno<br/>`1`- povoleno |
