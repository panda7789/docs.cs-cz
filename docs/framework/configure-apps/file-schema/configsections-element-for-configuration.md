---
title: '&lt;configSections&gt; element pro &lt;konfigurace&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145a2a5cc23758c9fd2211c2da7fee0bbd736f0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="d2c50-102">\<configSections > elementu pro \<konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d2c50-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="d2c50-103">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d2c50-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="d2c50-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d2c50-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d2c50-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="d2c50-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="d2c50-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="d2c50-106">Attributes</span></span>

<span data-ttu-id="d2c50-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="d2c50-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="d2c50-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="d2c50-108">Parent element</span></span>

|     | <span data-ttu-id="d2c50-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c50-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d2c50-110">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="d2c50-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="d2c50-111">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2c50-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d2c50-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d2c50-112">Child elements</span></span>

|     | <span data-ttu-id="d2c50-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c50-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d2c50-114">**\<část >**</span><span class="sxs-lookup"><span data-stu-id="d2c50-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="d2c50-115">Obsahuje deklaraci konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="d2c50-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="d2c50-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="d2c50-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="d2c50-117">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="d2c50-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="d2c50-118">**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="d2c50-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="d2c50-119">Odstraní předdefinované části nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="d2c50-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="d2c50-120">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="d2c50-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="d2c50-121">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="d2c50-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d2c50-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2c50-122">Remarks</span></span>

<span data-ttu-id="d2c50-123">Pokud tento element je v konfiguračním souboru, musí být první podřízený prvek  **\<konfigurace >** element.</span><span class="sxs-lookup"><span data-stu-id="d2c50-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="d2c50-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2c50-124">Example</span></span>

<span data-ttu-id="d2c50-125">Následující příklad ukazuje, jak definovat oddíl konfigurace a nastavení pro daný oddíl:</span><span class="sxs-lookup"><span data-stu-id="d2c50-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d2c50-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="d2c50-126">Configuration file</span></span>

<span data-ttu-id="d2c50-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2c50-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2c50-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2c50-128">See also</span></span>

[<span data-ttu-id="d2c50-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d2c50-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
