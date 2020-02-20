---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503811"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Vlastnosti nástroje MSBuild pro projekty .NET Core SDK

Tato stránka popisuje vlastnosti nástroje MSBuild pro konfiguraci projektů .NET Core.

> [!NOTE]
> Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK. Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Vlastnosti architektury

- [TargetFramework](#targetframework)
- [TargetFramework](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>targetFramework

Vlastnost `TargetFramework` určuje cílovou verzi rozhraní .NET Framework pro aplikaci, která implicitně odkazuje na [Metapackage](../packages.md#metapackages). Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFramework

Vlastnost `TargetFrameworks` použijte v případě, že chcete, aby aplikace byla cílena na více platforem. Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Tato vlastnost je ignorována, pokud je zadána `TargetFramework` (v jednotném čísle).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Tato vlastnost se vztahuje pouze na projekty používající `netstandard1.x`. Neplatí pro projekty, které používají `netstandard2.x`.

Vlastnost `NetStandardImplicitPackageVersion` použijte, pokud chcete zadat verzi rozhraní, která je nižší než verze [Metapackage](../packages.md#metapackages) . Soubor projektu v následujícím příkladu cílí na `netstandard1.3`, ale používá verzi 1.6.0 `NETStandard.Library`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Vlastnosti publikování

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

Vlastnost `RuntimeIdentifier` umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt. Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

Vlastnost `RuntimeIdentifiers` umožňuje zadat seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) pro daný projekt oddělený středníkem. Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime. `RuntimeIdentifiers` se používá v době obnovení, aby se zajistilo, že jsou správné prostředky v grafu.

> [!TIP]
> `RuntimeIdentifier` (jednotné) může poskytovat rychlejší sestavení, je-li vyžadován pouze jeden modul runtime.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

Vlastnost `UseAppHost` byla představena ve verzi 2.1.400 .NET Core SDK. Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor. Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.

V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní. Nastavte vlastnost `UseAppHost` na `false`, aby se zakázalo generování spustitelného souboru.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Vlastnosti kompilace

### <a name="langversion"></a>Langversion –

Vlastnost `LangVersion` umožňuje zadat konkrétní verzi programovacího jazyka. Pokud například chcete získat přístup k C# funkcím verze Preview, nastavte `LangVersion` na `preview`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Další informace najdete v tématu [ C# jazyková verze](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="nuget-packages"></a>Balíčky NuGet

- [PackageReference](#packagereference)

### <a name="packagereference"></a>PackageReference

Položka `PackageReference` umožňuje zadat závislost NuGet. Například můžete chtít odkazovat na jeden balíček místo [Metapackage](../packages.md#metapackages). Atribut `Include` Určuje ID balíčku. Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).

### <a name="pack-and-restore-targets"></a>Cíle sad a obnovení

MSBuild 15,1 představil `pack` a `restore` cíle pro vytváření a obnovování balíčků NuGet v rámci sestavení. Informace o vlastnostech MSBuild pro tyto cíle, včetně `PackageTargetFallback`, najdete v tématu [sada NuGet Pack a obnovení jako cíle MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Běžné vlastnosti nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Vlastnosti nástroje MSBuild pro balíček NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Vlastnosti nástroje MSBuild pro obnovení NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build)
