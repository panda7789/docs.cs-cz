---
title: Instalace .NET Core na Debian – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v Debian.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c66d8e1daad4e59a766781b7117600352879b724
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603053"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="ffc71-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v Debian</span><span class="sxs-lookup"><span data-stu-id="ffc71-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="ffc71-104">Tento článek popisuje, jak nainstalovat .NET Core na Debian.</span><span class="sxs-lookup"><span data-stu-id="ffc71-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="ffc71-105">Pokud je verze Debian mimo podporu, rozhraní .NET Core již není s touto verzí podporováno.</span><span class="sxs-lookup"><span data-stu-id="ffc71-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="ffc71-106">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="ffc71-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="ffc71-107">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="ffc71-107">Supported distributions</span></span>

<span data-ttu-id="ffc71-108">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Debian, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="ffc71-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="ffc71-109">Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Debian dosáhne konce životnosti](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="ffc71-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="ffc71-110">✔️ označuje, že je stále podporovaná verze Debian nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ffc71-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="ffc71-111">❌Indikuje, že verze Debian nebo .NET Core není v této verzi Debian podporována.</span><span class="sxs-lookup"><span data-stu-id="ffc71-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="ffc71-112">Pokud se ✔️á jak verze Debian, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="ffc71-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="ffc71-113">Debian</span><span class="sxs-lookup"><span data-stu-id="ffc71-113">Debian</span></span>                   | <span data-ttu-id="ffc71-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ffc71-114">.NET Core 2.1</span></span> | <span data-ttu-id="ffc71-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ffc71-115">.NET Core 3.1</span></span> | <span data-ttu-id="ffc71-116">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="ffc71-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="ffc71-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="ffc71-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="ffc71-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ffc71-118">✔️ 2.1</span></span>        | <span data-ttu-id="ffc71-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="ffc71-119">✔️ 3.1</span></span>        | <span data-ttu-id="ffc71-120">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="ffc71-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="ffc71-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="ffc71-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="ffc71-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ffc71-122">✔️ 2.1</span></span>        | <span data-ttu-id="ffc71-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="ffc71-123">✔️ 3.1</span></span>        | <span data-ttu-id="ffc71-124">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="ffc71-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="ffc71-125">❌[8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="ffc71-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="ffc71-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ffc71-126">✔️ 2.1</span></span>        | <span data-ttu-id="ffc71-127">❌3,1</span><span class="sxs-lookup"><span data-stu-id="ffc71-127">❌ 3.1</span></span>        | <span data-ttu-id="ffc71-128">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="ffc71-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="ffc71-129">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="ffc71-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="ffc71-130">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="ffc71-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ffc71-131">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc71-131">3.0</span></span>
- <span data-ttu-id="ffc71-132">2,2</span><span class="sxs-lookup"><span data-stu-id="ffc71-132">2.2</span></span>
- <span data-ttu-id="ffc71-133">2.0</span><span class="sxs-lookup"><span data-stu-id="ffc71-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ffc71-134">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="ffc71-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="ffc71-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="ffc71-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="ffc71-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="ffc71-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="ffc71-137">Debian 8❌</span><span class="sxs-lookup"><span data-stu-id="ffc71-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="ffc71-138">APT Update SDK nebo modul runtime</span><span class="sxs-lookup"><span data-stu-id="ffc71-138">APT update SDK or runtime</span></span>

<span data-ttu-id="ffc71-139">Když je k dispozici nová verze opravy pro .NET Core, můžete ji jednoduše upgradovat prostřednictvím APT pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="ffc71-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="ffc71-140">Řešení potíží s APT</span><span class="sxs-lookup"><span data-stu-id="ffc71-140">APT troubleshooting</span></span>

<span data-ttu-id="ffc71-141">V této části najdete informace o běžných chybách, ke kterým může dojít při použití APT k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ffc71-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="ffc71-142">Nejde najít.</span><span class="sxs-lookup"><span data-stu-id="ffc71-142">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="ffc71-143">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="ffc71-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="ffc71-144">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="ffc71-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="ffc71-145">Závislosti</span><span class="sxs-lookup"><span data-stu-id="ffc71-145">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="ffc71-146">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="ffc71-146">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="ffc71-147">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="ffc71-147">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="ffc71-148">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ffc71-148">Next steps</span></span>

- [<span data-ttu-id="ffc71-149">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ffc71-149">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
