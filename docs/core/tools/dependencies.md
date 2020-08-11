---
title: Správa závislostí v .NET Core
description: Vysvětluje, jak spravovat závislosti projektu pro aplikaci .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 02/25/2020
ms.openlocfilehash: 2aeedb56f774b51076764c2772eb02b2fa095d92
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062857"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="ccbef-103">Správa závislostí v aplikacích .NET Core</span><span class="sxs-lookup"><span data-stu-id="ccbef-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="ccbef-104">Tento článek vysvětluje, jak přidat a odebrat závislosti úpravou souboru projektu nebo pomocí rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ccbef-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="ccbef-105">\<PackageReference>Element</span><span class="sxs-lookup"><span data-stu-id="ccbef-105">The \<PackageReference> element</span></span>

<span data-ttu-id="ccbef-106">`<PackageReference>`Prvek soubor projektu má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="ccbef-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="ccbef-107">`Include`Atribut určuje ID balíčku, který se má přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="ccbef-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="ccbef-108">`Version`Atribut určuje verzi, která má být získána.</span><span class="sxs-lookup"><span data-stu-id="ccbef-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="ccbef-109">Verze jsou zadány na základě [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="ccbef-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="ccbef-110">Pokud nejste obeznámeni s syntaxí souboru projektu, další informace naleznete v referenční dokumentaci k [projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .</span><span class="sxs-lookup"><span data-stu-id="ccbef-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="ccbef-111">Podmínky použijte k přidání závislosti, která je k dispozici pouze v určitém cíli, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccbef-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="ccbef-112">Závislost v předchozím příkladu bude platná pouze v případě, že se pro daný cíl děje sestavení.</span><span class="sxs-lookup"><span data-stu-id="ccbef-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="ccbef-113">`$(TargetFramework)`V této podmínce je vlastnost MSBuild, která je nastavena v projektu.</span><span class="sxs-lookup"><span data-stu-id="ccbef-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="ccbef-114">Pro většinu běžných aplikací .NET Core to nemusíte dělat.</span><span class="sxs-lookup"><span data-stu-id="ccbef-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="ccbef-115">Přidat závislost úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="ccbef-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="ccbef-116">Chcete-li přidat závislost, přidejte `<PackageReference>` prvek uvnitř `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ccbef-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="ccbef-117">Můžete přidat do existujícího `<ItemGroup>` nebo vytvořit nový.</span><span class="sxs-lookup"><span data-stu-id="ccbef-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="ccbef-118">Následující příklad používá výchozí projekt konzolové aplikace, který je vytvořen pomocí `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="ccbef-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="ccbef-119">Přidání závislosti pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ccbef-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="ccbef-120">Chcete-li přidat závislost, spusťte [dotnet add package](dotnet-add-package.md) příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccbef-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="ccbef-121">Odstranění závislosti úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="ccbef-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="ccbef-122">Chcete-li odebrat závislost, odeberte její `<PackageReference>` prvek ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ccbef-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="ccbef-123">Odebrání závislosti pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ccbef-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="ccbef-124">Chcete-li odebrat závislost, spusťte [dotnet remove package](dotnet-remove-package.md) příkaz, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccbef-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="ccbef-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccbef-125">See also</span></span>

* [<span data-ttu-id="ccbef-126">Odkazy na balíčky v souborech projektů</span><span class="sxs-lookup"><span data-stu-id="ccbef-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [<span data-ttu-id="ccbef-127">dotnet list packagesystému</span><span class="sxs-lookup"><span data-stu-id="ccbef-127">dotnet list package command</span></span>](dotnet-list-package.md)
