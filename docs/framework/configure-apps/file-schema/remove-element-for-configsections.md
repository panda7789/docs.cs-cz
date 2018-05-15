---
title: '&lt;Odebrat&gt; element pro &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 6555981edeb6f7f088fb12c710d0146cf58d5be1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="90ecd-102">\<Odebrat > elementu pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="90ecd-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="90ecd-103">Odstraní předdefinované části nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="90ecd-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="90ecd-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="90ecd-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="90ecd-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="90ecd-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="90ecd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="90ecd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="90ecd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90ecd-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="90ecd-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="90ecd-108">Attribute</span></span>

|           | <span data-ttu-id="90ecd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="90ecd-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="90ecd-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="90ecd-110">**name**</span></span>  | <span data-ttu-id="90ecd-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="90ecd-111">Required attribute.</span></span><br><br><span data-ttu-id="90ecd-112">Určuje název oddílu nebo skupiny oddílů pro odebrání.</span><span class="sxs-lookup"><span data-stu-id="90ecd-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="90ecd-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="90ecd-113">Parent element</span></span>

|     | <span data-ttu-id="90ecd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="90ecd-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="90ecd-115">**\<configSections >** – Element</span><span class="sxs-lookup"><span data-stu-id="90ecd-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="90ecd-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="90ecd-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="90ecd-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="90ecd-117">Child elements</span></span>

<span data-ttu-id="90ecd-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="90ecd-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="90ecd-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90ecd-119">Remarks</span></span>

<span data-ttu-id="90ecd-120">Můžete použít  **\<odebrat >** elementu, který chcete odebrat oddíly a skupiny oddílů z vaší aplikace, které byly definované na vyšší úrovni v hierarchii souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="90ecd-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="90ecd-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="90ecd-121">Example</span></span>

<span data-ttu-id="90ecd-122">Následující příklad ukazuje, jak používat  **\<odebrat >** element v konfiguračním souboru aplikace pro odebrání oddílu dříve definována v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="90ecd-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="90ecd-123">Následující počítače konfigurační soubor kód deklaruje části  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="90ecd-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="90ecd-124">Odebere následující kód soubor konfigurace aplikace  **\<sampleSection >** části.</span><span class="sxs-lookup"><span data-stu-id="90ecd-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="90ecd-125">Po odebrání aplikace nelze načíst nastavení v  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="90ecd-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="90ecd-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="90ecd-126">Configuration file</span></span>

<span data-ttu-id="90ecd-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="90ecd-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="90ecd-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="90ecd-128">See also</span></span>

[<span data-ttu-id="90ecd-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90ecd-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
