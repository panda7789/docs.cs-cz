---
title: Průběžná integrace (CI) s .NET Core SDK a nástroji
description: Zjistěte, jak používat sadku .NET Core SDK a její nástroje na serveru sestavení s průběžnou integrací.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451035"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="55cd2-103">Použití sady .NET Core SDK a nástrojů v průběžné integraci (CI)</span><span class="sxs-lookup"><span data-stu-id="55cd2-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="55cd2-104">Tento dokument popisuje použití sady .NET Core SDK a jejích nástrojů na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="55cd2-105">Sada nástrojů .NET Core funguje interaktivně, kde vývojář zadá příkazy na příkazovém řádku a automaticky, kde server průběžné integrace (CI) spustí skript sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="55cd2-106">Příkazy, možnosti, vstupy a výstupy jsou stejné a jediné, co zadáte, jsou způsob, jak získat nástroje a systém pro sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="55cd2-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="55cd2-107">Tento dokument se zaměřuje na scénáře nástroje pořízení pro CI s doporučeními, jak navrhnout a strukturovat skripty sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="55cd2-108">Možnosti instalace pro servery sestavení CI</span><span class="sxs-lookup"><span data-stu-id="55cd2-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="55cd2-109">Použití nativních instalačních techniků</span><span class="sxs-lookup"><span data-stu-id="55cd2-109">Using the native installers</span></span>

<span data-ttu-id="55cd2-110">Nativní instalační programy jsou k dispozici pro macOS, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="55cd2-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="55cd2-111">Instalátory vyžadují přístup správce (sudo) k serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="55cd2-112">Výhodou použití nativního instalačního programu je, že nainstaluje všechny nativní závislosti potřebné ke spuštění nástrojů.</span><span class="sxs-lookup"><span data-stu-id="55cd2-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="55cd2-113">Nativní instalační programy také poskytují celosystémovou instalaci sady SDK.</span><span class="sxs-lookup"><span data-stu-id="55cd2-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="55cd2-114">Uživatelé macOS by měli používat instalační programy PKG.</span><span class="sxs-lookup"><span data-stu-id="55cd2-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="55cd2-115">Na Linuxu je na výběr použití správce balíčků založených na zdroji, jako je apt-get pro Ubuntu nebo yum pro CentOS, nebo pomocí samotných balíčků, DEB nebo RPM.</span><span class="sxs-lookup"><span data-stu-id="55cd2-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="55cd2-116">V systému Windows použijte instalační program MSI.</span><span class="sxs-lookup"><span data-stu-id="55cd2-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="55cd2-117">Nejnovější stabilní binární soubory se nacházejí v [souborech ke stažení .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="55cd2-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="55cd2-118">Pokud chcete použít nejnovější (a potenciálně nestabilní) předběžné nástroje, použijte odkazy uvedené v [úložišti GitHub dotnet/core-sdk](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="55cd2-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="55cd2-119">Pro linuxové `tar.gz` distribuce jsou k `tarballs`dispozici archivy (známé také jako); K instalaci rozhraní .NET Core použijte instalační skripty v archivu.</span><span class="sxs-lookup"><span data-stu-id="55cd2-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="55cd2-120">Použití instalačního skriptu</span><span class="sxs-lookup"><span data-stu-id="55cd2-120">Using the installer script</span></span>

<span data-ttu-id="55cd2-121">Použití instalačního skriptu umožňuje instalaci bez oprávnění správce na serveru sestavení a snadnou automatizaci pro získání nástrojů.</span><span class="sxs-lookup"><span data-stu-id="55cd2-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="55cd2-122">Skript se postará o stažení nástrojů a jeho extrahování do výchozího nebo určeného umístění pro použití.</span><span class="sxs-lookup"><span data-stu-id="55cd2-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="55cd2-123">Můžete také určit verzi nástroje, kterou chcete nainstalovat, a zda chcete nainstalovat celou sadu SDK nebo pouze sdílený běh ový čas.</span><span class="sxs-lookup"><span data-stu-id="55cd2-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="55cd2-124">Instalační skript je automatizován pro spuštění na začátku sestavení pro načtení a instalaci požadované verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="55cd2-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="55cd2-125">*Požadovaná verze* je bez ohledu na verzi sady SDK vaše projekty vyžadují k sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="55cd2-126">Skript umožňuje nainstalovat sadu SDK v místním adresáři na serveru, spustit nástroje z nainstalovaného umístění a poté vyčistit (nebo nechat službu CI vyčistit) po sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="55cd2-127">To poskytuje zapouzdření a izolace na celý proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="55cd2-128">Odkaz na instalační skript se nachází v článku [dotnet-install.](dotnet-install-script.md)</span><span class="sxs-lookup"><span data-stu-id="55cd2-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="55cd2-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="55cd2-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="55cd2-130">Při použití instalačního skriptu se nativní závislosti neinstalují automaticky.</span><span class="sxs-lookup"><span data-stu-id="55cd2-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="55cd2-131">Nativní závislosti je nutné nainstalovat, pokud je operační systém nemá.</span><span class="sxs-lookup"><span data-stu-id="55cd2-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="55cd2-132">Další informace naleznete v tématu [.NET Core závislosti a požadavky](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="55cd2-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="55cd2-133">Příklady nastavení CI</span><span class="sxs-lookup"><span data-stu-id="55cd2-133">CI setup examples</span></span>

<span data-ttu-id="55cd2-134">Tato část popisuje ruční nastavení pomocí skriptu PowerShell nebo bash spolu s popisem několika řešení CI softwaru jako služby (SaaS).</span><span class="sxs-lookup"><span data-stu-id="55cd2-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="55cd2-135">Řešení SaaS CI, na které se [vztahuje,](https://travis-ci.org/)jsou Travis CI , [AppVeyor](https://www.appveyor.com/)a [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="55cd2-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="55cd2-136">Ruční nastavení</span><span class="sxs-lookup"><span data-stu-id="55cd2-136">Manual setup</span></span>

<span data-ttu-id="55cd2-137">Každá služba SaaS má své vlastní metody pro vytváření a konfiguraci procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="55cd2-138">Pokud používáte jiné řešení SaaS než uvedené nebo vyžadují přizpůsobení nad rámec předběžné podpory, je nutné provést alespoň některé ruční konfigurace.</span><span class="sxs-lookup"><span data-stu-id="55cd2-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="55cd2-139">Obecně platí ruční nastavení vyžaduje, abyste získali verzi nástrojů (nebo nejnovější noční sestavení nástrojů) a spusťte skript sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="55cd2-140">Skript PowerShellu nebo bash můžete použít k orchestraci příkazů jádra .NET nebo použít soubor projektu, který nastiňuje proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="55cd2-141">[Část orchestrace](#orchestrating-the-build) obsahuje další podrobnosti o těchto možnostech.</span><span class="sxs-lookup"><span data-stu-id="55cd2-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="55cd2-142">Po vytvoření skriptu, který provádí ruční nastavení serveru sestavení CI, použijte jej na počítači pro účely dev k sestavení kódu místně pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="55cd2-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="55cd2-143">Jakmile potvrdíte, že skript běží dobře místně, nasaďte jej na server sestavení CI.</span><span class="sxs-lookup"><span data-stu-id="55cd2-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="55cd2-144">Relativně jednoduchý skript prostředí PowerShell ukazuje, jak získat sadku .NET Core SDK a nainstalovat ji na server sestavení systému Windows:</span><span class="sxs-lookup"><span data-stu-id="55cd2-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="55cd2-145">Můžete zadat implementaci pro proces sestavení na konci skriptu.</span><span class="sxs-lookup"><span data-stu-id="55cd2-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="55cd2-146">Skript získá nástroje a potom spustí proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="55cd2-147">U počítačů se systémem UNIX provádí následující skript bash akce popsané ve skriptu prostředí PowerShell podobným způsobem:</span><span class="sxs-lookup"><span data-stu-id="55cd2-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="55cd2-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="55cd2-148">Travis CI</span></span>

<span data-ttu-id="55cd2-149">Můžete nakonfigurovat [Travis CI](https://travis-ci.org/) nainstalovat .NET Core `csharp` SDK `dotnet` pomocí jazyka a klíče.</span><span class="sxs-lookup"><span data-stu-id="55cd2-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="55cd2-150">Další informace naleznete v oficiálních dokumentech Travis CI na [stavební C #, F# nebo Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="55cd2-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="55cd2-151">Všimněte si, že při přístupu `language: csharp` k informacím Travis CI, že identifikátor jazyka spravované komunitou funguje pro všechny jazyky .NET, včetně F#, a Mono.</span><span class="sxs-lookup"><span data-stu-id="55cd2-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="55cd2-152">Travis CI spouští úlohy macOS i Linux v *matici sestavení*, kde zadáte kombinaci runtime, prostředí a vyloučení/inkluzí, které pokryjí kombinace sestavení pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="55cd2-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="55cd2-153">Další informace naleznete v [tématu Přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) článku v dokumentaci Travis CI.</span><span class="sxs-lookup"><span data-stu-id="55cd2-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="55cd2-154">Nástroje založené na MSBuild zahrnují běhové časy LTS (1.0.x) a Current (1.1.x) v balíčku; takže instalací sady SDK obdržíte vše, co potřebujete k sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="55cd2-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="55cd2-155">AppVeyor</span></span>

<span data-ttu-id="55cd2-156">[AppVeyor](https://www.appveyor.com/) nainstaluje .NET Core 1.0.1 SDK s bitovou kopii pracovního procesu `Visual Studio 2017` sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="55cd2-157">Další image sestavení s různými verzemi sady .NET Core SDK jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="55cd2-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="55cd2-158">Další informace naleznete [v příkladu appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) a v článku [Sestavení pracovních bitových kopií](https://www.appveyor.com/docs/build-environment/#build-worker-images) v dokumentech AppVeyor.</span><span class="sxs-lookup"><span data-stu-id="55cd2-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="55cd2-159">Binární soubory sady .NET Core SDK se stahují a rozbalují v podadresáři `PATH` pomocí instalačního skriptu a pak jsou přidány do proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="55cd2-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="55cd2-160">Přidejte matici sestavení pro spuštění integračních testů s více verzemi sady .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="55cd2-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="55cd2-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="55cd2-161">Azure DevOps Services</span></span>

<span data-ttu-id="55cd2-162">Nakonfigurujte služby Azure DevOps services pro vytváření projektů .NET Core pomocí jednoho z těchto přístupů:</span><span class="sxs-lookup"><span data-stu-id="55cd2-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="55cd2-163">Spusťte skript z [kroku ručního nastavení](#manual-setup) pomocí příkazů.</span><span class="sxs-lookup"><span data-stu-id="55cd2-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="55cd2-164">Vytvořte sestavení složené z několika předdefinovaných úloh sestavení služby Azure DevOps Services, které jsou nakonfigurované pro použití nástrojů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55cd2-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="55cd2-165">Obě řešení jsou platná.</span><span class="sxs-lookup"><span data-stu-id="55cd2-165">Both solutions are valid.</span></span> <span data-ttu-id="55cd2-166">Pomocí skriptu ručního nastavení řídíte verzi nástrojů, které obdržíte, protože je stáhnete jako součást sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="55cd2-167">Sestavení je spuštěno ze skriptu, který je nutné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="55cd2-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="55cd2-168">Tento článek se vztahuje pouze na ruční možnost.</span><span class="sxs-lookup"><span data-stu-id="55cd2-168">This article only covers the manual option.</span></span> <span data-ttu-id="55cd2-169">Další informace o vytváření sestavení pomocí úloh sestavení služby Azure DevOps Services najdete v dokumentaci [k Azure Pipelines.](https://docs.microsoft.com/azure/devops/pipelines/index)</span><span class="sxs-lookup"><span data-stu-id="55cd2-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="55cd2-170">Chcete-li použít skript ručního nastavení ve službě Azure DevOps Services, vytvořte novou definici sestavení a zadejte skript, který se má spustit pro krok sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="55cd2-171">Toho se provádí pomocí uživatelského rozhraní služby Azure DevOps Services:</span><span class="sxs-lookup"><span data-stu-id="55cd2-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="55cd2-172">Začněte vytvořením nové definice sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-172">Start by creating a new build definition.</span></span> <span data-ttu-id="55cd2-173">Jakmile se dostanete na obrazovku, která vám poskytuje možnost definovat, jaký druh sestavení chcete vytvořit, vyberte možnost **Prázdné.**</span><span class="sxs-lookup"><span data-stu-id="55cd2-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Výběr prázdné definice sestavení](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="55cd2-175">Po konfiguraci úložiště k sestavení, budete přesměrováni na definice sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="55cd2-176">Vyberte **Přidat krok sestavení**:</span><span class="sxs-lookup"><span data-stu-id="55cd2-176">Select **Add build step**:</span></span>

   ![Přidání kroku sestavení](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="55cd2-178">Zobrazí se katalog **úkolů**.</span><span class="sxs-lookup"><span data-stu-id="55cd2-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="55cd2-179">Katalog obsahuje úkoly, které používáte v sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="55cd2-180">Vzhledem k tomu, že máte skript, vyberte tlačítko **Přidat** pro **PowerShell: Spuštění skriptu PowerShellu**.</span><span class="sxs-lookup"><span data-stu-id="55cd2-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Přidání kroku skriptu prostředí PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="55cd2-182">Nakonfigurujte krok sestavení.</span><span class="sxs-lookup"><span data-stu-id="55cd2-182">Configure the build step.</span></span> <span data-ttu-id="55cd2-183">Přidejte skript z úložiště, které vytváříte:</span><span class="sxs-lookup"><span data-stu-id="55cd2-183">Add the script from the repository that you're building:</span></span>

   ![Určení skriptu Prostředí PowerShell, který se má spustit](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="55cd2-185">Orchestrace sestavení</span><span class="sxs-lookup"><span data-stu-id="55cd2-185">Orchestrating the build</span></span>

<span data-ttu-id="55cd2-186">Většina tohoto dokumentu popisuje, jak získat nástroje .NET Core a konfigurovat různé služby CI bez poskytnutí informací o tom, jak organizovat nebo *skutečně sestavit*, váš kód s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55cd2-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="55cd2-187">Možnosti, jak strukturovat proces sestavení, závisí na mnoha faktorech, které zde nelze obecně pokrýt.</span><span class="sxs-lookup"><span data-stu-id="55cd2-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="55cd2-188">Další informace o orchestraci sestavení s každou technologií, prozkoumejte prostředky a ukázky uvedené v dokumentaci sady [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)a [Azure pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="55cd2-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="55cd2-189">Dva obecné přístupy, které budete mít při strukturování procesu sestavení pro kód .NET Core pomocí nástrojů .NET Core používají msbuild přímo nebo pomocí příkazů příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55cd2-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="55cd2-190">Jaký přístup byste měli vzít, je určen vaší úrovně pohodlí s přístupy a kompromisy ve složitosti.</span><span class="sxs-lookup"><span data-stu-id="55cd2-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="55cd2-191">MSBuild poskytuje možnost vyjádřit proces sestavení jako úkoly a cíle, ale přichází s přidanou složitost učení MSBuild syntaxe souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="55cd2-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="55cd2-192">Použití nástrojů příkazového řádku .NET Core je možná jednodušší, ale vyžaduje, abyste `bash` zapisovali logiku orchestrace ve skriptovacím jazyce, jako je powershell nebo PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55cd2-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="55cd2-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="55cd2-193">See also</span></span>

- [<span data-ttu-id="55cd2-194">.NET ke stažení - Linux</span><span class="sxs-lookup"><span data-stu-id="55cd2-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
