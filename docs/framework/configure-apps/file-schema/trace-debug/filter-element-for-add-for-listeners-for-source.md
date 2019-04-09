---
title: <filter> – Element pro <add> pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 3abfd0bdd40f98a9e4774677fc2cd5068c14333f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186729"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<Filtr > – Element pro \<Přidat > pro \<naslouchacích procesů > pro \<zdroje >
Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.  
  
 \<Konfigurace >  
\<system.diagnostics>  
\<zdroje >  
\<zdroj >  
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
|`sources`|Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.|  
|`source`|Určuje zdroj trasování, který iniciuje trasovací zprávy.|  
|`listeners`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat zprávy. Posluchači přímý výstup trasování příslušný cíli.|  
|`add`|Přidá naslouchací proces pro `Listeners` kolekci pro zdroj trasování.|  
  
## <a name="remarks"></a>Poznámky  
 `<filter>` Elementu musí být součástí `<add>` element pro zdroj trasování naslouchací proces, který určuje typ naslouchací proces, ne jenom název naslouchacího procesu definovaný v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md). Pokud je definován naslouchací proces ve [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr pro tuto naslouchací proces musí být definován v tomto elementu.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<filter>` prvek přidejte filtr k naslouchacímu procesu `console` v `Listeners` kolekce pro zdroj trasování `myTraceSource`, určení úroveň filtru událostí jako `Error`.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
