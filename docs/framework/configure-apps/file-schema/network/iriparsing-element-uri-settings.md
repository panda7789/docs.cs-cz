---
title: "&lt;iriParsing&gt; – Element (nastavení Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6cd69df9ccba39520cca26bb7042dc2932565336
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltiriparsinggt-element-uri-settings"></a>&lt;iriParsing&gt; – Element (nastavení Uri)
Určuje, zda analýza mezinárodní prostředků identifikátor (IRI) je použita k <xref:System.Uri> a zda má být použita IRI Analýza pravidla.  
  
## <a name="schema-hierarchy"></a>Schéma hierarchie  
 [\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identifikátor URI > elementu (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing >](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
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
|`enabled`|Určuje, zda je povoleno IRI analýza. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[identifikátor URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Obsahuje nastavení, které určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).|  
  
## <a name="remarks"></a>Poznámky  
 Existující <xref:System.Uri> třída rozšířilo v rozhraní .NET Framework 3.5. 3.0 SP1 a 2.0 SP1 zajistit podporu pro mezinárodní prostředků identifikátory (IRI) a mezinárodní názvy domén (IDN). Aktuální uživatelé neuvidí žádné chování se liší od rozhraní .NET Framework 2.0, pokud konkrétně povolit IRI a IDN podporovat. Tím se zajistí kompatibilitu aplikace s předchozí verze rozhraní .NET Framework.  
  
 Povolení podpory pro IRI, je potřeba udělat následující dvě změny:  
  
1.  Přidejte následující řádek do souboru machine.config v adresáři rozhraní .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Zadejte, zda má být použita IRI Analýza pravidla. To lze provést v souboru machine.config nebo v souboru app.config.  
  
 Povolení analýza IRI (iriParsing, povoleno = `true`) provede normalizaci a znak kontrola podle nejnovější IRI pravidla v dokumentu RFC 3987. Výchozí hodnota je `false` a proveďte normalizaci a znak kontrolu podle RFC 2396 a RFC 3986 (pro literály IPv6).  
  
### <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýzy IRI a IDN. názvy.  
  
### <a name="code"></a>Kód  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
