---
title: Element <dateTimeSerialization>
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459260"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization – element>
Určuje režim serializace <xref:System.DateTime> objekty.  
  
 \<> konfigurace  
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
  
|Atributy|Popis|  
|----------------|-----------------|  
|`mode`|Nepovinný parametr. Určuje režim serializace. Nastavte na jednu z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> hodnoty. Výchozí hodnota je **zpáteční**.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|System.XML.Serialization|Element nejvyšší úrovně pro řízení serializace XML.|  
  
## <a name="remarks"></a>Poznámky  
 V verzích 1,0, 1,1, 2,0 a novějších .NET Framework platí, že pokud je tato vlastnost nastavena na **místní**, <xref:System.DateTime> objekty jsou vždy formátovány jako místní čas. Informace o zóně Místní čas je vždy součástí serializovaná data. Nastavte tuto vlastnost na **místní** , aby se zajistila kompatibilita se staršími verzemi .NET Framework.  
  
 Ve verzi 2,0 a novějších .NET Framework, které mají tuto vlastnost nastavenou na hodnotu **zpětného převodu**, <xref:System.DateTime> jsou zkontrolovány objekty za účelem zjištění, zda jsou v místním, UTC nebo neurčeném časovém pásmu. <xref:System.DateTime> Objekty jsou pak serializován tak, že tyto informace je zachováno. Toto je výchozí chování a je doporučené chování pro všechny nové aplikace, které nekomunikují ve starších verzích rozhraní.  
  
## <a name="see-also"></a>Viz také

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions – element>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<Přidat> element pro \<>schemaImporterExtensions](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<System. XML. Serialization – element>](../../../docs/standard/serialization/system-xml-serialization-element.md)
