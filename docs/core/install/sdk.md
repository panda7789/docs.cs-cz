---
title: Instalace sady .NET Core SDK ve Windows, Linuxu a macOS - .NET Core
description: Přečtěte si, jak nainstalovat jádro .NET do Windows, Linuxu a macOS. Seznamte se s závislostimi potřebnými k vývoji aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399005"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="5e6ff-104">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="5e6ff-105">V tomto článku se dozvíte, jak nainstalovat sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="5e6ff-106">Sada .NET Core SDK se používá k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="5e6ff-107">Runtime jádra .NET je vždy nainstalován s sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="5e6ff-108">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="5e6ff-108">Install with an installer</span></span>

<span data-ttu-id="5e6ff-109">Systém Windows má samostatné instalační programy, které lze použít k instalaci sady .NET Core 3.1 SDK:</span><span class="sxs-lookup"><span data-stu-id="5e6ff-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="5e6ff-110">procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="5e6ff-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="5e6ff-111">x86 (32bitové) procesory</span><span class="sxs-lookup"><span data-stu-id="5e6ff-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="5e6ff-112">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="5e6ff-112">Install with an installer</span></span>

<span data-ttu-id="5e6ff-113">macOS má samostatné instalační programy, které lze použít k instalaci sady .NET Core 3.1 SDK:</span><span class="sxs-lookup"><span data-stu-id="5e6ff-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="5e6ff-114">procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="5e6ff-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="5e6ff-115">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="5e6ff-115">Download and manually install</span></span>

<span data-ttu-id="5e6ff-116">Jako alternativu k instalačním programům macOS pro .NET Core můžete stáhnout a ručně nainstalovat sdk.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="5e6ff-117">Chcete-li extrahovat sadu SDK a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="5e6ff-118">Potom otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="5e6ff-119">Předpokládá se, že runtime je `~/Downloads/dotnet-sdk.pkg` stažen do souboru.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="5e6ff-120">Instalace pomocí správce balíčků</span><span class="sxs-lookup"><span data-stu-id="5e6ff-120">Install with a package manager</span></span>

<span data-ttu-id="5e6ff-121">Sada .NET Core SDK můžete nainstalovat s mnoha běžnými správci balíčků Linuxu.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="5e6ff-122">Další informace naleznete v [tématu Linux Package Manager - Install .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="5e6ff-123">Instalace se správcem balíčků je podporována pouze na architektuře x64.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="5e6ff-124">Pokud instalujete sdk .NET Core SDK s jinou architekturou, jako je arm, postupujte podle pokynů [ke stažení a ručně nainstalujte](#download-and-manually-install) níže.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="5e6ff-125">Další informace o podporovaných architekturách naleznete v [tématu .NET Core závislosti a požadavky](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="5e6ff-126">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="5e6ff-126">Download and manually install</span></span>

<span data-ttu-id="5e6ff-127">Chcete-li extrahovat sadu SDK a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="5e6ff-128">Potom otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="5e6ff-129">Předchozí `export` příkazy zpřístupní pouze příkazy rozhraní PŘÍKAZU KONT .NET Core pro terminálovou relaci, ve které bylo spuštěno.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="5e6ff-130">Chcete-li trvale přidat příkazy, můžete upravit profil prostředí.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="5e6ff-131">Existuje celá řada různých shellů k dispozici pro Linux a každý má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="5e6ff-132">Například:</span><span class="sxs-lookup"><span data-stu-id="5e6ff-132">For example:</span></span>
>
> - <span data-ttu-id="5e6ff-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="5e6ff-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="5e6ff-134">**Korn Shell**: *~/.kshrc* nebo *.profil*</span><span class="sxs-lookup"><span data-stu-id="5e6ff-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="5e6ff-135">**Z Shell**: *~/.zshrc* nebo *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="5e6ff-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="5e6ff-136">Upravte příslušný zdrojový soubor prostředí `:$HOME/dotnet` a přidejte `PATH` na konec existujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="5e6ff-137">Pokud `PATH` není zahrnut žádný příkaz, `export PATH=$PATH:$HOME/dotnet`přidejte nový řádek s .</span><span class="sxs-lookup"><span data-stu-id="5e6ff-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="5e6ff-138">Také přidejte `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="5e6ff-139">Instalace pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e6ff-139">Install with Visual Studio</span></span>

<span data-ttu-id="5e6ff-140">Pokud používáte Visual Studio k vývoji aplikací .NET Core, následující tabulka popisuje minimální požadovanou verzi sady Visual Studio založenou na cílové verzi sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="5e6ff-141">Verze sady .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5e6ff-141">.NET Core SDK version</span></span> | <span data-ttu-id="5e6ff-142">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e6ff-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="5e6ff-143">3.1</span><span class="sxs-lookup"><span data-stu-id="5e6ff-143">3.1</span></span>                   | <span data-ttu-id="5e6ff-144">Visual Studio 2019 verze 16.4 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="5e6ff-145">3.0</span><span class="sxs-lookup"><span data-stu-id="5e6ff-145">3.0</span></span>                   | <span data-ttu-id="5e6ff-146">Visual Studio 2019 verze 16.3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="5e6ff-147">2,2</span><span class="sxs-lookup"><span data-stu-id="5e6ff-147">2.2</span></span>                   | <span data-ttu-id="5e6ff-148">Visual Studio 2017 verze 15.9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="5e6ff-149">2.1</span><span class="sxs-lookup"><span data-stu-id="5e6ff-149">2.1</span></span>                   | <span data-ttu-id="5e6ff-150">Visual Studio 2017 verze 15.7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="5e6ff-151">Pokud už máte nainstalovaný Visual Studio, můžete zkontrolovat verzi pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="5e6ff-152">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="5e6ff-153">Vyberte **nápovědu k** > **aplikaci Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="5e6ff-154">Přečtěte si číslo verze v dialogovém okně **Informace.**</span><span class="sxs-lookup"><span data-stu-id="5e6ff-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="5e6ff-155">Visual Studio můžete nainstalovat nejnovější .NET Core SDK a runtime.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="5e6ff-156">[Stáhnout visual studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="5e6ff-157">Výběr pracovního vytížení</span><span class="sxs-lookup"><span data-stu-id="5e6ff-157">Select a workload</span></span>

<span data-ttu-id="5e6ff-158">Při instalaci nebo úpravě sady Visual Studio vyberte jednu nebo více následujících úloh v závislosti na druhu vytvářené aplikace:</span><span class="sxs-lookup"><span data-stu-id="5e6ff-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="5e6ff-159">Úloha **vývoje napříč platformami .NET Core** v části **Ostatní sady nástrojů.**</span><span class="sxs-lookup"><span data-stu-id="5e6ff-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="5e6ff-160">**Úloha ASP.NET a vývoj webových** aplikací v části **Web & Cloud.**</span><span class="sxs-lookup"><span data-stu-id="5e6ff-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="5e6ff-161">Úloha **vývoje Azure** v části **Web & Cloud.**</span><span class="sxs-lookup"><span data-stu-id="5e6ff-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="5e6ff-162">Úloha **vývoje plochy .NET** v části **Desktop & Mobile.**</span><span class="sxs-lookup"><span data-stu-id="5e6ff-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="5e6ff-163">[![Windows Visual Studio 2019 s úlohami jádra .NET](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="5e6ff-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="5e6ff-164">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="5e6ff-164">Download and manually install</span></span>

<span data-ttu-id="5e6ff-165">Chcete-li extrahovat runtime a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="5e6ff-166">Potom vytvořte adresář, do který `%USERPROFILE%\dotnet`se chcete nainstalovat, například .</span><span class="sxs-lookup"><span data-stu-id="5e6ff-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="5e6ff-167">Nakonec extrahujte stažený soubor zip do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="5e6ff-168">Ve výchozím nastavení nebudou příkazy a aplikace rozhraní .NET Core CLI používat tímto způsobem nainstalované .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="5e6ff-169">Musíte explicitně zvolit jeho použití.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="5e6ff-170">Chcete-li tak učinit, změňte proměnné prostředí, se kterými je aplikace spuštěna:</span><span class="sxs-lookup"><span data-stu-id="5e6ff-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="5e6ff-171">Tento přístup umožňuje nainstalovat více verzí do samostatných umístění, pak explicitně zvolit, které umístění instalace aplikace by měla používat spuštěním aplikace s proměnnými prostředí ukazující na toto umístění.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="5e6ff-172">I když jsou tyto proměnné prostředí nastaveny, .NET Core stále považuje výchozí globální umístění instalace při výběru nejlepší rozhraní pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="5e6ff-173">Výchozí hodnota je `C:\Program Files\dotnet`obvykle , které instalační programy používají.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="5e6ff-174">Můžete dát pokyn, aby runtime používal pouze vlastní umístění instalace nastavením této proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="5e6ff-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="5e6ff-175">Instalace pomocí Visual Studia pro Mac</span><span class="sxs-lookup"><span data-stu-id="5e6ff-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="5e6ff-176">Visual Studio pro Mac nainstaluje sdk jádra .NET, když je vybráno zatížení **jádra .NET.**</span><span class="sxs-lookup"><span data-stu-id="5e6ff-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="5e6ff-177">Pokud chcete začít s vývojem jádra .NET v macOS, přečtěte si informace [o instalaci Visual Studia 2019 pro Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="5e6ff-178">Pro nejnovější verzi .NET Core 3.1, musíte použít Visual Studio pro Mac 8.4 Náhled.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="5e6ff-179">[![macOS Visual Studio 2019 pro Mac s funkcí zatížení Jádra .NET](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="5e6ff-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="5e6ff-180">Instalace vedle kódu sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e6ff-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="5e6ff-181">Visual Studio Code je výkonný a lehký editor zdrojového kódu, který běží na ploše.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="5e6ff-182">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="5e6ff-183">Zatímco Visual Studio Code nepřichází s automatickou instalační službou .NET Core, jako je visual studio, přidání podpory .NET Core je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="5e6ff-184">[Stáhněte a nainstalujte kód sady Visual Studio](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="5e6ff-185">[Stáhněte a nainstalujte sadu .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="5e6ff-186">[Nainstalujte rozšíření C# ze tržiště kódu sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="5e6ff-187">Instalace s automatizací Prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e6ff-187">Install with PowerShell automation</span></span>

<span data-ttu-id="5e6ff-188">Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace sady SDK bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="5e6ff-189">Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="5e6ff-190">Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="5e6ff-191">Chcete-li nainstalovat aktuální verzi rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="5e6ff-192">Instalace s automatizací bash</span><span class="sxs-lookup"><span data-stu-id="5e6ff-192">Install with bash automation</span></span>

<span data-ttu-id="5e6ff-193">Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace sady SDK bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="5e6ff-194">Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="5e6ff-195">Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="5e6ff-196">Chcete-li nainstalovat aktuální verzi rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="5e6ff-197">Všechny soubory ke stažení .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e6ff-197">All .NET Core downloads</span></span>

<span data-ttu-id="5e6ff-198">Můžete si stáhnout a nainstalovat .NET Core přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="5e6ff-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="5e6ff-199">Soubor ke stažení .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5e6ff-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="5e6ff-200">Soubor ke stažení .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5e6ff-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="5e6ff-201">Soubor ke stažení .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5e6ff-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="5e6ff-202">Soubor ke stažení .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5e6ff-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="5e6ff-203">Docker</span><span class="sxs-lookup"><span data-stu-id="5e6ff-203">Docker</span></span>

<span data-ttu-id="5e6ff-204">Kontejnery poskytují lehký způsob, jak izolovat aplikace od zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="5e6ff-205">Kontejnery na stejném počítači sdílejí pouze jádro a používají prostředky dané vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="5e6ff-206">Jádro .NET lze spustit v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="5e6ff-207">Oficiální image .NET Core Docker umožnou v registru Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="5e6ff-208">Každé úložiště obsahuje obrázky pro různé kombinace .NET (SDK nebo Runtime) a Operačního serveru, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="5e6ff-209">Společnost Microsoft poskytuje obrázky, které jsou přizpůsobeny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="5e6ff-210">[Například úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje image, které jsou vytvořené pro spouštění aplikací ASP.NET Core v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="5e6ff-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="5e6ff-211">Další informace o použití .NET Core v kontejneru Dockeru najdete v [tématu Úvod do .NET a Docker](../docker/introduction.md) a [ukázky](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5e6ff-212">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5e6ff-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="5e6ff-213">[Výukový program: Hello World tutorial](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="5e6ff-214">[Kurz: Vytvoření nové aplikace s visual studio kód](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="5e6ff-215">[Kurz: Kontejnerize .NET Core aplikace](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="5e6ff-216">[Práce s notářizací macOS Catalina](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="5e6ff-217">[Kurz: Začínáme s macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="5e6ff-218">[Kurz: Vytvoření nové aplikace s visual studio kód](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="5e6ff-219">[Kurz: Kontejnerize .NET Core aplikace](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="5e6ff-220">[Kurz: Vytvoření nové aplikace s visual studio kód](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="5e6ff-221">[Kurz: Kontejnerize .NET Core aplikace](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="5e6ff-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
