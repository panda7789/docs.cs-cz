---
title: "příkaz Obnovit DotNet - .NET Core rozhraní příkazového řádku"
description: "Zjistěte, jak obnovit závislosti a specifické pro projekt nástroje pomocí příkazu restore dotnet."
keywords: "příkaz DotNet obnovit, rozhraní příkazového řádku, rozhraní příkazového řádku, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 82a78dcb0cc85e2ba087b6df5ee029cbfb687358
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-restore"></a><span data-ttu-id="77b1f-104">obnovení DotNet.</span><span class="sxs-lookup"><span data-stu-id="77b1f-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="77b1f-105">Název</span><span class="sxs-lookup"><span data-stu-id="77b1f-105">Name</span></span>

<span data-ttu-id="77b1f-106">`dotnet restore`-Obnoví závislosti a nástroje projektu.</span><span class="sxs-lookup"><span data-stu-id="77b1f-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="77b1f-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="77b1f-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="77b1f-108">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="77b1f-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="77b1f-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="77b1f-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="77b1f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="77b1f-110">Description</span></span>

<span data-ttu-id="77b1f-111">`dotnet restore` Příkaz používá NuGet Obnovit závislosti, jakož i projektu konkrétní nástroje, které jsou určené v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="77b1f-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="77b1f-112">Ve výchozím nastavení jsou v paralelní provést obnovení závislosti a nástroje.</span><span class="sxs-lookup"><span data-stu-id="77b1f-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="77b1f-113">Chcete-li obnovit závislosti, musí NuGet informační kanály, kde se nachází balíčky.</span><span class="sxs-lookup"><span data-stu-id="77b1f-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="77b1f-114">Informační kanály se obvykle poskytují prostřednictvím *NuGet.config* konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="77b1f-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="77b1f-115">Výchozí konfigurační soubor je zadat při instalaci nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="77b1f-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="77b1f-116">Zadejte další informační kanály tak, že vytvoříte vlastní *NuGet.config* soubor v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="77b1f-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="77b1f-117">Můžete také určit další kanály pro volání na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="77b1f-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="77b1f-118">Závislosti, zadáte umístění obnoveného balíčky během obnovení operace pomocí `--packages` argument.</span><span class="sxs-lookup"><span data-stu-id="77b1f-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="77b1f-119">Pokud není zadáno, výchozí mezipaměti balíček NuGet se používá, který se nachází v `.nuget/packages` adresář v domovském adresáři uživatele ve všech operačních systémů (například */home/user1* v systému Linux nebo *C:\Users\user1*  v systému Windows).</span><span class="sxs-lookup"><span data-stu-id="77b1f-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="77b1f-120">Pro konkrétní projekt nástrojů, `dotnet restore` nejprve obnoví balíček, ve kterém se nástroj nachází v balení a potom pokračuje k obnovení nástroje závislosti uvedeného v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="77b1f-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="77b1f-121">Chování `dotnet restore` příkaz je ovlivňován některá nastavení v *Nuget.Config* soubor, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="77b1f-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="77b1f-122">Například nastavení `globalPackagesFolder` v *NuGet.Config* umístí obnovené balíčků NuGet v zadané složce.</span><span class="sxs-lookup"><span data-stu-id="77b1f-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="77b1f-123">Jde o alternativu k určení `--packages` možnost `dotnet restore` příkaz.</span><span class="sxs-lookup"><span data-stu-id="77b1f-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="77b1f-124">Další informace najdete v tématu [NuGet.Config odkaz](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="77b1f-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="arguments"></a><span data-ttu-id="77b1f-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="77b1f-125">Arguments</span></span>

`ROOT`

<span data-ttu-id="77b1f-126">Cesty k souboru projektu k obnovení.</span><span class="sxs-lookup"><span data-stu-id="77b1f-126">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="77b1f-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="77b1f-127">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="77b1f-128">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="77b1f-128">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="77b1f-129">Konfigurační soubor NuGet (*NuGet.config*) používat pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="77b1f-129">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="77b1f-130">Zakáže obnovení více projektů současně.</span><span class="sxs-lookup"><span data-stu-id="77b1f-130">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="77b1f-131">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="77b1f-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="77b1f-132">Jde o ekvivalent odstraňování *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="77b1f-132">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="77b1f-133">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="77b1f-133">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="77b1f-134">Pouze upozornění na selhání zdroje, pokud jsou balíčky splňuje požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="77b1f-134">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="77b1f-135">Určuje, pro balíčky a žádostí HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="77b1f-135">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="77b1f-136">Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="77b1f-136">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="77b1f-137">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="77b1f-137">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="77b1f-138">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="77b1f-138">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="77b1f-139">Slouží k obnovení balíčků pro moduly runtime není explicitně uvedené v `<RuntimeIdentifiers>` značky v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="77b1f-139">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="77b1f-140">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="77b1f-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="77b1f-141">Zadejte více identifikátorů RID tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="77b1f-141">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="77b1f-142">Určuje zdroj balíčku NuGet k použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="77b1f-142">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="77b1f-143">Všechny zdroje, zadaný v přepíše *NuGet.config* souborům.</span><span class="sxs-lookup"><span data-stu-id="77b1f-143">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="77b1f-144">Zadáním více než jednou. tuto možnost lze zadat více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="77b1f-144">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="77b1f-145">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="77b1f-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="77b1f-146">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="77b1f-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="77b1f-147">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="77b1f-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="77b1f-148">Konfigurační soubor NuGet (*NuGet.config*) používat pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="77b1f-148">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="77b1f-149">Zakáže obnovení více projektů současně.</span><span class="sxs-lookup"><span data-stu-id="77b1f-149">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="77b1f-150">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="77b1f-150">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="77b1f-151">Pouze upozornění na selhání zdroje, pokud jsou balíčky splňuje požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="77b1f-151">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="77b1f-152">Určuje, pro balíčky a žádostí HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="77b1f-152">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="77b1f-153">Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="77b1f-153">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="77b1f-154">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="77b1f-154">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="77b1f-155">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="77b1f-155">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="77b1f-156">Slouží k obnovení balíčků pro moduly runtime není explicitně uvedené v `<RuntimeIdentifiers>` značky v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="77b1f-156">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="77b1f-157">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="77b1f-157">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="77b1f-158">Zadejte více identifikátorů RID tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="77b1f-158">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="77b1f-159">Určuje zdroj balíčku NuGet k použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="77b1f-159">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="77b1f-160">Všechny zdroje, zadaný v přepíše *NuGet.config* souborům.</span><span class="sxs-lookup"><span data-stu-id="77b1f-160">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="77b1f-161">Zadáním více než jednou. tuto možnost lze zadat více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="77b1f-161">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="77b1f-162">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="77b1f-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="77b1f-163">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="77b1f-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="77b1f-164">Příklady</span><span class="sxs-lookup"><span data-stu-id="77b1f-164">Examples</span></span>

<span data-ttu-id="77b1f-165">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="77b1f-165">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="77b1f-166">Závislosti a nástroje pro obnovení `app1` v zadané cestě nalezen projektu:</span><span class="sxs-lookup"><span data-stu-id="77b1f-166">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="77b1f-167">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesta k souboru, který je k dispozici jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="77b1f-167">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="77b1f-168">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souborům dvě zadané jako zdroje:</span><span class="sxs-lookup"><span data-stu-id="77b1f-168">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="77b1f-169">Obnovte závislosti a nástroje pro projekt v aktuální adresář a zobrazuje pouze minimální výstup:</span><span class="sxs-lookup"><span data-stu-id="77b1f-169">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
