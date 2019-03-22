---
title: Element <sharedListeners>
ms.date: 03/30/2017
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
ms.openlocfilehash: 281cc0bd2e577dedaffb7f7eaf04fe46e6ee0b59
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348814"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners > – Element
Obsahuje moduly pro naslouchání, které všechny zdroje nebo trasování – element může odkazovat.  Tyto moduly pro naslouchání se nezobrazí žádné trasování ve výchozím nastavení a není možné načíst tyto moduly pro naslouchání v době běhu. Naslouchací procesy, které jsou identifikovány jako sdílené moduly pro naslouchání lze přidat do zdroje nebo trasování podle názvu.  
  
 \<Konfigurace >  
\<system.diagnostics>  
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Přidá naslouchací proces pro `sharedListeners` kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element části o konfiguraci technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Přidání posluchače do sdílené kolekce posluchačů neprovede aktivní naslouchací proces. Musí stále se přidá do zdroje trasování nebo trasování tak, že přidáte tak, `Listeners` kolekce pro daný element trasování. Naslouchací proces třídy v rozhraní .NET Framework jsou odvozeny od <xref:System.Diagnostics.TraceListener> třídy.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<sharedListeners>` prvek a přidat naslouchací proces `console` k `Listeners` kolekce pro obě <xref:System.Diagnostics.TraceSource> a <xref:System.Diagnostics.Trace> třídy. Naslouchacího procesu trasování konzoly informace trasování zapíše do konzoly pomocí volání na buď <xref:System.Diagnostics.TraceSource> nebo <xref:System.Diagnostics.Trace>.  
  
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
</configuration>
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Diagnostics.TraceListener>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
