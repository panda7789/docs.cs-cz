---
title: '&lt;Vymazat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 91b4b4f132138fa6752c1da9b28e7a3ab7fad006
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082887"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Vymazat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;
Vymaže `Listeners` kolekce pro trasování.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<trasování >  
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
|`trace`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.|  
|`listeners`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat zprávy. Posluchači přímý výstup trasování příslušný cíli.|  
  
## <a name="remarks"></a>Poznámky  
 `<clear>` Element odebere všechny moduly pro naslouchání z `Listeners` kolekce pro trasování. Můžete použít `<clear>` prvek před použitím `<add>` element je potřeba mít jistotu, nejsou žádné aktivní naslouchací procesy v kolekci.  
  
 Můžete vymazat `Listeners` kolekce programově zavoláním <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metodu <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnosti (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
> [!NOTE]
>  `<clear>` Odebere element <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce, změna chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody. Volání `Assert` nebo `Fail` metoda je normálně ve výsledku zobrazení okna se zprávou. Však se nezobrazí okno se zprávou, pokud <xref:System.Diagnostics.DefaultTraceListener> se nepoužívá `Listeners` kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<clear>` prvek před použitím `<add>` prvek a přidat naslouchací proces `console` k `Listeners` kolekce pro trasovacího.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
