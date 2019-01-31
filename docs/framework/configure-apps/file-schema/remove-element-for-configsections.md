---
title: <remove> – element pro element <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9ceffd3194c7df41f12ac6cd6b589602965b4920
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279094"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="81b73-102">\<Odebrat > – element pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="81b73-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="81b73-103">Odstraní předdefinované oddílu nebo skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="81b73-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="81b73-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="81b73-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="81b73-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="81b73-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="81b73-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="81b73-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="81b73-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81b73-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="81b73-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="81b73-108">Attribute</span></span>

|           | <span data-ttu-id="81b73-109">Popis</span><span class="sxs-lookup"><span data-stu-id="81b73-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="81b73-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="81b73-110">**name**</span></span>  | <span data-ttu-id="81b73-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="81b73-111">Required attribute.</span></span><br><br><span data-ttu-id="81b73-112">Určuje název sekce nebo skupiny části odebrat.</span><span class="sxs-lookup"><span data-stu-id="81b73-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="81b73-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="81b73-113">Parent element</span></span>

|     | <span data-ttu-id="81b73-114">Popis</span><span class="sxs-lookup"><span data-stu-id="81b73-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="81b73-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="81b73-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="81b73-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="81b73-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="81b73-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="81b73-117">Child elements</span></span>

<span data-ttu-id="81b73-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="81b73-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="81b73-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81b73-119">Remarks</span></span>

<span data-ttu-id="81b73-120">Můžete použít  **\<odebrat >** prvek, který chcete odstranit oddíly a skupin oddílů z vaší aplikace, které byly definovány na vyšší úrovni v hierarchii konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="81b73-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="81b73-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="81b73-121">Example</span></span>

<span data-ttu-id="81b73-122">Následující příklad ukazuje způsob použití  **\<odebrat >** prvku v konfiguračním souboru aplikace odebrat oddíl dříve definována v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="81b73-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="81b73-123">Následující počítače konfigurační soubor kód deklaruje části  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="81b73-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="81b73-124">Následující kód souboru konfigurace aplikace odebere  **\<sampleSection >** oddílu.</span><span class="sxs-lookup"><span data-stu-id="81b73-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="81b73-125">Po odebrání aplikace nelze načíst nastavení v  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="81b73-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="81b73-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="81b73-126">Configuration file</span></span>

<span data-ttu-id="81b73-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="81b73-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="81b73-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81b73-128">See also</span></span>

- [<span data-ttu-id="81b73-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81b73-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
