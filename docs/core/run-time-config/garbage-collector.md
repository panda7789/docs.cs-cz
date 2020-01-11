---
title: Nastavení konfigurace pro kolektor paměti
description: Přečtěte si o nastaveních modulu runtime pro konfiguraci způsobu, jakým systém uvolňování paměti spravuje paměť pro aplikace .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900100"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Možnosti konfigurace běhu pro uvolňování paměti

Tato stránka obsahuje informace o nastavení uvolňování paměti (GC), které lze změnit v době běhu. Pokud se snažíte dosáhnout výkonu nejvyšší úrovně spuštěné aplikace, zvažte použití těchto nastavení. Nicméně výchozí hodnoty poskytují optimální výkon pro většinu aplikací v typických situacích.

Nastavení jsou uspořádána do skupin na této stránce. Nastavení v rámci jednotlivých skupin se běžně používají spolu s tím, aby se dosáhlo konkrétního výsledku.

> [!NOTE]
>
> - Tato nastavení je možné také dynamicky měnit v aplikaci jako spuštěnou, takže všechna nastavená nastavení běhu mohou být přepsána.
> - Některá nastavení, jako je [úroveň latence](../../standard/garbage-collection/latency.md), obvykle nastavuje jenom rozhraní API v době návrhu. Tato nastavení jsou vynechána na této stránce.
> - Pro hodnoty Number použijte Desítkový zápis pro nastavení v souboru *runtimeconfig. JSON* a hexadecimální zápis pro nastavení proměnné prostředí. U hexadecimálních hodnot je můžete zadat s předponou "0x" nebo bez ní.

## <a name="flavors-of-garbage-collection"></a>Charakter uvolňování paměti

Mezi tyto dva hlavní typy uvolnění paměti patří pracovní stanice GC a UVOLŇOVÁNí paměti serveru. Další informace o rozdílech mezi těmito dvěma informacemi najdete v tématu [základní informace o uvolňování paměti](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Podmnožiny uvolňování paměti jsou pozadí a nejsou souběžné.

Pro výběr charakteru uvolňování paměti použijte následující nastavení:

### <a name="systemgcservercomplus_gcserver"></a>System. GC. Server/COMPlus_gcServer

- Nakonfiguruje, jestli aplikace používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru.
- Výchozí: shromažďování paměti pracovní stanice (`false`).

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Server` | `false` – pracovní stanice<br/>`true` – Server | .NET Core 1,0 |
| **Proměnná prostředí** | `COMPlus_gcServer` | `0` – pracovní stanice<br/>`1` – Server | .NET Core 1,0 |
| **App. config pro .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false` – pracovní stanice<br/>`true` – Server |  |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System. GC. souběžné/COMPlus_gcConcurrent

- Konfiguruje, zda je povoleno uvolňování paměti na pozadí (souběžně).
- Výchozí: povoleno (`true`).
- Další informace najdete v tématu [kolekce uvolnění paměti na pozadí](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) a [uvolňování paměti serveru na pozadí](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Concurrent` | `true` – GC na pozadí<br/>`false` – nesouběžný GC | .NET Core 1,0 |
| **Proměnná prostředí** | `COMPlus_gcConcurrent` | `true` – GC na pozadí<br/>`false` – nesouběžný GC | .NET Core 1,0 |
| **App. config pro .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true` – GC na pozadí<br/>`false` – nesouběžný GC |  |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a>Správa využití prostředků

Pomocí nastavení popsaných v této části můžete spravovat paměť a využití procesoru systémem uvolňování paměti.

Další informace o některých těchto nastaveních najdete v tématu [střední deska mezi pracovní stanicí a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) položkou blogu GC serveru.

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System. GC. HeapCount/COMPlus_GCHeapCount

- Omezuje počet hald vytvořených systémem uvolňování paměti.
- Platí jenom pro shromažďování paměti serveru.
- Je-li povoleno spřažení procesoru uvolňování paměti, což je výchozí nastavení počet haldy spřáhne `n` haldy GC nebo vlákna na první `n` procesory. (K určení přesně těch procesorů, které mají spřažení, použijte nastavení maska spřažení nebo rozsahy spřažení.)
- Pokud je spřažení procesoru GC zakázané, toto nastavení omezuje počet hald GC.
- Další informace najdete v tématu [GCHeapCount – poznámky](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapCount` | *desetinná hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapCount` | *hexadecimální hodnota* | .NET Core 3.0 |
| **App. config pro .NET Framework** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *desetinná hodnota* | .NET Framework 4.6.2 |

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
> Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu. Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu. Například chcete-li omezit počet hald na 16, hodnoty by byly 16 pro soubor JSON a 0x10 nebo 10 pro proměnnou prostředí.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Určuje přesné procesory, které by měly používat vlákna uvolňování paměti.
- Pokud je spřažení procesorů zakázané nastavením `System.GC.NoAffinitize` na `true`, bude toto nastavení ignorováno.
- Platí jenom pro shromažďování paměti serveru.
- Hodnota je Bitová maska definující procesory, které jsou k dispozici pro daný proces. Například Desítková hodnota 1023 (nebo hexadecimální hodnota 0x3FF nebo 3FF, pokud používáte proměnnou prostředí) je 0011 1111 1111 v binárním zápisu. Určuje, že se má používat prvních 10 procesorů. Chcete-li zadat další 10 procesorů, tedy procesory 10-19, zadejte desítkovou hodnotu 1047552 (nebo hexadecimální hodnotu 0xFFC00 nebo FFC00), která je ekvivalentní binární hodnotě 1111 1111 1100 0000 0000.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapAffinitizeMask` | *desetinná hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapAffinitizeMask` | *hexadecimální hodnota* | .NET Core 3.0 |
| **App. config pro .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *desetinná hodnota* | .NET Framework 4.6.2 |

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

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Určuje seznam procesorů, které se mají použít pro vlákna uvolňování paměti.
- Toto nastavení je podobné jako u `System.GC.HeapAffinitizeMask`, s výjimkou případů, kdy je možné zadat více než 64 procesorů.
- V operačních systémech Windows použijte předponu čísla procesoru nebo rozsahu s odpovídající [skupinou procesorů](/windows/win32/procthread/processor-groups), například 0:1-10, 0:12, 1:50-52, 1:70.
- Pokud je spřažení procesorů zakázané nastavením `System.GC.NoAffinitize` na `true`, bude toto nastavení ignorováno.
- Platí jenom pro shromažďování paměti serveru.
- Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.GCHeapAffinitizeRanges` | Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.<br/>Příklad systému UNIX: "1-10, 12, 50-52, 70"<br/>Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapAffinitizeRanges` | Čárkami oddělený seznam čísel procesorů nebo rozsahů čísel procesorů.<br/>Příklad systému UNIX: "1-10, 12, 50-52, 70"<br/>Příklad Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |

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

- Nakonfiguruje, jestli systém uvolňování paměti používá [skupiny procesorů](/windows/win32/procthread/processor-groups) , nebo ne.

  Pokud má 64 počítač s Windows více skupin PROCESORů, to znamená, že existuje více než 64 procesorů, povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU. Systém uvolňování paměti používá všechny jádra k vytváření a vyrovnání hald.

- Platí pro uvolňování paměti serveru pouze v 64 operačních systémech Windows.
- Výchozí: zakázáno (`0`).
- Další informace najdete v tématu [zlepšení konfigurace procesoru pro GC na počítačích s > 64 procesory](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu s Maoni Stephens.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_GCCpuGroup` | `0` – zakázáno<br/>`1` – povoleno | .NET Core 1,0 |
| **App. config pro .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false` – zakázáno<br/>`true` – povoleno |  |

> [!NOTE]
> Chcete-li nakonfigurovat modul CLR (Common Language Runtime) pro distribuci vláken z fondu vláken napříč všemi skupinami PROCESORů, povolte možnost [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) . U aplikací .NET Core můžete tuto možnost povolit nastavením hodnoty proměnné prostředí `COMPlus_Thread_UseAllCpuGroups` na `1`.

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System. GC. NoAffinitize/COMPlus_GCNoAffinitize

- Určuje, jestli se mají *spřažení* vlákna uvolňování paměti pomocí procesorů. Aby spřažení vlákno GC, znamená to, že ho lze spustit pouze na jeho specifickém procesoru. Pro každé vlákno GC se vytvoří halda.
- Platí jenom pro shromažďování paměti serveru.
- Výchozí: spřažení vlákna uvolňování paměti pomocí procesorů (`false`).

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.NoAffinitize` | `false` – spřažení<br/>`true` – spřažení | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCNoAffinitize` | `0` – spřažení<br/>`1` – spřažení | .NET Core 3.0 |
| **App. config pro .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false` – spřažení<br/>`true` – spřažení | .NET Framework 4.6.2 |

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

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit

- Určuje maximální velikost potvrzení (v bajtech) pro haldu uvolňování paměti a účetnictví GC.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimit` | *desetinná hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapHardLimit` | *hexadecimální hodnota* | .NET Core 3.0 |

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
> Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu. Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu. Chcete-li například určit pevný limit haldy 200 mebibytes (MiB), hodnoty by byly 209715200 pro soubor JSON a 0xC800000 nebo C800000 pro proměnnou prostředí.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Určuje využití haldy GC jako procento z celkové paměti.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimitPercent` | *desetinná hodnota* | .NET Core 3.0 |
| **Proměnná prostředí** | `COMPlus_GCHeapHardLimitPercent` | *hexadecimální hodnota* | .NET Core 3.0 |

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
> Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu. Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu. Chcete-li například omezit využití haldy na 30%, budou hodnoty 30 pro soubor JSON a 0x1E nebo 1E pro proměnnou prostředí.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System. GC. RetainVM/COMPlus_GCRetainVM

- Určuje, zda jsou segmenty, které mají být odstraněny, umístěny do úsporného seznamu pro pozdější použití nebo jsou vydány zpět do operačního systému (OS).
- Výchozí: segmenty verze zpět do operačního systému (`false`).

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.RetainVM` | `false` – vydání na operační systém<br/>`true` – vložit do úsporného režimu| .NET Core 1,0 |
| **Proměnná prostředí** | `COMPlus_GCRetainVM` | `0` – vydání na operační systém<br/>`1` – vložit do úsporného režimu | .NET Core 1,0 |

Příklad:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a>Velké stránky

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Určuje, zda mají být při nastavení vynuceného limitu haldy použity velké stránky.
- Výchozí: zakázáno (`0`).
- Toto je experimentální nastavení.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_GCLargePages` | `0` – zakázáno<br/>`1` – povoleno | .NET Core 3.0 |

## <a name="large-objects"></a>Velké objekty

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Konfiguruje podporu uvolňování paměti na 64ech platforem pro pole, která jsou v celkové velikosti větší než 2 gigabajty (GB).
- Výchozí: povoleno (`1`).
- Tato možnost může být zastaralá v budoucí verzi .NET.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_gcAllowVeryLargeObjects` | `1` – povoleno<br/> `0` – zakázáno | .NET Core 1,0 |
| **App. config pro .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1` – povoleno<br/> `0` – zakázáno | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Prahová hodnota haldy velkých objektů

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System. GC. LOHThreshold/COMPlus_GCLOHThreshold

- Určuje velikost prahové hodnoty v bajtech, která způsobí, že objekty budou jít na haldu velkých objektů (LOH).
- Výchozí prahová hodnota je 85 000 bajtů.
- Hodnota, kterou zadáte, musí být větší než výchozí prahová hodnota.

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.LOHThreshold` | *desetinná hodnota* | .NET Core 1,0 |
| **Proměnná prostředí** | `COMPlus_GCLOHThreshold` | *hexadecimální hodnota* | .NET Core 1,0 |
| **App. config pro .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *desetinná hodnota* | .NET Framework 4,8 |

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
> Pokud nastavujete možnost v *runtimeconfig. JSON*, zadejte desítkovou hodnotu. Pokud nastavujete možnost jako proměnnou prostředí, zadejte hexadecimální hodnotu. Chcete-li například nastavit prahovou hodnotu 120 000 bajtů, budou hodnoty 120000 pro soubor JSON a 0x1D4C0 nebo 1D4C0 pro proměnnou prostředí.

## <a name="standalone-gc"></a>Samostatná GC

### <a name="complus_gcname"></a>COMPlus_GCName

- Určuje cestu k knihovně obsahující systém uvolňování paměti, který modul runtime zamýšlí načíst.
- Další informace najdete v tématu [Návrh zavaděče samostatného modulu GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Název nastavení | Hodnoty | Představená verze |
| - | - | - | - |
| **runtimeconfig. JSON** | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. | NEUŽÍVÁ SE. |
| **Proměnná prostředí** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
