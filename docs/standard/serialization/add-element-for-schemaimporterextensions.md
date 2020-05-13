---
title: Element <add> pro <schemaImporterExtensions>
description: <add>Element přidá typy používané třídou XmlSchemaImporter pro mapování typů XSD na .NET Framework typy.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378470"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="b16c8-103">\<Přidat> element pro \<> schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="b16c8-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="b16c8-104">Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b16c8-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="b16c8-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="b16c8-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="b16c8-106">\<> konfigurace</span><span class="sxs-lookup"><span data-stu-id="b16c8-106">\<configuration></span></span>  
<span data-ttu-id="b16c8-107">\<System. XML. Serialization –></span><span class="sxs-lookup"><span data-stu-id="b16c8-107">\<system.xml.serialization></span></span>  
<span data-ttu-id="b16c8-108">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="b16c8-108">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="b16c8-109">\<Přidat></span><span class="sxs-lookup"><span data-stu-id="b16c8-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b16c8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b16c8-110">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b16c8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b16c8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b16c8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b16c8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b16c8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b16c8-113">Attributes</span></span>  
  
|<span data-ttu-id="b16c8-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="b16c8-114">Attribute</span></span>|<span data-ttu-id="b16c8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b16c8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b16c8-116">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="b16c8-116">**name**</span></span>|<span data-ttu-id="b16c8-117">Jednoduchý název, který je použit k vyhledání instance.</span><span class="sxs-lookup"><span data-stu-id="b16c8-117">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="b16c8-118">**textový**</span><span class="sxs-lookup"><span data-stu-id="b16c8-118">**type**</span></span>|<span data-ttu-id="b16c8-119">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b16c8-119">Required.</span></span> <span data-ttu-id="b16c8-120">Určuje třídu rozšíření schématu k přidání.</span><span class="sxs-lookup"><span data-stu-id="b16c8-120">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="b16c8-121">Hodnota atributu **Type** musí být na jednom řádku a musí obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="b16c8-121">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="b16c8-122">Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="b16c8-122">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b16c8-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b16c8-123">Child Elements</span></span>  
 <span data-ttu-id="b16c8-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="b16c8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b16c8-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b16c8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b16c8-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="b16c8-126">Element</span></span>|<span data-ttu-id="b16c8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="b16c8-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b16c8-128">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="b16c8-128">\<schemaImporterExtensions></span></span>|<span data-ttu-id="b16c8-129">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="b16c8-129">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b16c8-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b16c8-130">Example</span></span>  
 <span data-ttu-id="b16c8-131">Následující příklad kódu přidá typ rozšíření, která XmlSchemaImporter můžete použít, když mapování typů.</span><span class="sxs-lookup"><span data-stu-id="b16c8-131">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b16c8-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="b16c8-132">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="b16c8-133">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="b16c8-133">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="b16c8-134">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="b16c8-134">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
