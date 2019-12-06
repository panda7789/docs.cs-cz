---
title: Instalace modulu runtime .NET Core v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné ke spouštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 8f4a895ad66dea3063a32f785e4c521196266978
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835726"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="a4748-104">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="a4748-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="a4748-105">V tomto článku se dozvíte, jak stáhnout a nainstalovat modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4748-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="a4748-106">Modul runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4748-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="a4748-107">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="a4748-107">Install with an installer</span></span>

<span data-ttu-id="a4748-108">Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci modulu runtime .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="a4748-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="a4748-109">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="a4748-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="a4748-110">Procesory x86 (32 bitů)</span><span class="sxs-lookup"><span data-stu-id="a4748-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="a4748-111">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="a4748-111">Install with an installer</span></span>

<span data-ttu-id="a4748-112">macOS má samostatné instalační programy, které se dají použít k instalaci modulu runtime .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="a4748-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="a4748-113">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="a4748-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="a4748-114">Instalace pomocí Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="a4748-114">Install with a package manager</span></span>

<span data-ttu-id="a4748-115">Modul runtime .NET Core můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux.</span><span class="sxs-lookup"><span data-stu-id="a4748-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="a4748-116">Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="a4748-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="a4748-117">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="a4748-117">Install with PowerShell automation</span></span>

<span data-ttu-id="a4748-118">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a4748-118">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="a4748-119">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="a4748-119">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="a4748-120">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="a4748-120">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="a4748-121">Konkrétní vydání můžete zvolit zadáním přepínače `Channel`.</span><span class="sxs-lookup"><span data-stu-id="a4748-121">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="a4748-122">Pokud chcete nainstalovat modul runtime, přidejte přepínač `Runtime`.</span><span class="sxs-lookup"><span data-stu-id="a4748-122">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="a4748-123">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a4748-123">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="a4748-124">Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla.</span><span class="sxs-lookup"><span data-stu-id="a4748-124">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="a4748-125">Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4748-125">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="a4748-126">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="a4748-126">Install with bash automation</span></span>

<span data-ttu-id="a4748-127">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a4748-127">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="a4748-128">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="a4748-128">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="a4748-129">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="a4748-129">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="a4748-130">Konkrétní vydání můžete zvolit zadáním přepínače `current`.</span><span class="sxs-lookup"><span data-stu-id="a4748-130">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="a4748-131">Pokud chcete nainstalovat modul runtime, přidejte přepínač `runtime`.</span><span class="sxs-lookup"><span data-stu-id="a4748-131">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="a4748-132">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a4748-132">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="a4748-133">Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla.</span><span class="sxs-lookup"><span data-stu-id="a4748-133">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="a4748-134">Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4748-134">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="a4748-135">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="a4748-135">All .NET Core downloads</span></span>

<span data-ttu-id="a4748-136">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="a4748-136">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="a4748-137">Soubory ke stažení pro .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="a4748-137">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="a4748-138">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="a4748-138">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="a4748-139">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="a4748-139">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="a4748-140">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="a4748-140">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="a4748-141">Docker</span><span class="sxs-lookup"><span data-stu-id="a4748-141">Docker</span></span>

<span data-ttu-id="a4748-142">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="a4748-142">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="a4748-143">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="a4748-143">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="a4748-144">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="a4748-144">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="a4748-145">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="a4748-145">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="a4748-146">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="a4748-146">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="a4748-147">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="a4748-147">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="a4748-148">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="a4748-148">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="a4748-149">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="a4748-149">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a4748-150">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a4748-150">Next steps</span></span>

- <span data-ttu-id="a4748-151">[Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a4748-151">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
