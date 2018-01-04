---
title: "&lt;sharedListeners –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: aef29e6107a2f441d8c1a6826b16f0f0c0b56973
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsharedlistenersgt-element"></a>&lt;sharedListeners –&gt; – Element
Obsahuje naslouchací procesy, které může odkazovat všechny zdroje nebo element trasování.  Tyto moduly pro naslouchání neobdrží ve výchozím nastavení všechny trasování a není možné načíst tyto moduly pro naslouchání v době běhu. Moduly pro naslouchání identifikovány jako sdílené moduly pro naslouchání mohou být přidány do zdroje nebo trasování podle názvu.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<sharedListeners >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Přidá naslouchací proces a `sharedListeners` kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Přidávání do kolekce sdílené moduly pro naslouchání naslouchací proces neprovede active naslouchací proces. Je nutné stále jej přidat zdroj trasování nebo trasování přidáním jeho `Listeners` kolekce pro daný element trasování. Naslouchací proces třídy v rozhraní .NET Framework jsou odvozeny od <xref:System.Diagnostics.TraceListener> třídy.  
  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<sharedListeners>` elementu, který chcete přidat naslouchací proces `console` k `Listeners` kolekce pro oba <xref:System.Diagnostics.TraceSource> a <xref:System.Diagnostics.Trace> třídy. Naslouchací proces trasování konzoly informace trasování zapíše do konzoly prostřednictvím volání buď <xref:System.Diagnostics.TraceSource> nebo <xref:System.Diagnostics.Trace>.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
