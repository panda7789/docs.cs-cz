---
title: Element <schemaImporterExtensions>
description: <schemaImporterExtensions>Element obsahuje typy, které jsou používány XmlSchemaImporter pro mapování typů XSD na .NET Framework typy.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c46c5cb6e01463723f0f2ce3873fb4a6ec0b4e60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84278399"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="671b1-103">Element \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="671b1-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="671b1-104">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="671b1-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="671b1-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="671b1-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="671b1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="671b1-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="671b1-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="671b1-107">Child Elements</span></span>  
  
|<span data-ttu-id="671b1-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="671b1-108">Element</span></span>|<span data-ttu-id="671b1-109">Description</span><span class="sxs-lookup"><span data-stu-id="671b1-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="671b1-110">\<add>Element pro\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="671b1-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="671b1-111">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> k vytvoření mapování.</span><span class="sxs-lookup"><span data-stu-id="671b1-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="671b1-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="671b1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="671b1-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="671b1-113">Element</span></span>|<span data-ttu-id="671b1-114">Description</span><span class="sxs-lookup"><span data-stu-id="671b1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="671b1-115">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="671b1-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="671b1-116">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="671b1-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="671b1-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="671b1-117">Example</span></span>  
 <span data-ttu-id="671b1-118">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="671b1-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="671b1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="671b1-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="671b1-120">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="671b1-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="671b1-121">\<dateTimeSerialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="671b1-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="671b1-122">\<add>Element pro\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="671b1-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="671b1-123">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="671b1-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
