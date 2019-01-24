---
title: '&lt;iriParsing&gt; – Element (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: ca8fc86b5b64b971e54eec8f7338010394b73239
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552941"
---
# <a name="ltiriparsinggt-element-uri-settings"></a>&lt;iriParsing&gt; – Element (nastavení Uri)
Určuje, pokud analýze International Resource Identifier (IRI) se použije k <xref:System.Uri> a určuje, zda by měl použít IRI pravidel pro analýzu.  
  
## <a name="schema-hierarchy"></a>Schema Hierarchy  
 [\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identifikátor URI > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|`enabled`|Určuje, zda je povolena analýza IRI. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).|  
  
## <a name="remarks"></a>Poznámky  
 Existující <xref:System.Uri> bylo rozšířeno třídy v rozhraní .NET Framework 3.5. 3.0 SP1 a 2.0 SP1 pro poskytnutí podpory pro mezinárodní prostředků identifikátory (IRI) a mezinárodní názvy domén (IDN). Aktuální uživatelé neuvidí žádné změny v chování rozhraní .NET Framework 2.0, pokud výslovně povolit IRI a IDN podporovat. Tím se zajistí kompatibilitu aplikací se staršími verzemi rozhraní .NET Framework.  
  
 Povolení podpory pro IRI, jsou požadovány následující dvě změny:  
  
1.  Přidejte následující řádek do souboru machine.config, v adresáři rozhraní .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Určete, zda má být použita IRI pravidel pro analýzu. To můžete udělat v souboru machine.config nebo v souboru app.config.  
  
 Povolení analýza IRI (iriParsing, povoleno = `true`) provede normalizaci a znak kontroly podle nejnovějších IRI pravidla v dokumentu RFC 3987. Výchozí hodnota je `false` a proveďte normalizace a znak kontroly podle RFC 2396 a RFC 3986 (pro literály IPv6).  
  
### <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýza IRI a názvy IDN.  
  
### <a name="code"></a>Kód  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
