---
title: '&lt;System.XML.Serialization&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: b67c1ec1ec737976e4e50b80b42f34e508dc0224
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879361"
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="de9dc-102">&lt;System.XML.Serialization&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="de9dc-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="de9dc-103">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="de9dc-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="de9dc-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="de9dc-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="de9dc-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="de9dc-105">\<configuration></span></span>  
<span data-ttu-id="de9dc-106">\<System.XML.Serialization ></span><span class="sxs-lookup"><span data-stu-id="de9dc-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de9dc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de9dc-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de9dc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de9dc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="de9dc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de9dc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de9dc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="de9dc-110">Attributes</span></span>  
 <span data-ttu-id="de9dc-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="de9dc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de9dc-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de9dc-112">Child Elements</span></span>  
  
|<span data-ttu-id="de9dc-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="de9dc-113">Element</span></span>|<span data-ttu-id="de9dc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="de9dc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de9dc-115">\<dateTimeSerialization > – Element</span><span class="sxs-lookup"><span data-stu-id="de9dc-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="de9dc-116">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="de9dc-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="de9dc-117">\<schemaImporterExtensions > – Element</span><span class="sxs-lookup"><span data-stu-id="de9dc-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="de9dc-118">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de9dc-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de9dc-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de9dc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="de9dc-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="de9dc-120">Element</span></span>|<span data-ttu-id="de9dc-121">Popis</span><span class="sxs-lookup"><span data-stu-id="de9dc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de9dc-122">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="de9dc-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="de9dc-123">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de9dc-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de9dc-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="de9dc-124">Example</span></span>  
 <span data-ttu-id="de9dc-125">Následující příklad kódu ukazuje, jak určit režim serializace <xref:System.DateTime> objekt a přidání typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de9dc-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de9dc-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de9dc-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>  
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
- [<span data-ttu-id="de9dc-127">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="de9dc-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="de9dc-128">\<dateTimeSerialization > – Element</span><span class="sxs-lookup"><span data-stu-id="de9dc-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
- [<span data-ttu-id="de9dc-129">\<schemaImporterExtensions > – Element</span><span class="sxs-lookup"><span data-stu-id="de9dc-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
- [<span data-ttu-id="de9dc-130">\<Přidat > – Element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="de9dc-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
