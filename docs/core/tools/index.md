---
title: Rozhraní příkazového řádku .NET Core
titleSuffix: ''
description: Přehled .NET Core CLI a jeho funkcí.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920481"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="76144-103">Přehled .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="76144-103">.NET Core CLI overview</span></span>

<span data-ttu-id="76144-104">Rozhraní příkazového řádku .NET Core (CLI) je sada nástrojů pro různé platformy pro vývoj, sestavování, spouštění a publikování aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76144-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="76144-105">.NET Core CLI je součástí [.NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="76144-105">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="76144-106">Informace o tom, jak nainstalovat .NET Core SDK, najdete v tématu [instalace .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="76144-106">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="76144-107">Příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="76144-107">CLI commands</span></span>

<span data-ttu-id="76144-108">Ve výchozím nastavení jsou nainstalovány následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="76144-108">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="76144-109">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="76144-109">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="76144-110">**Základní příkazy**</span><span class="sxs-lookup"><span data-stu-id="76144-110">**Basic commands**</span></span>

- [<span data-ttu-id="76144-111">new</span><span class="sxs-lookup"><span data-stu-id="76144-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="76144-112">restore</span><span class="sxs-lookup"><span data-stu-id="76144-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="76144-113">budování</span><span class="sxs-lookup"><span data-stu-id="76144-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="76144-114">opětovn</span><span class="sxs-lookup"><span data-stu-id="76144-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="76144-115">spouštěl</span><span class="sxs-lookup"><span data-stu-id="76144-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="76144-116">test</span><span class="sxs-lookup"><span data-stu-id="76144-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="76144-117">vstest</span><span class="sxs-lookup"><span data-stu-id="76144-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="76144-118">pack</span><span class="sxs-lookup"><span data-stu-id="76144-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="76144-119">Přenes</span><span class="sxs-lookup"><span data-stu-id="76144-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="76144-120">Odstranit</span><span class="sxs-lookup"><span data-stu-id="76144-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="76144-121">sln</span><span class="sxs-lookup"><span data-stu-id="76144-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="76144-122">Pomoc</span><span class="sxs-lookup"><span data-stu-id="76144-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="76144-123">store</span><span class="sxs-lookup"><span data-stu-id="76144-123">store</span></span>](dotnet-store.md)

<span data-ttu-id="76144-124">**Příkazy pro úpravy projektu**</span><span class="sxs-lookup"><span data-stu-id="76144-124">**Project modification commands**</span></span>

- [<span data-ttu-id="76144-125">Přidat balíček</span><span class="sxs-lookup"><span data-stu-id="76144-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="76144-126">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="76144-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="76144-127">odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="76144-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="76144-128">odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="76144-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="76144-129">odkaz na seznam</span><span class="sxs-lookup"><span data-stu-id="76144-129">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="76144-130">**Rozšířené příkazy**</span><span class="sxs-lookup"><span data-stu-id="76144-130">**Advanced commands**</span></span>

- [<span data-ttu-id="76144-131">odstranění NuGet</span><span class="sxs-lookup"><span data-stu-id="76144-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="76144-132">národní prostředí NuGet</span><span class="sxs-lookup"><span data-stu-id="76144-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="76144-133">nabízení NuGet</span><span class="sxs-lookup"><span data-stu-id="76144-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="76144-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="76144-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="76144-135">instalace skriptu dotnet</span><span class="sxs-lookup"><span data-stu-id="76144-135">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="76144-136">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="76144-136">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="76144-137">**Základní příkazy**</span><span class="sxs-lookup"><span data-stu-id="76144-137">**Basic commands**</span></span>

- [<span data-ttu-id="76144-138">new</span><span class="sxs-lookup"><span data-stu-id="76144-138">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="76144-139">restore</span><span class="sxs-lookup"><span data-stu-id="76144-139">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="76144-140">budování</span><span class="sxs-lookup"><span data-stu-id="76144-140">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="76144-141">opětovn</span><span class="sxs-lookup"><span data-stu-id="76144-141">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="76144-142">spouštěl</span><span class="sxs-lookup"><span data-stu-id="76144-142">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="76144-143">test</span><span class="sxs-lookup"><span data-stu-id="76144-143">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="76144-144">vstest</span><span class="sxs-lookup"><span data-stu-id="76144-144">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="76144-145">pack</span><span class="sxs-lookup"><span data-stu-id="76144-145">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="76144-146">Přenes</span><span class="sxs-lookup"><span data-stu-id="76144-146">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="76144-147">Odstranit</span><span class="sxs-lookup"><span data-stu-id="76144-147">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="76144-148">sln</span><span class="sxs-lookup"><span data-stu-id="76144-148">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="76144-149">**Příkazy pro úpravy projektu**</span><span class="sxs-lookup"><span data-stu-id="76144-149">**Project modification commands**</span></span>

- [<span data-ttu-id="76144-150">Přidat balíček</span><span class="sxs-lookup"><span data-stu-id="76144-150">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="76144-151">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="76144-151">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="76144-152">odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="76144-152">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="76144-153">odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="76144-153">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="76144-154">odkaz na seznam</span><span class="sxs-lookup"><span data-stu-id="76144-154">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="76144-155">**Rozšířené příkazy**</span><span class="sxs-lookup"><span data-stu-id="76144-155">**Advanced commands**</span></span>

- [<span data-ttu-id="76144-156">odstranění NuGet</span><span class="sxs-lookup"><span data-stu-id="76144-156">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="76144-157">národní prostředí NuGet</span><span class="sxs-lookup"><span data-stu-id="76144-157">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="76144-158">nabízení NuGet</span><span class="sxs-lookup"><span data-stu-id="76144-158">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="76144-159">msbuild</span><span class="sxs-lookup"><span data-stu-id="76144-159">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="76144-160">instalace skriptu dotnet</span><span class="sxs-lookup"><span data-stu-id="76144-160">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="76144-161">Rozhraní příkazového řádku přijímá model rozšiřitelnosti, který umožňuje určit další nástroje pro vaše projekty.</span><span class="sxs-lookup"><span data-stu-id="76144-161">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="76144-162">Další informace naleznete v tématu [.NET Core CLI rozšiřující model](extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="76144-162">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="76144-163">Struktura příkazu</span><span class="sxs-lookup"><span data-stu-id="76144-163">Command structure</span></span>

<span data-ttu-id="76144-164">Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a možných [argumentů](#arguments) příkazů a [možností](#options).</span><span class="sxs-lookup"><span data-stu-id="76144-164">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="76144-165">Tento model se zobrazí ve většině operací CLI, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, protože následující příkazy se zobrazí při spuštění z adresáře s názvem *my_app*:</span><span class="sxs-lookup"><span data-stu-id="76144-165">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="76144-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="76144-166">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="76144-167">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="76144-167">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="76144-168">Faktorů</span><span class="sxs-lookup"><span data-stu-id="76144-168">Driver</span></span>

<span data-ttu-id="76144-169">Ovladač má název [dotnet](dotnet.md) a má dvě zodpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) , nebo spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="76144-169">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="76144-170">Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="76144-170">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="76144-171">Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="76144-171">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="76144-172">Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte možnost `--fx-version <VERSION>` (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="76144-172">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="76144-173">Když zadáte příkaz do ovladače, `dotnet.exe` spustí proces spuštění příkazu CLI.</span><span class="sxs-lookup"><span data-stu-id="76144-173">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="76144-174">Příklad:</span><span class="sxs-lookup"><span data-stu-id="76144-174">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="76144-175">Nejdřív ovladač určuje verzi sady SDK, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="76144-175">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="76144-176">Pokud není k dispozici [možnost Global. JSON](global-json.md), použije se nejnovější verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="76144-176">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="76144-177">To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.</span><span class="sxs-lookup"><span data-stu-id="76144-177">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="76144-178">Po určení verze sady SDK se spustí příkaz.</span><span class="sxs-lookup"><span data-stu-id="76144-178">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="76144-179">Příkaz</span><span class="sxs-lookup"><span data-stu-id="76144-179">Command</span></span>

<span data-ttu-id="76144-180">Příkaz provede akci.</span><span class="sxs-lookup"><span data-stu-id="76144-180">The command performs an action.</span></span> <span data-ttu-id="76144-181">Například `dotnet build` sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="76144-181">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="76144-182">`dotnet publish` publikuje kód.</span><span class="sxs-lookup"><span data-stu-id="76144-182">`dotnet publish` publishes code.</span></span> <span data-ttu-id="76144-183">Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.</span><span class="sxs-lookup"><span data-stu-id="76144-183">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="76144-184">Arguments</span><span class="sxs-lookup"><span data-stu-id="76144-184">Arguments</span></span>

<span data-ttu-id="76144-185">Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali.</span><span class="sxs-lookup"><span data-stu-id="76144-185">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="76144-186">Například při spuštění `dotnet publish my_app.csproj`argument `my_app.csproj` označuje projekt k publikování a je předán do příkazu `publish`.</span><span class="sxs-lookup"><span data-stu-id="76144-186">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="76144-187">Možnosti</span><span class="sxs-lookup"><span data-stu-id="76144-187">Options</span></span>

<span data-ttu-id="76144-188">Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="76144-188">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="76144-189">Například když spustíte `dotnet publish --output /build_output`, možnost `--output` a její hodnota se předají do příkazu `publish`.</span><span class="sxs-lookup"><span data-stu-id="76144-189">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="76144-190">Migrace z Project. JSON</span><span class="sxs-lookup"><span data-stu-id="76144-190">Migration from project.json</span></span>

<span data-ttu-id="76144-191">Pokud jste použili nástroj Preview 2 pro vytváření projektů založených na *projektu Project. JSON*, Projděte si téma věnované [migraci dotnet](dotnet-migrate.md) pro informace o migraci projektu do MSBuild/ *. csproj* pro použití s nástroji pro vydávání verzí.</span><span class="sxs-lookup"><span data-stu-id="76144-191">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="76144-192">Pro projekty .NET Core vytvořené před vydáním nástroje verze Preview 2 buď ručně aktualizujte projekt podle pokynů v části [migrace z DNX na .NET Core CLI (Project. JSON)](../migration/from-dnx.md) a pak použijte `dotnet migrate` nebo přímo upgradujte projekty.</span><span class="sxs-lookup"><span data-stu-id="76144-192">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="76144-193">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76144-193">See also</span></span>

- [<span data-ttu-id="76144-194">dotnet/úložiště GitHub SDK</span><span class="sxs-lookup"><span data-stu-id="76144-194">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="76144-195">Průvodce instalací .NET Core</span><span class="sxs-lookup"><span data-stu-id="76144-195">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
