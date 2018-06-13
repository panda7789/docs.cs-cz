---
title: Správa závislostí v nástrojů .NET Core
description: Vysvětluje, jak spravovat svoje závislosti pomocí nástrojů .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.openlocfilehash: c8f40b8571523b98da55b047fea8d2bf03b390a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213659"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="f9623-103">Správa závislostí s .NET Core SDK 1.0</span><span class="sxs-lookup"><span data-stu-id="f9623-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="f9623-104">S přechodem .NET Core projektů ze souboru project.json csproj a MSBuild došlo také významné investice, jejichž výsledkem sjednocení soubor projektu a prostředky, které umožňují sledování závislostí.</span><span class="sxs-lookup"><span data-stu-id="f9623-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="f9623-105">Pro projekty .NET Core se podobá se co project.json.</span><span class="sxs-lookup"><span data-stu-id="f9623-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="f9623-106">Není k dispozici žádný samostatný soubor XML nebo JSON, který sleduje závislostí NuGet.</span><span class="sxs-lookup"><span data-stu-id="f9623-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="f9623-107">Díky této změně jste zavedli jsme taky jiný typ *odkaz* do csproj syntaxe volat `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="f9623-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="f9623-108">Tento dokument popisuje nové odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="f9623-108">This document describes the new reference type.</span></span> <span data-ttu-id="f9623-109">Také ukazuje, jak můžete přidat závislost balíčku pomocí tento nový typ odkazu do projektu.</span><span class="sxs-lookup"><span data-stu-id="f9623-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="f9623-110">Nové \<PackageReference > elementu</span><span class="sxs-lookup"><span data-stu-id="f9623-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="f9623-111">`<PackageReference>` Má následující základní strukturu:</span><span class="sxs-lookup"><span data-stu-id="f9623-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="f9623-112">Pokud jste obeznámeni s MSBuild, bude vypadat pro jiné odkazové typy, které již existují.</span><span class="sxs-lookup"><span data-stu-id="f9623-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="f9623-113">Klíč je `Include` příkaz, který určuje id balíčku, který chcete přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="f9623-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="f9623-114">`<Version>` Podřízený element určuje verzi, chcete-li získat.</span><span class="sxs-lookup"><span data-stu-id="f9623-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="f9623-115">Verze jsou určené jako za [pravidla verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="f9623-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="f9623-116">Pokud nejste obeznámeni s celkovým `csproj` syntaxe, najdete v článku [projektu MSBuild – reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) Další informace naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="f9623-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="f9623-117">Přidání závislostí, která je k dispozici pouze v konkrétní cíl se provádí pomocí podmínky jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f9623-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="f9623-118">Výše uvedené znamená, že závislost bude pouze platné, pokud je pro tento zadané cílové nedošlo k sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9623-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="f9623-119">`$(TargetFramework)` Ve stavu, je nastavený v projektu nástroje MSBuild vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f9623-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="f9623-120">Pro nejčastěji používané aplikace .NET Core nebudete muset provést.</span><span class="sxs-lookup"><span data-stu-id="f9623-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="f9623-121">Přidání závislostí do projektu</span><span class="sxs-lookup"><span data-stu-id="f9623-121">Adding a dependency to your project</span></span>
<span data-ttu-id="f9623-122">Přidání závislostí do projektu je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="f9623-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="f9623-123">Tady je příklad toho, jak přidat Json.NET verze `9.0.1` do projektu.</span><span class="sxs-lookup"><span data-stu-id="f9623-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="f9623-124">Samozřejmě se vztahuje na všechny ostatní závislostí NuGet.</span><span class="sxs-lookup"><span data-stu-id="f9623-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="f9623-125">Když otevřete soubor projektu, se zobrazí dvě nebo více `<ItemGroup>` uzlů.</span><span class="sxs-lookup"><span data-stu-id="f9623-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="f9623-126">Si všimnete, že jeden z uzlů již `<PackageReference>` elementy v ní.</span><span class="sxs-lookup"><span data-stu-id="f9623-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="f9623-127">Můžete přidat nové závislosti pro tento uzel, nebo vytvořte novou; je zcela na vás jako výsledek budou stejné.</span><span class="sxs-lookup"><span data-stu-id="f9623-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="f9623-128">V tomto příkladu použijeme výchozí šablonu, která je zrušených `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="f9623-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="f9623-129">Toto je jednoduché konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9623-129">This is a simple console application.</span></span> <span data-ttu-id="f9623-130">Když jsme otevřete projekt, nám nejdřív najít `<ItemGroup>` s již existujícími `<PackageReference>` v ní.</span><span class="sxs-lookup"><span data-stu-id="f9623-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="f9623-131">Potom jsme do něj přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="f9623-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="f9623-132">Potom jsme uložte projekt a spusťte `dotnet restore` příkaz pro instalaci závislost.</span><span class="sxs-lookup"><span data-stu-id="f9623-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="f9623-133">Úplný projekt vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f9623-133">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="f9623-134">Odebrání závislost z projektu</span><span class="sxs-lookup"><span data-stu-id="f9623-134">Removing a dependency from the project</span></span>
<span data-ttu-id="f9623-135">Odebrání závislost ze souboru projektu vyžaduje jednoduše odebrání `<PackageReference>` ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f9623-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
