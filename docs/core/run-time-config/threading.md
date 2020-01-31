---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789853"
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

- Určuje minimální počet vláken pro fond pracovních vláken.
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

- Určuje maximální počet vláken pro fond pracovních vláken.
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
