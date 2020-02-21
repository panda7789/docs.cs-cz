---
title: .NET Core CLI
titleSuffix: ''
description: Přehled .NET Core CLI a jeho funkcí.
ms.date: 02/13/2020
ms.openlocfilehash: 1078d68ddc088274fa14b0094a81765f7af69dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543311"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="da036-103">Přehled .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="da036-103">.NET Core CLI overview</span></span>

<span data-ttu-id="da036-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="da036-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="da036-105">Rozhraní příkazového řádku .NET Core (CLI) je sada nástrojů pro různé platformy pro vývoj, sestavování, spouštění a publikování aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="da036-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="da036-106">.NET Core CLI je součástí [.NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="da036-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="da036-107">Informace o tom, jak nainstalovat .NET Core SDK, najdete v tématu [instalace .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="da036-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="da036-108">Příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="da036-108">CLI commands</span></span>

<span data-ttu-id="da036-109">Ve výchozím nastavení jsou nainstalovány následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="da036-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="da036-110">Základní příkazy</span><span class="sxs-lookup"><span data-stu-id="da036-110">Basic commands</span></span>

- [<span data-ttu-id="da036-111">new</span><span class="sxs-lookup"><span data-stu-id="da036-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="da036-112">restore</span><span class="sxs-lookup"><span data-stu-id="da036-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="da036-113">budování</span><span class="sxs-lookup"><span data-stu-id="da036-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="da036-114">publikování</span><span class="sxs-lookup"><span data-stu-id="da036-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="da036-115">spouštěl</span><span class="sxs-lookup"><span data-stu-id="da036-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="da036-116">napaden</span><span class="sxs-lookup"><span data-stu-id="da036-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="da036-117">VSTest</span><span class="sxs-lookup"><span data-stu-id="da036-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="da036-118">pack</span><span class="sxs-lookup"><span data-stu-id="da036-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="da036-119">migraci</span><span class="sxs-lookup"><span data-stu-id="da036-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="da036-120">Odstranit</span><span class="sxs-lookup"><span data-stu-id="da036-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="da036-121">SLN</span><span class="sxs-lookup"><span data-stu-id="da036-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="da036-122">Pomoc</span><span class="sxs-lookup"><span data-stu-id="da036-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="da036-123">uchovávat</span><span class="sxs-lookup"><span data-stu-id="da036-123">store</span></span>](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="da036-124">Příkazy pro modifikaci projektů</span><span class="sxs-lookup"><span data-stu-id="da036-124">Project modification commands</span></span>

- [<span data-ttu-id="da036-125">Přidat balíček</span><span class="sxs-lookup"><span data-stu-id="da036-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="da036-126">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="da036-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="da036-127">odebrat balíček</span><span class="sxs-lookup"><span data-stu-id="da036-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="da036-128">odebrat odkaz</span><span class="sxs-lookup"><span data-stu-id="da036-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="da036-129">odkaz na seznam</span><span class="sxs-lookup"><span data-stu-id="da036-129">list reference</span></span>](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="da036-130">Rozšířené příkazy</span><span class="sxs-lookup"><span data-stu-id="da036-130">Advanced commands</span></span>

- [<span data-ttu-id="da036-131">odstranění NuGet</span><span class="sxs-lookup"><span data-stu-id="da036-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="da036-132">národní prostředí NuGet</span><span class="sxs-lookup"><span data-stu-id="da036-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="da036-133">nabízení NuGet</span><span class="sxs-lookup"><span data-stu-id="da036-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="da036-134">nástroji</span><span class="sxs-lookup"><span data-stu-id="da036-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="da036-135">instalace skriptu dotnet</span><span class="sxs-lookup"><span data-stu-id="da036-135">dotnet install script</span></span>](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="da036-136">Příkazy správy nástrojů</span><span class="sxs-lookup"><span data-stu-id="da036-136">Tool management commands</span></span>

- [<span data-ttu-id="da036-137">Instalace nástroje</span><span class="sxs-lookup"><span data-stu-id="da036-137">tool install</span></span>](dotnet-tool-install.md)
- [<span data-ttu-id="da036-138">seznam nástrojů</span><span class="sxs-lookup"><span data-stu-id="da036-138">tool list</span></span>](dotnet-tool-list.md)
- [<span data-ttu-id="da036-139">Aktualizace nástroje</span><span class="sxs-lookup"><span data-stu-id="da036-139">tool update</span></span>](dotnet-tool-update.md)
- <span data-ttu-id="da036-140">[obnovení nástroje](global-tools.md#install-a-local-tool) **dostupné od .NET Core SDK 3,0**</span><span class="sxs-lookup"><span data-stu-id="da036-140">[tool restore](global-tools.md#install-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- <span data-ttu-id="da036-141">[spuštění nástroje](global-tools.md#invoke-a-local-tool) je **dostupné od .NET Core SDK 3,0**</span><span class="sxs-lookup"><span data-stu-id="da036-141">[tool run](global-tools.md#invoke-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- [<span data-ttu-id="da036-142">Odinstalace nástroje</span><span class="sxs-lookup"><span data-stu-id="da036-142">tool uninstall</span></span>](dotnet-tool-uninstall.md)

<span data-ttu-id="da036-143">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="da036-143">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="da036-144">Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="da036-144">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="da036-145">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="da036-145">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="da036-146">Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="da036-146">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="da036-147">Struktura příkazu</span><span class="sxs-lookup"><span data-stu-id="da036-147">Command structure</span></span>

<span data-ttu-id="da036-148">Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a možných [argumentů](#arguments) příkazů a [možností](#options).</span><span class="sxs-lookup"><span data-stu-id="da036-148">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="da036-149">Tento model se zobrazí ve většině operací CLI, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, protože následující příkazy se zobrazí při spuštění z adresáře s názvem *my_app*:</span><span class="sxs-lookup"><span data-stu-id="da036-149">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="da036-150">Ovladač</span><span class="sxs-lookup"><span data-stu-id="da036-150">Driver</span></span>

<span data-ttu-id="da036-151">Ovladač má název [dotnet](dotnet.md) a má dvě zodpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) , nebo spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="da036-151">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="da036-152">Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="da036-152">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="da036-153">Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="da036-153">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="da036-154">Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte možnost `--fx-version <VERSION>` (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="da036-154">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="da036-155">Když zadáte příkaz do ovladače, `dotnet.exe` spustí proces spuštění příkazu CLI.</span><span class="sxs-lookup"><span data-stu-id="da036-155">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="da036-156">Příklad:</span><span class="sxs-lookup"><span data-stu-id="da036-156">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="da036-157">Nejdřív ovladač určuje verzi sady SDK, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="da036-157">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="da036-158">Pokud není k dispozici [možnost Global. JSON](global-json.md), použije se nejnovější verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="da036-158">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="da036-159">To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.</span><span class="sxs-lookup"><span data-stu-id="da036-159">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="da036-160">Po určení verze sady SDK se spustí příkaz.</span><span class="sxs-lookup"><span data-stu-id="da036-160">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="da036-161">Příkaz</span><span class="sxs-lookup"><span data-stu-id="da036-161">Command</span></span>

<span data-ttu-id="da036-162">Příkaz provede akci.</span><span class="sxs-lookup"><span data-stu-id="da036-162">The command performs an action.</span></span> <span data-ttu-id="da036-163">Například `dotnet build` sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="da036-163">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="da036-164">`dotnet publish` publikuje kód.</span><span class="sxs-lookup"><span data-stu-id="da036-164">`dotnet publish` publishes code.</span></span> <span data-ttu-id="da036-165">Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.</span><span class="sxs-lookup"><span data-stu-id="da036-165">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="da036-166">Argumenty</span><span class="sxs-lookup"><span data-stu-id="da036-166">Arguments</span></span>

<span data-ttu-id="da036-167">Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali.</span><span class="sxs-lookup"><span data-stu-id="da036-167">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="da036-168">Například při spuštění `dotnet publish my_app.csproj`argument `my_app.csproj` označuje projekt k publikování a je předán do příkazu `publish`.</span><span class="sxs-lookup"><span data-stu-id="da036-168">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="da036-169">Možnosti</span><span class="sxs-lookup"><span data-stu-id="da036-169">Options</span></span>

<span data-ttu-id="da036-170">Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="da036-170">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="da036-171">Například když spustíte `dotnet publish --output /build_output`, možnost `--output` a její hodnota se předají do příkazu `publish`.</span><span class="sxs-lookup"><span data-stu-id="da036-171">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="da036-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da036-172">See also</span></span>

- [<span data-ttu-id="da036-173">dotnet/úložiště GitHub SDK</span><span class="sxs-lookup"><span data-stu-id="da036-173">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="da036-174">Průvodce instalací .NET Core</span><span class="sxs-lookup"><span data-stu-id="da036-174">.NET Core installation guide</span></span>](../install/sdk.md)
