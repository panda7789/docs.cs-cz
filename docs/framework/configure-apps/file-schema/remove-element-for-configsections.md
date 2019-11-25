---
title: <remove> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efc7208aa51cbf6abdb2fe151d48071c0aa95b5c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089053"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="55166-102">\<odebrat > element pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="55166-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="55166-103">Odebere předdefinovanou sekci nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="55166-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="55166-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="55166-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="55166-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="55166-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="55166-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="55166-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="55166-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55166-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="55166-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="55166-108">Attribute</span></span>

|           | <span data-ttu-id="55166-109">Popis</span><span class="sxs-lookup"><span data-stu-id="55166-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="55166-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="55166-110">**name**</span></span>  | <span data-ttu-id="55166-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="55166-111">Required attribute.</span></span><br><br><span data-ttu-id="55166-112">Určuje název oddílu nebo skupiny oddílů, které se mají odebrat.</span><span class="sxs-lookup"><span data-stu-id="55166-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="55166-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="55166-113">Parent element</span></span>

|     | <span data-ttu-id="55166-114">Popis</span><span class="sxs-lookup"><span data-stu-id="55166-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="55166-115"> **\<configSections >** Objekt</span><span class="sxs-lookup"><span data-stu-id="55166-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="55166-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="55166-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="55166-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="55166-117">Child elements</span></span>

<span data-ttu-id="55166-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="55166-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="55166-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55166-119">Remarks</span></span>

<span data-ttu-id="55166-120">Pomocí elementu **\<remove >** můžete odebrat oddíly a skupiny oddílů z vaší aplikace, které byly definovány na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="55166-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="55166-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="55166-121">Example</span></span>

<span data-ttu-id="55166-122">Následující příklad ukazuje, jak použít **\<odebrat >** elementu v konfiguračním souboru aplikace k odebrání oddílu dříve definovaného v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="55166-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="55166-123">Následující kód konfiguračního souboru počítače deklaruje oddíl **\<sampleSection >** :</span><span class="sxs-lookup"><span data-stu-id="55166-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="55166-124">Následující kód konfiguračního souboru aplikace odebere oddíl **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="55166-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="55166-125">Po odebrání nemůže aplikace načíst nastavení v **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="55166-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="55166-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="55166-126">Configuration file</span></span>

<span data-ttu-id="55166-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="55166-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="55166-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55166-128">See also</span></span>

- [<span data-ttu-id="55166-129">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="55166-129">Configuration file schema for the .NET Framework</span></span>](index.md)
