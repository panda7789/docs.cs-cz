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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087963"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="f3420-102">\<linkedConfiguration> – element</span><span class="sxs-lookup"><span data-stu-id="f3420-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="f3420-103">Určuje konfigurační soubor, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="f3420-103">Specifies a configuration file to include.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a><span data-ttu-id="f3420-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3420-104">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="f3420-105">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3420-105">Attribute</span></span>

|           | <span data-ttu-id="f3420-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f3420-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f3420-107">**odkaz**</span><span class="sxs-lookup"><span data-stu-id="f3420-107">**href**</span></span>  | <span data-ttu-id="f3420-108">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3420-108">Required attribute.</span></span><br><br><span data-ttu-id="f3420-109">Adresa URL konfiguračního souboru, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="f3420-109">The URL of the configuration file to include.</span></span> <span data-ttu-id="f3420-110">Jediným formátem, který je podporován pro atribut **href** , je `file://` .</span><span class="sxs-lookup"><span data-stu-id="f3420-110">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="f3420-111">Podporují se místní soubory a soubory UNC.</span><span class="sxs-lookup"><span data-stu-id="f3420-111">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f3420-112">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="f3420-112">Parent element</span></span>

|     | <span data-ttu-id="f3420-113">Description</span><span class="sxs-lookup"><span data-stu-id="f3420-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f3420-114">**\<assemblyBinding>** Objekt</span><span class="sxs-lookup"><span data-stu-id="f3420-114">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="f3420-115">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f3420-115">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f3420-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="f3420-116">Child elements</span></span>

<span data-ttu-id="f3420-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3420-117">None</span></span>

## <a name="remarks"></a><span data-ttu-id="f3420-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3420-118">Remarks</span></span>

<span data-ttu-id="f3420-119">**\<linkedConfiguration>** Element zjednodušuje údržbu pro sestavení komponent.</span><span class="sxs-lookup"><span data-stu-id="f3420-119">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="f3420-120">Pokud jedna nebo více aplikací používá sestavení, které má konfigurační soubor umístěný v dobře známém umístění, mohou konfigurační soubory aplikací, které používají sestavení, použít **\<linkedConfiguration>** element k zahrnutí konfiguračního souboru sestavení místo toho, aby byly přímo informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f3420-120">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="f3420-121">V případě, že je použito sestavení komponenty, aktualizace společného konfiguračního souboru poskytne aktualizované informace o konfiguraci pro všechny aplikace, které používají sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3420-121">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="f3420-122">**\<linkedConfiguration>** Element není podporován pro aplikace s manifesty vedle sebe v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f3420-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="f3420-123">Použití propojených konfiguračních souborů závisí na následujících pravidlech:</span><span class="sxs-lookup"><span data-stu-id="f3420-123">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="f3420-124">Nastavení v zahrnutých konfiguračních souborech ovlivní pouze zásady vazby zavaděče a používají se pouze zavaděč.</span><span class="sxs-lookup"><span data-stu-id="f3420-124">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="f3420-125">Zahrnuté konfigurační soubory mohou mít nastavení jiné než zásady vazeb, ale tato nastavení nemají žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="f3420-125">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="f3420-126">Jediným formátem, který je podporován pro `href` atribut, je `file://` .</span><span class="sxs-lookup"><span data-stu-id="f3420-126">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="f3420-127">Podporují se místní soubory a soubory UNC.</span><span class="sxs-lookup"><span data-stu-id="f3420-127">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="f3420-128">Počet propojených konfigurací na konfigurační soubor není nijak omezený.</span><span class="sxs-lookup"><span data-stu-id="f3420-128">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="f3420-129">Všechny propojené konfigurační soubory jsou sloučeny, aby tvořily jeden soubor podobný chování `#include` direktivy v C/C++.</span><span class="sxs-lookup"><span data-stu-id="f3420-129">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="f3420-130">**\<linkedConfiguration>** Element je povolen pouze v konfiguračních souborech aplikace; ignoruje se v souboru *Machine. config*.</span><span class="sxs-lookup"><span data-stu-id="f3420-130">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="f3420-131">Byly zjištěny a ukončeny cyklické odkazy.</span><span class="sxs-lookup"><span data-stu-id="f3420-131">Circular references are detected and terminated.</span></span> <span data-ttu-id="f3420-132">To znamená, že pokud **\<linkedConfiguration>** prvky řady konfiguračních souborů tvoří smyčku, je tato smyčka zjištěna a zastavena.</span><span class="sxs-lookup"><span data-stu-id="f3420-132">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="f3420-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3420-133">Example</span></span>

<span data-ttu-id="f3420-134">Následující příklad ukazuje, jak zahrnout konfigurační soubor z místního pevného disku:</span><span class="sxs-lookup"><span data-stu-id="f3420-134">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f3420-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3420-135">See also</span></span>

- [<span data-ttu-id="f3420-136">**\<assemblyBinding>** Objekt</span><span class="sxs-lookup"><span data-stu-id="f3420-136">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="f3420-137">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f3420-137">Configuration file schema for the .NET Framework</span></span>](index.md)
