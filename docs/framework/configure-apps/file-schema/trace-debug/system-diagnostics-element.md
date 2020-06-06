---
title: <element System. Diagnostics>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153204"
---
# <a name="systemdiagnostics-element"></a>Element \<system.diagnostics>
Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|Určuje, zda se má při volání metody zobrazit okno se zprávou <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> . určuje také název souboru, do kterého budou zapsány zprávy.|  
|[\<performanceCounters>](performancecounters-element.md)|Určuje velikost globální paměti sdílené čítači výkonu.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace. Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.|  
|[\<sources>](sources-element.md)|Určuje zdroje trasování, které spouštějí trasovací zprávy.|  
|[\<switches>](switches-element.md)|Obsahuje přepínače trasování a úrovně, kde jsou nastaveny přepínače trasování.|  
|[\<trace>](trace-element.md)|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vložit přepínač trasování a naslouchací proces trasování uvnitř **\<system.diagnostics>** elementu. `General`Přepínač trasování je nastaven na <xref:System.Diagnostics.TraceLevel> úroveň. Naslouchací proces trasování `myListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.  
  
> [!NOTE]
> V .NET Framework verze 2,0 můžete použít text a zadat hodnotu pro přepínač. Například můžete zadat `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo použít text představující hodnotu výčtu, například `Error` pro <xref:System.Diagnostics.TraceSwitch> . Čára `<add name="myTraceSwitch" value="Error" />` je ekvivalentem `<add name="myTraceSwitch" value="1" />` .  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [Trasování a ladění schématu nastavení](index.md)
