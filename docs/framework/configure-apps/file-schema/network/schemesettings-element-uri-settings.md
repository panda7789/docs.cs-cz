---
title: <schemeSettings> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 498aef77a1dfd8cffcac73b704b8d1bb6df5d165
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697759"
---
# <a name="schemesettings-element-uri-settings"></a>\<element > schemeSettings (nastavení URI)
Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.  
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<schemeSettings >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[add](add-element-for-schemesettings-uri-settings.md)|Přidá nastavení schématu pro název schématu.|  
|[jejich](clear-element-for-schemesettings-uri-settings.md)|Vymaže všechna existující nastavení schématu.|  
|[remove](remove-element-for-schemesettings-uri-settings.md)|Odebere nastavení schématu pro název schématu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[identifikátor URI](uri-element-uri-settings.md)|Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení třída <xref:System.Uri?displayProperty=nameWithType> před spuštěním komprimace cesty vymění v procentech zakódovaných oddělovačů cest. Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třída nejprve zruší oddělovače cest a pak použije kompresi cesty. Výsledek předání škodlivých adres URL výše do konstruktoru <xref:System.Uri?displayProperty=nameWithType> třídy vede k následujícímu identifikátoru URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu nekódovaných oddělovačů cest pro schéma HTTP v procentech.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>Informace o elementu  
  
|||
|-|-|  
|Obor názvů|Systém|  
|Název schématu||  
|Soubor ověření||  
|Může být prázdné||  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
