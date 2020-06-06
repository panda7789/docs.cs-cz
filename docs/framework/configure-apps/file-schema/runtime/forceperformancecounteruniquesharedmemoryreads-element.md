---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154137"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>Element \<forcePerformanceCounterUniqueSharedMemoryReads>
Určuje, jestli dokončení PerfCounter. dll používá nastavení registru CategoryOptions v aplikaci .NET Framework verze 1,1 k určení toho, jestli se mají načíst data čítače výkonu z sdílené paměti nebo globální paměti specifické pro danou kategorii.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
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
  
|Hodnota|Description|  
|-----------|-----------------|  
|`false`|Dokončení PerfCounter. dll nepoužívá nastavení registru CategoryOptions, což je výchozí nastavení.|  
|`true`|Dokončení PerfCounter. dll používá nastavení registru CategoryOptions.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Ve verzích .NET Framework před .NET Framework 4 je nahraná verze dokončení PerfCounter. dll odpovídající modulu runtime, který byl načten do procesu. Pokud má počítač nainstalovanou verzi .NET Framework 1,1 i .NET Framework 2,0, aplikace .NET Framework 1,1 by načetla .NET Framework 1,1 verze souboru dokončení PerfCounter. dll. Počínaje .NET Framework 4 je načtena nejnovější nainstalovaná verze dokončení PerfCounter. dll. To znamená, že aplikace .NET Framework 1,1 načte .NET Framework 4 verzi dokončení PerfCounter. dll, pokud je v počítači nainstalováno .NET Framework 4.  
  
 Počínaje .NET Framework 4 při zpracování čítačů výkonu zkontroluje dokončení PerfCounter. dll položku registru CategoryOptions pro každého poskytovatele a určí, jestli se má číst z sdílené paměti specifické pro kategorii nebo globální sdílené paměti. .NET Framework 1,1 dokončení PerfCounter. dll nepřečte položku registru, protože nemá informace o sdílené paměti specifické pro danou kategorii; vždy se čte z globální sdílené paměti.  
  
 Z důvodu zpětné kompatibility .NET Framework 4 dokončení PerfCounter. dll při spuštění v aplikaci .NET Framework 1,1 nekontroluje položku registru CategoryOptions. Jednoduše používá globální sdílenou paměť, stejně jako .NET Framework 1,1 dokončení PerfCounter. dll. Můžete však dát pokyn .NET Framework 4 dokončení PerfCounter. dll pro kontrolu nastavení registru povolením `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.  
  
> [!NOTE]
> Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` prvku nezaručuje, že bude použita sdílená paměť specifická pro danou kategorii. Nastavení povoleno `true` pouze způsobí, že dokončení PerfCounter. dll odkazuje na nastavení registru CategoryOptions. Výchozím nastavením pro CategoryOptions je použít sdílenou paměť specifickou pro kategorii; CategoryOptions však můžete změnit tak, aby označovala, že by měla být použita globální sdílená paměť.  
  
 Klíč registru, který obsahuje nastavení CategoryOptions, je HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<NázevKategorie \> \Performance. Ve výchozím nastavení je CategoryOptions nastaveno na hodnotu 3, což dává dokončení PerfCounter. dll pokyn, aby používala sdílenou paměť specifickou pro kategorii. Pokud je CategoryOptions nastavené na 0, dokončení PerfCounter. dll používá globální sdílenou paměť. Data instance se znovu použijí pouze v případě, že je název vytvářené instance stejný jako instance, která se právě používá. Všechny verze budou moci zapisovat do kategorie. Pokud je CategoryOptions nastaveno na hodnotu 1, je použita globální sdílená paměť, ale data instance lze znovu použít, pokud má název kategorie stejnou délku jako znovu používané kategorie.  
  
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
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
