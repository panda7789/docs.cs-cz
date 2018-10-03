---
title: '&lt;Filtr&gt; – Element pro &lt;přidat&gt; pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
author: mcleblanc
ms.author: markl
ms.openlocfilehash: be4f3dcce1a746b287e75e0e6d3ba6eaa1d9b57b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032553"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a>&lt;Filtr&gt; – Element pro &lt;přidat&gt; pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;
Přidá filtr do naslouchacího procesu v `Listeners` kolekce pro trasování.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<trasování >  
\<naslouchací procesy >  
\<add>  
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
|`type`|Požadovaný atribut.<br /><br /> Určuje typ filtru, která by měla dědit z <xref:System.Diagnostics.TraceFilter> třídy. Můžete použít název kvalifikovaný v oboru názvů typu, který odpovídá typu <xref:System.Type.FullName%2A> vlastnost, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, která odpovídá <xref:System.Type.AssemblyQualifiedName%2A> vlastnost. Informace o úplných názvů typů najdete v tématu [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro třídu zadaný filtr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`trace`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.|  
|`listeners`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat zprávy. Posluchači přímý výstup trasování příslušný cíli.|  
|`add`|Přidá naslouchací proces pro `Listeners` kolekce.|  
  
## <a name="remarks"></a>Poznámky  
 `<filter>` Elementu musí být součástí `<add>` – element pro naslouchací proces trasování, který určuje typ naslouchací proces, ne jenom název naslouchacího procesu definované v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md). Pokud je definován naslouchací proces ve [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr pro tuto naslouchací proces musí být definován v tomto elementu.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<filter>` prvek přidejte filtr k naslouchacímu procesu `console` v `Listeners` kolekce pro trasování a zadejte úroveň filtru událostí jako `Error`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
