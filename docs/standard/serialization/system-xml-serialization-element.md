---
title: Element <system.xml.serialization>
description: Tento článek popisuje prvek < System. XML. Serialization >, který je prvkem nejvyšší úrovně pro řízení serializace XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f69e80592e9321de64421b977a63b83d8be2ad9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289483"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="cf14b-103">Element \<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="cf14b-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="cf14b-104">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="cf14b-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="cf14b-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="cf14b-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="cf14b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf14b-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf14b-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cf14b-107">Attributes and Elements</span></span>

<span data-ttu-id="cf14b-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cf14b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf14b-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="cf14b-109">Attributes</span></span>

<span data-ttu-id="cf14b-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf14b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf14b-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cf14b-111">Child Elements</span></span>

|<span data-ttu-id="cf14b-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf14b-112">Element</span></span>|<span data-ttu-id="cf14b-113">Description</span><span class="sxs-lookup"><span data-stu-id="cf14b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf14b-114">\<dateTimeSerialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="cf14b-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="cf14b-115">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="cf14b-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="cf14b-116">\<schemaImporterExtensions>Objekt</span><span class="sxs-lookup"><span data-stu-id="cf14b-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="cf14b-117">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf14b-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cf14b-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cf14b-118">Parent Elements</span></span>

|<span data-ttu-id="cf14b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf14b-119">Element</span></span>|<span data-ttu-id="cf14b-120">Description</span><span class="sxs-lookup"><span data-stu-id="cf14b-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf14b-121">\<configuration>Objekt</span><span class="sxs-lookup"><span data-stu-id="cf14b-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="cf14b-122">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf14b-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="cf14b-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf14b-123">Example</span></span>

<span data-ttu-id="cf14b-124">Následující příklad kódu ukazuje, jak určit režim serializace <xref:System.DateTime> objekt a přidání typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf14b-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cf14b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf14b-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="cf14b-126">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="cf14b-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="cf14b-127">\<dateTimeSerialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="cf14b-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="cf14b-128">\<schemaImporterExtensions>Objekt</span><span class="sxs-lookup"><span data-stu-id="cf14b-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="cf14b-129">\<add>Element pro\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="cf14b-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
