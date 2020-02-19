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
# <a name="net-core-project-sdks"></a><span data-ttu-id="3517f-103">Sady SDK pro projekty .NET Core</span><span class="sxs-lookup"><span data-stu-id="3517f-103">.NET Core project SDKs</span></span>

<span data-ttu-id="3517f-104">Projekty .NET Core jsou přidruženy k sadě SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="3517f-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="3517f-105">Každá sada SDK projektu je sada [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild a přidružených [úloh](/visualstudio/msbuild/msbuild-tasks) , které jsou zodpovědné za kompilování, balení a publikování kódu.</span><span class="sxs-lookup"><span data-stu-id="3517f-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="3517f-106">Dostupné sady SDK</span><span class="sxs-lookup"><span data-stu-id="3517f-106">Available SDKs</span></span>

<span data-ttu-id="3517f-107">Pro .NET Core jsou k dispozici následující sady SDK:</span><span class="sxs-lookup"><span data-stu-id="3517f-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="3517f-108">ID</span><span class="sxs-lookup"><span data-stu-id="3517f-108">ID</span></span> | <span data-ttu-id="3517f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3517f-109">Description</span></span> | <span data-ttu-id="3517f-110">Sestavy</span><span class="sxs-lookup"><span data-stu-id="3517f-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="3517f-111">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="3517f-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="3517f-112">[Sada Web SDK](/aspnet/core/razor-pages/web-sdk) pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="3517f-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="3517f-113">[Sada SDK](/aspnet/core/razor-pages/sdk) .NET Core Razor</span><span class="sxs-lookup"><span data-stu-id="3517f-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="3517f-114">Sada SDK služby .NET Core Worker</span><span class="sxs-lookup"><span data-stu-id="3517f-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="3517f-115">WinForms a sada WPF SDK pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="3517f-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="3517f-116">.NET Core SDK je základní sada SDK pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3517f-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="3517f-117">Ostatní sady SDK odkazují na .NET Core SDK a projekty, které jsou přidruženy k ostatním sadám SDK, mají k dispozici všechny vlastnosti .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3517f-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="3517f-118">Webová sada SDK například závisí na .NET Core SDK i sadě Razor SDK.</span><span class="sxs-lookup"><span data-stu-id="3517f-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="3517f-119">Můžete také vytvořit vlastní sadu SDK, která se dá distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="3517f-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="3517f-120">Soubory projektu</span><span class="sxs-lookup"><span data-stu-id="3517f-120">Project files</span></span>

<span data-ttu-id="3517f-121">Projekty .NET Core jsou založeny na formátu [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="3517f-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="3517f-122">Soubory projektu, které mají rozšíření jako *. csproj* pro C# projekty a *. fsproj* pro F# projekty, jsou ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="3517f-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="3517f-123">Kořenový prvek souboru projektu MSBuild je [projektový](/msbuild/project-element-msbuild) prvek.</span><span class="sxs-lookup"><span data-stu-id="3517f-123">The root element of an MSBuild project file is the [Project](/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="3517f-124">Element `Project` má volitelný `Sdk` atribut, který určuje sadu SDK (a verzi), která se má použít.</span><span class="sxs-lookup"><span data-stu-id="3517f-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="3517f-125">Chcete-li použít nástroje .NET Core a sestavit kód, nastavte atribut `Sdk` na jedno z ID v tabulce dostupné sady [SDK](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="3517f-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="3517f-126">Pokud chcete zadat sadu SDK, která pochází z NuGet, zahrňte na konci názvu verzi nebo zadejte název a verzi v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="3517f-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="3517f-127">Dalším způsobem, jak zadat sadu SDK, je element [sady SDK](/visualstudio/msbuild/sdk-element-msbuild) na nejvyšší úrovni:</span><span class="sxs-lookup"><span data-stu-id="3517f-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="3517f-128">Odkazování na sadu SDK jedním z těchto způsobů značně zjednodušuje soubory projektu pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3517f-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="3517f-129">Při vyhodnocování projektu nástroj MSBuild přidá implicitní importy pro `Sdk.props` v horní části souboru projektu a `Sdk.targets` v dolní části.</span><span class="sxs-lookup"><span data-stu-id="3517f-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="3517f-130">V počítači s Windows se soubory *SDK. props* a *SDK. targets* dají najít ve složce *%ProgramFiles%\dotnet\sdk\\[verze] \Sdks\Microsoft.NET.Sdk\Sdk* .</span><span class="sxs-lookup"><span data-stu-id="3517f-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="3517f-131">Předběžné zpracování souboru projektu</span><span class="sxs-lookup"><span data-stu-id="3517f-131">Preprocess the project file</span></span>

<span data-ttu-id="3517f-132">Pokud je sada SDK a její cíle zahrnutá pomocí příkazu `dotnet msbuild -preprocess`, můžete zobrazit plně rozbalený projekt jako MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3517f-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="3517f-133">Přepínač [předběžného zpracování](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="3517f-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="3517f-134">Pokud má projekt více cílových rozhraní, zaměřte výsledky příkazu pouze na jednu architekturu zadáním jako vlastnost MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3517f-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="3517f-135">Například:</span><span class="sxs-lookup"><span data-stu-id="3517f-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="3517f-136">Výchozí kompilace zahrnuje</span><span class="sxs-lookup"><span data-stu-id="3517f-136">Default compilation includes</span></span>

<span data-ttu-id="3517f-137">Výchozí zahrnutí a vyloučení položek kompilace a integrovaných prostředků jsou definovány v sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="3517f-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="3517f-138">Na rozdíl od projektů, které nejsou .NET Framework SDK, není nutné zadávat tyto položky v souboru projektu, protože výchozí hodnoty se vztahují na nejběžnější případy použití.</span><span class="sxs-lookup"><span data-stu-id="3517f-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="3517f-139">To vede k menšímu množství souborů projektu, které se v případě potřeby snáze pochopí a také upraví.</span><span class="sxs-lookup"><span data-stu-id="3517f-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="3517f-140">Následující tabulka ukazuje, který prvek a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="3517f-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="3517f-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="3517f-141">Element</span></span>           | <span data-ttu-id="3517f-142">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="3517f-142">Include glob</span></span>                              | <span data-ttu-id="3517f-143">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="3517f-143">Exclude glob</span></span>                                                  | <span data-ttu-id="3517f-144">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="3517f-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="3517f-145">Kompilace</span><span class="sxs-lookup"><span data-stu-id="3517f-145">Compile</span></span>           | <span data-ttu-id="3517f-146">\*\*/\*. cs (nebo jiné jazykové rozšíření)</span><span class="sxs-lookup"><span data-stu-id="3517f-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="3517f-147">\*\*/\*. User;  \*\*/\*.\*proj;  \*\*/\*. sln;  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="3517f-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="3517f-148">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="3517f-148">N/A</span></span>                      |
| <span data-ttu-id="3517f-149">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="3517f-149">EmbeddedResource</span></span>  | <span data-ttu-id="3517f-150">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="3517f-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="3517f-151">\*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="3517f-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="3517f-152">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="3517f-152">N/A</span></span>                      |
| <span data-ttu-id="3517f-153">Žádná</span><span class="sxs-lookup"><span data-stu-id="3517f-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="3517f-154">\*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="3517f-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="3517f-155">\*\*/\*. cs; \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="3517f-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="3517f-156">`./bin` a `./obj` složky, které jsou reprezentovány vlastnostmi `$(BaseOutputPath)` a `$(BaseIntermediateOutputPath)` MSBuild, jsou ve výchozím nastavení vyloučeny z globy.</span><span class="sxs-lookup"><span data-stu-id="3517f-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="3517f-157">Vyloučení jsou reprezentovány vlastností `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="3517f-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="3517f-158">Pokud tyto položky v souboru projektu explicitně definujete, pravděpodobně se zobrazí následující chyba:</span><span class="sxs-lookup"><span data-stu-id="3517f-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="3517f-159">**Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK obsahuje ve výchozím nastavení položky kompilace z adresáře projektu. Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.**</span><span class="sxs-lookup"><span data-stu-id="3517f-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="3517f-160">Chcete-li chybu vyřešit, buď odeberte explicitní `Compile` položky, které odpovídají implicitním parametrům uvedeným v předchozí tabulce, nebo nastavte vlastnost `EnableDefaultCompileItems` na hodnotu `false`, která zakáže implicitní zahrnutí:</span><span class="sxs-lookup"><span data-stu-id="3517f-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="3517f-161">Pokud chcete určit, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanizmy nástroje MSBuild, například prvek `Content`.</span><span class="sxs-lookup"><span data-stu-id="3517f-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="3517f-162">`EnableDefaultCompileItems` zakáže pouze `Compile` globy, ale nemá vliv na jiné globy, jako je například implicitní `None` glob, které platí také pro \*položky. cs.</span><span class="sxs-lookup"><span data-stu-id="3517f-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="3517f-163">Z tohoto důvodu Průzkumník řešení v aplikaci Visual Studio zobrazovat \*. cs položky jako součást projektu, včetně položek `None`.</span><span class="sxs-lookup"><span data-stu-id="3517f-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="3517f-164">Pokud chcete zakázat implicitní `None` glob, nastavte `EnableDefaultNoneItems` na `false`:</span><span class="sxs-lookup"><span data-stu-id="3517f-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="3517f-165">Pokud chcete zakázat *všechna* implicitní globy, nastavte vlastnost `EnableDefaultItems` na `false`:</span><span class="sxs-lookup"><span data-stu-id="3517f-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="3517f-166">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="3517f-166">Customize the build</span></span>

<span data-ttu-id="3517f-167">Existují různé způsoby [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="3517f-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="3517f-168">Můžete chtít přepsat vlastnost předáním jako argumentu příkazu [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) nebo [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="3517f-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="3517f-169">Můžete také přidat vlastnost do souboru projektu nebo do souboru *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="3517f-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="3517f-170">Seznam užitečných vlastností pro projekty .NET Core naleznete v tématu [vlastnosti MSBuild pro .NET Core SDK projekty](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="3517f-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3517f-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="3517f-171">See also</span></span>

- <span data-ttu-id="3517f-172">[Nainstalovat .NET Core](../install/index.md).</span><span class="sxs-lookup"><span data-stu-id="3517f-172">[Install .NET Core](../install/index.md)</span></span>
- [<span data-ttu-id="3517f-173">Jak používat sady SDK projektů MSBuild</span><span class="sxs-lookup"><span data-stu-id="3517f-173">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
