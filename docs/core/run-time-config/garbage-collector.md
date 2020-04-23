---
title: Nastavení konfigurace systému uvolňování paměti
description: Informace o nastavení za běhu pro konfiguraci, jak systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: ec575bdd17c8a7c290673b7085074bbba94cedef
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102863"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Možnosti konfigurace za běhu pro uvolňování paměti

Tato stránka obsahuje informace o nastavení systému uvolňování paměti (GC), které lze změnit za běhu. Pokud se snažíte dosáhnout špičkového výkonu spuštěné aplikace, zvažte použití těchto nastavení. Výchozí hodnoty však poskytují optimální výkon pro většinu aplikací v typických situacích.

Nastavení jsou uspořádána do skupin na této stránce. Nastavení v rámci každé skupiny se běžně používají ve spojení s sebou k dosažení určitého výsledku.

> [!NOTE]
>
> - Tato nastavení může také dynamicky měnit aplikace při spuštění, takže všechna nastavení běhu, která nastavíte, mohou být přepsána.
> - Některá nastavení, například [úroveň latence](../../standard/garbage-collection/latency.md), jsou obvykle nastavena pouze prostřednictvím rozhraní API v době návrhu. Tato nastavení jsou na této stránce vynechána.
> - Pro číselné hodnoty použijte desítkovou notaci pro nastavení v souboru *runtimeconfig.json* a šestnáctkový zápis pro nastavení proměnných prostředí. Pro šestnáctkové hodnoty je můžete zadat s předponou "0x" nebo bez ní.

## <a name="flavors-of-garbage-collection"></a>Příchutě uvolňování paměti

Dvě hlavní varianty uvolňování paměti jsou pracovní stanice GC a server GC. Další informace o rozdílech mezi těmito dvěma informacemi naleznete v tématu [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).

Podpříchutě uvolňování paměti jsou pozadí a non-souběžné.

Pomocí následujících nastavení vyberte varianty uvolňování paměti:

### <a name="systemgcservercomplus_gcserver"></a>Systém.GC.Server/COMPlus_gcServer

- Konfiguruje, zda aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.
- Výchozí: Uvolňování paměti`false`pracovní stanice ( ).

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false`- pracovní stanice<br/>`true`- server | .NET Jádro 1.0 |
| **MSBuild, vlastnost** | `ServerGarbageCollection` | `false`- pracovní stanice<br/>`true`- server | .NET Jádro 1.0 |
| **Proměnná prostředí** | `COMPlus_gcServer` | `0`- pracovní stanice<br/>`1`- server | .NET Jádro 1.0 |
| **app.config pro rozhraní .NET Framework** | [Server GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`- pracovní stanice<br/>`true`- server |  |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.GC.Concurrent/COMPlus_gcConcurrent

- Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžné).
- Výchozí hodnota:`true`Povoleno ( ).
- Další informace naleznete v [tématu uvolňování paměti na pozadí](../../standard/garbage-collection/background-gc.md).

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true`- pozadí GC<br/>`false`- nesouběžné GC | .NET Jádro 1.0 |
| **MSBuild, vlastnost** | `ConcurrentGarbageCollection` | `true`- pozadí GC<br/>`false`- nesouběžné GC | .NET Jádro 1.0 |
| **Proměnná prostředí** | `COMPlus_gcConcurrent` | `true`- pozadí GC<br/>`false`- nesouběžné GC | .NET Jádro 1.0 |
| **app.config pro rozhraní .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`- pozadí GC<br/>`false`- nesouběžné GC |  |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>Správa využití prostředků

Pomocí nastavení popsaných v této části můžete spravovat využití paměti a procesoru systému uvolňování paměti.

Další informace o některých z těchto nastavení naleznete v [tématu Middle ground mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu server GC.

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System.GC.HeapCount/COMPlus_GCHeapCount

- Omezuje počet hromad vytvořených systémem uvolňování paměti.
- Platí pouze pro uvolnění paměti serveru.
- Pokud je [povolena spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) což je výchozí, nastavení `n` spřažení haldy `n` GC haldy/vlákna na první procesory. (Pomocí nastavení [spřažení nebo](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) [spřažení rozsahů určete](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) přesně, které procesory chcete spárovat.)
- Pokud je [zakázána spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) toto nastavení omezuje počet hromad GC.
- Další informace naleznete v [poznámkách GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | *desítková hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapCount` | *šestnáctková hodnota* | .NET Core 3.0 |
| **app.config pro rozhraní .NET Framework** | [Počet gcheapcount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *desítková hodnota* | .NET Framework 4.6.2 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu. Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu. Chcete-li například omezit počet hromad na 16, hodnoty by 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Určuje přesné procesory, které by měly používat vlákna systému uvolňování paměti.
- Pokud je [zakázána spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) bude toto nastavení ignorováno.
- Platí pouze pro uvolnění paměti serveru.
- Hodnota je bitová maska, která definuje procesory, které jsou k dispozici pro proces. Například desetinná hodnota 1023 (nebo šestnáctkové hodnoty 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu. To určuje, že má být použito prvních 10 procesorů. Chcete-li zadat dalších 10 procesorů, tedy procesorů 10-19, zadejte desetinnou hodnotu 1047552 (nebo šestnáctkovou hodnotu 0xFFC00 nebo FFC00), což odpovídá binární hodnotě 1111 1111 1100 0000 0000.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | *desítková hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapAffinitizeMask` | *šestnáctková hodnota* | .NET Core 3.0 |
| **app.config pro rozhraní .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *desítková hodnota* | .NET Framework 4.6.2 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Určuje seznam procesorů, které mají být používány pro vlákna systému uvolňování paměti.
- Toto nastavení je podobné [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), kromě toho umožňuje zadat více než 64 procesorů.
- Pro operační systémy Windows předponu číslo procesoru nebo rozsah s odpovídající [skupinou procesoru](/windows/win32/procthread/processor-groups), například "0:1-10,0:12,1:50-52,1:70".
- Pokud je [zakázána spřažení procesoru GC,](#systemgcnoaffinitizecomplus_gcnoaffinitize) bude toto nastavení ignorováno.
- Platí pouze pro uvolnění paměti serveru.
- Další informace najdete [v tématu Lepší konfigurace procesoru pro GC na počítačích s procesory > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.GCHeapAffinitizeRanges` | Seznam procesorů oddělených čárkami nebo rozsahy procesorových čísel.<br/>Unix příklad: "1-10,12,50-52,70"<br/>Příklad systému Windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapAffinitizeRanges` | Seznam procesorů oddělených čárkami nebo rozsahy procesorových čísel.<br/>Unix příklad: "1-10,12,50-52,70"<br/>Příklad systému Windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- Konfiguruje, zda systém uvolňování paměti používá [skupiny procesoru](/windows/win32/procthread/processor-groups) nebo ne.

  Pokud 64bitový počítač se systémem Windows obsahuje více skupin procesorů, to znamená, že existuje více než 64 procesorů, povolení tohoto prvku rozšiřuje uvolňování paměti ve všech skupinách procesoru. Systém uvolňování paměti používá všechna jádra k vytvoření a vyvážení hald.

- Platí pouze pro uvolňování paměti serveru v 64bitových operačních systémech Windows.
- Výchozí: Zakázáno (`0`).
- Další informace najdete [v tématu Lepší konfigurace procesoru pro GC na počítačích s procesory > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | – | – | – |
| **Proměnná prostředí** | `COMPlus_GCCpuGroup` | `0`- zakázáno<br/>`1`- povoleno | .NET Jádro 1.0 |
| **app.config pro rozhraní .NET Framework** | [Skupina GCCpu](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`- zakázáno<br/>`true`- povoleno |  |

> [!NOTE]
> Chcete-li nakonfigurovat běžný jazyk runtime (CLR) také distribuovat podprocesy z fondu vláken ve všech skupinách procesoru, povolte [možnost Thread_UseAllCpuGroups prvek.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) Pro aplikace .NET Core můžete tuto možnost povolit `COMPlus_Thread_UseAllCpuGroups` nastavením `1`hodnoty proměnné prostředí na .

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System.GC.NoAffinitize/COMPlus_GCNoAffinitize

- Určuje, zda chcete *spárovat* vlákna uvolňování paměti s procesory. Chcete-li spřažení podprocesu GC znamená, že jej lze spustit pouze na jeho konkrétní procesor. Haldy je vytvořen pro každý podproces GC.
- Platí pouze pro uvolnění paměti serveru.
- Výchozí: Spřažení podprocesů uvolňování paměti`false`s procesory ( ).

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false`- afinitizovat<br/>`true`- nesoužejte | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCNoAffinitize` | `0`- afinitizovat<br/>`1`- nesoužejte | .NET Core 3.0 |
| **app.config pro rozhraní .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`- afinitizovat<br/>`true`- nesoužejte | .NET Framework 4.6.2 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit

- Určuje maximální velikost potvrzení v bajtech pro hromadu GC a účetnictví gc.
- Toto nastavení platí pouze pro 64bitové počítače.
- Výchozí hodnota, která platí pouze v určitých případech, je větší 20 MB nebo 75 % limitu paměti v kontejneru. Výchozí hodnota se použije v případě, že:

  - Proces je spuštěn uvnitř kontejneru, který má zadaný limit paměti.
  - [System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) není nastavena.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimit` | *desítková hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapHardLimit` | *šestnáctková hodnota* | .NET Core 3.0 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu. Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu. Chcete-li například zadat pevný limit haldy 200 mebibytes (MiB), hodnoty by 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Určuje povolené využití haldy GC jako procento celkové fyzické paměti.
- Pokud [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) je také nastavena, toto nastavení je ignorována.
- Toto nastavení platí pouze pro 64bitové počítače.
- Pokud je proces spuštěn uvnitř kontejneru, který má zadaný limit paměti, procento se vypočítá jako procento tohoto limitu paměti.
- Výchozí hodnota, která platí pouze v určitých případech, je menší 20 MB nebo 75 % limitu paměti v kontejneru. Výchozí hodnota se použije v případě, že:

  - Proces je spuštěn uvnitř kontejneru, který má zadaný limit paměti.
  - [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) není nastaven.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPercent` | *desítková hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapHardLimitPercent` | *šestnáctková hodnota* | .NET Core 3.0 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu. Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu. Chcete-li například omezit využití haldy na 30 %, hodnoty by byly 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System.GC.RetainVM/COMPlus_GCRetainVM

- Konfiguruje, zda segmenty, které mají být odstraněny jsou uvedeny do pohotovostního seznamu pro budoucí použití nebo jsou uvolněny zpět do operačního systému (OS).
- Výchozí: Uvolnění segmentů zpět do`false`operačního systému ( ).

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false`- uvolnění do OS<br/>`true`- v pohotovostním režimu | .NET Jádro 1.0 |
| **MSBuild, vlastnost** | `RetainVMGarbageCollection` | `false`- uvolnění do OS<br/>`true`- v pohotovostním režimu | .NET Jádro 1.0 |
| **Proměnná prostředí** | `COMPlus_GCRetainVM` | `0`- uvolnění do OS<br/>`1`- v pohotovostním režimu | .NET Jádro 1.0 |

### <a name="examples"></a>Příklady

*soubor runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

Soubor projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>Velké stránky

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Určuje, zda mají být velké stránky použity při nastavení pevného limitu haldy.
- Výchozí: Zakázáno (`0`).
- Toto je experimentální prostředí.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | – | – | – |
| **Proměnná prostředí** | `COMPlus_GCLargePages` | `0`- zakázáno<br/>`1`- povoleno | .NET Core 3.0 |

## <a name="large-objects"></a>Velké objekty

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Konfiguruje podporu systému uvolňování paměti na 64bitových platformách pro pole větší než 2 gigabajty (GB) v celkové velikosti.
- Výchozí hodnota:`1`Povoleno ( ).
- Tato možnost může být v budoucí verzi rozhraní .NET zastaralá.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | – | – | – |
| **Proměnná prostředí** | `COMPlus_gcAllowVeryLargeObjects` | `1`- povoleno<br/> `0`- zakázáno | .NET Jádro 1.0 |
| **app.config pro rozhraní .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`- povoleno<br/> `0`- zakázáno | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Prahová hodnota haldy velkého objektu

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System.GC.LOHPrahová hodnota/COMPlus_GCLOHThreshold

- Určuje velikost prahu v bajtů, která způsobí, že objekty přejít na haldy velkého objektu (LOH).
- Výchozí prahová hodnota je 85 000 bajtů.
- Zadaná hodnota musí být větší než výchozí prahová hodnota.

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | *desítková hodnota* | .NET Jádro 1.0 |
| **Proměnná prostředí** | `COMPlus_GCLOHThreshold` | *šestnáctková hodnota* | .NET Jádro 1.0 |
| **app.config pro rozhraní .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *desítková hodnota* |  .NET Framework 4.8 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> Pokud nastavujete tuto možnost v *souboru runtimeconfig.json*, zadejte desetinnou hodnotu. Pokud nastavujete volbu jako proměnnou prostředí, zadejte šestnáctkovou hodnotu. Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.

## <a name="standalone-gc"></a>Samostatný GC

### <a name="complus_gcname"></a>COMPlus_GCName

- Určuje cestu ke knihovně obsahující systém uvolňování paměti, který má za můe být načíst.
- Další informace naleznete [v tématu Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Název nastavení | Hodnoty | Zavedená verze |
| - | - | - | - |
| **runtimeconfig.json** | – | – | – |
| **Proměnná prostředí** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
