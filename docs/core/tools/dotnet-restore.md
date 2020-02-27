---
title: dotnet restore – příkaz
description: Naučte se obnovit závislosti a nástroje specifické pro projekt pomocí příkazu dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: c221e8a34e844d0ad0482d2bb4aa6e1c795555ca
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626057"
---
# <a name="dotnet-restore"></a><span data-ttu-id="2174b-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2174b-103">dotnet restore</span></span>

<span data-ttu-id="2174b-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="2174b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2174b-105">Název</span><span class="sxs-lookup"><span data-stu-id="2174b-105">Name</span></span>

<span data-ttu-id="2174b-106">`dotnet restore` – obnoví závislosti a nástroje projektu.</span><span class="sxs-lookup"><span data-stu-id="2174b-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2174b-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="2174b-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2174b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2174b-108">Description</span></span>

<span data-ttu-id="2174b-109">Příkaz `dotnet restore` používá NuGet pro obnovení závislostí a také nástrojů specifických pro projekt, které jsou uvedeny v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="2174b-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="2174b-110">Ve výchozím nastavení jsou obnovení závislostí a nástrojů spouštěny paralelně.</span><span class="sxs-lookup"><span data-stu-id="2174b-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="2174b-111">Pro obnovení závislostí potřebuje NuGet informační kanály, ve kterých se balíčky nacházejí.</span><span class="sxs-lookup"><span data-stu-id="2174b-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="2174b-112">Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="2174b-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="2174b-113">Výchozí konfigurační soubor se poskytne při instalaci .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="2174b-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="2174b-114">Další kanály určíte tak, že vytvoříte vlastní soubor *NuGet. config* v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="2174b-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="2174b-115">Informační kanály *NuGet. config* můžete přepsat pomocí možnosti-`-s`.</span><span class="sxs-lookup"><span data-stu-id="2174b-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="2174b-116">U závislostí určíte, kde se obnovené balíčky umístí během operace obnovení pomocí argumentu `--packages`.</span><span class="sxs-lookup"><span data-stu-id="2174b-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="2174b-117">Pokud není zadaný, použije se výchozí mezipaměť balíčků NuGet, která se nachází v adresáři `.nuget/packages` v domovském adresáři uživatele ve všech operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="2174b-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="2174b-118">Například */Home/user1* v systému Linux nebo *C:\Users\user1* ve Windows.</span><span class="sxs-lookup"><span data-stu-id="2174b-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="2174b-119">U nástrojů specifických pro projekt `dotnet restore` nejprve obnovte balíček, ve kterém je nástroj zabalený, a pak pokračuje v obnovování závislostí nástroje, jak je uvedeno v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="2174b-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="2174b-120">rozdíly v NuGet. config</span><span class="sxs-lookup"><span data-stu-id="2174b-120">nuget.config differences</span></span>

<span data-ttu-id="2174b-121">Chování `dotnet restore` příkazu je ovlivněno nastavením v souboru *NuGet. config* , pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2174b-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="2174b-122">Například nastavení `globalPackagesFolder` v *souboru NuGet. config* umístí obnovené balíčky NuGet do zadané složky.</span><span class="sxs-lookup"><span data-stu-id="2174b-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="2174b-123">Toto je alternativa k zadání možnosti `--packages` v příkazu `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="2174b-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="2174b-124">Další informace najdete v referenčních informacích k [NuGet. config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="2174b-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="2174b-125">Existují tři specifická nastavení, která `dotnet restore` ignorují:</span><span class="sxs-lookup"><span data-stu-id="2174b-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="2174b-126">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="2174b-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="2174b-127">Přesměrování vazby nefungují s prvky `<PackageReference>` a .NET Core podporuje pouze `<PackageReference>` prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="2174b-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="2174b-128">řešení</span><span class="sxs-lookup"><span data-stu-id="2174b-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="2174b-129">Toto nastavení je specifické pro Visual Studio a neplatí pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2174b-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="2174b-130">.NET Core nepoužívá soubor `packages.config` a místo toho používá `<PackageReference>` prvky pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="2174b-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="2174b-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="2174b-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="2174b-132">Toto nastavení se nedá použít, protože [NuGet zatím nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) pro důvěryhodné balíčky v různých platformách.</span><span class="sxs-lookup"><span data-stu-id="2174b-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="2174b-133">Implicitní obnovení</span><span class="sxs-lookup"><span data-stu-id="2174b-133">Implicit restore</span></span>

<span data-ttu-id="2174b-134">Příkaz `dotnet restore` se v případě potřeby spustí implicitně, když spustíte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="2174b-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="2174b-135">Ve většině případů nemusíte explicitně používat příkaz `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="2174b-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="2174b-136">V některých případech může být nepraktické spustit `dotnet restore` implicitně.</span><span class="sxs-lookup"><span data-stu-id="2174b-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="2174b-137">Například některé automatizované systémy, například systémy sestavení, musí volat `dotnet restore` explicitně pro řízení, když dojde k obnovení, aby bylo možné řídit využití sítě.</span><span class="sxs-lookup"><span data-stu-id="2174b-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="2174b-138">Chcete-li zabránit spuštění `dotnet restore` implicitně, můžete použít příznak `--no-restore` s některým z těchto příkazů k zakázání implicitního obnovení.</span><span class="sxs-lookup"><span data-stu-id="2174b-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="2174b-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2174b-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="2174b-140">Volitelná cesta k souboru projektu, který má být obnoven.</span><span class="sxs-lookup"><span data-stu-id="2174b-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="2174b-141">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2174b-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2174b-142">Konfigurační soubor NuGet (*NuGet. config*), který se má použít pro operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="2174b-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="2174b-143">Zakáže obnovení více projektů paralelně.</span><span class="sxs-lookup"><span data-stu-id="2174b-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="2174b-144">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="2174b-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2174b-145">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2174b-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2174b-146">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="2174b-146">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="2174b-147">Pouze upozornit na zdroje, které selhaly, pokud existují balíčky, které splňují požadavky na verzi.</span><span class="sxs-lookup"><span data-stu-id="2174b-147">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--no-cache`**

  <span data-ttu-id="2174b-148">Určuje, že nejsou balíčky mezipaměti a požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="2174b-148">Specifies to not cache packages and HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="2174b-149">Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.</span><span class="sxs-lookup"><span data-stu-id="2174b-149">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="2174b-150">Určuje adresář pro obnovené balíčky.</span><span class="sxs-lookup"><span data-stu-id="2174b-150">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="2174b-151">Určuje modul runtime pro obnovení balíčku.</span><span class="sxs-lookup"><span data-stu-id="2174b-151">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="2174b-152">Slouží k obnovení balíčků pro moduly runtime, které nejsou explicitně uvedeny v značce `<RuntimeIdentifiers>` v souboru *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="2174b-152">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="2174b-153">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2174b-153">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="2174b-154">Zadáním této možnosti několikrát zadejte víc identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="2174b-154">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="2174b-155">Určuje zdroj balíčku NuGet, který se použije během operace obnovení.</span><span class="sxs-lookup"><span data-stu-id="2174b-155">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="2174b-156">Toto nastavení přepíše všechny zdroje zadané v souborech *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="2174b-156">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="2174b-157">Více zdrojů lze zadat zadáním této možnosti několikrát.</span><span class="sxs-lookup"><span data-stu-id="2174b-157">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--verbosity <LEVEL>`**

  <span data-ttu-id="2174b-158">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="2174b-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2174b-159">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2174b-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2174b-160">Výchozí hodnota je `minimal`.</span><span class="sxs-lookup"><span data-stu-id="2174b-160">Default value is `minimal`.</span></span>

- **`--interactive`**

  <span data-ttu-id="2174b-161">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="2174b-161">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="2174b-162">Vzhledem k tomu, že .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="2174b-162">Since .NET Core 2.1.400.</span></span>

## <a name="examples"></a><span data-ttu-id="2174b-163">Příklady</span><span class="sxs-lookup"><span data-stu-id="2174b-163">Examples</span></span>

- <span data-ttu-id="2174b-164">Obnovit závislosti a nástroje pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="2174b-164">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="2174b-165">V dané cestě se našly závislosti a nástroje pro `app1` projekt:</span><span class="sxs-lookup"><span data-stu-id="2174b-165">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="2174b-166">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, který jste zadali jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="2174b-166">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="2174b-167">Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:</span><span class="sxs-lookup"><span data-stu-id="2174b-167">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="2174b-168">Obnoví závislosti a nástroje pro projekt v aktuálním adresáři se zobrazeným podrobným výstupem:</span><span class="sxs-lookup"><span data-stu-id="2174b-168">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
