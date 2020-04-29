---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 105b7d67ea24515ea88481cb4a4fe42d2a03cfd0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506783"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Vlastnosti nástroje MSBuild pro projekty .NET Core SDK

Tato stránka popisuje vlastnosti nástroje MSBuild pro konfiguraci projektů .NET Core.

> [!NOTE]
> Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK. Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Vlastnosti architektury

- [TargetFramework](#targetframework)
- [TargetFramework](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework` Vlastnost určuje cílovou verzi rozhraní .NET Framework pro aplikaci, která implicitně odkazuje na [Metapackage](../packages.md#metapackages). Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFramework

Vlastnost použijte `TargetFrameworks` , pokud chcete, aby aplikace byla cílena na více platforem. Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Tato vlastnost je ignorována `TargetFramework` , pokud je zadáno (jednotné).

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
> Tato vlastnost se vztahuje pouze na projekty `netstandard1.x`používající. Neplatí pro projekty, které používají `netstandard2.x`.

`NetStandardImplicitPackageVersion` Vlastnost použijte, pokud chcete zadat verzi rozhraní, která je nižší než verze [Metapackage](../packages.md#metapackages) . Soubor projektu v následujícím příkladu cílí `netstandard1.3` , ale používá 1.6.0 verzi. `NETStandard.Library`

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
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`RuntimeIdentifier` Vlastnost umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt. Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`RuntimeIdentifiers` Vlastnost umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) oddělených středníky pro projekt. Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime. `RuntimeIdentifiers`se používá v čase obnovení, aby se zajistilo, že jsou správné prostředky v grafu.

> [!TIP]
> `RuntimeIdentifier`(jednotné) může poskytovat rychlejší sestavení, pokud je potřeba jenom jeden modul runtime.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

`TrimmerRootAssembly` Položka umožňuje vyloučit sestavení z [*ořezávání*](../deploying/trim-self-contained.md). Oříznutí je proces odebrání nepoužívaných částí modulu runtime ze zabalené aplikace. V některých případech může oříznutí nesprávně odebrat požadované odkazy.

Následující kód XML vylučuje `System.Security` sestavení z ořezávání.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` Vlastnost byla představena ve verzi 2.1.400 .NET Core SDK. Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor. Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.

V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní. Nastavte `UseAppHost` vlastnost na `false` hodnotu pro zakázání generování spustitelného souboru.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Vlastnosti kompilace

- [Langversion –](#langversion)

### <a name="langversion"></a>Langversion –

`LangVersion` Vlastnost umožňuje zadat konkrétní verzi programovacího jazyka. Například pokud chcete mít přístup k funkcím verze Preview jazyka C#, `LangVersion` nastavte `preview`na.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Další informace najdete v tématu [Správa verzí jazyka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="run-time-configuration-properties"></a>Vlastnosti konfigurace runtime

Můžete nakonfigurovat některé chování za běhu zadáním vlastností MSBuild v souboru projektu aplikace. Informace o jiných způsobech konfigurace chování za běhu najdete v tématu [nastavení konfigurace prostředí .NET Core](../run-time-config/index.md)runtime.

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [InvariantGlobalization](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [TieredCompilationQuickJit](#tieredcompilationquickjit)
- [TieredCompilationQuickJitForLoops](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

`ConcurrentGarbageCollection` Vlastnost konfiguruje, zda je povoleno [uvolňování paměti na pozadí (souběžně)](../../standard/garbage-collection/background-gc.md) . Nastavte hodnotu na zakázat `false` uvolňování paměti na pozadí. Další informace najdete v tématu [System. GC. souběžné/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

`InvariantGlobalization` Vlastnost nakonfiguruje, jestli aplikace běží v režimu *invariantní globalizace* , což znamená, že nemá přístup k datům specifickým pro jazykovou verzi. Nastavte hodnotu `true` pro spuštění v režimu invariantní globalizace. Další informace naleznete v tématu [invariantní režim](../run-time-config/globalization.md#invariant-mode).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection` Vlastnost konfiguruje systém uvolňování paměti pro vložení odstraněných segmentů paměti v pohotovostním seznamu pro budoucí použití nebo uvolnění. Nastavením hodnoty určíte `true` , aby systém uvolňování paměti umístil segmenty do seznamu pohotovostních hodnot. Další informace najdete v tématu [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

`ServerGarbageCollection` Vlastnost konfiguruje, zda aplikace používá [uvolňování paměti pracovní stanice nebo uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md). Nastavte hodnotu `true` na použít uvolňování paměti serveru. Další informace najdete v tématu [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads` Vlastnost konfiguruje maximální počet vláken pro fond pracovních vláken. Další informace najdete v tématu [maximální počet vláken](../run-time-config/threading.md#maximum-threads).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads` Vlastnost konfiguruje minimální počet vláken pro fond pracovních vláken. Další informace najdete v tématu [minimální počet vláken](../run-time-config/threading.md#minimum-threads).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a>TieredCompilation

`TieredCompilation` Vlastnost určuje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation). Nastavte hodnotu `false` na zakázat vrstvenou kompilaci. Další informace najdete v tématu [vrstvená kompilace](../run-time-config/compilation.md#tiered-compilation).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

`TieredCompilationQuickJit` Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT. Nastavením hodnoty `false` na zakážete rychlou JIT. Další informace najdete v tématu [rychlá JIT](../run-time-config/compilation.md#quick-jit).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

`TieredCompilationQuickJitForLoops` Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky. Nastavte hodnotu na, `true` Chcete-li povolit rychlou JIT v metodách, které obsahují smyčky. Další informace najdete v tématu [rychlá JIT pro smyčky](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a>Balíčky NuGet

- [PackageReference](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

`PackageReference` Položka umožňuje zadat závislost NuGet. Například můžete chtít odkazovat na jeden balíček místo [Metapackage](../packages.md#metapackages). `Include` Atribut určuje ID balíčku. Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).

### <a name="assettargetfallback"></a>AssetTargetFallback

`AssetTargetFallback` Vlastnost umožňuje určit další kompatibilní verze rozhraní pro projekty, na které projekt odkazuje, a balíčky NuGet, které váš projekt spotřebovává. Pokud například zadáte závislost balíčku pomocí `PackageReference` , ale tento balíček neobsahuje prostředky, které jsou kompatibilní s vašimi projekty `TargetFramework`, vlastnost se `AssetTargetFallback` dostane do hry. Kompatibilita odkazovaného balíčku je znovu zkontrolována pomocí každé cílové architektury, která je určena v `AssetTargetFallback`.

Můžete nastavit `AssetTargetFallback` vlastnost na jednu nebo více [cílových verzí rozhraní .NET Framework](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Cíle sad a obnovení

Byl zaveden `pack` MSBuild 15,1 `restore` a cílený pro vytváření a obnovování balíčků NuGet v rámci sestavení. Informace o vlastnostech MSBuild pro tyto cíle, včetně `PackageTargetFallback`, najdete v tématu [sada NuGet Pack a obnovení jako cíle MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Běžné vlastnosti nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Vlastnosti nástroje MSBuild pro balíček NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Vlastnosti nástroje MSBuild pro obnovení NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build)
