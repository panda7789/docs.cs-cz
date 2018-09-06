---
title: Pomocí sady .NET Core SDK a nástroje v kontinuální integrace (CI)
description: Informace o použití sady .NET Core SDK a jeho nástroje na serveru sestavení.
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.openlocfilehash: 0835ffafc6c091c311b03c90f665cbd669cccfe9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749931"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="95c8d-103">Pomocí sady .NET Core SDK a nástroje v kontinuální integrace (CI)</span><span class="sxs-lookup"><span data-stu-id="95c8d-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

## <a name="overview"></a><span data-ttu-id="95c8d-104">Přehled</span><span class="sxs-lookup"><span data-stu-id="95c8d-104">Overview</span></span>

<span data-ttu-id="95c8d-105">Tento dokument popisuje, jak pomocí .NET Core SDK a jeho nástrojů na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-105">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="95c8d-106">.NET Core nástrojů prací obou interaktivně, kde vývojář typů příkazy do příkazového řádku a automaticky, pokud server kontinuální integrace (CI) spustí skript sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-106">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="95c8d-107">Příkazy, možnosti, vstupy a výstupy jsou stejné, a jedinou akcí, které zadáte představují způsob, jak získat nástroje a systém k sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="95c8d-107">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="95c8d-108">Tento dokument se zaměřuje na scénáře pořízení nástroj pro nepřetržitou Integraci s doporučeními o tom, jak navrhovat a strukturují vaše skripty sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-108">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="95c8d-109">Možnosti instalace pro nepřetržitou Integraci sestavovacích serverů</span><span class="sxs-lookup"><span data-stu-id="95c8d-109">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="95c8d-110">Použití nativních instalačních programů</span><span class="sxs-lookup"><span data-stu-id="95c8d-110">Using the native installers</span></span>

<span data-ttu-id="95c8d-111">Nativní instalační programy jsou dostupné pro macOS, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="95c8d-111">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="95c8d-112">Instalační programy vyžadují přístup správce (sudo) na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-112">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="95c8d-113">Výhodou použití nativní instalačního programu se nainstaluje všechny komponenty nástroje nativní závislosti, které vyžaduje pro spuštění nástroje.</span><span class="sxs-lookup"><span data-stu-id="95c8d-113">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="95c8d-114">Nativních instalačních programů poskytují také systémová instalace sady SDK.</span><span class="sxs-lookup"><span data-stu-id="95c8d-114">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="95c8d-115">macOS uživatelé by měli použít instalační programy balíčku.</span><span class="sxs-lookup"><span data-stu-id="95c8d-115">macOS users should use the PKG installers.</span></span> <span data-ttu-id="95c8d-116">V systému Linux je pomocí Správce balíčků založená na informační kanál, třeba apt-get pro Ubuntu nebo yumu pro CentOS, nebo pomocí balíčků, sami, DEB nebo ot. / min.</span><span class="sxs-lookup"><span data-stu-id="95c8d-116">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="95c8d-117">Ve Windows použijte instalační službu MSI.</span><span class="sxs-lookup"><span data-stu-id="95c8d-117">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="95c8d-118">Nejnovější stabilní binární soubory se nacházejí v [Začínáme s .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="95c8d-118">The latest stable binaries are found at [Get Started with .NET Core](https://aka.ms/dotnetcoregs).</span></span> <span data-ttu-id="95c8d-119">Pokud chcete používat nejnovější (a potenciálně nestabilní) předběžné verze nástroje, pomocí odkazů uvedených v [úložiště GitHub dotnet/cli](https://github.com/dotnet/cli#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="95c8d-119">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/cli GitHub repository](https://github.com/dotnet/cli#installers-and-binaries).</span></span> <span data-ttu-id="95c8d-120">Pro distribuce Linuxu `tar.gz` archivy (označované také jako `tarballs`) jsou k dispozici; nainstalujte .NET Core pomocí skriptů instalace v rámci archivu.</span><span class="sxs-lookup"><span data-stu-id="95c8d-120">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="95c8d-121">Pomocí skriptů Instalační program</span><span class="sxs-lookup"><span data-stu-id="95c8d-121">Using the installer script</span></span>

<span data-ttu-id="95c8d-122">Pomocí skriptu instalačního programu umožňuje instalaci bez oprávnění správce na serveru sestavení a snadná automatizace pro získání nástrojů.</span><span class="sxs-lookup"><span data-stu-id="95c8d-122">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="95c8d-123">Skript se postará o stažení nástrojů a extrahování do výchozí nebo zadané umístění pro použití.</span><span class="sxs-lookup"><span data-stu-id="95c8d-123">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="95c8d-124">Můžete také určit verzi nástrojů, kterou chcete nainstalovat a určuje, zda chcete nainstalovat celou sadu SDK nebo pouze sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="95c8d-124">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="95c8d-125">Skript instalačního programu je automatické spouštění na začátku operace sestavení pro načtení a instalaci požadované verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="95c8d-125">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="95c8d-126">*Požadovanou verzi* je libovolné verzi sady SDK vyžadovat vaše projekty k sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-126">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="95c8d-127">Skript umožňuje nainstalovat sadu SDK do místního adresáře na serveru, spustit nástroje z umístění instalace a potom vyčištění (nebo umožní službě CI vyčistit) po sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-127">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="95c8d-128">Poskytuje zapouzdření a izolace pro celý váš proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-128">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="95c8d-129">Odkaz na instalační skript se nachází v [nainstalujte dotnet](dotnet-install-script.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="95c8d-129">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="95c8d-130">Pokud používáte skript instalačního programu, nativní závislosti nejsou nainstalovány automaticky.</span><span class="sxs-lookup"><span data-stu-id="95c8d-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="95c8d-131">Pokud operační systém nemá, je nutné nainstalovat nativní závislosti.</span><span class="sxs-lookup"><span data-stu-id="95c8d-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="95c8d-132">Zobrazit seznam požadavků [požadavky na nativní .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="95c8d-132">See the list of prerequisites in the [.NET Core native prerequisites](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) topic.</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="95c8d-133">Příklady nastavení položky konfigurace</span><span class="sxs-lookup"><span data-stu-id="95c8d-133">CI setup examples</span></span>

<span data-ttu-id="95c8d-134">Tato část popisuje ruční instalaci pomocí skriptu prostředí PowerShell nebo prostředí bash, popisy několik softwaru jako řešení CI služby (SaaS).</span><span class="sxs-lookup"><span data-stu-id="95c8d-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="95c8d-135">Řešení SaaS CI popsaná jsou [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [Visual Studio Team Services Build](https://docs.microsoft.com/vsts/build-release/index).</span><span class="sxs-lookup"><span data-stu-id="95c8d-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Visual Studio Team Services Build](https://docs.microsoft.com/vsts/build-release/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="95c8d-136">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="95c8d-136">Manual setup</span></span>

<span data-ttu-id="95c8d-137">Každá služba SaaS má své vlastní metody vytvoření a konfigurace procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="95c8d-138">Pokud používáte jiné řešení SaaS, než je uveden nebo vyžadují přizpůsobení kromě předem zabalené podpory, je nutné provést nejméně část konfigurace ručně.</span><span class="sxs-lookup"><span data-stu-id="95c8d-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="95c8d-139">Obecně platí ruční instalaci je potřeba získat z verze nástroje (nebo noční sestavení nástrojů) a spusťte váš skript buildu.</span><span class="sxs-lookup"><span data-stu-id="95c8d-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="95c8d-140">Můžete použít prostředí PowerShell nebo bash skript k orchestraci příkazy .NET Core nebo soubor projektu, který popisuje proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="95c8d-141">[Orchestrace části](#orchestrating-the-build) poskytující víc podrobností o těchto možnostech.</span><span class="sxs-lookup"><span data-stu-id="95c8d-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="95c8d-142">Po vytvoření skriptu, který provádí ruční instalací serveru sestavení CI, používejte ji na vývojovém počítači k sestavení vašeho kódu místně pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="95c8d-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="95c8d-143">Jakmile se ujistíte, že je a místně spuštěný skript, nasaďte na server sestavení CI.</span><span class="sxs-lookup"><span data-stu-id="95c8d-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="95c8d-144">Poměrně jednoduchý skript prostředí PowerShell ukazuje, jak získat sadu .NET Core SDK a nainstalujte ho na server sestavení Windows:</span><span class="sxs-lookup"><span data-stu-id="95c8d-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="95c8d-145">Poskytuje implementaci pro proces sestavení na konci tohoto skriptu.</span><span class="sxs-lookup"><span data-stu-id="95c8d-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="95c8d-146">Skript získá nástroje a poté spustí proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="95c8d-147">Následující skript bash pro počítače platformy UNIX provede akce popsané v skriptu prostředí PowerShell podobným způsobem:</span><span class="sxs-lookup"><span data-stu-id="95c8d-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="95c8d-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="95c8d-148">Travis CI</span></span>

<span data-ttu-id="95c8d-149">Můžete nakonfigurovat [Travis CI](https://travis-ci.org/) nainstalovat s použitím sady .NET Core SDK `csharp` jazyka a `dotnet` klíč.</span><span class="sxs-lookup"><span data-stu-id="95c8d-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="95c8d-150">Najdete v oficiální dokumentace Travis CI na [sestavení C#, F # nebo projektu jazyka Visual Basic](https://docs.travis-ci.com/user/languages/csharp/) Další informace.</span><span class="sxs-lookup"><span data-stu-id="95c8d-150">See the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) for more information.</span></span> <span data-ttu-id="95c8d-151">Všimněte si, jak přistupovat k informacím Travis CI, která udržuje komunity `language: csharp` identifikátor jazyka se dá použít pro všechny jazyky .NET, včetně F # a Mono.</span><span class="sxs-lookup"><span data-stu-id="95c8d-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="95c8d-152">Travis CI běží i macOS (OS X 10.11, OS X 10.12) a Linux (Ubuntu 14.04) úlohy v *sestavení matice*, kde můžete určit kombinaci modulu runtime, prostředí a vyloučení nebo zahrnutí pokrýt kombinace vašeho sestavení pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="95c8d-152">Travis CI runs both macOS (OS X 10.11, OS X 10.12) and Linux (Ubuntu 14.04) jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="95c8d-153">Najdete v článku [. Příklad travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) souboru a [přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) v dokumentaci Travis CI pro další informace.</span><span class="sxs-lookup"><span data-stu-id="95c8d-153">See the [.travis.yml example](https://github.com/dotnet/docs/blob/master/.travis.yml) file and [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) in the Travis CI docs for more information.</span></span> <span data-ttu-id="95c8d-154">Nástroje založené na MSBuild zahrnují LTS (1.0.x) a moduly runtime aktuální (1.1.x) v balíčku. takže nainstalováním sady SDK, zobrazí se všechno, co potřebujete k vytváření.</span><span class="sxs-lookup"><span data-stu-id="95c8d-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="95c8d-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="95c8d-155">AppVeyor</span></span>

<span data-ttu-id="95c8d-156">[AppVeyor](https://www.appveyor.com/) nainstaluje .NET Core 1.0.1 SDK se `Visual Studio 2017` sestavení image pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="95c8d-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="95c8d-157">Další sestavení Image s různými verzemi nástroje .NET Core SDK jsou k dispozici. najdete v článku [appveyor.yml příklad](https://github.com/dotnet/docs/blob/master/appveyor.yml) a [sestavování imagí pro pracovníka](https://www.appveyor.com/docs/build-environment/#build-worker-images) tématu v dokumentaci AppVeyor pro další informace.</span><span class="sxs-lookup"><span data-stu-id="95c8d-157">Other build images with different versions of the .NET Core SDK are available; see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) topic in the AppVeyor docs for more information.</span></span>

<span data-ttu-id="95c8d-158">Binární soubory sady SDK .NET Core stáhnou a odblokujte v podadresáři pomocí instalačního skriptu, a potom se přidají do `PATH` proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="95c8d-158">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="95c8d-159">Přidáte matici sestavení ke spuštění testů integrace s více verzemi nástroje .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="95c8d-159">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a><span data-ttu-id="95c8d-160">Visual Studio Team Services (VSTS)</span><span class="sxs-lookup"><span data-stu-id="95c8d-160">Visual Studio Team Services (VSTS)</span></span>

<span data-ttu-id="95c8d-161">Konfigurace Visual Studio Team Services (VSTS) k sestavení projektů .NET Core pomocí jedné z těchto přístupů:</span><span class="sxs-lookup"><span data-stu-id="95c8d-161">Configure Visual Studio Team Services (VSTS) to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="95c8d-162">Spusťte skript ze [ruční instalaci krok](#manual-setup) pomocí příkazů.</span><span class="sxs-lookup"><span data-stu-id="95c8d-162">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="95c8d-163">Vytvořte sestavení se skládá z několika úloh VSTS integrované sestavení, které jsou nakonfigurovány pro použití nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95c8d-163">Create a build composed of several VSTS built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="95c8d-164">Obě řešení jsou platné.</span><span class="sxs-lookup"><span data-stu-id="95c8d-164">Both solutions are valid.</span></span> <span data-ttu-id="95c8d-165">Pomocí skriptu ruční instalace, řízení verze nástrojů, které jste dostali, protože si stáhnout jako součást sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-165">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="95c8d-166">Sestavení je spuštěno ze skriptu, který je nutné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="95c8d-166">The build is run from a script that you must create.</span></span> <span data-ttu-id="95c8d-167">Toto téma popisuje pouze možnost ručně.</span><span class="sxs-lookup"><span data-stu-id="95c8d-167">This topic only covers the manual option.</span></span> <span data-ttu-id="95c8d-168">Další informace o vytváření sestavení s využitím VSTS úlohy sestavení, najdete ve VSTS [průběžnou integraci a nasazování](https://docs.microsoft.com/vsts/build-release/index) tématu.</span><span class="sxs-lookup"><span data-stu-id="95c8d-168">For more information on composing a build with VSTS build tasks, visit the VSTS [Continuous integration and deployment](https://docs.microsoft.com/vsts/build-release/index) topic.</span></span>

<span data-ttu-id="95c8d-169">Použití skriptu ruční instalace ve VSTS, vytvořte novou definici sestavení a určete skript, který chcete spustit kroku sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-169">To use a manual setup script in VSTS, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="95c8d-170">To lze provést pomocí uživatelského rozhraní VSTS:</span><span class="sxs-lookup"><span data-stu-id="95c8d-170">This is accomplished using the VSTS user interface:</span></span>

1. <span data-ttu-id="95c8d-171">Začněte vytvořením nové definice sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-171">Start by creating a new build definition.</span></span> <span data-ttu-id="95c8d-172">Jakmile se obrazovka, která poskytuje možnost určit, jaký typ sestavení, kterou chcete vytvořit, vyberte **prázdný** možnost.</span><span class="sxs-lookup"><span data-stu-id="95c8d-172">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Vyberte definici sestavení prázdný](./media/using-ci-with-cli/screen1.png)

1. <span data-ttu-id="95c8d-174">Po dokončení konfigurace úložiště k sestavení, budete přesměrováni na definice sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-174">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="95c8d-175">Vyberte **přidat krok sestavení**:</span><span class="sxs-lookup"><span data-stu-id="95c8d-175">Select **Add build step**:</span></span>

   ![Přidání kroku sestavení](./media/using-ci-with-cli/screen2.png)

1. <span data-ttu-id="95c8d-177">Zobrazí se vám **katalogu úloh**.</span><span class="sxs-lookup"><span data-stu-id="95c8d-177">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="95c8d-178">Katalog obsahuje úlohy, které můžete použít v sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-178">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="95c8d-179">Protože máte skript, vyberte **přidat** tlačítko pro **prostředí PowerShell: spustit skript prostředí PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="95c8d-179">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Přidání kroku skript prostředí PowerShell](./media/using-ci-with-cli/screen3.png)

1. <span data-ttu-id="95c8d-181">Nakonfigurujte krok sestavení.</span><span class="sxs-lookup"><span data-stu-id="95c8d-181">Configure the build step.</span></span> <span data-ttu-id="95c8d-182">Přidáte z úložiště, kterou vytváříte skript:</span><span class="sxs-lookup"><span data-stu-id="95c8d-182">Add the script from the repository that you're building:</span></span>

   ![Určení spuštění skriptu prostředí PowerShell](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="95c8d-184">Orchestrace sestavení</span><span class="sxs-lookup"><span data-stu-id="95c8d-184">Orchestrating the build</span></span>

<span data-ttu-id="95c8d-185">Většina tento dokument popisuje, jak získat nástroje .NET Core a konfigurovat různé služby CI bez zadání informací o tom, jak orchestrovat, nebo *sestavují*, váš kód s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95c8d-185">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="95c8d-186">Volby v tom, jak strukturovat proces sestavení závisí na mnoha faktorech, které nejde pokrýt obecné způsobem.</span><span class="sxs-lookup"><span data-stu-id="95c8d-186">The choices on how to structure the build process depend on many factors that cannot be covered in a general way here.</span></span> <span data-ttu-id="95c8d-187">Prozkoumat prostředky a ukázky, které jsou součástí sady dokumentace [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [VSTS](https://docs.microsoft.com/vsts/build-release/index) Další informace o orchestraci buildů v každé technologie.</span><span class="sxs-lookup"><span data-stu-id="95c8d-187">Explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [VSTS](https://docs.microsoft.com/vsts/build-release/index) for more information on orchestrating your builds with each technology.</span></span>

<span data-ttu-id="95c8d-188">Dvě obecné metody, které provedete v strukturování proces sestavení pro kód .NET Core pomocí nástroje .NET Core jsou přímo pomocí nástroje MSBuild nebo pomocí příkazů příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95c8d-188">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="95c8d-189">Jaký přístup je potřeba se určuje podle vaší úrovně pohodlí přístupy a kompromisy složitost.</span><span class="sxs-lookup"><span data-stu-id="95c8d-189">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="95c8d-190">Nástroj MSBuild poskytuje schopnost procesu sestavení je možné vyjádřit jako úlohy a cíle, ale obsahuje přidaná složitost studijních syntaxe souboru projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="95c8d-190">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="95c8d-191">Pomocí nástroje příkazového řádku .NET Core je možná jednodušší, ale vyžaduje, abyste psát logiku Orchestrace ve skriptovacím jazyce jako `bash` nebo prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95c8d-191">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="95c8d-192">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95c8d-192">See also</span></span>

* [<span data-ttu-id="95c8d-193">Postup získání Ubuntu</span><span class="sxs-lookup"><span data-stu-id="95c8d-193">Ubuntu acquisition steps</span></span>](https://www.microsoft.com/net/core#linuxubuntu)
