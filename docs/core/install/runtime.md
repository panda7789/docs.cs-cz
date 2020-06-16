---
title: Instalace modulu runtime .NET Core v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné ke spouštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d3f7083366e2019d01884b5dff6e60d05ed565dd
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768284"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="02d7e-104">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="02d7e-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="02d7e-105">V tomto článku se dozvíte, jak stáhnout a nainstalovat modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02d7e-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="02d7e-106">Modul runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02d7e-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="02d7e-107">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="02d7e-107">Install with an installer</span></span>

<span data-ttu-id="02d7e-108">Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci modulu runtime .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="02d7e-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="02d7e-109">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="02d7e-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="02d7e-110">Procesory x86 (32 bitů)</span><span class="sxs-lookup"><span data-stu-id="02d7e-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="02d7e-111">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="02d7e-111">Install with an installer</span></span>

<span data-ttu-id="02d7e-112">macOS má samostatné instalační programy, které se dají použít k instalaci modulu runtime .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="02d7e-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="02d7e-113">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="02d7e-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="02d7e-114">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="02d7e-114">Download and manually install</span></span>

<span data-ttu-id="02d7e-115">Jako alternativu pro instalační programy macOS pro .NET Core můžete stáhnout a ručně nainstalovat modul runtime.</span><span class="sxs-lookup"><span data-stu-id="02d7e-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="02d7e-116">Chcete-li nainstalovat modul runtime a povolit příkazy .NET Core CLI k dispozici v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02d7e-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="02d7e-117">Pak otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="02d7e-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="02d7e-118">Předpokládá se, že se modul runtime stáhne do `~/Downloads/dotnet-runtime.pkg` souboru.</span><span class="sxs-lookup"><span data-stu-id="02d7e-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="02d7e-119">Instalace v systému Linux</span><span class="sxs-lookup"><span data-stu-id="02d7e-119">Install on Linux</span></span>

<span data-ttu-id="02d7e-120">Tento článek bude brzy odebrán.</span><span class="sxs-lookup"><span data-stu-id="02d7e-120">This article will be removed soon.</span></span> <span data-ttu-id="02d7e-121">V tuto chvíli se nahrazuje [instalací .NET Core v systému Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="02d7e-121">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="02d7e-122">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="02d7e-122">Install with PowerShell automation</span></span>

<span data-ttu-id="02d7e-123">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="02d7e-123">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="02d7e-124">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="02d7e-124">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="02d7e-125">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="02d7e-125">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="02d7e-126">Konkrétní vydání můžete zvolit zadáním `Channel` přepínače.</span><span class="sxs-lookup"><span data-stu-id="02d7e-126">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="02d7e-127">Zahrňte `Runtime` přepínač pro instalaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="02d7e-127">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="02d7e-128">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="02d7e-128">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="02d7e-129">Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla.</span><span class="sxs-lookup"><span data-stu-id="02d7e-129">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="02d7e-130">Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02d7e-130">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="02d7e-131">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="02d7e-131">Download and manually install</span></span>

<span data-ttu-id="02d7e-132">Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02d7e-132">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="02d7e-133">Pak vytvořte adresář, do kterého chcete nainstalovat například `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="02d7e-133">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="02d7e-134">Nakonec Extrahujte stažený soubor zip do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="02d7e-134">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="02d7e-135">Ve výchozím nastavení nepoužívají .NET Core CLI příkazy a aplikace tímto způsobem nainstalované rozhraní .NET Core a musíte ho explicitně použít.</span><span class="sxs-lookup"><span data-stu-id="02d7e-135">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="02d7e-136">Provedete to tak, že změníte proměnné prostředí, se kterými je aplikace spuštěná:</span><span class="sxs-lookup"><span data-stu-id="02d7e-136">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="02d7e-137">Tento přístup umožňuje nainstalovat více verzí do samostatných umístění a pak explicitně zvolit umístění instalace, které by měla aplikace používat, a to spuštěním aplikace s proměnnými prostředí, které ukazují na toto umístění.</span><span class="sxs-lookup"><span data-stu-id="02d7e-137">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="02d7e-138">I v případě, že jsou tyto proměnné prostředí nastaveny, .NET Core při výběru nejlepšího rozhraní pro spuštění aplikace i nadále posuzuje výchozí globální umístění instalace.</span><span class="sxs-lookup"><span data-stu-id="02d7e-138">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="02d7e-139">Výchozí hodnota je obvykle `C:\Program Files\dotnet` , kterou instalační programy používají.</span><span class="sxs-lookup"><span data-stu-id="02d7e-139">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="02d7e-140">Modulu runtime můžete dát pokyn, aby používal pouze vlastní umístění instalace, a to nastavením této proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="02d7e-140">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="02d7e-141">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="02d7e-141">Install with bash automation</span></span>

<span data-ttu-id="02d7e-142">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="02d7e-142">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="02d7e-143">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="02d7e-143">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="02d7e-144">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="02d7e-144">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="02d7e-145">Konkrétní vydání můžete zvolit zadáním `current` přepínače.</span><span class="sxs-lookup"><span data-stu-id="02d7e-145">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="02d7e-146">Zahrňte `runtime` přepínač pro instalaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="02d7e-146">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="02d7e-147">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="02d7e-147">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="02d7e-148">Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla.</span><span class="sxs-lookup"><span data-stu-id="02d7e-148">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="02d7e-149">Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02d7e-149">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="02d7e-150">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="02d7e-150">All .NET Core downloads</span></span>

<span data-ttu-id="02d7e-151">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="02d7e-151">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="02d7e-152">Soubory ke stažení pro .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="02d7e-152">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="02d7e-153">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="02d7e-153">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="02d7e-154">Docker</span><span class="sxs-lookup"><span data-stu-id="02d7e-154">Docker</span></span>

<span data-ttu-id="02d7e-155">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="02d7e-155">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="02d7e-156">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="02d7e-156">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="02d7e-157">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="02d7e-157">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="02d7e-158">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="02d7e-158">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="02d7e-159">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="02d7e-159">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="02d7e-160">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="02d7e-160">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="02d7e-161">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="02d7e-161">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="02d7e-162">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="02d7e-162">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="02d7e-163">Další kroky</span><span class="sxs-lookup"><span data-stu-id="02d7e-163">Next steps</span></span>

- <span data-ttu-id="02d7e-164">[Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="02d7e-164">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
