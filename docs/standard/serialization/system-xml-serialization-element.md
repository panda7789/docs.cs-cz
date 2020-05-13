---
title: Element <system.xml.serialization>
description: Tento článek popisuje prvek <System. XML. Serialization>, který je prvkem nejvyšší úrovně pro řízení serializace XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 1e66220004d561f937d03c506e6f30db4ccc635b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380119"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="ec226-103">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="ec226-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="ec226-104">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="ec226-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="ec226-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec226-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="ec226-106">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="ec226-106">\<configuration></span></span>\
<span data-ttu-id="ec226-107">\<System. XML. Serialization –></span><span class="sxs-lookup"><span data-stu-id="ec226-107">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="ec226-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec226-108">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec226-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec226-109">Attributes and Elements</span></span>

<span data-ttu-id="ec226-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec226-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec226-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec226-111">Attributes</span></span>

<span data-ttu-id="ec226-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec226-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec226-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec226-113">Child Elements</span></span>

|<span data-ttu-id="ec226-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec226-114">Element</span></span>|<span data-ttu-id="ec226-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ec226-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec226-116">\<dateTimeSerialization – element></span><span class="sxs-lookup"><span data-stu-id="ec226-116">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="ec226-117">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="ec226-117">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="ec226-118">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="ec226-118">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="ec226-119">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec226-119">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ec226-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec226-120">Parent Elements</span></span>

|<span data-ttu-id="ec226-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec226-121">Element</span></span>|<span data-ttu-id="ec226-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ec226-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec226-123">\<Element> konfigurace</span><span class="sxs-lookup"><span data-stu-id="ec226-123">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ec226-124">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec226-124">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="ec226-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec226-125">Example</span></span>

<span data-ttu-id="ec226-126">Následující příklad kódu ukazuje, jak určit režim serializace <xref:System.DateTime> objekt a přidání typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec226-126">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec226-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec226-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="ec226-128">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ec226-128">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ec226-129">\<dateTimeSerialization – element></span><span class="sxs-lookup"><span data-stu-id="ec226-129">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="ec226-130">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="ec226-130">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="ec226-131">\<Přidat> element pro \<>schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="ec226-131">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
