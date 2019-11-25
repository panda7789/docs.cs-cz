---
title: <sectionGroup> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 746a997e162b0fd370a249b8d039be623b57d77f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089009"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="df2de-102">> element \<sectionGroup pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="df2de-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="df2de-103">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="df2de-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="df2de-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="df2de-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="df2de-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="df2de-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="df2de-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<oddílů** ></span><span class="sxs-lookup"><span data-stu-id="df2de-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="df2de-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df2de-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="df2de-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="df2de-108">Attribute</span></span>

|           | <span data-ttu-id="df2de-109">Popis</span><span class="sxs-lookup"><span data-stu-id="df2de-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="df2de-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="df2de-110">**name**</span></span>  | <span data-ttu-id="df2de-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="df2de-111">Required attribute.</span></span><br><br><span data-ttu-id="df2de-112">Určuje název skupiny oddílů, kterou definujete.</span><span class="sxs-lookup"><span data-stu-id="df2de-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="df2de-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="df2de-113">Parent element</span></span>

|     | <span data-ttu-id="df2de-114">Popis</span><span class="sxs-lookup"><span data-stu-id="df2de-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="df2de-115"> **\<configSections >** Objekt</span><span class="sxs-lookup"><span data-stu-id="df2de-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="df2de-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="df2de-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="df2de-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="df2de-117">Child elements</span></span>

|     | <span data-ttu-id="df2de-118">Popis</span><span class="sxs-lookup"><span data-stu-id="df2de-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="df2de-119">**oddíl \<** </span><span class="sxs-lookup"><span data-stu-id="df2de-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="df2de-120">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="df2de-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="df2de-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df2de-121">Remarks</span></span>

<span data-ttu-id="df2de-122">Deklarace skupiny oddílů vytvoří značku kontejneru pro konfigurační oddíly a zajistí, že nedojde ke konfliktu názvů s konfiguračními oddíly definovanými někým jiným.</span><span class="sxs-lookup"><span data-stu-id="df2de-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="df2de-123">> Prvky můžete vnořovat do sebe **\<** .</span><span class="sxs-lookup"><span data-stu-id="df2de-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="df2de-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="df2de-124">Example</span></span>

<span data-ttu-id="df2de-125">Následující příklad ukazuje, jak deklarovat skupinu oddílů a deklarovat oddíly v rámci skupiny oddílů:</span><span class="sxs-lookup"><span data-stu-id="df2de-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="df2de-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="df2de-126">Configuration file</span></span>

<span data-ttu-id="df2de-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="df2de-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="df2de-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df2de-128">See also</span></span>

- [<span data-ttu-id="df2de-129">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df2de-129">Configuration file schema for the .NET Framework</span></span>](index.md)
