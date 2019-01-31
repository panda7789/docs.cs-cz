---
title: Element <dateTimeSerialization>
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: af0d8eeb36e023b4d38f9ad5831de3d392a487fd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288259"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization > – Element
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
 Ve verzích 1.0 a 1.1, 2.0 a novějších verzích rozhraní .NET Framework, když je tato vlastnost nastavená na **místní**, <xref:System.DateTime> objekty jsou vždy formátována jako místní čas. Informace o zóně Místní čas je vždy součástí serializovaná data. Tuto vlastnost nastavte na **místní** k zajištění kompatibility se staršími verzemi rozhraní .NET Framework.  
  
 Ve verzi 2.0 a novějších verzích rozhraní .NET Framework, které mají tato vlastnost nastavena na **umožňujícím zpětnou transformaci**, <xref:System.DateTime> objekty jsou prověřit, abyste zjistili, jestli jsou v místním, UTC nebo nespecifikované časového pásma. <xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno. Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<Přidat > – Element pro \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)
