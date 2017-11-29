---
title: "příkaz pack DotNet - .NET Core rozhraní příkazového řádku"
description: "Příkaz pack dotnet vytvoří balíčky NuGet pro projekt .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 8594c863d67baf0237b63e61f28ca9ee315eeddf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-pack"></a><span data-ttu-id="02a4d-103">pack DotNet.</span><span class="sxs-lookup"><span data-stu-id="02a4d-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="02a4d-104">Název</span><span class="sxs-lookup"><span data-stu-id="02a4d-104">Name</span></span>

<span data-ttu-id="02a4d-105">`dotnet pack`-Pack kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="02a4d-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="02a4d-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="02a4d-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="02a4d-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="02a4d-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="02a4d-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="02a4d-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="02a4d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="02a4d-109">Description</span></span>

<span data-ttu-id="02a4d-110">`dotnet pack` Příkaz vytvoří projekt a vytvořit balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="02a4d-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="02a4d-111">Výsledek tohoto příkazu je balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="02a4d-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="02a4d-112">Pokud `--include-symbols` možnost nachází, je vytvořen jiný balíček obsahující symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="02a4d-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="02a4d-113">Závislosti NuGet sbalené projektu se přidají do *příponou .nuspec* souboru tak, aby správně přeložit, když je balíček nainstalován.</span><span class="sxs-lookup"><span data-stu-id="02a4d-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="02a4d-114">Odkazy na projekt na projekt nejsou zabalené do projektu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="02a4d-115">V současné době musí mít balíček podle projektů, pokud máte závislosti projektu k projektu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="02a4d-116">Ve výchozím nastavení `dotnet pack` nejprve sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="02a4d-117">Pokud chcete-li se tomu vyhnout, předat `--no-build` možnost.</span><span class="sxs-lookup"><span data-stu-id="02a4d-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="02a4d-118">Toto je často užitečný ve scénářích sestavení nepřetržité integrace (CI), které víte, že kód byl dříve vytvořený.</span><span class="sxs-lookup"><span data-stu-id="02a4d-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="02a4d-119">Můžete zadat vlastnosti nástroje MSBuild k `dotnet pack` příkazu pro proces okolních.</span><span class="sxs-lookup"><span data-stu-id="02a4d-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="02a4d-120">Další informace najdete v tématu [NuGet metadata vlastnosti](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="02a4d-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="arguments"></a><span data-ttu-id="02a4d-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="02a4d-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="02a4d-122">Projekt pack.</span><span class="sxs-lookup"><span data-stu-id="02a4d-122">The project to pack.</span></span> <span data-ttu-id="02a4d-123">Je buď cestu k [csproj souboru](csproj.md) nebo do adresáře.</span><span class="sxs-lookup"><span data-stu-id="02a4d-123">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="02a4d-124">Při vynechání je použita k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="02a4d-124">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="02a4d-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="02a4d-125">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="02a4d-126">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="02a4d-126">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="02a4d-127">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="02a4d-127">Defines the build configuration.</span></span> <span data-ttu-id="02a4d-128">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-128">The default value is `Debug`.</span></span>

<span data-ttu-id="02a4d-129">`--force`Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="02a4d-129">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="02a4d-130">Jde o ekvivalent odstraňování *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="02a4d-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="02a4d-131">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="02a4d-131">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="02a4d-132">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="02a4d-132">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="02a4d-133">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-133">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="02a4d-134">Generuje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-134">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="02a4d-135">Není sestavení projektu před okolních.</span><span class="sxs-lookup"><span data-stu-id="02a4d-135">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="02a4d-136">Ignoruje odkazy na projekt na projekt a obnoví pouze kořenové projektu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="02a4d-137">Neprovede implicitní obnovení, při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="02a4d-138">Zadaný adresář umístí připravené balíčky.</span><span class="sxs-lookup"><span data-stu-id="02a4d-138">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="02a4d-139">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="02a4d-139">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="02a4d-140">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="02a4d-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="02a4d-141">Nastaví příznak obsluhovatelná v balíčku.</span><span class="sxs-lookup"><span data-stu-id="02a4d-141">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="02a4d-142">Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="02a4d-142">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="02a4d-143">Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-143">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="02a4d-144">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="02a4d-145">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="02a4d-146">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="02a4d-146">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="02a4d-147">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="02a4d-147">Defines the build configuration.</span></span> <span data-ttu-id="02a4d-148">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-148">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="02a4d-149">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="02a4d-149">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="02a4d-150">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="02a4d-150">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="02a4d-151">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-151">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="02a4d-152">Generuje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-152">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="02a4d-153">Není sestavení projektu před okolních.</span><span class="sxs-lookup"><span data-stu-id="02a4d-153">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="02a4d-154">Zadaný adresář umístí připravené balíčky.</span><span class="sxs-lookup"><span data-stu-id="02a4d-154">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="02a4d-155">Nastaví příznak obsluhovatelná v balíčku.</span><span class="sxs-lookup"><span data-stu-id="02a4d-155">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="02a4d-156">Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="02a4d-156">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="02a4d-157">Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-157">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="02a4d-158">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="02a4d-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="02a4d-159">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="02a4d-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="02a4d-160">Příklady</span><span class="sxs-lookup"><span data-stu-id="02a4d-160">Examples</span></span>

<span data-ttu-id="02a4d-161">Sada pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="02a4d-161">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="02a4d-162">Sada `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="02a4d-162">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="02a4d-163">Pack projekt v aktuálním adresáři a umístí do výsledného balíčky `nupkgs` složky:</span><span class="sxs-lookup"><span data-stu-id="02a4d-163">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="02a4d-164">Pack projekt v aktuálním adresáři do `nupkgs` složku a přeskočit krok sestavení:</span><span class="sxs-lookup"><span data-stu-id="02a4d-164">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="02a4d-165">V projektu je verze přípona nakonfigurovat jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v *.csproj* souboru, pack aktuální projekt a aktualizaci výsledné verzi balíčku s příponou dané:</span><span class="sxs-lookup"><span data-stu-id="02a4d-165">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="02a4d-166">Nastavte verzi balíčku `2.1.0` s `PackageVersion` vlastnosti MSBuild:</span><span class="sxs-lookup"><span data-stu-id="02a4d-166">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`
