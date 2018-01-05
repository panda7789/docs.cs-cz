---
title: "&lt;Zdroj&gt; – Element"
ms.date: 09/29/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d6c5c65be8a540fdbba64d5a604c0963f9797e0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsourcegt-element"></a>&lt;Zdroj&gt; – Element
Určuje zdroj trasování, který iniciuje trasování zpráv.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<zdroje >  
\<zdroj >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Nepovinný atribut.<br /><br /> Určuje název zdroje trasování.|  
|`switchName`|Nepovinný atribut.<br /><br /> Určuje název instance přepínače trasování v aplikaci. Pokud přepínač není v identifikovat `<switches>` elementu, hodnota určuje úroveň přepínače.|  
|`switchType`|Nepovinný atribut.<br /><br /> Určuje typ přepínače trasování. Pokud je k dispozici, typ musí být platný název třídy a nemůže být prázdný řetězec.|  
|`extraAttribute`|Nepovinný atribut.<br /><br /> Určuje hodnotu pro atribut konkrétní zdroj trasování identifikovaný <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodu pro tento zdroj trasování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<moduly pro naslouchání >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Obsahuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
|`sources`|Obsahuje trasování zdrojů, které zahájí trasování zpráv.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<source>` elementu, který chcete přidat zdroj trasování `mySource` a nastaví úroveň přepínač zdroje s názvem `sourceSwitch`. Naslouchací proces trasování konzoly je přidaná který informace trasování zapíše do konzoly.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Přepínače trasování](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
