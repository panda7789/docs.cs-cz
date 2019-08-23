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
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927123"
---
# <a name="trace-and-debug-settings-schema"></a>Trasování a ladění schématu nastavení
Nastavení trasování a ladění určují naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.  
  
 Následující tabulka popisuje funkci každého prvku nastavení trasování a ladění.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.|  
|[\<add>](add-element-for-listeners-for-trace.md)|Přidá naslouchací proces do `Listeners` kolekce.|  
|[\<add>](add-element-for-sharedlisteners.md)|Přidá naslouchací proces do `sharedListeners` kolekce.|  
|[\<add>](add-element-for-switches.md)|Určuje úroveň, kde je nastaven přepínač trasování.|  
|[\<assert>](assert-element.md)|Určuje, zda se má při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody zobrazit okno se zprávou. určuje také název souboru, do kterého budou zapsány zprávy.|  
|[\<clear>](clear-element-for-listeners-for-source.md)|`Listeners` Vymaže kolekci zdroje trasování.|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|`Listeners` Vymaže kolekci pro Trace.|  
|[\<Filtrovat >](filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.|  
|[\<Filtrovat >](filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro trasování.|  
|[\<Filtrovat >](filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchacího procesu v `sharedListeners` kolekci.|  
|[\<> naslouchací proces](listeners-element-for-source.md)|Určuje naslouchací procesy pro `Listeners` kolekci pro zdroj trasování.|  
|[\<> naslouchací proces](listeners-element-for-trace.md)|Určuje naslouchací procesy pro `Listeners` kolekci pro trasování.|  
|[\<performanceCounters>](performancecounters-element.md)|Určuje velikost globální paměti sdílené čítači výkonu.|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|Odebere naslouchací proces z `Listeners` kolekce pro trasování.|  
|[\<remove>](remove-element-for-listeners-for-source.md)|Odebere naslouchací proces z `Listeners` kolekce pro zdroj trasování.|  
|[\<> sharedListeners](sharedlisteners-element.md)|Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.|  
|[\<> zdrojů](sources-element.md)|Obsahuje zdroje trasování, které spouštějí trasovací zprávy.|  
|[\<> zdroje](source-element.md)|Určuje zdroj trasování, který inicializuje trasovací zprávy.|  
|[\<switches>](switches-element.md)|Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.|  
|[\<system.diagnostics>](system-diagnostics-element.md)|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|[\<trace>](trace-element.md)|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [Schéma konfiguračního souboru](../index.md)
