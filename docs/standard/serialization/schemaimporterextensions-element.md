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
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278399"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="8c99c-103">Element \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="8c99c-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="8c99c-104">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c99c-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="8c99c-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c99c-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c99c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c99c-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="8c99c-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c99c-107">Child Elements</span></span>  
  
|<span data-ttu-id="8c99c-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c99c-108">Element</span></span>|<span data-ttu-id="8c99c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8c99c-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c99c-110">\<add>Element pro\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="8c99c-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="8c99c-111">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> k vytvoření mapování.</span><span class="sxs-lookup"><span data-stu-id="8c99c-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="8c99c-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c99c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8c99c-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c99c-113">Element</span></span>|<span data-ttu-id="8c99c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8c99c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c99c-115">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="8c99c-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="8c99c-116">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="8c99c-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8c99c-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c99c-117">Example</span></span>  
 <span data-ttu-id="8c99c-118">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c99c-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c99c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c99c-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="8c99c-120">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8c99c-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="8c99c-121">\<dateTimeSerialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="8c99c-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="8c99c-122">\<add>Element pro\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="8c99c-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="8c99c-123">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="8c99c-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
