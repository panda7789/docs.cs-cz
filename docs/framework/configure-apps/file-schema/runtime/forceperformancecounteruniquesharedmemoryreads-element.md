---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e9073e48141bc6895d00c773c2d3d2cfeb260f6
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456457"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
Určuje, jestli má PerfCounter.dll CategoryOptions nastavení registru v rozhraní .NET Framework verze 1.1 aplikace k určení, jestli se má načíst data čítače výkonu ze sdílené paměti podle kategorií nebo globální paměti.  
  
 \<Konfigurace >  
\<modul runtime >  
\<forcePerformanceCounterUniqueSharedMemoryReads>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda PerfCounter.dll nastavení registru CategoryOptions používá k určení, jestli se má načíst data čítače výkonu ze sdílené paměti podle kategorií nebo globální paměti.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|PerfCounter.dll CategoryOptions nepoužívá výchozí nastavení je toto nastavení registru.|  
|`true`|PerfCounter.dll pomocí nastavení registru CategoryOptions.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Ve verzích rozhraní .NET Framework před [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], odpovídaly verzi PerfCounter.dll, který byl načten modul runtime, který byl načten v procesu. Pokud počítač měl i rozhraní .NET Framework verze 1.1 a [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] nainstalované, by aplikace rozhraní .NET Framework 1.1 načtení verze rozhraní .NET Framework 1.1 PerfCounter.dll. Od verze rozhraní .NET Framework 4, je nainstalovaná nejnovější verze PerfCounter.dll načten. To znamená, že aplikace rozhraní .NET Framework 1.1 načte verzi rozhraní .NET Framework 4 PerfCounter.dll pokud rozhraní .NET Framework 4 je nainstalován v počítači.  
  
 Od verze rozhraní .NET Framework 4, při využívání čítače výkonu, zkontroluje PerfCounter.dll CategoryOptions položka registru pro každého zprostředkovatele k určení, zda by měl číst ze sdílené paměti podle kategorií nebo globální sdílené paměti. Rozhraní .NET Framework 1.1 PerfCounter.dll nenačítá této položky registru, protože nebude vědět o sdílené paměti podle kategorií. vždy čte z globální sdílené paměti.  
  
 Z důvodu zpětné kompatibility PerfCounter.dll rozhraní .NET Framework 4 nekontroluje položku registru CategoryOptions při spuštění aplikace rozhraní .NET Framework 1.1. Jednoduše používá globální sdílené paměti, stejně jako PerfCounter.dll 1.1 rozhraní .NET Framework. Ale můžete dát pokyn PerfCounter.dll rozhraní .NET Framework 4 zkontrolovat nastavení registru tím, že `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.  
  
> [!NOTE]
>  Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` element nezaručuje, že se použije sdílené paměti podle kategorií. Nastavení povolit, aby `true` pouze způsobí, že PerfCounter.dll odkazovat CategoryOptions nastavení registru. Výchozí nastavení pro CategoryOptions je použití sdílené paměti podle kategorií. Můžete však změnit CategoryOptions k označení, že má být použit globální sdílené paměti.  
  
 Klíč registru, který obsahuje nastavení CategoryOptions je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. Ve výchozím nastavení CategoryOptions nastavená na 3, který dává pokyn PerfCounter.dll použití sdílené paměti podle kategorií. Pokud CategoryOptions je nastavena na hodnotu 0, PerfCounter.dll používá globální sdílenou paměť. Instance data bude znovu použita, pouze v případě, že je název instance vytváří je stejný jako instance používána znovu. Všechny verze bude moci zapisovat do kategorie. Pokud CategoryOptions je nastavená na 1, se používá globální sdílenou paměť, ale instance data můžete opětovně název kategorie je stejnou délku jako kategorie používána znovu.  
  
 Nastavení 0 a 1 může vést k nevracení paměti a naplnění nahoru paměti čítače výkonu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že by měly odkazovat PerfCounter.dll položku registru CategoryOptions zjistěte, zda by měl použít sdílené paměti podle kategorií.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
