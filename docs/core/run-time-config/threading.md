---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733430"
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
| **Vlastnost MSBuild** | `ThreadPoolMinThreads` | Celé číslo, které představuje minimální počet vláken |
| **Proměnná prostředí** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |

### <a name="examples"></a>Příklady

soubor *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a>Maximální počet vláken

- Určuje maximální počet vláken pro vlákno pracovního procesu.
- Odpovídá metodě <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Celé číslo, které představuje maximální počet vláken |
| **Vlastnost MSBuild** | `ThreadPoolMaxThreads` | Celé číslo, které představuje maximální počet vláken |
| **Proměnná prostředí** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |

### <a name="examples"></a>Příklady

soubor *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
