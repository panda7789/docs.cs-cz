---
title: Element <dateTimeSerialization>
description: Tento článek popisuje <dateTimeSerialization> prvek, který určuje režim serializace objektů typu DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289639"
---
# <a name="datetimeserialization-element"></a>Element \<dateTimeSerialization>
Určuje režim serializace <xref:System.DateTime> objekty.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atributy|Description|  
|----------------|-----------------|  
|`mode`|Nepovinný parametr. Určuje režim serializace. Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty. Výchozí hodnota je **zpáteční**.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|System.XML.Serialization|Element nejvyšší úrovně pro řízení serializace XML.|  
  
## <a name="remarks"></a>Poznámky  
 V verzích 1,0, 1,1, 2,0 a novějších .NET Framework platí, že pokud je tato vlastnost nastavena na **místní**, <xref:System.DateTime> objekty jsou vždy formátovány jako místní čas. Informace o zóně Místní čas je vždy součástí serializovaná data. Nastavte tuto vlastnost na **místní** , aby se zajistila kompatibilita se staršími verzemi .NET Framework.  
  
 Ve verzi 2,0 a novějších .NET Framework, které mají tuto vlastnost nastavenou na hodnotu **zpětného převodu**, <xref:System.DateTime> jsou zkontrolovány objekty za účelem zjištění, zda jsou v místním, UTC nebo neurčeném časovém pásmu. <xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno. Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.  
  
## <a name="see-also"></a>Viz také

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schéma konfiguračního souboru](../../framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions>Objekt](schemaimporterextensions-element.md)
- [\<add>Element pro\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization>Objekt](system-xml-serialization-element.md)
