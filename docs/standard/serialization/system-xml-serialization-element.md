---
title: "&lt;System.XML.Serialization&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d70879d5e0a579af7b5c507910d4dcb19ddee52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemxmlserializationgt-element"></a>&lt;System.XML.Serialization&gt; – Element
Element nejvyšší úrovně pro řízení serializace XML. Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<Konfigurace >  
\<System.XML.Serialization >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<dateTimeSerialization > elementu](../../../docs/standard/serialization/datetimeserialization-element.md)|Určuje režim serializace <xref:System.DateTime> objekty.|  
|[\<schemaImporterExtensions > elementu](../../../docs/standard/serialization/schemaimporterextensions-element.md)|Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace > elementu](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak určit režim serializace <xref:System.DateTime> objekt a přidání typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<dateTimeSerialization > elementu](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [\<schemaImporterExtensions > elementu](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<Přidat > elementu pro \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)
