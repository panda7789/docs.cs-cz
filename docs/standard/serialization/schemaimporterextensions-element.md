---
title: '&lt;schemaImporterExtensions&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c9f4f6800c2718c3b2c2b9b5b2b6d97e1114dbcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581326"
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="2bebd-102">&lt;schemaImporterExtensions&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="2bebd-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="2bebd-103">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bebd-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="2bebd-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="2bebd-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bebd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bebd-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="2bebd-106">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2bebd-106">Child Elements</span></span>  
  
|<span data-ttu-id="2bebd-107">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bebd-107">Element</span></span>|<span data-ttu-id="2bebd-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2bebd-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bebd-109">\<Přidat > elementu pro \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2bebd-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="2bebd-110">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> vytvořit mapování.</span><span class="sxs-lookup"><span data-stu-id="2bebd-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="2bebd-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2bebd-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2bebd-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bebd-112">Element</span></span>|<span data-ttu-id="2bebd-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2bebd-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bebd-114">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="2bebd-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="2bebd-115">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="2bebd-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2bebd-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bebd-116">Example</span></span>  
 <span data-ttu-id="2bebd-117">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bebd-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bebd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bebd-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="2bebd-119">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2bebd-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2bebd-120">\<dateTimeSerialization > elementu</span><span class="sxs-lookup"><span data-stu-id="2bebd-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="2bebd-121">\<Přidat > elementu pro \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2bebd-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="2bebd-122">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="2bebd-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
