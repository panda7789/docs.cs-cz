---
title: Element <add> pro <schemaImporterExtensions>
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
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="4104e-102">\<Přidat> element pro \<> schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="4104e-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="4104e-103">Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4104e-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="4104e-104">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="4104e-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="4104e-105">\<> konfigurace</span><span class="sxs-lookup"><span data-stu-id="4104e-105">\<configuration></span></span>  
<span data-ttu-id="4104e-106">\<System. XML. Serialization –></span><span class="sxs-lookup"><span data-stu-id="4104e-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="4104e-107">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="4104e-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="4104e-108">\<Přidat></span><span class="sxs-lookup"><span data-stu-id="4104e-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4104e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4104e-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4104e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4104e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4104e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4104e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4104e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4104e-112">Attributes</span></span>  
  
|<span data-ttu-id="4104e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4104e-113">Attribute</span></span>|<span data-ttu-id="4104e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4104e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4104e-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="4104e-115">**name**</span></span>|<span data-ttu-id="4104e-116">Jednoduchý název, který je použit k vyhledání instance.</span><span class="sxs-lookup"><span data-stu-id="4104e-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="4104e-117">**textový**</span><span class="sxs-lookup"><span data-stu-id="4104e-117">**type**</span></span>|<span data-ttu-id="4104e-118">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="4104e-118">Required.</span></span> <span data-ttu-id="4104e-119">Určuje třídu rozšíření schématu k přidání.</span><span class="sxs-lookup"><span data-stu-id="4104e-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="4104e-120">Hodnota atributu **Type** musí být na jednom řádku a musí obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="4104e-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="4104e-121">Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="4104e-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4104e-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4104e-122">Child Elements</span></span>  
 <span data-ttu-id="4104e-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="4104e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4104e-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4104e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4104e-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="4104e-125">Element</span></span>|<span data-ttu-id="4104e-126">Popis</span><span class="sxs-lookup"><span data-stu-id="4104e-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4104e-127">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="4104e-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="4104e-128">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="4104e-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4104e-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="4104e-129">Example</span></span>  
 <span data-ttu-id="4104e-130">Následující příklad kódu přidá typ rozšíření, která XmlSchemaImporter můžete použít, když mapování typů.</span><span class="sxs-lookup"><span data-stu-id="4104e-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4104e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="4104e-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="4104e-132">\<System. XML. Serialization – element></span><span class="sxs-lookup"><span data-stu-id="4104e-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="4104e-133">\<schemaImporterExtensions – element></span><span class="sxs-lookup"><span data-stu-id="4104e-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
