---
title: Using .NET Core SDK and tools in Continuous Integration (CI)
description: Information on the usage of the .NET Core SDK and its tools on the build server.
author: mairaw
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: 481d54904192ee82da1f9d34bbf62fa8ffe1cd3b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428591"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="07332-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span><span class="sxs-lookup"><span data-stu-id="07332-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="07332-104">This document outlines using the .NET Core SDK and its tools on a build server.</span><span class="sxs-lookup"><span data-stu-id="07332-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="07332-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span><span class="sxs-lookup"><span data-stu-id="07332-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="07332-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span><span class="sxs-lookup"><span data-stu-id="07332-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="07332-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span><span class="sxs-lookup"><span data-stu-id="07332-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="07332-108">Installation options for CI build servers</span><span class="sxs-lookup"><span data-stu-id="07332-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="07332-109">Using the native installers</span><span class="sxs-lookup"><span data-stu-id="07332-109">Using the native installers</span></span>

<span data-ttu-id="07332-110">Native installers are available for macOS, Linux, and Windows.</span><span class="sxs-lookup"><span data-stu-id="07332-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="07332-111">The installers require admin (sudo) access to the build server.</span><span class="sxs-lookup"><span data-stu-id="07332-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="07332-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span><span class="sxs-lookup"><span data-stu-id="07332-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="07332-113">Native installers also provide a system-wide installation of the SDK.</span><span class="sxs-lookup"><span data-stu-id="07332-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="07332-114">macOS users should use the PKG installers.</span><span class="sxs-lookup"><span data-stu-id="07332-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="07332-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span><span class="sxs-lookup"><span data-stu-id="07332-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="07332-116">On Windows, use the MSI installer.</span><span class="sxs-lookup"><span data-stu-id="07332-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="07332-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="07332-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="07332-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="07332-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="07332-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07332-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="07332-120">Using the installer script</span><span class="sxs-lookup"><span data-stu-id="07332-120">Using the installer script</span></span>

<span data-ttu-id="07332-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span><span class="sxs-lookup"><span data-stu-id="07332-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="07332-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span><span class="sxs-lookup"><span data-stu-id="07332-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="07332-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span><span class="sxs-lookup"><span data-stu-id="07332-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="07332-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span><span class="sxs-lookup"><span data-stu-id="07332-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="07332-125">The *desired version* is whatever version of the SDK your projects require to build.</span><span class="sxs-lookup"><span data-stu-id="07332-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="07332-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span><span class="sxs-lookup"><span data-stu-id="07332-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="07332-127">This provides encapsulation and isolation to your entire build process.</span><span class="sxs-lookup"><span data-stu-id="07332-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="07332-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span><span class="sxs-lookup"><span data-stu-id="07332-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="07332-129">**Služby Azure DevOps**</span><span class="sxs-lookup"><span data-stu-id="07332-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="07332-130">When using the installer script, native dependencies aren't installed automatically.</span><span class="sxs-lookup"><span data-stu-id="07332-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="07332-131">You must install the native dependencies if the operating system doesn't have them.</span><span class="sxs-lookup"><span data-stu-id="07332-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="07332-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="07332-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="07332-133">CI setup examples</span><span class="sxs-lookup"><span data-stu-id="07332-133">CI setup examples</span></span>

<span data-ttu-id="07332-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span><span class="sxs-lookup"><span data-stu-id="07332-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="07332-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="07332-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="07332-136">Manual setup</span><span class="sxs-lookup"><span data-stu-id="07332-136">Manual setup</span></span>

<span data-ttu-id="07332-137">Each SaaS service has its own methods for creating and configuring a build process.</span><span class="sxs-lookup"><span data-stu-id="07332-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="07332-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span><span class="sxs-lookup"><span data-stu-id="07332-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="07332-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span><span class="sxs-lookup"><span data-stu-id="07332-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="07332-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span><span class="sxs-lookup"><span data-stu-id="07332-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="07332-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span><span class="sxs-lookup"><span data-stu-id="07332-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="07332-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span><span class="sxs-lookup"><span data-stu-id="07332-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="07332-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span><span class="sxs-lookup"><span data-stu-id="07332-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="07332-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span><span class="sxs-lookup"><span data-stu-id="07332-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="07332-145">You provide the implementation for your build process at the end of the script.</span><span class="sxs-lookup"><span data-stu-id="07332-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="07332-146">The script acquires the tools and then executes your build process.</span><span class="sxs-lookup"><span data-stu-id="07332-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="07332-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span><span class="sxs-lookup"><span data-stu-id="07332-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="07332-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="07332-148">Travis CI</span></span>

<span data-ttu-id="07332-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span><span class="sxs-lookup"><span data-stu-id="07332-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="07332-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="07332-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="07332-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span><span class="sxs-lookup"><span data-stu-id="07332-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="07332-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span><span class="sxs-lookup"><span data-stu-id="07332-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="07332-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span><span class="sxs-lookup"><span data-stu-id="07332-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="07332-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span><span class="sxs-lookup"><span data-stu-id="07332-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="07332-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="07332-155">AppVeyor</span></span>

<span data-ttu-id="07332-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span><span class="sxs-lookup"><span data-stu-id="07332-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="07332-157">Other build images with different versions of the .NET Core SDK are available.</span><span class="sxs-lookup"><span data-stu-id="07332-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="07332-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span><span class="sxs-lookup"><span data-stu-id="07332-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="07332-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span><span class="sxs-lookup"><span data-stu-id="07332-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="07332-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="07332-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="07332-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="07332-161">Azure DevOps Services</span></span>

<span data-ttu-id="07332-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span><span class="sxs-lookup"><span data-stu-id="07332-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="07332-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span><span class="sxs-lookup"><span data-stu-id="07332-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="07332-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span><span class="sxs-lookup"><span data-stu-id="07332-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="07332-165">Both solutions are valid.</span><span class="sxs-lookup"><span data-stu-id="07332-165">Both solutions are valid.</span></span> <span data-ttu-id="07332-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span><span class="sxs-lookup"><span data-stu-id="07332-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="07332-167">The build is run from a script that you must create.</span><span class="sxs-lookup"><span data-stu-id="07332-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="07332-168">This article only covers the manual option.</span><span class="sxs-lookup"><span data-stu-id="07332-168">This article only covers the manual option.</span></span> <span data-ttu-id="07332-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span><span class="sxs-lookup"><span data-stu-id="07332-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="07332-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span><span class="sxs-lookup"><span data-stu-id="07332-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="07332-171">This is accomplished using the Azure DevOps Services user interface:</span><span class="sxs-lookup"><span data-stu-id="07332-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="07332-172">Start by creating a new build definition.</span><span class="sxs-lookup"><span data-stu-id="07332-172">Start by creating a new build definition.</span></span> <span data-ttu-id="07332-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span><span class="sxs-lookup"><span data-stu-id="07332-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Selecting an empty build definition](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="07332-175">After configuring the repository to build, you're directed to the build definitions.</span><span class="sxs-lookup"><span data-stu-id="07332-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="07332-176">Select **Add build step**:</span><span class="sxs-lookup"><span data-stu-id="07332-176">Select **Add build step**:</span></span>

   ![Adding a build step](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="07332-178">You're presented with the **Task catalog**.</span><span class="sxs-lookup"><span data-stu-id="07332-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="07332-179">The catalog contains tasks that you use in the build.</span><span class="sxs-lookup"><span data-stu-id="07332-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="07332-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span><span class="sxs-lookup"><span data-stu-id="07332-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Adding a PowerShell script step](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="07332-182">Configure the build step.</span><span class="sxs-lookup"><span data-stu-id="07332-182">Configure the build step.</span></span> <span data-ttu-id="07332-183">Add the script from the repository that you're building:</span><span class="sxs-lookup"><span data-stu-id="07332-183">Add the script from the repository that you're building:</span></span>

   ![Specifying the PowerShell script to run](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="07332-185">Orchestrating the build</span><span class="sxs-lookup"><span data-stu-id="07332-185">Orchestrating the build</span></span>

<span data-ttu-id="07332-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07332-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="07332-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span><span class="sxs-lookup"><span data-stu-id="07332-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="07332-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="07332-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="07332-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span><span class="sxs-lookup"><span data-stu-id="07332-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="07332-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span><span class="sxs-lookup"><span data-stu-id="07332-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="07332-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span><span class="sxs-lookup"><span data-stu-id="07332-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="07332-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07332-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="07332-193">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07332-193">See also</span></span>

- [<span data-ttu-id="07332-194">.NET downloads - Linux</span><span class="sxs-lookup"><span data-stu-id="07332-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
