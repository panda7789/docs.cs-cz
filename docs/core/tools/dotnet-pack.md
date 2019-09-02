---
title: příkaz dotnet Pack
description: Příkaz dotnet Pack vytvoří balíčky NuGet pro projekt .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: c5c00f3bb06e5bc5579c0d3d6bdd39fbdf3db656
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202841"
---
# <a name="dotnet-pack"></a><span data-ttu-id="330f2-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="330f2-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="330f2-104">Name</span><span class="sxs-lookup"><span data-stu-id="330f2-104">Name</span></span>

<span data-ttu-id="330f2-105">`dotnet pack`– Zabalí kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="330f2-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="330f2-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="330f2-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="330f2-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="330f2-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="330f2-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="330f2-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="330f2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="330f2-109">Description</span></span>

<span data-ttu-id="330f2-110">`dotnet pack` Příkaz sestaví projekt a vytvoří balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="330f2-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="330f2-111">Výsledek tohoto příkazu je balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="330f2-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="330f2-112">Pokud je `--include-symbols` Tato možnost k dispozici, je vytvořen jiný balíček obsahující symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="330f2-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="330f2-113">Do souboru *. nuspec* jsou přidány závislosti NuGet zkomprimovaného projektu, aby byly po instalaci balíčku správně vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="330f2-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="330f2-114">Odkazy z projektu na projekt nejsou zabaleny do projektu.</span><span class="sxs-lookup"><span data-stu-id="330f2-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="330f2-115">V současné době je nutné mít balíček na projekt, pokud máte závislosti typu projekt-projekt.</span><span class="sxs-lookup"><span data-stu-id="330f2-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="330f2-116">Ve výchozím nastavení `dotnet pack` sestaví projekt jako první.</span><span class="sxs-lookup"><span data-stu-id="330f2-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="330f2-117">Pokud se chcete tomuto chování vyhnout, předejte `--no-build` možnost.</span><span class="sxs-lookup"><span data-stu-id="330f2-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="330f2-118">Tato možnost je často užitečná ve scénářích průběžné integrace (CI), kde víte, že kód byl dříve sestaven.</span><span class="sxs-lookup"><span data-stu-id="330f2-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="330f2-119">Vlastnosti nástroje MSBuild můžete zadat pro `dotnet pack` příkaz pro proces balení.</span><span class="sxs-lookup"><span data-stu-id="330f2-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="330f2-120">Další informace najdete v tématu [vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="330f2-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="330f2-121">V části s [Příklady](#examples) se dozvíte, jak použít přepínač MSBuild-p pro několik různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="330f2-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="330f2-122">Webové projekty nejsou ve výchozím nastavení nabaleny.</span><span class="sxs-lookup"><span data-stu-id="330f2-122">Web projects aren't packable by default.</span></span> <span data-ttu-id="330f2-123">Chcete-li přepsat výchozí chování, přidejte do souboru *. csproj* následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="330f2-123">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="330f2-124">Arguments</span><span class="sxs-lookup"><span data-stu-id="330f2-124">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="330f2-125">Projekt, který se má zabalit</span><span class="sxs-lookup"><span data-stu-id="330f2-125">The project to pack.</span></span> <span data-ttu-id="330f2-126">Jedná se buď o cestu k [souboru csproj](csproj.md) , nebo k adresáři.</span><span class="sxs-lookup"><span data-stu-id="330f2-126">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="330f2-127">Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="330f2-127">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="330f2-128">Možnosti</span><span class="sxs-lookup"><span data-stu-id="330f2-128">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="330f2-129">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="330f2-129">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="330f2-130">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="330f2-130">Defines the build configuration.</span></span> <span data-ttu-id="330f2-131">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="330f2-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="330f2-132">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="330f2-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="330f2-133">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="330f2-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="330f2-134">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="330f2-134">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="330f2-135">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="330f2-135">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="330f2-136">Zdrojové soubory jsou zahrnuty ve `src` složce v `nupkg`rámci.</span><span class="sxs-lookup"><span data-stu-id="330f2-136">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="330f2-137">Vygeneruje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="330f2-137">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="330f2-138">Nevytvoří projekt před balením.</span><span class="sxs-lookup"><span data-stu-id="330f2-138">Doesn't build the project before packing.</span></span> <span data-ttu-id="330f2-139">Také implicitně nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="330f2-139">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="330f2-140">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="330f2-140">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="330f2-141">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="330f2-141">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="330f2-142">Umístí sestavené balíčky do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="330f2-142">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="330f2-143">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="330f2-143">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="330f2-144">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="330f2-144">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="330f2-145">Nastaví v balíčku příznak služby.</span><span class="sxs-lookup"><span data-stu-id="330f2-145">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="330f2-146">Další informace najdete na [blogu .NET: rozhraní .NET 4.5.1 podporuje aktualizace zabezpečení Microsoftu pro knihovny NuGet pro .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="330f2-146">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="330f2-147">Definuje hodnotu `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="330f2-147">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="330f2-148">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="330f2-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="330f2-149">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="330f2-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="330f2-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="330f2-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="330f2-151">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="330f2-151">Defines the build configuration.</span></span> <span data-ttu-id="330f2-152">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="330f2-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="330f2-153">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="330f2-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="330f2-154">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="330f2-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="330f2-155">Zdrojové soubory jsou zahrnuty ve `src` složce v `nupkg`rámci.</span><span class="sxs-lookup"><span data-stu-id="330f2-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="330f2-156">Vygeneruje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="330f2-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="330f2-157">Nevytvoří projekt před balením.</span><span class="sxs-lookup"><span data-stu-id="330f2-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="330f2-158">Umístí sestavené balíčky do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="330f2-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="330f2-159">Nastaví v balíčku příznak služby.</span><span class="sxs-lookup"><span data-stu-id="330f2-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="330f2-160">Další informace najdete na [blogu .NET: rozhraní .NET 4.5.1 podporuje aktualizace zabezpečení Microsoftu pro knihovny NuGet pro .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="330f2-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="330f2-161">Definuje hodnotu `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="330f2-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="330f2-162">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="330f2-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="330f2-163">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="330f2-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="330f2-164">Příklady</span><span class="sxs-lookup"><span data-stu-id="330f2-164">Examples</span></span>

* <span data-ttu-id="330f2-165">Sbalit projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="330f2-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="330f2-166">`app1` Sbalit projekt:</span><span class="sxs-lookup"><span data-stu-id="330f2-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="330f2-167">Sbalení projektu v aktuálním adresáři a umístění výsledných balíčků do `nupkgs` složky:</span><span class="sxs-lookup"><span data-stu-id="330f2-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="330f2-168">Sbalení projektu v aktuálním adresáři do `nupkgs` složky a přeskočení kroku sestavení:</span><span class="sxs-lookup"><span data-stu-id="330f2-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="330f2-169">S příponou verze projektu nakonfigurovanou jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v souboru *. csproj* rozbalte aktuální projekt a aktualizujte výslednou verzi balíčku s danou příponou:</span><span class="sxs-lookup"><span data-stu-id="330f2-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="330f2-170">Nastavte na verzi `2.1.0` `PackageVersion` balíčku vlastnost MSBuild:</span><span class="sxs-lookup"><span data-stu-id="330f2-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="330f2-171">Sbalení projektu pro konkrétní [cílové rozhraní](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="330f2-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="330f2-172">Sbalení projektu a použití konkrétního modulu runtime (Windows 10) pro operaci obnovení (.NET Core SDK 2,0 a novější verze):</span><span class="sxs-lookup"><span data-stu-id="330f2-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="330f2-173">Sbalení projektu pomocí [souboru. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="330f2-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
