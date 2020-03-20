---
title: <schemeSettings> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154644"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeNastavení> elementu (Nastavení uri)
Určuje, jak <xref:System.Uri> bude analýza pro konkrétní schémata.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeNastavení>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádný  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Přidat](add-element-for-schemesettings-uri-settings.md)|Přidá nastavení schématu pro název schématu.|  
|[Jasné](clear-element-for-schemesettings-uri-settings.md)|Vymaže všechna existující nastavení schématu.|  
|[Odebrat](remove-element-for-schemesettings-uri-settings.md)|Odebere nastavení schématu pro název schématu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Uri](uri-element-uri-settings.md)|Obsahuje nastavení, která určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů jednotného prostředku (URI).|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím <xref:System.Uri?displayProperty=nameWithType> nastavení třída un-escapes procent procent kódované cesty oddělovače před spuštěním komprese cesty. To to bylo implementováno jako mechanismus zabezpečení proti útokům, jako je následující:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Pokud tento identifikátor URI bude předán modulům, které nezpracovávají méně kódované znaky, může dojít k provedení následujícího příkazu serverem:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Z tohoto <xref:System.Uri?displayProperty=nameWithType> důvodu třída první un-escapes oddělovače cesty a potom použije kompresi cesty. Výsledkem předání výše uvedené <xref:System.Uri?displayProperty=nameWithType> škodlivé adresy URL konstruktoru třídy je výsledkem následující identifikátor URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Toto výchozí chování lze upravit tak, aby neodcházaly procentově kódované oddělovače cest pomocí možnosti konfigurace schemeSettings pro určité schéma.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje konfiguraci <xref:System.Uri> používanou třídou pro podporu neunikající oddělovače cest kódovaných procenty pro schéma http.  
  
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
|Obor názvů|Systémový|  
|Název schématu||  
|Ověřovací soubor||  
|Může být prázdný||  
  
## <a name="see-also"></a>Viz také

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
