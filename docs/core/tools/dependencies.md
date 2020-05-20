---
title: ''
description: ''
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: ''
ms.openlocfilehash: 667b2d4d68edd82a4d18c370e45ea18f4d4b379a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702840"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="2be33-101">Správa závislostí v aplikacích .NET Core</span><span class="sxs-lookup"><span data-stu-id="2be33-101">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="2be33-102">Tento článek vysvětluje, jak přidat a odebrat závislosti úpravou souboru projektu nebo pomocí rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2be33-102">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="2be33-103">\<Element PackageReference></span><span class="sxs-lookup"><span data-stu-id="2be33-103">The \<PackageReference> element</span></span>

<span data-ttu-id="2be33-104">`<PackageReference>`Prvek soubor projektu má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="2be33-104">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="2be33-105">`Include`Atribut určuje ID balíčku, který se má přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="2be33-105">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="2be33-106">`Version`Atribut určuje verzi, která má být získána.</span><span class="sxs-lookup"><span data-stu-id="2be33-106">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="2be33-107">Verze jsou zadány na základě [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="2be33-107">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="2be33-108">Pokud nejste obeznámeni s syntaxí souboru projektu, další informace naleznete v referenční dokumentaci k [projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .</span><span class="sxs-lookup"><span data-stu-id="2be33-108">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="2be33-109">Podmínky použijte k přidání závislosti, která je k dispozici pouze v určitém cíli, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2be33-109">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="2be33-110">Závislost v předchozím příkladu bude platná pouze v případě, že se pro daný cíl děje sestavení.</span><span class="sxs-lookup"><span data-stu-id="2be33-110">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="2be33-111">`$(TargetFramework)`V této podmínce je vlastnost MSBuild, která je nastavena v projektu.</span><span class="sxs-lookup"><span data-stu-id="2be33-111">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="2be33-112">Pro většinu běžných aplikací .NET Core to nemusíte dělat.</span><span class="sxs-lookup"><span data-stu-id="2be33-112">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="2be33-113">Přidat závislost úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="2be33-113">Add a dependency by editing the project file</span></span>

<span data-ttu-id="2be33-114">Chcete-li přidat závislost, přidejte `<PackageReference>` prvek uvnitř `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="2be33-114">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="2be33-115">Můžete přidat do existujícího `<ItemGroup>` nebo vytvořit nový.</span><span class="sxs-lookup"><span data-stu-id="2be33-115">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="2be33-116">Následující příklad používá výchozí projekt konzolové aplikace, který je vytvořen pomocí `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="2be33-116">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="2be33-117">Přidání závislosti pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2be33-117">Add a dependency by using the CLI</span></span>

<span data-ttu-id="2be33-118">Chcete-li přidat závislost, spusťte [dotnet add package](dotnet-add-package.md) příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2be33-118">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="2be33-119">Odstranění závislosti úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="2be33-119">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="2be33-120">Chcete-li odebrat závislost, odeberte její `<PackageReference>` prvek ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="2be33-120">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="2be33-121">Odebrání závislosti pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2be33-121">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="2be33-122">Chcete-li odebrat závislost, spusťte [dotnet remove package](dotnet-remove-package.md) příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2be33-122">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="2be33-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2be33-123">See also</span></span>

* [<span data-ttu-id="2be33-124">Odkazy na balíčky v souborech projektů</span><span class="sxs-lookup"><span data-stu-id="2be33-124">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="2be33-125">[dotnet list packagesystému](dotnet-list-package.md)</span><span class="sxs-lookup"><span data-stu-id="2be33-125">[dotnet list package command](dotnet-list-package.md)</span></span>
