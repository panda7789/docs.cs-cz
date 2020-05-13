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
# <a name="net-core-project-sdks"></a><span data-ttu-id="6f615-103">Sady SDK pro projekty .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f615-103">.NET Core project SDKs</span></span>

<span data-ttu-id="6f615-104">Projekty .NET Core jsou přidruženy k sadě SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="6f615-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="6f615-105">Každá *sada SDK projektu* je sada [cílů](/visualstudio/msbuild/msbuild-targets) MSBuild a přidružených [úloh](/visualstudio/msbuild/msbuild-tasks) , které jsou zodpovědné za kompilování, balení a publikování kódu.</span><span class="sxs-lookup"><span data-stu-id="6f615-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="6f615-106">Projekt, který odkazuje na sadu SDK projektu, se někdy označuje jako *projekt ve stylu sady SDK*.</span><span class="sxs-lookup"><span data-stu-id="6f615-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="6f615-107">Dostupné sady SDK</span><span class="sxs-lookup"><span data-stu-id="6f615-107">Available SDKs</span></span>

<span data-ttu-id="6f615-108">Pro .NET Core jsou k dispozici následující sady SDK:</span><span class="sxs-lookup"><span data-stu-id="6f615-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="6f615-109">ID</span><span class="sxs-lookup"><span data-stu-id="6f615-109">ID</span></span> | <span data-ttu-id="6f615-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6f615-110">Description</span></span> | <span data-ttu-id="6f615-111">Sestavy</span><span class="sxs-lookup"><span data-stu-id="6f615-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="6f615-112">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6f615-112">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="6f615-113">[Sada Web SDK](/aspnet/core/razor-pages/web-sdk) pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f615-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="6f615-114">[Sada SDK](/aspnet/core/razor-pages/sdk) .NET Core Razor</span><span class="sxs-lookup"><span data-stu-id="6f615-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="6f615-115">Sada SDK služby .NET Core Worker</span><span class="sxs-lookup"><span data-stu-id="6f615-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="6f615-116">WinForms a sada WPF SDK pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f615-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="6f615-117">.NET Core SDK je základní sada SDK pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f615-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="6f615-118">Ostatní sady SDK odkazují na .NET Core SDK a projekty, které jsou přidruženy k ostatním sadám SDK, mají k dispozici všechny vlastnosti .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6f615-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="6f615-119">Webová sada SDK například závisí na .NET Core SDK i sadě Razor SDK.</span><span class="sxs-lookup"><span data-stu-id="6f615-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="6f615-120">Můžete také vytvořit vlastní sadu SDK, která se dá distribuovat přes NuGet.</span><span class="sxs-lookup"><span data-stu-id="6f615-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="6f615-121">Soubory projektu</span><span class="sxs-lookup"><span data-stu-id="6f615-121">Project files</span></span>

<span data-ttu-id="6f615-122">Projekty .NET Core jsou založeny na formátu [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="6f615-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="6f615-123">Soubory projektu, které mají rozšíření jako *. csproj* pro projekty C# a *. fsproj* pro projekty F #, jsou ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="6f615-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="6f615-124">Kořenový prvek souboru projektu MSBuild je [projektový](/visualstudio/msbuild/project-element-msbuild) prvek.</span><span class="sxs-lookup"><span data-stu-id="6f615-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="6f615-125">`Project`Element má volitelný `Sdk` atribut, který určuje sadu SDK (a verze), která se má použít.</span><span class="sxs-lookup"><span data-stu-id="6f615-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="6f615-126">Chcete-li použít nástroje .NET Core a sestavit kód, nastavte `Sdk` atribut na jedno z ID v tabulce [dostupných sad SDK](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="6f615-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="6f615-127">Pokud chcete zadat sadu SDK, která pochází z NuGet, zahrňte na konci názvu verzi nebo zadejte název a verzi v souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="6f615-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="6f615-128">Dalším způsobem, jak zadat sadu SDK, je element [sady SDK](/visualstudio/msbuild/sdk-element-msbuild) na nejvyšší úrovni:</span><span class="sxs-lookup"><span data-stu-id="6f615-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="6f615-129">Odkazování na sadu SDK jedním z těchto způsobů značně zjednodušuje soubory projektu pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f615-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="6f615-130">Při vyhodnocování projektu nástroj MSBuild přidá implicitní importy do `Sdk.props` horní části souboru projektu a `Sdk.targets` v dolní části.</span><span class="sxs-lookup"><span data-stu-id="6f615-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="6f615-131">V počítači s Windows se soubory *SDK. props* a *SDK. targets* dají najít ve složce *%ProgramFiles%\dotnet\sdk \\ [Version] \Sdks\Microsoft.NET.Sdk\Sdk* .</span><span class="sxs-lookup"><span data-stu-id="6f615-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="6f615-132">Předběžné zpracování souboru projektu</span><span class="sxs-lookup"><span data-stu-id="6f615-132">Preprocess the project file</span></span>

<span data-ttu-id="6f615-133">Úplný rozbalený projekt se zobrazí po zobrazení nástroje MSBuild po sadě SDK a jeho cílech pomocí `dotnet msbuild -preprocess` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f615-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="6f615-134">Přepínač [předběžného zpracování](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) příkazu ukazuje, které soubory jsou importovány, jejich zdroje a jejich příspěvky na sestavení bez skutečného sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="6f615-135">Pokud má projekt více cílových rozhraní, zaměřte výsledky příkazu pouze na jednu architekturu zadáním jako vlastnost MSBuild.</span><span class="sxs-lookup"><span data-stu-id="6f615-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="6f615-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6f615-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="6f615-137">Výchozí kompilace zahrnuje</span><span class="sxs-lookup"><span data-stu-id="6f615-137">Default compilation includes</span></span>

<span data-ttu-id="6f615-138">Výchozí zahrnutí a vyloučení položek kompilace, integrovaných prostředků a `None` položek je definováno v sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="6f615-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="6f615-139">Na rozdíl od projektů, které nejsou .NET Framework SDK, není nutné zadávat tyto položky v souboru projektu, protože výchozí hodnoty se vztahují na nejběžnější případy použití.</span><span class="sxs-lookup"><span data-stu-id="6f615-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="6f615-140">Tím se soubor projektu zmenší a v případě potřeby bude snazší pochopit a upravovat.</span><span class="sxs-lookup"><span data-stu-id="6f615-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="6f615-141">Následující tabulka ukazuje, které prvky a které [globy](https://en.wikipedia.org/wiki/Glob_(programming)) jsou zahrnuty a vyloučeny v .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="6f615-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="6f615-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="6f615-142">Element</span></span>           | <span data-ttu-id="6f615-143">Zahrnout glob</span><span class="sxs-lookup"><span data-stu-id="6f615-143">Include glob</span></span>                              | <span data-ttu-id="6f615-144">Vyloučit glob</span><span class="sxs-lookup"><span data-stu-id="6f615-144">Exclude glob</span></span>                                                  | <span data-ttu-id="6f615-145">Odebrat glob</span><span class="sxs-lookup"><span data-stu-id="6f615-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="6f615-146">Sestavení</span><span class="sxs-lookup"><span data-stu-id="6f615-146">Compile</span></span>           | <span data-ttu-id="6f615-147">\*\*/\*cs (nebo jiné jazykové rozšíření)</span><span class="sxs-lookup"><span data-stu-id="6f615-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="6f615-148">\*\*/\*uživatelský  \*\*/\*.\* Souhrn  \*\*/\*. SLN  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="6f615-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="6f615-149">–</span><span class="sxs-lookup"><span data-stu-id="6f615-149">N/A</span></span>                      |
| <span data-ttu-id="6f615-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="6f615-150">EmbeddedResource</span></span>  | <span data-ttu-id="6f615-151">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="6f615-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="6f615-152">\*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="6f615-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6f615-153">–</span><span class="sxs-lookup"><span data-stu-id="6f615-153">N/A</span></span>                      |
| <span data-ttu-id="6f615-154">Žádné</span><span class="sxs-lookup"><span data-stu-id="6f615-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="6f615-155">\*\*/\*uživatelský \*\*/\*.\* Souhrn \*\*/\*. SLN \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="6f615-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6f615-156">\*\*/\*cs \*\*/\*. RESX</span><span class="sxs-lookup"><span data-stu-id="6f615-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="6f615-157">`./bin`Složky a `./obj` , které jsou reprezentovány `$(BaseOutputPath)` vlastnostmi a nástroje `$(BaseIntermediateOutputPath)` MSBuild, jsou ve výchozím nastavení vyloučeny z globy.</span><span class="sxs-lookup"><span data-stu-id="6f615-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="6f615-158">Vyloučení jsou reprezentovány vlastností `$(DefaultItemExcludes)` .</span><span class="sxs-lookup"><span data-stu-id="6f615-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="6f615-159">Chyby sestavení</span><span class="sxs-lookup"><span data-stu-id="6f615-159">Build errors</span></span>

<span data-ttu-id="6f615-160">Pokud explicitně definujete některou z těchto položek v souboru projektu, pravděpodobně se zobrazí chyba Build "NETSDK1022", která bude vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="6f615-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="6f615-161">Byly zahrnuty duplicitní položky Compile.</span><span class="sxs-lookup"><span data-stu-id="6f615-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="6f615-162">Sada .NET SDK obsahuje ve výchozím nastavení položky kompilovat z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="6f615-163">Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultCompileItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="6f615-164">Byly zahrnuty duplicitní položky ' EmbeddedResource '.</span><span class="sxs-lookup"><span data-stu-id="6f615-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="6f615-165">Sada .NET SDK obsahuje ve výchozím nastavení položky "EmbeddedResource" z adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="6f615-166">Můžete buď odebrat tyto položky ze souboru projektu, nebo nastavit vlastnost ' EnableDefaultEmbeddedResourceItems ' na hodnotu ' false ', pokud je chcete explicitně zahrnout do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="6f615-167">Chcete-li tyto chyby vyřešit, proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="6f615-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="6f615-168">Odeberte explicitní `Compile` položky, `EmbeddedResource` nebo, `None` které odpovídají implicitním těm uvedeným v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="6f615-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="6f615-169">Nastavte `EnableDefaultItems` vlastnost tak, aby `false` se zakázalo zahrnutí všech implicitních souborů:</span><span class="sxs-lookup"><span data-stu-id="6f615-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="6f615-170">Pokud chcete určit soubory, které mají být publikovány s vaší aplikací, můžete stále používat známé mechanizmy nástroje MSBuild, například `Content` prvek.</span><span class="sxs-lookup"><span data-stu-id="6f615-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="6f615-171">Selektivně zakažte pouze `Compile` , `EmbeddedResource` nebo `None` globy nastavením `EnableDefaultCompileItems` `EnableDefaultEmbeddedResourceItems` vlastnosti, nebo `EnableDefaultNoneItems` na `false` :</span><span class="sxs-lookup"><span data-stu-id="6f615-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="6f615-172">Pokud zakážete pouze `Compile` globy, Průzkumník řešení v aplikaci Visual Studio stále zobrazuje \* položky. cs jako součást projektu, které jsou zahrnuty jako `None` položky.</span><span class="sxs-lookup"><span data-stu-id="6f615-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="6f615-173">Pokud chcete zakázat implicitní `None` glob, nastavte `EnableDefaultNoneItems` na hodnotu `false` příliš.</span><span class="sxs-lookup"><span data-stu-id="6f615-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="6f615-174">Přizpůsobení sestavení</span><span class="sxs-lookup"><span data-stu-id="6f615-174">Customize the build</span></span>

<span data-ttu-id="6f615-175">Existují různé způsoby [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="6f615-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="6f615-176">Můžete chtít přepsat vlastnost předáním jako argumentu příkazu [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) nebo [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="6f615-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="6f615-177">Můžete také přidat vlastnost do souboru projektu nebo do souboru *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="6f615-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="6f615-178">Seznam užitečných vlastností pro projekty .NET Core naleznete v tématu [Reference k MSBuild pro .NET Core SDK projekty](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="6f615-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="6f615-179">Vlastní cíle</span><span class="sxs-lookup"><span data-stu-id="6f615-179">Custom targets</span></span>

<span data-ttu-id="6f615-180">Projekty .NET Core můžou zabalit vlastní cíle a vlastnosti MSBuild pro použití projekty, které balíček využívají.</span><span class="sxs-lookup"><span data-stu-id="6f615-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="6f615-181">Tento typ rozšiřitelnosti použijte v případě, že chcete:</span><span class="sxs-lookup"><span data-stu-id="6f615-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="6f615-182">Rozšíří proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="6f615-182">Extend the build process.</span></span>
- <span data-ttu-id="6f615-183">Přístup k artefaktům procesu sestavení, jako je například vygenerované soubory.</span><span class="sxs-lookup"><span data-stu-id="6f615-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="6f615-184">Zkontrolujte konfiguraci, pod kterou je vyvoláno sestavení.</span><span class="sxs-lookup"><span data-stu-id="6f615-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="6f615-185">Vlastní cíle sestavení nebo vlastnosti můžete přidat umístěním souborů ve formuláři `<package_id>.targets` nebo `<package_id>.props` (například `Contoso.Utility.UsefulStuff.targets` ) do složky *sestavení* projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="6f615-186">Následující kód XML je fragmentem ze souboru *. csproj* , který instruuje příkaz, který [`dotnet pack`](../tools/dotnet-pack.md) se má zabalit.</span><span class="sxs-lookup"><span data-stu-id="6f615-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="6f615-187">`<ItemGroup Label="dotnet pack instructions">`Prvek umístí soubory cílů do složky *sestavení* uvnitř balíčku.</span><span class="sxs-lookup"><span data-stu-id="6f615-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="6f615-188">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Prvek umístí sestavení a soubory *. JSON* do složky *sestavení* .</span><span class="sxs-lookup"><span data-stu-id="6f615-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="6f615-189">Chcete-li využívat vlastní cíl v projektu, přidejte `PackageReference` prvek, který odkazuje na balíček a jeho verzi.</span><span class="sxs-lookup"><span data-stu-id="6f615-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="6f615-190">Na rozdíl od nástrojů je balíček vlastních cílů zahrnut v uzávěrce náročného projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="6f615-191">Můžete nakonfigurovat, jak se má používat vlastní cíl.</span><span class="sxs-lookup"><span data-stu-id="6f615-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="6f615-192">Vzhledem k tomu, že se jedná o cíl MSBuild, může záviset na daném cíli, spustit po jiném cíli nebo být ručně vyvolán pomocí `dotnet msbuild -t:<target-name>` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f615-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="6f615-193">Chcete-li však zajistit lepší činnost koncového uživatele, můžete kombinovat nástroje pro jednotlivé projekty a vlastní cíle.</span><span class="sxs-lookup"><span data-stu-id="6f615-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="6f615-194">V tomto scénáři akceptuje Nástroj pro každý projekt jakékoli parametry, které jsou potřeba, a překládá se na požadované [`dotnet msbuild`](../tools/dotnet-msbuild.md) vyvolání, které provádí cíl.</span><span class="sxs-lookup"><span data-stu-id="6f615-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="6f615-195">Ukázku tohoto druhu součinnosti si můžete prohlédnout v úložišti [ukázek MVP 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) v [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.</span><span class="sxs-lookup"><span data-stu-id="6f615-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f615-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f615-196">See also</span></span>

- [<span data-ttu-id="6f615-197">Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="6f615-197">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="6f615-198">Jak používat sady SDK projektů MSBuild</span><span class="sxs-lookup"><span data-stu-id="6f615-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="6f615-199">Balíčky vlastních cílů a vlastností MSBuild balíčku pomocí NuGet</span><span class="sxs-lookup"><span data-stu-id="6f615-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
