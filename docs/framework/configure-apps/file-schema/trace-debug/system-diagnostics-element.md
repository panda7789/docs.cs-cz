---
title: < element System. Diagnostics >
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699198"
---
# <a name="systemdiagnostics-element"></a>\<element System. Diagnostics >
Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.  
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. diagnostics >**  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|Určuje, zda se má při volání metody <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> zobrazit okno se zprávou. Určuje také název souboru, do kterého se mají zapisovat zprávy.|  
|[\<performanceCounters>](performancecounters-element.md)|Určuje velikost globální paměti sdílené čítači výkonu.|  
|[\<sharedListeners >](sharedlisteners-element.md)|Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace. Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.|  
|[zdroje \<>](sources-element.md)|Určuje zdroje trasování, které spouštějí trasovací zprávy.|  
|[\<switches>](switches-element.md)|Obsahuje přepínače trasování a úrovně, kde jsou nastaveny přepínače trasování.|  
|[\<trace>](trace-element.md)|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vložit přepínač trasování a naslouchací proces trasování v rámci prvku **\<System. diagnostic >** . Přepínač trasování `General` je nastaven na úroveň <xref:System.Diagnostics.TraceLevel>. Naslouchací proces trasování `myListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.  
  
> [!NOTE]
> V .NET Framework verze 2,0 můžete použít text a zadat hodnotu pro přepínač. Můžete například zadat `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo použít text reprezentující hodnotu výčtu, jako je například `Error` pro <xref:System.Diagnostics.TraceSwitch>. `<add name="myTraceSwitch" value="Error" />` řádku je ekvivalentem `<add name="myTraceSwitch" value="1" />`.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [Trasování a ladění schématu nastavení](index.md)
