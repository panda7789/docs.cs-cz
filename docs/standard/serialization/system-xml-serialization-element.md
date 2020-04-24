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
# <a name="systemxmlserialization-element"></a><span data-ttu-id="9ef71-102">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="9ef71-102">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="9ef71-103">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="9ef71-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="9ef71-104">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ef71-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="9ef71-105">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="9ef71-105">\<configuration></span></span>\
<span data-ttu-id="9ef71-106">\<System. XML. Serialization –></span><span class="sxs-lookup"><span data-stu-id="9ef71-106">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="9ef71-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ef71-107">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ef71-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9ef71-108">Attributes and Elements</span></span>

<span data-ttu-id="9ef71-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9ef71-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ef71-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9ef71-110">Attributes</span></span>

<span data-ttu-id="9ef71-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="9ef71-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ef71-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9ef71-112">Child Elements</span></span>

|<span data-ttu-id="9ef71-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="9ef71-113">Element</span></span>|<span data-ttu-id="9ef71-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9ef71-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ef71-115">\<dateTimeSerialization – element></span><span class="sxs-lookup"><span data-stu-id="9ef71-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="9ef71-116">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="9ef71-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="9ef71-117">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="9ef71-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="9ef71-118">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ef71-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9ef71-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9ef71-119">Parent Elements</span></span>

|<span data-ttu-id="9ef71-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9ef71-120">Element</span></span>|<span data-ttu-id="9ef71-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9ef71-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ef71-122">\<Element> konfigurace</span><span class="sxs-lookup"><span data-stu-id="9ef71-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="9ef71-123">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ef71-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="9ef71-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ef71-124">Example</span></span>

<span data-ttu-id="9ef71-125">Následující příklad kódu ukazuje, jak určit režim serializace <xref:System.DateTime> objekt a přidání typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ef71-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9ef71-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ef71-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="9ef71-127">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9ef71-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="9ef71-128">\<dateTimeSerialization – element></span><span class="sxs-lookup"><span data-stu-id="9ef71-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="9ef71-129">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="9ef71-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="9ef71-130">\<Přidat> element pro \<>schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="9ef71-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
