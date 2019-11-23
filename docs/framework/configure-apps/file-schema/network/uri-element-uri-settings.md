---
title: <uri> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697443"
---
# <a name="uri-element-uri-settings"></a>\<element > identifikátoru URI (nastavení URI)
Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).  
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<uri >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[IDN](idn-element-uri-settings.md)|Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).|  
|[iriParsing](iriparsing-element-uri-settings.md)|Určuje, jestli se má u <xref:System.Uri> použít analýza mezinárodního identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[rozšířeného](../configuration-element.md)|Obsahuje nastavení pro všechny obory názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Element `uri` obsahuje nastavení pro členy třídy <xref:System.Uri> používané třídami v oboru názvů <xref:System.Net>. Nastavení konfigurují podporu pro IRI a IDN.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu IRIch analýz a názvů IDN. Tento příklad také vymaže všechna nastavení schématu a pak přidá podporu pro nekódované oddělovače cest v procentech pro schéma HTTP.  
  
### <a name="code"></a>Kód  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení sítě](index.md)
