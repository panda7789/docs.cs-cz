---
title: Element <add> pro <schemaImporterExtensions>
description: <add>Element přidá typy používané třídou XmlSchemaImporter pro mapování typů XSD na .NET Framework typy.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 6fd8113ad39a22c927035fca574151ae8f002685
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288326"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="ab5fb-103">Element \<add> pro \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="ab5fb-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="ab5fb-104">Přidá typy používané <xref:System.Xml.Serialization.XmlSchemaImporter> pro mapování typů XSD na typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="ab5fb-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab5fb-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="ab5fb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab5fb-106">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab5fb-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab5fb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ab5fb-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab5fb-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab5fb-109">Attributes</span></span>  
  
|<span data-ttu-id="ab5fb-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="ab5fb-110">Attribute</span></span>|<span data-ttu-id="ab5fb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ab5fb-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab5fb-112">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="ab5fb-112">**name**</span></span>|<span data-ttu-id="ab5fb-113">Jednoduchý název, který je použit k vyhledání instance.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-113">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="ab5fb-114">**textový**</span><span class="sxs-lookup"><span data-stu-id="ab5fb-114">**type**</span></span>|<span data-ttu-id="ab5fb-115">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-115">Required.</span></span> <span data-ttu-id="ab5fb-116">Určuje třídu rozšíření schématu k přidání.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-116">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="ab5fb-117">Hodnota atributu **Type** musí být na jednom řádku a musí obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-117">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="ab5fb-118">Při sestavení je umístěn v globální mezipaměti sestavení (GAC), musí také zahrnovat verze, jazykovou verzi a token veřejného klíče podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-118">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab5fb-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab5fb-119">Child Elements</span></span>  
 <span data-ttu-id="ab5fb-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab5fb-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab5fb-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab5fb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ab5fb-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab5fb-122">Element</span></span>|<span data-ttu-id="ab5fb-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ab5fb-123">Description</span></span>|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|<span data-ttu-id="ab5fb-124">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-124">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ab5fb-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab5fb-125">Example</span></span>  
 <span data-ttu-id="ab5fb-126">Následující příklad kódu přidá typ rozšíření, která XmlSchemaImporter můžete použít, když mapování typů.</span><span class="sxs-lookup"><span data-stu-id="ab5fb-126">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab5fb-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab5fb-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="ab5fb-128">\<system.xml.serialization>Objekt</span><span class="sxs-lookup"><span data-stu-id="ab5fb-128">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="ab5fb-129">\<schemaImporterExtensions>Objekt</span><span class="sxs-lookup"><span data-stu-id="ab5fb-129">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
