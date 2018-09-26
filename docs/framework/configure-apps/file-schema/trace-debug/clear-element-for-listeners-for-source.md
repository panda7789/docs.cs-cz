---
title: '&lt;Vymazat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;zdroje&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3674b5e8f54735010da901c76b77bd617218891e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071750"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Vymazat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;zdroje&gt;
Vymaže `Listeners` kolekci pro zdroj trasování.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<zdroje >  
\<zdroj >  
\<naslouchací procesy >  
\<Vymazat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.|  
|`source`|Určuje zdroj trasování, který iniciuje trasovací zprávy.|  
|`listeners`|Určuje naslouchací procesy, které shromažďování, ukládání a směrovat zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 `<clear>` Element odebere všechny moduly pro naslouchání z `Listeners` kolekce pro zdroj trasování, včetně <xref:System.Diagnostics.DefaultTraceListener>. Můžete použít `<clear>` prvek před použitím `<add>` element je potřeba mít jistotu, nejsou žádné aktivní naslouchací procesy v kolekci.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<clear>` prvek před použitím `<add>` prvky pro přidání posluchače `console` a `textListener` k `Listeners` kolekce pro zdroj trasování `TraceSourceApp`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
