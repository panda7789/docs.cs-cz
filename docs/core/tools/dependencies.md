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
# <a name="manage-dependencies-in-net-core-applications"></a>Správa závislostí v aplikacích .NET Core

Tento článek vysvětluje, jak přidat a odebrat závislosti úpravou souboru projektu nebo pomocí rozhraní příkazového řádku.

## <a name="the-packagereference-element"></a>Element \<PackageReference >

Prvek souboru projektu `<PackageReference>` má následující strukturu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Atribut `Include` Určuje ID balíčku, který se má přidat do projektu. Atribut `Version` určuje verzi, která má být získána. Verze jsou zadány na základě [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Pokud nejste obeznámeni s syntaxí souboru projektu, další informace naleznete v referenční dokumentaci k [projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .

Podmínky použijte k přidání závislosti, která je k dispozici pouze v určitém cíli, jak je znázorněno v následujícím příkladu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Závislost v předchozím příkladu bude platná pouze v případě, že se pro daný cíl děje sestavení. `$(TargetFramework)` v podmínce je vlastnost MSBuild, která je nastavena v projektu. Pro většinu běžných aplikací .NET Core to nemusíte dělat.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Přidat závislost úpravou souboru projektu

Chcete-li přidat závislost, přidejte `<PackageReference>` element uvnitř elementu `<ItemGroup>`. Můžete přidat do existujícího `<ItemGroup>` nebo vytvořit nový. Následující příklad používá výchozí projekt konzolové aplikace, který je vytvořen pomocí `dotnet new console`:

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

## <a name="add-a-dependency-by-using-the-cli"></a>Přidání závislosti pomocí rozhraní příkazového řádku

Chcete-li přidat závislost, spusťte příkaz [dotnet add package](dotnet-add-package.md) , jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Odstranění závislosti úpravou souboru projektu

Chcete-li odebrat závislost, odeberte její `<PackageReference>` element ze souboru projektu.

## <a name="remove-a-dependency-by-using-the-cli"></a>Odebrání závislosti pomocí rozhraní příkazového řádku

Chcete-li odebrat závislost, spusťte příkaz [dotnet remove package](dotnet-remove-package.md) , jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Viz také

* [Balíčky NuGet v souborech projektu](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list package – příkaz](dotnet-remove-package.md)
