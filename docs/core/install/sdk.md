---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné pro vývoj aplikací .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a11d1eb3bae6affaa548407cbd68c166a30e99da
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324657"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="00d00-104">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="00d00-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="00d00-105">V tomto článku se naučíte, jak nainstalovat .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="00d00-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="00d00-106">.NET Core SDK slouží k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00d00-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="00d00-107">Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="00d00-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="00d00-108">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="00d00-108">Install with an installer</span></span>

<span data-ttu-id="00d00-109">Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci sady .NET Core 3,1 SDK:</span><span class="sxs-lookup"><span data-stu-id="00d00-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="00d00-110">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="00d00-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="00d00-111">Procesory x86 (32 bitů)</span><span class="sxs-lookup"><span data-stu-id="00d00-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="00d00-112">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="00d00-112">Install with an installer</span></span>

<span data-ttu-id="00d00-113">macOS má samostatné instalační programy, které se dají použít k instalaci sady .NET Core 3,1 SDK:</span><span class="sxs-lookup"><span data-stu-id="00d00-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="00d00-114">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="00d00-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="00d00-115">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="00d00-115">Download and manually install</span></span>

<span data-ttu-id="00d00-116">Jako alternativu k instalačním modulům macOS pro .NET Core můžete sadu SDK stáhnout a nainstalovat ručně.</span><span class="sxs-lookup"><span data-stu-id="00d00-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="00d00-117">K extrakci sady SDK a zpřístupnění .NET Core CLI příkazů v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00d00-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="00d00-118">Pak otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="00d00-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="00d00-119">Předpokládá se, že se modul runtime stáhne do `~/Downloads/dotnet-sdk.pkg` souboru.</span><span class="sxs-lookup"><span data-stu-id="00d00-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="00d00-120">Instalace v systému Linux</span><span class="sxs-lookup"><span data-stu-id="00d00-120">Install on Linux</span></span>

<span data-ttu-id="00d00-121">Tento článek bude brzy odebrán.</span><span class="sxs-lookup"><span data-stu-id="00d00-121">This article will be removed soon.</span></span> <span data-ttu-id="00d00-122">V tuto chvíli se nahrazuje [instalací .NET Core v systému Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-122">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="00d00-123">Instalace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="00d00-123">Install with Visual Studio</span></span>

<span data-ttu-id="00d00-124">Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="00d00-124">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="00d00-125">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="00d00-125">.NET Core SDK version</span></span> | <span data-ttu-id="00d00-126">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="00d00-126">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="00d00-127">3.1</span><span class="sxs-lookup"><span data-stu-id="00d00-127">3.1</span></span>                   | <span data-ttu-id="00d00-128">Visual Studio 2019 verze 16,4 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="00d00-128">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="00d00-129">3.0</span><span class="sxs-lookup"><span data-stu-id="00d00-129">3.0</span></span>                   | <span data-ttu-id="00d00-130">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="00d00-130">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="00d00-131">2,2</span><span class="sxs-lookup"><span data-stu-id="00d00-131">2.2</span></span>                   | <span data-ttu-id="00d00-132">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="00d00-132">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="00d00-133">2.1</span><span class="sxs-lookup"><span data-stu-id="00d00-133">2.1</span></span>                   | <span data-ttu-id="00d00-134">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="00d00-134">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="00d00-135">Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="00d00-135">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="00d00-136">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="00d00-136">Open Visual Studio.</span></span>
01. <span data-ttu-id="00d00-137">Vyberte **nápovědu**  >  **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="00d00-137">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="00d00-138">Přečtěte si číslo verze v dialogovém okně **o produktu** .</span><span class="sxs-lookup"><span data-stu-id="00d00-138">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="00d00-139">Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="00d00-139">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="00d00-140">[Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="00d00-140">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="00d00-141">Vyberte úlohu.</span><span class="sxs-lookup"><span data-stu-id="00d00-141">Select a workload</span></span>

<span data-ttu-id="00d00-142">Při instalaci nebo úpravách sady Visual Studio vyberte jednu nebo více následujících úloh v závislosti na typu aplikace, kterou vytváříte:</span><span class="sxs-lookup"><span data-stu-id="00d00-142">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="00d00-143">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="00d00-143">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="00d00-144">Úlohy **vývoje ASP.NET a webu** v části **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="00d00-144">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="00d00-145">Úlohy **vývoje Azure** v části **Web & cloudu** .</span><span class="sxs-lookup"><span data-stu-id="00d00-145">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="00d00-146">Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="00d00-146">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="00d00-147">[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="00d00-147">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="00d00-148">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="00d00-148">Download and manually install</span></span>

<span data-ttu-id="00d00-149">Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00d00-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="00d00-150">Pak vytvořte adresář, do kterého chcete nainstalovat například `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="00d00-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="00d00-151">Nakonec Extrahujte stažený soubor zip do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="00d00-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="00d00-152">Ve výchozím nastavení nepoužívají .NET Core CLI příkazy a aplikace tímto způsobem nainstalované rozhraní .NET Core a musíte ho explicitně použít.</span><span class="sxs-lookup"><span data-stu-id="00d00-152">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="00d00-153">Provedete to tak, že změníte proměnné prostředí, se kterými je aplikace spuštěná:</span><span class="sxs-lookup"><span data-stu-id="00d00-153">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="00d00-154">Tento přístup umožňuje nainstalovat více verzí do samostatných umístění a pak explicitně zvolit umístění instalace, které by měla aplikace používat, a to spuštěním aplikace s proměnnými prostředí, které ukazují na toto umístění.</span><span class="sxs-lookup"><span data-stu-id="00d00-154">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="00d00-155">I v případě, že jsou tyto proměnné prostředí nastaveny, .NET Core při výběru nejlepšího rozhraní pro spuštění aplikace i nadále posuzuje výchozí globální umístění instalace.</span><span class="sxs-lookup"><span data-stu-id="00d00-155">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="00d00-156">Výchozí hodnota je obvykle `C:\Program Files\dotnet` , kterou instalační programy používají.</span><span class="sxs-lookup"><span data-stu-id="00d00-156">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="00d00-157">Modulu runtime můžete dát pokyn, aby používal pouze vlastní umístění instalace, a to nastavením této proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="00d00-157">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="00d00-158">Instalace pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="00d00-158">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="00d00-159">Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="00d00-159">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="00d00-160">Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="00d00-160">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="00d00-161">Pro nejnovější vydání .NET Core 3,1 je nutné použít Visual Studio pro Mac 8,4 Preview.</span><span class="sxs-lookup"><span data-stu-id="00d00-161">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="00d00-162">[![macOS Visual Studio 2019 for Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="00d00-162">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-windows,os-macos"

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="00d00-163">Nainstalovat společně Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="00d00-163">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="00d00-164">Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="00d00-164">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="00d00-165">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="00d00-165">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="00d00-166">I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="00d00-166">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="00d00-167">[Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="00d00-167">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="00d00-168">[Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="00d00-168">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="00d00-169">[Nainstalujte rozšíření C# z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="00d00-169">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="00d00-170">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="00d00-170">Install with PowerShell automation</span></span>

<span data-ttu-id="00d00-171">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="00d00-171">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="00d00-172">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-172">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="00d00-173">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="00d00-173">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="00d00-174">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="00d00-174">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="00d00-175">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="00d00-175">Install with bash automation</span></span>

<span data-ttu-id="00d00-176">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="00d00-176">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="00d00-177">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-177">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="00d00-178">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="00d00-178">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="00d00-179">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="00d00-179">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="00d00-180">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="00d00-180">All .NET Core downloads</span></span>

<span data-ttu-id="00d00-181">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="00d00-181">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="00d00-182">Soubory ke stažení pro .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="00d00-182">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="00d00-183">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="00d00-183">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="00d00-184">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="00d00-184">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="00d00-185">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="00d00-185">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="00d00-186">Docker</span><span class="sxs-lookup"><span data-stu-id="00d00-186">Docker</span></span>

<span data-ttu-id="00d00-187">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="00d00-187">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="00d00-188">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="00d00-188">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="00d00-189">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="00d00-189">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="00d00-190">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="00d00-190">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="00d00-191">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="00d00-191">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="00d00-192">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="00d00-192">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="00d00-193">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="00d00-193">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="00d00-194">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-194">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="00d00-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="00d00-195">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="00d00-196">[Kurz: kurz Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-196">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="00d00-197">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-197">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="00d00-198">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="00d00-198">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="00d00-199">[Práce s MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-199">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="00d00-200">[Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="00d00-201">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="00d00-202">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="00d00-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="00d00-203">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="00d00-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="00d00-204">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="00d00-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
