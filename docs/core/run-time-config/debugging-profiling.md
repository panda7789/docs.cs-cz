---
title: Ladění nastavení konfigurace profilace
description: Přečtěte si o nastaveních za běhu, které konfiguruje ladění a profilování pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802797"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Možnosti konfigurace běhu pro ladění a profilování

## <a name="enable-diagnostics"></a>Povolení diagnostiky

- Nakonfiguruje, jestli jsou povolené nebo zakázané diagnostiky ladicího programu, profileru a EventPipe.
- Výchozí: povoleno (`1`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_EnableDiagnostics` | `1` – povoleno<br/>`0` – zakázáno |

## <a name="enable-profiling"></a>Povolit profilaci

- Nakonfiguruje, jestli je profilace povolená pro aktuálně běžící proces.
- Výchozí: zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `CORECLR_ENABLE_PROFILING` | `0` – zakázáno<br/>`1` – povoleno |

## <a name="profiler-guid"></a>Identifikátor GUID profileru

- Určuje identifikátor GUID profileru, který se má načíst do aktuálně spuštěného procesu.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `CORECLR_PROFILER` | *řetězec GUID* |

## <a name="profiler-location"></a>Umístění profileru

- Určuje cestu k souboru DLL profileru, která se má načíst do aktuálně spuštěného procesu (nebo 32 nebo 64 procesu).
- Pokud je nastavena více než jedna proměnná, budou mít proměnné specifické pro bitová verze přednost. Určují, které bitová verze profileru se má načíst.
- Další informace najdete v tématu [vyhledání knihovny profileru](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Název nastavení | Hodnoty |
| - | - | - |
| **Proměnná prostředí** | `CORECLR_PROFILER_PATH` | *řetězec – cesta* |
| **Proměnná prostředí** | `CORECLR_PROFILER_PATH_32` | *řetězec – cesta* |
| **Proměnná prostředí** | `CORECLR_PROFILER_PATH_64` | *řetězec – cesta* |

## <a name="write-perf-map"></a>Zapsat mapu výkonu

- Povoluje nebo zakazuje zápis */tmp/perf-$PID. map* na systémy Linux.
- Výchozí: zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_PerfMapEnabled` | `0` – zakázáno<br/>`1` – povoleno |

## <a name="perf-log-markers"></a>Značky protokolu výkonu

- Pokud je `COMPlus_PerfMapEnabled` nastaveno na hodnotu `1`, povolí nebo zakáže, aby byl zadaný signál přijat a ignorován jako značka v protokolech výkonu.
- Výchozí: zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_PerfMapIgnoreSignal` | `0` – zakázáno<br/>`1` – povoleno |
