---
title: <add> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: efd52557ea8b617a39e685ff8ad69bab01322a7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699597"
---
# <a name="add-element-for-schemesettings-uri-settings"></a>@no__t – element > 0add pro schemeSettings (nastavení URI)
Přidá nastavení schématu pro název schématu.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Název schématu, pro který platí toto nastavení. Jediné podporované hodnoty jsou Name = "http" a Name = "https".|  
  
## <a name="attribute-name-attribute"></a>{Název atributu} Přidělen  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|genericUriParserOptions|Možnosti analyzátoru pro toto schéma. Jediná podporovaná hodnota je genericUriParserOptions = "DontUnescapePathDotsAndSlashes".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[@no__t – element > 1schemeSettings (nastavení URI)](schemesettings-element-uri-settings.md)|Určuje, jak se bude pro konkrétní schémata analyzovat <xref:System.Uri>.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení třídy <xref:System.Uri?displayProperty=nameWithType> zruší řídicí oddělovače% zakódovaných cest před spuštěním komprese cesty. Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tohoto důvodu třída <xref:System.Uri?displayProperty=nameWithType> nejprve zruší oddělovače cest a pak použije kompresi cesty. Výsledek předání škodlivých adres URL výše do konstruktoru třídy <xref:System.Uri?displayProperty=nameWithType> vede k následujícímu identifikátoru URI:  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
