---
title: '&lt;performanceCounters&gt; Element'
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
ms.openlocfilehash: a7b32f9cf797729aa0ca0d176b31732d06e73907
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701921"
---
# <a name="ltperformancecountersgt-element"></a>&lt;performanceCounters&gt; Element
Určuje velikost globální paměť sdílenou čítače výkonu.  
  
 \<Konfigurace >  
\<system.diagnostics>  
\<performanceCounters>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|filemappingsize|Požadovaný atribut.<br /><br /> Určuje velikost v bajtech, globální paměti sdílí čítače výkonu. Výchozí hodnota je 524288.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element části o konfiguraci technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Čítače výkonu pomocí souboru mapování paměti nebo sdílené paměti k vydávání dat výkonu.  Velikost sdílené paměti určuje, kolik instancí je možné najednou.  Existují dva typy sdílené paměti: globální sdílené paměti a samostatné sdílené paměti.  Všechny kategorie čítačů výkonu nainstalovaný v rozhraní .NET Framework verze 1.0 nebo 1.1 používá globální sdílenou paměť.  Kategorie čítače výkonu nainstalovaná s použitím rozhraní .NET Framework verze 2.0 pomocí samostatné sdílené paměti, s každou kategorii čítače výkonu má svůj vlastní paměti.  
  
 Velikost globální sdílené paměti lze nastavit pouze s konfiguračním souborem.  Výchozí velikost je 524,288 kolik, maximální velikost je 33,554,432 bajtů a minimální velikost je 32 768 bajtů.  Protože globální sdílené paměti se sdílí všemi procesy a kategorií, určuje první Tvůrce velikost.  Při definování velikost v konfiguračním souboru aplikace, tato velikost se používá pouze pokud je první aplikaci, která způsobí, že čítače výkonu ke spuštění aplikace.  Proto do správného umístění k určení `filemappingsize` hodnota je soubor Machine.config.  Nelze uvolnit paměť v globální sdílené paměti podle jednotlivých čítače, takže nakonec vyčerpá globální sdílené paměti, pokud se vytvoří velký počet instancí čítače výkonu s různými názvy.  
  
 Pro velikost samostatné sdílené paměti hodnotu DWORD FileMappingSize v registru klíč HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<název kategorie >* \Performance odkazuje nejprve za nímž následuje hodnota zadaná pro globální sdílené paměti v konfiguračním souboru. Pokud hodnota FileMappingSize neexistuje, je velikost samostatné sdílené paměti je nastavena na čtvrté jeden (1/4) globální nastavení v konfiguračním souboru.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
