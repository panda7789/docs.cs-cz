---
title: "Vlastní element pro SingleTagSectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 496967bc3638344d2b39d428b85270b575b325ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="7d0fe-102">Vlastní element pro SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="7d0fe-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="7d0fe-103">Definuje nastavení v části vlastní konfigurace, který je definován</span><span class="sxs-lookup"><span data-stu-id="7d0fe-103">Defines settings in a custom configuration section that is defined by a</span></span> <section> <span data-ttu-id="7d0fe-104">element a používá <xref:System.Configuration.SingleTagSectionHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="7d0fe-104">element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="7d0fe-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7d0fe-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="7d0fe-106">&nbsp;&nbsp;*\<sectionName >*</span><span class="sxs-lookup"><span data-stu-id="7d0fe-106">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="7d0fe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d0fe-107">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="7d0fe-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d0fe-108">Attributes</span></span>

<span data-ttu-id="7d0fe-109">Atributy a hodnoty atributů jsou definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7d0fe-109">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="7d0fe-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="7d0fe-110">Parent element</span></span>

|     | <span data-ttu-id="7d0fe-111">Popis</span><span class="sxs-lookup"><span data-stu-id="7d0fe-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7d0fe-112">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="7d0fe-112">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="7d0fe-113">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d0fe-113">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7d0fe-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7d0fe-114">Child elements</span></span>

<span data-ttu-id="7d0fe-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d0fe-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="7d0fe-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d0fe-116">Remarks</span></span>

<span data-ttu-id="7d0fe-117">**\<SectionName >** element je vlastní definované [  **\<části >** ](~/docs/framework/configure-apps/file-schema/section-element.md) značky v [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span><span class="sxs-lookup"><span data-stu-id="7d0fe-117">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="7d0fe-118">Konfigurační systém vrátí <xref:System.Collections.IDictionary> objektu při volání <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d0fe-118">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="7d0fe-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d0fe-119">Example</span></span>

<span data-ttu-id="7d0fe-120">Následující příklad deklaruje vlastní prvek s názvem  **\<sampleSection >** obsahující nastavení číst <xref:System.Configuration.SingleTagSectionHandler> třídy:</span><span class="sxs-lookup"><span data-stu-id="7d0fe-120">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="7d0fe-121">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="7d0fe-121">Configuration file</span></span>

<span data-ttu-id="7d0fe-122">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d0fe-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d0fe-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d0fe-123">See also</span></span>

[<span data-ttu-id="7d0fe-124">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7d0fe-124">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
