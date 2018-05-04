---
title: '&lt;gcconcurrent –&gt; – Element'
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
ms.openlocfilehash: ee00c3a307523d2cae831274630ad6828cd9daf6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcconcurrentgt-element"></a>&lt;gcconcurrent –&gt; – Element
Určuje, zda modul common language runtime spuštěna uvolňování paměti na samostatné vlákno.  
  
 \<Konfigurace >  
\<modul runtime >  
\<gcconcurrent – >  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime běží souběžně uvolňování paměti.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Současně nespouští uvolňování paměti.|  
|`true`|Uvolňování paměti běží souběžně. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Uvolňování paměti pracovních stanic před rozhraní .NET Framework 4 podporováno souběžné uvolňování paměti, která provádí uvolňování paměti na pozadí na samostatné vlákno. V rozhraní .NET Framework 4 souběžné uvolňování nahradily pozadí globální Katalog, který také provádí uvolňování paměti na pozadí na samostatné vlákno. Od verze rozhraní .NET Framework 4.5, pozadí kolekce jsou k dispozici v kolekce paměti na serveru. `<gcConcurrent>` Element řídí, zda modul runtime provádí buď souběžných nebo na pozadí uvolňování paměti, pokud je k dispozici, nebo zda vykonává uvolňování paměti v popředí.  
  
> [!WARNING]
>  Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí. Podmínky *souběžných* a *pozadí* se zcela zaměnitelným významem používají v dokumentaci k rozhraní .NET Framework. Chcete-li zakázat kolekce paměti na pozadí, použijte `<gcConcurrent>` elementu, jak je popsáno v tomto článku.  
  
 Ve výchozím nastavení používá modul runtime souběžných nebo kolekce paměti na pozadí, která je optimalizovaná pro latenci. Pokud vaše aplikace zahrnuje interakce velkou uživatele, ponechejte souběžné uvolňování povoleno minimalizovat čas pozastavení aplikace k provedení uvolňování paměti. Pokud nastavíte `enabled` atribut `<gcConcurrent>` element `false`, modul runtime používá nesouběžného uvolňování paměti, která je optimalizovaná pro propustnost. Následující konfigurační soubor zakáže kolekce paměti na pozadí.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Pokud dojde `<gcConcurrentSetting>` nastavení v konfiguračním souboru počítače, definuje výchozí hodnota pro všechny aplikace rozhraní .NET Framework. Nastavení počítače konfiguračního souboru přepíše nastavení konfiguračního souboru aplikace.  
  
 Další informace o souběžných a kolekce paměti na pozadí, najdete v části "souběžné uvolňování paměti" v [základy uvolnění paměti](../../../../../docs/standard/garbage-collection/fundamentals.md) tématu.  
  
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
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Základy kolekce paměti](../../../../../docs/standard/garbage-collection/fundamentals.md)
