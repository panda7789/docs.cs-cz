---
title: <filter>Prvek <add> pro pro<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153450"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<filtr> \<Element pro \<přidání> pro> sharedListeners
Přidá filtr do naslouchací proces v kolekci. `sharedListeners`  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtru**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Typ**|Požadovaný atribut.<br /><br /> Určuje typ filtru. Můžete použít pouze úplný název typu (ve formátu <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnosti), nebo můžete použít plně kvalifikovaný název typu včetně <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> informací o sestavení (ve formátu vlastnosti). Informace o vytvoření plně kvalifikovaného názvu typu naleznete [v tématu Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**inicializovatData**|Nepovinný atribut.<br /><br /> Řetězec předán konstruktoru pro zadanou třídu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
|`sharedListeners`|Kolekce naslouchacích procesy, které může odkazovat libovolný zdroj nebo prvek trasování.|  
|`add`|Přidá naslouchací proces do kolekce **sharedListeners.**|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je definován `<add>` naslouchací proces v prvku `<sharedListeners>` prvku, `<filter>` filtr pro tento naslouchací proces by měl být definován v elementu, který je podřízeným `<add>` prvkem prvku.  
  
 Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `<filter>` použít prvek k přidání `console` filtru `sharedListeners` do naslouchací proces trasování v kolekci.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [Trasování a ladění schématu nastavení](index.md)
