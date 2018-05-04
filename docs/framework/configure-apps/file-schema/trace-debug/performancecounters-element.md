---
title: '&lt;čítače výkonu&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cb4af08095c14c0c748a79f53104d8454d3dcd47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltperformancecountersgt-element"></a>&lt;čítače výkonu&gt; – Element
Určuje velikost globální paměť sdíleny čítače výkonu.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<čítače výkonu >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|filemappingsize|Požadovaný atribut.<br /><br /> Určuje velikost v bajtech globální paměť sdíleny čítače výkonu. Výchozí hodnota je 524288.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Čítače výkonu pomocí souboru mapované paměti nebo sdílené paměti, k vydávání dat výkonu.  Velikost sdílené paměti určuje, kolik instancí lze najednou.  Existují dva typy sdílené paměti: globální sdílené paměti a samostatné sdílené paměti.  Všechny kategorie čítače výkonu nainstalované rozhraní .NET Framework verze 1.0 nebo 1.1 používá globální sdílené paměti.  Kategorie čítače výkonu nainstalované s rozhraním .NET Framework verze 2.0 pomocí každé kategorie čítače výkonu má svou vlastní paměti samostatné sdílené paměti.  
  
 Velikost globální sdílené paměti lze nastavit pouze s konfiguračním souborem.  Výchozí velikost je kolik se 524,288, maximální velikost je 33,554,432 bajtů a minimální velikost je 32 768 bajtů.  Vzhledem k tomu, že globální sdílené paměti sdílí všechny procesy a kategorií, určuje první creator velikost.  Pokud definujete velikost v konfiguračním souboru aplikace, této velikosti se používá pouze pokud je první aplikaci, která způsobuje čítače výkonu pro spuštění aplikace.  Proto na správné místo k určení `filemappingsize` hodnota je souboru Machine.config.  Nelze uvolnit paměti v globální sdílené paměti podle jednotlivé čítače, takže nakonec vyčerpá globální sdílené paměti. Pokud jsou vytvořené velký počet instancí čítače výkonu s různými názvy.  
  
 Pro velikost samostatné sdílené paměti, klíče v registru hodnotu DWORD FileMappingSize HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<název kategorie >* \Performance odkazuje nejprve následovaný hodnota zadaná pro globální sdílené paměti v konfiguračním souboru. Pokud hodnota FileMappingSize neexistuje, pak velikost samostatné sdílené paměti je nastavena na čtvrtý jedna (1/4) globální nastavení v konfiguračním souboru.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
