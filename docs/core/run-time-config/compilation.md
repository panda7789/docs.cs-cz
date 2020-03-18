---
title: Nastavení konfigurace kompilace
description: Přečtěte si o nastavení za běhu, které konfigurují, jak kompilátor JIT funguje pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092886"
---
# <a name="run-time-configuration-options-for-compilation"></a>Možnosti konfigurace za běhu pro kompilaci

## <a name="tiered-compilation"></a>Vrstvená kompilace

- Konfiguruje, zda kompilátor just-in-time (JIT) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation). Vrstvené metody přechodů kompilace prostřednictvím dvou úrovní:
  - První vrstva generuje kód rychleji[(rychlé JIT)](#quick-jit)nebo načte předkompilovaný kód[(ReadyToRun).](#readytorun)
  - Druhá vrstva generuje optimalizovaný kód na pozadí ("optimalizace JIT").
- V rozhraní .NET Core 3.0 a novější je ve výchozím nastavení povolena vrstvená kompilace.
- V rozhraních .NET Core 2.1 a 2.2 je vrstvená kompilace ve výchozím nastavení zakázána.
- Další informace naleznete v [průvodci vrstvenou kompilací](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation` | `true`- povoleno<br/>`false`- zakázáno |
| **MSBuild, vlastnost** | `TieredCompilation` | `true`- povoleno<br/>`false`- zakázáno |
| **Proměnná prostředí** | `COMPlus_TieredCompilation` | `1`- povoleno<br/>`0`- zakázáno |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a>Rychlé JIT

- Konfiguruje, zda kompilátor JIT používá *rychlé JIT*. Pro metody, které neobsahují smyčky a pro které není k dispozici předkompilovaný kód, rychlé JIT zkompiluje rychleji, ale bez optimalizace.
- Povolení rychlé JIT snižuje dobu spuštění, ale může produkovat kód se sníženou charakteristikou výkonu. Kód může například využít více místa v zásobníku, přidělit více paměti a spustit pomaleji.
- Pokud je rychlá JIT [zakázána, ale je povolena vrstvená kompilace,](#tiered-compilation) účastní se vrstvené kompilace pouze předkompilovaný kód. Pokud metoda není předkompilován s [ReadyToRun](#readytorun), chování JIT je stejný, jako kdyby [vrstvené kompilace](#tiered-compilation) byly zakázány.
- V rozhraní .NET Core 3.0 a novějším je ve výchozím nastavení povolen rychlý JIT.
- V rozhraní .NET Core 2.1 a 2.2 je rychlé JIT ve výchozím nastavení zakázáno.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJit` | `true`- povoleno<br/>`false`- zakázáno |
| **MSBuild, vlastnost** | `TieredCompilationQuickJit` | `true`- povoleno<br/>`false`- zakázáno |
| **Proměnná prostředí** | `COMPlus_TC_QuickJit` | `1`- povoleno<br/>`0`- zakázáno |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a>Rychlé JIT pro smyčky

- Konfiguruje, zda kompilátor JIT používá rychlé JIT na metody, které obsahují smyčky.
- Povolení rychlé JIT pro smyčky může zlepšit výkon při spuštění. Dlouhotrvající smyčky však může uvíznout v méně optimalizovaný kód pro dlouhou dobu.
- Pokud je [funkce rychléHO JIT](#quick-jit) zakázána, nemá toto nastavení žádný vliv.
- Výchozí: Zakázáno (`false`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false`- zakázáno<br/>`true`- povoleno |
| **MSBuild, vlastnost** | `TieredCompilationQuickJitForLoops` | `false`- zakázáno<br/>`true`- povoleno |
| **Proměnná prostředí** | `COMPlus_TC_QuickJitForLoops` | `0`- zakázáno<br/>`1`- povoleno |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a>ReadyToRun

- Konfiguruje, zda runtime jádra .NET používá předkompilovaný kód pro bitové kopie s dostupnými daty ReadyToRun. Zakázání této možnosti vynutí runtime na kód architektury kompilace JIT.
- Další informace naleznete v tématu [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Výchozí hodnota:`1`Povoleno ( ).

| | Název nastavení | Hodnoty |
| - | - | - |
| **Proměnná prostředí** | `COMPlus_ReadyToRun` | `1`- povoleno<br/>`0`- zakázáno |
