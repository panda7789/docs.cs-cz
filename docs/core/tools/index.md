---
title: Nástroje .NET core rozhraní příkazového řádku (CLI)
description: Přehled funkcí a nástrojů pro .NET Core rozhraní příkazového řádku (CLI).
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: e174867ce06e573fc85579183df0196d8276fb37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647421"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="06f1a-103">Nástroje .NET core rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="06f1a-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="06f1a-104">Rozhraní příkazového řádku .NET Core (CLI) je nová sada nástrojů napříč platformami pro vývoj aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="06f1a-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="06f1a-105">Rozhraní příkazového řádku je jako základ, na které chcete získat podrobnější popis nástroje, jako je integrované vývojové prostředí (IDE), editory a orchestrátorů sestavení, můžete rozhraní rest.</span><span class="sxs-lookup"><span data-stu-id="06f1a-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="06f1a-106">Instalace</span><span class="sxs-lookup"><span data-stu-id="06f1a-106">Installation</span></span>

<span data-ttu-id="06f1a-107">Použijte nativních instalačních programů nebo použít skripty prostředí instalace:</span><span class="sxs-lookup"><span data-stu-id="06f1a-107">Either use the native installers or use the installation shell scripts:</span></span>

* <span data-ttu-id="06f1a-108">Nativních instalačních programů se používají především na počítačích pro vývojáře a použití každé podporované platformy nativní nainstalujte mechanismus, například DEB balíčků na Ubuntu nebo MSI svazků na Windows.</span><span class="sxs-lookup"><span data-stu-id="06f1a-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="06f1a-109">Tyto instalační programy instalace a konfigurace prostředí k okamžitému použití vývojář, ale vyžadují oprávnění správce na počítači.</span><span class="sxs-lookup"><span data-stu-id="06f1a-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="06f1a-110">Můžete zobrazit na pokyny k instalaci v [Průvodce instalací rozhraní .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="06f1a-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
* <span data-ttu-id="06f1a-111">Skripty prostředí se používají především pro nastavení serverů sestavení nebo když chcete nainstalovat nástroje bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="06f1a-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="06f1a-112">Nainstalujte skripty neinstalujte požadavky na počítač, který musí ručně doinstalovat.</span><span class="sxs-lookup"><span data-stu-id="06f1a-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="06f1a-113">Další informace najdete v tématu [instalaci skriptu referenční téma](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="06f1a-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="06f1a-114">Informace o tom, jak nastavení rozhraní příkazového řádku na serveru sestavení kontinuální integrace (CI), najdete v části [pomocí .NET Core SDK a nástroje v kontinuální integrace (CI)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="06f1a-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="06f1a-115">Ve výchozím nastavení nainstaluje rozhraní příkazového řádku (SxS) způsobem vedle sebe, tak více verzemi nástroje rozhraní příkazového řádku můžou existovat společně na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="06f1a-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="06f1a-116">Určení, kterou verzi se používá na počítači, ve kterém je nainstalováno více verzí je vysvětleno podrobněji [ovladač](#driver) oddílu.</span><span class="sxs-lookup"><span data-stu-id="06f1a-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="06f1a-117">Příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="06f1a-117">CLI commands</span></span>

<span data-ttu-id="06f1a-118">Ve výchozím nastavení jsou nainstalované následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="06f1a-118">The following commands are installed by default:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="06f1a-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="06f1a-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="06f1a-120">**Základní příkazy**</span><span class="sxs-lookup"><span data-stu-id="06f1a-120">**Basic commands**</span></span>

* [<span data-ttu-id="06f1a-121">new</span><span class="sxs-lookup"><span data-stu-id="06f1a-121">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="06f1a-122">restore</span><span class="sxs-lookup"><span data-stu-id="06f1a-122">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="06f1a-123">Sestavení</span><span class="sxs-lookup"><span data-stu-id="06f1a-123">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="06f1a-124">Publikování</span><span class="sxs-lookup"><span data-stu-id="06f1a-124">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="06f1a-125">Spuštění</span><span class="sxs-lookup"><span data-stu-id="06f1a-125">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="06f1a-126">test</span><span class="sxs-lookup"><span data-stu-id="06f1a-126">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="06f1a-127">vstest</span><span class="sxs-lookup"><span data-stu-id="06f1a-127">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="06f1a-128">pack</span><span class="sxs-lookup"><span data-stu-id="06f1a-128">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="06f1a-129">Migrace</span><span class="sxs-lookup"><span data-stu-id="06f1a-129">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="06f1a-130">Vyčistit</span><span class="sxs-lookup"><span data-stu-id="06f1a-130">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="06f1a-131">sln</span><span class="sxs-lookup"><span data-stu-id="06f1a-131">sln</span></span>](dotnet-sln.md)
* [<span data-ttu-id="06f1a-132">Pomoc</span><span class="sxs-lookup"><span data-stu-id="06f1a-132">help</span></span>](dotnet-help.md)
* [<span data-ttu-id="06f1a-133">store</span><span class="sxs-lookup"><span data-stu-id="06f1a-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="06f1a-134">**Příkazy pro modifikaci projektů**</span><span class="sxs-lookup"><span data-stu-id="06f1a-134">**Project modification commands**</span></span>

* [<span data-ttu-id="06f1a-135">Přidání balíčku</span><span class="sxs-lookup"><span data-stu-id="06f1a-135">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="06f1a-136">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="06f1a-136">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="06f1a-137">Odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="06f1a-137">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="06f1a-138">Odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="06f1a-138">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="06f1a-139">odkaz na seznam</span><span class="sxs-lookup"><span data-stu-id="06f1a-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="06f1a-140">**Rozšířené příkazy**</span><span class="sxs-lookup"><span data-stu-id="06f1a-140">**Advanced commands**</span></span>

* [<span data-ttu-id="06f1a-141">odstranění nuget</span><span class="sxs-lookup"><span data-stu-id="06f1a-141">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="06f1a-142">nuget locals</span><span class="sxs-lookup"><span data-stu-id="06f1a-142">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="06f1a-143">nuget push</span><span class="sxs-lookup"><span data-stu-id="06f1a-143">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="06f1a-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="06f1a-144">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="06f1a-145">DotNet instalační skript</span><span class="sxs-lookup"><span data-stu-id="06f1a-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="06f1a-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="06f1a-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="06f1a-147">**Základní příkazy**</span><span class="sxs-lookup"><span data-stu-id="06f1a-147">**Basic commands**</span></span>

* [<span data-ttu-id="06f1a-148">new</span><span class="sxs-lookup"><span data-stu-id="06f1a-148">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="06f1a-149">restore</span><span class="sxs-lookup"><span data-stu-id="06f1a-149">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="06f1a-150">Sestavení</span><span class="sxs-lookup"><span data-stu-id="06f1a-150">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="06f1a-151">Publikování</span><span class="sxs-lookup"><span data-stu-id="06f1a-151">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="06f1a-152">Spuštění</span><span class="sxs-lookup"><span data-stu-id="06f1a-152">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="06f1a-153">test</span><span class="sxs-lookup"><span data-stu-id="06f1a-153">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="06f1a-154">vstest</span><span class="sxs-lookup"><span data-stu-id="06f1a-154">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="06f1a-155">pack</span><span class="sxs-lookup"><span data-stu-id="06f1a-155">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="06f1a-156">Migrace</span><span class="sxs-lookup"><span data-stu-id="06f1a-156">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="06f1a-157">Vyčistit</span><span class="sxs-lookup"><span data-stu-id="06f1a-157">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="06f1a-158">sln</span><span class="sxs-lookup"><span data-stu-id="06f1a-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="06f1a-159">**Příkazy pro modifikaci projektů**</span><span class="sxs-lookup"><span data-stu-id="06f1a-159">**Project modification commands**</span></span>

* [<span data-ttu-id="06f1a-160">Přidání balíčku</span><span class="sxs-lookup"><span data-stu-id="06f1a-160">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="06f1a-161">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="06f1a-161">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="06f1a-162">Odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="06f1a-162">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="06f1a-163">Odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="06f1a-163">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="06f1a-164">odkaz na seznam</span><span class="sxs-lookup"><span data-stu-id="06f1a-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="06f1a-165">**Rozšířené příkazy**</span><span class="sxs-lookup"><span data-stu-id="06f1a-165">**Advanced commands**</span></span>

* [<span data-ttu-id="06f1a-166">odstranění nuget</span><span class="sxs-lookup"><span data-stu-id="06f1a-166">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="06f1a-167">nuget locals</span><span class="sxs-lookup"><span data-stu-id="06f1a-167">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="06f1a-168">nuget push</span><span class="sxs-lookup"><span data-stu-id="06f1a-168">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="06f1a-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="06f1a-169">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="06f1a-170">DotNet instalační skript</span><span class="sxs-lookup"><span data-stu-id="06f1a-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="06f1a-171">Rozhraní příkazového řádku přijme model rozšiřitelnosti, pomocí kterých můžete zadat další nástroje pro vaše projekty.</span><span class="sxs-lookup"><span data-stu-id="06f1a-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="06f1a-172">Další informace najdete v tématu [model rozšíření rozhraní příkazového řádku .NET Core](extensibility.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="06f1a-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="06f1a-173">Příkaz struktura</span><span class="sxs-lookup"><span data-stu-id="06f1a-173">Command structure</span></span>

<span data-ttu-id="06f1a-174">Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu (nebo "akce")](#command-verb)a případně příkaz [argumenty](#arguments) a [možnosti](#options).</span><span class="sxs-lookup"><span data-stu-id="06f1a-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command (or "verb")](#command-verb), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="06f1a-175">Zobrazí tento model většinu operací rozhraní příkazového řádku, jako je vytváření nových konzolovou aplikaci a spuštění z příkazového řádku jako následující příkazy, zobrazit při spuštění z adresáře s názvem *my_app*:</span><span class="sxs-lookup"><span data-stu-id="06f1a-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="06f1a-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="06f1a-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="06f1a-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="06f1a-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="06f1a-178">Ovladač</span><span class="sxs-lookup"><span data-stu-id="06f1a-178">Driver</span></span>

<span data-ttu-id="06f1a-179">Ovladač jmenuje [dotnet](dotnet.md) a má dvě odpovědnosti, buď spuštěný [aplikace závisí na architektuře](../deploying/index.md) nebo spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="06f1a-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="06f1a-180">Spuštění aplikace závisí na architektuře, zadejte aplikace, po ovladače, například `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="06f1a-180">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="06f1a-181">Při provádění příkazu ze složky, ve které se nachází aplikaci knihovny DLL, stačí provést `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="06f1a-181">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="06f1a-182">Pokud chcete použít konkrétní verzi modulu .NET Core Runtime, použijte `--fx-version <VERSION>` možnost (najdete v článku [příkaz dotnet](dotnet.md) odkaz).</span><span class="sxs-lookup"><span data-stu-id="06f1a-182">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="06f1a-183">Když zadáte příkaz k ovladači, `dotnet.exe` zahájí proces spuštění příkazu rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="06f1a-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="06f1a-184">Příklad:</span><span class="sxs-lookup"><span data-stu-id="06f1a-184">For example:</span></span>

```bash
> dotnet build
```

<span data-ttu-id="06f1a-185">Nejprve ovladač Určuje verzi sady SDK používat.</span><span class="sxs-lookup"><span data-stu-id="06f1a-185">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="06f1a-186">Pokud není žádný ["global.json"](global-json.md), se používá nejnovější verzi sady SDK k dispozici.</span><span class="sxs-lookup"><span data-stu-id="06f1a-186">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="06f1a-187">To může být buď ve verzi preview nebo stabilní verze, v závislosti na tom, co je to nejnovější na počítači.</span><span class="sxs-lookup"><span data-stu-id="06f1a-187">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="06f1a-188">Jakmile se určí verzi sady SDK, vykoná příkaz.</span><span class="sxs-lookup"><span data-stu-id="06f1a-188">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command-verb"></a><span data-ttu-id="06f1a-189">Příkaz ("operace")</span><span class="sxs-lookup"><span data-stu-id="06f1a-189">Command ("verb")</span></span>

<span data-ttu-id="06f1a-190">Příkaz (nebo "akce") je jednoduše příkaz, který provede akci.</span><span class="sxs-lookup"><span data-stu-id="06f1a-190">The command (or "verb") is simply a command that performs an action.</span></span> <span data-ttu-id="06f1a-191">Například `dotnet build` sestaví váš kód.</span><span class="sxs-lookup"><span data-stu-id="06f1a-191">For example, `dotnet build` builds your code.</span></span> <span data-ttu-id="06f1a-192">`dotnet publish` publikuje váš kód.</span><span class="sxs-lookup"><span data-stu-id="06f1a-192">`dotnet publish` publishes your code.</span></span> <span data-ttu-id="06f1a-193">Příkazy jsou implementovány jako konzolovou aplikaci pomocí `dotnet {verb}` konvence.</span><span class="sxs-lookup"><span data-stu-id="06f1a-193">The commands are implemented as a console application using a `dotnet {verb}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="06f1a-194">Arguments</span><span class="sxs-lookup"><span data-stu-id="06f1a-194">Arguments</span></span>

<span data-ttu-id="06f1a-195">Argumenty, které můžete předat do příkazového řádku jsou argumenty k vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="06f1a-195">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="06f1a-196">Například při spuštění `dotnet publish my_app.csproj`, `my_app.csproj` argument určuje projekt k publikování a je předán `publish` příkazu.</span><span class="sxs-lookup"><span data-stu-id="06f1a-196">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="06f1a-197">Možnosti</span><span class="sxs-lookup"><span data-stu-id="06f1a-197">Options</span></span>

<span data-ttu-id="06f1a-198">Možnosti, které můžete předat do příkazového řádku jsou možnosti k vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="06f1a-198">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="06f1a-199">Například při spuštění `dotnet publish --output /build_output`, `--output` možnost a jeho hodnota jsou předány `publish` příkazu.</span><span class="sxs-lookup"><span data-stu-id="06f1a-199">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="06f1a-200">Migrace z project.json</span><span class="sxs-lookup"><span data-stu-id="06f1a-200">Migration from project.json</span></span>

<span data-ttu-id="06f1a-201">Pokud jste použili ve verzi Preview 2 nástroje k vytvoření *project.json*-podle projektů, naleznete [dotnet migrate](dotnet-migrate.md) informace o migraci vašeho projektu nástroje MSBuild /*.csproj*pomocí verze nástroje.</span><span class="sxs-lookup"><span data-stu-id="06f1a-201">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="06f1a-202">Pro .NET Core projekty vytvořené před verzí nástroje ve verzi Preview 2, buď ručně aktualizovat projekt následující pokyny v [migrace z DNX na .NET Core CLI (project.json)](../migration/from-dnx.md) a pak použijte `dotnet migrate` nebo přímo upgradovat. vaše projekty.</span><span class="sxs-lookup"><span data-stu-id="06f1a-202">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="06f1a-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06f1a-203">See also</span></span>

- [<span data-ttu-id="06f1a-204">DotNet/CLI úložiště GitHub</span><span class="sxs-lookup"><span data-stu-id="06f1a-204">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="06f1a-205">Průvodce instalací rozhraní .NET core</span><span class="sxs-lookup"><span data-stu-id="06f1a-205">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
