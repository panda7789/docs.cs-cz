---
title: Element <system.xml.serialization>
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410550"
---
# <a name="systemxmlserialization-element"></a>\<System. XML. Serialization – element>

Element nejvyšší úrovně pro řízení serializace XML. Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).

\<> Konfigurace \
\<System. XML. Serialization –>

## <a name="syntax"></a>Syntaxe

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné.

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<dateTimeSerialization – element>](../../../docs/standard/serialization/datetimeserialization-element.md)|Určuje režim serializace <xref:System.DateTime> objekty.|
|[\<schemaImporterExtensions – element>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[\<Element> konfigurace](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|

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
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization – element>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<schemaImporterExtensions – element>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<Přidat> element pro \<>schemaImporterExtensions](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
