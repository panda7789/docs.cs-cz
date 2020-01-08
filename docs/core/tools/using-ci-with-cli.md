---
title: Průběžná integrace (CI) s .NET Core SDK a nástroji
description: Naučte se používat .NET Core SDK a jeho nástroje na serveru sestavení s nepřetržitou integrací.
author: mairaw
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: 0f6049d1f2868ff330fd59c4f40e6c02231c6f71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343528"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="65f94-103">Používání .NET Core SDK a nástrojů v kontinuální integraci (CI)</span><span class="sxs-lookup"><span data-stu-id="65f94-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="65f94-104">Tento dokument popisuje použití .NET Core SDK a jeho nástrojů na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="65f94-105">Sada nástrojů .NET Core funguje interaktivně, pokud vývojář zadá příkazy na příkazovém řádku a automaticky, kde server průběžné integrace (CI) spouští skript sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="65f94-106">Příkazy, možnosti, vstupy a výstupy jsou stejné a jediné, co zadáte, je způsob, jak získat nástroje a systém pro sestavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="65f94-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="65f94-107">Tento dokument se zaměřuje na scénáře získání nástrojů pro CI s doporučeními, jak navrhovat a strukturovat skripty sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="65f94-108">Možnosti instalace pro servery sestavení CI</span><span class="sxs-lookup"><span data-stu-id="65f94-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="65f94-109">Použití nativních instalačních programů</span><span class="sxs-lookup"><span data-stu-id="65f94-109">Using the native installers</span></span>

<span data-ttu-id="65f94-110">Nativní instalační programy jsou k dispozici pro macOS, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="65f94-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="65f94-111">Instalační programy vyžadují přístup správce (sudo) k serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="65f94-112">Výhodou použití nativního instalačního programu je instalace všech nativních závislostí potřebných ke spuštění nástrojů.</span><span class="sxs-lookup"><span data-stu-id="65f94-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="65f94-113">Nativní instalační programy také poskytují instalaci sady SDK pro všechny systémy.</span><span class="sxs-lookup"><span data-stu-id="65f94-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="65f94-114">macOS uživatelé by měli používat instalační programy PKG.</span><span class="sxs-lookup"><span data-stu-id="65f94-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="65f94-115">V systému Linux existuje možnost použití Správce balíčků na základě informačního kanálu, jako je apt-get pro Ubuntu nebo Yumu pro CentOS, nebo použití samotných balíčků, DEB nebo ot./min.</span><span class="sxs-lookup"><span data-stu-id="65f94-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="65f94-116">Ve Windows použijte instalační program MSI.</span><span class="sxs-lookup"><span data-stu-id="65f94-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="65f94-117">Nejnovější stabilní binární soubory najdete v části [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="65f94-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="65f94-118">Pokud chcete použít nejnovější (a potenciálně nestabilní) předběžné verze nástrojů, použijte odkazy, které jsou k dispozici v [úložišti GitHub/Core-SDK](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="65f94-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="65f94-119">U distribucí Linux jsou k dispozici `tar.gz` archivy (označované také jako `tarballs`); pomocí instalačních skriptů v archivech nainstalujte .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65f94-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="65f94-120">Použití skriptu instalačního programu</span><span class="sxs-lookup"><span data-stu-id="65f94-120">Using the installer script</span></span>

<span data-ttu-id="65f94-121">Použití skriptu instalačního programu umožňuje instalaci bez oprávnění správce na serveru sestavení a snadné automatizace pro získání nástrojů.</span><span class="sxs-lookup"><span data-stu-id="65f94-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="65f94-122">Skript se postará o stažení nástrojů a jejich extrakci do výchozího nebo zadaného umístění, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="65f94-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="65f94-123">Můžete také zadat verzi nástrojů, které chcete nainstalovat, a zda chcete nainstalovat celou sadu SDK nebo pouze sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="65f94-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="65f94-124">Skript instalačního programu je automatizovaný pro spuštění na začátku sestavení za účelem načtení a instalaci požadované verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="65f94-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="65f94-125">*Požadovaná verze* je libovolná verze sady SDK, kterou vaše projekty vyžadují pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="65f94-126">Skript vám umožní nainstalovat sadu SDK do místního adresáře na serveru, spustit nástroje z nainstalovaného umístění a potom vyčistit (nebo nechat službu CI vyčistit) po sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="65f94-127">To zajišťuje zapouzdření a izolaci pro celý proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="65f94-128">Odkaz na instalační skript najdete v článku [dotnet-Install](dotnet-install-script.md) .</span><span class="sxs-lookup"><span data-stu-id="65f94-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="65f94-129">**Služby Azure DevOps**</span><span class="sxs-lookup"><span data-stu-id="65f94-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="65f94-130">Při použití skriptu instalačního programu nejsou nativní závislosti automaticky nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="65f94-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="65f94-131">Nativní závislosti je nutné nainstalovat, pokud je operační systém neobsahuje.</span><span class="sxs-lookup"><span data-stu-id="65f94-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="65f94-132">Další informace najdete v tématu [závislosti a požadavky .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="65f94-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="65f94-133">Příklady nastavení CI</span><span class="sxs-lookup"><span data-stu-id="65f94-133">CI setup examples</span></span>

<span data-ttu-id="65f94-134">Tato část popisuje ruční instalaci pomocí skriptu PowerShellu nebo bash spolu s popisem několika řešení CI pro software jako služba (SaaS).</span><span class="sxs-lookup"><span data-stu-id="65f94-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="65f94-135">Zahrnutá řešení SaaS CI jsou [TRAVIS CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)a [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="65f94-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="65f94-136">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="65f94-136">Manual setup</span></span>

<span data-ttu-id="65f94-137">Každá služba SaaS má své vlastní metody pro vytváření a konfiguraci procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="65f94-138">Pokud používáte jiné řešení SaaS, než je uvedené v seznamu nebo vyžadovat přizpůsobení nad rámec předběžného použití, musíte provést alespoň nějakou ruční konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="65f94-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="65f94-139">Obecně platí, že ruční instalace vyžaduje, abyste získali verzi nástrojů (nebo nejnovější noční sestavení nástrojů) a spustili skript sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="65f94-140">Pomocí skriptu PowerShell nebo bash můžete orchestrovat příkazy .NET Core nebo použít soubor projektu, který popisuje proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="65f94-141">Další informace o těchto možnostech najdete v [části orchestrace](#orchestrating-the-build) .</span><span class="sxs-lookup"><span data-stu-id="65f94-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="65f94-142">Po vytvoření skriptu, který provede ruční instalaci serveru sestavení CI, ho použijte ve vývojovém počítači k místnímu sestavení kódu pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="65f94-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="65f94-143">Jakmile ověříte, že se skript spouští dobře místně, nasaďte ho do svého serveru sestavení CI.</span><span class="sxs-lookup"><span data-stu-id="65f94-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="65f94-144">Poměrně jednoduchý skript PowerShellu ukazuje, jak získat .NET Core SDK a jak ho nainstalovat na server sestavení Windows.</span><span class="sxs-lookup"><span data-stu-id="65f94-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="65f94-145">Implementaci pro proces sestavení zadáte na konci skriptu.</span><span class="sxs-lookup"><span data-stu-id="65f94-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="65f94-146">Skript získá nástroje a pak provede proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="65f94-147">Pro počítače se systémem UNIX provede následující skript bash akce popsané ve skriptu prostředí PowerShell podobným způsobem:</span><span class="sxs-lookup"><span data-stu-id="65f94-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="65f94-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="65f94-148">Travis CI</span></span>

<span data-ttu-id="65f94-149">[TRAVIS CI](https://travis-ci.org/) můžete nakonfigurovat pro instalaci .NET Core SDK pomocí jazyka `csharp` a `dotnet`ho klíče.</span><span class="sxs-lookup"><span data-stu-id="65f94-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="65f94-150">Další informace najdete v oficiální dokumentaci k Travis ci na webu [vytváření C#, F#nebo Visual Basic projektu](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="65f94-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="65f94-151">Mějte na paměti, že při přístupu k Travis informacím o CI, které komunita udržuje `language: csharp` identifikátor jazyka, funguje pro všechny F#jazyky .NET, včetně a mono.</span><span class="sxs-lookup"><span data-stu-id="65f94-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="65f94-152">Travis CI spouští úlohy macOS a Linux v *matrici sestavení*, kde zadáváte kombinaci modulu runtime, prostředí a vyloučení a zahrnutí, která budou zahrnovat vaše kombinace sestavení pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="65f94-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="65f94-153">Další informace naleznete v článku [přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) v dokumentaci k Travis CI.</span><span class="sxs-lookup"><span data-stu-id="65f94-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="65f94-154">Nástroje založené na MSBuildu zahrnují do balíčku modul runtime LTS (1.0. x) a aktuální (1.1. x). instalace sady SDK proto obdržíte všechno, co potřebujete k sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="65f94-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="65f94-155">AppVeyor</span></span>

<span data-ttu-id="65f94-156">[AppVeyor](https://www.appveyor.com/) nainstaluje sadu SDK sady .NET Core 1.0.1 pomocí `Visual Studio 2017` image pro sestavení pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="65f94-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="65f94-157">K dispozici jsou další image sestavení s různými verzemi .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="65f94-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="65f94-158">Další informace najdete v článku [příklad AppVeyor. yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) a [Build Worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) v dokumentaci AppVeyor.</span><span class="sxs-lookup"><span data-stu-id="65f94-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="65f94-159">.NET Core SDK binární soubory byly staženy a extrahovány v podadresáři pomocí instalačního skriptu a poté přidány do proměnné prostředí `PATH`.</span><span class="sxs-lookup"><span data-stu-id="65f94-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="65f94-160">Přidejte matrici sestavení pro spuštění testů integrace s více verzemi .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="65f94-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="65f94-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="65f94-161">Azure DevOps Services</span></span>

<span data-ttu-id="65f94-162">Nakonfigurujte Azure DevOps Services pro sestavení projektů .NET Core pomocí jednoho z těchto přístupů:</span><span class="sxs-lookup"><span data-stu-id="65f94-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="65f94-163">Spusťte skript z [kroku ruční instalace](#manual-setup) pomocí příkazů.</span><span class="sxs-lookup"><span data-stu-id="65f94-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="65f94-164">Vytvořte sestavení složené z několika Azure DevOps Services integrovaných úloh sestavení, které jsou nakonfigurovány pro použití nástrojů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65f94-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="65f94-165">Obě řešení jsou platná.</span><span class="sxs-lookup"><span data-stu-id="65f94-165">Both solutions are valid.</span></span> <span data-ttu-id="65f94-166">Pomocí skriptu ručního nastavení můžete řídit verzi nástrojů, které obdržíte, protože je stáhnete jako součást sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="65f94-167">Sestavení je spuštěno ze skriptu, který je třeba vytvořit.</span><span class="sxs-lookup"><span data-stu-id="65f94-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="65f94-168">Tento článek se týká pouze ručních možností.</span><span class="sxs-lookup"><span data-stu-id="65f94-168">This article only covers the manual option.</span></span> <span data-ttu-id="65f94-169">Další informace o vytváření sestavení pomocí Azure DevOps Services úloh sestavení naleznete v dokumentaci k [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) .</span><span class="sxs-lookup"><span data-stu-id="65f94-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="65f94-170">Chcete-li použít skript ručního nastavení v Azure DevOps Services, vytvořte novou definici sestavení a zadejte skript, který bude spuštěn pro krok sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="65f94-171">K tomu je možné použít Azure DevOps Services uživatelské rozhraní:</span><span class="sxs-lookup"><span data-stu-id="65f94-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="65f94-172">Začněte vytvořením nové definice sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-172">Start by creating a new build definition.</span></span> <span data-ttu-id="65f94-173">Až se dostanete na obrazovku, která vám poskytne možnost definovat typ sestavení, který chcete vytvořit, vyberte **prázdnou** možnost.</span><span class="sxs-lookup"><span data-stu-id="65f94-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Výběr prázdné definice sestavení](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="65f94-175">Po nakonfigurování úložiště, které se má sestavit, budete přesměrováni na definice sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="65f94-176">Vyberte **Přidat krok sestavení**:</span><span class="sxs-lookup"><span data-stu-id="65f94-176">Select **Add build step**:</span></span>

   ![Přidání kroku sestavení](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="65f94-178">Zobrazuje se v **katalogu úloh**.</span><span class="sxs-lookup"><span data-stu-id="65f94-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="65f94-179">Katalog obsahuje úlohy, které v sestavení používáte.</span><span class="sxs-lookup"><span data-stu-id="65f94-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="65f94-180">Vzhledem k tomu, že máte skript, vyberte tlačítko **Přidat** pro **PowerShell: Spusťte powershellový skript**.</span><span class="sxs-lookup"><span data-stu-id="65f94-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Přidání kroku skriptu PowerShellu](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="65f94-182">Nakonfigurujte krok sestavení.</span><span class="sxs-lookup"><span data-stu-id="65f94-182">Configure the build step.</span></span> <span data-ttu-id="65f94-183">Přidejte skript z úložiště, které vytváříte:</span><span class="sxs-lookup"><span data-stu-id="65f94-183">Add the script from the repository that you're building:</span></span>

   ![Určení skriptu prostředí PowerShell, který se má spustit](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="65f94-185">Orchestrace sestavení</span><span class="sxs-lookup"><span data-stu-id="65f94-185">Orchestrating the build</span></span>

<span data-ttu-id="65f94-186">Většina tohoto dokumentu popisuje, jak získat nástroje .NET Core a nakonfigurovat různé služby CI bez poskytování informací o tom, jak orchestrovat, nebo *ve skutečnosti sestavit*kód pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65f94-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="65f94-187">Volby, jak strukturovat proces sestavení, závisí na mnoha faktorech, které se tady nedají zakrýt obecným způsobem.</span><span class="sxs-lookup"><span data-stu-id="65f94-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="65f94-188">Další informace o orchestraci vašich sestavení s každou technologií najdete v dokumentaci k prostředkům a ukázkám, které jsou k dispozici v dokumentaci sady [TRAVIS CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)a [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="65f94-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="65f94-189">Dva obecné přístupy, které přiberete při vytváření struktury procesu sestavení pro kód .NET Core pomocí nástrojů .NET Core, používají přímo nástroj MSBuild nebo pomocí příkazů příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65f94-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="65f94-190">Jaký přístup byste měli vzít v úvahu, závisí na vaší úrovni pohodlí s ohledem na složitost a kompromisy.</span><span class="sxs-lookup"><span data-stu-id="65f94-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="65f94-191">Nástroj MSBuild poskytuje možnost vyjádřit svůj proces sestavení jako úkoly a cíle, ale obsahuje i zvýšení složitosti syntaxe souboru projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="65f94-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="65f94-192">Použití nástrojů příkazového řádku .NET Core je možná jednodušší, ale vyžaduje, abyste napsali logiku orchestrace ve skriptovacím jazyce, jako je `bash` nebo PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65f94-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="65f94-193">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65f94-193">See also</span></span>

- [<span data-ttu-id="65f94-194">Soubory ke stažení pro .NET – Linux</span><span class="sxs-lookup"><span data-stu-id="65f94-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
