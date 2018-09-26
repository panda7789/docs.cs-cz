---
title: '&lt;Identifikátor URI&gt; – Element (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a58c27500c0258415c12a5fd8e552b3ee43f50e8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108907"
---
# <a name="lturigt-element-uri-settings"></a>&lt;Identifikátor URI&gt; – Element (nastavení Uri)
Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).  
  
## <a name="schema-hierarchy"></a>Hierarchie schémat  
 [\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<identifikátor URI >](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[IDN](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Určuje, pokud analýza mezinárodních názvů domén (IDN) platí pro názvy domén.|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Určuje, pokud analýze International Resource Identifier (IRI) se použije k <xref:System.Uri> a určuje, zda by měl použít IRI pravidel pro analýzu.|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Konfigurace](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Obsahuje nastavení pro všechny obory názvů.|  
  
## <a name="remarks"></a>Poznámky  
 `uri` Element obsahuje nastavení pro členy programu <xref:System.Uri> třídy používané třídami oboru <xref:System.Net> oboru názvů. Nastavení konfigurace podpory pro IRI a IDN.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýza IRI a názvy IDN. V příkladu rovněž vymaže všechna nastavení schéma a pak přidává podporu pro není uvozovací znaky oddělovače procentuálně zakódovaný cestu pro schéma protokolu http.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
