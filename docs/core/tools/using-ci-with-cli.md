---
title: "Pomocí rozhraní .NET Core SDK a nástrojů v nepřetržité integrace (CI)"
description: "Informace o použití rozhraní .NET Core SDK a její nástroje na buildovacím serveru."
keywords: "Rozhraní .NET, .NET core, průběžnou integraci, ci, sestavení, automatizace, Travis CI, AppVeyor, Visual Studio Team Services, služby vsts"
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
ms.workload: dotnetcore
ms.openlocfilehash: cc2defb72c61e45ecfebd26937f1c3fd2d405171
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="466ce-104">Pomocí rozhraní .NET Core SDK a nástrojů v nepřetržité integrace (CI)</span><span class="sxs-lookup"><span data-stu-id="466ce-104">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

## <a name="overview"></a><span data-ttu-id="466ce-105">Přehled</span><span class="sxs-lookup"><span data-stu-id="466ce-105">Overview</span></span>

<span data-ttu-id="466ce-106">Tento dokument popisuje pomocí jeho nástroje a rozhraní .NET Core SDK na sestavení serveru.</span><span class="sxs-lookup"><span data-stu-id="466ce-106">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="466ce-107">.NET Core nástrojů funguje jak interaktivně, kde vývojář typy příkazů do příkazového řádku a automaticky, kde nepřetržité integrace konfigurace serveru spouští skript sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-107">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="466ce-108">Příkazy, možnosti, vstupy a výstupy jsou stejné, a pouze věcí, které zadáte představují způsob, jak získat nástroje a systém k sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="466ce-108">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="466ce-109">Tento dokument se zaměřuje na scénáře pořízení nástroj pro nepřetržitou Integraci s doporučeními pro návrh a struktury skripty sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-109">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="466ce-110">Možnosti instalace pro nepřetržitou Integraci sestavení servery</span><span class="sxs-lookup"><span data-stu-id="466ce-110">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="466ce-111">Pomocí nativní instalační programy</span><span class="sxs-lookup"><span data-stu-id="466ce-111">Using the native installers</span></span>

<span data-ttu-id="466ce-112">Nativní instalační programy jsou k dispozici pro systému macOS, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="466ce-112">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="466ce-113">Instalační programy vyžadují správce (sudo) přístup k serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-113">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="466ce-114">Výhodou použití nativní instalační program je nainstaluje všechny nativní závislosti potřebné pro nástrojů ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="466ce-114">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="466ce-115">Nativní instalační programy také poskytují systémové instalace sady SDK.</span><span class="sxs-lookup"><span data-stu-id="466ce-115">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="466ce-116">Uživatelé systému macOS by měl používat PKG instalační programy.</span><span class="sxs-lookup"><span data-stu-id="466ce-116">macOS users should use the PKG installers.</span></span> <span data-ttu-id="466ce-117">V systému Linux je volba pomocí Správce balíčků na základě informačního kanálu, jako například výstižný get pro Ubuntu nebo yum pro CentOS, nebo pomocí balíčků, sami bázi DEB nebo ot. / min.</span><span class="sxs-lookup"><span data-stu-id="466ce-117">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="466ce-118">V systému Windows použijte instalační služby MSI.</span><span class="sxs-lookup"><span data-stu-id="466ce-118">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="466ce-119">Nejnovější stabilní binární soubory se nacházejí v [Začínáme s .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="466ce-119">The latest stable binaries are found at [Get Started with .NET Core](https://aka.ms/dotnetcoregs).</span></span> <span data-ttu-id="466ce-120">Pokud chcete použít předběžné verze nástroje nejnovější (a potenciálně nestabilním), pomocí odkazů uvedených v [úložiště GitHub dotnet nebo rozhraní příkazového řádku](https://github.com/dotnet/cli#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="466ce-120">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/cli GitHub repository](https://github.com/dotnet/cli#installers-and-binaries).</span></span> <span data-ttu-id="466ce-121">Pro Linux distribuce `tar.gz` archivy (také označované jako `tarballs`) jsou k dispozici, pomocí skriptů instalace v rámci archivu pro instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="466ce-121">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="466ce-122">Pomocí skriptu Instalační program</span><span class="sxs-lookup"><span data-stu-id="466ce-122">Using the installer script</span></span>

<span data-ttu-id="466ce-123">Pomocí skriptu Instalační program umožňuje instalaci bez oprávnění správce na serveru sestavení a snadno automatizace pro získání nástrojů.</span><span class="sxs-lookup"><span data-stu-id="466ce-123">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="466ce-124">Tento skript má na starosti stahování nástroje a extrahování do výchozí hodnotu nebo zadané umístění pro použití.</span><span class="sxs-lookup"><span data-stu-id="466ce-124">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="466ce-125">Můžete také zadat verzi nástrojů, který chcete nainstalovat a jestli chcete nainstalovat celý SDK nebo pouze sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="466ce-125">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="466ce-126">Skript instalačního programu je automatizované ke spuštění na začátku sestavení pro načtení a nainstalujte požadovanou verzi sady SDK.</span><span class="sxs-lookup"><span data-stu-id="466ce-126">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="466ce-127">*Požadovanou verzi* libovolnou verzi sady SDK vyžadovat projekty k sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-127">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="466ce-128">Skript můžete nainstalovat sadu SDK do místního adresáře na serveru, spusťte nástroje z umístění instalace a pak vyčistit (nebo nechat službu CI vyčištění) po sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-128">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="466ce-129">To poskytuje zapouzdření a izolaci celého procesu vytváření.</span><span class="sxs-lookup"><span data-stu-id="466ce-129">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="466ce-130">Odkaz na instalační skript se nachází v [dotnet instalace](dotnet-install-script.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="466ce-130">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="466ce-131">Pokud používáte skript instalačního programu, nativní závislosti se neinstalují automaticky.</span><span class="sxs-lookup"><span data-stu-id="466ce-131">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="466ce-132">Pokud je operační systém nemá, je nutné nainstalovat nativní závislosti.</span><span class="sxs-lookup"><span data-stu-id="466ce-132">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="466ce-133">Najdete v seznamu požadavky [.NET Core nativní požadavky](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="466ce-133">See the list of prerequisites in the [.NET Core native prerequisites](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) topic.</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="466ce-134">Instalační program Příklady položek konfigurace</span><span class="sxs-lookup"><span data-stu-id="466ce-134">CI setup examples</span></span>

<span data-ttu-id="466ce-135">Tato část popisuje ruční instalaci pomocí skriptu prostředí PowerShell nebo bash, společně s popis několik softwaru jako řešení položek konfigurace služba (SaaS).</span><span class="sxs-lookup"><span data-stu-id="466ce-135">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="466ce-136">Řešení SaaS CI popsaná jsou [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [Visual Studio Team Services Build](https://www.visualstudio.com/docs/build/overview).</span><span class="sxs-lookup"><span data-stu-id="466ce-136">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Visual Studio Team Services Build](https://www.visualstudio.com/docs/build/overview).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="466ce-137">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="466ce-137">Manual setup</span></span>

<span data-ttu-id="466ce-138">Každá služba SaaS má svou vlastní metody pro vytváření a konfigurace procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-138">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="466ce-139">Pokud používáte jiné řešení SaaS než uvedených nebo vyžadují přizpůsobení kromě předem zabalené podpory, musíte provést minimálně část konfigurace ručně.</span><span class="sxs-lookup"><span data-stu-id="466ce-139">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="466ce-140">Obecně platí ruční instalaci, musíte získat verzi nástroje (nebo noční sestavení nástroje) a spusťte skript buildu.</span><span class="sxs-lookup"><span data-stu-id="466ce-140">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="466ce-141">Můžete použít prostředí PowerShell nebo bash skript k orchestraci příkazy .NET Core nebo použít soubor projektu, který popisuje proces vytváření.</span><span class="sxs-lookup"><span data-stu-id="466ce-141">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="466ce-142">[Orchestration části](#orchestrating-the-build) poskytující víc podrobností o těchto možnostech.</span><span class="sxs-lookup"><span data-stu-id="466ce-142">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="466ce-143">Jakmile vytvoříte skript, který provede ruční vytvoření položek konfigurace nastavení serveru, používejte ji na vývojářském počítači k vytvoření kódu místně pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="466ce-143">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="466ce-144">Jakmile potvrdíte, že skript běží i místně, nasaďte ho na vašem serveru sestavení položek konfigurace.</span><span class="sxs-lookup"><span data-stu-id="466ce-144">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="466ce-145">Relativně jednoduché skript prostředí PowerShell ukazuje, jak získat .NET Core SDK a nainstalujte ji na server Windows sestavení:</span><span class="sxs-lookup"><span data-stu-id="466ce-145">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the 
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the 
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it 
#   does, it's removed. This is not strictly required, but it's a 
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the 
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the 
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the 
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="466ce-146">Poskytnete implementace pro proces sestavení na konci tohoto skriptu.</span><span class="sxs-lookup"><span data-stu-id="466ce-146">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="466ce-147">Skript získá nástroje a potom provede vašeho procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-147">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="466ce-148">Následující skript bash pro počítače, UNIX, provede akce popsané v skriptu prostředí PowerShell podobným způsobem:</span><span class="sxs-lookup"><span data-stu-id="466ce-148">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="466ce-149">Travis CI</span><span class="sxs-lookup"><span data-stu-id="466ce-149">Travis CI</span></span>

<span data-ttu-id="466ce-150">Můžete nakonfigurovat [Travis CI](https://travis-ci.org/) a nainstalovat .NET Core SDK `csharp` jazyk a `dotnet` klíč.</span><span class="sxs-lookup"><span data-stu-id="466ce-150">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="466ce-151">O najdete v oficiální dokumentaci Travis CI [vytváření C#, F # nebo Visual Basic projektu](https://docs.travis-ci.com/user/languages/csharp/) Další informace.</span><span class="sxs-lookup"><span data-stu-id="466ce-151">See the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) for more information.</span></span> <span data-ttu-id="466ce-152">Všimněte si, jak je přístup k informacím Travis CI který udržuje komunitní `language: csharp` identifikátor jazyka funguje pro všechny jazyky rozhraní .NET, včetně F # a Mono.</span><span class="sxs-lookup"><span data-stu-id="466ce-152">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="466ce-153">Travis CI běží obou systému macOS (OS X 10.11, OS X 10.12) a Linux (Ubuntu 14.04) úlohy v *sestavení matice*, kde můžete určit kombinaci modul runtime, prostředí a vyloučení nebo zahrnutí tak, aby pokrývalo vaší kombinace sestavení pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="466ce-153">Travis CI runs both macOS (OS X 10.11, OS X 10.12) and Linux (Ubuntu 14.04) jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="466ce-154">Najdete v článku [. Příklad travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) souboru a [přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) v Travis CI dokumentace pro další informace.</span><span class="sxs-lookup"><span data-stu-id="466ce-154">See the [.travis.yml example](https://github.com/dotnet/docs/blob/master/.travis.yml) file and [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) in the Travis CI docs for more information.</span></span> <span data-ttu-id="466ce-155">Nástroje využívající MSBuild zahrnout LTS (1.0.x) a aktuální moduly runtime (1.1.x) do balíčku. takže instalací sady SDK, se zobrazí všechny objekty, které potřebujete k vytváření.</span><span class="sxs-lookup"><span data-stu-id="466ce-155">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="466ce-156">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="466ce-156">AppVeyor</span></span>

<span data-ttu-id="466ce-157">[AppVeyor](https://www.appveyor.com/) nainstaluje .NET Core 1.0.1 SDK `Visual Studio 2017` sestavení pracovní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="466ce-157">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="466ce-158">Ostatní sestavení Image s různými verzemi nástroje .NET Core SDK jsou k dispozici. najdete v článku [appveyor.yml příklad](https://github.com/dotnet/docs/blob/master/appveyor.yml) a [vytvářet bitové kopie pracovní](https://www.appveyor.com/docs/build-environment/#build-worker-images) téma v AppVeyor dokumentace pro další informace.</span><span class="sxs-lookup"><span data-stu-id="466ce-158">Other build images with different versions of the .NET Core SDK are available; see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) topic in the AppVeyor docs for more information.</span></span>

<span data-ttu-id="466ce-159">.NET Core SDK binární soubory jsou stažené a rozbalené v podadresáři pomocí skriptu install a pak se přidá do `PATH` proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="466ce-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="466ce-160">Přidáte matici sestavení testy integrace s více verzemi .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="466ce-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a><span data-ttu-id="466ce-161">Visual Studio Team Services (služby VSTS)</span><span class="sxs-lookup"><span data-stu-id="466ce-161">Visual Studio Team Services (VSTS)</span></span>

<span data-ttu-id="466ce-162">Konfigurace Visual Studio Team Services (služby VSTS) k vytvoření projektů .NET Core pomocí jedné z těchto postupů:</span><span class="sxs-lookup"><span data-stu-id="466ce-162">Configure Visual Studio Team Services (VSTS) to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="466ce-163">Spusťte skript ze [ruční instalaci krok](#manual-setup) vaše příkazy.</span><span class="sxs-lookup"><span data-stu-id="466ce-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="466ce-164">Vytvořte sestavení skládá z několika služby VSTS předdefinované sestavení úlohy, které jsou nakonfigurovány pro použití nástroje pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="466ce-164">Create a build composed of several VSTS built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="466ce-165">Obě řešení jsou platné.</span><span class="sxs-lookup"><span data-stu-id="466ce-165">Both solutions are valid.</span></span> <span data-ttu-id="466ce-166">Pomocí skriptu ruční instalace, můžete řídit verzi nástroje, které se zobrazí, protože jste je stáhnout jako součást sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="466ce-167">Sestavení se spouští ze skriptu, který je nutné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="466ce-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="466ce-168">Toto téma se vztahuje pouze na ruční.</span><span class="sxs-lookup"><span data-stu-id="466ce-168">This topic only covers the manual option.</span></span> <span data-ttu-id="466ce-169">Další informace o sestavení pomocí služby VSTS skládání úlohy sestavení, přejděte služby VSTS [průběžnou integraci a nasazení](https://www.visualstudio.com/docs/build/overview) tématu.</span><span class="sxs-lookup"><span data-stu-id="466ce-169">For more information on composing a build with VSTS build tasks, visit the VSTS [Continuous integration and deployment](https://www.visualstudio.com/docs/build/overview) topic.</span></span>

<span data-ttu-id="466ce-170">Použití skriptu ruční instalaci v služby VSTS, vytvořte novou definici sestavení a zadejte skript, který chcete spustit pro krok sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-170">To use a manual setup script in VSTS, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="466ce-171">To se provádí pomocí uživatelského rozhraní služby VSTS:</span><span class="sxs-lookup"><span data-stu-id="466ce-171">This is accomplished using the VSTS user interface:</span></span>

1. <span data-ttu-id="466ce-172">Začněte vytvořením nové definice buildu.</span><span class="sxs-lookup"><span data-stu-id="466ce-172">Start by creating a new build definition.</span></span> <span data-ttu-id="466ce-173">Jakmile se na obrazovce, která poskytuje možnost definovat, jaký druh sestavení, které chcete vytvořit, vyberte **prázdný** možnost.</span><span class="sxs-lookup"><span data-stu-id="466ce-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Výběr definici prázdný sestavení](./media/using-ci-with-cli/screen1.png)

1. <span data-ttu-id="466ce-175">Po dokončení konfigurace úložiště k sestavení, se přesměruje na definice sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="466ce-176">Vyberte **přidat krok sestavení**:</span><span class="sxs-lookup"><span data-stu-id="466ce-176">Select **Add build step**:</span></span>

   ![Přidání kroku sestavení](./media/using-ci-with-cli/screen2.png)

1. <span data-ttu-id="466ce-178">Nabízí **úloha katalogu**.</span><span class="sxs-lookup"><span data-stu-id="466ce-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="466ce-179">Katalog obsahuje úlohy, které použijete v buildu.</span><span class="sxs-lookup"><span data-stu-id="466ce-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="466ce-180">Vzhledem k tomu, že máte skript, vyberte **přidat** tlačítko pro **prostředí PowerShell: spustit skript prostředí PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="466ce-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Přidání kroku skriptu prostředí PowerShell](./media/using-ci-with-cli/screen3.png)

1. <span data-ttu-id="466ce-182">Nakonfigurujte krok sestavení.</span><span class="sxs-lookup"><span data-stu-id="466ce-182">Configure the build step.</span></span> <span data-ttu-id="466ce-183">Přidejte skript z úložiště, který umožňuje vytvářet:</span><span class="sxs-lookup"><span data-stu-id="466ce-183">Add the script from the repository that you're building:</span></span>

   ![Určení spuštění skriptu prostředí PowerShell](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="466ce-185">Orchestrace sestavení</span><span class="sxs-lookup"><span data-stu-id="466ce-185">Orchestrating the build</span></span>

<span data-ttu-id="466ce-186">Většina tento dokument popisuje, jak získat nástroje .NET Core a nakonfigurovat různé služby CI bez zadání informací o tom, jak orchestraci, nebo *ve skutečnosti sestavení*, kódu s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="466ce-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="466ce-187">Volby o tom, jak struktury procesu sestavení závisí na mnoha faktorech, které nejde pokrýt obecné způsobem.</span><span class="sxs-lookup"><span data-stu-id="466ce-187">The choices on how to structure the build process depend on many factors that cannot be covered in a general way here.</span></span> <span data-ttu-id="466ce-188">Prozkoumejte prostředků a ukázky, které jsou součástí sady dokumentace [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [služby VSTS](https://www.visualstudio.com/docs/build/overview) Další informace o Orchestrace buildy s každým technologie.</span><span class="sxs-lookup"><span data-stu-id="466ce-188">Explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [VSTS](https://www.visualstudio.com/docs/build/overview) for more information on orchestrating your builds with each technology.</span></span>

<span data-ttu-id="466ce-189">Dva obecné přístupy, které provedete v procesu sestavení pro kód .NET Core pomocí nástrojů .NET Core strukturování jsou přímo pomocí nástroje MSBuild nebo používá příkazy příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="466ce-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="466ce-190">Jaký přístup byste měli vzít je určen podle vaše pohodlí úroveň s přístupy a kompromis složitostí.</span><span class="sxs-lookup"><span data-stu-id="466ce-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="466ce-191">MSBuild poskytuje schopnost express vašeho procesu sestavení jako úlohy a cíle, ale se dodává s přidané složitosti učení syntaxe souboru projektu nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="466ce-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="466ce-192">Pomocí nástroje příkazového řádku .NET Core je možná jednodušší, ale vyžaduje zapisovat orchestration logiku v skriptovací jazyk jako `bash` nebo prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="466ce-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="466ce-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="466ce-193">See also</span></span>

[<span data-ttu-id="466ce-194">Postup získání Ubuntu</span><span class="sxs-lookup"><span data-stu-id="466ce-194">Ubuntu acquisition steps</span></span>](https://www.microsoft.com/net/core#linuxubuntu)   
