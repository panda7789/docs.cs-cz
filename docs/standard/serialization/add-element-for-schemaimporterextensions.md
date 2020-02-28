---
title: <add> – element pro <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 4f47623aa305ae6e98625acc3d199a76e27d2ea5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159933"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="95fd7-102">\<přidat > element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="95fd7-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="95fd7-103">Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95fd7-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="95fd7-104">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="95fd7-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="95fd7-105">Konfigurace \<></span><span class="sxs-lookup"><span data-stu-id="95fd7-105">\<configuration></span></span>  
<span data-ttu-id="95fd7-106">\<System. XML. Serialization ></span><span class="sxs-lookup"><span data-stu-id="95fd7-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="95fd7-107">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="95fd7-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="95fd7-108">\<přidat ></span><span class="sxs-lookup"><span data-stu-id="95fd7-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95fd7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95fd7-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95fd7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="95fd7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="95fd7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="95fd7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95fd7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="95fd7-112">Attributes</span></span>  
  
|<span data-ttu-id="95fd7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="95fd7-113">Attribute</span></span>|<span data-ttu-id="95fd7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="95fd7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95fd7-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="95fd7-115">**name**</span></span>|<span data-ttu-id="95fd7-116">Jednoduchý název, který je použit k vyhledání instance.</span><span class="sxs-lookup"><span data-stu-id="95fd7-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="95fd7-117">**type**</span><span class="sxs-lookup"><span data-stu-id="95fd7-117">**type**</span></span>|<span data-ttu-id="95fd7-118">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="95fd7-118">Required.</span></span> <span data-ttu-id="95fd7-119">Určuje třídu rozšíření schématu k přidání.</span><span class="sxs-lookup"><span data-stu-id="95fd7-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="95fd7-120">Hodnota atributu **Type** musí být na jednom řádku a musí obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="95fd7-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="95fd7-121">Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="95fd7-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95fd7-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="95fd7-122">Child Elements</span></span>  
 <span data-ttu-id="95fd7-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="95fd7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95fd7-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="95fd7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="95fd7-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="95fd7-125">Element</span></span>|<span data-ttu-id="95fd7-126">Popis</span><span class="sxs-lookup"><span data-stu-id="95fd7-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95fd7-127">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="95fd7-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="95fd7-128">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="95fd7-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95fd7-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="95fd7-129">Example</span></span>  
 <span data-ttu-id="95fd7-130">Následující příklad kódu přidá typ rozšíření, která XmlSchemaImporter můžete použít, když mapování typů.</span><span class="sxs-lookup"><span data-stu-id="95fd7-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95fd7-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="95fd7-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="95fd7-132">\<element System. XML. Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="95fd7-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="95fd7-133">\<element > schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="95fd7-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
