---
title: "&lt;dateTimeSerialization&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd6dda1f26e44c4864d5afea1427b2580ac1ed10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatetimeserializationgt-element"></a>&lt;dateTimeSerialization&gt; – Element
Určuje režim serializace <xref:System.DateTime> objekty.  
  
 \<Konfigurace >  
\<dateTimeSerialization >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atributy|Popis|  
|----------------|-----------------|  
|`mode`|Volitelné. Určuje režim serializace. Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty. Výchozí hodnota je **umožňujícím zpětnou transformaci**.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|System.XML.Serialization|Element nejvyšší úrovně pro řízení serializace XML.|  
  
## <a name="remarks"></a>Poznámky  
 Verze 1.0, 1.1, 2.0 nebo novější verze rozhraní .NET Framework, když je tato vlastnost nastavena na **místní**, <xref:System.DateTime> objekty jsou vždy formátovaný jako místní čas. Informace o zóně Místní čas je vždy součástí serializovaná data. Tuto vlastnost nastavit na **místní** pro zajištění kompatibility s starší verze rozhraní .NET Framework.  
  
 Ve verzi 2.0 a novější verze rozhraní .NET Framework, které mají tuto vlastnost nastavit na **umožňujícím zpětnou transformaci**, <xref:System.DateTime> objekty jsou prověřit, abyste zjistili, jestli jsou v místní, UTC nebo neurčené časové pásmo. <xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno. Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<schemaImporterExtensions > elementu](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<Přidat > elementu pro \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [\<System.XML.Serialization > elementu](../../../docs/standard/serialization/system-xml-serialization-element.md)
