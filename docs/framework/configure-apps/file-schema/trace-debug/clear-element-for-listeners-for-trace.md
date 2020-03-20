---
title: <clear>Prvek <listeners> pro pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153539"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<clear> \<Element pro \<posluchače> pro trasování>
Vymaže `Listeners` kolekce pro trasování.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trasovací>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<jasné>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasování zpráv.|  
|`listeners`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy. Naslouchací procesy nasměrují výstup trasování na příslušný cíl.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `<clear>` odebere všechny posluchače `Listeners` z kolekce pro trasování. Prvek můžete `<clear>` použít před `<add>` použitím prvku být jisti, že neexistují žádné další aktivní posluchače v kolekci.  
  
 Kolekci `Listeners` můžete vymazat programově voláním <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metody <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> ve`System.Diagnostics.Trace.Listeners.Clear()`vlastnosti ( ).  
  
 Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.  
  
> [!NOTE]
> Prvek `<clear>` odebere <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce, mění chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody. Volání `Assert` nebo `Fail` metoda obvykle vede k zobrazení okna se zprávou. Okno se zprávou se však <xref:System.Diagnostics.DefaultTraceListener> nezobrazí, `Listeners` pokud není v kolekci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `<clear>` použít prvek `<add>` před použitím `console` prvku `Listeners` přidat naslouchací proces do kolekce pro trasování.  
  
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
- [\<odebrat>](remove-element-for-listeners-for-trace.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
