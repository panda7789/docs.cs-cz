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
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153318"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners> Element
Obsahuje naslouchací procesy, na které může odkazovat libovolný zdroj ový prvek nebo prvek trasování.  Tyto naslouchací procesy nepřijímají žádné stopy ve výchozím nastavení a není možné načíst tyto naslouchací procesy v době běhu. Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<přidat>](add-element-for-listeners-for-trace.md)|Přidá naslouchací proces do `sharedListeners` kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`Configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový prvek oddílu konfigurace ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Přidání naslouchací proces sdílené posluchače kolekce neznamená, že aktivní naslouchací proces. Musí být stále přidán do zdroje trasování nebo `Listeners` trasování přidáním do kolekce pro tento prvek trasování. Třídy posluchače v rozhraní .NET Framework jsou odvozeny z třídy. <xref:System.Diagnostics.TraceListener>  
  
 Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `<sharedListeners>` použít prvek `console` přidat `Listeners` naslouchací proces do kolekce pro <xref:System.Diagnostics.TraceSource> a <xref:System.Diagnostics.Trace> třídy. Naslouchací proces trasování konzoly <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace>zapisuje informace o trasování do konzoly prostřednictvím volání buď nebo .  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.TraceListener>
- [Trasování a ladění schématu nastavení](index.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
