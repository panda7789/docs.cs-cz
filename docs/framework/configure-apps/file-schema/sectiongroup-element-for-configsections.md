---
title: <sectionGroup> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 750708483f9680745eef4531d86fa7ecaa329f51
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301198"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="91943-102">\<sectionGroup > – element pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="91943-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="91943-103">Definuje obor názvů pro oddíly konfigurace.</span><span class="sxs-lookup"><span data-stu-id="91943-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="91943-104">[ **\<Konfigurace >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="91943-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="91943-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="91943-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="91943-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="91943-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="91943-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91943-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="91943-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="91943-108">Attribute</span></span>

|           | <span data-ttu-id="91943-109">Popis</span><span class="sxs-lookup"><span data-stu-id="91943-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="91943-110">**name**</span><span class="sxs-lookup"><span data-stu-id="91943-110">**name**</span></span>  | <span data-ttu-id="91943-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="91943-111">Required attribute.</span></span><br><br><span data-ttu-id="91943-112">Určuje název skupiny oddílů, které definujete.</span><span class="sxs-lookup"><span data-stu-id="91943-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="91943-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="91943-113">Parent element</span></span>

|     | <span data-ttu-id="91943-114">Popis</span><span class="sxs-lookup"><span data-stu-id="91943-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="91943-115"> *\*\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="91943-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="91943-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="91943-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="91943-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="91943-117">Child elements</span></span>

|     | <span data-ttu-id="91943-118">Popis</span><span class="sxs-lookup"><span data-stu-id="91943-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="91943-119"> *\*\<část >** </span><span class="sxs-lookup"><span data-stu-id="91943-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="91943-120">Obsahuje deklarace oddíl konfigurace.</span><span class="sxs-lookup"><span data-stu-id="91943-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="91943-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91943-121">Remarks</span></span>

<span data-ttu-id="91943-122">Deklarace skupiny oddílů vytvoří značku kontejneru pro konfigurační oddíly a zajistí, že neexistují žádné zásady je v konfliktu s konfigurační oddíly funkce definované někým jiným.</span><span class="sxs-lookup"><span data-stu-id="91943-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="91943-123">Je možné vnořovat  **\<sectionGroup >** elementů v rámci sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="91943-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="91943-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="91943-124">Example</span></span>

<span data-ttu-id="91943-125">Následující příklad ukazuje, jak deklarovat skupiny oddílů a deklarovat oddíly v rámci skupiny oddílů:</span><span class="sxs-lookup"><span data-stu-id="91943-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="91943-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="91943-126">Configuration file</span></span>

<span data-ttu-id="91943-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="91943-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="91943-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91943-128">See also</span></span>

- [<span data-ttu-id="91943-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="91943-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
