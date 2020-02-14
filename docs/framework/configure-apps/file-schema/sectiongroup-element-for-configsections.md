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
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215263"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="9d064-102">> element \<sectionGroup pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="9d064-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="9d064-103">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="9d064-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="9d064-104">[**konfigurační >\<** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d064-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="9d064-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9d064-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="9d064-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<oddílů** ></span><span class="sxs-lookup"><span data-stu-id="9d064-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9d064-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d064-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="9d064-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d064-108">Attribute</span></span>

|           | <span data-ttu-id="9d064-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9d064-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9d064-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="9d064-110">**name**</span></span>  | <span data-ttu-id="9d064-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9d064-111">Required attribute.</span></span><br><br><span data-ttu-id="9d064-112">Určuje název skupiny oddílů, kterou definujete.</span><span class="sxs-lookup"><span data-stu-id="9d064-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9d064-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="9d064-113">Parent element</span></span>

|     | <span data-ttu-id="9d064-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9d064-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9d064-115"> **\<configSections >** Objekt</span><span class="sxs-lookup"><span data-stu-id="9d064-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="9d064-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9d064-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9d064-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9d064-117">Child elements</span></span>

|     | <span data-ttu-id="9d064-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9d064-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9d064-119">**oddíl \<>** </span><span class="sxs-lookup"><span data-stu-id="9d064-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="9d064-120">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="9d064-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9d064-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d064-121">Remarks</span></span>

<span data-ttu-id="9d064-122">Deklarace skupiny oddílů vytvoří značku kontejneru pro konfigurační oddíly a zajistí, že nedojde ke konfliktu názvů s konfiguračními oddíly definovanými někým jiným.</span><span class="sxs-lookup"><span data-stu-id="9d064-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="9d064-123">> Prvky můžete vnořovat do sebe **\<** .</span><span class="sxs-lookup"><span data-stu-id="9d064-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="9d064-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d064-124">Example</span></span>

<span data-ttu-id="9d064-125">Následující příklad ukazuje, jak deklarovat skupinu oddílů a deklarovat oddíly v rámci skupiny oddílů:</span><span class="sxs-lookup"><span data-stu-id="9d064-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="9d064-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="9d064-126">Configuration file</span></span>

<span data-ttu-id="9d064-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="9d064-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d064-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d064-128">See also</span></span>

- [<span data-ttu-id="9d064-129">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d064-129">Configuration file schema for the .NET Framework</span></span>](index.md)
