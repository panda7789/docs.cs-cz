---
title: Element <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153292"
---
# <a name="source-element"></a>\<zdroj> Element
Určuje zdroj trasování, který iniciuje trasování zpráv.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<zdrojové>**

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
|`switchName`|Nepovinný atribut.<br /><br /> Určuje název instance přepínače trasování v aplikaci. Pokud přepínač není v `<switches>` prvku identifikován, hodnota určuje úroveň přepínače.|  
|`switchType`|Nepovinný atribut.<br /><br /> Určuje typ přepínače trasování. Pokud je k dispozici, musí být typ platný název třídy a nemůže být prázdný řetězec.|  
|`extraAttribute`|Nepovinný atribut.<br /><br /> Určuje hodnotu atributu specifického pro zdroj <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> trasování identifikovaného metodou pro daný zdroj trasování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<posluchači>](listeners-element-for-source.md)|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které iniciují tracing zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `<source>` pomocí prvku přidat `mySource` zdroj trasování a nastavit `sourceSwitch`úroveň pro zdrojový přepínač s názvem . Je přidán naslouchací proces trasování konzoly, který zapisuje informace o trasování do konzoly.  
  
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

- [Trasování a ladění schématu nastavení](index.md)
- [Přepínače trasování](../../../debug-trace-profile/trace-switches.md)
