---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Learn how to install .NET Core on Windows, Linux, and macOS. Discover the dependencies required to develop .NET Core apps.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 1f7efaedaa1a0be90f7b619f954bdf78eecafa07
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959834"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="f3b1f-104">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f3b1f-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="f3b1f-105">In this article, you'll learn how to install the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="f3b1f-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="f3b1f-107">The .NET Core runtime is always installed with the SDK.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="f3b1f-108">Install with an installer</span><span class="sxs-lookup"><span data-stu-id="f3b1f-108">Install with an installer</span></span>

<span data-ttu-id="f3b1f-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span><span class="sxs-lookup"><span data-stu-id="f3b1f-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="f3b1f-110">x64 (64-bit) CPUs</span><span class="sxs-lookup"><span data-stu-id="f3b1f-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f3b1f-111">x86 (32-bit) CPUs</span><span class="sxs-lookup"><span data-stu-id="f3b1f-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="f3b1f-112">Install with an installer</span><span class="sxs-lookup"><span data-stu-id="f3b1f-112">Install with an installer</span></span>

<span data-ttu-id="f3b1f-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span><span class="sxs-lookup"><span data-stu-id="f3b1f-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="f3b1f-114">x64 (64-bit) CPUs</span><span class="sxs-lookup"><span data-stu-id="f3b1f-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="f3b1f-115">Install with a package manager</span><span class="sxs-lookup"><span data-stu-id="f3b1f-115">Install with a package manager</span></span>

<span data-ttu-id="f3b1f-116">You can install the .NET Core SDK with many of the common Linux package managers.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="f3b1f-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="f3b1f-118">Download and manually install</span><span class="sxs-lookup"><span data-stu-id="f3b1f-118">Download and manually install</span></span>

<span data-ttu-id="f3b1f-119">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-119">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="f3b1f-120">Then, open a terminal and run the following commands.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-120">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="f3b1f-121">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-121">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="f3b1f-122">You can edit your shell profile to permanently add the commands.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-122">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="f3b1f-123">There are a number of different shells available for Linux and each has a different profile.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-123">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="f3b1f-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f3b1f-124">For example:</span></span>
>
> - <span data-ttu-id="f3b1f-125">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="f3b1f-125">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="f3b1f-126">**Korn Shell**: *~/.kshrc* or *.profile*</span><span class="sxs-lookup"><span data-stu-id="f3b1f-126">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="f3b1f-127">**Z Shell**: *~/.zshrc* or *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="f3b1f-127">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="f3b1f-128">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-128">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="f3b1f-129">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-129">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="f3b1f-130">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-130">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="f3b1f-131">Install with Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3b1f-131">Install with Visual Studio</span></span>

<span data-ttu-id="f3b1f-132">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-132">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="f3b1f-133">.NET Core SDK version</span><span class="sxs-lookup"><span data-stu-id="f3b1f-133">.NET Core SDK version</span></span> | <span data-ttu-id="f3b1f-134">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3b1f-134">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="f3b1f-135">3.1</span><span class="sxs-lookup"><span data-stu-id="f3b1f-135">3.1</span></span>                   | <span data-ttu-id="f3b1f-136">Visual Studio 2019 version 16.4 or higher.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-136">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="f3b1f-137">3,0</span><span class="sxs-lookup"><span data-stu-id="f3b1f-137">3.0</span></span>                   | <span data-ttu-id="f3b1f-138">Visual Studio 2019 version 16.3 or higher.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-138">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="f3b1f-139">2.2</span><span class="sxs-lookup"><span data-stu-id="f3b1f-139">2.2</span></span>                   | <span data-ttu-id="f3b1f-140">Visual Studio 2017 version 15.9 or higher.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-140">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="f3b1f-141">2.1</span><span class="sxs-lookup"><span data-stu-id="f3b1f-141">2.1</span></span>                   | <span data-ttu-id="f3b1f-142">Visual Studio 2017 version 15.7 or higher.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-142">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="f3b1f-143">If you already have Visual Studio installed, you can check your version with the following steps.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-143">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="f3b1f-144">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-144">Open Visual Studio.</span></span>
01. <span data-ttu-id="f3b1f-145">Select **Help** > **About Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-145">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="f3b1f-146">Read the version number from the **About** dialog.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-146">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="f3b1f-147">Visual Studio can install the latest .NET Core SDK and runtime.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-147">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="f3b1f-148">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-148">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="f3b1f-149">Select a workload</span><span class="sxs-lookup"><span data-stu-id="f3b1f-149">Select a workload</span></span>

<span data-ttu-id="f3b1f-150">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span><span class="sxs-lookup"><span data-stu-id="f3b1f-150">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="f3b1f-151">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-151">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="f3b1f-152">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-152">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f3b1f-153">The **Azure development** workload in the **Web & Cloud** section.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-153">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f3b1f-154">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-154">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="f3b1f-155">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="f3b1f-155">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="f3b1f-156">Install with Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="f3b1f-156">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="f3b1f-157">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-157">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="f3b1f-158">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-158">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="f3b1f-159">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-159">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="f3b1f-160">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="f3b1f-160">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="f3b1f-161">Install alongside Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f3b1f-161">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="f3b1f-162">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-162">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="f3b1f-163">Visual Studio Code is available for Windows, macOS, and Linux.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-163">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="f3b1f-164">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-164">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="f3b1f-165">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-165">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="f3b1f-166">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-166">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="f3b1f-167">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-167">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="f3b1f-168">Install with PowerShell automation</span><span class="sxs-lookup"><span data-stu-id="f3b1f-168">Install with PowerShell automation</span></span>

<span data-ttu-id="f3b1f-169">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-169">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="f3b1f-170">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-170">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f3b1f-171">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-171">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="f3b1f-172">To install the current release of .NET Core, run the script with the following switch.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-172">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="f3b1f-173">Install with bash automation</span><span class="sxs-lookup"><span data-stu-id="f3b1f-173">Install with bash automation</span></span>

<span data-ttu-id="f3b1f-174">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-174">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="f3b1f-175">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-175">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f3b1f-176">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-176">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="f3b1f-177">To install the current release of .NET Core, run the script with the following switch.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-177">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="f3b1f-178">All .NET Core downloads</span><span class="sxs-lookup"><span data-stu-id="f3b1f-178">All .NET Core downloads</span></span>

<span data-ttu-id="f3b1f-179">You can download and install .NET Core directly with one of the following links:</span><span class="sxs-lookup"><span data-stu-id="f3b1f-179">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="f3b1f-180">.NET Core 3.1 downloads</span><span class="sxs-lookup"><span data-stu-id="f3b1f-180">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f3b1f-181">.NET Core 3.0 downloads</span><span class="sxs-lookup"><span data-stu-id="f3b1f-181">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="f3b1f-182">.NET Core 2.2 downloads</span><span class="sxs-lookup"><span data-stu-id="f3b1f-182">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="f3b1f-183">.NET Core 2.1 downloads</span><span class="sxs-lookup"><span data-stu-id="f3b1f-183">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="f3b1f-184">Docker</span><span class="sxs-lookup"><span data-stu-id="f3b1f-184">Docker</span></span>

<span data-ttu-id="f3b1f-185">Containers provide a lightweight way to isolate your application from the rest of the host system.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-185">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="f3b1f-186">Containers on the same machine share just the kernel and use resources given to your application.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-186">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="f3b1f-187">.NET Core can run in a Docker container.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-187">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="f3b1f-188">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-188">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="f3b1f-189">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-189">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="f3b1f-190">Microsoft provides images that are tailored for specific scenarios.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-190">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="f3b1f-191">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span><span class="sxs-lookup"><span data-stu-id="f3b1f-191">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="f3b1f-192">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-192">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f3b1f-193">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f3b1f-193">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="f3b1f-194">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-194">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="f3b1f-195">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-195">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="f3b1f-196">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-196">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="f3b1f-197">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-197">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="f3b1f-198">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-198">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="f3b1f-199">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-199">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="f3b1f-200">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-200">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="f3b1f-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="f3b1f-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="f3b1f-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
