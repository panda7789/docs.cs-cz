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
ms.openlocfilehash: 79054ba450dcab1a18562aaadd71b9171896c1e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177434"
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
|[\<assert>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|Určuje, jestli se má zobrazit okno se zprávou, když zavoláte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zpráv do.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Vymaže `Listeners` kolekci pro zdroj trasování.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Vymaže `Listeners` kolekce pro trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekce pro trasování.|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchacího procesu v `sharedListeners` kolekce.|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Určuje naslouchací procesy pro `Listeners` kolekci pro zdroj trasování.|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Určuje naslouchací procesy pro `Listeners` kolekce pro trasování.|  
|[\<performanceCounters>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|Určuje velikost globální paměť sdílenou čítače výkonu.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Odebere z naslouchacího procesu `Listeners` kolekce pro trasování.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Odebere z naslouchacího procesu `Listeners` kolekci pro zdroj trasování.|  
|[\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|Obsahuje moduly pro naslouchání, které všechny zdroje nebo trasování – element může odkazovat.|  
|[\<sources>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.|  
|[\<zdroj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|Určuje zdroj trasování, který iniciuje trasovací zprávy.|  
|[\<switches>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|Obsahuje přepínače trasování a úrovně, ve kterém jsou nastavené přepínačů trasování.|  
|[\<system.diagnostics>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|[\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
