---
title: Přehled sady Project SDK pro .NET Core
description: Přečtěte si o sadách SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: b1b839f81b1b4a8d20dbb34d3d2fc000c64acb8a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453802"
---
# <a name="net-core-project-sdks"></a>Sady SDK pro projekty .NET Core

Projekty .NET Core jsou přidruženy k sadě SDK (Software Development Kit). Každá sada SDK projektu je sada [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild a přidružených [úloh](/visualstudio/msbuild/msbuild-tasks) , které jsou zodpovědné za kompilování, balení a publikování kódu.

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

Projekty .NET Core jsou založeny na formátu [MSBuild](/visualstudio/msbuild/msbuild) . Soubory projektu, které mají rozšíření jako *. csproj* pro C# projekty a *. fsproj* pro F# projekty, jsou ve formátu XML. Kořenový prvek souboru projektu MSBuild je [projektový](/msbuild/project-element-msbuild) prvek. Element `Project` má volitelný `Sdk` atribut, který určuje sadu SDK (a verzi), která se má použít. Chcete-li použít nástroje .NET Core a sestavit kód, nastavte atribut `Sdk` na jedno z ID v tabulce dostupné sady [SDK](#available-sdks) .

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

Odkazování na sadu SDK jedním z těchto způsobů značně zjednodušuje soubory projektu pro .NET Core. Při vyhodnocování projektu nástroj MSBuild přidá implicitní importy pro `Sdk.props` v horní části souboru projektu a `Sdk.targets` v dolní části.

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
> V počítači s Windows se soubory *SDK. props* a *SDK. targets* dají najít ve složce *%ProgramFiles%\dotnet\sdk\\[verze] \Sdks\Microsoft.NET.Sdk\Sdk* .

### <a name="preprocess-the-project-file"></a>Předběžné zpracování souboru projektu

Pokud je sada SDK a její cíle zahrnutá pomocí příkazu `dotnet msbuild -preprocess`, můžete zobrazit plně rozbalený projekt jako MSBuild. Přepínač [předběžného zpracování](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu.

Pokud má projekt více cílových rozhraní, zaměřte výsledky příkazu pouze na jednu architekturu zadáním jako vlastnost MSBuild. Například:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Výchozí kompilace zahrnuje

Výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků jsou definovány v sadě SDK. Na rozdíl od projektů, které nejsou .NET Framework SDK, není nutné zadávat tyto položky v souboru projektu, protože výchozí hodnoty se vztahují na nejběžnější případy použití. To vede k menšímu množství souborů projektu, které se v případě potřeby snáze pochopí a také upraví.

Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v .NET Core SDK:

| Prvek           | Zahrnout glob                              | Vyloučit glob                                                  | Odebrat glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Kompilace           | \*\*/\*. cs (nebo jiné jazykové rozšíření) | \*\*/\*. User;  \*\*/\*.\*proj;  \*\*/\*. sln;  \*\*/\*. vssscc  | Není k dispozici                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. vssscc     | Není k dispozici                      |
| Žádná              | \*\*/\*                                   | \*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. vssscc     | \*\*/\*. cs; \*\*/\*. resx |

> [!NOTE]
> `./bin` a `./obj` složky, které jsou reprezentovány vlastnostmi `$(BaseOutputPath)` a `$(BaseIntermediateOutputPath)` MSBuild, jsou ve výchozím nastavení vyloučeny z globy. Vyloučení jsou reprezentovány vlastností `$(DefaultItemExcludes)`.

Pokud tyto položky v souboru projektu explicitně definujete, pravděpodobně se zobrazí následující chyba:

**Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu. Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.**

Chcete-li chybu vyřešit, buď odeberte explicitní `Compile` položky, které odpovídají implicitním parametrům uvedeným v předchozí tabulce, nebo nastavte vlastnost `EnableDefaultCompileItems` na hodnotu `false`, která zakáže implicitní zahrnutí:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanizmy nástroje MSBuild, například prvek `Content`.

`EnableDefaultCompileItems` zakáže pouze `Compile` globy, ale nemá vliv na jiné globy, jako je například implicitní `None` glob, které platí také pro \*položky. cs. Z tohoto důvodu Průzkumník řešení v aplikaci Visual Studio zobrazovat \*. cs položky jako součást projektu, včetně položek `None`. Pokud chcete zakázat implicitní `None` glob, nastavte `EnableDefaultNoneItems` na `false`:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Pokud chcete zakázat *všechna* implicitní globy, nastavte vlastnost `EnableDefaultItems` na `false`:

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Přizpůsobení sestavení

Existují různé způsoby [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build). Můžete chtít přepsat vlastnost předáním jako argumentu příkazu [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) nebo [dotnet](../tools/index.md) . Můžete také přidat vlastnost do souboru projektu nebo do souboru *Directory. Build. props* . Seznam užitečných vlastností pro projekty .NET Core naleznete v tématu [vlastnosti MSBuild pro .NET Core SDK projekty](msbuild-props.md).

## <a name="see-also"></a>Viz také

- [Nainstalovat .NET Core](../install/index.md).
- [Jak používat sady SDK projektů MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
