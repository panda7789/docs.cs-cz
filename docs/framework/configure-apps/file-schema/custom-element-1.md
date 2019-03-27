---
title: Vlastní element pro SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bfc2a916e37ac27d45746eb268912b3752f4d80f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464434"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="51dd9-102">Vlastní element pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="51dd9-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="51dd9-103">Definuje nastavení, v části vlastní konfigurace, který je definován \<části > element a používá <xref:System.Configuration.SingleTagSectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="51dd9-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="51dd9-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="51dd9-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="51dd9-105">&nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="51dd9-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="51dd9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51dd9-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="51dd9-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="51dd9-107">Attributes</span></span>

<span data-ttu-id="51dd9-108">Atributy a hodnoty atributů jsou definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="51dd9-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="51dd9-109">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="51dd9-109">Parent element</span></span>

|     | <span data-ttu-id="51dd9-110">Popis</span><span class="sxs-lookup"><span data-stu-id="51dd9-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="51dd9-111">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="51dd9-111">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="51dd9-112">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51dd9-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="51dd9-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="51dd9-113">Child elements</span></span>

<span data-ttu-id="51dd9-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="51dd9-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="51dd9-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51dd9-115">Remarks</span></span>

<span data-ttu-id="51dd9-116"> *\*\<SectionName >** prvek je prvek vlastní, určené [  *\*\<části >** ](~/docs/framework/configure-apps/file-schema/section-element.md) značku [  *\*\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="51dd9-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="51dd9-117">Konfigurační systém vrátí <xref:System.Collections.IDictionary> objektu při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51dd9-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="51dd9-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="51dd9-118">Example</span></span>

<span data-ttu-id="51dd9-119">Následující příklad deklaruje vlastní prvek s názvem  **\<sampleSection >** , který obsahuje nastavení přečtou <xref:System.Configuration.SingleTagSectionHandler> třídy:</span><span class="sxs-lookup"><span data-stu-id="51dd9-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="51dd9-120">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="51dd9-120">Configuration file</span></span>

<span data-ttu-id="51dd9-121">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="51dd9-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="51dd9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51dd9-122">See also</span></span>

- [<span data-ttu-id="51dd9-123">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="51dd9-123">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
