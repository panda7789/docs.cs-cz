---
title: Element <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5ed80ac370e34d6b62bb2b601cb7bd978228a302
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159816"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="957c1-102">\<element > schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="957c1-102">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="957c1-103">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="957c1-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="957c1-104">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="957c1-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="957c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="957c1-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="957c1-106">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="957c1-106">Child Elements</span></span>  
  
|<span data-ttu-id="957c1-107">Prvek</span><span class="sxs-lookup"><span data-stu-id="957c1-107">Element</span></span>|<span data-ttu-id="957c1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="957c1-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="957c1-109">\<přidat > element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="957c1-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="957c1-110">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> k vytvoření mapování.</span><span class="sxs-lookup"><span data-stu-id="957c1-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="957c1-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="957c1-111">Parent Elements</span></span>  
  
|<span data-ttu-id="957c1-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="957c1-112">Element</span></span>|<span data-ttu-id="957c1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="957c1-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="957c1-114">\<element System. XML. Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="957c1-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="957c1-115">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="957c1-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="957c1-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="957c1-116">Example</span></span>  
 <span data-ttu-id="957c1-117">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="957c1-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="957c1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="957c1-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="957c1-119">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="957c1-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="957c1-120">\<element > dateTimeSerialization</span><span class="sxs-lookup"><span data-stu-id="957c1-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="957c1-121">\<přidat > element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="957c1-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="957c1-122">\<element System. XML. Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="957c1-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
