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
# <a name="manage-dependencies-in-net-core-applications"></a>Správa závislostí v základních aplikacích rozhraní .NET

Tento článek vysvětluje, jak přidat a odebrat závislosti úpravou souboru projektu nebo pomocí příkazového příkazového příkazu.

## <a name="the-packagereference-element"></a>Prvek \<PackageReference>

Prvek `<PackageReference>` souboru projektu má následující strukturu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Atribut `Include` určuje ID balíčku, který má být do projektu přidejte. Atribut `Version` určuje verzi, kterou chcete získat. Verze jsou určeny podle [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Pokud nejste obeznámeni se syntaxí souboru projektu, naleznete další informace v dokumentaci [k odkazu na projekt MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)

Pomocí podmínek můžete přidat závislost, která je dostupná pouze v určitém cíli, jak je znázorněno v následujícím příkladu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Závislost v předchozím příkladu bude platná pouze v případě, že sestavení prodaný cíl. V `$(TargetFramework)` podmínce je MSBuild vlastnost, která je nastavena v projektu. Pro většinu běžných aplikací .NET Core to není nutné provést.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Přidání závislosti úpravou souboru projektu

Chcete-li přidat závislost, `<PackageReference>` přidejte `<ItemGroup>` prvek uvnitř prvku. Můžete přidat do `<ItemGroup>` existující nebo vytvořit nový. Následující příklad používá výchozí projekt aplikace konzoly, který je vytvořen `dotnet new console`:

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

## <a name="add-a-dependency-by-using-the-cli"></a>Přidání závislosti pomocí zapisování/li se konzauma

Chcete-li přidat závislost, [dotnet add package](dotnet-add-package.md) spusťte příkaz, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Odebrání závislosti úpravou souboru projektu

Chcete-li odebrat závislost, odeberte její `<PackageReference>` prvek ze souboru projektu.

## <a name="remove-a-dependency-by-using-the-cli"></a>Odebrání závislosti pomocí zapisování/li se konzauma

Chcete-li odstranit závislost, [dotnet remove package](dotnet-remove-package.md) spusťte příkaz, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Viz také

* [Balíčky NuGet v souborech projektu](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list packagePříkaz](dotnet-remove-package.md)
