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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153163"
---
# <a name="trace-element"></a>Element \<trace>
Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
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
|`autoflush`|Nepovinný atribut.<br /><br /> Určuje, zda naslouchací proces trasování po každé operaci zápisu automaticky vyprázdní výstupní vyrovnávací paměť.|  
|`indentsize`|Nepovinný atribut.<br /><br /> Určuje počet mezer, které mají být odsazeny.|  
|`useGlobalLock`|Nepovinný atribut.<br /><br /> Určuje, zda má být použit globální zámek.|  
  
## <a name="autoflush-attribute"></a>AutoFlush – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`false`|Nevyprázdní výstupní vyrovnávací paměť automaticky. Toto nastavení je výchozí.|  
|`true`|Automaticky vyprázdní výstupní vyrovnávací paměť.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`false`|Nepoužívá globální zámek, pokud naslouchací proces je bezpečný pro přístup z více vláken; v opačném případě používá globální zámek.|  
|`true`|Používá globální zámek bez ohledu na to, zda je naslouchací proces bezpečný pro přístup z více vláken. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<trace>` element k přidání naslouchacího procesu `MyListener` do `Listeners` kolekce. `MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `useGlobalLock`Atribut je nastaven na `false` , což způsobí, že globální zámek nebude použit, pokud je naslouchací proces trasování bezpečný pro přístup z více vláken. `autoflush`Atribut je nastaven na `true` , což způsobí, že naslouchací proces trasování zapisuje do souboru bez ohledu na to, zda <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> je metoda volána. `indentsize`Atribut je nastaven na hodnotu 0 (nula), což způsobí, že naslouchací proces při volání metody odsadí nula mezer <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> .  
  
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
