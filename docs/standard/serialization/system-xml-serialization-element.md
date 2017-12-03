---
title: "&lt;System.XML.Serialization&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d70879d5e0a579af7b5c507910d4dcb19ddee52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="dc8f9-102">&lt;System.XML.Serialization&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="dc8f9-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="dc8f9-103">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="dc8f9-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="dc8f9-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc8f9-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="dc8f9-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="dc8f9-105">\<configuration></span></span>  
<span data-ttu-id="dc8f9-106">\<System.XML.Serialization ></span><span class="sxs-lookup"><span data-stu-id="dc8f9-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc8f9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc8f9-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc8f9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc8f9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dc8f9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc8f9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc8f9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc8f9-110">Attributes</span></span>  
 <span data-ttu-id="dc8f9-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="dc8f9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc8f9-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc8f9-112">Child Elements</span></span>  
  
|<span data-ttu-id="dc8f9-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc8f9-113">Element</span></span>|<span data-ttu-id="dc8f9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dc8f9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc8f9-115">\<dateTimeSerialization > elementu</span><span class="sxs-lookup"><span data-stu-id="dc8f9-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="dc8f9-116">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="dc8f9-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="dc8f9-117">\<schemaImporterExtensions > elementu</span><span class="sxs-lookup"><span data-stu-id="dc8f9-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="dc8f9-118">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc8f9-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc8f9-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc8f9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dc8f9-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc8f9-120">Element</span></span>|<span data-ttu-id="dc8f9-121">Popis</span><span class="sxs-lookup"><span data-stu-id="dc8f9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc8f9-122">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="dc8f9-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="dc8f9-123">Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc8f9-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dc8f9-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc8f9-124">Example</span></span>  
 <span data-ttu-id="dc8f9-125">Následující příklad kódu ukazuje, jak určit režim serializace <xref:System.DateTime> objekt a přidání typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc8f9-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc8f9-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc8f9-126">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="dc8f9-127">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="dc8f9-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="dc8f9-128">\<dateTimeSerialization > elementu</span><span class="sxs-lookup"><span data-stu-id="dc8f9-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="dc8f9-129">\<schemaImporterExtensions > elementu</span><span class="sxs-lookup"><span data-stu-id="dc8f9-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [<span data-ttu-id="dc8f9-130">\<Přidat > elementu pro \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="dc8f9-130">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)
