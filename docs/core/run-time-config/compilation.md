---
title: Konfigurační nastavení kompilace
description: Přečtěte si o nastaveních modulu runtime, která konfigurují, jak kompilátor JIT funguje pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092886"
---
# <a name="run-time-configuration-options-for-compilation"></a>Možnosti konfigurace běhu pro kompilaci

## <a name="tiered-compilation"></a>Vrstvená kompilace

- Konfiguruje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation). Vrstvená kompilace metody přechází přes dvě úrovně:
  - První vrstva generuje kód rychleji ([rychlá JIT](#quick-jit)) nebo načítá předem kompilovaný kód ([ReadyToRun](#readytorun)).
  - Druhá vrstva generuje optimalizovaný kód na pozadí ("optimalizuje JIT").
- V rozhraní .NET Core 3,0 a novějších je vrstvená kompilace ve výchozím nastavení povolená.
- V .NET Core 2,1 a 2,2 je vrstvená kompilace ve výchozím nastavení zakázaná.
- Další informace najdete v [Průvodci vrstvenou kompilací](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation` | `true` – povoleno<br/>`false` – zakázáno |
| **Vlastnost MSBuild** | `TieredCompilation` | `true` – povoleno<br/>`false` – zakázáno |
| **Proměnná prostředí** | `COMPlus_TieredCompilation` | `1` – povoleno<br/>`0` – zakázáno |

### <a name="examples"></a>Příklady

soubor *runtimeconfig. JSON* :

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

## <a name="quick-jit"></a>Rychlá JIT

- Konfiguruje, zda kompilátor JIT používá *rychlou JIT*. Pro metody, které neobsahují smyčky a pro které není předem kompilovaný kód k dispozici, rychlá kompilátor JIT je zkompiluje rychleji, ale bez optimalizace.
- Povolení rychlé deaktivace JIT zkracuje čas spuštění, ale může vytvořit kód s zhoršenými charakteristikami výkonu. Kód může například použít více místa v zásobníku, přidělit více paměti a spustit pomaleji.
- Pokud je rychlá aktivace JIT zakázaná, ale je povolená [vrstvená kompilace](#tiered-compilation) , podílí se v vrstvené kompilaci jenom předem kompilovaný kód. Pokud metoda není předem kompilována s [ReadyToRun](#readytorun), chování JIT je stejné jako v případě zakázání [vrstvené kompilace](#tiered-compilation) .
- V .NET Core 3,0 a novějších verzích je ve výchozím nastavení povolená rychlá technologie JIT.
- V .NET Core 2,1 a 2,2 je rychlá technologie JIT ve výchozím nastavení zakázaná.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJit` | `true` – povoleno<br/>`false` – zakázáno |
| **Vlastnost MSBuild** | `TieredCompilationQuickJit` | `true` – povoleno<br/>`false` – zakázáno |
| **Proměnná prostředí** | `COMPlus_TC_QuickJit` | `1` – povoleno<br/>`0` – zakázáno |

### <a name="examples"></a>Příklady

soubor *runtimeconfig. JSON* :

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

## <a name="quick-jit-for-loops"></a>Rychlá JIT pro smyčky

- Konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky.
- Povolení rychlé JIT pro smyčky může zlepšit výkon při spuštění. Dlouhotrvající smyčky však můžou zablokovat v méně optimalizovaném kódu po dlouhou dobu.
- Pokud je [rychlá JIT](#quick-jit) zakázaná, toto nastavení nemá žádný vliv.
- Výchozí: zakázáno (`false`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Runtime.TieredCompilation.QuickJitForLoops` | `false` – zakázáno<br/>`true` – povoleno |
| **Vlastnost MSBuild** | `TieredCompilationQuickJitForLoops` | `false` – zakázáno<br/>`true` – povoleno |
| **Proměnná prostředí** | `COMPlus_TC_QuickJitForLoops` | `0` – zakázáno<br/>`1` – povoleno |

### <a name="examples"></a>Příklady

soubor *runtimeconfig. JSON* :

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

- Konfiguruje, zda modul runtime .NET Core používá předem kompilovaný kód pro image s dostupnými ReadyToRun daty. Když se tato možnost zakáže, vynutí modul runtime kód rozhraní kompilování JIT.
- Další informace najdete v tématu [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).
- Výchozí: povoleno (`1`).

| | Název nastavení | Hodnoty |
| - | - | - |
| **Proměnná prostředí** | `COMPlus_ReadyToRun` | `1` – povoleno<br/>`0` – zakázáno |
