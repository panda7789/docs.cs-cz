---
title: příkaz dotnet Pack
description: Příkaz dotnet Pack vytvoří balíčky NuGet pro projekt .NET Core.
ms.date: 04/28/2020
ms.openlocfilehash: 00cda2c52a12a7a3aef5f61291120f522536131d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442225"
---
# <a name="dotnet-pack"></a><span data-ttu-id="8c761-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8c761-103">dotnet pack</span></span>

<span data-ttu-id="8c761-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="8c761-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8c761-105">Name</span><span class="sxs-lookup"><span data-stu-id="8c761-105">Name</span></span>

<span data-ttu-id="8c761-106">`dotnet pack`– Zabalí kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c761-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8c761-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="8c761-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="8c761-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8c761-108">Description</span></span>

<span data-ttu-id="8c761-109">Příkaz sestaví `dotnet pack` projekt a vytvoří balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c761-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="8c761-110">Výsledek tohoto příkazu je balíček NuGet (to znamená soubor *. nupkg* ).</span><span class="sxs-lookup"><span data-stu-id="8c761-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="8c761-111">Pokud chcete vygenerovat balíček, který obsahuje symboly ladění, máte k dispozici dvě možnosti:</span><span class="sxs-lookup"><span data-stu-id="8c761-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="8c761-112">`--include-symbols`– vytvoří balíček symbolů.</span><span class="sxs-lookup"><span data-stu-id="8c761-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="8c761-113">`--include-source`– vytvoří balíček symbolů se `src` složkou uvnitř obsahující zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="8c761-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="8c761-114">Do souboru *. nuspec* jsou přidány závislosti NuGet zkomprimovaného projektu, aby byly po instalaci balíčku správně vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="8c761-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="8c761-115">Odkazy z projektu na projekt nejsou zabaleny do projektu.</span><span class="sxs-lookup"><span data-stu-id="8c761-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="8c761-116">V současné době je nutné mít balíček na projekt, pokud máte závislosti typu projekt-projekt.</span><span class="sxs-lookup"><span data-stu-id="8c761-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="8c761-117">Ve výchozím nastavení sestaví `dotnet pack` projekt jako první.</span><span class="sxs-lookup"><span data-stu-id="8c761-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="8c761-118">Pokud se chcete tomuto chování vyhnout, předejte `--no-build` možnost.</span><span class="sxs-lookup"><span data-stu-id="8c761-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="8c761-119">Tato možnost je často užitečná ve scénářích průběžné integrace (CI), kde víte, že kód byl dříve sestaven.</span><span class="sxs-lookup"><span data-stu-id="8c761-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="8c761-120">V některých případech nelze implicitní sestavení provést.</span><span class="sxs-lookup"><span data-stu-id="8c761-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="8c761-121">Tato situace může nastat `GeneratePackageOnBuild` , pokud je nastavena, aby nedocházelo k cyklické závislosti mezi cíli sestavení a balíčku.</span><span class="sxs-lookup"><span data-stu-id="8c761-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="8c761-122">Sestavení může selhat i v případě, že existuje uzamčený soubor nebo jiný problém.</span><span class="sxs-lookup"><span data-stu-id="8c761-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="8c761-123">Vlastnosti nástroje MSBuild můžete zadat pro `dotnet pack` příkaz pro proces balení.</span><span class="sxs-lookup"><span data-stu-id="8c761-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="8c761-124">Další informace najdete v tématu [vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="8c761-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="8c761-125">V části s [Příklady](#examples) se dozvíte, jak použít přepínač MSBuild-p pro několik různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="8c761-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="8c761-126">Webové projekty nejsou ve výchozím nastavení nabaleny.</span><span class="sxs-lookup"><span data-stu-id="8c761-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="8c761-127">Chcete-li přepsat výchozí chování, přidejte do souboru *. csproj* následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="8c761-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="8c761-128">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="8c761-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="8c761-129">Arguments</span><span class="sxs-lookup"><span data-stu-id="8c761-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="8c761-130">Projekt nebo řešení, které se má zabalit</span><span class="sxs-lookup"><span data-stu-id="8c761-130">The project or solution to pack.</span></span> <span data-ttu-id="8c761-131">Jedná se buď o cestu k [souboru csproj](csproj.md), vbproj, souboru fsproj, souboru řešení nebo k adresáři.</span><span class="sxs-lookup"><span data-stu-id="8c761-131">It's either a path to a [csproj file](csproj.md), vbproj file, fsproj file, a solution file, or to a directory.</span></span> <span data-ttu-id="8c761-132">Pokud není zadán, příkaz vyhledá v aktuálním adresáři soubor projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="8c761-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="8c761-133">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8c761-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="8c761-134">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c761-134">Defines the build configuration.</span></span> <span data-ttu-id="8c761-135">Výchozí hodnota pro většinu projektů je `Debug` , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="8c761-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="8c761-136">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="8c761-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="8c761-137">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="8c761-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8c761-138">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="8c761-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="8c761-139">Obsahuje kromě běžných balíčků NuGet ve výstupním adresáři také balíčky NuGet pro ladicí symboly.</span><span class="sxs-lookup"><span data-stu-id="8c761-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="8c761-140">Zdrojové soubory jsou zahrnuty ve `src` složce v rámci balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="8c761-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="8c761-141">Obsahuje kromě běžných balíčků NuGet ve výstupním adresáři také balíčky NuGet pro ladicí symboly.</span><span class="sxs-lookup"><span data-stu-id="8c761-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="8c761-142">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="8c761-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="8c761-143">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="8c761-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="8c761-144">Nevytvoří projekt před balením.</span><span class="sxs-lookup"><span data-stu-id="8c761-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="8c761-145">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="8c761-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="8c761-146">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="8c761-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="8c761-147">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="8c761-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="8c761-148">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="8c761-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="8c761-149">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="8c761-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="8c761-150">Umístí sestavené balíčky do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="8c761-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="8c761-151">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="8c761-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="8c761-152">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8c761-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="8c761-153">Nastaví v balíčku příznak služby.</span><span class="sxs-lookup"><span data-stu-id="8c761-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="8c761-154">Další informace najdete na [blogu .NET: rozhraní .NET 4.5.1 podporuje aktualizace zabezpečení Microsoftu pro knihovny NuGet pro .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="8c761-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="8c761-155">Definuje hodnotu `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="8c761-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="8c761-156">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="8c761-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8c761-157">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="8c761-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="8c761-158">Příklady</span><span class="sxs-lookup"><span data-stu-id="8c761-158">Examples</span></span>

- <span data-ttu-id="8c761-159">Sbalit projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="8c761-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="8c761-160">Sbalit `app1` projekt:</span><span class="sxs-lookup"><span data-stu-id="8c761-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="8c761-161">Sbalení projektu v aktuálním adresáři a umístění výsledných balíčků do `nupkgs` složky:</span><span class="sxs-lookup"><span data-stu-id="8c761-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="8c761-162">Sbalení projektu v aktuálním adresáři do `nupkgs` složky a přeskočení kroku sestavení:</span><span class="sxs-lookup"><span data-stu-id="8c761-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="8c761-163">S příponou verze projektu nakonfigurovanou jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v souboru *. csproj* rozbalte aktuální projekt a aktualizujte výslednou verzi balíčku s danou příponou:</span><span class="sxs-lookup"><span data-stu-id="8c761-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="8c761-164">Nastavte na verzi balíčku `2.1.0` `PackageVersion` vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="8c761-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="8c761-165">Sbalení projektu pro konkrétní [cílové rozhraní](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="8c761-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="8c761-166">Sbalení projektu a použití konkrétního modulu runtime (Windows 10) pro operaci obnovení:</span><span class="sxs-lookup"><span data-stu-id="8c761-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="8c761-167">Sbalení projektu pomocí souboru *. nuspec* :</span><span class="sxs-lookup"><span data-stu-id="8c761-167">Pack the project using a *.nuspec* file:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```

  <span data-ttu-id="8c761-168">Informace o tom, jak používat `NuspecFile` , `NuspecBasePath` a `NuspecProperties` , najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="8c761-168">For information about how to use `NuspecFile`, `NuspecBasePath`, and `NuspecProperties`, see the following resources:</span></span>
  
  - [<span data-ttu-id="8c761-169">Balení pomocí. nuspec</span><span class="sxs-lookup"><span data-stu-id="8c761-169">Packing using a .nuspec</span></span>](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)
  - [<span data-ttu-id="8c761-170">Rozšířené body rozšíření pro vytvoření přizpůsobeného balíčku</span><span class="sxs-lookup"><span data-stu-id="8c761-170">Advanced extension points to create customized package</span></span>](https://docs.microsoft.com/nuget/reference/msbuild-targets#advanced-extension-points-to-create-customized-package)
  - [<span data-ttu-id="8c761-171">Globální vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8c761-171">Global properties</span></span>](https://docs.microsoft.com/visualstudio/msbuild/msbuild-properties?view=vs-2019#global-properties)
