---
title: Instalace .NET Core na Ubuntu – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: eef724138f2b908bf8601a509d298a06e55fb13e
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324741"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="cd441-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cd441-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="cd441-104">Rozhraní .NET Core je podporováno v Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cd441-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="cd441-105">Tento článek popisuje, jak nainstalovat .NET Core na Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cd441-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="cd441-106">Pokud je verze Ubuntu mimo podporu, rozhraní .NET Core již není s touto verzí podporováno.</span><span class="sxs-lookup"><span data-stu-id="cd441-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="cd441-107">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="cd441-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="cd441-108">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="cd441-108">Supported distributions</span></span>

<span data-ttu-id="cd441-109">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Ubuntu, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="cd441-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="cd441-110">Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Ubuntu dosáhne konce životnosti](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="cd441-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="cd441-111">✔️ označuje, že je stále podporovaná verze Ubuntu nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd441-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="cd441-112">❌Indikuje, že verze Ubuntu nebo .NET Core není v této verzi Ubuntu podporována.</span><span class="sxs-lookup"><span data-stu-id="cd441-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="cd441-113">Pokud se ✔️á jak verze Ubuntu, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="cd441-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="cd441-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cd441-114">Ubuntu</span></span>                   | <span data-ttu-id="cd441-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd441-115">.NET Core 2.1</span></span> | <span data-ttu-id="cd441-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-116">.NET Core 3.1</span></span> | <span data-ttu-id="cd441-117">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="cd441-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="cd441-118">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="cd441-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="cd441-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-119">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-120">✔️ 3.1</span></span>        | <span data-ttu-id="cd441-121">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-122">✔️ [19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="cd441-122">✔️ [19.10](#1910-)</span></span>       | <span data-ttu-id="cd441-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-123">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-124">✔️ 3.1</span></span>        | <span data-ttu-id="cd441-125">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-126">❌[19,04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="cd441-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="cd441-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-127">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-128">✔️ 3.1</span></span>        | <span data-ttu-id="cd441-129">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-130">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="cd441-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="cd441-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-131">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-132">❌3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-132">❌ 3.1</span></span>        | <span data-ttu-id="cd441-133">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-134">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="cd441-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="cd441-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-135">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-136">✔️ 3.1</span></span>        | <span data-ttu-id="cd441-137">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-138">❌[17,10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="cd441-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="cd441-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-139">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-140">❌3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-140">❌ 3.1</span></span>        | <span data-ttu-id="cd441-141">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-142">❌[17,04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="cd441-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="cd441-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-143">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-144">❌3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-144">❌ 3.1</span></span>        | <span data-ttu-id="cd441-145">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-146">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="cd441-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="cd441-147">❌2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-147">❌ 2.1</span></span>        | <span data-ttu-id="cd441-148">❌3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-148">❌ 3.1</span></span>        | <span data-ttu-id="cd441-149">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cd441-150">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="cd441-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="cd441-151">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd441-151">✔️ 2.1</span></span>        | <span data-ttu-id="cd441-152">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd441-152">✔️ 3.1</span></span>        | <span data-ttu-id="cd441-153">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd441-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="cd441-154">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="cd441-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="cd441-155">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="cd441-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="cd441-156">3.0</span><span class="sxs-lookup"><span data-stu-id="cd441-156">3.0</span></span>
- <span data-ttu-id="cd441-157">2,2</span><span class="sxs-lookup"><span data-stu-id="cd441-157">2.2</span></span>
- <span data-ttu-id="cd441-158">2.0</span><span class="sxs-lookup"><span data-stu-id="cd441-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cd441-159">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="cd441-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="cd441-160">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cd441-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="cd441-161">19,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="cd441-161">19.10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="cd441-162">19,04❌</span><span class="sxs-lookup"><span data-stu-id="cd441-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="cd441-163">18,10❌</span><span class="sxs-lookup"><span data-stu-id="cd441-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="cd441-164">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cd441-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="cd441-165">17,10❌</span><span class="sxs-lookup"><span data-stu-id="cd441-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="cd441-166">17,04❌</span><span class="sxs-lookup"><span data-stu-id="cd441-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="cd441-167">16,10❌</span><span class="sxs-lookup"><span data-stu-id="cd441-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="cd441-168">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cd441-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="cd441-169">APT Update SDK nebo modul runtime</span><span class="sxs-lookup"><span data-stu-id="cd441-169">APT update SDK or runtime</span></span>

<span data-ttu-id="cd441-170">Když je k dispozici nová verze opravy pro .NET Core, můžete ji jednoduše upgradovat prostřednictvím APT pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="cd441-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="cd441-171">Řešení potíží s APT</span><span class="sxs-lookup"><span data-stu-id="cd441-171">APT troubleshooting</span></span>

<span data-ttu-id="cd441-172">V této části najdete informace o běžných chybách, ke kterým může dojít při použití APT k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd441-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="cd441-173">Nejde najít.</span><span class="sxs-lookup"><span data-stu-id="cd441-173">Unable to locate</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="cd441-174">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="cd441-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="cd441-175">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="cd441-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="cd441-176">Závislosti</span><span class="sxs-lookup"><span data-stu-id="cd441-176">Dependencies</span></span>

<span data-ttu-id="cd441-177">Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás.</span><span class="sxs-lookup"><span data-stu-id="cd441-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="cd441-178">Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:</span><span class="sxs-lookup"><span data-stu-id="cd441-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="cd441-179">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="cd441-179">liblttng-ust0</span></span>
- <span data-ttu-id="cd441-180">libcurl3 (pro 14. x a 16. x)</span><span class="sxs-lookup"><span data-stu-id="cd441-180">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="cd441-181">libcurl4 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="cd441-181">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="cd441-182">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="cd441-182">libssl1.0.0</span></span>
- <span data-ttu-id="cd441-183">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="cd441-183">libkrb5-3</span></span>
- <span data-ttu-id="cd441-184">zlib1g</span><span class="sxs-lookup"><span data-stu-id="cd441-184">zlib1g</span></span>
- <span data-ttu-id="cd441-185">libicu52 (pro 14. x)</span><span class="sxs-lookup"><span data-stu-id="cd441-185">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="cd441-186">libicu55 (pro 16. x)</span><span class="sxs-lookup"><span data-stu-id="cd441-186">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="cd441-187">libicu57 (pro 17. x)</span><span class="sxs-lookup"><span data-stu-id="cd441-187">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="cd441-188">libicu60 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="cd441-188">libicu60 (for 18.x)</span></span>

<span data-ttu-id="cd441-189">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="cd441-189">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="cd441-190">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="cd441-190">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="cd441-191">Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="cd441-191">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="cd441-192">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="cd441-192">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="cd441-193">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="cd441-193">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="cd441-194">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="cd441-194">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="cd441-195">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cd441-195">Next steps</span></span>

- [<span data-ttu-id="cd441-196">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cd441-196">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
