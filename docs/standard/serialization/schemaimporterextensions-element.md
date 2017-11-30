---
title: "&lt;schemaImporterExtensions&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b3cc5e75cded5d468323a2b953bc61271f89e3e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="12513-102">&lt;schemaImporterExtensions&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="12513-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="12513-103">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12513-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="12513-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="12513-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12513-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12513-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="12513-106">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="12513-106">Child Elements</span></span>  
  
|<span data-ttu-id="12513-107">Prvek</span><span class="sxs-lookup"><span data-stu-id="12513-107">Element</span></span>|<span data-ttu-id="12513-108">Popis</span><span class="sxs-lookup"><span data-stu-id="12513-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12513-109">\<Přidat > elementu pro \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="12513-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="12513-110">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> vytvořit mapování.</span><span class="sxs-lookup"><span data-stu-id="12513-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="12513-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12513-111">Parent Elements</span></span>  
  
|<span data-ttu-id="12513-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="12513-112">Element</span></span>|<span data-ttu-id="12513-113">Popis</span><span class="sxs-lookup"><span data-stu-id="12513-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12513-114">\<System.XML.Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="12513-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="12513-115">Element nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="12513-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="12513-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="12513-116">Example</span></span>  
 <span data-ttu-id="12513-117">Následující příklad kódu ukazuje, jak přidat typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> při mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12513-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12513-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="12513-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="12513-119">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="12513-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="12513-120">\<dateTimeSerialization > elementu</span><span class="sxs-lookup"><span data-stu-id="12513-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="12513-121">\<Přidat > elementu pro \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="12513-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="12513-122">\<System.XML.Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="12513-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
