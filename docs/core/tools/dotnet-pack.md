---
title: "příkaz pack DotNet - .NET Core rozhraní příkazového řádku"
description: "Příkaz pack dotnet vytvoří balíčky NuGet pro projekt .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 12/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 28cd05db0643097a7271fd0488354846598ba493
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-pack"></a><span data-ttu-id="25bb9-103">pack DotNet.</span><span class="sxs-lookup"><span data-stu-id="25bb9-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="25bb9-104">Název</span><span class="sxs-lookup"><span data-stu-id="25bb9-104">Name</span></span>

<span data-ttu-id="25bb9-105">`dotnet pack`-Pack kód do balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="25bb9-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="25bb9-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="25bb9-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="25bb9-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="25bb9-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="25bb9-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="25bb9-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="25bb9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="25bb9-109">Description</span></span>

<span data-ttu-id="25bb9-110">`dotnet pack` Příkaz vytvoří projekt a vytvořit balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="25bb9-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="25bb9-111">Výsledek tohoto příkazu je balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="25bb9-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="25bb9-112">Pokud `--include-symbols` možnost nachází, je vytvořen jiný balíček obsahující symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="25bb9-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="25bb9-113">Závislosti NuGet sbalené projektu se přidají do *příponou .nuspec* souboru tak, aby správně přeložit, když je balíček nainstalován.</span><span class="sxs-lookup"><span data-stu-id="25bb9-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="25bb9-114">Odkazy na projekt na projekt nejsou zabalené do projektu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="25bb9-115">V současné době musí mít balíček podle projektů, pokud máte závislosti projektu k projektu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="25bb9-116">Ve výchozím nastavení `dotnet pack` nejprve sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="25bb9-117">Pokud chcete-li se tomu vyhnout, předat `--no-build` možnost.</span><span class="sxs-lookup"><span data-stu-id="25bb9-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="25bb9-118">Toto je často užitečný ve scénářích sestavení nepřetržité integrace (CI), které víte, že kód byl dříve vytvořený.</span><span class="sxs-lookup"><span data-stu-id="25bb9-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="25bb9-119">Můžete zadat vlastnosti nástroje MSBuild k `dotnet pack` příkazu pro proces okolních.</span><span class="sxs-lookup"><span data-stu-id="25bb9-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="25bb9-120">Další informace najdete v tématu [NuGet metadata vlastnosti](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="25bb9-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="25bb9-121">[Příklady](#examples) část ukazuje způsob použití nástroje MSBuild přepínače pro několik různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="25bb9-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

## <a name="arguments"></a><span data-ttu-id="25bb9-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="25bb9-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="25bb9-123">Projekt pack.</span><span class="sxs-lookup"><span data-stu-id="25bb9-123">The project to pack.</span></span> <span data-ttu-id="25bb9-124">Je buď cestu k [csproj souboru](csproj.md) nebo do adresáře.</span><span class="sxs-lookup"><span data-stu-id="25bb9-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="25bb9-125">Při vynechání je použita k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="25bb9-125">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="25bb9-126">Možnosti</span><span class="sxs-lookup"><span data-stu-id="25bb9-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="25bb9-127">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="25bb9-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="25bb9-128">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="25bb9-128">Defines the build configuration.</span></span> <span data-ttu-id="25bb9-129">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-129">The default value is `Debug`.</span></span>

<span data-ttu-id="25bb9-130">`--force`Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="25bb9-130">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="25bb9-131">Jde o ekvivalent odstraňování *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="25bb9-131">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="25bb9-132">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="25bb9-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="25bb9-133">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="25bb9-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="25bb9-134">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="25bb9-135">Generuje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="25bb9-136">Není sestavení projektu před okolních.</span><span class="sxs-lookup"><span data-stu-id="25bb9-136">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="25bb9-137">Ignoruje odkazy na projekt na projekt a obnoví pouze kořenové projektu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-137">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="25bb9-138">Neprovede implicitní obnovení, při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-138">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="25bb9-139">Zadaný adresář umístí připravené balíčky.</span><span class="sxs-lookup"><span data-stu-id="25bb9-139">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="25bb9-140">Určuje cílový modul runtime pro obnovení balíčků pro.</span><span class="sxs-lookup"><span data-stu-id="25bb9-140">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="25bb9-141">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="25bb9-141">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="25bb9-142">Nastaví příznak obsluhovatelná v balíčku.</span><span class="sxs-lookup"><span data-stu-id="25bb9-142">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="25bb9-143">Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="25bb9-143">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="25bb9-144">Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-144">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="25bb9-145">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="25bb9-146">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="25bb9-147">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="25bb9-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="25bb9-148">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="25bb9-148">Defines the build configuration.</span></span> <span data-ttu-id="25bb9-149">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-149">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="25bb9-150">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="25bb9-150">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="25bb9-151">Obsahuje zdrojové soubory v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="25bb9-151">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="25bb9-152">Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-152">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="25bb9-153">Generuje symboly `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-153">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="25bb9-154">Není sestavení projektu před okolních.</span><span class="sxs-lookup"><span data-stu-id="25bb9-154">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="25bb9-155">Zadaný adresář umístí připravené balíčky.</span><span class="sxs-lookup"><span data-stu-id="25bb9-155">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="25bb9-156">Nastaví příznak obsluhovatelná v balíčku.</span><span class="sxs-lookup"><span data-stu-id="25bb9-156">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="25bb9-157">Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="25bb9-157">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="25bb9-158">Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-158">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="25bb9-159">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="25bb9-159">Sets the verbosity level of the command.</span></span> <span data-ttu-id="25bb9-160">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="25bb9-160">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="25bb9-161">Příklady</span><span class="sxs-lookup"><span data-stu-id="25bb9-161">Examples</span></span>

<span data-ttu-id="25bb9-162">Sada pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="25bb9-162">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="25bb9-163">Sada `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="25bb9-163">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="25bb9-164">Pack projekt v aktuálním adresáři a umístí do výsledného balíčky `nupkgs` složky:</span><span class="sxs-lookup"><span data-stu-id="25bb9-164">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="25bb9-165">Pack projekt v aktuálním adresáři do `nupkgs` složku a přeskočit krok sestavení:</span><span class="sxs-lookup"><span data-stu-id="25bb9-165">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="25bb9-166">V projektu je verze přípona nakonfigurovat jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v *.csproj* souboru, pack aktuální projekt a aktualizaci výsledné verzi balíčku s příponou dané:</span><span class="sxs-lookup"><span data-stu-id="25bb9-166">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="25bb9-167">Nastavte verzi balíčku `2.1.0` s `PackageVersion` vlastnosti MSBuild:</span><span class="sxs-lookup"><span data-stu-id="25bb9-167">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="25bb9-168">Pack projekt pro konkrétní [cílové rozhraní](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="25bb9-168">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`
