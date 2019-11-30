---
title: Instalace modulu runtime .NET Core v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné ke spouštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: fbe9b9e12dc53d9ab6570299e03f2b0a8868fb53
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567270"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="36b4e-104">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="36b4e-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="36b4e-105">V tomto článku se dozvíte, jak stáhnout a nainstalovat modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36b4e-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="36b4e-106">Modul runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="36b4e-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="36b4e-107">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="36b4e-107">Install with an installer</span></span>

<span data-ttu-id="36b4e-108">Windows i macOS mají samostatné instalační programy, které je možné použít k instalaci modulu runtime .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="36b4e-108">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 runtime.</span></span>

- <span data-ttu-id="36b4e-109">Procesory Windows [x64 (64-bit)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | procesory [x86 (32 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="36b4e-109">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="36b4e-110">macOS [procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="36b4e-110">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="36b4e-111">Instalace pomocí Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="36b4e-111">Install with a package manager</span></span>

<span data-ttu-id="36b4e-112">Modul runtime .NET Core můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux.</span><span class="sxs-lookup"><span data-stu-id="36b4e-112">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="36b4e-113">Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="36b4e-113">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="36b4e-114">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="36b4e-114">Install with PowerShell automation</span></span>

<span data-ttu-id="36b4e-115">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="36b4e-115">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="36b4e-116">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="36b4e-116">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="36b4e-117">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="36b4e-117">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="36b4e-118">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core (3,0), spusťte skript s následujícím přepínačem:</span><span class="sxs-lookup"><span data-stu-id="36b4e-118">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="36b4e-119">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="36b4e-119">Install with bash automation</span></span>

<span data-ttu-id="36b4e-120">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="36b4e-120">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="36b4e-121">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="36b4e-121">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="36b4e-122">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="36b4e-122">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="36b4e-123">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core (3,0), spusťte skript s následujícím přepínačem:</span><span class="sxs-lookup"><span data-stu-id="36b4e-123">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="36b4e-124">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="36b4e-124">All .NET Core downloads</span></span>

<span data-ttu-id="36b4e-125">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="36b4e-125">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="36b4e-126">Soubory ke stažení pro .NET Core 3,1 Preview</span><span class="sxs-lookup"><span data-stu-id="36b4e-126">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="36b4e-127">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="36b4e-127">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="36b4e-128">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="36b4e-128">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="36b4e-129">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="36b4e-129">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="36b4e-130">Docker</span><span class="sxs-lookup"><span data-stu-id="36b4e-130">Docker</span></span>

<span data-ttu-id="36b4e-131">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="36b4e-131">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="36b4e-132">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="36b4e-132">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="36b4e-133">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="36b4e-133">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="36b4e-134">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="36b4e-134">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="36b4e-135">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="36b4e-135">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="36b4e-136">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="36b4e-136">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="36b4e-137">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="36b4e-137">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="36b4e-138">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="36b4e-138">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="36b4e-139">Další kroky</span><span class="sxs-lookup"><span data-stu-id="36b4e-139">Next steps</span></span>

- <span data-ttu-id="36b4e-140">[Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="36b4e-140">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
