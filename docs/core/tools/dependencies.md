---
title: "Správa závislostí v nástrojů .NET Core"
description: "Vysvětluje, jak spravovat svoje závislosti pomocí nástrojů .NET Core."
keywords: "Rozhraní příkazového řádku, rozšiřitelnosti, vlastní příkazy, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.workload: dotnetcore
ms.openlocfilehash: a064ae72a077583cfb544309700555ebd9d398a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="393a8-104">Správa závislostí s .NET Core SDK 1.0</span><span class="sxs-lookup"><span data-stu-id="393a8-104">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="393a8-105">S přechodem .NET Core projektů ze souboru project.json csproj a MSBuild došlo také významné investice, jejichž výsledkem sjednocení soubor projektu a prostředky, které umožňují sledování závislostí.</span><span class="sxs-lookup"><span data-stu-id="393a8-105">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="393a8-106">Pro projekty .NET Core se podobá se co project.json.</span><span class="sxs-lookup"><span data-stu-id="393a8-106">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="393a8-107">Není k dispozici žádný samostatný soubor XML nebo JSON, který sleduje závislostí NuGet.</span><span class="sxs-lookup"><span data-stu-id="393a8-107">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="393a8-108">Díky této změně jste zavedli jsme taky jiný typ *odkaz* do csproj syntaxe volat `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="393a8-108">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="393a8-109">Tento dokument popisuje nové odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="393a8-109">This document describes the new reference type.</span></span> <span data-ttu-id="393a8-110">Také ukazuje, jak můžete přidat závislost balíčku pomocí tento nový typ odkazu do projektu.</span><span class="sxs-lookup"><span data-stu-id="393a8-110">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="393a8-111">Nové \<PackageReference > elementu</span><span class="sxs-lookup"><span data-stu-id="393a8-111">The new \<PackageReference> element</span></span>
<span data-ttu-id="393a8-112">`<PackageReference>` Má následující základní strukturu:</span><span class="sxs-lookup"><span data-stu-id="393a8-112">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="393a8-113">Pokud jste obeznámeni s MSBuild, bude vypadat pro jiné odkazové typy, které již existují.</span><span class="sxs-lookup"><span data-stu-id="393a8-113">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="393a8-114">Klíč je `Include` příkaz, který určuje id balíčku, který chcete přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="393a8-114">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="393a8-115">`<Version>` Podřízený element určuje verzi, chcete-li získat.</span><span class="sxs-lookup"><span data-stu-id="393a8-115">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="393a8-116">Verze jsou určené jako za [pravidla verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="393a8-116">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="393a8-117">Pokud nejste obeznámeni s celkovým `csproj` syntaxe, najdete v článku [projektu MSBuild – reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) Další informace naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="393a8-117">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="393a8-118">Přidání závislostí, která je k dispozici pouze v konkrétní cíl se provádí pomocí podmínky jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="393a8-118">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="393a8-119">Výše uvedené znamená, že závislost bude pouze platné, pokud je pro tento zadané cílové nedošlo k sestavení.</span><span class="sxs-lookup"><span data-stu-id="393a8-119">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="393a8-120">`$(TargetFramework)` Ve stavu, je nastavený v projektu nástroje MSBuild vlastnost.</span><span class="sxs-lookup"><span data-stu-id="393a8-120">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="393a8-121">Pro nejčastěji používané aplikace .NET Core nebudete muset provést.</span><span class="sxs-lookup"><span data-stu-id="393a8-121">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="393a8-122">Přidání závislostí do projektu</span><span class="sxs-lookup"><span data-stu-id="393a8-122">Adding a dependency to your project</span></span>
<span data-ttu-id="393a8-123">Přidání závislostí do projektu je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="393a8-123">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="393a8-124">Tady je příklad toho, jak přidat Json.NET verze `9.0.1` do projektu.</span><span class="sxs-lookup"><span data-stu-id="393a8-124">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="393a8-125">Samozřejmě se vztahuje na všechny ostatní závislostí NuGet.</span><span class="sxs-lookup"><span data-stu-id="393a8-125">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="393a8-126">Když otevřete soubor projektu, se zobrazí dvě nebo více `<ItemGroup>` uzlů.</span><span class="sxs-lookup"><span data-stu-id="393a8-126">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="393a8-127">Si všimnete, že jeden z uzlů již `<PackageReference>` elementy v ní.</span><span class="sxs-lookup"><span data-stu-id="393a8-127">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="393a8-128">Můžete přidat nové závislosti pro tento uzel, nebo vytvořte novou; je zcela na vás jako výsledek budou stejné.</span><span class="sxs-lookup"><span data-stu-id="393a8-128">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="393a8-129">V tomto příkladu použijeme výchozí šablonu, která je zrušených `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="393a8-129">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="393a8-130">Toto je jednoduché konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="393a8-130">This is a simple console application.</span></span> <span data-ttu-id="393a8-131">Když jsme otevřete projekt, nám nejdřív najít `<ItemGroup>` s již existujícími `<PackageReference>` v ní.</span><span class="sxs-lookup"><span data-stu-id="393a8-131">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="393a8-132">Potom jsme do něj přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="393a8-132">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="393a8-133">Potom jsme uložte projekt a spusťte `dotnet restore` příkaz pro instalaci závislost.</span><span class="sxs-lookup"><span data-stu-id="393a8-133">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="393a8-134">Úplný projekt vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="393a8-134">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="393a8-135">Odebrání závislost z projektu</span><span class="sxs-lookup"><span data-stu-id="393a8-135">Removing a dependency from the project</span></span>
<span data-ttu-id="393a8-136">Odebrání závislost ze souboru projektu vyžaduje jednoduše odebrání `<PackageReference>` ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="393a8-136">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
