---
title: <iriParsing> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698092"
---
# <a name="iriparsing-element-uri-settings"></a>\<element > iriParsing (nastavení URI)
Určuje, jestli se má u <xref:System.Uri> použít analýza mezinárodního identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.  
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<iriParsing >**  
  
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
 Existující třída <xref:System.Uri> byla rozšířena v .NET Framework 3,5. 3,0 SP1 a 2,0 SP1 pro poskytování podpory pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN). Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN. Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.  
  
 Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:  
  
1. Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Určete, jestli se mají použít pravidla analýzy IRI. To lze provést v souboru Machine. config nebo v souboru App. config.  
  
 Povolení analýzy IRI (iriParsing Enabled = `true`) provede normalizaci a kontrolu znaku podle nejnovějších pravidel IRI v dokumentu RFC 3987. Výchozí hodnota je `false` a provede normalizaci a kontrolu znaku podle RFC 2396 a RFC 3986 (pro literály IPv6).  
  
### <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu IRIch analýz a názvů IDN.  
  
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
