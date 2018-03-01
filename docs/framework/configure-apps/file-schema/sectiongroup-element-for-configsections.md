---
title: '&lt;sectionGroup&gt; element pro &lt;configSections&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 654a6e639a24120e1e0c993ebe36f14e75b46a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="625b3-102">\<sectionGroup > elementu pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="625b3-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="625b3-103">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="625b3-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="625b3-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="625b3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="625b3-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="625b3-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="625b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="625b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="625b3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="625b3-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="625b3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="625b3-108">Attribute</span></span>

|           | <span data-ttu-id="625b3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="625b3-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="625b3-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="625b3-110">**name**</span></span>  | <span data-ttu-id="625b3-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="625b3-111">Required attribute.</span></span><br><br><span data-ttu-id="625b3-112">Určuje název oddílu skupiny, kterou definujete.</span><span class="sxs-lookup"><span data-stu-id="625b3-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="625b3-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="625b3-113">Parent element</span></span>

|     | <span data-ttu-id="625b3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="625b3-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="625b3-115">**\<configSections >** – Element</span><span class="sxs-lookup"><span data-stu-id="625b3-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="625b3-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="625b3-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="625b3-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="625b3-117">Child elements</span></span>

|     | <span data-ttu-id="625b3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="625b3-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="625b3-119">**\<část >**</span><span class="sxs-lookup"><span data-stu-id="625b3-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="625b3-120">Obsahuje deklaraci konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="625b3-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="625b3-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="625b3-121">Remarks</span></span>

<span data-ttu-id="625b3-122">Deklarování skupinu oddílů vytvoří značku kontejneru konfiguračních oddílů a zajišťuje, že neexistují žádné pojmenování je v konfliktu s konfiguračních oddílů, které jsou definované někdo jiný.</span><span class="sxs-lookup"><span data-stu-id="625b3-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="625b3-123">Lze vnořit  **\<sectionGroup >** elementů v rámci navzájem.</span><span class="sxs-lookup"><span data-stu-id="625b3-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="625b3-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="625b3-124">Example</span></span>

<span data-ttu-id="625b3-125">Následující příklad ukazuje, jak deklarovat skupinu oddílů a deklarovat oddíly v rámci skupiny oddílů:</span><span class="sxs-lookup"><span data-stu-id="625b3-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="625b3-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="625b3-126">Configuration file</span></span>

<span data-ttu-id="625b3-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="625b3-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="625b3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="625b3-128">See also</span></span>

[<span data-ttu-id="625b3-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="625b3-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
