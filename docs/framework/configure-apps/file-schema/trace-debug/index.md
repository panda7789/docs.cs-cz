---
title: "Trasování a ladění schématu nastavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: e6d9e5ca97e4d5940dd9de3f3ffbd4db4183196c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="trace-and-debug-settings-schema"></a>Trasování a ladění schématu nastavení
Nastavení trasování a ladění zadejte naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.  
  
 Následující tabulka popisuje funkci jednotlivých prvků nastavení trasování a ladění.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Přidá naslouchací proces a `Listeners` kolekce zdroje trasování.|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Přidá naslouchací proces a `Listeners` kolekce.|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|Přidá naslouchací proces a `sharedListeners` kolekce.|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|Určuje úroveň, kde je nastaven na přepínač trasování.|  
|[\<Assert – >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Určuje, jestli se má zobrazit okno se zprávou při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zprávy.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Vymaže `Listeners` kolekce zdroje trasování.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Vymaže `Listeners` kolekce pro trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchací proces ve `Listeners` kolekce zdroje trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr do naslouchací proces ve `Listeners` kolekce pro trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchací proces ve `sharedListeners` kolekce.|  
|[\<moduly pro naslouchání >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Určuje naslouchací procesy pro `Listeners` kolekce zdroje trasování.|  
|[\<moduly pro naslouchání >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Určuje naslouchací procesy pro `Listeners` kolekce pro trasování.|  
|[\<čítače výkonu >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Určuje velikost globální paměť sdíleny čítače výkonu.|  
|[\<Odebrat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Odebere naslouchací proces z `Listeners` kolekce pro trasování.|  
|[\<Odebrat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Odebere naslouchací proces z `Listeners` kolekce zdroje trasování.|  
|[\<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Obsahuje naslouchací procesy, které může odkazovat všechny zdroje nebo element trasování.|  
|[\<zdroje >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|Obsahuje trasování zdrojů, které zahájí trasování zpráv.|  
|[\<zdroj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|Určuje zdroj trasování, který iniciuje trasování zpráv.|  
|[\<přepínače >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|Obsahuje trasování – přepínače a úroveň, kde jsou nastaveny trasování – přepínače.|  
|[\<System.Diagnostics >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
|[\<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
