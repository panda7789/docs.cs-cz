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
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087963"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="9f410-102">\<element > linkedConfiguration</span><span class="sxs-lookup"><span data-stu-id="9f410-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="9f410-103">Určuje konfigurační soubor, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="9f410-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="9f410-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9f410-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="9f410-105">&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9f410-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="9f410-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="9f410-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9f410-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f410-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="9f410-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f410-108">Attribute</span></span>

|           | <span data-ttu-id="9f410-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9f410-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9f410-110">**odkaz**</span><span class="sxs-lookup"><span data-stu-id="9f410-110">**href**</span></span>  | <span data-ttu-id="9f410-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9f410-111">Required attribute.</span></span><br><br><span data-ttu-id="9f410-112">Adresa URL konfiguračního souboru, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="9f410-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="9f410-113">Jediným formátem, který je podporován pro atribut **href** , je `file://`.</span><span class="sxs-lookup"><span data-stu-id="9f410-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="9f410-114">Podporují se místní soubory a soubory UNC.</span><span class="sxs-lookup"><span data-stu-id="9f410-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9f410-115">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="9f410-115">Parent element</span></span>

|     | <span data-ttu-id="9f410-116">Popis</span><span class="sxs-lookup"><span data-stu-id="9f410-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9f410-117"> **\<assemblyBinding >** Objekt</span><span class="sxs-lookup"><span data-stu-id="9f410-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="9f410-118">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9f410-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9f410-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9f410-119">Child elements</span></span>

<span data-ttu-id="9f410-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f410-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="9f410-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f410-121">Remarks</span></span>

<span data-ttu-id="9f410-122">**\<prvek > linkedConfiguration** zjednodušuje údržbu pro sestavení komponent.</span><span class="sxs-lookup"><span data-stu-id="9f410-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="9f410-123">Pokud jedna nebo více aplikací používá sestavení, které má konfigurační soubor umístěný v dobře známém umístění, mohou konfigurační soubory aplikací, které používají sestavení, použít prvek **\<linkedConfiguration >** pro zahrnutí konfiguračního souboru sestavení, a ne přímo informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="9f410-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="9f410-124">V případě, že je použito sestavení komponenty, aktualizace společného konfiguračního souboru poskytne aktualizované informace o konfiguraci pro všechny aplikace, které používají sestavení.</span><span class="sxs-lookup"><span data-stu-id="9f410-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="9f410-125">Element **\<linkedConfiguration >** není podporován pro aplikace s manifesty vedle sebe v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9f410-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="9f410-126">Použití propojených konfiguračních souborů závisí na následujících pravidlech:</span><span class="sxs-lookup"><span data-stu-id="9f410-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="9f410-127">Nastavení v zahrnutých konfiguračních souborech ovlivní pouze zásady vazby zavaděče a používají se pouze zavaděč.</span><span class="sxs-lookup"><span data-stu-id="9f410-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="9f410-128">Zahrnuté konfigurační soubory mohou mít nastavení jiné než zásady vazeb, ale tato nastavení nemají žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="9f410-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="9f410-129">Jediným formátem, který je podporován pro atribut `href`, je `file://`.</span><span class="sxs-lookup"><span data-stu-id="9f410-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="9f410-130">Podporují se místní soubory a soubory UNC.</span><span class="sxs-lookup"><span data-stu-id="9f410-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="9f410-131">Počet propojených konfigurací na konfigurační soubor není nijak omezený.</span><span class="sxs-lookup"><span data-stu-id="9f410-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="9f410-132">Všechny propojené konfigurační soubory jsou sloučeny, aby tvořily jeden soubor podobný chování direktivy `#include` v C/C++.</span><span class="sxs-lookup"><span data-stu-id="9f410-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="9f410-133">Element **\<linkedConfiguration >** je povolen pouze v konfiguračních souborech aplikace; ignoruje se v *souboru Machine. config*.</span><span class="sxs-lookup"><span data-stu-id="9f410-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="9f410-134">Byly zjištěny a ukončeny cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="9f410-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="9f410-135">To znamená, že pokud **\<linkedConfiguration >** prvky řady konfiguračních souborů tvoří smyčku, je smyčka zjištěna a zastavena.</span><span class="sxs-lookup"><span data-stu-id="9f410-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="9f410-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f410-136">Example</span></span>

<span data-ttu-id="9f410-137">Následující příklad ukazuje, jak zahrnout konfigurační soubor z místního pevného disku:</span><span class="sxs-lookup"><span data-stu-id="9f410-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9f410-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f410-138">See also</span></span>

- [<span data-ttu-id="9f410-139"> **\<assemblyBinding >** Objekt</span><span class="sxs-lookup"><span data-stu-id="9f410-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="9f410-140">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f410-140">Configuration file schema for the .NET Framework</span></span>](index.md)
