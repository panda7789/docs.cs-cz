---
title: Element <schemaImporterExtensions>
description: <schemaImporterExtensions>Element obsahuje typy, které jsou používány XmlSchemaImporter pro mapování typů XSD na .NET Framework typy.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379793"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="e9b9d-103">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="e9b9d-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="e9b9d-104">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9b9d-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="e9b9d-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9b9d-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9b9d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9b9d-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="e9b9d-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e9b9d-107">Child Elements</span></span>  
  
|<span data-ttu-id="e9b9d-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9b9d-108">Element</span></span>|<span data-ttu-id="e9b9d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e9b9d-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9b9d-110">\<Přidat> element pro \<>schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="e9b9d-110">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="e9b9d-111">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> k vytvoření mapování.</span><span class="sxs-lookup"><span data-stu-id="e9b9d-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="e9b9d-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e9b9d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e9b9d-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9b9d-113">Element</span></span>|<span data-ttu-id="e9b9d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e9b9d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9b9d-115">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="e9b9d-115">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="e9b9d-116">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="e9b9d-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9b9d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9b9d-117">Example</span></span>  
 <span data-ttu-id="e9b9d-118">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9b9d-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9b9d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9b9d-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="e9b9d-120">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e9b9d-120">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="e9b9d-121">\<dateTimeSerialization – element></span><span class="sxs-lookup"><span data-stu-id="e9b9d-121">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="e9b9d-122">\<Přidat> element pro \<>schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="e9b9d-122">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="e9b9d-123">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="e9b9d-123">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
