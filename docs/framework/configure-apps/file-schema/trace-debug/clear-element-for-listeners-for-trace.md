---
title: <clear>Element pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927174"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<Clear > element pro \<naslouchací procesy > \<pro > trasování
`Listeners` Vymaže kolekci pro Trace.  
  
 \<> Konfigurace  
\<system.diagnostics>  
\<> trasování  
\<> naslouchací proces  
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
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
|`listeners`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
  
## <a name="remarks"></a>Poznámky  
 Element odebere všechny naslouchací procesy `Listeners` z kolekce pro trasování. `<clear>` `<clear>` Element lze použít před `<add>` použitím prvku, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.  
  
 `Listeners` Kolekci můžete vymazat programově <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> voláním metody pro <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnost (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
> [!NOTE]
> `<clear>` Prvek odebere<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> z kolekce`Listeners`a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>změní chování metod<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>,,a. <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DefaultTraceListener> Volání metody `Fail` nebo obvykle vede k zobrazení okna se zprávou. `Assert` Okno se zprávou se ale nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není `Listeners` v kolekci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `<clear>` , jak použít element před `<add>` použitím elementu pro `Listeners` přidání naslouchacího procesu `console` do kolekce pro trasování.  
  
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
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
