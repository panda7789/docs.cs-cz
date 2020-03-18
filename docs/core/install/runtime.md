---
title: Instalace runtime .NET Core ve Windows, Linuxu a macOS - .NET Core
description: Přečtěte si, jak nainstalovat jádro .NET do Windows, Linuxu a macOS. Seznamte se se závislostmi potřebnými ke spuštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399012"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="96a55-104">Instalace rozhraní .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="96a55-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="96a55-105">V tomto článku se dozvíte, jak stáhnout a nainstalovat zaběhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96a55-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="96a55-106">Runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96a55-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="96a55-107">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="96a55-107">Install with an installer</span></span>

<span data-ttu-id="96a55-108">Systém Windows má samostatné instalační programy, které lze použít k instalaci runtime .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="96a55-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="96a55-109">procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="96a55-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="96a55-110">x86 (32bitové) procesory</span><span class="sxs-lookup"><span data-stu-id="96a55-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="96a55-111">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="96a55-111">Install with an installer</span></span>

<span data-ttu-id="96a55-112">macOS má samostatné instalační programy, které lze použít k instalaci runtime .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="96a55-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="96a55-113">procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="96a55-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="96a55-114">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="96a55-114">Download and manually install</span></span>

<span data-ttu-id="96a55-115">Jako alternativu k instalačním programům macOS pro .NET Core můžete stáhnout a ručně nainstalovat runtime.</span><span class="sxs-lookup"><span data-stu-id="96a55-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="96a55-116">Chcete-li nainstalovat runtime a povolit příkazy rozhraní PŘÍKAZU .NET Core, které jsou k dispozici na terminálu, [nejprve stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96a55-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="96a55-117">Potom otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="96a55-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="96a55-118">Předpokládá se, že runtime je `~/Downloads/dotnet-runtime.pkg` stažen do souboru.</span><span class="sxs-lookup"><span data-stu-id="96a55-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="96a55-119">Instalace pomocí správce balíčků</span><span class="sxs-lookup"><span data-stu-id="96a55-119">Install with a package manager</span></span>

<span data-ttu-id="96a55-120">Runtime .NET Core Runtime můžete nainstalovat s mnoha běžnými správci balíčků Linuxu.</span><span class="sxs-lookup"><span data-stu-id="96a55-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="96a55-121">Další informace naleznete v [tématu Linux Package Manager - Install .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="96a55-122">Instalace se správcem balíčků je podporována pouze na architektuře x64.</span><span class="sxs-lookup"><span data-stu-id="96a55-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="96a55-123">Pokud instalujete rozhraní .NET Core Runtime s jinou architekturou, jako je arm, postupujte podle pokynů v části [Stáhnout a ručně nainstalovat.](#download-and-manually-install)</span><span class="sxs-lookup"><span data-stu-id="96a55-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="96a55-124">Další informace o podporovaných architekturách naleznete v [tématu .NET Core závislosti a požadavky](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="96a55-125">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="96a55-125">Download and manually install</span></span>

<span data-ttu-id="96a55-126">Chcete-li extrahovat runtime a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96a55-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="96a55-127">Potom otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="96a55-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="96a55-128">Předchozí `export` příkazy zpřístupní pouze příkazy rozhraní PŘÍKAZU KONT .NET Core pro terminálovou relaci, ve které bylo spuštěno.</span><span class="sxs-lookup"><span data-stu-id="96a55-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="96a55-129">Chcete-li trvale přidat příkazy, můžete upravit profil prostředí.</span><span class="sxs-lookup"><span data-stu-id="96a55-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="96a55-130">Existuje celá řada různých shellů k dispozici pro Linux a každý má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="96a55-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="96a55-131">Například:</span><span class="sxs-lookup"><span data-stu-id="96a55-131">For example:</span></span>
>
> - <span data-ttu-id="96a55-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="96a55-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="96a55-133">**Korn Shell**: *~/.kshrc* nebo *.profil*</span><span class="sxs-lookup"><span data-stu-id="96a55-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="96a55-134">**Z Shell**: *~/.zshrc* nebo *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="96a55-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="96a55-135">Upravte příslušný zdrojový soubor prostředí `:$HOME/dotnet` a přidejte `PATH` na konec existujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="96a55-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="96a55-136">Pokud `PATH` není zahrnut žádný příkaz, `export PATH=$PATH:$HOME/dotnet`přidejte nový řádek s .</span><span class="sxs-lookup"><span data-stu-id="96a55-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="96a55-137">Také přidejte `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="96a55-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="96a55-138">Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a explicitně zvolit, kterou z nich použít, kterou aplikací.</span><span class="sxs-lookup"><span data-stu-id="96a55-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="96a55-139">Instalace s automatizací Prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="96a55-139">Install with PowerShell automation</span></span>

<span data-ttu-id="96a55-140">Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace runtime bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="96a55-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="96a55-141">Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="96a55-142">Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="96a55-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="96a55-143">Určitou verzi můžete zvolit zadáním přepínače. `Channel`</span><span class="sxs-lookup"><span data-stu-id="96a55-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="96a55-144">Zahrňte `Runtime` přepínač pro instalaci runtime.</span><span class="sxs-lookup"><span data-stu-id="96a55-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="96a55-145">V opačném případě skript nainstaluje sadu [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="96a55-146">Výše uvedený příkaz nainstaluje ASP.NET core runtime pro maximální kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="96a55-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="96a55-147">ASP.NET Core runtime také obsahuje standardní .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="96a55-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="96a55-148">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="96a55-148">Download and manually install</span></span>

<span data-ttu-id="96a55-149">Chcete-li extrahovat runtime a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96a55-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="96a55-150">Potom vytvořte adresář, do který `%USERPROFILE%\dotnet`se chcete nainstalovat, například .</span><span class="sxs-lookup"><span data-stu-id="96a55-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="96a55-151">Nakonec extrahujte stažený soubor zip do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="96a55-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="96a55-152">Ve výchozím nastavení nebudou příkazy a aplikace rozhraní .NET Core CLI používat tímto způsobem nainstalované .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96a55-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="96a55-153">Musíte explicitně zvolit jeho použití.</span><span class="sxs-lookup"><span data-stu-id="96a55-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="96a55-154">Chcete-li tak učinit, změňte proměnné prostředí, se kterými je aplikace spuštěna:</span><span class="sxs-lookup"><span data-stu-id="96a55-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="96a55-155">Tento přístup umožňuje nainstalovat více verzí do samostatných umístění, pak explicitně zvolit, které umístění instalace aplikace by měla používat spuštěním aplikace s proměnnými prostředí ukazující na toto umístění.</span><span class="sxs-lookup"><span data-stu-id="96a55-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="96a55-156">I když jsou tyto proměnné prostředí nastaveny, .NET Core stále považuje výchozí globální umístění instalace při výběru nejlepší rozhraní pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="96a55-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="96a55-157">Výchozí hodnota je `C:\Program Files\dotnet`obvykle , které instalační programy používají.</span><span class="sxs-lookup"><span data-stu-id="96a55-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="96a55-158">Můžete dát pokyn, aby runtime používal pouze vlastní umístění instalace nastavením této proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="96a55-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="96a55-159">Instalace s automatizací bash</span><span class="sxs-lookup"><span data-stu-id="96a55-159">Install with bash automation</span></span>

<span data-ttu-id="96a55-160">Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace runtime bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="96a55-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="96a55-161">Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="96a55-162">Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="96a55-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="96a55-163">Určitou verzi můžete zvolit zadáním přepínače. `current`</span><span class="sxs-lookup"><span data-stu-id="96a55-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="96a55-164">Zahrňte `runtime` přepínač pro instalaci runtime.</span><span class="sxs-lookup"><span data-stu-id="96a55-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="96a55-165">V opačném případě skript nainstaluje sadu [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="96a55-166">Výše uvedený příkaz nainstaluje ASP.NET core runtime pro maximální kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="96a55-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="96a55-167">ASP.NET Core runtime také obsahuje standardní .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="96a55-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="96a55-168">Všechny soubory ke stažení .NET Core</span><span class="sxs-lookup"><span data-stu-id="96a55-168">All .NET Core downloads</span></span>

<span data-ttu-id="96a55-169">Můžete si stáhnout a nainstalovat .NET Core přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="96a55-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="96a55-170">Soubor ke stažení .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="96a55-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="96a55-171">Soubor ke stažení .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="96a55-171">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="96a55-172">Docker</span><span class="sxs-lookup"><span data-stu-id="96a55-172">Docker</span></span>

<span data-ttu-id="96a55-173">Kontejnery poskytují lehký způsob, jak izolovat aplikace od zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="96a55-173">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="96a55-174">Kontejnery na stejném počítači sdílejí pouze jádro a používají prostředky dané vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="96a55-174">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="96a55-175">Jádro .NET lze spustit v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="96a55-175">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="96a55-176">Oficiální image .NET Core Docker umožnou v registru Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="96a55-176">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="96a55-177">Každé úložiště obsahuje obrázky pro různé kombinace .NET (SDK nebo Runtime) a Operačního serveru, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="96a55-177">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="96a55-178">Společnost Microsoft poskytuje obrázky, které jsou přizpůsobeny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="96a55-178">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="96a55-179">[Například úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje image, které jsou vytvořené pro spouštění aplikací ASP.NET Core v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="96a55-179">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="96a55-180">Další informace o použití .NET Core v kontejneru Dockeru najdete v [tématu Úvod do .NET a Docker](../docker/introduction.md) a [ukázky](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-180">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="96a55-181">Další kroky</span><span class="sxs-lookup"><span data-stu-id="96a55-181">Next steps</span></span>

- <span data-ttu-id="96a55-182">[Jak zkontrolovat, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="96a55-182">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
