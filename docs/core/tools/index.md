---
title: Nástroje rozhraní příkazového řádku .NET Core (CLI)
description: Přehled nástrojů a funkcí rozhraní příkazového řádku (CLI) .NET Core
ms.date: 08/14/2017
ms.openlocfilehash: b3bffb47ff973bd0da90e3f943e817756e563138
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714140"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="20bb1-103">Nástroje rozhraní příkazového řádku .NET Core (CLI)</span><span class="sxs-lookup"><span data-stu-id="20bb1-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="20bb1-104">Rozhraní příkazového řádku .NET Core (CLI) je nové sada nástrojů pro různé platformy pro vývoj aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="20bb1-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="20bb1-105">Rozhraní příkazového řádku je základ, na kterém můžou REST nástroje, jako jsou například integrovaná vývojová prostředí (IDEs), editory a orchestrace sestavení.</span><span class="sxs-lookup"><span data-stu-id="20bb1-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="20bb1-106">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="20bb1-106">Installation</span></span>

<span data-ttu-id="20bb1-107">Buď použijte nativní instalační programy, nebo použijte skripty instalačního prostředí:</span><span class="sxs-lookup"><span data-stu-id="20bb1-107">Either use the native installers or use the installation shell scripts:</span></span>

- <span data-ttu-id="20bb1-108">Nativní instalační programy se primárně používají na počítačích vývojáře a používají nativní mechanizmus instalace každého podporované platformy, například balíčky DEB na Ubuntu nebo sady MSI v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="20bb1-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="20bb1-109">Tyto instalační programy instalují a konfigurují prostředí pro okamžité použití vývojářem, ale vyžadují na počítači oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="20bb1-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="20bb1-110">Pokyny k instalaci si můžete zobrazit v [Průvodci instalací .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="20bb1-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
- <span data-ttu-id="20bb1-111">Skripty prostředí se primárně používají k nastavení serverů sestavení nebo k instalaci nástrojů bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="20bb1-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="20bb1-112">Nainstalovat skripty neinstalují požadavky na počítač, který je nutné nainstalovat ručně.</span><span class="sxs-lookup"><span data-stu-id="20bb1-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="20bb1-113">Další informace naleznete v [tématu Install Script reference](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="20bb1-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="20bb1-114">Informace o tom, jak nastavit rozhraní příkazového řádku pro server sestavení kontinuální integrace (CI), najdete v tématu [použití .NET Core SDK a nástrojů v rámci kontinuální integrace (CI)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="20bb1-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="20bb1-115">Ve výchozím nastavení se rozhraní příkazového řádku instaluje souběžně (SxS), takže v jednom počítači může existovat více verzí nástrojů rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="20bb1-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="20bb1-116">Určení verze používané na počítači, kde je nainstalováno více verzí, je podrobněji vysvětleno v části [ovladače](#driver) .</span><span class="sxs-lookup"><span data-stu-id="20bb1-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="20bb1-117">Příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="20bb1-117">CLI commands</span></span>

<span data-ttu-id="20bb1-118">Ve výchozím nastavení jsou nainstalovány následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="20bb1-118">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="20bb1-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="20bb1-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="20bb1-120">**Základní příkazy**</span><span class="sxs-lookup"><span data-stu-id="20bb1-120">**Basic commands**</span></span>

- [<span data-ttu-id="20bb1-121">new</span><span class="sxs-lookup"><span data-stu-id="20bb1-121">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="20bb1-122">restore</span><span class="sxs-lookup"><span data-stu-id="20bb1-122">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="20bb1-123">budování</span><span class="sxs-lookup"><span data-stu-id="20bb1-123">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="20bb1-124">publikování</span><span class="sxs-lookup"><span data-stu-id="20bb1-124">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="20bb1-125">spouštěl</span><span class="sxs-lookup"><span data-stu-id="20bb1-125">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="20bb1-126">test</span><span class="sxs-lookup"><span data-stu-id="20bb1-126">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="20bb1-127">vstest</span><span class="sxs-lookup"><span data-stu-id="20bb1-127">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="20bb1-128">pack</span><span class="sxs-lookup"><span data-stu-id="20bb1-128">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="20bb1-129">migraci</span><span class="sxs-lookup"><span data-stu-id="20bb1-129">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="20bb1-130">Odstranit</span><span class="sxs-lookup"><span data-stu-id="20bb1-130">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="20bb1-131">sln</span><span class="sxs-lookup"><span data-stu-id="20bb1-131">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="20bb1-132">Pomoc</span><span class="sxs-lookup"><span data-stu-id="20bb1-132">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="20bb1-133">store</span><span class="sxs-lookup"><span data-stu-id="20bb1-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="20bb1-134">**Příkazy pro úpravy projektu**</span><span class="sxs-lookup"><span data-stu-id="20bb1-134">**Project modification commands**</span></span>

- [<span data-ttu-id="20bb1-135">Přidat balíček</span><span class="sxs-lookup"><span data-stu-id="20bb1-135">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="20bb1-136">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="20bb1-136">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="20bb1-137">odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="20bb1-137">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="20bb1-138">odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="20bb1-138">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="20bb1-139">odkaz na seznam</span><span class="sxs-lookup"><span data-stu-id="20bb1-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="20bb1-140">**Rozšířené příkazy**</span><span class="sxs-lookup"><span data-stu-id="20bb1-140">**Advanced commands**</span></span>

- [<span data-ttu-id="20bb1-141">odstranění NuGet</span><span class="sxs-lookup"><span data-stu-id="20bb1-141">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="20bb1-142">národní prostředí NuGet</span><span class="sxs-lookup"><span data-stu-id="20bb1-142">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="20bb1-143">nabízení NuGet</span><span class="sxs-lookup"><span data-stu-id="20bb1-143">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="20bb1-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="20bb1-144">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="20bb1-145">instalace skriptu dotnet</span><span class="sxs-lookup"><span data-stu-id="20bb1-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="20bb1-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="20bb1-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="20bb1-147">**Základní příkazy**</span><span class="sxs-lookup"><span data-stu-id="20bb1-147">**Basic commands**</span></span>

- [<span data-ttu-id="20bb1-148">new</span><span class="sxs-lookup"><span data-stu-id="20bb1-148">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="20bb1-149">restore</span><span class="sxs-lookup"><span data-stu-id="20bb1-149">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="20bb1-150">budování</span><span class="sxs-lookup"><span data-stu-id="20bb1-150">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="20bb1-151">publikování</span><span class="sxs-lookup"><span data-stu-id="20bb1-151">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="20bb1-152">spouštěl</span><span class="sxs-lookup"><span data-stu-id="20bb1-152">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="20bb1-153">test</span><span class="sxs-lookup"><span data-stu-id="20bb1-153">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="20bb1-154">vstest</span><span class="sxs-lookup"><span data-stu-id="20bb1-154">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="20bb1-155">pack</span><span class="sxs-lookup"><span data-stu-id="20bb1-155">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="20bb1-156">migraci</span><span class="sxs-lookup"><span data-stu-id="20bb1-156">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="20bb1-157">Odstranit</span><span class="sxs-lookup"><span data-stu-id="20bb1-157">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="20bb1-158">sln</span><span class="sxs-lookup"><span data-stu-id="20bb1-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="20bb1-159">**Příkazy pro úpravy projektu**</span><span class="sxs-lookup"><span data-stu-id="20bb1-159">**Project modification commands**</span></span>

- [<span data-ttu-id="20bb1-160">Přidat balíček</span><span class="sxs-lookup"><span data-stu-id="20bb1-160">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="20bb1-161">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="20bb1-161">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="20bb1-162">odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="20bb1-162">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="20bb1-163">odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="20bb1-163">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="20bb1-164">odkaz na seznam</span><span class="sxs-lookup"><span data-stu-id="20bb1-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="20bb1-165">**Rozšířené příkazy**</span><span class="sxs-lookup"><span data-stu-id="20bb1-165">**Advanced commands**</span></span>

- [<span data-ttu-id="20bb1-166">odstranění NuGet</span><span class="sxs-lookup"><span data-stu-id="20bb1-166">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="20bb1-167">národní prostředí NuGet</span><span class="sxs-lookup"><span data-stu-id="20bb1-167">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="20bb1-168">nabízení NuGet</span><span class="sxs-lookup"><span data-stu-id="20bb1-168">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="20bb1-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="20bb1-169">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="20bb1-170">instalace skriptu dotnet</span><span class="sxs-lookup"><span data-stu-id="20bb1-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="20bb1-171">Rozhraní příkazového řádku přijímá model rozšiřitelnosti, který umožňuje určit další nástroje pro vaše projekty.</span><span class="sxs-lookup"><span data-stu-id="20bb1-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="20bb1-172">Další informace naleznete v tématu [.NET Core CLI rozšiřující model](extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="20bb1-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="20bb1-173">Struktura příkazu</span><span class="sxs-lookup"><span data-stu-id="20bb1-173">Command structure</span></span>

<span data-ttu-id="20bb1-174">Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a možných [argumentů](#arguments) příkazů a [možností](#options).</span><span class="sxs-lookup"><span data-stu-id="20bb1-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="20bb1-175">Tento model se zobrazí ve většině operací CLI, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, protože následující příkazy se zobrazí při spuštění z adresáře s názvem *my_app*:</span><span class="sxs-lookup"><span data-stu-id="20bb1-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="20bb1-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="20bb1-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="20bb1-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="20bb1-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="20bb1-178">kartu Ovladač</span><span class="sxs-lookup"><span data-stu-id="20bb1-178">Driver</span></span>

<span data-ttu-id="20bb1-179">Ovladač má název [dotnet](dotnet.md) a má dvě zodpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) , nebo spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="20bb1-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="20bb1-180">Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="20bb1-180">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="20bb1-181">Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="20bb1-181">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="20bb1-182">Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte možnost `--fx-version <VERSION>` (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="20bb1-182">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="20bb1-183">Když zadáte příkaz do ovladače, `dotnet.exe` spustí proces spuštění příkazu CLI.</span><span class="sxs-lookup"><span data-stu-id="20bb1-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="20bb1-184">Příklad:</span><span class="sxs-lookup"><span data-stu-id="20bb1-184">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="20bb1-185">Nejdřív ovladač určuje verzi sady SDK, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="20bb1-185">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="20bb1-186">Pokud není k dispozici [možnost Global. JSON](global-json.md), použije se nejnovější verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="20bb1-186">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="20bb1-187">To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.</span><span class="sxs-lookup"><span data-stu-id="20bb1-187">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="20bb1-188">Po určení verze sady SDK se spustí příkaz.</span><span class="sxs-lookup"><span data-stu-id="20bb1-188">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="20bb1-189">Příkaz</span><span class="sxs-lookup"><span data-stu-id="20bb1-189">Command</span></span>

<span data-ttu-id="20bb1-190">Příkaz provede akci.</span><span class="sxs-lookup"><span data-stu-id="20bb1-190">The command performs an action.</span></span> <span data-ttu-id="20bb1-191">Například `dotnet build` sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="20bb1-191">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="20bb1-192">`dotnet publish` publikuje kód.</span><span class="sxs-lookup"><span data-stu-id="20bb1-192">`dotnet publish` publishes code.</span></span> <span data-ttu-id="20bb1-193">Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.</span><span class="sxs-lookup"><span data-stu-id="20bb1-193">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="20bb1-194">Arguments</span><span class="sxs-lookup"><span data-stu-id="20bb1-194">Arguments</span></span>

<span data-ttu-id="20bb1-195">Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali.</span><span class="sxs-lookup"><span data-stu-id="20bb1-195">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="20bb1-196">Například při spuštění `dotnet publish my_app.csproj`argument `my_app.csproj` označuje projekt k publikování a je předán do příkazu `publish`.</span><span class="sxs-lookup"><span data-stu-id="20bb1-196">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="20bb1-197">Možnosti</span><span class="sxs-lookup"><span data-stu-id="20bb1-197">Options</span></span>

<span data-ttu-id="20bb1-198">Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="20bb1-198">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="20bb1-199">Například když spustíte `dotnet publish --output /build_output`, možnost `--output` a její hodnota se předají do příkazu `publish`.</span><span class="sxs-lookup"><span data-stu-id="20bb1-199">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="20bb1-200">Migrace z Project. JSON</span><span class="sxs-lookup"><span data-stu-id="20bb1-200">Migration from project.json</span></span>

<span data-ttu-id="20bb1-201">Pokud jste použili nástroj Preview 2 pro vytváření projektů založených na *projektu Project. JSON*, Projděte si téma věnované [migraci dotnet](dotnet-migrate.md) pro informace o migraci projektu do MSBuild/ *. csproj* pro použití s nástroji pro vydávání verzí.</span><span class="sxs-lookup"><span data-stu-id="20bb1-201">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="20bb1-202">Pro projekty .NET Core vytvořené před vydáním nástroje verze Preview 2 buď ručně aktualizujte projekt podle pokynů v části [migrace z DNX na .NET Core CLI (Project. JSON)](../migration/from-dnx.md) a pak použijte `dotnet migrate` nebo přímo upgradujte projekty.</span><span class="sxs-lookup"><span data-stu-id="20bb1-202">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="20bb1-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20bb1-203">See also</span></span>

- [<span data-ttu-id="20bb1-204">dotnet/CLI – úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="20bb1-204">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="20bb1-205">Průvodce instalací .NET Core</span><span class="sxs-lookup"><span data-stu-id="20bb1-205">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
