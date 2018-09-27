---
title: Trasování a ladění schématu nastavení
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9927ad0e853577abb19750d54ba9e852a4e7ec51
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397943"
---
# <a name="trace-and-debug-settings-schema"></a>Trasování a ladění schématu nastavení
Nastavení trasování a ladění zadejte naslouchací procesy trasování, které shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.  
  
 Následující tabulka popisuje funkce každého prvku nastavení ladění a trasování.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Přidá naslouchací proces pro `Listeners` kolekci pro zdroj trasování.|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Přidá naslouchací proces pro `Listeners` kolekce.|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|Přidá naslouchací proces pro `sharedListeners` kolekce.|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|Určuje úroveň, kde je nastaven přepínač trasování.|  
|[\<vyhodnocení >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Určuje, jestli se má zobrazit okno se zprávou, když zavoláte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zpráv do.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Vymaže `Listeners` kolekci pro zdroj trasování.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Vymaže `Listeners` kolekce pro trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekce pro trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchacího procesu v `sharedListeners` kolekce.|  
|[\<naslouchací procesy >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Určuje naslouchací procesy pro `Listeners` kolekci pro zdroj trasování.|  
|[\<naslouchací procesy >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Určuje naslouchací procesy pro `Listeners` kolekce pro trasování.|  
|[\<čítače výkonu >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Určuje velikost globální paměť sdílenou čítače výkonu.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Odebere z naslouchacího procesu `Listeners` kolekce pro trasování.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Odebere z naslouchacího procesu `Listeners` kolekci pro zdroj trasování.|  
|[\<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Obsahuje moduly pro naslouchání, které všechny zdroje nebo trasování – element může odkazovat.|  
|[\<zdroje >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.|  
|[\<zdroj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|Určuje zdroj trasování, který iniciuje trasovací zprávy.|  
|[\<přepínače >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|Obsahuje přepínače trasování a úrovně, ve kterém jsou nastavené přepínačů trasování.|  
|[\<System.Diagnostics >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|[\<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
