---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154137"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryRe> element
Určuje, zda program PerfCounter.dll používá nastavení registru CategoryOptions v aplikaci rozhraní .NET Framework verze 1.1 k určení, zda má být načtena data čítače výkonu ze sdílené paměti specifické pro danou kategorii nebo globální paměti.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryRe>**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Označuje, zda služba PerfCounter.dll používá nastavení registru CategoryOptions k určení, zda se mají načíst data čítače výkonu ze sdílené paměti specifické pro danou kategorii nebo globální paměti.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Soubor PerfCounter.dll nepoužívá nastavení registru CategoryOptions Toto je výchozí nastavení.|  
|`true`|Soubor PerfCounter.dll používá nastavení registru CategoryOptions.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Ve verzích rozhraní .NET Framework před rozhraním .NET Framework 4 odpovídala verze souboru PerfCounter.dll, která byla načtena, době runtime načtené v procesu. Pokud by byl v počítači nainstalována rozhraní .NET Framework verze 1.1 i rozhraní .NET Framework 2.0, načetla by aplikace rozhraní .NET Framework 1.1 verzi souboru PerfCounter.dll. Počínaje rozhraním .NET Framework 4 je načtena nejnovější nainstalovaná verze souboru PerfCounter.dll. To znamená, že aplikace rozhraní .NET Framework 1.1 načte verzi souboru PerfCounter.dll v rámci rozhraní .NET Framework 4, pokud je v počítači nainstalována rozhraní .NET Framework 4.  
  
 Počínaje rozhraním .NET Framework 4 při využívání čítačů výkonu perfCounter.dll zkontroluje položku registru CategoryOptions pro každého zprostředkovatele a určí, zda má číst ze sdílené paměti specifické pro kategorii nebo globální sdílené paměti. Rozhraní .NET Framework 1.1 PerfCounter.dll nečte tuto položku registru, protože si není vědoma sdílené paměti specifické pro kategorii; vždy čte z globální sdílené paměti.  
  
 Z důvodu zpětné kompatibility nekontroluje soubor .NET Framework 4 PerfCounter.dll položku registru CategoryOptions při spuštění v aplikaci rozhraní .NET Framework 1.1. Jednoduše používá globální sdílenou paměť, stejně jako rozhraní .NET Framework 1.1 PerfCounter.dll. Můžete však dát pokyn rozhraní .NET Framework 4 PerfCounter.dll `<forcePerformanceCounterUniqueSharedMemoryReads>` ke kontrole nastavení registru povolením prvku.  
  
> [!NOTE]
> Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` prvku nezaručuje, že bude použita sdílená paměť specifická pro kategorii. Nastavení povoleno `true` pouze způsobí, že soubor PerfCounter.dll odkazuje na nastavení registru CategoryOptions. Výchozí nastavení pro CategoryOptions je použití sdílené paměti specifické pro kategorii; můžete však změnit CategoryOptions označující, že by měla být použita globální sdílená paměť.  
  
 Klíč registru, který obsahuje nastavení CategoryOptions, je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance. Ve výchozím nastavení categoryOptions je nastavena na 3, který pokyn PerfCounter.dll používat kategorii specifické sdílené paměti. Pokud CategoryOptions je nastavena na 0, PerfCounter.dll používá globální sdílené paměti. Data instance budou znovu použita pouze v případě, že název vytvářené instance je shodný s opětovně používanou instancí. Všechny verze budou moci zapisovat do kategorie. Pokud CategoryOptions je nastavena na 1, globální sdílené paměti se používá, ale data instance lze znovu použít, pokud název kategorie je stejná délka jako kategorie opakovaně.  
  
 Nastavení 0 a 1 může vést k nevracení paměti a vyplnění paměti čítače výkonu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že PerfCounter.dll by měl odkazovat na položku registru CategoryOptions k určení, zda by měl používat sdílené paměti specifické pro kategorii.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
