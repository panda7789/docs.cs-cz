---
title: '&lt;gcServer&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46aae3ad287c2626123cf3f513fc72bc1acdd06e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltgcservergt-element"></a>&lt;gcServer&gt; Element
Určuje, zda modul common language runtime běží kolekce paměti na serveru.  
  
 \<Konfigurace >  
\<modul runtime >  
\<gcServer>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime běží kolekce paměti na serveru.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Kolekce paměti na serveru nelze spustit. Toto nastavení je výchozí.|  
|`true`|Kolekce paměti na serveru běží.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (CLR) podporuje dva typy uvolňování paměti: uvolnění paměti pro pracovní stanice, která je k dispozici na všech systémech, a kolekce paměti na serveru, která je k dispozici v systémech s více procesory. Můžete použít `<gcServer>` provede elementu k řízení typu uvolňování paměti modulu CLR. Použití <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> vlastnosti k určení, zda je kolekce paměti na serveru povoleno.  
  
 Pro počítače, jeden procesor by měla být uvolňování výchozí pracovní stanice nejrychlejší možnost. Pracovní stanice nebo server lze použít pro počítače se dvěma procesory. Kolekce paměti na serveru by měl být nejrychlejší možnost pro více než dva procesory.  
  
 Tento element může použít pouze v konfiguračním souboru aplikace; je ignorován, pokud je v konfiguračním souboru počítače.  
  
> [!NOTE]
>  V rozhraní .NET Framework 4 a dřívějších verzích souběžné uvolňování paměti není k dispozici při uvolňování paměti serveru je povoleno. Od verze [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], je souběžné uvolňování paměti serveru. Chcete-li použít server nesouběžného uvolňování paměti, nastavte `<gcServer>` element `true` a [ \<gcconcurrent – > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) k `false`.  
  
## <a name="example"></a>Příklad  
 Následující příklad povolí kolekce paměti na serveru.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Postupy: zakázat souběžná kolekce paměti](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
