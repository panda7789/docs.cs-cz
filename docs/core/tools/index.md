---
title: .NET Core CLI
titleSuffix: ''
description: Přehled .NET Core CLI a jeho funkcí.
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 18dde384058206f437b53572b2f8331d65324482
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062688"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="a9ade-103">Přehled rozhraní .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a9ade-103">.NET Core CLI overview</span></span>

<span data-ttu-id="a9ade-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="a9ade-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="a9ade-105">Rozhraní příkazového řádku .NET Core (CLI) je sada nástrojů pro různé platformy pro vývoj, sestavování, spouštění a publikování aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9ade-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="a9ade-106">.NET Core CLI je součástí [.NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a9ade-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="a9ade-107">Informace o tom, jak nainstalovat .NET Core SDK, najdete v tématu [instalace .NET Core](../install/windows.md).</span><span class="sxs-lookup"><span data-stu-id="a9ade-107">To learn how to install the .NET Core SDK, see [Install .NET Core](../install/windows.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="a9ade-108">Příkazy rozhraní CLI</span><span class="sxs-lookup"><span data-stu-id="a9ade-108">CLI commands</span></span>

<span data-ttu-id="a9ade-109">Ve výchozím nastavení jsou nainstalovány následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="a9ade-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="a9ade-110">Základní příkazy</span><span class="sxs-lookup"><span data-stu-id="a9ade-110">Basic commands</span></span>

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

### <a name="project-modification-commands"></a><span data-ttu-id="a9ade-111">Příkazy pro modifikaci projektů</span><span class="sxs-lookup"><span data-stu-id="a9ade-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="a9ade-112">Rozšířené příkazy</span><span class="sxs-lookup"><span data-stu-id="a9ade-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="a9ade-113">Příkazy správy nástrojů</span><span class="sxs-lookup"><span data-stu-id="a9ade-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="a9ade-114">[`tool restore`](global-tools.md#install-a-local-tool)K dispozici od .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="a9ade-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="a9ade-115">[`tool run`](global-tools.md#invoke-a-local-tool)K dispozici od .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="a9ade-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="a9ade-116">Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a9ade-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="a9ade-117">Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="a9ade-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="a9ade-118">Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="a9ade-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="a9ade-119">Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a9ade-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="a9ade-120">Struktura příkazu</span><span class="sxs-lookup"><span data-stu-id="a9ade-120">Command structure</span></span>

<span data-ttu-id="a9ade-121">Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a možných [argumentů](#arguments) příkazů a [možností](#options).</span><span class="sxs-lookup"><span data-stu-id="a9ade-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="a9ade-122">Tento model se zobrazí ve většině operací CLI, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, protože následující příkazy se zobrazí při spuštění z adresáře s názvem *my_app*:</span><span class="sxs-lookup"><span data-stu-id="a9ade-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="a9ade-123">Ovladač</span><span class="sxs-lookup"><span data-stu-id="a9ade-123">Driver</span></span>

<span data-ttu-id="a9ade-124">Ovladač má název [dotnet](dotnet.md) a má dvě zodpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) , nebo spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="a9ade-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="a9ade-125">Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll` .</span><span class="sxs-lookup"><span data-stu-id="a9ade-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="a9ade-126">Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll` .</span><span class="sxs-lookup"><span data-stu-id="a9ade-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="a9ade-127">Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte `--fx-version <VERSION>` možnost (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="a9ade-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="a9ade-128">Když zadáte příkaz do ovladače, `dotnet.exe` spustí se proces spuštění příkazu CLI.</span><span class="sxs-lookup"><span data-stu-id="a9ade-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="a9ade-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a9ade-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="a9ade-130">Nejdřív ovladač určuje verzi sady SDK, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="a9ade-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="a9ade-131">Pokud k souboru není [global.js](global-json.md) , použije se nejnovější verze sady SDK, která je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a9ade-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="a9ade-132">To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.</span><span class="sxs-lookup"><span data-stu-id="a9ade-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="a9ade-133">Po určení verze sady SDK se spustí příkaz.</span><span class="sxs-lookup"><span data-stu-id="a9ade-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="a9ade-134">Příkaz</span><span class="sxs-lookup"><span data-stu-id="a9ade-134">Command</span></span>

<span data-ttu-id="a9ade-135">Příkaz provede akci.</span><span class="sxs-lookup"><span data-stu-id="a9ade-135">The command performs an action.</span></span> <span data-ttu-id="a9ade-136">Například `dotnet build` sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="a9ade-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="a9ade-137">`dotnet publish`publikuje kód.</span><span class="sxs-lookup"><span data-stu-id="a9ade-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="a9ade-138">Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.</span><span class="sxs-lookup"><span data-stu-id="a9ade-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="a9ade-139">Arguments</span><span class="sxs-lookup"><span data-stu-id="a9ade-139">Arguments</span></span>

<span data-ttu-id="a9ade-140">Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali.</span><span class="sxs-lookup"><span data-stu-id="a9ade-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="a9ade-141">Například když spustíte `dotnet publish my_app.csproj` , `my_app.csproj` argument označuje projekt k publikování a je předán do `publish` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a9ade-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="a9ade-142">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a9ade-142">Options</span></span>

<span data-ttu-id="a9ade-143">Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="a9ade-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="a9ade-144">Například když spustíte `dotnet publish --output /build_output` , `--output` možnost a její hodnota jsou předány do `publish` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a9ade-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9ade-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9ade-145">See also</span></span>

- [<span data-ttu-id="a9ade-146">dotnet/úložiště GitHub SDK</span><span class="sxs-lookup"><span data-stu-id="a9ade-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="a9ade-147">Průvodce instalací .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9ade-147">.NET Core installation guide</span></span>](../install/windows.md)
