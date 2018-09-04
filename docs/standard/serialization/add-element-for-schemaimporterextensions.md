---
title: '&lt;Přidat&gt; – Element pro &lt;schemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 3d3c72fd64042032d44c49ebde867d111ce03b94
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542637"
---
# <a name="ltaddgt-element-for-ltschemaimporterextensionsgt"></a><span data-ttu-id="5ea83-102">&lt;Přidat&gt; – Element pro &lt;schemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="5ea83-102">&lt;add&gt; Element for &lt;schemaImporterExtensions&gt;</span></span>
<span data-ttu-id="5ea83-103">Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ea83-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="5ea83-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="5ea83-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="5ea83-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="5ea83-105">\<configuration></span></span>  
<span data-ttu-id="5ea83-106">\<System.XML.Serialization ></span><span class="sxs-lookup"><span data-stu-id="5ea83-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="5ea83-107">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="5ea83-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="5ea83-108">\<add></span><span class="sxs-lookup"><span data-stu-id="5ea83-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea83-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ea83-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ea83-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ea83-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ea83-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ea83-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ea83-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ea83-112">Attributes</span></span>  
  
|<span data-ttu-id="5ea83-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5ea83-113">Attribute</span></span>|<span data-ttu-id="5ea83-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea83-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ea83-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="5ea83-115">**name**</span></span>|<span data-ttu-id="5ea83-116">Jednoduchý název, který je použit k vyhledání instance.</span><span class="sxs-lookup"><span data-stu-id="5ea83-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="5ea83-117">**Typ**</span><span class="sxs-lookup"><span data-stu-id="5ea83-117">**type**</span></span>|<span data-ttu-id="5ea83-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="5ea83-118">Required.</span></span> <span data-ttu-id="5ea83-119">Určuje třídu rozšíření schématu k přidání.</span><span class="sxs-lookup"><span data-stu-id="5ea83-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="5ea83-120">**Typ** hodnota atributu musí být na jednom řádku a zahrnout plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="5ea83-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="5ea83-121">Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="5ea83-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ea83-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ea83-122">Child Elements</span></span>  
 <span data-ttu-id="5ea83-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="5ea83-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ea83-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ea83-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5ea83-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ea83-125">Element</span></span>|<span data-ttu-id="5ea83-126">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea83-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ea83-127">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="5ea83-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="5ea83-128">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="5ea83-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5ea83-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ea83-129">Example</span></span>  
 <span data-ttu-id="5ea83-130">Následující příklad kódu přidá typ rozšíření, která XmlSchemaImporter můžete použít, když mapování typů.</span><span class="sxs-lookup"><span data-stu-id="5ea83-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ea83-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ea83-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="5ea83-132">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="5ea83-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="5ea83-133">\<schemaImporterExtensions > – Element</span><span class="sxs-lookup"><span data-stu-id="5ea83-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
