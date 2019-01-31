---
title: <Thread_UseAllCpuGroups> Element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95411f5adde07c0d00124b2793b495c7ed8f49ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288935"
---
# <a name="threaduseallcpugroups-element"></a>\<Thread_UseAllCpuGroups > – Element
Určuje, zda modul runtime provádí distribuci spravovaných vláken ve všech skupinách procesoru.  
  
 \<Konfigurace >  
\<modul runtime >  
<Thread_UseAllCpuGroups>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime provádí distribuci spravovaných vláken ve všech skupinách procesoru.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime neprovádí distribuci spravovaných vláken ve více skupinách procesoru. Toto nastavení je výchozí.|  
|`true`|Modul runtime provádí distribuci spravovaných vláken ve více skupinách procesoru, pokud má počítač více skupin procesorů a [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) prvek povolený.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud počítač má více skupin procesorů, povolení tohoto prvku způsobí, že modul runtime bude distribuovat spravovaná vlákna ve všech skupinách procesoru. Chcete-li tuto funkci používat, musíte také povolit [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, který rozšiřuje uvolňování paměti na všech skupinách procesoru a všechna jádra bere v úvahu při vytváření a rozložení zátěže haldy. Povolení [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element vyžaduje povolení [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elementu. Pokud tyto prvky nejsou povoleny, takže `<Thread_UseAllCpuGroups>` element nemá žádný vliv.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit podporu pro více skupin procesorů.  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<GCCpuGroup> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
