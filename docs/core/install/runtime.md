---
title: Instalace modulu runtime .NET Core v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné ke spouštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d36909e06bd9a3de0940c4c1b2b9eacbf9cafe7f
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740589"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="f4b32-104">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="f4b32-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="f4b32-105">V tomto článku se dozvíte, jak stáhnout a nainstalovat modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4b32-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="f4b32-106">Modul runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4b32-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="f4b32-107">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="f4b32-107">Install with an installer</span></span>

<span data-ttu-id="f4b32-108">Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci modulu runtime .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="f4b32-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="f4b32-109">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="f4b32-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f4b32-110">Procesory x86 (32 bitů)</span><span class="sxs-lookup"><span data-stu-id="f4b32-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="f4b32-111">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="f4b32-111">Install with an installer</span></span>

<span data-ttu-id="f4b32-112">macOS má samostatné instalační programy, které se dají použít k instalaci modulu runtime .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="f4b32-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="f4b32-113">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="f4b32-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="f4b32-114">Instalace pomocí Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="f4b32-114">Install with a package manager</span></span>

<span data-ttu-id="f4b32-115">Modul runtime .NET Core můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux.</span><span class="sxs-lookup"><span data-stu-id="f4b32-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="f4b32-116">Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="f4b32-117">Instalace pomocí Správce balíčků se podporuje jenom v architektuře x64.</span><span class="sxs-lookup"><span data-stu-id="f4b32-117">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="f4b32-118">Pokud instalujete modul runtime .NET Core s jinou architekturou, jako je například ARM, postupujte podle pokynů v části [Stažení a ruční instalace](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="f4b32-118">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="f4b32-119">Další informace o podporovaných architekturách najdete v tématu [závislosti a požadavky .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-119">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="f4b32-120">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="f4b32-120">Download and manually install</span></span>

<span data-ttu-id="f4b32-121">Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4b32-121">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="f4b32-122">Pak otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="f4b32-122">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="f4b32-123">Předchozí příkazy `export` zpřístupňují pouze příkazy .NET Core CLI dostupné pro relaci terminálu, ve které byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f4b32-123">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="f4b32-124">Úpravou profilu prostředí můžete tyto příkazy trvale přidat.</span><span class="sxs-lookup"><span data-stu-id="f4b32-124">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="f4b32-125">K dispozici je řada různých prostředí pro Linux a každá má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="f4b32-125">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="f4b32-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f4b32-126">For example:</span></span>
>
> - <span data-ttu-id="f4b32-127">**Prostředí bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="f4b32-127">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="f4b32-128">**Korn shell**: *~/.KSHRC* nebo *. Profile*</span><span class="sxs-lookup"><span data-stu-id="f4b32-128">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="f4b32-129">**Prostředí Z**: *~/.zshrc* nebo *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="f4b32-129">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="f4b32-130">Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího příkazu `PATH`.</span><span class="sxs-lookup"><span data-stu-id="f4b32-130">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="f4b32-131">Pokud není zahrnutý žádný příkaz `PATH`, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="f4b32-131">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="f4b32-132">Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="f4b32-132">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="f4b32-133">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="f4b32-133">Install with PowerShell automation</span></span>

<span data-ttu-id="f4b32-134">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f4b32-134">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="f4b32-135">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-135">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f4b32-136">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="f4b32-136">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="f4b32-137">Konkrétní vydání můžete zvolit zadáním přepínače `Channel`.</span><span class="sxs-lookup"><span data-stu-id="f4b32-137">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="f4b32-138">Pokud chcete nainstalovat modul runtime, přidejte přepínač `Runtime`.</span><span class="sxs-lookup"><span data-stu-id="f4b32-138">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="f4b32-139">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-139">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="f4b32-140">Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla.</span><span class="sxs-lookup"><span data-stu-id="f4b32-140">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="f4b32-141">Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4b32-141">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="f4b32-142">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="f4b32-142">Install with bash automation</span></span>

<span data-ttu-id="f4b32-143">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f4b32-143">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="f4b32-144">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-144">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f4b32-145">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="f4b32-145">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="f4b32-146">Konkrétní vydání můžete zvolit zadáním přepínače `current`.</span><span class="sxs-lookup"><span data-stu-id="f4b32-146">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="f4b32-147">Pokud chcete nainstalovat modul runtime, přidejte přepínač `runtime`.</span><span class="sxs-lookup"><span data-stu-id="f4b32-147">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="f4b32-148">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-148">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="f4b32-149">Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla.</span><span class="sxs-lookup"><span data-stu-id="f4b32-149">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="f4b32-150">Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4b32-150">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="f4b32-151">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="f4b32-151">All .NET Core downloads</span></span>

<span data-ttu-id="f4b32-152">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="f4b32-152">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="f4b32-153">Soubory ke stažení pro .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f4b32-153">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f4b32-154">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="f4b32-154">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="f4b32-155">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="f4b32-155">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="f4b32-156">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="f4b32-156">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="f4b32-157">Docker</span><span class="sxs-lookup"><span data-stu-id="f4b32-157">Docker</span></span>

<span data-ttu-id="f4b32-158">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="f4b32-158">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="f4b32-159">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="f4b32-159">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="f4b32-160">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="f4b32-160">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="f4b32-161">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="f4b32-161">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="f4b32-162">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="f4b32-162">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="f4b32-163">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="f4b32-163">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="f4b32-164">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="f4b32-164">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="f4b32-165">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-165">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f4b32-166">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f4b32-166">Next steps</span></span>

- <span data-ttu-id="f4b32-167">[Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f4b32-167">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
