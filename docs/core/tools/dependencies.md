---
title: Správa závislostí v nástroje pro .NET Core
description: Vysvětluje, jak spravovat závislosti s nástroji .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.openlocfilehash: cbeb9ad17932f6abaf14333a71fab2b4b8fd099c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749348"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="270df-103">Správa závislostí s .NET Core SDK 1.0</span><span class="sxs-lookup"><span data-stu-id="270df-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="270df-104">S přechodem na projektů .NET Core ze souboru project.json na csproj a MSBuild došlo také významnou investici, jejímž výsledkem sjednocení soubor projektu a prostředky, které umožňují sledování závislostí.</span><span class="sxs-lookup"><span data-stu-id="270df-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="270df-105">Pro projekty .NET Core je podobná nebyla jaké project.json.</span><span class="sxs-lookup"><span data-stu-id="270df-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="270df-106">Neexistuje žádný samostatný soubor JSON nebo XML, který sleduje závislostí NuGet.</span><span class="sxs-lookup"><span data-stu-id="270df-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="270df-107">S touto změnou jsme zavedli jiný typ *odkaz* do souboru csproj syntaxe volána `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="270df-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="270df-108">Tento dokument popisuje nový typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="270df-108">This document describes the new reference type.</span></span> <span data-ttu-id="270df-109">Také ukazuje, jak přidat závislost balíčku pomocí tento nový typ odkazu do projektu.</span><span class="sxs-lookup"><span data-stu-id="270df-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="270df-110">Nové \<PackageReference > – element</span><span class="sxs-lookup"><span data-stu-id="270df-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="270df-111">`<PackageReference>` Má následující základní strukturu:</span><span class="sxs-lookup"><span data-stu-id="270df-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="270df-112">Pokud jste se seznámili s nástrojem MSBuild, bude vypadat povědomě na jiné typy odkazů, které již existují.</span><span class="sxs-lookup"><span data-stu-id="270df-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="270df-113">Klíč je `Include` příkazu, který určuje id balíčku, který chcete přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="270df-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="270df-114">`<Version>` Podřízený prvek určuje verzi zobrazíte.</span><span class="sxs-lookup"><span data-stu-id="270df-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="270df-115">Verze jsou určeny podle [pravidla verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="270df-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="270df-116">Pokud nejste obeznámeni s celkovým `csproj` syntaxe, naleznete v tématu [odkaz na projekt MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) Další informace naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="270df-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="270df-117">Přidání závislostí, který je k dispozici pouze v konkrétní cíle se provádí pomocí podmínek stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="270df-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="270df-118">Výše uvedené znamená, že závislost budou pouze platná, pokud sestavení se děje to uvedeny cíle.</span><span class="sxs-lookup"><span data-stu-id="270df-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="270df-119">`$(TargetFramework)` v podmínce je vlastnost MSBuild, která je nastavena v projektu.</span><span class="sxs-lookup"><span data-stu-id="270df-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="270df-120">Pro nejčastěji používané aplikace .NET Core nemusíte to provést.</span><span class="sxs-lookup"><span data-stu-id="270df-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="270df-121">Přidání závislostí do projektu</span><span class="sxs-lookup"><span data-stu-id="270df-121">Adding a dependency to your project</span></span>
<span data-ttu-id="270df-122">Přidání závislostí pro váš projekt je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="270df-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="270df-123">Tady je příklad toho, jak přidat verzi Json.NET `9.0.1` do projektu.</span><span class="sxs-lookup"><span data-stu-id="270df-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="270df-124">Samozřejmě se vztahuje na všechny další závislosti NuGet.</span><span class="sxs-lookup"><span data-stu-id="270df-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="270df-125">Při otevření souboru projektu se zobrazí dvě nebo více `<ItemGroup>` uzly.</span><span class="sxs-lookup"><span data-stu-id="270df-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="270df-126">Všimnete si, že jeden z uzlů již `<PackageReference>` prvky v ní.</span><span class="sxs-lookup"><span data-stu-id="270df-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="270df-127">Můžete přidat nové závislosti pro tento uzel nebo vytvořte novou; To je zcela na vás jako výsledek bude stejný.</span><span class="sxs-lookup"><span data-stu-id="270df-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="270df-128">V tomto příkladu použijeme výchozí šablonu, která na základě `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="270df-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="270df-129">Toto je jednoduchou konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="270df-129">This is a simple console application.</span></span> <span data-ttu-id="270df-130">Když nám otevřít projekt, jsme nejprve vyhledat `<ItemGroup>` s již existujícím `<PackageReference>` v ní.</span><span class="sxs-lookup"><span data-stu-id="270df-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="270df-131">Potom jsme do něj přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="270df-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="270df-132">Potom jsme uložte projekt a spusťte `dotnet restore` příkaz a nainstalujte závislosti.</span><span class="sxs-lookup"><span data-stu-id="270df-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="270df-133">Úplný projekt vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="270df-133">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="270df-134">Odebrání závislostí projektu</span><span class="sxs-lookup"><span data-stu-id="270df-134">Removing a dependency from the project</span></span>
<span data-ttu-id="270df-135">Odebrání závislosti ze souboru projektu vyžaduje jednoduše odebrání `<PackageReference>` ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="270df-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
