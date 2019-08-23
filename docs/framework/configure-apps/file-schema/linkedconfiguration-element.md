---
title: <linkedConfiguration> – element
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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921016"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="8300b-102">\<linkedConfiguration – element ></span><span class="sxs-lookup"><span data-stu-id="8300b-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="8300b-103">Určuje konfigurační soubor, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="8300b-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="8300b-104">[ **\<> Konfigurace**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8300b-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="8300b-105">&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="8300b-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="8300b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="8300b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8300b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8300b-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="8300b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8300b-108">Attribute</span></span>

|           | <span data-ttu-id="8300b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8300b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="8300b-110">**href**</span><span class="sxs-lookup"><span data-stu-id="8300b-110">**href**</span></span>  | <span data-ttu-id="8300b-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8300b-111">Required attribute.</span></span><br><br><span data-ttu-id="8300b-112">Adresa URL konfiguračního souboru, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="8300b-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="8300b-113">Jediným formátem, který je podporován pro atribut `file://`href, je.</span><span class="sxs-lookup"><span data-stu-id="8300b-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="8300b-114">Podporují se místní soubory a soubory UNC.</span><span class="sxs-lookup"><span data-stu-id="8300b-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="8300b-115">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="8300b-115">Parent element</span></span>

|     | <span data-ttu-id="8300b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="8300b-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8300b-117">assemblyBinding – element >  **\<** </span><span class="sxs-lookup"><span data-stu-id="8300b-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="8300b-118">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8300b-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8300b-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="8300b-119">Child elements</span></span>

<span data-ttu-id="8300b-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="8300b-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="8300b-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8300b-121">Remarks</span></span>

<span data-ttu-id="8300b-122">**\<Linkedconfiguration – >** element zjednodušuje údržbu pro sestavení komponent.</span><span class="sxs-lookup"><span data-stu-id="8300b-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="8300b-123">Pokud jeden nebo více aplikací používat sestavení, která obsahuje konfigurační soubor umístěný v dobře známého umístění, můžete použít konfigurační soubory aplikace, které používají sestavení **\<linkedconfiguration – >** Element zahrnout konfigurační soubor sestavení, nikoli přímo včetně informací o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8300b-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="8300b-124">V případě, že je použito sestavení komponenty, aktualizace společného konfiguračního souboru poskytne aktualizované informace o konfiguraci pro všechny aplikace, které používají sestavení.</span><span class="sxs-lookup"><span data-stu-id="8300b-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="8300b-125">**\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="8300b-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="8300b-126">Použití propojených konfiguračních souborů závisí na následujících pravidlech:</span><span class="sxs-lookup"><span data-stu-id="8300b-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="8300b-127">Nastavení v zahrnutých konfiguračních souborech ovlivní pouze zásady vazby zavaděče a používají se pouze zavaděč.</span><span class="sxs-lookup"><span data-stu-id="8300b-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="8300b-128">Zahrnuté konfigurační soubory mohou mít nastavení jiné než zásady vazeb, ale tato nastavení nemají žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="8300b-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="8300b-129">Jediným formátem, který je `href` podporován pro `file://`atribut, je.</span><span class="sxs-lookup"><span data-stu-id="8300b-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="8300b-130">Podporují se místní soubory a soubory UNC.</span><span class="sxs-lookup"><span data-stu-id="8300b-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="8300b-131">Počet propojených konfigurací na konfigurační soubor není nijak omezený.</span><span class="sxs-lookup"><span data-stu-id="8300b-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="8300b-132">Všechny propojené konfigurační soubory jsou sloučeny, aby tvořily jeden soubor podobný chování `#include` direktivy v C/.C++</span><span class="sxs-lookup"><span data-stu-id="8300b-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="8300b-133">**\<Linkedconfiguration – >** element je povolen pouze v konfiguračních souborech aplikace, je ignorován v *Machine.config*.</span><span class="sxs-lookup"><span data-stu-id="8300b-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="8300b-134">Byly zjištěny a ukončeny cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="8300b-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="8300b-135">To znamená, že pokud  **\<linkedConfiguration >** prvky řady konfiguračních souborů tvoří smyčku, je tato smyčka zjištěna a zastavena.</span><span class="sxs-lookup"><span data-stu-id="8300b-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="8300b-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="8300b-136">Example</span></span>

<span data-ttu-id="8300b-137">Následující příklad ukazuje, jak zahrnout konfigurační soubor z místního pevného disku:</span><span class="sxs-lookup"><span data-stu-id="8300b-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8300b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8300b-138">See also</span></span>

- [<span data-ttu-id="8300b-139">assemblyBinding – element >  **\<** </span><span class="sxs-lookup"><span data-stu-id="8300b-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="8300b-140">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8300b-140">Configuration file schema for the .NET Framework</span></span>](index.md)
