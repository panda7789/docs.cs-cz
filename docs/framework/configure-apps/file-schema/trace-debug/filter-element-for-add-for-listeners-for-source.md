---
title: "&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ff5acf8edcda68979c04f5e62237464ee6f040a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;
Přidá filtr do naslouchací proces ve `Listeners` kolekce zdroje trasování.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<zdroje >  
\<zdroj >  
\<moduly pro naslouchání >  
\<Přidat >  
\<Filtr >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`type`|Požadovaný atribut.<br /><br /> Určuje typ filtru, který by měl dědí <xref:System.Diagnostics.TraceFilter> třídy. Můžete použít obor názvů kvalifikovaný název typu, který odpovídá na typ <xref:System.Type.FullName%2A> vlastnost, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, který odpovídá <xref:System.Type.AssemblyQualifiedName%2A> vlastnost. Informace o úplné názvy typů najdete v tématu [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro třídu zadaný filtr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
|`sources`|Obsahuje trasování zdrojů, které zahájí trasování zpráv.|  
|`source`|Určuje zdroj trasování, který iniciuje trasování zpráv.|  
|`listeners`|Obsahuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv. Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.|  
|`add`|Přidá naslouchací proces a `Listeners` kolekce zdroje trasování.|  
  
## <a name="remarks"></a>Poznámky  
 `<filter>` Element musí být obsažená v `<add>` element pro naslouchací proces zdroj trasování, který určuje typ naslouchacího procesu, nikoli jen název naslouchací proces definované v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md). Pokud naslouchací proces je definována v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr pro tento naslouchacího procesu musí být definován v daný element.  
  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<filter>` elementu, který chcete přidat filtr na naslouchací proces `console` v `Listeners` kolekci pro zdroj trasování `myTraceSource`, zadání úroveň události filtru jako `Error`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
