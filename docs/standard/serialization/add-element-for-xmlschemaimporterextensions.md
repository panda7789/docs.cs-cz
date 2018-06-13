---
title: '&lt;Přidat&gt; Element pro &lt;xmlSchemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <xmlSchemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 6e14c478e33c465d2ea3d10158f856dc5ca6c49a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581739"
---
# <a name="ltaddgt-element-for-ltxmlschemaimporterextensionsgt"></a><span data-ttu-id="65e17-102">&lt;Přidat&gt; Element pro &lt;xmlSchemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="65e17-102">&lt;add&gt; Element for &lt;xmlSchemaImporterExtensions&gt;</span></span>
<span data-ttu-id="65e17-103">Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65e17-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="65e17-104">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="65e17-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="65e17-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="65e17-105">\<configuration></span></span>  
<span data-ttu-id="65e17-106">\<System.XML.Serialization ></span><span class="sxs-lookup"><span data-stu-id="65e17-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="65e17-107">\<XmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="65e17-107">\<XmlSchemaImporterExtensions></span></span>  
<span data-ttu-id="65e17-108">\<add></span><span class="sxs-lookup"><span data-stu-id="65e17-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e17-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65e17-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65e17-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="65e17-110">Attributes and Elements</span></span>  
 <span data-ttu-id="65e17-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="65e17-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65e17-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="65e17-112">Attributes</span></span>  
  
|<span data-ttu-id="65e17-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="65e17-113">Attribute</span></span>|<span data-ttu-id="65e17-114">Popis</span><span class="sxs-lookup"><span data-stu-id="65e17-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65e17-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="65e17-115">**name**</span></span>|<span data-ttu-id="65e17-116">Jednoduchý název, který je použit k vyhledání instance.</span><span class="sxs-lookup"><span data-stu-id="65e17-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="65e17-117">**Typ**</span><span class="sxs-lookup"><span data-stu-id="65e17-117">**type**</span></span>|<span data-ttu-id="65e17-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="65e17-118">Required.</span></span> <span data-ttu-id="65e17-119">Určuje třídu rozšíření schématu k přidání.</span><span class="sxs-lookup"><span data-stu-id="65e17-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="65e17-120">**Typ** hodnota atributu musí být na jednom řádku a zahrnout plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="65e17-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="65e17-121">Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e17-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65e17-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="65e17-122">Child Elements</span></span>  
 <span data-ttu-id="65e17-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="65e17-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65e17-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="65e17-124">Parent Elements</span></span>  
  
|<span data-ttu-id="65e17-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="65e17-125">Element</span></span>|<span data-ttu-id="65e17-126">Popis</span><span class="sxs-lookup"><span data-stu-id="65e17-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65e17-127">\<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="65e17-127">\<xmlSchemaImporterExtensions></span></span>|<span data-ttu-id="65e17-128">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="65e17-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="65e17-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="65e17-129">Example</span></span>  
 <span data-ttu-id="65e17-130">Následující příklad kódu přidá typ rozšíření, která XmlSchemaImporter můžete použít, když mapování typů.</span><span class="sxs-lookup"><span data-stu-id="65e17-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65e17-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="65e17-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="65e17-132">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="65e17-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="65e17-133">\<schemaImporterExtensions > elementu</span><span class="sxs-lookup"><span data-stu-id="65e17-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
