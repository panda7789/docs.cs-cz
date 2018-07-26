---
title: příkaz DotNet restore - rozhraní příkazového řádku .NET Core
description: Zjistěte, jak obnovit závislostí a specifické pro projekt nástroje pomocí příkazu dotnet restore.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 0eaab1aa1bc52bd5b3c51a6ed2dd7a59c35a4aa5
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960585"
---
# <a name="dotnet-restore"></a><span data-ttu-id="41acc-103">DotNet restore</span><span class="sxs-lookup"><span data-stu-id="41acc-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="41acc-104">Název</span><span class="sxs-lookup"><span data-stu-id="41acc-104">Name</span></span>

<span data-ttu-id="41acc-105">`dotnet restore` -Obnoví závislostí a nástrojů projektu.</span><span class="sxs-lookup"><span data-stu-id="41acc-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="41acc-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="41acc-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="41acc-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="41acc-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="41acc-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="41acc-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="41acc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="41acc-109">Description</span></span>

<span data-ttu-id="41acc-110">`dotnet restore` Příkaz používá NuGet pro obnovení závislostí, stejně jako nástroje specifické pro projekt, které jsou uvedeny v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="41acc-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="41acc-111">Ve výchozím nastavení obnovení závislostí a tools spouští paralelně.</span><span class="sxs-lookup"><span data-stu-id="41acc-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="41acc-112">K obnovení závislosti, potřebuje NuGet informační kanály, kde se nacházejí balíčky.</span><span class="sxs-lookup"><span data-stu-id="41acc-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="41acc-113">Informační kanály jsou obvykle k dispozici prostřednictvím *NuGet.config* konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="41acc-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="41acc-114">Výchozí konfigurační soubor je k dispozici při instalaci nástroje rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="41acc-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="41acc-115">Zadejte další informační kanály tím, že vytvoříte vlastní *NuGet.config* soubor v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="41acc-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="41acc-116">Zadejte také další kanály na vyvolání z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="41acc-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="41acc-117">Pro závislosti, zadáte umístění obnoveného balíčky při použití operace obnovení `--packages` argument.</span><span class="sxs-lookup"><span data-stu-id="41acc-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="41acc-118">Pokud není zadán, výchozí mezipaměti balíčku NuGet se používá, která byla nalezena v `.nuget/packages` adresáře do domovského adresáře uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="41acc-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="41acc-119">Například */home/user1* v Linuxu nebo *C:\Users\user1* na Windows.</span><span class="sxs-lookup"><span data-stu-id="41acc-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="41acc-120">Pro nástroje specifické pro projekt `dotnet restore` nejprve obnoví balíček, ve které je zabalena nástroj a pak pokračuje k obnovení závislostí nástroje uvedené v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="41acc-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="41acc-121">Chování `dotnet restore` příkaz je ovlivněna některá nastavení v *Nuget.Config* soubor, pokud jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="41acc-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="41acc-122">Například nastavení `globalPackagesFolder` v *NuGet.Config* umístí obnovené balíčky NuGet v zadané složce.</span><span class="sxs-lookup"><span data-stu-id="41acc-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="41acc-123">Jedná se o alternativu k určení `--packages` možnost `dotnet restore` příkazu.</span><span class="sxs-lookup"><span data-stu-id="41acc-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="41acc-124">Další informace najdete v tématu [odkaz na soubor NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="41acc-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="41acc-125">Implicitní `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="41acc-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="41acc-126">Od verze rozhraní .NET Core 2.0, `dotnet restore` spuštění implicitně v případě potřeby při vydání následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="41acc-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="41acc-127">Ve většině případů už nepotřebujete explicitně `dotnet restore` příkazu.</span><span class="sxs-lookup"><span data-stu-id="41acc-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="41acc-128">V některých případech může být nepraktické spustit `dotnet restore` implicitně.</span><span class="sxs-lookup"><span data-stu-id="41acc-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="41acc-129">Například některé automatizované systémy, jako jsou systémy sestavení potřebné k volání `dotnet restore` explicitně k řízení, pokud dojde k obnovení tak, aby se můžete řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="41acc-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="41acc-130">Aby se zabránilo `dotnet restore` ve spuštění implicitně, můžete použít `--no-restore` příznak s žádným z těchto příkazů můžete zakázat implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="41acc-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="41acc-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="41acc-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="41acc-132">Volitelná cesta k souboru projektu, chcete-li obnovit.</span><span class="sxs-lookup"><span data-stu-id="41acc-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="41acc-133">Možnosti</span><span class="sxs-lookup"><span data-stu-id="41acc-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="41acc-134">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="41acc-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="41acc-135">Konfigurační soubor NuGet (*NuGet.config*) pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="41acc-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="41acc-136">Zakáže obnovování několika projektů najednou.</span><span class="sxs-lookup"><span data-stu-id="41acc-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="41acc-137">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="41acc-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="41acc-138">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="41acc-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="41acc-139">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="41acc-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="41acc-140">Pouze upozornění na neúspěšné zdroje, pokud existují balíčky, které splňují požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="41acc-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="41acc-141">Určuje, balíčky a požadavky HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="41acc-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="41acc-142">Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="41acc-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="41acc-143">Určuje adresář pro obnovený balíčky.</span><span class="sxs-lookup"><span data-stu-id="41acc-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="41acc-144">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="41acc-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="41acc-145">Tento parametr slouží k obnovení balíčků pro moduly runtime, které nejsou výslovně uvedené v `<RuntimeIdentifiers>` značku *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="41acc-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="41acc-146">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="41acc-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="41acc-147">Poskytuje více identifikátorů RID, protože zadání této možnosti více než jednou.</span><span class="sxs-lookup"><span data-stu-id="41acc-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="41acc-148">Určuje zdroj balíčku NuGet pro použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="41acc-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="41acc-149">Toto nastavení potlačí všechny zdroje podle *NuGet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="41acc-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="41acc-150">Více zdrojů můžete zadat tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="41acc-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="41acc-151">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="41acc-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="41acc-152">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="41acc-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="41acc-153">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="41acc-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="41acc-154">Konfigurační soubor NuGet (*NuGet.config*) pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="41acc-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="41acc-155">Zakáže obnovování několika projektů najednou.</span><span class="sxs-lookup"><span data-stu-id="41acc-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="41acc-156">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="41acc-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="41acc-157">Pouze upozornění na neúspěšné zdroje, pokud existují balíčky, které splňují požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="41acc-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="41acc-158">Určuje, balíčky a požadavky HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="41acc-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="41acc-159">Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="41acc-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="41acc-160">Určuje adresář pro obnovený balíčky.</span><span class="sxs-lookup"><span data-stu-id="41acc-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="41acc-161">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="41acc-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="41acc-162">Tento parametr slouží k obnovení balíčků pro moduly runtime, které nejsou výslovně uvedené v `<RuntimeIdentifiers>` značku *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="41acc-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="41acc-163">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="41acc-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="41acc-164">Poskytuje více identifikátorů RID, protože zadání této možnosti více než jednou.</span><span class="sxs-lookup"><span data-stu-id="41acc-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="41acc-165">Určuje zdroj balíčku NuGet pro použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="41acc-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="41acc-166">Tím se přepíše všechny zdroje podle *NuGet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="41acc-166">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="41acc-167">Více zdrojů můžete zadat tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="41acc-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="41acc-168">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="41acc-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="41acc-169">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="41acc-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="41acc-170">Příklady</span><span class="sxs-lookup"><span data-stu-id="41acc-170">Examples</span></span>

<span data-ttu-id="41acc-171">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="41acc-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="41acc-172">Obnovte závislosti a nástroje pro `app1` projekt najít v zadané cestě:</span><span class="sxs-lookup"><span data-stu-id="41acc-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="41acc-173">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí jako zdroj zadaná cesta k souboru:</span><span class="sxs-lookup"><span data-stu-id="41acc-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="41acc-174">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souborům dvou zdrojů ve formě:</span><span class="sxs-lookup"><span data-stu-id="41acc-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="41acc-175">Obnovte závislosti a nástroje pro projekt do aktuálního adresáře a zobrazuje pouze minimální výstupu:</span><span class="sxs-lookup"><span data-stu-id="41acc-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
