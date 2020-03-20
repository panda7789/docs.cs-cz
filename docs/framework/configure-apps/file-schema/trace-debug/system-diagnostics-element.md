---
title: <system.diagnostics> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153204"
---
# <a name="systemdiagnostics-element"></a>\<system.diagnostics> Element
Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostická>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<uplatnit>](assert-element.md)|Určuje, zda se má při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody zobrazit okno se zprávou. také určuje název souboru, do který má být zapisován.|  
|[\<performanceCounters>](performancecounters-element.md)|Určuje velikost globální paměti sdílené čítači výkonu.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Obsahuje naslouchací procesy, na které může odkazovat libovolný zdroj ový prvek nebo prvek trasování. Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.|  
|[\<zdroje>](sources-element.md)|Určuje zdroje trasování, které iniciují zprávy trasování.|  
|[\<přepínače>](switches-element.md)|Obsahuje přepínače trasování a úrovně, kde jsou přepínače trasování nastaveny.|  
|[\<trasovací>](trace-element.md)|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasování zpráv.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vložit přepínač trasování a naslouchací proces trasování uvnitř prvku ** \<system.diagnostics>.** Přepínač `General` trasování je <xref:System.Diagnostics.TraceLevel> nastaven na úroveň. Naslouchací proces trasování `myListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.  
  
> [!NOTE]
> V rozhraní .NET Framework verze 2.0 můžete použít text k určení hodnoty přepínače. Můžete například zadat `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo použít text představující hodnotu výčtu, například `Error` <xref:System.Diagnostics.TraceSwitch>pro . Řádek `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.  
  
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
