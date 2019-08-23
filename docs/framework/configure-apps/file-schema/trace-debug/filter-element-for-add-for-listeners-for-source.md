---
title: <filter><add> Element<listeners> pro pro pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0d25d0b955a94986147922914068c8a1cf2d96c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920523"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<> element Filter elementu \<Add > for \<Listeners > \<for Source >
Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.  
  
 \<> Konfigurace  
\<system.diagnostics>  
\<> zdrojů  
\<> zdroje  
\<> naslouchací proces  
\<add>  
\<Filtrovat >  
  
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
|`type`|Požadovaný atribut.<br /><br /> Určuje typ filtru, který by měl dědit z <xref:System.Diagnostics.TraceFilter> třídy. Můžete použít název kvalifikovaný obor názvů typu, který odpovídá <xref:System.Type.FullName%2A> vlastnosti typu, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, které odpovídají <xref:System.Type.AssemblyQualifiedName%2A> vlastnosti. Informace o plně kvalifikovaných názvech typů naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro určenou třídu filtru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které spouštějí trasovací zprávy.|  
|`source`|Určuje zdroj trasování, který inicializuje trasovací zprávy.|  
|`listeners`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
|`add`|Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Element musí být obsažen `<add>` v elementu pro naslouchací proces zdroje trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného v [ \<> sharedListeners.](sharedlisteners-element.md) `<filter>` Pokud je naslouchací proces definován v [ \<> sharedListeners](sharedlisteners-element.md), filtr pro tento naslouchací proces musí být definován v tomto elementu.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do naslouchacího procesu `console` v `Listeners` kolekci pro zdroj `myTraceSource`trasování a určení úrovně události filtru jako `Error`.  
  
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
- [Trasování a ladění schématu nastavení](index.md)
