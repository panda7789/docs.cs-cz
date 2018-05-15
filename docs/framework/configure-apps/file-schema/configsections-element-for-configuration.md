---
title: '&lt;configSections&gt; element pro &lt;konfigurace&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 33406a67389cdf857fa5030e20d8a4dec7662741
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="88cd2-102">\<configSections > elementu pro \<konfigurace ></span><span class="sxs-lookup"><span data-stu-id="88cd2-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="88cd2-103">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="88cd2-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="88cd2-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="88cd2-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="88cd2-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="88cd2-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="88cd2-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="88cd2-106">Attributes</span></span>

<span data-ttu-id="88cd2-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="88cd2-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="88cd2-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="88cd2-108">Parent element</span></span>

|     | <span data-ttu-id="88cd2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="88cd2-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="88cd2-110">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="88cd2-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="88cd2-111">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88cd2-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="88cd2-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="88cd2-112">Child elements</span></span>

|     | <span data-ttu-id="88cd2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="88cd2-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="88cd2-114">**\<část >**</span><span class="sxs-lookup"><span data-stu-id="88cd2-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="88cd2-115">Obsahuje deklaraci konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="88cd2-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="88cd2-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="88cd2-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="88cd2-117">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="88cd2-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="88cd2-118">**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="88cd2-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="88cd2-119">Odstraní předdefinované části nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="88cd2-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="88cd2-120">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="88cd2-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="88cd2-121">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="88cd2-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="88cd2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88cd2-122">Remarks</span></span>

<span data-ttu-id="88cd2-123">Pokud tento element je v konfiguračním souboru, musí být první podřízený prvek  **\<konfigurace >** element.</span><span class="sxs-lookup"><span data-stu-id="88cd2-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="88cd2-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="88cd2-124">Example</span></span>

<span data-ttu-id="88cd2-125">Následující příklad ukazuje, jak definovat oddíl konfigurace a nastavení pro daný oddíl:</span><span class="sxs-lookup"><span data-stu-id="88cd2-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="88cd2-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="88cd2-126">Configuration file</span></span>

<span data-ttu-id="88cd2-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="88cd2-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="88cd2-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="88cd2-128">See also</span></span>

[<span data-ttu-id="88cd2-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="88cd2-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
