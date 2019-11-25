---
title: Element <filter> pro <add> <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: cc970240ac07ad3ea72be50d1e9af452da638fa9
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088895"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<filtr > elementu \<přidat > pro \<naslouchací procesy > pro \<trasování >
Přidá filtr do naslouchacího procesu v kolekci `Listeners` pro trasování.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trace >** ](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<naslouchacího procesu >** ](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<přidat >** ](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtr >**

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
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
|`listeners`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
|`add`|Přidá naslouchací proces do kolekce `Listeners`.|  
  
## <a name="remarks"></a>Poznámky  
 Element `<filter>` musí být obsažen v elementu `<add>` pro naslouchací proces trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného ve [\<sharedListeners >](sharedlisteners-element.md). Pokud je naslouchací proces definován ve [\<sharedListeners >](sharedlisteners-element.md), musí být v tomto elementu definován filtr pro tento naslouchací proces.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do `console` naslouchacího procesu v kolekci `Listeners` pro trasování, určení úrovně události filtru jako `Error`.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Trasování a ladění schématu nastavení](index.md)
