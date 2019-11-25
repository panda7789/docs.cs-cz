---
title: Element <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: b59144f4772c940f8c7e6ca19aa21666069b4b55
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088821"
---
# <a name="source-element"></a>zdrojový > elementu \<
Určuje zdroj trasování, který inicializuje trasovací zprávy.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdrojů >** ](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zdroj >**

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
|`switchName`|Nepovinný atribut.<br /><br /> Určuje název instance přepínače trasování v aplikaci. Pokud není přepínač identifikován v prvku `<switches>`, hodnota určuje úroveň přepínače.|  
|`switchType`|Nepovinný atribut.<br /><br /> Určuje typ přepínače trasování. Je-li k dispozici typ, musí být platný název třídy a nemůže být prázdným řetězcem.|  
|`extraAttribute`|Nepovinný atribut.<br /><br /> Určuje hodnotu pro atribut specifický pro zdroj trasování identifikovaný metodou <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> pro daný zdroj trasování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[naslouchací procesy \<](listeners-element-for-source.md)|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které spouštějí trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít element `<source>` k přidání `mySource` zdroje trasování a k nastavení úrovně pro zdrojový přepínač s názvem `sourceSwitch`. Je přidán naslouchací proces trasování konzoly, který zapisuje trasovací informace do konzoly.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Trasování a ladění schématu nastavení](index.md)
- [Přepínače trasování](../../../debug-trace-profile/trace-switches.md)
