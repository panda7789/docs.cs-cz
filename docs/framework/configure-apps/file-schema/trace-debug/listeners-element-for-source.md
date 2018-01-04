---
title: "&lt;moduly pro naslouchání&gt; Element pro &lt;zdroje&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dbabe9fbdc7ac4e611d96bf4bd696b716cf68156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a>&lt;moduly pro naslouchání&gt; Element pro &lt;zdroje&gt;
Přidá nebo odebere naslouchací procesy v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekci <xref:System.Diagnostics.TraceSource>. Naslouchací proces nasměruje výstup trasování do příslušné cílové, jako je například protokol, okno nebo textového souboru.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<zdroje >  
\<zdroj >  
\<moduly pro naslouchání > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|Přidá naslouchací proces a `Listeners` kolekce.|  
|[\<Odebrat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|Odebere naslouchací proces z `Listeners` kolekce.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|Vymaže `Listeners` kolekce zdroje trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
|`sources`|Obsahuje trasování zdrojů, které zahájí trasování zpráv.|  
|`source`|Určuje zdroj trasování, který iniciuje trasování zpráv.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<listeners>` elementu, který chcete přidat naslouchací konzoly na `mySource` zdroje a odeberete naslouchací proces trasování výchozí.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
