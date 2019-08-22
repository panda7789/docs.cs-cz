---
title: <iriParsing> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 2c99edf2f1a03e0e510858c106cad43b0eaa27b4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664089"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing – element > (nastavení URI)
Určuje, jestli se <xref:System.Uri> má použít analýza mezinárodní identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.  
  
## <a name="schema-hierarchy"></a>Hierarchie schématu  
 [\<Element > Konfigurace](../configuration-element.md)  
  
 [\<Identifikátor URI > – element (nastavení URI)](uri-element-uri-settings.md)  
  
 [\<iriParsing>](iriparsing-element-uri-settings.md)  
  
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
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[identifikátor URI](uri-element-uri-settings.md)|Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).|  
  
## <a name="remarks"></a>Poznámky  
 Existující <xref:System.Uri> třída se rozšířila v .NET Framework 3,5. 3,0 SP1 a 2,0 SP1 pro poskytování podpory pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN). Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN. Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.  
  
 Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:  
  
1. Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Určete, jestli se mají použít pravidla analýzy IRI. To lze provést v souboru Machine. config nebo v souboru App. config.  
  
 Povolení analýzy IRI (IriParsing Enabled = `true`) provede normalizaci a kontrolu znaku podle nejnovějších pravidel IRI v dokumentu RFC 3987. Výchozí hodnota je `false` a provede normalizaci a kontrolu znaku podle RFC 2396 a RFC 3986 (pro literály IPv6).  
  
### <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfiguraci, kterou <xref:System.Uri> třída používá pro podporu IRIch analýz a názvů IDN.  
  
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
- [Schéma nastavení sítě](index.md)
