---
title: '&lt;Odebrat&gt; – element pro &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 11a930120c375616d73faae68a6d6807c2f633cb
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307224"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="2cc8b-102">\<Odebrat > – element pro \<configSections ></span><span class="sxs-lookup"><span data-stu-id="2cc8b-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="2cc8b-103">Odstraní předdefinované oddílu nebo skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="2cc8b-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2cc8b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="2cc8b-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="2cc8b-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="2cc8b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="2cc8b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2cc8b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc8b-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="2cc8b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="2cc8b-108">Attribute</span></span>

|           | <span data-ttu-id="2cc8b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2cc8b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="2cc8b-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="2cc8b-110">**name**</span></span>  | <span data-ttu-id="2cc8b-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-111">Required attribute.</span></span><br><br><span data-ttu-id="2cc8b-112">Určuje název sekce nebo skupiny části odebrat.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="2cc8b-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="2cc8b-113">Parent element</span></span>

|     | <span data-ttu-id="2cc8b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2cc8b-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2cc8b-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="2cc8b-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="2cc8b-116">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2cc8b-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2cc8b-117">Child elements</span></span>

<span data-ttu-id="2cc8b-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="2cc8b-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="2cc8b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cc8b-119">Remarks</span></span>

<span data-ttu-id="2cc8b-120">Můžete použít  **\<odebrat >** prvek, který chcete odstranit oddíly a skupin oddílů z vaší aplikace, které byly definovány na vyšší úrovni v hierarchii konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="2cc8b-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cc8b-121">Example</span></span>

<span data-ttu-id="2cc8b-122">Následující příklad ukazuje způsob použití  **\<odebrat >** prvku v konfiguračním souboru aplikace odebrat oddíl dříve definována v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="2cc8b-123">Následující počítače konfigurační soubor kód deklaruje části  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="2cc8b-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="2cc8b-124">Následující kód souboru konfigurace aplikace odebere  **\<sampleSection >** oddílu.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="2cc8b-125">Po odebrání aplikace nelze načíst nastavení v  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="2cc8b-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="2cc8b-126">Configuration file</span></span>

<span data-ttu-id="2cc8b-127">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="2cc8b-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cc8b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cc8b-128">See also</span></span>

[<span data-ttu-id="2cc8b-129">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2cc8b-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
