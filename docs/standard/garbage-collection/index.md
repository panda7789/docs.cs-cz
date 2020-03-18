---
title: Kolekce paměti
ms.date: 03/30/2017
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
ms.openlocfilehash: 846df5ecb1e681e8d0440e627586a681bf071efa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160141"
---
# <a name="garbage-collection"></a>Kolekce paměti
. NET systém uvolňování paměti spravuje přidělení a uvolnění paměti pro vaši aplikaci. Při každém vytvoření nového objektu modul CLR přidělí objektu paměť ze spravované haldy. Dokud je ve spravované haldě k dispozici adresní prostor, modul runtime bude pokračovat v přidělování prostoru pro nové objekty. Paměť však není neomezená. Z důvodu získání paměti musí nakonec systém uvolňování paměti provést uvolnění paměti. Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení uvolnění paměti na základě způsobu přidělování paměti. Při uvolňování paměti systém ověřuje, zda objekty ve spravované haldě již nejsou používány aplikací, a provede nezbytné úkony k opětovnému získání paměti.  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Základy kolekce paměti](../../../docs/standard/garbage-collection/fundamentals.md)|Popisuje způsob, jakým funguje systém uvolňování paměti, jakým způsobem jsou objekty přidělovány na spravované haldě, a další základní pojmy.|  
|[Uvolnění paměti a výkon](../../../docs/standard/garbage-collection/performance.md)|Popisuje kontroly výkonu, které slouží k diagnostice problémů uvolňování paměti a výkonu.|  
|[Vyvolané kolekce](../../../docs/standard/garbage-collection/induced.md)|Popisuje způsob aktivace uvolňování paměti.|  
|[Latentní režimy](../../../docs/standard/garbage-collection/latency.md)|Popisuje režimy, které určují parametry systému uvolňování paměti.|  
|[Optimalizace pro sdílené hostování webů](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Popisuje způsob optimalizace uvolňování paměti na serverech, které jsou sdíleny několika malými weby.|  
|[Oznámení pro kolekci paměti](../../../docs/standard/garbage-collection/notifications.md)|Popisuje, jakým způsobem lze zjistit, kdy se blíží termín úplného uvolňování paměti a kdy bude uvolňování dokončeno.|  
|[Sledování prostředků domény aplikace](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Popisuje sledování využití procesoru a paměti doménou aplikace.|  
|[Slabé odkazy](../../../docs/standard/garbage-collection/weak-references.md)|Popisuje funkce, které systému uvolňování paměti umožňují získat paměť objektu a zároveň podporují přístup aplikace k danému objektu.|  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také

- [Vymazání nespravovaných prostředků](../../../docs/standard/garbage-collection/unmanaged.md)
