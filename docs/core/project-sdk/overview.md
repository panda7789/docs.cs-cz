---
title: Přehled sady Project SDK pro .NET Core
titleSuffix: ''
description: Přečtěte si o sadách SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 88ec1bf2c4917c69b80b997d090219097694d2bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206049"
---
# <a name="net-core-project-sdks"></a>Sady SDK pro projekty .NET Core

Projekty .NET Core jsou přidruženy k sadě SDK (Software Development Kit). Každá *sada SDK projektu* je sada [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild a přidružených [úloh](/visualstudio/msbuild/msbuild-tasks) , které jsou zodpovědné za kompilování, balení a publikování kódu. Projekt, který odkazuje na sadu SDK projektu, se někdy označuje jako *projekt ve stylu sady SDK*.

## <a name="available-sdks"></a>Dostupné sady SDK

Pro .NET Core jsou k dispozici následující sady SDK:

| ID | Popis | Sestavy|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET Core SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | [Sada Web SDK](/aspnet/core/razor-pages/web-sdk) pro .NET Core | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | [Sada SDK](/aspnet/core/razor-pages/sdk) .NET Core Razor |
| `Microsoft.NET.Sdk.Worker` | Sada SDK služby .NET Core Worker |
| `Microsoft.NET.Sdk.WindowsDesktop` | WinForms a sada WPF SDK pro .NET Core |

.NET Core SDK je základní sada SDK pro .NET Core. Ostatní sady SDK odkazují na .NET Core SDK a projekty, které jsou přidruženy k ostatním sadám SDK, mají k dispozici všechny vlastnosti .NET Core SDK. Webová sada SDK například závisí na .NET Core SDK i sadě Razor SDK.

Můžete také vytvořit vlastní sadu SDK, která se dá distribuovat přes NuGet.

## <a name="project-files"></a>Soubory projektu

Projekty .NET Core jsou založeny na formátu [MSBuild](/visualstudio/msbuild/msbuild) . Soubory projektu, které mají rozšíření jako *. csproj* pro projekty C# a *. fsproj* pro projekty F #, jsou ve formátu XML. Kořenový prvek souboru projektu MSBuild je [projektový](/visualstudio/msbuild/project-element-msbuild) prvek. `Project`Element má volitelný `Sdk` atribut, který určuje sadu SDK (a verze), která se má použít. Chcete-li použít nástroje .NET Core a sestavit kód, nastavte `Sdk` atribut na jedno z ID v tabulce [dostupných sad SDK](#available-sdks) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Pokud chcete zadat sadu SDK, která pochází z NuGet, zahrňte na konci názvu verzi nebo zadejte název a verzi v souboru *Global. JSON* .

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Dalším způsobem, jak zadat sadu SDK, je element [sady SDK](/visualstudio/msbuild/sdk-element-msbuild) na nejvyšší úrovni:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Odkazování na sadu SDK jedním z těchto způsobů značně zjednodušuje soubory projektu pro .NET Core. Při vyhodnocování projektu nástroj MSBuild přidá implicitní importy do `Sdk.props` horní části souboru projektu a `Sdk.targets` v dolní části.

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> V počítači s Windows se soubory *SDK. props* a *SDK. targets* dají najít ve složce *%ProgramFiles%\dotnet\sdk \\ [Version] \Sdks\Microsoft.NET.Sdk\Sdk* .

### <a name="preprocess-the-project-file"></a>Předběžné zpracování souboru projektu

Úplný rozbalený projekt se zobrazí po zobrazení nástroje MSBuild po sadě SDK a jeho cílech pomocí `dotnet msbuild -preprocess` příkazu. Přepínač [předběžného zpracování](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) příkazu ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu.

Pokud má projekt více cílových rozhraní, zaměřte výsledky příkazu pouze na jednu architekturu zadáním jako vlastnost MSBuild. Příklad:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Výchozí kompilace zahrnuje

Výchozí zahrnutí a vyloučení položek kompilace, integrovaných prostředků a `None` položek je definováno v sadě SDK. Na rozdíl od projektů, které nejsou .NET Framework SDK, není nutné zadávat tyto položky v souboru projektu, protože výchozí hodnoty se vztahují na nejběžnější případy použití. Tím se soubor projektu zmenší a v případě potřeby bude snazší pochopit a upravovat.

Následující tabulka ukazuje, které prvky a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v .NET Core SDK:

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Sestavení           | \*\*/\*cs (nebo jiné jazykové rozšíření) | \*\*/\*uživatelský  \*\*/\*.\* Souhrn  \*\*/\*. SLN  \*\*/\*. vssscc  | –                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc     | –                      |
| Žádné              | \*\*/\*                                   | \*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc     | \*\*/\*cs \*\*/\*. RESX |

> [!NOTE]
> `./bin`Složky a `./obj` , které jsou reprezentovány `$(BaseOutputPath)` vlastnostmi a nástroje `$(BaseIntermediateOutputPath)` MSBuild, jsou ve výchozím nastavení vyloučeny z globy. Vyloučení jsou reprezentovány vlastností `$(DefaultItemExcludes)` .

#### <a name="build-errors"></a>Chyby sestavení

Pokud explicitně definujete některou z těchto položek v souboru projektu, pravděpodobně se zobrazí chyba Build "NETSDK1022", která bude vypadat přibližně takto:

  > Byly zahrnuty duplicitní položky Compile. Sada .NET SDK obsahuje ve výchozím nastavení položky kompilovat z adresáře projektu. Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.

  > Byly zahrnuty duplicitní položky ' EmbeddedResource '. Sada .NET SDK obsahuje ve výchozím nastavení položky "EmbeddedResource" z adresáře projektu. Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultEmbeddedResourceItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.

Chcete-li tyto chyby vyřešit, proveďte jednu z následujících akcí:

- Odeberte explicitní `Compile` položky, `EmbeddedResource` nebo, `None` které odpovídají implicitním těm uvedeným v předchozí tabulce.

- Nastavte `EnableDefaultItems` vlastnost tak, aby `false` se zakázalo zahrnutí všech implicitních souborů:

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  Pokud chcete určit soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanizmy nástroje MSBuild, například `Content` prvek.

- Selektivně zakažte pouze `Compile` , `EmbeddedResource` nebo `None` globy nastavením `EnableDefaultCompileItems` `EnableDefaultEmbeddedResourceItems` vlastnosti, nebo `EnableDefaultNoneItems` na `false` :

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  Pokud zakážete pouze `Compile` globy, Průzkumník řešení v aplikaci Visual Studio stále zobrazuje \* položky. cs jako součást projektu, které jsou zahrnuty jako `None` položky. Pokud chcete zakázat implicitní `None` glob, nastavte `EnableDefaultNoneItems` na hodnotu `false` příliš.

## <a name="customize-the-build"></a>Přizpůsobení sestavení

Existují různé způsoby [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build). Můžete chtít přepsat vlastnost předáním jako argumentu příkazu [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) nebo [dotnet](../tools/index.md) . Můžete také přidat vlastnost do souboru projektu nebo do souboru *Directory. Build. props* . Seznam užitečných vlastností pro projekty .NET Core naleznete v tématu [Reference k MSBuild pro .NET Core SDK projekty](msbuild-props.md).

### <a name="custom-targets"></a>Vlastní cíle

Projekty .NET Core můžou zabalit vlastní cíle a vlastnosti MSBuild pro použití projekty, které balíček využívají. Tento typ rozšiřitelnosti použijte v případě, že chcete:

- Rozšíří proces sestavení.
- Přístup k artefaktům procesu sestavení, jako je například vygenerované soubory.
- Zkontrolujte konfiguraci, pod kterou je vyvoláno sestavení.

Vlastní cíle sestavení nebo vlastnosti můžete přidat umístěním souborů ve formuláři `<package_id>.targets` nebo `<package_id>.props` (například `Contoso.Utility.UsefulStuff.targets` ) do složky *sestavení* projektu.

Následující kód XML je fragmentem ze souboru *. csproj* , který instruuje příkaz, který [`dotnet pack`](../tools/dotnet-pack.md) se má zabalit. `<ItemGroup Label="dotnet pack instructions">`Prvek umístí soubory cílů do složky *sestavení* uvnitř balíčku. `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Prvek umístí sestavení a soubory *. JSON* do složky *sestavení* .

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

Chcete-li využívat vlastní cíl v projektu, přidejte `PackageReference` prvek, který odkazuje na balíček a jeho verzi. Na rozdíl od nástrojů je balíček vlastních cílů zahrnut v uzávěrce náročného projektu.

Můžete nakonfigurovat, jak se má používat vlastní cíl. Vzhledem k tomu, že se jedná o cíl MSBuild, může záviset na daném cíli, spustit po jiném cíli nebo být ručně vyvolán pomocí `dotnet msbuild -t:<target-name>` příkazu. Chcete-li však zajistit lepší činnost koncového uživatele, můžete kombinovat nástroje pro jednotlivé projekty a vlastní cíle. V tomto scénáři akceptuje Nástroj pro každý projekt jakékoli parametry, které jsou potřeba, a překládá se na požadované [`dotnet msbuild`](../tools/dotnet-msbuild.md) vyvolání, které provádí cíl. Ukázku tohoto druhu součinnosti si můžete prohlédnout v úložišti [ukázek MVP 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) v [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.

## <a name="see-also"></a>Viz také

- [Instalace .NET Core](../install/index.md)
- [Jak používat sady SDK projektů MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Balíčky vlastních cílů a vlastností MSBuild balíčku pomocí NuGet](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
