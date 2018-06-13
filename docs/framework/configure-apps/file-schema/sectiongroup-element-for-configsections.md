---
title: '&lt;sectionGroup&gt; element pro &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
ms.openlocfilehash: b898c81700e95ec9bc94e04c5a76494b7ac4b0dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754011"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="4708a-102">\<sectionGroup > elementu pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="4708a-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="4708a-103">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="4708a-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="4708a-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4708a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="4708a-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4708a-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="4708a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="4708a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4708a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4708a-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="4708a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="4708a-108">Attribute</span></span>

|           | <span data-ttu-id="4708a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4708a-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4708a-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="4708a-110">**name**</span></span>  | <span data-ttu-id="4708a-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4708a-111">Required attribute.</span></span><br><br><span data-ttu-id="4708a-112">Určuje název oddílu skupiny, kterou definujete.</span><span class="sxs-lookup"><span data-stu-id="4708a-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4708a-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="4708a-113">Parent element</span></span>

|     | <span data-ttu-id="4708a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4708a-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4708a-115">**\<configSections >** – Element</span><span class="sxs-lookup"><span data-stu-id="4708a-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="4708a-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4708a-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4708a-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="4708a-117">Child elements</span></span>

|     | <span data-ttu-id="4708a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="4708a-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4708a-119">**\<část >**</span><span class="sxs-lookup"><span data-stu-id="4708a-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="4708a-120">Obsahuje deklaraci konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="4708a-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4708a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4708a-121">Remarks</span></span>

<span data-ttu-id="4708a-122">Deklarování skupinu oddílů vytvoří značku kontejneru konfiguračních oddílů a zajišťuje, že neexistují žádné pojmenování je v konfliktu s konfiguračních oddílů, které jsou definované někdo jiný.</span><span class="sxs-lookup"><span data-stu-id="4708a-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="4708a-123">Lze vnořit  **\<sectionGroup >** elementů v rámci navzájem.</span><span class="sxs-lookup"><span data-stu-id="4708a-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="4708a-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4708a-124">Example</span></span>

<span data-ttu-id="4708a-125">Následující příklad ukazuje, jak deklarovat skupinu oddílů a deklarovat oddíly v rámci skupiny oddílů:</span><span class="sxs-lookup"><span data-stu-id="4708a-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4708a-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="4708a-126">Configuration file</span></span>

<span data-ttu-id="4708a-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="4708a-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4708a-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4708a-128">See also</span></span>

[<span data-ttu-id="4708a-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4708a-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
