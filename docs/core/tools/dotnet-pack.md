---
title: dotnet pack, příkaz
description: Příkaz dotnet pack vytvoří balíčky NuGet pro váš projekt .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503654"
---
# <a name="dotnet-pack"></a><span data-ttu-id="a1204-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a1204-103">dotnet pack</span></span>

<span data-ttu-id="a1204-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="a1204-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a1204-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="a1204-105">Name</span></span>

<span data-ttu-id="a1204-106">`dotnet pack`- Zabalí kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a1204-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a1204-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="a1204-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a1204-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a1204-108">Description</span></span>

<span data-ttu-id="a1204-109">Příkaz `dotnet pack` vytvoří projekt a vytvoří balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="a1204-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="a1204-110">Výsledkem tohoto příkazu je balíček NuGet (to znamená soubor *.nupkg).*</span><span class="sxs-lookup"><span data-stu-id="a1204-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="a1204-111">Pokud chcete vygenerovat balíček, který obsahuje symboly ladění, máte k dispozici dvě možnosti:</span><span class="sxs-lookup"><span data-stu-id="a1204-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="a1204-112">`--include-symbols`- vytváří balíček symbolů.</span><span class="sxs-lookup"><span data-stu-id="a1204-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="a1204-113">`--include-source`- vytváří balíček symbolů se `src` složkou uvnitř obsahující zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="a1204-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="a1204-114">NuGet závislosti zabalené projektu jsou přidány do souboru *.nuspec,* takže jsou správně vyřešeny při instalaci balíčku.</span><span class="sxs-lookup"><span data-stu-id="a1204-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="a1204-115">Odkazy na projekt nejsou zabaleny uvnitř projektu.</span><span class="sxs-lookup"><span data-stu-id="a1204-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="a1204-116">V současné době musíte mít balíček na projekt, pokud máte závislosti mezi projekty.</span><span class="sxs-lookup"><span data-stu-id="a1204-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="a1204-117">Ve výchozím `dotnet pack` nastavení nejprve vytvoří projekt.</span><span class="sxs-lookup"><span data-stu-id="a1204-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="a1204-118">Pokud se chcete tomuto chování `--no-build` vyhnout, předejte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="a1204-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="a1204-119">Tato možnost je často užitečné ve scénářích sestavení průběžné integrace (CI), kde víte, že kód byl dříve sestaven.</span><span class="sxs-lookup"><span data-stu-id="a1204-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="a1204-120">Můžete zadat MSBuild vlastnosti příkazu `dotnet pack` pro proces balení.</span><span class="sxs-lookup"><span data-stu-id="a1204-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="a1204-121">Další informace naleznete [v tématu Vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [odkaz na příkazový řádek msbuildu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="a1204-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="a1204-122">[Příklady](#examples) část ukazuje, jak používat přepínač MSBuild -p pro několik různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="a1204-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="a1204-123">Webové projekty nejsou ve výchozím nastavení sbalitelné.</span><span class="sxs-lookup"><span data-stu-id="a1204-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="a1204-124">Chcete-li přepsat výchozí chování, přidejte do souboru *.csproj* následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="a1204-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="a1204-125">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a1204-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="a1204-126">Projekt nebo řešení pro balení.</span><span class="sxs-lookup"><span data-stu-id="a1204-126">The project or solution to pack.</span></span> <span data-ttu-id="a1204-127">Je to buď cesta k [souboru csproj](csproj.md), soubor řešení, nebo do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a1204-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="a1204-128">Pokud není zadán, příkaz prohledá aktuální adresář pro soubor projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="a1204-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="a1204-129">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a1204-129">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="a1204-130">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1204-130">Defines the build configuration.</span></span> <span data-ttu-id="a1204-131">Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="a1204-131">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="a1204-132">Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="a1204-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a1204-133">Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="a1204-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a1204-134">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a1204-134">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="a1204-135">Obsahuje ladicí symboly NuGet balíčky kromě běžné NuGet balíčky ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="a1204-135">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="a1204-136">Soubory zdrojů jsou zahrnuty ve `src` složce v balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="a1204-136">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="a1204-137">Obsahuje ladicí symboly NuGet balíčky kromě běžné NuGet balíčky ve výstupním adresáři.</span><span class="sxs-lookup"><span data-stu-id="a1204-137">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="a1204-138">Umožňuje příkazu zastavit a čekat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="a1204-138">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="a1204-139">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a1204-139">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="a1204-140">Nestaví projekt před balením.</span><span class="sxs-lookup"><span data-stu-id="a1204-140">Doesn't build the project before packing.</span></span> <span data-ttu-id="a1204-141">Také implicitně nastaví příznak. `--no-restore`</span><span class="sxs-lookup"><span data-stu-id="a1204-141">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="a1204-142">Ignoruje odkazy projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="a1204-142">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a1204-143">Nespustí implicitní obnovení při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="a1204-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="a1204-144">Nezobrazuje spouštěcí banner ani zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="a1204-144">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="a1204-145">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="a1204-145">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a1204-146">Umístí vytvořené balíčky do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="a1204-146">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a1204-147">Určuje cílový čas běhu, pro který má být obnoveny balíčky.</span><span class="sxs-lookup"><span data-stu-id="a1204-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="a1204-148">Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a1204-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="a1204-149">Nastaví příznak opravitelný v balíčku.</span><span class="sxs-lookup"><span data-stu-id="a1204-149">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="a1204-150">Další informace naleznete [v tématu .NET Blog: .NET 4.5.1 Podporuje aktualizace zabezpečení společnosti Microsoft pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="a1204-150">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="a1204-151">Definuje hodnotu vlastnosti `$(VersionSuffix)` MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="a1204-151">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a1204-152">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="a1204-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a1204-153">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="a1204-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="a1204-154">Příklady</span><span class="sxs-lookup"><span data-stu-id="a1204-154">Examples</span></span>

- <span data-ttu-id="a1204-155">Zabalte projekt do aktuálního adresáře:</span><span class="sxs-lookup"><span data-stu-id="a1204-155">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="a1204-156">Sbalte `app1` si projekt:</span><span class="sxs-lookup"><span data-stu-id="a1204-156">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="a1204-157">Zabalte projekt do aktuálního adresáře a `nupkgs` umístěte výsledné balíčky do složky:</span><span class="sxs-lookup"><span data-stu-id="a1204-157">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="a1204-158">Zabalte projekt do aktuálního `nupkgs` adresáře do složky a přeskočte krok sestavení:</span><span class="sxs-lookup"><span data-stu-id="a1204-158">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="a1204-159">S příponou verze projektu nakonfigurované jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v souboru *.csproj* zabalte aktuální projekt a aktualizujte výslednou verzi balíčku s danou příponou:</span><span class="sxs-lookup"><span data-stu-id="a1204-159">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="a1204-160">Nastavte verzi balíčku `2.1.0` na `PackageVersion` vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="a1204-160">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="a1204-161">Zabalte projekt pro konkrétní [cílový rámec](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="a1204-161">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="a1204-162">Zabalte projekt a použijte konkrétní runtime (Windows 10) pro operaci obnovení:</span><span class="sxs-lookup"><span data-stu-id="a1204-162">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="a1204-163">Zabalte projekt pomocí [souboru .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="a1204-163">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
