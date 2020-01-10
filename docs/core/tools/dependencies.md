---
title: Správa závislostí v nástrojích .NET Core
description: Vysvětluje, jak spravovat závislosti pomocí nástrojů .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 9c088829ce3d5197198b7ff22a1331b8baba41d7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714212"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="9832a-103">Správa závislostí pomocí .NET Core SDK 1,0</span><span class="sxs-lookup"><span data-stu-id="9832a-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="9832a-104">Když přesunete projekty .NET Core z Project. JSON na csproj a MSBuild, nastaly se významné investice také z důvodu sjednocení souboru projektu a prostředků, které umožňují sledování závislostí.</span><span class="sxs-lookup"><span data-stu-id="9832a-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="9832a-105">Pro projekty .NET Core se jedná o podobný kód jako Project. JSON.</span><span class="sxs-lookup"><span data-stu-id="9832a-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="9832a-106">Neexistuje žádný samostatný soubor JSON nebo XML, který sleduje závislosti NuGet.</span><span class="sxs-lookup"><span data-stu-id="9832a-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="9832a-107">V této změně jsme také zavedli další typ *odkazu* do syntaxe csproj s názvem `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="9832a-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="9832a-108">Tento dokument popisuje nový typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="9832a-108">This document describes the new reference type.</span></span> <span data-ttu-id="9832a-109">Také ukazuje, jak přidat závislost balíčku pomocí tohoto nového typu odkazu na váš projekt.</span><span class="sxs-lookup"><span data-stu-id="9832a-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="9832a-110">Nový \<prvek > PackageReference</span><span class="sxs-lookup"><span data-stu-id="9832a-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="9832a-111">`<PackageReference>` má následující základní strukturu:</span><span class="sxs-lookup"><span data-stu-id="9832a-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="9832a-112">Pokud jste obeznámeni s nástrojem MSBuild, bude se seznámit s dalšími typy odkazů, které již existují.</span><span class="sxs-lookup"><span data-stu-id="9832a-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="9832a-113">Klíč je příkaz `Include`, který určuje ID balíčku, který chcete přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="9832a-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="9832a-114">Podřízený prvek `<Version>` určuje verzi, která má být získána.</span><span class="sxs-lookup"><span data-stu-id="9832a-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="9832a-115">Verze jsou zadány na základě [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="9832a-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="9832a-116">Pokud nejste obeznámeni s celkovou syntaxí `csproj`, další informace naleznete v referenční dokumentaci k [projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .</span><span class="sxs-lookup"><span data-stu-id="9832a-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="9832a-117">Přidání závislosti, která je k dispozici pouze v určitém cíli, se provádí pomocí podmínek, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9832a-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="9832a-118">Výše uvedené znamená, že závislost bude platná pouze v případě, že se pro daný cíl děje sestavení.</span><span class="sxs-lookup"><span data-stu-id="9832a-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="9832a-119">`$(TargetFramework)` v podmínce je vlastnost MSBuild, která je nastavena v projektu.</span><span class="sxs-lookup"><span data-stu-id="9832a-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="9832a-120">Pro většinu běžných aplikací .NET Core to nebudete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="9832a-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="9832a-121">Přidání závislosti do projektu</span><span class="sxs-lookup"><span data-stu-id="9832a-121">Adding a dependency to your project</span></span>
<span data-ttu-id="9832a-122">Přidání závislosti do projektu je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="9832a-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="9832a-123">Tady je příklad, jak přidat Json.NET verze `9.0.1` do projektu.</span><span class="sxs-lookup"><span data-stu-id="9832a-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="9832a-124">Samozřejmě platí pro všechny ostatní závislosti NuGet.</span><span class="sxs-lookup"><span data-stu-id="9832a-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="9832a-125">Po otevření souboru projektu se zobrazí dva nebo více `<ItemGroup>`ch uzlů.</span><span class="sxs-lookup"><span data-stu-id="9832a-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="9832a-126">Všimněte si, že jeden z uzlů již obsahuje `<PackageReference>` prvky.</span><span class="sxs-lookup"><span data-stu-id="9832a-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="9832a-127">Do tohoto uzlu můžete přidat novou závislost nebo vytvořit novou. je zcela na vás, protože výsledek bude stejný.</span><span class="sxs-lookup"><span data-stu-id="9832a-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="9832a-128">V tomto příkladu použijeme výchozí šablonu, která je zahozena `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="9832a-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="9832a-129">Toto je jednoduchá Konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="9832a-129">This is a simple console application.</span></span> <span data-ttu-id="9832a-130">Po otevření projektu jsme nejdřív našli `<ItemGroup>` už existující `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="9832a-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="9832a-131">Následně do něj přidáte následující:</span><span class="sxs-lookup"><span data-stu-id="9832a-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="9832a-132">Potom uložte projekt a spuštěním příkazu `dotnet restore` pro instalaci závislosti.</span><span class="sxs-lookup"><span data-stu-id="9832a-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="9832a-133">Úplný projekt vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="9832a-133">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="9832a-134">Odebrání závislosti z projektu</span><span class="sxs-lookup"><span data-stu-id="9832a-134">Removing a dependency from the project</span></span>
<span data-ttu-id="9832a-135">Odebrání závislosti ze souboru projektu zahrnuje pouhou odebrání `<PackageReference>` ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9832a-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
