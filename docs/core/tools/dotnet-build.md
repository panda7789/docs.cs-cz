---
title: DotNet sestavení command - .NET Core rozhraní příkazového řádku
description: Dotnet sestavení příkaz sestavení projektu a všechny jeho závislé součásti.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 6b0b7bc11b560d8632b38f1dfa4e7eb3ce6c54d2
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697128"
---
# <a name="dotnet-build"></a><span data-ttu-id="b4d8d-103">sestavení pro DotNet.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b4d8d-104">Název</span><span class="sxs-lookup"><span data-stu-id="b4d8d-104">Name</span></span>

<span data-ttu-id="b4d8d-105">`dotnet build` -Sestavení projektu a všechny jeho závislé součásti.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b4d8d-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="b4d8d-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b4d8d-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="b4d8d-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b4d8d-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="b4d8d-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="b4d8d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b4d8d-109">Description</span></span>

<span data-ttu-id="b4d8d-110">`dotnet build` Příkaz sestavení projektu a jeho závislosti do sady binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="b4d8d-111">Binární soubory zahrnují projektu kódu v souborech Intermediate Language (IL) s *.dll* rozšíření a symbol soubory používané pro ladění pomocí *PDB* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="b4d8d-112">Soubor JSON závislosti (*\*. deps.json*) vytváří, jsou uvedené závislosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="b4d8d-113">A  *\*. runtimeconfig.json* vytvořil soubor, který určuje sdílený modul runtime a její verzi pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="b4d8d-114">Pokud projekt má závislosti třetích stran, například knihoven z NuGet, se z mezipaměti NuGet rozpoznána a nejsou k dispozici integrované výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="b4d8d-115">Si uvědomit, produkt `dotnet build` není připraven k přesunu do jiného počítače ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="b4d8d-116">Tím se liší od chování rozhraní .NET Framework v které vytváření spustitelný projekt (aplikace) vytváří výstup, který je spustitelného na libovolném počítači nainstalovanou rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="b4d8d-117">Pokud chcete, aby na podobném principu s .NET Core, budete muset použít [dotnet publikování](dotnet-publish.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="b4d8d-118">Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="b4d8d-119">Vytváření vyžaduje *project.assets.json* souboru, který uvádí závislosti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="b4d8d-120">Soubor je vytvořen, když [ `dotnet restore` ](dotnet-restore.md) se spustí.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="b4d8d-121">Bez souboru prostředků v místě nelze nástroji vyřešit referenční sestavení, což vede k chybám.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="b4d8d-122">S .NET Core 1.x SDK potřebné ke spuštění explicitně `dotnet restore` dřív, než spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="b4d8d-123">Od verze rozhraní .NET Core SDK 2.0, `dotnet restore` implicitně spouští při spuštění `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="b4d8d-124">Pokud chcete zakázat implicitní obnovení při spuštění příkazu sestavení, můžete předat `--no-restore` možnost.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="b4d8d-125">`dotnet build` používá pro sestavení projektu MSBuild, takže podporuje paralelní i přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-125">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="b4d8d-126">Další informace najdete v tématu [přírůstková sestavení](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-126">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="b4d8d-127">Kromě jeho možností `dotnet build` příkaz přijímá MSBuild možnosti, jako například `/p` pro nastavení vlastností nebo `/l` k definování protokolovacího nástroje.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `/p` for setting properties or `/l` to define a logger.</span></span> <span data-ttu-id="b4d8d-128">Další informace o těchto možnostech najdete v tématu [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-128">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="b4d8d-129">Jestli je projekt spustitelný soubor nebo ne je dáno `<OutputType>` vlastnost v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="b4d8d-130">Následující příklad ukazuje projekt, který vytváří spustitelného kódu:</span><span class="sxs-lookup"><span data-stu-id="b4d8d-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="b4d8d-131">Chcete-li vytvořit knihovnu, vynechejte `<OutputType>` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="b4d8d-132">Hlavní rozdíl ve vytvořené výstupu je, že IL DLL pro knihovnu neobsahuje vstupní body a nelze provést.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

## <a name="arguments"></a><span data-ttu-id="b4d8d-133">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4d8d-133">Arguments</span></span>

`PROJECT`

<span data-ttu-id="b4d8d-134">K vytvoření souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-134">The project file to build.</span></span> <span data-ttu-id="b4d8d-135">Pokud projekt soubor není zadán, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, které *proj* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-135">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="b4d8d-136">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b4d8d-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b4d8d-137">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="b4d8d-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="b4d8d-138">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-138">Defines the build configuration.</span></span> <span data-ttu-id="b4d8d-139">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b4d8d-140">Zkompiluje pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="b4d8d-141">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

<span data-ttu-id="b4d8d-142">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b4d8d-143">Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="b4d8d-144">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="b4d8d-145">Ignoruje odkazů (P2P) projekt na projekt a pouze sestavení projektu zadaný kořenový.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-145">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="b4d8d-146">Označí sestavení jako bezpečné pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="b4d8d-147">Tento příznak vypne přírůstkové kompilace a vynutí čistou opětovné sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-147">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="b4d8d-148">Neprovede implicitní obnovení během vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-148">Doesn't execute an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b4d8d-149">Adresář, do níž umístíte integrovaný binární soubory.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="b4d8d-150">Budete také muset definovat `--framework` Pokud zadáte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b4d8d-151">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-151">Specifies the target runtime.</span></span> <span data-ttu-id="b4d8d-152">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b4d8d-153">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b4d8d-154">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="b4d8d-155">Definuje verze přípona hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="b4d8d-156">Formát řídí pokyny verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b4d8d-157">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="b4d8d-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="b4d8d-158">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-158">Defines the build configuration.</span></span> <span data-ttu-id="b4d8d-159">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b4d8d-160">Zkompiluje pro konkrétní [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="b4d8d-161">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="b4d8d-162">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="b4d8d-163">Ignoruje odkazů (P2P) projekt na projekt a pouze sestavení projektu zadaný kořenový.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-163">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="b4d8d-164">Označí sestavení jako bezpečné pro přírůstkové sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="b4d8d-165">Tento příznak vypne přírůstkové kompilace a vynutí čistou opětovné sestavení grafu závislostí projektu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-165">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b4d8d-166">Adresář, do níž umístíte integrovaný binární soubory.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="b4d8d-167">Budete také muset definovat `--framework` Pokud zadáte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b4d8d-168">Určuje cílový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-168">Specifies the target runtime.</span></span> <span data-ttu-id="b4d8d-169">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b4d8d-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b4d8d-170">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b4d8d-171">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="b4d8d-172">Definuje verze přípona hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="b4d8d-173">Formát řídí pokyny verze NuGet.</span><span class="sxs-lookup"><span data-stu-id="b4d8d-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="b4d8d-174">Příklady</span><span class="sxs-lookup"><span data-stu-id="b4d8d-174">Examples</span></span>

<span data-ttu-id="b4d8d-175">Sestavte projekt a jeho závislé součásti:</span><span class="sxs-lookup"><span data-stu-id="b4d8d-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="b4d8d-176">Sestavte projekt a jeho závislosti pomocí konfigurace verze:</span><span class="sxs-lookup"><span data-stu-id="b4d8d-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="b4d8d-177">Sestavte projekt a jeho závislosti pro konkrétní runtime (v tomto příkladu Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="b4d8d-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

<span data-ttu-id="b4d8d-178">Sestavte projekt a použijte zadaný zdroj balíčku NuGet během operace obnovení (.NET Core SDK 2.0 a novější):</span><span class="sxs-lookup"><span data-stu-id="b4d8d-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet build --source c:\packages\mypackages`