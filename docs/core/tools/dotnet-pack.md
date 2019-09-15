---
title: příkaz dotnet Pack
description: Příkaz dotnet Pack vytvoří balíčky NuGet pro projekt .NET Core.
ms.date: 08/08/2019
ms.openlocfilehash: ba5a438d58963222c3fa55d2c585ef503dcd49db
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990412"
---
# <a name="dotnet-pack"></a><span data-ttu-id="5f714-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5f714-103">dotnet pack</span></span>

<span data-ttu-id="5f714-104">**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="5f714-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5f714-105">Name</span><span class="sxs-lookup"><span data-stu-id="5f714-105">Name</span></span>

<span data-ttu-id="5f714-106">`dotnet pack`– Zabalí kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="5f714-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5f714-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5f714-107">Synopsis</span></span>

```console
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive] 
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable] 
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5f714-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5f714-108">Description</span></span>

<span data-ttu-id="5f714-109">`dotnet pack` Příkaz sestaví projekt a vytvoří balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="5f714-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="5f714-110">Výsledek tohoto příkazu je balíček NuGet (to znamená soubor *. nupkg* ).</span><span class="sxs-lookup"><span data-stu-id="5f714-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span> 

<span data-ttu-id="5f714-111">Pokud chcete vygenerovat balíček, který obsahuje symboly ladění, máte k dispozici dvě možnosti:</span><span class="sxs-lookup"><span data-stu-id="5f714-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="5f714-112">`--include-symbols`– vytvoří balíček symbolů.</span><span class="sxs-lookup"><span data-stu-id="5f714-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="5f714-113">`--include-source`– vytvoří balíček symbolů se `src` složkou uvnitř obsahující zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="5f714-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="5f714-114">Do souboru *. nuspec* jsou přidány závislosti NuGet zkomprimovaného projektu, aby byly po instalaci balíčku správně vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="5f714-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="5f714-115">Odkazy z projektu na projekt nejsou zabaleny do projektu.</span><span class="sxs-lookup"><span data-stu-id="5f714-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="5f714-116">V současné době je nutné mít balíček na projekt, pokud máte závislosti typu projekt-projekt.</span><span class="sxs-lookup"><span data-stu-id="5f714-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="5f714-117">Ve výchozím nastavení `dotnet pack` sestaví projekt jako první.</span><span class="sxs-lookup"><span data-stu-id="5f714-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="5f714-118">Pokud se chcete tomuto chování vyhnout, předejte `--no-build` možnost.</span><span class="sxs-lookup"><span data-stu-id="5f714-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="5f714-119">Tato možnost je často užitečná ve scénářích průběžné integrace (CI), kde víte, že kód byl dříve sestaven.</span><span class="sxs-lookup"><span data-stu-id="5f714-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="5f714-120">Vlastnosti nástroje MSBuild můžete zadat pro `dotnet pack` příkaz pro proces balení.</span><span class="sxs-lookup"><span data-stu-id="5f714-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="5f714-121">Další informace najdete v tématu [vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="5f714-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="5f714-122">V části s [Příklady](#examples) se dozvíte, jak použít přepínač MSBuild-p pro několik různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="5f714-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="5f714-123">Webové projekty nejsou ve výchozím nastavení nabaleny.</span><span class="sxs-lookup"><span data-stu-id="5f714-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="5f714-124">Chcete-li přepsat výchozí chování, přidejte do souboru *. csproj* následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="5f714-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="5f714-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f714-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="5f714-126">Projekt nebo řešení, které se má zabalit</span><span class="sxs-lookup"><span data-stu-id="5f714-126">The project or solution to pack.</span></span> <span data-ttu-id="5f714-127">Jedná se buď o cestu k [souboru csproj](csproj.md), k souboru řešení nebo k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5f714-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="5f714-128">Pokud není zadán, příkaz vyhledá v aktuálním adresáři soubor projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="5f714-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="5f714-129">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5f714-129">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="5f714-130">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="5f714-130">Defines the build configuration.</span></span> <span data-ttu-id="5f714-131">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="5f714-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="5f714-132">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="5f714-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5f714-133">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5f714-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="5f714-134">Možnost je k dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5f714-134">Option available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="5f714-135">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="5f714-135">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="5f714-136">Obsahuje kromě běžných balíčků NuGet ve výstupním adresáři také balíčky NuGet pro ladicí symboly.</span><span class="sxs-lookup"><span data-stu-id="5f714-136">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="5f714-137">Zdrojové soubory jsou zahrnuty ve `src` složce v rámci balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="5f714-137">The sources files are included in the `src` folder within the symbols package.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="5f714-138">Obsahuje kromě běžných balíčků NuGet ve výstupním adresáři také balíčky NuGet pro ladicí symboly.</span><span class="sxs-lookup"><span data-stu-id="5f714-138">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

* **`--interactive`**

  <span data-ttu-id="5f714-139">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="5f714-139">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="5f714-140">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5f714-140">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-build`**

  <span data-ttu-id="5f714-141">Nevytvoří projekt před balením.</span><span class="sxs-lookup"><span data-stu-id="5f714-141">Doesn't build the project before packing.</span></span> <span data-ttu-id="5f714-142">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="5f714-142">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="5f714-143">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="5f714-143">Ignores project-to-project references and only restores the root project.</span></span> <span data-ttu-id="5f714-144">Možnost je k dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5f714-144">Option available since .NET Core 2.0 SDK.</span></span>

* **`--no-restore`**

  <span data-ttu-id="5f714-145">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="5f714-145">Doesn't execute an implicit restore when running the command.</span></span> <span data-ttu-id="5f714-146">Možnost je k dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5f714-146">Option available since .NET Core 2.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="5f714-147">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="5f714-147">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="5f714-148">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5f714-148">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5f714-149">Umístí sestavené balíčky do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="5f714-149">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5f714-150">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="5f714-150">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="5f714-151">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="5f714-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="5f714-152">Možnost je k dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5f714-152">Option available since .NET Core 2.0 SDK.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="5f714-153">Nastaví v balíčku příznak služby.</span><span class="sxs-lookup"><span data-stu-id="5f714-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="5f714-154">Další informace najdete na [blogu .NET: rozhraní .NET 4.5.1 podporuje aktualizace zabezpečení Microsoftu pro knihovny NuGet pro .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="5f714-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="5f714-155">Definuje hodnotu `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="5f714-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5f714-156">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="5f714-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5f714-157">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="5f714-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="5f714-158">Příklady</span><span class="sxs-lookup"><span data-stu-id="5f714-158">Examples</span></span>

* <span data-ttu-id="5f714-159">Sbalit projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="5f714-159">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="5f714-160">`app1` Sbalit projekt:</span><span class="sxs-lookup"><span data-stu-id="5f714-160">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="5f714-161">Sbalení projektu v aktuálním adresáři a umístění výsledných balíčků do `nupkgs` složky:</span><span class="sxs-lookup"><span data-stu-id="5f714-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="5f714-162">Sbalení projektu v aktuálním adresáři do `nupkgs` složky a přeskočení kroku sestavení:</span><span class="sxs-lookup"><span data-stu-id="5f714-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="5f714-163">S příponou verze projektu nakonfigurovanou jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v souboru *. csproj* rozbalte aktuální projekt a aktualizujte výslednou verzi balíčku s danou příponou:</span><span class="sxs-lookup"><span data-stu-id="5f714-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="5f714-164">Nastavte na verzi `2.1.0` `PackageVersion` balíčku vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="5f714-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="5f714-165">Sbalení projektu pro konkrétní [cílové rozhraní](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="5f714-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="5f714-166">Sbalení projektu a použití konkrétního modulu runtime (Windows 10) pro operaci obnovení (.NET Core SDK 2,0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="5f714-166">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="5f714-167">Sbalení projektu pomocí [souboru. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="5f714-167">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
