---
title: příkaz DotNet restore
description: Zjistěte, jak obnovit závislostí a specifické pro projekt nástroje pomocí příkazu dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: 3ddb9f679cfcab972483a4cb53ffe2b075867614
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613967"
---
# <a name="dotnet-restore"></a><span data-ttu-id="9f765-103">DotNet restore</span><span class="sxs-lookup"><span data-stu-id="9f765-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9f765-104">Name</span><span class="sxs-lookup"><span data-stu-id="9f765-104">Name</span></span>

<span data-ttu-id="9f765-105">`dotnet restore` -Obnoví závislostí a nástrojů projektu.</span><span class="sxs-lookup"><span data-stu-id="9f765-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9f765-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="9f765-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9f765-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="9f765-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9f765-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9f765-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="9f765-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9f765-109">Description</span></span>

<span data-ttu-id="9f765-110">`dotnet restore` Příkaz používá NuGet pro obnovení závislostí, stejně jako nástroje specifické pro projekt, které jsou uvedeny v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f765-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="9f765-111">Ve výchozím nastavení obnovení závislostí a tools spouští paralelně.</span><span class="sxs-lookup"><span data-stu-id="9f765-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="9f765-112">K obnovení závislosti, potřebuje NuGet informační kanály, kde se nacházejí balíčky.</span><span class="sxs-lookup"><span data-stu-id="9f765-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="9f765-113">Informační kanály jsou obvykle k dispozici prostřednictvím *NuGet.config* konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="9f765-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="9f765-114">Výchozí konfigurační soubor je k dispozici při instalaci nástroje rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9f765-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="9f765-115">Zadejte další informační kanály tím, že vytvoříte vlastní *NuGet.config* soubor v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="9f765-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="9f765-116">Zadejte také další kanály na vyvolání z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9f765-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="9f765-117">Pro závislosti, zadáte umístění obnoveného balíčky při použití operace obnovení `--packages` argument.</span><span class="sxs-lookup"><span data-stu-id="9f765-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="9f765-118">Pokud není zadán, výchozí mezipaměti balíčku NuGet se používá, která byla nalezena v `.nuget/packages` adresáře do domovského adresáře uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="9f765-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="9f765-119">Například */home/user1* v Linuxu nebo *C:\Users\user1* na Windows.</span><span class="sxs-lookup"><span data-stu-id="9f765-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="9f765-120">Pro nástroje specifické pro projekt `dotnet restore` nejprve obnoví balíček, ve které je zabalena nástroj a pak pokračuje k obnovení závislostí nástroje uvedené v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f765-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="9f765-121">Chování `dotnet restore` příkaz je ovlivněna některá nastavení v *Nuget.Config* soubor, pokud jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9f765-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="9f765-122">Například nastavení `globalPackagesFolder` v *NuGet.Config* umístí obnovené balíčky NuGet v zadané složce.</span><span class="sxs-lookup"><span data-stu-id="9f765-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="9f765-123">Jedná se o alternativu k určení `--packages` možnost `dotnet restore` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f765-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="9f765-124">Další informace najdete v tématu [odkaz na soubor NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="9f765-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="9f765-125">Implicitní `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="9f765-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="9f765-126">Od verze rozhraní .NET Core 2.0, `dotnet restore` spuštění implicitně v případě potřeby při vydání následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="9f765-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="9f765-127">Ve většině případů už nepotřebujete explicitně `dotnet restore` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f765-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="9f765-128">V některých případech může být nepraktické spustit `dotnet restore` implicitně.</span><span class="sxs-lookup"><span data-stu-id="9f765-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="9f765-129">Například některé automatizované systémy, jako jsou systémy sestavení potřebné k volání `dotnet restore` explicitně k řízení, pokud dojde k obnovení tak, aby se můžete řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="9f765-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="9f765-130">Aby se zabránilo `dotnet restore` ve spuštění implicitně, můžete použít `--no-restore` příznak s žádným z těchto příkazů můžete zakázat implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f765-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="9f765-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f765-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="9f765-132">Volitelná cesta k souboru projektu, chcete-li obnovit.</span><span class="sxs-lookup"><span data-stu-id="9f765-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="9f765-133">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9f765-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9f765-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="9f765-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="9f765-135">Konfigurační soubor NuGet (*NuGet.config*) pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f765-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="9f765-136">Zakáže obnovování několika projektů najednou.</span><span class="sxs-lookup"><span data-stu-id="9f765-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="9f765-137">Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9f765-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9f765-138">Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="9f765-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9f765-139">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9f765-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="9f765-140">Pouze upozornění na neúspěšné zdroje, pokud existují balíčky, které splňují požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="9f765-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="9f765-141">Určuje, balíčky a požadavky HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9f765-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="9f765-142">Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="9f765-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="9f765-143">Určuje adresář pro obnovený balíčky.</span><span class="sxs-lookup"><span data-stu-id="9f765-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9f765-144">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="9f765-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="9f765-145">Tento parametr slouží k obnovení balíčků pro moduly runtime, které nejsou výslovně uvedené v `<RuntimeIdentifiers>` značku *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="9f765-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="9f765-146">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9f765-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9f765-147">Poskytuje více identifikátorů RID, protože zadání této možnosti více než jednou.</span><span class="sxs-lookup"><span data-stu-id="9f765-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="9f765-148">Určuje zdroj balíčku NuGet pro použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f765-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="9f765-149">Toto nastavení potlačí všechny zdroje podle *NuGet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="9f765-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="9f765-150">Více zdrojů můžete zadat tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="9f765-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="9f765-151">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f765-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9f765-152">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9f765-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--interactive`

<span data-ttu-id="9f765-153">Povoluje příkazu zastavit a počkat na vstup uživatele nebo akci (třeba k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="9f765-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="9f765-154">Od .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="9f765-154">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9f765-155">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9f765-155">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="9f765-156">Konfigurační soubor NuGet (*NuGet.config*) pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f765-156">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="9f765-157">Zakáže obnovování několika projektů najednou.</span><span class="sxs-lookup"><span data-stu-id="9f765-157">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="9f765-158">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="9f765-158">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="9f765-159">Pouze upozornění na neúspěšné zdroje, pokud existují balíčky, které splňují požadavek na verzi.</span><span class="sxs-lookup"><span data-stu-id="9f765-159">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="9f765-160">Určuje, balíčky a požadavky HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9f765-160">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="9f765-161">Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="9f765-161">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="9f765-162">Určuje adresář pro obnovený balíčky.</span><span class="sxs-lookup"><span data-stu-id="9f765-162">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9f765-163">Určuje modul runtime pro obnovení balíčků.</span><span class="sxs-lookup"><span data-stu-id="9f765-163">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="9f765-164">Tento parametr slouží k obnovení balíčků pro moduly runtime, které nejsou výslovně uvedené v `<RuntimeIdentifiers>` značku *.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="9f765-164">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="9f765-165">Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9f765-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9f765-166">Poskytuje více identifikátorů RID, protože zadání této možnosti více než jednou.</span><span class="sxs-lookup"><span data-stu-id="9f765-166">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="9f765-167">Určuje zdroj balíčku NuGet pro použití během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="9f765-167">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="9f765-168">Tím se přepíše všechny zdroje podle *NuGet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="9f765-168">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="9f765-169">Více zdrojů můžete zadat tak, že zadáte tuto možnost vícekrát.</span><span class="sxs-lookup"><span data-stu-id="9f765-169">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="9f765-170">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f765-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9f765-171">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9f765-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="9f765-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="9f765-172">Examples</span></span>

<span data-ttu-id="9f765-173">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="9f765-173">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="9f765-174">Obnovte závislosti a nástroje pro `app1` projekt najít v zadané cestě:</span><span class="sxs-lookup"><span data-stu-id="9f765-174">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="9f765-175">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí jako zdroj zadaná cesta k souboru:</span><span class="sxs-lookup"><span data-stu-id="9f765-175">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="9f765-176">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souborům dvou zdrojů ve formě:</span><span class="sxs-lookup"><span data-stu-id="9f765-176">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="9f765-177">Obnovte závislosti a nástroje pro projekt do aktuálního adresáře a zobrazuje pouze minimální výstupu:</span><span class="sxs-lookup"><span data-stu-id="9f765-177">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
