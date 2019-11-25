---
title: <remove> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089153"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a>\<odebrat element > pro schemeSettings (nastavení URI)
Odebere nastavení schématu pro název schématu.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<identifikátor uri >** ](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Název schématu, pro který platí toto nastavení. Jediné podporované hodnoty jsou Name = "http" a Name = "https".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<element > schemeSettings (nastavení URI)](schemesettings-element-uri-settings.md)|Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.|  
  
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
 Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri>, která odebere všechna nastavení schématu pro schéma HTTP.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
