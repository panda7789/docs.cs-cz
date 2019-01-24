---
title: '&lt;schemaImporterExtensions&gt; Element'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: dbe85ea817a597db84ddad530d67b1c2b7953f75
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535365"
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="65477-102">&lt;schemaImporterExtensions&gt; Element</span><span class="sxs-lookup"><span data-stu-id="65477-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="65477-103">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65477-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="65477-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="65477-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65477-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65477-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="65477-106">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="65477-106">Child Elements</span></span>  
  
|<span data-ttu-id="65477-107">Prvek</span><span class="sxs-lookup"><span data-stu-id="65477-107">Element</span></span>|<span data-ttu-id="65477-108">Popis</span><span class="sxs-lookup"><span data-stu-id="65477-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65477-109">\<Přidat > – Element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="65477-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="65477-110">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> vytvoření mapování.</span><span class="sxs-lookup"><span data-stu-id="65477-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="65477-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="65477-111">Parent Elements</span></span>  
  
|<span data-ttu-id="65477-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="65477-112">Element</span></span>|<span data-ttu-id="65477-113">Popis</span><span class="sxs-lookup"><span data-stu-id="65477-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65477-114">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="65477-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="65477-115">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="65477-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="65477-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="65477-116">Example</span></span>  
 <span data-ttu-id="65477-117">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65477-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="65477-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65477-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="65477-119">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="65477-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="65477-120">\<dateTimeSerialization > – Element</span><span class="sxs-lookup"><span data-stu-id="65477-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="65477-121">\<Přidat > – Element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="65477-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="65477-122">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="65477-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
