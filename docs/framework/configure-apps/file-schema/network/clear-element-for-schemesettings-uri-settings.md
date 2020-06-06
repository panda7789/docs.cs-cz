---
title: <clear> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 90035c1c9ccdb8ac888aec84e506ccde41748c9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087447"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a>\<clear> – element pro schemeSettings (nastavení URI)
Vymaže všechna existující nastavení schématu.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<schemeSettings>– Element (nastavení URI)](schemesettings-element-uri-settings.md)|Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty. Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty. Výsledek předání škodlivou adresu URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktoru třídy má za následek následující identifikátor URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou, která vymaže všechna nastavení schématu, a potom přidá podporu pro nekódované oddělovače cest pro schéma HTTP v procentech.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
