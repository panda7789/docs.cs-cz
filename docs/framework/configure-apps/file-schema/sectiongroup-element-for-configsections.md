---
title: <sectionGroup> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215263"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="abe8e-102">\<sectionGroup> – element pro \<configSections></span><span class="sxs-lookup"><span data-stu-id="abe8e-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="abe8e-103">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="abe8e-103">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="abe8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abe8e-104">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="abe8e-105">Atribut</span><span class="sxs-lookup"><span data-stu-id="abe8e-105">Attribute</span></span>

|           | <span data-ttu-id="abe8e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="abe8e-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="abe8e-107">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="abe8e-107">**name**</span></span>  | <span data-ttu-id="abe8e-108">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="abe8e-108">Required attribute.</span></span><br><br><span data-ttu-id="abe8e-109">Určuje název skupiny oddílů, kterou definujete.</span><span class="sxs-lookup"><span data-stu-id="abe8e-109">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="abe8e-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="abe8e-110">Parent element</span></span>

|     | <span data-ttu-id="abe8e-111">Description</span><span class="sxs-lookup"><span data-stu-id="abe8e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="abe8e-112">**\<configSections>** Objekt</span><span class="sxs-lookup"><span data-stu-id="abe8e-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="abe8e-113">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="abe8e-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="abe8e-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="abe8e-114">Child elements</span></span>

|     | <span data-ttu-id="abe8e-115">Description</span><span class="sxs-lookup"><span data-stu-id="abe8e-115">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="abe8e-116">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="abe8e-116">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="abe8e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abe8e-117">Remarks</span></span>

<span data-ttu-id="abe8e-118">Deklarace skupiny oddílů vytvoří značku kontejneru pro konfigurační oddíly a zajistí, že nedojde ke konfliktu názvů s konfiguračními oddíly definovanými někým jiným.</span><span class="sxs-lookup"><span data-stu-id="abe8e-118">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="abe8e-119">Prvky lze vnořit **\<sectionGroup>** do sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="abe8e-119">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="abe8e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="abe8e-120">Example</span></span>

<span data-ttu-id="abe8e-121">Následující příklad ukazuje, jak deklarovat skupinu oddílů a deklarovat oddíly v rámci skupiny oddílů:</span><span class="sxs-lookup"><span data-stu-id="abe8e-121">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="abe8e-122">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="abe8e-122">Configuration file</span></span>

<span data-ttu-id="abe8e-123">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="abe8e-123">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="abe8e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="abe8e-124">See also</span></span>

- [<span data-ttu-id="abe8e-125">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="abe8e-125">Configuration file schema for the .NET Framework</span></span>](index.md)
