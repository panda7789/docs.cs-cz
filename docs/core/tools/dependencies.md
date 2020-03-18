---
title: Správa závislostí v rozhraní .NET Core
description: Vysvětluje, jak spravovat závislosti projektu pro aplikaci .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399145"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="4eb3a-103">Správa závislostí v základních aplikacích rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="4eb3a-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="4eb3a-104">Tento článek vysvětluje, jak přidat a odebrat závislosti úpravou souboru projektu nebo pomocí příkazového příkazového příkazu.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="4eb3a-105">Prvek \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="4eb3a-105">The \<PackageReference> element</span></span>

<span data-ttu-id="4eb3a-106">Prvek `<PackageReference>` souboru projektu má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="4eb3a-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="4eb3a-107">Atribut `Include` určuje ID balíčku, který má být do projektu přidejte.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="4eb3a-108">Atribut `Version` určuje verzi, kterou chcete získat.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="4eb3a-109">Verze jsou určeny podle [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="4eb3a-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="4eb3a-110">Pokud nejste obeznámeni se syntaxí souboru projektu, naleznete další informace v dokumentaci [k odkazu na projekt MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)</span><span class="sxs-lookup"><span data-stu-id="4eb3a-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="4eb3a-111">Pomocí podmínek můžete přidat závislost, která je dostupná pouze v určitém cíli, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4eb3a-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="4eb3a-112">Závislost v předchozím příkladu bude platná pouze v případě, že sestavení prodaný cíl.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="4eb3a-113">V `$(TargetFramework)` podmínce je MSBuild vlastnost, která je nastavena v projektu.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="4eb3a-114">Pro většinu běžných aplikací .NET Core to není nutné provést.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="4eb3a-115">Přidání závislosti úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="4eb3a-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="4eb3a-116">Chcete-li přidat závislost, `<PackageReference>` přidejte `<ItemGroup>` prvek uvnitř prvku.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="4eb3a-117">Můžete přidat do `<ItemGroup>` existující nebo vytvořit nový.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="4eb3a-118">Následující příklad používá výchozí projekt aplikace konzoly, který je vytvořen `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="4eb3a-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="4eb3a-119">Přidání závislosti pomocí zapisování/li se konzauma</span><span class="sxs-lookup"><span data-stu-id="4eb3a-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="4eb3a-120">Chcete-li přidat závislost, [dotnet add package](dotnet-add-package.md) spusťte příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4eb3a-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="4eb3a-121">Odebrání závislosti úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="4eb3a-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="4eb3a-122">Chcete-li odebrat závislost, odeberte její `<PackageReference>` prvek ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="4eb3a-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="4eb3a-123">Odebrání závislosti pomocí zapisování/li se konzauma</span><span class="sxs-lookup"><span data-stu-id="4eb3a-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="4eb3a-124">Chcete-li odstranit závislost, [dotnet remove package](dotnet-remove-package.md) spusťte příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4eb3a-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="4eb3a-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4eb3a-125">See also</span></span>

* [<span data-ttu-id="4eb3a-126">Balíčky NuGet v souborech projektu</span><span class="sxs-lookup"><span data-stu-id="4eb3a-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="4eb3a-127">[dotnet list packagePříkaz](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="4eb3a-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
