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
# <a name="manage-dependencies-in-net-core-applications"></a>Správa závislostí v aplikacích .NET Core

Tento článek vysvětluje, jak přidat a odebrat závislosti úpravou souboru projektu nebo pomocí rozhraní příkazového řádku.

## <a name="the-packagereference-element"></a>\<Element PackageReference>

`<PackageReference>`Prvek soubor projektu má následující strukturu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

`Include`Atribut určuje ID balíčku, který se má přidat do projektu. `Version`Atribut určuje verzi, která má být získána. Verze jsou zadány na základě [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Pokud nejste obeznámeni s syntaxí souboru projektu, další informace naleznete v referenční dokumentaci k [projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .

Podmínky použijte k přidání závislosti, která je k dispozici pouze v určitém cíli, jak je znázorněno v následujícím příkladu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Závislost v předchozím příkladu bude platná pouze v případě, že se pro daný cíl děje sestavení. `$(TargetFramework)`V této podmínce je vlastnost MSBuild, která je nastavena v projektu. Pro většinu běžných aplikací .NET Core to nemusíte dělat.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Přidat závislost úpravou souboru projektu

Chcete-li přidat závislost, přidejte `<PackageReference>` prvek uvnitř `<ItemGroup>` elementu. Můžete přidat do existujícího `<ItemGroup>` nebo vytvořit nový. Následující příklad používá výchozí projekt konzolové aplikace, který je vytvořen pomocí `dotnet new console` :

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

Chcete-li přidat závislost, spusťte [dotnet add package](dotnet-add-package.md) příkaz, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Odstranění závislosti úpravou souboru projektu

Chcete-li odebrat závislost, odeberte její `<PackageReference>` prvek ze souboru projektu.

## <a name="remove-a-dependency-by-using-the-cli"></a>Odebrání závislosti pomocí rozhraní příkazového řádku

Chcete-li odebrat závislost, spusťte [dotnet remove package](dotnet-remove-package.md) příkaz, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Viz také

* [Odkazy na balíčky v souborech projektů](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [dotnet list packagesystému](dotnet-list-package.md)
