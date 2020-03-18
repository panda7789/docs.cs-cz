---
title: Vlastnosti MSBuild pro sadu Microsoft.NET.Sdk
description: Odkaz na vlastnosti MSBuild, které jsou chápány sadou .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399180"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Vlastnosti msbuild pro projekty sady .NET Core SDK

Tato stránka popisuje vlastnosti MSBuild pro konfiguraci projektů .NET Core.

> [!NOTE]
> Tato stránka je nedokončená a neuvádí všechny užitečné vlastnosti MSBuild pro sadu .NET Core SDK. Seznam běžných vlastností MSBuild naleznete [v tématu Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Vlastnosti rozhraní Framework

- [Targetframework](#targetframework)
- [Cílové rámce](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>Targetframework

Vlastnost `TargetFramework` určuje verzi cílového rozhraní pro aplikaci, která implicitně odkazuje na [metabalíček](../packages.md#metapackages). Seznam platných zástupných názvů cílové architektury naleznete v tématu [Cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Další informace naleznete v tématu [Target frameworks in SDK-style projects](../../standard/frameworks.md).

### <a name="targetframeworks"></a>Cílové rámce

Vlastnost `TargetFrameworks` použijte, když chcete, aby vaše aplikace cílila na více platforem. Seznam platných zástupných názvů cílové architektury naleznete v tématu [Cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Tato vlastnost je `TargetFramework` ignorována, pokud je zadán (singulární) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Další informace naleznete v tématu [Target frameworks in SDK-style projects](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Tato vlastnost se vztahuje `netstandard1.x`pouze na projekty pomocí . Nevztahuje se na projekty, které používají `netstandard2.x`.

`NetStandardImplicitPackageVersion` Vlastnost použijte, pokud chcete zadat verzi architektury, která je nižší než verze [metabalíčku.](../packages.md#metapackages) Soubor projektu v následujícím `netstandard1.3` příkladu cíle, ale používá `NETStandard.Library`verzi 1.6.0 .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Publikovat vlastnosti

- [Identifikátor runtime](#runtimeidentifier)
- [Identifikátory runtime](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>Identifikátor runtime

Vlastnost `RuntimeIdentifier` umožňuje zadat jeden [identifikátor runtime (RID)](../rid-catalog.md) pro projekt. Rid umožňuje publikování samostatné nasazení.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>Identifikátory runtime

Vlastnost `RuntimeIdentifiers` umožňuje zadat seznam [identifikátorů runtime (RID)](../rid-catalog.md) pro projekt oddělený středníkem. Tuto vlastnost použijte, pokud potřebujete publikovat pro více runtimes. `RuntimeIdentifiers`se používá v době obnovení, aby bylo zajištěno, že správné prostředky jsou v grafu.

> [!TIP]
> `RuntimeIdentifier`(singulární) může poskytnout rychlejší sestavení, když je vyžadován pouze jeden runtime.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

Vlastnost `UseAppHost` byla zavedena ve verzi 2.1.400 sady .NET Core SDK. Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor. Nativní spustitelný soubor je vyžadován pro samostatná nasazení.

V rozhraní .NET Core 3.0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní. Nastavte `UseAppHost` vlastnost `false` zakázat generování spustitelného souboru.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Další informace o nasazení naleznete v tématu [.NET Core application deployment](../deploying/index.md).

## <a name="compile-properties"></a>Kompilovat vlastnosti

### <a name="langversion"></a>LangVersion

Vlastnost `LangVersion` umožňuje určit konkrétní verzi programovacího jazyka. Například pokud chcete přístup k c# `LangVersion` náhled `preview`funkce, nastavte na .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Další informace naleznete v [tématu C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="nuget-packages"></a>Balíčky NuGet

- [Odkaz na balíček](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>Odkaz na balíček

Položka `PackageReference` umožňuje zadat závislost NuGet. Můžete například odkazovat na jeden balíček namísto [metabalíčku](../packages.md#metapackages). Atribut `Include` určuje ID balíčku. Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Další informace naleznete [v tématu Odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).

### <a name="assettargetfallback"></a>AssetTargetFallback

Vlastnost `AssetTargetFallback` umožňuje zadat další verze architektury kompatibilní pro projekty, které odkazuje na váš projekt a Balíčky NuGet, které váš projekt spotřebovává. Například pokud zadáte závislost balíčku `PackageReference` pomocí, ale tento balíček neobsahuje prostředky, `TargetFramework`které `AssetTargetFallback` jsou kompatibilní s projekty , vlastnost vstoupí do hry. Kompatibilita odkazovaného balíčku je znovu kontrolována pomocí každého `AssetTargetFallback`cílového rozhraní, které je zadáno v aplikaci .

Vlastnost můžete `AssetTargetFallback` nastavit na jednu nebo více [verzí cílové architektury](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Sbalit a obnovit cíle

MSBuild 15.1 `pack` zavedena a `restore` cíle pro vytváření a obnovení nuget balíčky jako součást sestavení. Informace o vlastnostech MSBuild pro `PackageTargetFallback`tyto cíle, včetně naleznete v [tématu NuGet pack a restore as MSBuild targets](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Viz také

- [Odkaz na schéma msbuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Vlastnosti MSBuild pro balíček NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Vlastnosti MSBuild pro obnovení NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build)
