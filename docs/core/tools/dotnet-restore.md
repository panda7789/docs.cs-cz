---
title: příkaz Obnovit DotNet - .NET Core rozhraní příkazového řádku
description: Zjistěte, jak obnovit závislosti a specifické pro projekt nástroje pomocí příkazu restore dotnet.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 0eaab1aa1bc52bd5b3c51a6ed2dd7a59c35a4aa5
ms.sourcegitcommit: 736ec4d3e2c74895b47a0d36126657b95da383c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2018
ms.locfileid: "37140252"
---
# <a name="dotnet-restore"></a><span data-ttu-id="86e37-103">obnovení DotNet.</span><span class="sxs-lookup"><span data-stu-id="86e37-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="86e37-104">Název</span><span class="sxs-lookup"><span data-stu-id="86e37-104">Name</span></span>

<span data-ttu-id="86e37-105">`dotnet restore` -Obnoví závislosti a nástroje projektu.</span><span class="sxs-lookup"><span data-stu-id="86e37-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="86e37-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="86e37-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="86e37-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="86e37-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="86e37-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="86e37-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="86e37-109">Popis</span><span class="sxs-lookup"><span data-stu-id="86e37-109">Description</span></span>

<span data-ttu-id="86e37-110">`dotnet restore` Příkaz používá NuGet Obnovit závislosti, jakož i projektu konkrétní nástroje, které jsou určené v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="86e37-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="86e37-111">Ve výchozím nastavení jsou paralelně spustit obnovení závislosti a nástroje.</span><span class="sxs-lookup"><span data-stu-id="86e37-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="86e37-112">Chcete-li obnovit závislosti, musí NuGet informační kanály, kde se nachází balíčky.</span><span class="sxs-lookup"><span data-stu-id="86e37-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="86e37-113">Informační kanály se obvykle poskytují prostřednictvím *NuGet.config* konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="86e37-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="86e37-114">Výchozí konfigurační soubor je zadat při instalaci nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="86e37-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="86e37-115">Zadejte další informační kanály tak, že vytvoříte vlastní *NuGet.config* soubor v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="86e37-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="86e37-116">Můžete také určit další kanály pro volání na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="86e37-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="86e37-117">Závislosti, zadáte umístění obnoveného balíčky během obnovení operace pomocí `--packages` argument.</span><span class="sxs-lookup"><span data-stu-id="86e37-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="86e37-118">Pokud není zadáno, výchozí mezipaměti balíček NuGet se používá, který se nachází v `.nuget/packages` adresář v domovském adresáři uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="86e37-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="86e37-119">Například */home/user1* v systému Linux nebo *C:\Users\user1* v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="86e37-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="86e37-120">Pro konkrétní projekt nástrojů, `dotnet restore` nejprve obnoví balíček, ve kterém se nástroj nachází v balení a potom pokračuje k obnovení nástroje závislosti uvedeného v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="86e37-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="86e37-121">Chování `dotnet restore` příkaz je ovlivňován některá nastavení v *Nuget.Config* soubor, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="86e37-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="86e37-122">Například nastavení `globalPackagesFolder` v *NuGet.Config* umístí obnovené balíčků NuGet v zadané složce.</span><span class="sxs-lookup"><span data-stu-id="86e37-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="86e37-123">Jde o alternativu k určení `--packages` možnost `dotnet restore` příkaz.</span><span class="sxs-lookup"><span data-stu-id="86e37-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="86e37-124">Další informace najdete v tématu [NuGet.Config odkaz](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="86e37-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="86e37-125">Implicitní `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="86e37-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="86e37-126">Od verze rozhraní .NET 2.0 jádra, `dotnet restore` spuštění implicitně v případě potřeby při vydání následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="86e37-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="86e37-127">Ve většině případů potřebujete už explicitně použít `dotnet restore` příkaz.</span><span class="sxs-lookup"><span data-stu-id="86e37-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="86e37-128">V některých případech může být praktické, že lze spustit `dotnet restore` implicitně.</span><span class="sxs-lookup"><span data-stu-id="86e37-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="86e37-129">Například některé automatizované systémy, jako je například systémy sestavení muset volat `dotnet restore` explicitně k řízení, když dojde k obnovení, abyste se mohli řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="86e37-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="86e37-130">Aby se zabránilo `dotnet restore` ve spuštění implicitně, můžete použít `--no-restore` příznak s žádným z těchto příkazů zakázat implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="86e37-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="86e37-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="86e37-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="86e37-132">Cesty k souboru projektu k obnovení.</span><span class="sxs-lookup"><span data-stu-id="86e37-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="86e37-133">Možnosti</span><span class="sxs-lookup"><span data-stu-id="86e37-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="86e37-134">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="86e37-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="86e37-135">Konfigurační soubor NuGet (*NuGet.config*) používat pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="86e37-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="86e37-136">Zakáže obnovení více projektů současně.</span><span class="sxs-lookup"><span data-stu-id="86e37-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="86e37-137">Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="86e37-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="86e37-138">Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="86e37-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="86e37-139">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="86e37-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="86e37-140">Pouze upozornění na selhání zdroje, pokud jsou balíčky splňuje požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="86e37-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="86e37-141">Určuje, pro balíčky a žádostí HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="86e37-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="86e37-142">Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="86e37-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="86e37-143">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="86e37-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="86e37-144">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="86e37-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="86e37-145">Slouží k obnovení balíčků pro moduly runtime není explicitně uvedené v `<RuntimeIdentifiers>` značky v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="86e37-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="86e37-146">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="86e37-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="86e37-147">Zadejte více identifikátorů RID tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="86e37-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="86e37-148">Určuje zdroj balíčku NuGet k použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="86e37-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="86e37-149">Toto nastavení potlačí všechny zdroje, zadaný v *NuGet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="86e37-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="86e37-150">Zadáním více než jednou. tuto možnost lze zadat více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="86e37-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="86e37-151">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="86e37-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="86e37-152">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="86e37-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="86e37-153">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="86e37-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="86e37-154">Konfigurační soubor NuGet (*NuGet.config*) používat pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="86e37-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="86e37-155">Zakáže obnovení více projektů současně.</span><span class="sxs-lookup"><span data-stu-id="86e37-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="86e37-156">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="86e37-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="86e37-157">Pouze upozornění na selhání zdroje, pokud jsou balíčky splňuje požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="86e37-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="86e37-158">Určuje, pro balíčky a žádostí HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="86e37-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="86e37-159">Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="86e37-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="86e37-160">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="86e37-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="86e37-161">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="86e37-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="86e37-162">Slouží k obnovení balíčků pro moduly runtime není explicitně uvedené v `<RuntimeIdentifiers>` značky v *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="86e37-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="86e37-163">Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="86e37-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="86e37-164">Zadejte více identifikátorů RID tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="86e37-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="86e37-165">Určuje zdroj balíčku NuGet k použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="86e37-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="86e37-166">Všechny zdroje, zadaný v přepíše *NuGet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="86e37-166">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="86e37-167">Zadáním více než jednou. tuto možnost lze zadat více zdrojů.</span><span class="sxs-lookup"><span data-stu-id="86e37-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="86e37-168">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="86e37-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="86e37-169">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="86e37-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="86e37-170">Příklady</span><span class="sxs-lookup"><span data-stu-id="86e37-170">Examples</span></span>

<span data-ttu-id="86e37-171">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="86e37-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="86e37-172">Závislosti a nástroje pro obnovení `app1` v zadané cestě nalezen projektu:</span><span class="sxs-lookup"><span data-stu-id="86e37-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="86e37-173">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesta k souboru, který je k dispozici jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="86e37-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="86e37-174">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souborům dvě zadané jako zdroje:</span><span class="sxs-lookup"><span data-stu-id="86e37-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="86e37-175">Obnovte závislosti a nástroje pro projekt v aktuální adresář a zobrazuje pouze minimální výstup:</span><span class="sxs-lookup"><span data-stu-id="86e37-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
