---
title: Element <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 43f8439708c73e8e5241a923360caf549bf09d8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017956"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="c3254-102">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="c3254-102">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="c3254-103">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3254-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="c3254-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="c3254-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3254-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3254-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="c3254-106">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c3254-106">Child Elements</span></span>  
  
|<span data-ttu-id="c3254-107">Prvek</span><span class="sxs-lookup"><span data-stu-id="c3254-107">Element</span></span>|<span data-ttu-id="c3254-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c3254-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3254-109">\<Přidat > – Element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="c3254-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="c3254-110">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> vytvoření mapování.</span><span class="sxs-lookup"><span data-stu-id="c3254-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="c3254-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c3254-111">Parent Elements</span></span>  
  
|<span data-ttu-id="c3254-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="c3254-112">Element</span></span>|<span data-ttu-id="c3254-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c3254-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3254-114">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="c3254-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="c3254-115">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="c3254-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c3254-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3254-116">Example</span></span>  
 <span data-ttu-id="c3254-117">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3254-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3254-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3254-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="c3254-119">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c3254-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c3254-120">\<dateTimeSerialization > – Element</span><span class="sxs-lookup"><span data-stu-id="c3254-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="c3254-121">\<Přidat > – Element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="c3254-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="c3254-122">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="c3254-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
