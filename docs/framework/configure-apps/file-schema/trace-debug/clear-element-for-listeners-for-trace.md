---
title: <clear>Element pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153539"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<clear>Element pro \<listeners> pro\<trace>
Vymaže `Listeners` kolekci pro Trace.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

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
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
|`listeners`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
  
## <a name="remarks"></a>Poznámky  
 `<clear>`Element odebere všechny naslouchací procesy z `Listeners` kolekce pro trasování. Element lze použít `<clear>` před použitím `<add>` prvku, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.  
  
 Kolekci můžete vymazat `Listeners` programově voláním <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metody pro <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnost ( `System.Diagnostics.Trace.Listeners.Clear()` ).  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
> [!NOTE]
> `<clear>`Prvek odebere <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce a změní chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> metod,, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> . Volání `Assert` metody nebo `Fail` obvykle vede k zobrazení okna se zprávou. Okno se zprávou se ale nezobrazí, pokud není <xref:System.Diagnostics.DefaultTraceListener> v `Listeners` kolekci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<clear>` element před použitím `<add>` elementu pro přidání naslouchacího procesu `console` do `Listeners` kolekce pro trasování.  
  
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

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Trasování a ladění schématu nastavení](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
