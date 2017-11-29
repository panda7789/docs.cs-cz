---
title: "&lt;Thread_UseAllCpuGroups&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 187e391acf3b80a5ae2dfe795c4a3b397af815ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltthreaduseallcpugroupsgt-element"></a>&lt;Thread_UseAllCpuGroups&gt; – Element
Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.  
  
 \<Konfigurace >  
\<modul runtime >  
< Thread_UseAllCpuGroups >  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime neprovede distribuci spravovaných vláknech v několika skupinách pro využití procesoru. Toto nastavení je výchozí.|  
|`true`|Modul runtime distribuuje spravovaných vláknech v několika skupinách pro procesor, pokud má počítač více skupin procesoru a [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element je povoleno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud počítač obsahuje více skupin procesoru, povolení tohoto elementu způsobí, že modul runtime pro distribuci spravovaných vláken ve všech skupinách procesoru. Chcete-li tuto funkci používat, musíte také povolit [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, který rozšiřuje uvolňování paměti pro všechny skupiny procesoru a bere v potaz při vytváření a vyrovnávání haldách všechny jader. Povolení [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) prvek vyžaduje povolení [ \<gcserver – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element. Pokud nejsou povolené tyto prvky, povolení `<Thread_UseAllCpuGroups>` element nemá žádný vliv.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit podporu pro více skupin procesoru.  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<Gccpugroup – > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
