---
title: <listeners> – element pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 10530cfadf2e182f912c699e50294af4b57f47b5
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088866"
---
# <a name="listeners-element-for-trace"></a>> elementu \<Listeners pro \<trasování >
Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trace >** ](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<listeners >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<přidat >](add-element-for-listeners-for-trace.md)|Přidá naslouchací proces do kolekce `Listeners`.|  
|[\<vymazat >](clear-element-for-listeners-for-trace.md)|Vymaže kolekci `Listeners` pro trasování.|  
|[\<odebrat >](remove-element-for-listeners-for-trace.md)|Odebere naslouchací proces z kolekce `Listeners`.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element konfiguračního oddílu ASP.NET.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> sdílejí stejnou kolekci **posluchačů** . Pokud přidáte objekt naslouchacího procesu do kolekce v jedné z těchto tříd, použije druhá třída stejný naslouchací proces. Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít > elementu **\<Listeners** k přidání `MyListener` posluchačů a `MyEventListener` do kolekce **posluchačů** . `MyListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `MyEventListener` vytvoří položku v protokolu událostí.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceListener>
- [Trasování a ladění schématu nastavení](index.md)
