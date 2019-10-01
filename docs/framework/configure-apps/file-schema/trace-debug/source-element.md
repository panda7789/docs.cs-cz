---
title: Element <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: c4f7e31422ccd8129599db1120f9b0cb327d9319
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697199"
---
# <a name="source-element"></a>@no__t – element > 0source
Určuje zdroj trasování, který inicializuje trasovací zprávy.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<source >**  
  
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
|`switchName`|Nepovinný atribut.<br /><br /> Určuje název instance přepínače trasování v aplikaci. Pokud není přepínač identifikován v elementu `<switches>`, hodnota určuje úroveň přepínače.|  
|`switchType`|Nepovinný atribut.<br /><br /> Určuje typ přepínače trasování. Je-li k dispozici typ, musí být platný název třídy a nemůže být prázdným řetězcem.|  
|`extraAttribute`|Nepovinný atribut.<br /><br /> Určuje hodnotu pro atribut specifický pro zdroj trasování identifikovaný metodou <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> pro tento zdroj trasování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[@no__t – 1listeners >](listeners-element-for-source.md)|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které spouštějí trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití prvku `<source>` pro přidání zdroje trasování `mySource` a nastavení úrovně pro zdrojový přepínač s názvem `sourceSwitch`. Je přidán naslouchací proces trasování konzoly, který zapisuje trasovací informace do konzoly.  
  
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
