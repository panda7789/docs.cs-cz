---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné pro vývoj aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 0aa323533dd9136372c2bbc330c9c3056fdf428c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157568"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="9c09a-104">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="9c09a-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="9c09a-105">V tomto článku se naučíte, jak nainstalovat .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9c09a-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="9c09a-106">.NET Core SDK slouží k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c09a-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="9c09a-107">Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="9c09a-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="9c09a-108">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="9c09a-108">Install with an installer</span></span>

<span data-ttu-id="9c09a-109">Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci sady .NET Core 3,1 SDK:</span><span class="sxs-lookup"><span data-stu-id="9c09a-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9c09a-110">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="9c09a-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9c09a-111">Procesory x86 (32 bitů)</span><span class="sxs-lookup"><span data-stu-id="9c09a-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="9c09a-112">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="9c09a-112">Install with an installer</span></span>

<span data-ttu-id="9c09a-113">macOS má samostatné instalační programy, které se dají použít k instalaci sady .NET Core 3,1 SDK:</span><span class="sxs-lookup"><span data-stu-id="9c09a-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="9c09a-114">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="9c09a-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="9c09a-115">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="9c09a-115">Download and manually install</span></span>

<span data-ttu-id="9c09a-116">Jako alternativu k instalačním modulům macOS pro .NET Core můžete sadu SDK stáhnout a nainstalovat ručně.</span><span class="sxs-lookup"><span data-stu-id="9c09a-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="9c09a-117">K extrakci sady SDK a zpřístupnění .NET Core CLI příkazů v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c09a-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9c09a-118">Pak otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="9c09a-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="9c09a-119">Předpokládá se, že se modul runtime stáhne do souboru `~/Downloads/dotnet-sdk.pkg`.</span><span class="sxs-lookup"><span data-stu-id="9c09a-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="9c09a-120">Instalace pomocí Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="9c09a-120">Install with a package manager</span></span>

<span data-ttu-id="9c09a-121">.NET Core SDK můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux.</span><span class="sxs-lookup"><span data-stu-id="9c09a-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="9c09a-122">Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="9c09a-123">Instalace pomocí Správce balíčků se podporuje jenom v architektuře x64.</span><span class="sxs-lookup"><span data-stu-id="9c09a-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="9c09a-124">Pokud .NET Core SDK instalujete s jinou architekturou, jako je například ARM, postupujte podle pokynů níže v části [Stažení a ruční instalace](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="9c09a-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="9c09a-125">Další informace o podporovaných architekturách najdete v tématu [závislosti a požadavky .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9c09a-126">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="9c09a-126">Download and manually install</span></span>

<span data-ttu-id="9c09a-127">K extrakci sady SDK a zpřístupnění .NET Core CLI příkazů v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c09a-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9c09a-128">Pak otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="9c09a-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="9c09a-129">Předchozí příkazy `export` zpřístupňují pouze příkazy .NET Core CLI dostupné pro relaci terminálu, ve které byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9c09a-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="9c09a-130">Úpravou profilu prostředí můžete tyto příkazy trvale přidat.</span><span class="sxs-lookup"><span data-stu-id="9c09a-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="9c09a-131">K dispozici je řada různých prostředí pro Linux a každá má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="9c09a-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="9c09a-132">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9c09a-132">For example:</span></span>
>
> - <span data-ttu-id="9c09a-133">**Prostředí bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="9c09a-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="9c09a-134">**Korn shell**: *~/.KSHRC* nebo *. Profile*</span><span class="sxs-lookup"><span data-stu-id="9c09a-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="9c09a-135">**Prostředí Z**: *~/.zshrc* nebo *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="9c09a-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="9c09a-136">Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího příkazu `PATH`.</span><span class="sxs-lookup"><span data-stu-id="9c09a-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="9c09a-137">Pokud není zahrnutý žádný příkaz `PATH`, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="9c09a-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="9c09a-138">Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="9c09a-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="9c09a-139">Instalace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c09a-139">Install with Visual Studio</span></span>

<span data-ttu-id="9c09a-140">Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9c09a-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="9c09a-141">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="9c09a-141">.NET Core SDK version</span></span> | <span data-ttu-id="9c09a-142">Verze Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c09a-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="9c09a-143">3.1</span><span class="sxs-lookup"><span data-stu-id="9c09a-143">3.1</span></span>                   | <span data-ttu-id="9c09a-144">Visual Studio 2019 verze 16,4 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9c09a-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="9c09a-145">3.0</span><span class="sxs-lookup"><span data-stu-id="9c09a-145">3.0</span></span>                   | <span data-ttu-id="9c09a-146">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9c09a-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="9c09a-147">2.2</span><span class="sxs-lookup"><span data-stu-id="9c09a-147">2.2</span></span>                   | <span data-ttu-id="9c09a-148">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9c09a-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="9c09a-149">2.1</span><span class="sxs-lookup"><span data-stu-id="9c09a-149">2.1</span></span>                   | <span data-ttu-id="9c09a-150">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9c09a-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="9c09a-151">Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="9c09a-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="9c09a-152">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c09a-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="9c09a-153">Vyberte **nápovědu** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9c09a-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="9c09a-154">Přečtěte si číslo verze v dialogovém okně **o produktu** .</span><span class="sxs-lookup"><span data-stu-id="9c09a-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="9c09a-155">Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="9c09a-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="9c09a-156">[Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="9c09a-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="9c09a-157">Vyberte úlohu.</span><span class="sxs-lookup"><span data-stu-id="9c09a-157">Select a workload</span></span>

<span data-ttu-id="9c09a-158">Při instalaci nebo úpravách sady Visual Studio vyberte jednu nebo více následujících úloh v závislosti na typu aplikace, kterou vytváříte:</span><span class="sxs-lookup"><span data-stu-id="9c09a-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="9c09a-159">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="9c09a-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="9c09a-160">Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="9c09a-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9c09a-161">Úlohy **vývoje Azure** v části **web & cloudu** .</span><span class="sxs-lookup"><span data-stu-id="9c09a-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9c09a-162">Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="9c09a-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="9c09a-163">[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9c09a-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9c09a-164">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="9c09a-164">Download and manually install</span></span>

<span data-ttu-id="9c09a-165">Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c09a-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="9c09a-166">Pak vytvořte adresář, do kterého chcete nainstalovat, například `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="9c09a-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="9c09a-167">Nakonec Extrahujte stažený soubor zip do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="9c09a-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="9c09a-168">Ve výchozím nastavení nepoužívají .NET Core CLI příkazy a aplikace tímto způsobem instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c09a-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="9c09a-169">Musíte ho výslovně použít.</span><span class="sxs-lookup"><span data-stu-id="9c09a-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="9c09a-170">Provedete to tak, že změníte proměnné prostředí, se kterými je aplikace spuštěná:</span><span class="sxs-lookup"><span data-stu-id="9c09a-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="9c09a-171">Tento přístup umožňuje nainstalovat více verzí do samostatných umístění a pak explicitně zvolit umístění instalace, které by měla aplikace používat, a to spuštěním aplikace s proměnnými prostředí, které ukazují na toto umístění.</span><span class="sxs-lookup"><span data-stu-id="9c09a-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="9c09a-172">I v případě, že jsou tyto proměnné prostředí nastaveny, .NET Core při výběru nejlepšího rozhraní pro spuštění aplikace i nadále posuzuje výchozí globální umístění instalace.</span><span class="sxs-lookup"><span data-stu-id="9c09a-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="9c09a-173">Výchozí hodnota je obvykle `C:\Program Files\dotnet`, kterou instalační programy používají.</span><span class="sxs-lookup"><span data-stu-id="9c09a-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="9c09a-174">Modulu runtime můžete dát pokyn, aby používal pouze vlastní umístění instalace, a to nastavením této proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="9c09a-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="9c09a-175">Instalace pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="9c09a-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="9c09a-176">Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="9c09a-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="9c09a-177">Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="9c09a-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="9c09a-178">Pro nejnovější vydání .NET Core 3,1 je nutné použít Visual Studio pro Mac 8,4 Preview.</span><span class="sxs-lookup"><span data-stu-id="9c09a-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="9c09a-179">[![macOS sady Visual Studio 2019 pro Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9c09a-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="9c09a-180">Nainstalovat společně Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9c09a-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="9c09a-181">Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9c09a-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="9c09a-182">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="9c09a-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9c09a-183">I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="9c09a-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="9c09a-184">[Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="9c09a-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="9c09a-185">[Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="9c09a-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="9c09a-186">[Nainstalujte C# rozšíření z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="9c09a-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="9c09a-187">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="9c09a-187">Install with PowerShell automation</span></span>

<span data-ttu-id="9c09a-188">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="9c09a-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9c09a-189">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9c09a-190">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9c09a-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9c09a-191">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="9c09a-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="9c09a-192">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="9c09a-192">Install with bash automation</span></span>

<span data-ttu-id="9c09a-193">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="9c09a-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="9c09a-194">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9c09a-195">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9c09a-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9c09a-196">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="9c09a-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="9c09a-197">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c09a-197">All .NET Core downloads</span></span>

<span data-ttu-id="9c09a-198">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="9c09a-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="9c09a-199">Soubory ke stažení pro .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9c09a-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9c09a-200">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="9c09a-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="9c09a-201">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="9c09a-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="9c09a-202">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="9c09a-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="9c09a-203">Docker</span><span class="sxs-lookup"><span data-stu-id="9c09a-203">Docker</span></span>

<span data-ttu-id="9c09a-204">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="9c09a-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="9c09a-205">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="9c09a-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="9c09a-206">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="9c09a-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="9c09a-207">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="9c09a-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="9c09a-208">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="9c09a-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="9c09a-209">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="9c09a-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="9c09a-210">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9c09a-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="9c09a-211">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9c09a-212">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9c09a-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="9c09a-213">[Kurz: kurz Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="9c09a-214">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9c09a-215">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="9c09a-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="9c09a-216">[Práce s MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="9c09a-217">[Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="9c09a-218">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9c09a-219">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="9c09a-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="9c09a-220">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="9c09a-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9c09a-221">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="9c09a-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
