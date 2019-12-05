---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802762"
---
# <a name="run-time-configuration-options-for-threading"></a>Možnosti konfigurace běhu pro dělení na vlákna

## <a name="cpu-groups"></a>Skupiny PROCESORů

- Konfiguruje, zda jsou vlákna automaticky distribuována napříč skupinami PROCESORů.
- Výchozí: zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_Thread_UseAllCpuGroups` | `0` – zakázáno<br/>`1` – povoleno |

## <a name="minimum-threads"></a>Minimální počet vláken

- Určuje minimální počet vláken pro nepracovní podproces pracovního procesu.
- Odpovídá metodě <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Celé číslo, které představuje minimální počet vláken |
| **Proměnná prostředí** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |

## <a name="maximum-threads"></a>Maximální počet vláken

- Určuje maximální počet vláken pro vlákno pracovního procesu.
- Odpovídá metodě <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Celé číslo, které představuje maximální počet vláken |
| **Proměnná prostředí** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
