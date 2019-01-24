---
title: '&lt;linkedconfiguration –&gt; – element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e5c8449e72414775c40ced2c344e12d5137ac03f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546410"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="2f9f3-102">\<linkedconfiguration – > – element</span><span class="sxs-lookup"><span data-stu-id="2f9f3-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="2f9f3-103">Určuje konfigurační soubor, který chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="2f9f3-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2f9f3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="2f9f3-105">&nbsp;&nbsp;[**\<assemblybinding – >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="2f9f3-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="2f9f3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="2f9f3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2f9f3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f9f3-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="2f9f3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="2f9f3-108">Attribute</span></span>

|           | <span data-ttu-id="2f9f3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2f9f3-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="2f9f3-110">**href**</span><span class="sxs-lookup"><span data-stu-id="2f9f3-110">**href**</span></span>  | <span data-ttu-id="2f9f3-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-111">Required attribute.</span></span><br><br><span data-ttu-id="2f9f3-112">Adresa URL konfiguračního souboru chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="2f9f3-113">Jediným formátem podporovaným **href** atribut je `file://`.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="2f9f3-114">Jsou podporovány místní soubory a soubory ve formátu UNC.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="2f9f3-115">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="2f9f3-115">Parent element</span></span>

|     | <span data-ttu-id="2f9f3-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2f9f3-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2f9f3-117">**\<assemblybinding – >** – Element</span><span class="sxs-lookup"><span data-stu-id="2f9f3-117">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="2f9f3-118">Určuje zásady vazeb sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2f9f3-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2f9f3-119">Child elements</span></span>

<span data-ttu-id="2f9f3-120">Žádná</span><span class="sxs-lookup"><span data-stu-id="2f9f3-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="2f9f3-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f9f3-121">Remarks</span></span>

<span data-ttu-id="2f9f3-122"> *\*\<Linkedconfiguration – >** element zjednodušuje údržbu pro sestavení komponent.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="2f9f3-123">Pokud jeden nebo více aplikací používat sestavení, která obsahuje konfigurační soubor umístěný v dobře známého umístění, můžete použít konfigurační soubory aplikace, které používají sestavení  **\<linkedconfiguration – >** Element zahrnout konfigurační soubor sestavení, nikoli přímo včetně informací o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="2f9f3-124">Při sestavení součástí je údržba, aktualizace společné konfigurační soubor obsahuje informace aktualizovanou konfiguraci pro všechny aplikace, které používají sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="2f9f3-125"> *\*\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="2f9f3-126">Následující pravidla určují, použití propojené konfigurační soubory:</span><span class="sxs-lookup"><span data-stu-id="2f9f3-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="2f9f3-127">Nastavení v souborech konfigurace na zahrnuté pouze ovlivnit zavaděč zásady vazeb a jsou používány pouze zavaděč.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="2f9f3-128">Konfigurace zahrnuté soubory mohou mít nastavení vazby zásady, ale tato nastavení nemají žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="2f9f3-129">Jediným formátem podporovaným `href` atribut je `file://`.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="2f9f3-130">Jsou podporovány místní soubory a soubory ve formátu UNC.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="2f9f3-131">Neexistuje žádné omezení počtu propojené konfigurace na konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="2f9f3-132">Všechny propojené konfigurační soubory jsou sloučeny do jednoho souboru, podobně jako chování `#include` direktiva v jazyce C/C++.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="2f9f3-133"> *\*\<Linkedconfiguration – >** element je povolen pouze v konfiguračních souborech aplikace, je ignorován v \*Machine.config\*.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="2f9f3-134">Cyklické odkazy jsou zjištěny a byla ukončena.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="2f9f3-135">To znamená pokud  **\<linkedconfiguration – >** prvky z řady konfigurační soubory tvoří cyklus, smyčky je zjištěna a zastavena.</span><span class="sxs-lookup"><span data-stu-id="2f9f3-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="2f9f3-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f9f3-136">Example</span></span>

<span data-ttu-id="2f9f3-137">Následující příklad ukazuje, jak zahrnout konfigurační soubor z místního pevného disku:</span><span class="sxs-lookup"><span data-stu-id="2f9f3-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2f9f3-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f9f3-138">See also</span></span>

- [<span data-ttu-id="2f9f3-139">**\<assemblybinding – >** – Element</span><span class="sxs-lookup"><span data-stu-id="2f9f3-139">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="2f9f3-140">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2f9f3-140">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
