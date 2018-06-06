---
title: příkaz pack DotNet - .NET Core rozhraní příkazového řádku
description: Příkaz pack dotnet vytvoří balíčky NuGet pro projekt .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8c2569ec7598b21fe9b673176143d0e54b9eb065
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696816"
---
# <a name="dotnet-pack"></a><span data-ttu-id="a7d36-103">pack DotNet.</span><span class="sxs-lookup"><span data-stu-id="a7d36-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a7d36-104">Název</span><span class="sxs-lookup"><span data-stu-id="a7d36-104">Name</span></span>

<span data-ttu-id="a7d36-105">`dotnet pack` -Pack kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7d36-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7d36-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a7d36-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a7d36-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="a7d36-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a7d36-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="a7d36-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a7d36-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a7d36-109">Description</span></span>

<span data-ttu-id="a7d36-110">`dotnet pack` Příkaz vytvoří projekt a vytvořit balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7d36-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="a7d36-111">Výsledek tohoto příkazu je balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7d36-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="a7d36-112">Pokud `--include-symbols` možnost nachází, je vytvořen jiný balíček obsahující symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="a7d36-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="a7d36-113">Závislosti NuGet sbalené projektu se přidají do *příponou .nuspec* souboru tak, aby správně přeložit, když je balíček nainstalován.</span><span class="sxs-lookup"><span data-stu-id="a7d36-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="a7d36-114">Odkazy na projekt na projekt nejsou zabalené do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="a7d36-115">V současné době musí mít balíček podle projektů, pokud máte závislosti projektu k projektu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="a7d36-116">Ve výchozím nastavení `dotnet pack` nejprve sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="a7d36-117">Pokud chcete-li se tomu vyhnout, předat `--no-build` možnost.</span><span class="sxs-lookup"><span data-stu-id="a7d36-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="a7d36-118">Tato možnost je často užitečný ve scénářích sestavení nepřetržité integrace (CI), které víte, že kód byl dříve vytvořený.</span><span class="sxs-lookup"><span data-stu-id="a7d36-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="a7d36-119">Můžete zadat vlastnosti nástroje MSBuild k `dotnet pack` příkazu pro proces okolních.</span><span class="sxs-lookup"><span data-stu-id="a7d36-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="a7d36-120">Další informace najdete v tématu [NuGet metadata vlastnosti](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="a7d36-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="a7d36-121">[Příklady](#examples) část ukazuje způsob použití nástroje MSBuild přepínače pro několik různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="a7d36-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="a7d36-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="a7d36-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a7d36-123">Projekt pack.</span><span class="sxs-lookup"><span data-stu-id="a7d36-123">The project to pack.</span></span> <span data-ttu-id="a7d36-124">Je buď cestu k [csproj souboru](csproj.md) nebo do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a7d36-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="a7d36-125">Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="a7d36-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="a7d36-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a7d36-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a7d36-127">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="a7d36-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a7d36-128">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="a7d36-128">Defines the build configuration.</span></span> <span data-ttu-id="a7d36-129">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-129">The default value is `Debug`.</span></span>

`--force`

<span data-ttu-id="a7d36-130">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="a7d36-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a7d36-131">Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="a7d36-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="a7d36-132">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a7d36-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="a7d36-133">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7d36-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="a7d36-134">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="a7d36-135">Generuje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="a7d36-136">Není sestavení projektu před okolních.</span><span class="sxs-lookup"><span data-stu-id="a7d36-136">Doesn't build the project before packing.</span></span> <span data-ttu-id="a7d36-137">Také implicitní nastaví `--no-restore` příznak.</span><span class="sxs-lookup"><span data-stu-id="a7d36-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="a7d36-138">Ignoruje odkazy na projekt na projekt a obnoví pouze kořenové projektu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-138">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="a7d36-139">Implicitní obnovení není spustit, když spustíte příkaz.</span><span class="sxs-lookup"><span data-stu-id="a7d36-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a7d36-140">Zadaný adresář umístí připravené balíčky.</span><span class="sxs-lookup"><span data-stu-id="a7d36-140">Places the built packages in the directory specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a7d36-141">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="a7d36-141">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="a7d36-142">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a7d36-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="a7d36-143">Nastaví příznak obsluhovatelná v balíčku.</span><span class="sxs-lookup"><span data-stu-id="a7d36-143">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="a7d36-144">Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="a7d36-144">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a7d36-145">Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-145">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a7d36-146">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a7d36-147">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a7d36-148">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="a7d36-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a7d36-149">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="a7d36-149">Defines the build configuration.</span></span> <span data-ttu-id="a7d36-150">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-150">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="a7d36-151">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a7d36-151">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="a7d36-152">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7d36-152">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="a7d36-153">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-153">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="a7d36-154">Generuje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-154">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="a7d36-155">Není sestavení projektu před okolních.</span><span class="sxs-lookup"><span data-stu-id="a7d36-155">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a7d36-156">Zadaný adresář umístí připravené balíčky.</span><span class="sxs-lookup"><span data-stu-id="a7d36-156">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="a7d36-157">Nastaví příznak obsluhovatelná v balíčku.</span><span class="sxs-lookup"><span data-stu-id="a7d36-157">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="a7d36-158">Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="a7d36-158">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a7d36-159">Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-159">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a7d36-160">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="a7d36-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a7d36-161">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a7d36-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a7d36-162">Příklady</span><span class="sxs-lookup"><span data-stu-id="a7d36-162">Examples</span></span>

<span data-ttu-id="a7d36-163">Sada pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="a7d36-163">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="a7d36-164">Sada `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="a7d36-164">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`

<span data-ttu-id="a7d36-165">Pack projekt v aktuálním adresáři a umístí do výsledného balíčky `nupkgs` složky:</span><span class="sxs-lookup"><span data-stu-id="a7d36-165">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="a7d36-166">Pack projekt v aktuálním adresáři do `nupkgs` složku a přeskočit krok sestavení:</span><span class="sxs-lookup"><span data-stu-id="a7d36-166">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="a7d36-167">V projektu je verze přípona nakonfigurovat jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v *.csproj* souboru, pack aktuální projekt a aktualizaci výsledné verzi balíčku s příponou dané:</span><span class="sxs-lookup"><span data-stu-id="a7d36-167">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="a7d36-168">Nastavte verzi balíčku `2.1.0` s `PackageVersion` vlastnosti MSBuild:</span><span class="sxs-lookup"><span data-stu-id="a7d36-168">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="a7d36-169">Pack projekt pro konkrétní [cílové rozhraní](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="a7d36-169">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`

<span data-ttu-id="a7d36-170">Pack projektu a pro operaci obnovení (.NET Core SDK 2.0 a novějších verzí) pomocí konkrétní runtime (Windows 10):</span><span class="sxs-lookup"><span data-stu-id="a7d36-170">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet pack --runtime win10-x64`