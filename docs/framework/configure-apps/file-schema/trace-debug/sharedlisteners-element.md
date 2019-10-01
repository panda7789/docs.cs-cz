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
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699292"
---
# <a name="sharedlisteners-element"></a>@no__t – element > 0sharedListeners
Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.  Tyto naslouchací procesy neobdrží žádné trasování ve výchozím nastavení a není možné načíst tyto naslouchací procesy v době běhu. Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<sharedListeners >**  
  
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
|[@no__t – 1add >](add-element-for-listeners-for-trace.md)|Přidá naslouchací proces do kolekce `sharedListeners`.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element konfiguračního oddílu ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
 Přidání naslouchacího procesu do kolekce Shared Listeners neprovádí aktivní naslouchací proces. Ještě musí být přidán do zdroje trasování nebo do trasování, protože ho přidáte do kolekce `Listeners` pro tento prvek Trace. Třídy naslouchacího procesu v .NET Framework jsou odvozeny z třídy <xref:System.Diagnostics.TraceListener>.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití prvku `<sharedListeners>` pro přidání naslouchacího procesu `console` do kolekce `Listeners` pro třídy <xref:System.Diagnostics.TraceSource> a <xref:System.Diagnostics.Trace>. Naslouchací proces trasování konzoly zapisuje trasovací informace do konzoly prostřednictvím volání buď <xref:System.Diagnostics.TraceSource> nebo <xref:System.Diagnostics.Trace>.  
  
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
- [Trasování a ladění schématu nastavení](index.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
