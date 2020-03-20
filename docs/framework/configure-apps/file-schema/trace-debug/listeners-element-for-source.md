---
title: Element <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153409"
---
# <a name="listeners-element-for-source"></a>\<naslouchací> Element pro \<zdrojový>
Přidá nebo odebere posluchače v kolekci <xref:System.Diagnostics.TraceSource.Listeners%2A> pro <xref:System.Diagnostics.TraceSource>. Naslouchací proces směruje výstup trasování na příslušný cíl, například protokol, okno nebo textový soubor.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdrojové>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<posluchači>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<přidat>](add-element-for-listeners-for-source.md)|Přidá naslouchací proces do `Listeners` kolekce.|  
|[\<odebrat>](remove-element-for-listeners-for-source.md)|Odebere naslouchací proces z `Listeners` kolekce.|  
|[\<jasné>](clear-element-for-listeners-for-source.md)|Vymaže kolekci `Listeners` pro zdroj trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které iniciují tracing zprávy.|  
|`source`|Určuje zdroj trasování, který iniciuje trasování zpráv.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `<listeners>` použít prvek k přidání `mySource` posluchače trasování konzoly do zdroje a odebrat výchozí naslouchací proces trasování.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.TraceListener>
- [Trasování a ladění schématu nastavení](index.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
