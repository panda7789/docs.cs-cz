---
title: Vlastnosti nástroje MSBuild pro Microsoft. NET. SDK
description: Referenční informace o vlastnostech a položkách MSBuild, které jsou srozumitelné pro .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 39cbd18121d2b8659b2f5270f39624798f4ebbdc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810519"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a>Referenční dokumentace nástroje MSBuild pro projekty .NET Core SDK

Tato stránka je odkazem na vlastnosti a položky nástroje MSBuild, které lze použít ke konfiguraci projektů .NET Core.

> [!NOTE]
> Tato stránka je Nedokončená práce a neobsahuje seznam všech užitečných vlastností MSBuild pro .NET Core SDK. Seznam běžných vlastností MSBuild najdete v tématu [běžné vlastnosti MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Vlastnosti architektury

- [TargetFramework](#targetframework)
- [TargetFramework](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework`Vlastnost určuje cílovou verzi rozhraní .NET Framework pro aplikaci. Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFramework

Vlastnost použijte, `TargetFrameworks` Pokud chcete, aby aplikace byla cílena na více platforem. Seznam platných monikerů cílového rozhraní Framework naleznete v tématu [cílové architektury v projektech ve stylu sady SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Tato vlastnost je ignorována `TargetFramework` , pokud je zadáno (jednotné).

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

Další informace naleznete v tématu [cílová rozhraní v projektech ve stylu sady SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Tato vlastnost se vztahuje pouze na projekty používající `netstandard1.x` . Neplatí pro projekty, které používají `netstandard2.x` .

Vlastnost použijte `NetStandardImplicitPackageVersion` , pokud chcete zadat verzi rozhraní, která je nižší než verze Metapackage. Soubor projektu v následujícím příkladu cílí, `netstandard1.3` ale používá 1.6.0 verzi `NETStandard.Library` .

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a>Vlastnosti balíčku

Můžete zadat vlastnosti, například, `PackageId` , `PackageVersion` `PackageIcon` , `Title` a `Description` pro popis balíčku, který je vytvořen z projektu. Informace o těchto a dalších vlastnostech naleznete v tématu [targeting pack](/nuget/reference/msbuild-targets#pack-target).

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a>Publikování vlastností a položek

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`RuntimeIdentifier`Vlastnost umožňuje zadat jeden [identifikátor modulu runtime (RID)](../rid-catalog.md) pro projekt. Identifikátor RID umožňuje publikování samostatně zahrnutého nasazení.

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`RuntimeIdentifiers`Vlastnost umožňuje určit seznam [identifikátorů modulu runtime (identifikátorů RID)](../rid-catalog.md) oddělených středníky pro projekt. Tuto vlastnost použijte v případě, že potřebujete publikovat více modulů runtime. `RuntimeIdentifiers` se používá v čase obnovení, aby se zajistilo, že jsou správné prostředky v grafu.

> [!TIP]
> `RuntimeIdentifier` (jednotné) může poskytovat rychlejší sestavení, pokud je potřeba jenom jeden modul runtime.

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

`TrimmerRootAssembly`Položka umožňuje vyloučit sestavení z [*ořezávání*](../deploying/trim-self-contained.md). Oříznutí je proces odebrání nepoužívaných částí modulu runtime ze zabalené aplikace. V některých případech může oříznutí nesprávně odebrat požadované odkazy.

Následující kód XML vylučuje `System.Security` sestavení z ořezávání.

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost`Vlastnost byla představena ve verzi 2.1.400 .NET Core SDK. Určuje, zda je pro nasazení vytvořen nativní spustitelný soubor. Pro samostatně obsažená nasazení je vyžadován nativní spustitelný soubor.

V rozhraní .NET Core 3,0 a novějších verzích je ve výchozím nastavení vytvořen spustitelný soubor závislý na rozhraní. Nastavte `UseAppHost` vlastnost na hodnotu `false` pro zakázání generování spustitelného souboru.

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

Další informace o nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Vlastnosti kompilace

- [EmbeddedResourceUseDependentUponConvention](#embeddedresourceusedependentuponconvention)
- [Langversion –](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a>EmbeddedResourceUseDependentUponConvention

`EmbeddedResourceUseDependentUponConvention`Vlastnost určuje, zda jsou názvy souborů manifestu prostředku generovány z informací o typu ve zdrojových souborech, které jsou umístěny společně se soubory prostředků. Například pokud je *Form1. resx* ve stejné složce jako *Form1.cs*a `EmbeddedResourceUseDependentUponConvention` je nastavena na `true` , vygenerovaný soubor *. Resources* převezme svůj název od prvního typu, který je definován v *Form1.cs*. Například pokud `MyNamespace.Form1` je první typ definovaný v *Form1.cs*, vygenerovaný název souboru je *MyNamespace. Form1. Resources*.

> [!NOTE]
> `LogicalName`V případě, že `ManifestResourceName` `DependentUpon` jsou pro položku zadána metadata, `EmbeddedResource` vygenerovaný název souboru manifestu pro tento soubor prostředků je založen na těchto metadatech.

Ve výchozím nastavení je v novém projektu .NET Core Tato vlastnost nastavena na `true` . Pokud `false` `LogicalName` je pro položku v souboru projektu nastavena na, a ne, nebo, je `ManifestResourceName` `DependentUpon` `EmbeddedResource` název souboru manifestu prostředku založen na kořenovém oboru názvů pro projekt a relativní cestě k souboru souboru *. resx* . Další informace naleznete v tématu [jak jsou pojmenovány soubory manifestu prostředků](../resources/manifest-file-names.md).

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a>Langversion –

`LangVersion`Vlastnost umožňuje zadat konkrétní verzi programovacího jazyka. Například pokud chcete mít přístup k funkcím verze Preview jazyka C#, nastavte `LangVersion` na `preview` .

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Další informace najdete v tématu [Správa verzí jazyka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="code-analysis-properties"></a>Vlastnosti analýzy kódu

### <a name="analysislevel"></a>AnalysisLevel

`AnalysisLevel`Vlastnost umožňuje určit úroveň analýzy kódu. Například pokud chcete mít přístup k analyzátorům kódu ve verzi Preview, nastavte `AnalysisLevel` na `preview` . Výchozí hodnota je `latest`.

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

V následující tabulce jsou uvedeny dostupné možnosti.

| Hodnota | Význam |
|-|-|
| `latest` | Použijí se nejnovější analyzátory kódu, které byly vydány. Tato možnost je výchozí. |
| `preview` | Používají se nejnovější analyzátory kódu, a to i v případě, že jsou ve verzi Preview. |
| `5.0` | Použije se sada pravidel, která byla povolena pro vydání .NET 5,0, i v případě, že jsou k dispozici novější pravidla. |
| `5` | Použije se sada pravidel, která byla povolena pro vydání .NET 5,0, i v případě, že jsou k dispozici novější pravidla. |

### <a name="codeanalysistreatwarningsaserrors"></a>CodeAnalysisTreatWarningsAsErrors

`CodeAnalysisTreatWarningsAsErrors`Vlastnost umožňuje nakonfigurovat, zda by měla být upozornění analýzy kódu zpracována jako upozornění a přerušeno sestavení. Použijete-li `-warnaserror` příznak při sestavování projektů, jsou upozornění [analýzy kódu .NET](../../fundamentals/productivity/code-analysis.md) také považována za chyby. Pokud chcete, aby upozornění kompilátoru byla považována za chyby, můžete `CodeAnalysisTreatWarningsAsErrors` vlastnost MSBuild nastavit na `false` v souboru projektu.

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a>EnableNETAnalyzers

[Analýza kódu .NET](../../fundamentals/productivity/code-analysis.md) je ve výchozím nastavení povolená pro projekty, které cílí na .NET 5,0 nebo novější. Můžete povolit analýzu kódu .NET pro projekty, které jsou cíleny na starší verze rozhraní .NET, nastavením `EnableNETAnalyzers` vlastnosti na hodnotu true. Chcete-li zakázat analýzu kódu v jakémkoli projektu, nastavte tuto vlastnost na `false` .

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> Další způsob, jak povolit analýzu kódu .NET v projektech, které cílí na verze .NET starší než .NET 5,0, je nastavit vlastnost [AnalysisLevel](#analysislevel) na hodnotu `latest` .

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

`ConcurrentGarbageCollection`Vlastnost konfiguruje, zda je povoleno [uvolňování paměti na pozadí (souběžně)](../../standard/garbage-collection/background-gc.md) . Nastavte hodnotu na `false` Zakázat uvolňování paměti na pozadí. Další informace najdete v tématu [GC na pozadí](../run-time-config/garbage-collector.md#background-gc).

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

`InvariantGlobalization`Vlastnost nakonfiguruje, jestli aplikace běží v režimu *invariantní globalizace* , což znamená, že nemá přístup k datům specifickým pro jazykovou verzi. Nastavte hodnotu pro `true` spuštění v režimu invariantní globalizace. Další informace naleznete v tématu [invariantní režim](../run-time-config/globalization.md#invariant-mode).

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection`Vlastnost konfiguruje systém uvolňování paměti pro vložení odstraněných segmentů paměti v pohotovostním seznamu pro budoucí použití nebo uvolnění. Nastavením hodnoty určíte `true` , aby systém uvolňování paměti umístil segmenty do seznamu pohotovostních hodnot. Další informace najdete v tématu [uchování virtuálního počítače](../run-time-config/garbage-collector.md#retain-vm).

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

`ServerGarbageCollection`Vlastnost konfiguruje, zda aplikace používá [uvolňování paměti pracovní stanice nebo uvolňování paměti serveru](../../standard/garbage-collection/workstation-server-gc.md). Nastavte hodnotu na `true` použít uvolňování paměti serveru. Další informace najdete v tématu [pracovní stanice vs. Server](../run-time-config/garbage-collector.md#workstation-vs-server).

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads`Vlastnost konfiguruje maximální počet vláken pro fond pracovních vláken. Další informace najdete v tématu [maximální počet vláken](../run-time-config/threading.md#maximum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads`Vlastnost konfiguruje minimální počet vláken pro fond pracovních vláken. Další informace najdete v tématu [minimální počet vláken](../run-time-config/threading.md#minimum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a>TieredCompilation

`TieredCompilation`Vlastnost určuje, zda kompilátor JIT (just-in-time) používá [vrstvenou kompilaci](../whats-new/dotnet-core-3-0.md#tiered-compilation). Nastavte hodnotu na `false` Zakázat vrstvenou kompilaci. Další informace najdete v tématu [vrstvená kompilace](../run-time-config/compilation.md#tiered-compilation).

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

`TieredCompilationQuickJit`Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT. Nastavením hodnoty na `false` zakážete rychlou JIT. Další informace najdete v tématu [rychlá JIT](../run-time-config/compilation.md#quick-jit).

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

`TieredCompilationQuickJitForLoops`Vlastnost konfiguruje, zda kompilátor JIT používá rychlou JIT v metodách, které obsahují smyčky. Nastavte hodnotu na, `true` Chcete-li povolit rychlou JIT v metodách, které obsahují smyčky. Další informace najdete v tématu [rychlá JIT pro smyčky](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a>Odkazování vlastností a položek

- [AssetTargetFallback](#assettargetfallback)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [Odkaz](#reference)
- [Obnovit vlastnosti](#restore-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

`AssetTargetFallback`Vlastnost umožňuje zadat další kompatibilní verze rozhraní pro odkazy na projekt a balíčky NuGet. Pokud například zadáte závislost balíčku pomocí, `PackageReference` ale tento balíček neobsahuje prostředky, které jsou kompatibilní s vašimi projekty `TargetFramework` , `AssetTargetFallback` vlastnost se dostane do hry. Kompatibilita odkazovaného balíčku je znovu zkontrolována pomocí každé cílové architektury, která je určena v `AssetTargetFallback` .

Můžete nastavit `AssetTargetFallback` vlastnost na jednu nebo více [cílových verzí rozhraní .NET Framework](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

`PackageReference`Položka definuje odkaz na balíček NuGet.

`Include`Atribut určuje ID balíčku. `Version`Atribut určuje verzi nebo rozsah verzí. Informace o tom, jak zadat minimální verzi, maximální verzi, rozsah nebo přesnou shodu, najdete v tématu [rozsahy verzí](/nuget/concepts/package-versioning#version-ranges). Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets` , `ExcludeAssets` a `PrivateAssets` .

Fragment souboru projektu v následujícím příkladu odkazuje na balíček [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

Další informace naleznete v tématu [odkazy na balíčky v souborech projektu](/nuget/consume-packages/package-references-in-project-files).

### <a name="projectreference"></a>ProjectReference

`ProjectReference`Položka definuje odkaz na jiný projekt. Odkazovaný projekt je přidán jako závislost balíčku NuGet, to znamená, že je zpracována jako `PackageReference` .

`Include`Atribut určuje cestu k projektu. Do odkazu na projekt můžete také přidat následující metadata: `IncludeAssets` , `ExcludeAssets` a `PrivateAssets` .

Fragment souboru projektu v následujícím příkladu odkazuje na projekt s názvem `Project2` .

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a>Referenční informace

`Reference`Položka definuje odkaz na soubor sestavení.

`Include`Atribut určuje název souboru a `HintPath` metadata určují cestu k sestavení.

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a>Obnovit vlastnosti

Při obnovení odkazovaného balíčku se nainstaluje všechny jeho přímé závislosti a všechny závislosti těchto závislostí. Obnovení balíčku můžete přizpůsobit zadáním vlastností, jako jsou `RestorePackagesPath` a `RestoreIgnoreFailedSources` . Další informace o těchto a dalších vlastnostech naleznete v tématu [Restore Target](/nuget/reference/msbuild-targets#restore-target).

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Běžné vlastnosti nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Vlastnosti nástroje MSBuild pro balíček NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Vlastnosti nástroje MSBuild pro obnovení NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build)
