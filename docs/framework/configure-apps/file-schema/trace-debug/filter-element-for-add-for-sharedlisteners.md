---
title: '&lt;Filtr&gt; – Element pro &lt;přidat&gt; pro &lt;sharedListeners&gt;'
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
ms.openlocfilehash: a811d2ae8112bb1ab9386510fc8435d00f454f85
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083792"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a>&lt;Filtr&gt; – Element pro &lt;přidat&gt; pro &lt;sharedListeners&gt;
Přidá filtr do naslouchacího procesu v `sharedListeners` kolekce.  
  
 \<Konfigurace >  
\<system.diagnostics>  
\<sharedListeners > – Element  
\<add>  
\<Filtr >  
  
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
|**type**|Požadovaný atribut.<br /><br /> Určuje typ filtru. Můžete použít pouze úplný název typu (ve formátu <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost), nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení (ve formátu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> vlastnost). Informace o vytvoření plně kvalifikovaného názvu typu, najdete v tématu [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro zadanou třídu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sharedListeners`|Kolekce naslouchacích procesů, které všechny zdroje nebo trasování – element může odkazovat.|  
|`add`|Přidá naslouchací proces pro **sharedListeners** kolekce.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud naslouchací proces je definována v `<add>` elementu `<sharedListeners>` elementu, filtr pro tuto naslouchací proces musí být definován v `<filter>` element, který je podřízeným prvkem `<add>` elementu.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<filter>` prvek, který chcete přidat filtr na naslouchací proces trasování `console` v `sharedListeners` kolekce.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
