---
title: Uvolňování paměti .NET
description: Přečtěte si o uvolňování paměti v .NET. Systém uvolňování paměti .NET spravuje přidělování a uvolňování paměti pro vaši aplikaci.
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662482"
---
# <a name="garbage-collection"></a>Uvolnění paměti

. Systém uvolňování paměti sítě spravuje přidělování a uvolňování paměti pro vaši aplikaci. Při každém vytvoření nového objektu modul CLR přidělí objektu paměť ze spravované haldy. Dokud je ve spravované haldě k dispozici adresní prostor, modul runtime bude pokračovat v přidělování prostoru pro nové objekty. Paměť však není neomezená. Z důvodu získání paměti musí nakonec systém uvolňování paměti provést uvolnění paměti. Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení uvolnění paměti na základě způsobu přidělování paměti. Při uvolňování paměti systém ověřuje, zda objekty ve spravované haldě již nejsou používány aplikací, a provede nezbytné úkony k opětovnému získání paměti.  
  
## <a name="in-this-section"></a>V této části
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Základní informace o uvolňování paměti](fundamentals.md)|Popisuje způsob, jakým funguje systém uvolňování paměti, jakým způsobem jsou objekty přidělovány na spravované haldě, a další základní pojmy.|  
|[Uvolnění paměti pracovní stanice a serveru](workstation-server-gc.md)|Popisuje rozdíly mezi uvolňováním paměti pracovní stanice pro klientské aplikace a shromažďování paměti serveru pro serverové aplikace.|
|[Uvolňování paměti na pozadí](background-gc.md)|Popisuje shromažďování paměti na pozadí, což je kolekce objektů generace 0 a 1, zatímco probíhá shromažďování 2. generace.|
|[Halda pro velké objekty](large-object-heap.md)|Popisuje haldu rozsáhlých objektů (LOH) a jak velké objekty jsou uvolněny z paměti.|
|[Uvolňování paměti a výkon](performance.md)|Popisuje kontroly výkonu, které slouží k diagnostice problémů uvolňování paměti a výkonu.|  
|[Vyvolané kolekce](induced.md)|Popisuje způsob aktivace uvolňování paměti.|  
|[Režimy latence](latency.md)|Popisuje režimy, které určují parametry systému uvolňování paměti.|  
|[Optimalizace pro sdílené hostování webů](optimization-for-shared-web-hosting.md)|Popisuje způsob optimalizace uvolňování paměti na serverech, které jsou sdíleny několika malými weby.|  
|[Oznámení o uvolňování paměti](notifications.md)|Popisuje, jakým způsobem lze zjistit, kdy se blíží termín úplného uvolňování paměti a kdy bude uvolňování dokončeno.|  
|[Sledování prostředků domény aplikace](app-domain-resource-monitoring.md)|Popisuje sledování využití procesoru a paměti doménou aplikace.|  
|[Slabé odkazy](weak-references.md)|Popisuje funkce, které systému uvolňování paměti umožňují získat paměť objektu a zároveň podporují přístup aplikace k danému objektu.|  
  
## <a name="reference"></a>Referenční informace

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také

- [Vyčištění nespravovaných prostředků](unmanaged.md)
