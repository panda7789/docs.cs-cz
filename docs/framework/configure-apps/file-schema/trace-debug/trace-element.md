---
title: Element <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153163"
---
# <a name="trace-element"></a>\<trasování> Element
Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasování zpráv.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trasovací>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`autoflush`|Nepovinný atribut.<br /><br /> Určuje, zda posluchači trasování automaticky vyprázdní výstupní vyrovnávací paměť po každé operaci zápisu.|  
|`indentsize`|Nepovinný atribut.<br /><br /> Určuje počet mezer, které se mají odsazet.|  
|`useGlobalLock`|Nepovinný atribut.<br /><br /> Označuje, zda má být globální zámek použit.|  
  
## <a name="autoflush-attribute"></a>atribut automatického vyprázdnění  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Není automaticky vyprázdnění výstupní vyrovnávací paměti. Toto nastavení je výchozí.|  
|`true`|Automaticky vyprázdní výstupní vyrovnávací paměť.|  
  
## <a name="usegloballock-attribute"></a>atribut useGlobalLock  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nepoužívá globální zámek, pokud je naslouchací proces bezpečný pro přístup z více vláken; v opačném případě používá globální zámek.|  
|`true`|Používá globální zámek bez ohledu na to, zda je naslouchací proces bezpečný pro přístup z více vláken. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<posluchači>](listeners-element-for-trace.md)|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `<trace>` použít prvek `MyListener` k `Listeners` přidání naslouchací proces do kolekce. `MyListener`vytvoří soubor s `MyListener.log` názvem a zapíše výstup do souboru. Atribut `useGlobalLock` je nastaven `false`na , což způsobí, že globální zámek nelze použít, pokud je naslouchací proces trasování bezpečný pro přístup z více vláken. Atribut `autoflush` je nastaven `true`na , což způsobí, že posluchač trasování <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> zapisovat do souboru bez ohledu na to, zda je volána metoda. Atribut `indentsize` je nastaven na 0 (nula), což způsobí, <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> že posluchač odsadit nulové mezery při volání metody.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Trasování a ladění schématu nastavení](index.md)
