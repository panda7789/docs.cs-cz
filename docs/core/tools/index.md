---
title: Rozhraní příkazového řádku .NET Core
titleSuffix: ''
description: Přehled rozhraní .NET Core CLI a jeho funkcí.
ms.date: 02/13/2020
ms.openlocfilehash: 45a40063f70a621e807abf5e01ceecb125aecd7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399117"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="33255-103">Přehled rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="33255-103">.NET Core CLI overview</span></span>

<span data-ttu-id="33255-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="33255-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="33255-105">Rozhraní příkazového řádku .NET Core (CLI) je nástroj pro různé platformy pro vývoj, vytváření, spouštění a publikování aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="33255-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="33255-106">Rozhraní .NET Core CLI je součástí sady [.NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="33255-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="33255-107">Informace o instalaci sady .NET Core SDK naleznete [v tématu Instalace sady .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="33255-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="33255-108">Příkazy příkazového příkazu</span><span class="sxs-lookup"><span data-stu-id="33255-108">CLI commands</span></span>

<span data-ttu-id="33255-109">Ve výchozím nastavení jsou nainstalovány následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="33255-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="33255-110">Základní příkazy</span><span class="sxs-lookup"><span data-stu-id="33255-110">Basic commands</span></span>

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="33255-111">Příkazy pro modifikaci projektů</span><span class="sxs-lookup"><span data-stu-id="33255-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="33255-112">Rozšířené příkazy</span><span class="sxs-lookup"><span data-stu-id="33255-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="33255-113">Příkazy pro správu nástrojů</span><span class="sxs-lookup"><span data-stu-id="33255-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="33255-114">[`tool restore`](global-tools.md#install-a-local-tool)K dispozici od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="33255-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="33255-115">[`tool run`](global-tools.md#invoke-a-local-tool)K dispozici od .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="33255-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="33255-116">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="33255-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="33255-117">Můžete psát nástroje sami nebo instalovat nástroje napsané třetími stranami.</span><span class="sxs-lookup"><span data-stu-id="33255-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="33255-118">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="33255-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="33255-119">Další informace naleznete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="33255-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="33255-120">Struktura příkazů</span><span class="sxs-lookup"><span data-stu-id="33255-120">Command structure</span></span>

<span data-ttu-id="33255-121">Struktura příkazu příkazu příkazu se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a případně [argumentů](#arguments) a [možností](#options)příkazu .</span><span class="sxs-lookup"><span data-stu-id="33255-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="33255-122">Tento vzor se zobrazí ve většině operací rozhraní příkazového řádku, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, jak se následující příkazy zobrazují při spuštění z adresáře s názvem *my_app*:</span><span class="sxs-lookup"><span data-stu-id="33255-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="33255-123">Ovladač</span><span class="sxs-lookup"><span data-stu-id="33255-123">Driver</span></span>

<span data-ttu-id="33255-124">Ovladač má název [dotnet](dotnet.md) a má dvě odpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) nebo provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="33255-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="33255-125">Chcete-li spustit aplikaci závislou na rámci, zadejte aplikaci za ovladačem, `dotnet /path/to/my_app.dll`například .</span><span class="sxs-lookup"><span data-stu-id="33255-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="33255-126">Při provádění příkazu ze složky, kde se nachází dll aplikace, jednoduše spustit `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="33255-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="33255-127">Pokud chcete použít určitou verzi rozhraní .NET Core `--fx-version <VERSION>` Runtime, použijte tuto možnost (viz odkaz na [příkaz dotnet).](dotnet.md)</span><span class="sxs-lookup"><span data-stu-id="33255-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="33255-128">Když zadáte příkaz k ovladači, `dotnet.exe` spustí proces spuštění příkazu příkazu.</span><span class="sxs-lookup"><span data-stu-id="33255-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="33255-129">Například:</span><span class="sxs-lookup"><span data-stu-id="33255-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="33255-130">Nejprve ovladač určuje verzi sady SDK, která má být používána.</span><span class="sxs-lookup"><span data-stu-id="33255-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="33255-131">Pokud neexistuje žádný soubor [global.json,](global-json.md) použije se nejnovější verze sady SDK, která je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="33255-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="33255-132">To může být buď náhled nebo stabilní verze, v závislosti na tom, co je nejnovější v počítači.</span><span class="sxs-lookup"><span data-stu-id="33255-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="33255-133">Jakmile je určena verze sady SDK, provede příkaz.</span><span class="sxs-lookup"><span data-stu-id="33255-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="33255-134">Příkaz</span><span class="sxs-lookup"><span data-stu-id="33255-134">Command</span></span>

<span data-ttu-id="33255-135">Příkaz provede akci.</span><span class="sxs-lookup"><span data-stu-id="33255-135">The command performs an action.</span></span> <span data-ttu-id="33255-136">Například `dotnet build` vytvoří kód.</span><span class="sxs-lookup"><span data-stu-id="33255-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="33255-137">`dotnet publish`zveřejňuje kód.</span><span class="sxs-lookup"><span data-stu-id="33255-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="33255-138">Příkazy jsou implementovány jako konzolové aplikace pomocí konvence. `dotnet {command}`</span><span class="sxs-lookup"><span data-stu-id="33255-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="33255-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="33255-139">Arguments</span></span>

<span data-ttu-id="33255-140">Argumenty, které předáte na příkazovém řádku, jsou argumenty do volaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="33255-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="33255-141">Například při `dotnet publish my_app.csproj`spuštění `my_app.csproj` argument označuje projekt publikovat a je `publish` předán příkazu.</span><span class="sxs-lookup"><span data-stu-id="33255-141">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="33255-142">Možnosti</span><span class="sxs-lookup"><span data-stu-id="33255-142">Options</span></span>

<span data-ttu-id="33255-143">Možnosti, které předáte na příkazovém řádku, jsou možnosti vyvolaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="33255-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="33255-144">Například při `dotnet publish --output /build_output`spuštění `--output` , možnost a jeho `publish` hodnota jsou předány příkazu.</span><span class="sxs-lookup"><span data-stu-id="33255-144">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="33255-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="33255-145">See also</span></span>

- [<span data-ttu-id="33255-146">úložiště GitHub dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="33255-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="33255-147">Instalační příručka jádra rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="33255-147">.NET Core installation guide</span></span>](../install/sdk.md)
