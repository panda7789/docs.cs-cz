---
title: "&lt;forceperformancecounteruniquesharedmemoryreads –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c90799ed2db061e8f42cde79804789eb8d2da0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a>&lt;forceperformancecounteruniquesharedmemoryreads –&gt; – Element
Určuje, zda PerfCounter.dll používá nastavení registru CategoryOptions v rozhraní .NET Framework verze 1.1 aplikaci a určí, jestli se načíst data čítače výkonu z kategorie sdílené paměti nebo globální paměť.  
  
 \<Konfigurace >  
\<modul runtime >  
\<forceperformancecounteruniquesharedmemoryreads – >  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Označuje, zda PerfCounter.dll používá nastavení registru CategoryOptions a určí, jestli se načíst data čítače výkonu z kategorie sdílené paměti nebo globální paměť.|  
  
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
 Ve verzích rozhraní .NET Framework, než [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], verze PerfCounter.dll, která byla načtena odpovídaly modul runtime, která byla načtena v procesu. Pokud počítač měl i rozhraní .NET Framework verze 1.1 a [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] nainstalovaná, by aplikace rozhraní .NET Framework 1.1 načtení verze rozhraní .NET Framework 1.1 PerfCounter.dll. Od verze [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], je nainstalovaná nejnovější verze PerfCounter.dll načtena. To znamená, že se načte aplikaci .NET Framework 1.1 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] verzi PerfCounter.dll pokud [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] je nainstalován v počítači.  
  
 Od verze [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], při využívání čítače výkonu, PerfCounter.dll ověří položku registru CategoryOptions pro každého zprostředkovatele k určení, jestli má číst ze sdílené paměti podle kategorií nebo globální sdílené paměti. PerfCounter.dll rozhraní .NET Framework 1.1 nepodporuje čtení této položky registru, protože nemá žádné informace o sdílené paměti podle kategorií; vždy čte z globální sdílené paměti.  
  
 Z důvodu zpětné kompatibility [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll nekontroluje položku registru CategoryOptions při spuštění v aplikaci .NET Framework 1.1. Používá jednoduše globální sdílené paměti, stejně jako PerfCounter.dll rozhraní .NET Framework 1.1. Ale můžete určit, aby [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll zkontrolovat nastavení registru povolením `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.  
  
> [!NOTE]
>  Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` element nezaručí, že se použije sdílené paměti podle kategorií. Povoleným nastavením `true` pouze způsobí, že PerfCounter.dll tak, aby odkazovaly CategoryOptions nastavení registru. Výchozí nastavení pro CategoryOptions se má používat sdílené paměti podle kategorií; Můžete však změnit CategoryOptions indikující, že má být použita globální sdílené paměti.  
  
 Klíč registru, který obsahuje nastavení CategoryOptions je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. Ve výchozím nastavení CategoryOptions je hodnotu 3, která dá pokyn PerfCounter.dll používat sdílené paměti podle kategorií. Pokud CategoryOptions nastavena na hodnotu 0, používá PerfCounter.dll globální sdílené paměti. Instance data bude znovu použita, pouze v případě, že název instance, vytváření je stejný jako instance opakovaně používáno. Všechny verze budou moci zapsat do kategorie. Pokud CategoryOptions nastavena na hodnotu 1, se používá globální sdílené paměti, ale instance data můžete znovu použít, pokud název kategorie je stejnou délku jako kategorie opakovaně používáno.  
  
 Nastavení hodnoty 0 a 1 může vést k nevracení paměti a naplnění až paměti čítače výkonu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že PerfCounter.dll by měla odkazovat položku registru CategoryOptions k určení, zda se má použít sdílené paměti podle kategorií.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
