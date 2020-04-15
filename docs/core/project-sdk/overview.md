---
title: Přehled sady SDK základního projektu .NET
description: Další informace o sadách SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: d0ac01dca31dffea482745126e00c34b1da20774
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389671"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="0ea09-103">Sady SDK core aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="0ea09-103">.NET Core project SDKs</span></span>

<span data-ttu-id="0ea09-104">.NET Core projekty jsou spojeny s sadou pro vývoj softwaru (SDK).</span><span class="sxs-lookup"><span data-stu-id="0ea09-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="0ea09-105">Každý *projekt SDK* je sada [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild a přidružené [úkoly,](/visualstudio/msbuild/msbuild-tasks) které jsou zodpovědné za kompilaci, balení a publikování kódu.</span><span class="sxs-lookup"><span data-stu-id="0ea09-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="0ea09-106">Projekt, který odkazuje na projekt SDK je někdy označován jako *projekt ve stylu sady SDK*.</span><span class="sxs-lookup"><span data-stu-id="0ea09-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="0ea09-107">Dostupné sady SDK</span><span class="sxs-lookup"><span data-stu-id="0ea09-107">Available SDKs</span></span>

<span data-ttu-id="0ea09-108">Pro službu .NET Core jsou k dispozici následující sady SDK:</span><span class="sxs-lookup"><span data-stu-id="0ea09-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="0ea09-109">ID</span><span class="sxs-lookup"><span data-stu-id="0ea09-109">ID</span></span> | <span data-ttu-id="0ea09-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0ea09-110">Description</span></span> | <span data-ttu-id="0ea09-111">Repo</span><span class="sxs-lookup"><span data-stu-id="0ea09-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="0ea09-112">Sada SDK jádra .NET</span><span class="sxs-lookup"><span data-stu-id="0ea09-112">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="0ea09-113">Sada .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="0ea09-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="0ea09-114">Sada [SDK .NET](/aspnet/core/razor-pages/sdk) Core Razor</span><span class="sxs-lookup"><span data-stu-id="0ea09-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="0ea09-115">Sada SDK základní pracovní služby .NET</span><span class="sxs-lookup"><span data-stu-id="0ea09-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="0ea09-116">Základní winforms rozhraní .NET a sada WPF SDK</span><span class="sxs-lookup"><span data-stu-id="0ea09-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="0ea09-117">Sada .NET Core SDK je základní sadou SDK pro jádro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ea09-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="0ea09-118">Ostatní sady SDK odkazují na sadu .NET Core SDK a projekty, které jsou přidruženy k ostatním sadám SDK, mají všechny vlastnosti sady .NET Core SDK, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0ea09-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="0ea09-119">Web SDK, například závisí na .NET Core SDK a Razor SDK.</span><span class="sxs-lookup"><span data-stu-id="0ea09-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="0ea09-120">Můžete také vytvářet vlastní sdk, které mohou být distribuovány prostřednictvím NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ea09-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="0ea09-121">Soubory projektu</span><span class="sxs-lookup"><span data-stu-id="0ea09-121">Project files</span></span>

<span data-ttu-id="0ea09-122">Základní projekty .NET jsou založeny na formátu [MSBuild.](/visualstudio/msbuild/msbuild)</span><span class="sxs-lookup"><span data-stu-id="0ea09-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="0ea09-123">Soubory projektu, které mají rozšíření jako *.csproj* pro projekty C# a *.fsproj* pro projekty F#, jsou ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="0ea09-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="0ea09-124">Kořenový prvek souboru projektu MSBuild je prvek [Project.](/visualstudio/msbuild/project-element-msbuild)</span><span class="sxs-lookup"><span data-stu-id="0ea09-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="0ea09-125">Prvek `Project` má volitelný `Sdk` atribut, který určuje, který SDK (a verze) použít.</span><span class="sxs-lookup"><span data-stu-id="0ea09-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="0ea09-126">Chcete-li použít nástroje .NET Core a `Sdk` vytvořit kód, nastavte atribut na jedno z ID v tabulce [Dostupné sady SDK.](#available-sdks)</span><span class="sxs-lookup"><span data-stu-id="0ea09-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="0ea09-127">Chcete-li zadat sadu SDK, která pochází z NuGet, zadejte verzi na konci názvu nebo zadejte název a verzi v souboru *global.json.*</span><span class="sxs-lookup"><span data-stu-id="0ea09-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="0ea09-128">Dalším způsobem, jak určit sdk je s nejvyšší úrovně [Sdk](/visualstudio/msbuild/sdk-element-msbuild) prvek:</span><span class="sxs-lookup"><span data-stu-id="0ea09-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="0ea09-129">Odkazování na sdk jedním z těchto způsobů výrazně zjednodušuje soubory projektu pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ea09-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="0ea09-130">Při vyhodnocování projektu MSBuild `Sdk.props` přidá implicitní importy `Sdk.targets` v horní části souboru projektu a v dolní části.</span><span class="sxs-lookup"><span data-stu-id="0ea09-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="0ea09-131">V počítači se systémem Windows lze soubory *Sdk.props* a *Sdk.targets* nalézt ve složce *%ProgramFiles%\dotnet\sdk\\[verze]\Sdks\Microsoft.NET.Sdk\Sdk.*</span><span class="sxs-lookup"><span data-stu-id="0ea09-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="0ea09-132">Předběžné zpracování souboru projektu</span><span class="sxs-lookup"><span data-stu-id="0ea09-132">Preprocess the project file</span></span>

<span data-ttu-id="0ea09-133">Můžete vidět plně rozšířený projekt jako MSBuild vidí po SDK a jeho `dotnet msbuild -preprocess` cíle jsou zahrnuty pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="0ea09-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="0ea09-134">[Předprocesový](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) přepínač [`dotnet msbuild`](../tools/dotnet-msbuild.md) příkazu zobrazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky k sestavení, aniž by skutečně stavěly projekt.</span><span class="sxs-lookup"><span data-stu-id="0ea09-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="0ea09-135">Pokud projekt má více cílových architektur, zaměřte výsledky příkazu pouze na jeden rámec zadáním jako vlastnost MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0ea09-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="0ea09-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0ea09-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="0ea09-137">Výchozí kompilace zahrnuje</span><span class="sxs-lookup"><span data-stu-id="0ea09-137">Default compilation includes</span></span>

<span data-ttu-id="0ea09-138">Výchozí zahrnuje a vylučuje pro kompilaci položky a vložené prostředky jsou definovány v sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="0ea09-138">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="0ea09-139">Na rozdíl od projektů, které nejsou sdk.net framework, není nutné zadat tyto položky v souboru projektu, protože výchozí pokrytí většiny běžných případů použití.</span><span class="sxs-lookup"><span data-stu-id="0ea09-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="0ea09-140">To vede k menším souborům projektu, které jsou srozumitelnější a v případě potřeby ručně upravovány.</span><span class="sxs-lookup"><span data-stu-id="0ea09-140">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="0ea09-141">V následující tabulce je uvedeno, který prvek a které globs jsou [zahrnuty](https://en.wikipedia.org/wiki/Glob_(programming)) a vyloučeny do sady .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="0ea09-141">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="0ea09-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="0ea09-142">Element</span></span>           | <span data-ttu-id="0ea09-143">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="0ea09-143">Include glob</span></span>                              | <span data-ttu-id="0ea09-144">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="0ea09-144">Exclude glob</span></span>                                                  | <span data-ttu-id="0ea09-145">Odstranit glob</span><span class="sxs-lookup"><span data-stu-id="0ea09-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="0ea09-146">Kompilaci</span><span class="sxs-lookup"><span data-stu-id="0ea09-146">Compile</span></span>           | <span data-ttu-id="0ea09-147">\*\*/\*.cs (nebo jiná jazyková rozšíření)</span><span class="sxs-lookup"><span data-stu-id="0ea09-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="0ea09-148">\*\*/\*.user;  \*\*/\*. \*proj;  \* \* /.sln; \*  \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0ea09-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="0ea09-149">–</span><span class="sxs-lookup"><span data-stu-id="0ea09-149">N/A</span></span>                      |
| <span data-ttu-id="0ea09-150">Vložený prostředek</span><span class="sxs-lookup"><span data-stu-id="0ea09-150">EmbeddedResource</span></span>  | <span data-ttu-id="0ea09-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="0ea09-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="0ea09-152">\*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0ea09-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0ea09-153">–</span><span class="sxs-lookup"><span data-stu-id="0ea09-153">N/A</span></span>                      |
| <span data-ttu-id="0ea09-154">Žádná</span><span class="sxs-lookup"><span data-stu-id="0ea09-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="0ea09-155">\*\*/\*.user; \*\*/\*. \*proj; \* \* /.sln; \* \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0ea09-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0ea09-156">\*\*/\*.cs; \* \* /.resx \*</span><span class="sxs-lookup"><span data-stu-id="0ea09-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="0ea09-157">A `./bin` `./obj` složky, které jsou `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` reprezentovány vlastnostmi a MSBuild, jsou ve výchozím nastavení vyloučeny z globs.</span><span class="sxs-lookup"><span data-stu-id="0ea09-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="0ea09-158">Nezahrnuje jsou reprezentovány `$(DefaultItemExcludes)`vlastností .</span><span class="sxs-lookup"><span data-stu-id="0ea09-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="0ea09-159">Pokud explicitně definujete tyto položky v souboru projektu, pravděpodobně se zobrazí následující chyba:</span><span class="sxs-lookup"><span data-stu-id="0ea09-159">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="0ea09-160">**Byly zahrnuty duplicitní položky kompilace. Sada .NET SDK ve výchozím nastavení obsahuje položky kompilace z adresáře projektu. Tyto položky můžete odebrat ze souboru projektu nebo nastavit vlastnost EnableDefaultCompileItems na hodnotu false, pokud je chcete explicitně zahrnout do souboru projektu.**</span><span class="sxs-lookup"><span data-stu-id="0ea09-160">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="0ea09-161">Chcete-li chybu vyřešit, `Compile` odeberte explicitní položky, které odpovídají implicitním položkám uvedeným v předchozí tabulce, nebo nastavte `EnableDefaultCompileItems` vlastnost na `false`, která zakáže implicitní zahrnutí:</span><span class="sxs-lookup"><span data-stu-id="0ea09-161">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="0ea09-162">Pokud chcete zadat, například některé soubory, které mají být publikovány s vaší aplikací, můžete stále použít `Content` známé mechanismy MSBuild pro tento prvek.</span><span class="sxs-lookup"><span data-stu-id="0ea09-162">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="0ea09-163">`EnableDefaultCompileItems`pouze zakáže `Compile` globs, ale nemá vliv na `None` jiné globs, \*jako implicitní glob, který se vztahuje i na .cs položky.</span><span class="sxs-lookup"><span data-stu-id="0ea09-163">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="0ea09-164">Z tohoto důvodu Průzkumník řešení \*v sadě Visual Studio zobrazuje položky .cs jako součást projektu, zahrnuté jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="0ea09-164">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="0ea09-165">Chcete-li `None` implicitní `EnableDefaultNoneItems` glob `false`zakázat, nastavte na :</span><span class="sxs-lookup"><span data-stu-id="0ea09-165">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="0ea09-166">Chcete-li zakázat *všechny* `EnableDefaultItems` implicitní `false`globs, nastavte vlastnost na :</span><span class="sxs-lookup"><span data-stu-id="0ea09-166">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="0ea09-167">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="0ea09-167">Customize the build</span></span>

<span data-ttu-id="0ea09-168">Existují různé způsoby [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="0ea09-168">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="0ea09-169">Vlastnost můžete přepsat předáním jako argument příkazu [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) nebo [dotnet.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="0ea09-169">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="0ea09-170">Vlastnost můžete také přidat do souboru projektu nebo do souboru *Directory.Build.props.*</span><span class="sxs-lookup"><span data-stu-id="0ea09-170">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="0ea09-171">Seznam užitečných vlastností pro projekty .NET Core naleznete v [tématu Vlastnosti msbuild pro projekty sady .NET Core SDK](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="0ea09-171">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="0ea09-172">Vlastní cíle</span><span class="sxs-lookup"><span data-stu-id="0ea09-172">Custom targets</span></span>

<span data-ttu-id="0ea09-173">.NET Core projekty můžete balíček vlastní MSBuild cíle a vlastnosti pro použití projekty, které spotřebovávají balíček.</span><span class="sxs-lookup"><span data-stu-id="0ea09-173">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="0ea09-174">Tento typ rozšiřitelnosti použijte, pokud chcete:</span><span class="sxs-lookup"><span data-stu-id="0ea09-174">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="0ea09-175">Rozšiřte proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ea09-175">Extend the build process.</span></span>
- <span data-ttu-id="0ea09-176">Přístup artefakty procesu sestavení, jako jsou generované soubory.</span><span class="sxs-lookup"><span data-stu-id="0ea09-176">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="0ea09-177">Zkontrolujte konfiguraci, pod kterou je vyvoláno sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ea09-177">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="0ea09-178">Vlastní cíle sestavení nebo vlastnosti přidáte `<package_id>.targets` umístěním souborů do formuláře nebo `<package_id>.props` `Contoso.Utility.UsefulStuff.targets`(například) do složky *sestavení* projektu.</span><span class="sxs-lookup"><span data-stu-id="0ea09-178">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="0ea09-179">Následující kód XML je výstřižek ze souboru *.csproj,* který příkaz udává, [`dotnet pack`](../tools/dotnet-pack.md) co má sbalit.</span><span class="sxs-lookup"><span data-stu-id="0ea09-179">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="0ea09-180">Prvek `<ItemGroup Label="dotnet pack instructions">` umístí soubory cílů do složky *sestavení* uvnitř balíčku.</span><span class="sxs-lookup"><span data-stu-id="0ea09-180">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="0ea09-181">Prvek `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` umístí sestavení a *soubory JSON* do složky *sestavení.*</span><span class="sxs-lookup"><span data-stu-id="0ea09-181">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="0ea09-182">Chcete-li spotřebovat vlastní cíl `PackageReference` v projektu, přidejte prvek, který odkazuje na balíček a jeho verzi.</span><span class="sxs-lookup"><span data-stu-id="0ea09-182">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="0ea09-183">Na rozdíl od nástrojů je balíček vlastních cílů součástí uzavření závislosti náročného projektu.</span><span class="sxs-lookup"><span data-stu-id="0ea09-183">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="0ea09-184">Můžete nakonfigurovat, jak používat vlastní cíl.</span><span class="sxs-lookup"><span data-stu-id="0ea09-184">You can configure how to use the custom target.</span></span> <span data-ttu-id="0ea09-185">Vzhledem k tomu, že je cíl MSBuild, může záviset na daný cíl, spustit `dotnet msbuild -t:<target-name>` za jiným cílem nebo ručně vyvolat pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="0ea09-185">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="0ea09-186">Chcete-li však poskytnout lepší uživatelské prostředí, můžete kombinovat nástroje pro jednotlivé projekty a vlastní cíle.</span><span class="sxs-lookup"><span data-stu-id="0ea09-186">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="0ea09-187">V tomto scénáři nástroj pro jednotlivé projekty přijímá všechny parametry, [`dotnet msbuild`](../tools/dotnet-msbuild.md) které jsou potřeba, a překládá, že do požadované vyvolání, který provede cíl.</span><span class="sxs-lookup"><span data-stu-id="0ea09-187">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="0ea09-188">Ukázku tohoto druhu synergie si můžete prohlédnout na [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) příkladech vzorků [Hackathon summitu MVP summitu 2016](https://github.com/dotnet/MVPSummitHackathon2016) v projektu.</span><span class="sxs-lookup"><span data-stu-id="0ea09-188">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ea09-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ea09-189">See also</span></span>

- [<span data-ttu-id="0ea09-190">Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ea09-190">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="0ea09-191">Použití sad SDK projektu MSBuild</span><span class="sxs-lookup"><span data-stu-id="0ea09-191">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="0ea09-192">Balíček vlastních cílů msbuild a rekvizit y nuget</span><span class="sxs-lookup"><span data-stu-id="0ea09-192">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
