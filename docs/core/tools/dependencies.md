---
title: Správa závislostí v .NET Core
description: Vysvětluje, jak spravovat závislosti projektu pro aplikaci .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157242"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="07636-103">Správa závislostí v aplikacích .NET Core</span><span class="sxs-lookup"><span data-stu-id="07636-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="07636-104">Tento článek vysvětluje, jak přidat a odebrat závislosti úpravou souboru projektu nebo pomocí rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="07636-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="07636-105">Element \<PackageReference ></span><span class="sxs-lookup"><span data-stu-id="07636-105">The \<PackageReference> element</span></span>

<span data-ttu-id="07636-106">Prvek souboru projektu `<PackageReference>` má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="07636-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="07636-107">Atribut `Include` Určuje ID balíčku, který se má přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="07636-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="07636-108">Atribut `Version` určuje verzi, která má být získána.</span><span class="sxs-lookup"><span data-stu-id="07636-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="07636-109">Verze jsou zadány na základě [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="07636-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="07636-110">Pokud nejste obeznámeni s syntaxí souboru projektu, další informace naleznete v referenční dokumentaci k [projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .</span><span class="sxs-lookup"><span data-stu-id="07636-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="07636-111">Podmínky použijte k přidání závislosti, která je k dispozici pouze v určitém cíli, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="07636-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="07636-112">Závislost v předchozím příkladu bude platná pouze v případě, že se pro daný cíl děje sestavení.</span><span class="sxs-lookup"><span data-stu-id="07636-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="07636-113">`$(TargetFramework)` v podmínce je vlastnost MSBuild, která je nastavena v projektu.</span><span class="sxs-lookup"><span data-stu-id="07636-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="07636-114">Pro většinu běžných aplikací .NET Core to nemusíte dělat.</span><span class="sxs-lookup"><span data-stu-id="07636-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="07636-115">Přidat závislost úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="07636-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="07636-116">Chcete-li přidat závislost, přidejte `<PackageReference>` element uvnitř elementu `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="07636-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="07636-117">Můžete přidat do existujícího `<ItemGroup>` nebo vytvořit nový.</span><span class="sxs-lookup"><span data-stu-id="07636-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="07636-118">Následující příklad používá výchozí projekt konzolové aplikace, který je vytvořen pomocí `dotnet new console`:</span><span class="sxs-lookup"><span data-stu-id="07636-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="07636-119">Přidání závislosti pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="07636-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="07636-120">Chcete-li přidat závislost, spusťte příkaz [dotnet add package](dotnet-add-package.md) , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="07636-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="07636-121">Odstranění závislosti úpravou souboru projektu</span><span class="sxs-lookup"><span data-stu-id="07636-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="07636-122">Chcete-li odebrat závislost, odeberte její `<PackageReference>` element ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="07636-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="07636-123">Odebrání závislosti pomocí rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="07636-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="07636-124">Chcete-li odebrat závislost, spusťte příkaz [dotnet remove package](dotnet-remove-package.md) , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="07636-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="07636-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="07636-125">See also</span></span>

* [<span data-ttu-id="07636-126">Balíčky NuGet v souborech projektu</span><span class="sxs-lookup"><span data-stu-id="07636-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="07636-127">[dotnet list package – příkaz](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="07636-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
