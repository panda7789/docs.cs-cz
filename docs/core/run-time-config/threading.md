---
title: Nastavení konfigurace zřetězení
description: Přečtěte si o nastavení za běhu, které konfigurují zřetězení pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789853"
---
# <a name="run-time-configuration-options-for-threading"></a>Možnosti konfigurace za běhu pro zřetězení

## <a name="cpu-groups"></a>Skupiny procesorů

- Konfiguruje, zda jsou vlákna automaticky distribuována mezi skupinami procesorů.
- Výchozí: Zakázáno (`0`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | Není dostupné. | Není dostupné. |
| **Proměnná prostředí** | `COMPlus_Thread_UseAllCpuGroups` | `0`- zakázáno<br/>`1`- povoleno |

## <a name="minimum-threads"></a>Minimální závity

- Určuje minimální počet podprocesů pro fond pracovních vláken.
- Odpovídá metodě. <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MinThreads` | Celé číslo představující minimální počet podprocesů |
| **MSBuild, vlastnost** | `ThreadPoolMinThreads` | Celé číslo představující minimální počet podprocesů |
| **Proměnná prostředí** | Není dostupné. | Není dostupné. |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

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

- Určuje maximální počet podprocesů pro fond pracovních vláken.
- Odpovídá metodě. <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Threading.ThreadPool.MaxThreads` | Celé číslo představující maximální počet podprocesů |
| **MSBuild, vlastnost** | `ThreadPoolMaxThreads` | Celé číslo představující maximální počet podprocesů |
| **Proměnná prostředí** | Není dostupné. | Není dostupné. |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

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
