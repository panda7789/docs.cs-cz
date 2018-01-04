---
title: "&lt;trasování&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d7ddcbdbdbbc2924d4f725d2fd401f873a4cfb0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttracegt-element"></a>&lt;trasování&gt; – Element
Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<trasování >  
  
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
|`autoflush`|Nepovinný atribut.<br /><br /> Určuje, zda naslouchací procesy trasování automaticky vyprázdnění výstupní vyrovnávací paměť po každé operace zápisu.|  
|`indentsize`|Nepovinný atribut.<br /><br /> Určuje počet prostory pro odsazení.|  
|`useGlobalLock`|Nepovinný atribut.<br /><br /> Určuje, zda má být použita globální zámek.|  
  
## <a name="autoflush-attribute"></a>autoflush atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Není k vyprázdnění automaticky výstupní vyrovnávací paměť. Toto nastavení je výchozí.|  
|`true`|Automaticky vyprázdní vyrovnávací paměť pro výstup.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Pokud je naslouchací proces vláken; nepoužívá globální zámek jinak použije globální zámek.|  
|`true`|Využívá globální zámek bez ohledu na to, jestli naslouchací proces je zaručeno bezpečné používání vláken. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<moduly pro naslouchání >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Určuje naslouchací proces, který shromažďuje, úložiště a směrování zpráv.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<trace>` elementu, který chcete přidat naslouchací proces `MyListener` k `Listeners` kolekce. `MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `useGlobalLock` Je atribut nastaven na `false`, což způsobí, že globální zámek nechcete použít v případě naslouchací proces trasování je zaručeno bezpečné používání vláken. `autoflush` Je atribut nastaven na `true`, což způsobí, že naslouchací proces trasování k zápisu do souboru bez ohledu na to, jestli <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> metoda je volána. `indentsize` Je nastavena na hodnotu 0 (nula), což způsobí, že naslouchací proces pro odsazení nulové prostory při <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> metoda je volána.  
  
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
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
