---
title: Nastavení konfigurace vláken
description: Přečtěte si o nastaveních prostředí runtime, která konfigurují vlákna pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761925"
---
# <a name="run-time-configuration-options-for-threading"></a>Možnosti konfigurace běhu pro dělení na vlákna

## <a name="cpu-groups"></a>Skupiny PROCESORů

- Konfiguruje, zda jsou vlákna automaticky distribuována napříč skupinami PROCESORů.
- Pokud toto nastavení vynecháte, nebudou vlákna distribuována mezi skupiny PROCESORů. To je ekvivalentní nastavení hodnoty na `0` .

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | – | – |
| **Proměnná prostředí** | `COMPlus_Thread_UseAllCpuGroups` | `0`– zakázáno<br/>`1`– povoleno |

## <a name="minimum-threads"></a>Minimální počet vláken

- Určuje minimální počet vláken pro fond pracovních vláken.
- Odpovídá <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> metodě.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MinThreads` | Celé číslo, které představuje minimální počet vláken |
| **Vlastnost MSBuild** | `ThreadPoolMinThreads` | Celé číslo, které představuje minimální počet vláken |
| **Proměnná prostředí** | – | – |

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
- Odpovídá <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> metodě.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Threading.ThreadPool.MaxThreads` | Celé číslo, které představuje maximální počet vláken |
| **Vlastnost MSBuild** | `ThreadPoolMaxThreads` | Celé číslo, které představuje maximální počet vláken |
| **Proměnná prostředí** | – | – |

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
