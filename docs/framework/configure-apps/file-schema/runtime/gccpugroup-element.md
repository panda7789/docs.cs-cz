---
title: '&lt;Gccpugroup –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25d083b730117a791fb8ab550b36f7b2e6c5f5be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613710"
---
# <a name="ltgccpugroupgt-element"></a>&lt;Gccpugroup –&gt; – Element
Určuje, zda uvolňování podporuje více skupin procesorů.  
  
 \<Konfigurace >  
\<modul runtime >  
\<GCCpuGroup>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda uvolňování podporuje více skupin procesorů.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Uvolňování paměti kolekce nepodporuje více skupin procesorů. Toto nastavení je výchozí.|  
|`true`|Uvolňování paměti podporuje více skupin procesorů, pokud je povolené uvolnění paměti serveru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Když počítač má více skupin procesorů a uvolňování paměti serveru je povolená (najdete v článku [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), povolení tohoto prvku rozšiřuje uvolňování paměti ve všech skupinách procesoru a přejde do všech jader účet při vytváření a rozložení zátěže haldy.  
  
> [!NOTE]
>  Tento element se vztahují pouze k vlákna uvolňování paměti. Pokud chcete povolit modul runtime bude distribuovat Uživatelská vlákna ve všech skupinách procesoru, musíte také povolit [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesorů.  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Postupy: Zakázat souběžné uvolňování paměti](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
- [Uvolňování paměti pracovní stanice a serveru](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
