---
title: "&lt;Identifikátor URI&gt; – Element (nastavení Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 735a6596b22e6d6fdcff776dd79224230db5b7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lturigt-element-uri-settings"></a>&lt;Identifikátor URI&gt; – Element (nastavení Uri)
Obsahuje nastavení, které určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).  
  
## <a name="schema-hierarchy"></a>Schéma hierarchie  
 [\<Konfigurace > elementu](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
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
|[IDN.](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Určuje, pokud analýza mezinárodní název domény (IDN) se použijí pro názvy domén.|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Určuje, pokud analýza mezinárodní prostředků identifikátor (IRI) se použijí pro <xref:System.Uri> a zda má být použita IRI Analýza pravidla.|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Určuje, jak <xref:System.Uri> bude analyzovat pro konkrétní schémat.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Konfigurace](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Obsahuje nastavení pro všechny obory názvů.|  
  
## <a name="remarks"></a>Poznámky  
 `uri` Element obsahuje nastavení pro členy <xref:System.Uri> třídy používané třídy v <xref:System.Net> oboru názvů. Nastavení konfigurace podpory pro IRI a IDN.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýzy IRI a IDN. názvy. V příkladu rovněž vymaže všechna nastavení schéma a pak přidává podporu pro není uvozovací znaky oddělovače kódováním procent cestu pro schéma protokolu http.  
  
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
