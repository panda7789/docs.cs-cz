---
title: Ladění nastavení konfigurace profilace
description: Přečtěte si o nastaveních za běhu, které konfiguruje ladění a profilování pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761990"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Možnosti konfigurace běhu pro ladění a profilování

## <a name="enable-diagnostics"></a>Povolení diagnostiky

- Nakonfiguruje, jestli jsou povolené nebo zakázané diagnostiky ladicího programu, profileru a EventPipe.
- Pokud toto nastavení vynecháte, bude Diagnostika povolena. To je ekvivalentní nastavení hodnoty na `1` .

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | – | – |
| **Proměnná prostředí** | `COMPlus_EnableDiagnostics` | `1`– povoleno<br/>`0`– zakázáno |

## <a name="enable-profiling"></a>Povolit profilaci

- Nakonfiguruje, jestli je profilace povolená pro aktuálně běžící proces.
- Pokud toto nastavení vynecháte, profilace je zakázána. To je ekvivalentní nastavení hodnoty na `0` .

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | – | – |
| **Proměnná prostředí** | `CORECLR_ENABLE_PROFILING` | `0`– zakázáno<br/>`1`– povoleno |

## <a name="profiler-guid"></a>Identifikátor GUID profileru

- Určuje identifikátor GUID profileru, který se má načíst do aktuálně spuštěného procesu.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | – | – |
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
- Pokud toto nastavení vynecháte, bude zápis mapy výkonu zakázán. To je ekvivalentní nastavení hodnoty na `0` .

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | – | – |
| **Proměnná prostředí** | `COMPlus_PerfMapEnabled` | `0`– zakázáno<br/>`1`– povoleno |

## <a name="perf-log-markers"></a>Značky protokolu výkonu

- Povolí nebo zakáže přijetí a ignorování zadaného signálu jako značky v protokolech výkonu.
- Pokud toto nastavení vynecháte, zadaný signál se Neignoruje. To je ekvivalentní nastavení hodnoty na `0` .

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | – | – |
| **Proměnná prostředí** | `COMPlus_PerfMapIgnoreSignal` | `0`– zakázáno<br/>`1`– povoleno |

> [!NOTE]
> Toto nastavení je ignorováno, pokud je [COMPlus_PerfMapEnabled](#write-perf-map) vynecháno nebo nastaveno na `0` (to je zakázáno).
