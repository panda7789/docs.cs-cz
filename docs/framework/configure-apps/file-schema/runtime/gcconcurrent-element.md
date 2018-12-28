---
title: '&lt;gcConcurrent&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fa802ab9d1025bd130a6265b50050284aae0150
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612384"
---
# <a name="ltgcconcurrentgt-element"></a>&lt;gcConcurrent&gt; – Element
Určuje, zda modul common language runtime spustí uvolnění paměti na samostatném vlákně.  
  
 \<Konfigurace >  
\<modul runtime >  
\<gcConcurrent >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime souběžně spustí uvolňování paměti.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nejde spustit uvolňování paměti současně.|  
|`true`|Uvolňování paměti běží souběžně. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Před rozhraní .NET Framework 4 uvolnění paměti pracovní stanice nepodporuje souběžné uvolňování paměti, které provádí uvolňování paměti na pozadí v samostatném vlákně. Souběžné uvolňování paměti v rozhraní .NET Framework 4, byl nahrazen uvolňování paměti, který také provádí uvolňování paměti na pozadí v samostatném vlákně na pozadí. Od verze rozhraní .NET Framework 4.5, shromažďování na pozadí jsou dostupné v uvolňování paměti serveru. `<gcConcurrent>` Prvek určuje, zda modul runtime provádí buď souběžné nebo při uvolňování paměti na pozadí, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.  
  
> [!WARNING]
>  Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí. Podmínky *souběžných* a *pozadí* zaměňují v dokumentaci k rozhraní .NET Framework. Chcete-li zakázat uvolňování paměti na pozadí, použijte `<gcConcurrent>` elementu, jak je popsáno v tomto článku.  
  
 Ve výchozím nastavení používá modul runtime souběžné nebo uvolňování paměti na pozadí, které je optimalizováno pro zpoždění. Pokud aplikace vyžaduje interakci uživatele náročné, nechte souběžné uvolňování paměti povoleno, chcete-li minimalizovat čas pozastavení aplikace pro provádění uvolnění. Pokud jste nastavili `enabled` atribut `<gcConcurrent>` element `false`, používá modul runtime nesouběžné uvolňování paměti, které je optimalizováno pro výkon. Následující konfigurační soubor zakáže uvolňování paměti na pozadí.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Pokud je `<gcConcurrentSetting>` nastavení v konfiguračním souboru počítače, definuje výchozí hodnotu pro všechny aplikace rozhraní .NET Framework. Nastavení konfiguračního souboru počítače přepíše nastavení konfiguračního souboru aplikace.  
  
 Další informace o současných a uvolňování paměti na pozadí, naleznete v části "souběžné uvolňování paměti" v [základy kolekce paměti](../../../../../docs/standard/garbage-collection/fundamentals.md) tématu.  
  
## <a name="example"></a>Příklad  
 Následující příklad umožňuje souběžné uvolňování paměti.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Základy kolekce paměti](../../../../../docs/standard/garbage-collection/fundamentals.md)
