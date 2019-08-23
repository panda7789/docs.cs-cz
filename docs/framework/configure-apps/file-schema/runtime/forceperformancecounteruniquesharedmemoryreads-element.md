---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29fbe951b955c97e39ebaf80885729a45c1a3fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927399"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
Určuje, jestli dokončení PerfCounter. dll používá nastavení registru CategoryOptions v aplikaci .NET Framework verze 1,1 k určení toho, jestli se mají načíst data čítače výkonu z sdílené paměti nebo globální paměti specifické pro danou kategorii.  
  
 \<> Konfigurace  
\<> modulu runtime  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda dokončení PerfCounter. dll používá nastavení registru CategoryOptions k určení, zda mají být načtena data čítače výkonu z sdílené paměti specifické pro kategorii nebo z globální paměti.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Dokončení PerfCounter. dll nepoužívá nastavení registru CategoryOptions, což je výchozí nastavení.|  
|`true`|Dokončení PerfCounter. dll používá nastavení registru CategoryOptions.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Ve verzích .NET Framework před .NET Framework 4 je nahraná verze dokončení PerfCounter. dll odpovídající modulu runtime, který byl načten do procesu. Pokud má počítač nainstalovanou verzi .NET Framework 1,1 i .NET Framework 2,0, aplikace .NET Framework 1,1 by načetla .NET Framework 1,1 verze souboru dokončení PerfCounter. dll. Počínaje .NET Framework 4 je načtena nejnovější nainstalovaná verze dokončení PerfCounter. dll. To znamená, že aplikace .NET Framework 1,1 načte .NET Framework 4 verzi dokončení PerfCounter. dll, pokud je v počítači nainstalováno .NET Framework 4.  
  
 Počínaje .NET Framework 4 při zpracování čítačů výkonu zkontroluje dokončení PerfCounter. dll položku registru CategoryOptions pro každého poskytovatele a určí, jestli se má číst z sdílené paměti specifické pro kategorii nebo globální sdílené paměti. .NET Framework 1,1 dokončení PerfCounter. dll nepřečte položku registru, protože nemá informace o sdílené paměti specifické pro danou kategorii; vždy se čte z globální sdílené paměti.  
  
 Z důvodu zpětné kompatibility .NET Framework 4 dokončení PerfCounter. dll při spuštění v aplikaci .NET Framework 1,1 nekontroluje položku registru CategoryOptions. Jednoduše používá globální sdílenou paměť, stejně jako .NET Framework 1,1 dokončení PerfCounter. dll. Můžete však dát pokyn .NET Framework 4 dokončení PerfCounter. dll pro kontrolu nastavení registru povolením `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.  
  
> [!NOTE]
> `<forcePerformanceCounterUniqueSharedMemoryReads>` Povolení prvku nezaručuje, že bude použita sdílená paměť specifická pro danou kategorii. Nastavení povoleno `true` pouze způsobí, že dokončení PerfCounter. dll odkazuje na nastavení registru CategoryOptions. Výchozím nastavením pro CategoryOptions je použít sdílenou paměť specifickou pro kategorii; CategoryOptions však můžete změnit tak, aby označovala, že by měla být použita globální sdílená paměť.  
  
 Klíč registru obsahující nastavení CategoryOptions je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< CategoryName \Performance.\> Ve výchozím nastavení je CategoryOptions nastaveno na hodnotu 3, což dává dokončení PerfCounter. dll pokyn, aby používala sdílenou paměť specifickou pro kategorii. Pokud je CategoryOptions nastavené na 0, dokončení PerfCounter. dll používá globální sdílenou paměť. Data instance se znovu použijí pouze v případě, že je název vytvářené instance stejný jako instance, která se právě používá. Všechny verze budou moci zapisovat do kategorie. Pokud je CategoryOptions nastaveno na hodnotu 1, je použita globální sdílená paměť, ale data instance lze znovu použít, pokud má název kategorie stejnou délku jako znovu používané kategorie.  
  
 Nastavení 0 a 1 mohou vést k nevrácení paměti a vyplňování paměti čítače výkonu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že dokončení PerfCounter. dll má odkazovat na položku registru CategoryOptions, aby určila, zda má používat sdílenou paměť specifickou pro kategorii.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
