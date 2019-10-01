---
title: <clear> element pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 0361580724351f8f42d058d5e20354e3335bac2f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699370"
---
# <a name="clear-element-for-listeners-for-trace"></a>> element \<clear pro \<listeners > pro \<trace >
Vymaže kolekci `Listeners` pro trasování.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**  
  
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
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
|`listeners`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
  
## <a name="remarks"></a>Poznámky  
 Element `<clear>` odebere všechny naslouchací procesy z kolekce `Listeners` pro trasování. Element `<clear>` lze použít před použitím prvku `<add>`, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.  
  
 Kolekci `Listeners` můžete programově vymazat voláním metody <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> na vlastnosti <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
> [!NOTE]
> Element `<clear>` odebere <xref:System.Diagnostics.DefaultTraceListener> z kolekce `Listeners` a změní chování metod <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>. Volání metody `Assert` nebo `Fail` obvykle vede k zobrazení okna se zprávou. Okno se zprávou se ale nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není v kolekci `Listeners`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít prvek `<clear>` před použitím prvku `<add>` pro přidání naslouchacího procesu `console` do kolekce `Listeners` pro trasování.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Trasování a ladění schématu nastavení](index.md)
- [@no__t – 1remove >](remove-element-for-listeners-for-trace.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
