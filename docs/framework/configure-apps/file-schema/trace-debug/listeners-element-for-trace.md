---
title: "&lt;moduly pro naslouchání&gt; Element pro &lt;trasování&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b9c1f52f880a38791a9a8d5b5372b2ad53c5569f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltlistenersgt-element-for-lttracegt"></a>&lt;moduly pro naslouchání&gt; Element pro &lt;trasování&gt;
Určuje naslouchací proces, který shromažďuje, úložiště a směrování zpráv. Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.  
  
 \<Konfigurace > elementu  
\<System.Diagnostics > elementu  
\<trasování > elementu  
\<moduly pro naslouchání > elementu pro \<trasování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Přidá naslouchací proces a `Listeners` kolekce.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Vymaže `Listeners` kolekce pro trasování.|  
|[\<Odebrat >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Odebere naslouchací proces z `Listeners` kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> třídy sdílet stejný **naslouchací procesy** kolekce. Pokud přidáte objekt naslouchací proces ke kolekci v jedné z těchto tříd, používá jiná třída stejný naslouchací proces. Naslouchací proces třídy součástí rozhraní .NET Framework odvozena od <xref:System.Diagnostics.TraceListener> třídy.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat  **\<naslouchací procesy >** elementu, který chcete přidat posluchače `MyListener` a `MyEventListener` k **naslouchací procesy** kolekce. `MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `MyEventListener`vytvoří záznam v protokolu událostí.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
