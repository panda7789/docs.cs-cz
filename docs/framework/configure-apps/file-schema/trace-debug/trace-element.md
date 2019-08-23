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
ms.openlocfilehash: fd90d271591a47849b3f70aea50cbe909b6fd613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920402"
---
# <a name="trace-element"></a>\<Trace – element > elementu
Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.  
  
 \<> Konfigurace  
\<system.diagnostics>  
\<> trasování  
  
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
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Nevyprázdní výstupní vyrovnávací paměť automaticky. Toto nastavení je výchozí.|  
|`true`|Automaticky vyprázdní výstupní vyrovnávací paměť.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Nepoužívá globální zámek, pokud naslouchací proces je bezpečný pro přístup z více vláken; v opačném případě používá globální zámek.|  
|`true`|Používá globální zámek bez ohledu na to, zda je naslouchací proces bezpečný pro přístup z více vláken. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> naslouchací proces](listeners-element-for-trace.md)|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<trace>` element k přidání naslouchacího procesu `MyListener` do `Listeners` kolekce. `MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. Atribut je nastaven na `false`, což způsobí, že globální zámek nebude použit, pokud je naslouchací proces trasování bezpečný pro přístup z více vláken. `useGlobalLock` Atribut je nastaven na `true`, což způsobí, že naslouchací proces trasování zapisuje do souboru <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> bez ohledu na to, zda je metoda volána. `autoflush` Atribut je nastaven na hodnotu 0 (nula), což způsobí, že naslouchací proces <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> při volání metody odsadí nula mezer. `indentsize`  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Trasování a ladění schématu nastavení](index.md)
