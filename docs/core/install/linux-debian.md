---
title: Instalace .NET Core na Debian – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v Debian.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 68a3e848b3d80806e875dfb2fb7e2cbf223f8ad5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619491"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="528f0-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v Debian</span><span class="sxs-lookup"><span data-stu-id="528f0-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="528f0-104">Tento článek popisuje, jak nainstalovat .NET Core na Debian.</span><span class="sxs-lookup"><span data-stu-id="528f0-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="528f0-105">Pokud je verze Debian mimo podporu, rozhraní .NET Core již není s touto verzí podporováno.</span><span class="sxs-lookup"><span data-stu-id="528f0-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="528f0-106">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="528f0-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="528f0-107">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="528f0-107">Supported distributions</span></span>

<span data-ttu-id="528f0-108">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Debian, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="528f0-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="528f0-109">Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Debian dosáhne konce životnosti](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="528f0-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="528f0-110">✔️ označuje, že je stále podporovaná verze Debian nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="528f0-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="528f0-111">❌Indikuje, že verze Debian nebo .NET Core není v této verzi Debian podporována.</span><span class="sxs-lookup"><span data-stu-id="528f0-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="528f0-112">Pokud se ✔️á jak verze Debian, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="528f0-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="528f0-113">Debian</span><span class="sxs-lookup"><span data-stu-id="528f0-113">Debian</span></span>                   | <span data-ttu-id="528f0-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="528f0-114">.NET Core 2.1</span></span> | <span data-ttu-id="528f0-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="528f0-115">.NET Core 3.1</span></span> | <span data-ttu-id="528f0-116">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="528f0-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="528f0-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="528f0-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="528f0-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="528f0-118">✔️ 2.1</span></span>        | <span data-ttu-id="528f0-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="528f0-119">✔️ 3.1</span></span>        | <span data-ttu-id="528f0-120">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="528f0-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="528f0-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="528f0-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="528f0-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="528f0-122">✔️ 2.1</span></span>        | <span data-ttu-id="528f0-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="528f0-123">✔️ 3.1</span></span>        | <span data-ttu-id="528f0-124">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="528f0-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="528f0-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="528f0-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="528f0-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="528f0-126">✔️ 2.1</span></span>        | <span data-ttu-id="528f0-127">❌3,1</span><span class="sxs-lookup"><span data-stu-id="528f0-127">❌ 3.1</span></span>        | <span data-ttu-id="528f0-128">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="528f0-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="528f0-129">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="528f0-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="528f0-130">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="528f0-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="528f0-131">3.0</span><span class="sxs-lookup"><span data-stu-id="528f0-131">3.0</span></span>
- <span data-ttu-id="528f0-132">2,2</span><span class="sxs-lookup"><span data-stu-id="528f0-132">2.2</span></span>
- <span data-ttu-id="528f0-133">2.0</span><span class="sxs-lookup"><span data-stu-id="528f0-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="528f0-134">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="528f0-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="528f0-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="528f0-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="528f0-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="528f0-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="528f0-137">Debian 8❌</span><span class="sxs-lookup"><span data-stu-id="528f0-137">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="528f0-138">APT Update SDK nebo modul runtime</span><span class="sxs-lookup"><span data-stu-id="528f0-138">APT update SDK or runtime</span></span>

<span data-ttu-id="528f0-139">Když je k dispozici nová verze opravy pro .NET Core, můžete ji jednoduše upgradovat prostřednictvím APT pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="528f0-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="528f0-140">Řešení potíží s APT</span><span class="sxs-lookup"><span data-stu-id="528f0-140">APT troubleshooting</span></span>

<span data-ttu-id="528f0-141">V této části najdete informace o běžných chybách, ke kterým může dojít při použití APT k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="528f0-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="528f0-142">Nejde najít.</span><span class="sxs-lookup"><span data-stu-id="528f0-142">Unable to locate</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="528f0-143">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="528f0-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="528f0-144">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="528f0-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="528f0-145">Závislosti</span><span class="sxs-lookup"><span data-stu-id="528f0-145">Dependencies</span></span>

<span data-ttu-id="528f0-146">Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás.</span><span class="sxs-lookup"><span data-stu-id="528f0-146">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="528f0-147">Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:</span><span class="sxs-lookup"><span data-stu-id="528f0-147">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="528f0-148">libc6</span><span class="sxs-lookup"><span data-stu-id="528f0-148">libc6</span></span>
- <span data-ttu-id="528f0-149">libgcc1</span><span class="sxs-lookup"><span data-stu-id="528f0-149">libgcc1</span></span>
- <span data-ttu-id="528f0-150">libgssapi – krb5 – 2</span><span class="sxs-lookup"><span data-stu-id="528f0-150">libgssapi-krb5-2</span></span>
- <span data-ttu-id="528f0-151">libicu52 (pro 8. x)</span><span class="sxs-lookup"><span data-stu-id="528f0-151">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="528f0-152">libicu57 (pro 9. x)</span><span class="sxs-lookup"><span data-stu-id="528f0-152">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="528f0-153">libicu63 (pro 10. x)</span><span class="sxs-lookup"><span data-stu-id="528f0-153">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="528f0-154">libicu67 (pro 11. x)</span><span class="sxs-lookup"><span data-stu-id="528f0-154">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="528f0-155">libssl 1.0.0 (pro 8. x)</span><span class="sxs-lookup"><span data-stu-id="528f0-155">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="528f0-156">libssl 1.1 (pro 9. x-11. x)</span><span class="sxs-lookup"><span data-stu-id="528f0-156">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="528f0-157">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="528f0-157">libstdc++6</span></span>
- <span data-ttu-id="528f0-158">zlib1g</span><span class="sxs-lookup"><span data-stu-id="528f0-158">zlib1g</span></span>

<span data-ttu-id="528f0-159">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="528f0-159">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="528f0-160">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="528f0-160">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="528f0-161">Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="528f0-161">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="528f0-162">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="528f0-162">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="528f0-163">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="528f0-163">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="528f0-164">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="528f0-164">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="528f0-165">Další kroky</span><span class="sxs-lookup"><span data-stu-id="528f0-165">Next steps</span></span>

- [<span data-ttu-id="528f0-166">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="528f0-166">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
