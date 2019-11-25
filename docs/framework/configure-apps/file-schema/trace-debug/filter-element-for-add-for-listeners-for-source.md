---
title: Element <filter> pro <add> <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 766088b8a26ce3218031df74b193658ba8024280
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088908"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<filtr > elementu \<přidat > pro \<naslouchací procesy > pro \<zdrojového >
Přidá filtr do naslouchacího procesu v kolekci `Listeners` pro zdroj trasování.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdrojů >** ](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdroj >** ](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Listeners**](listeners-element-for-source.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<přidat >** ](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtr >**

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
|`type`|Požadovaný atribut.<br /><br /> Určuje typ filtru, který by měl dědit z třídy <xref:System.Diagnostics.TraceFilter>. Můžete použít název kvalifikovaný obor názvů typu, který odpovídá vlastnosti <xref:System.Type.FullName%2A> typu, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, který odpovídá vlastnosti <xref:System.Type.AssemblyQualifiedName%2A>. Informace o plně kvalifikovaných názvech typů naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
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
|`add`|Přidá naslouchací proces do kolekce `Listeners` pro zdroj trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Element `<filter>` musí být obsažen v elementu `<add>` pro naslouchací proces zdroje trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného v [\<ch sharedListeners >](sharedlisteners-element.md). Pokud je naslouchací proces definován ve [\<sharedListeners >](sharedlisteners-element.md), musí být v tomto elementu definován filtr pro tento naslouchací proces.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do `console` naslouchacího procesu v kolekci `Listeners` pro `myTraceSource`zdroj trasování a určení úrovně události filtru jako `Error`.  
  
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
