---
title: Instalace .NET Core na Fedora – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v Fedora.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c90c08eefa074fa139642a268f879af79d7280da
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619478"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a><span data-ttu-id="649f7-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v Fedora</span><span class="sxs-lookup"><span data-stu-id="649f7-103">Install .NET Core SDK or .NET Core Runtime on Fedora</span></span>

<span data-ttu-id="649f7-104">Rozhraní .NET Core je podporováno v Fedora.</span><span class="sxs-lookup"><span data-stu-id="649f7-104">.NET Core is supported on Fedora.</span></span> <span data-ttu-id="649f7-105">Tento článek popisuje, jak nainstalovat .NET Core na Fedora.</span><span class="sxs-lookup"><span data-stu-id="649f7-105">This article describes how to install .NET Core on Fedora.</span></span> <span data-ttu-id="649f7-106">Pokud je verze Fedora mimo podporu, rozhraní .NET Core již není s touto verzí podporováno.</span><span class="sxs-lookup"><span data-stu-id="649f7-106">When a Fedora version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="649f7-107">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="649f7-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="649f7-108">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="649f7-108">Supported distributions</span></span>

<span data-ttu-id="649f7-109">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Fedora, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="649f7-109">The following table is a list of currently supported .NET Core releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="649f7-110">Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Fedora dosáhne konce životnosti](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="649f7-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="649f7-111">✔️ označuje, že je stále podporovaná verze Fedora nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="649f7-111">A ✔️ indicates that the version of Fedora or .NET Core is still supported.</span></span>
- <span data-ttu-id="649f7-112">❌Indikuje, že verze Fedora nebo .NET Core není v této verzi Fedora podporována.</span><span class="sxs-lookup"><span data-stu-id="649f7-112">A ❌ indicates that the version of Fedora or .NET Core isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="649f7-113">Pokud se ✔️á jak verze Fedora, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="649f7-113">When both a version of Fedora and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="649f7-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="649f7-114">Fedora</span></span>                   | <span data-ttu-id="649f7-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="649f7-115">.NET Core 2.1</span></span> | <span data-ttu-id="649f7-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="649f7-116">.NET Core 3.1</span></span> | <span data-ttu-id="649f7-117">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="649f7-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="649f7-118">✔️ [32](linux-fedora.md#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="649f7-118">✔️ [32](linux-fedora.md#fedora-32-)</span></span> | <span data-ttu-id="649f7-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="649f7-119">✔️ 2.1</span></span>        | <span data-ttu-id="649f7-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="649f7-120">✔️ 3.1</span></span>        | <span data-ttu-id="649f7-121">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="649f7-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="649f7-122">✔️ [31](linux-fedora.md#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="649f7-122">✔️ [31](linux-fedora.md#fedora-31-)</span></span> | <span data-ttu-id="649f7-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="649f7-123">✔️ 2.1</span></span>        | <span data-ttu-id="649f7-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="649f7-124">✔️ 3.1</span></span>        | <span data-ttu-id="649f7-125">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="649f7-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="649f7-126">❌[30](linux-fedora.md#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="649f7-126">❌ [30](linux-fedora.md#fedora-30-)</span></span> | <span data-ttu-id="649f7-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="649f7-127">✔️ 2.1</span></span>        | <span data-ttu-id="649f7-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="649f7-128">✔️ 3.1</span></span>        | <span data-ttu-id="649f7-129">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="649f7-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="649f7-130">❌[29](linux-fedora.md#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="649f7-130">❌ [29](linux-fedora.md#fedora-29-)</span></span> | <span data-ttu-id="649f7-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="649f7-131">✔️ 2.1</span></span>        | <span data-ttu-id="649f7-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="649f7-132">✔️ 3.1</span></span>        | <span data-ttu-id="649f7-133">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="649f7-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="649f7-134">❌[28](linux-fedora.md#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="649f7-134">❌ [28](linux-fedora.md#fedora-28-)</span></span> | <span data-ttu-id="649f7-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="649f7-135">✔️ 2.1</span></span>        | <span data-ttu-id="649f7-136">❌3,1</span><span class="sxs-lookup"><span data-stu-id="649f7-136">❌ 3.1</span></span>        | <span data-ttu-id="649f7-137">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="649f7-137">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="649f7-138">❌[27](linux-fedora.md#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="649f7-138">❌ [27](linux-fedora.md#fedora-27-)</span></span> | <span data-ttu-id="649f7-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="649f7-139">✔️ 2.1</span></span>        | <span data-ttu-id="649f7-140">❌3,1</span><span class="sxs-lookup"><span data-stu-id="649f7-140">❌ 3.1</span></span>        | <span data-ttu-id="649f7-141">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="649f7-141">❌ 5.0 Preview</span></span> |

<span data-ttu-id="649f7-142">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="649f7-142">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="649f7-143">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="649f7-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="649f7-144">3.0</span><span class="sxs-lookup"><span data-stu-id="649f7-144">3.0</span></span>
- <span data-ttu-id="649f7-145">2,2</span><span class="sxs-lookup"><span data-stu-id="649f7-145">2.2</span></span>
- <span data-ttu-id="649f7-146">2.0</span><span class="sxs-lookup"><span data-stu-id="649f7-146">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="649f7-147">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="649f7-147">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a><span data-ttu-id="649f7-148">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="649f7-148">Fedora 32 ✔️</span></span>

<span data-ttu-id="649f7-149">.NET Core 3,1 je k dispozici ve výchozích úložištích balíčků pro Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="649f7-149">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="649f7-150">Fedora 31 ✔️</span><span class="sxs-lookup"><span data-stu-id="649f7-150">Fedora 31 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="649f7-151">Fedora 30❌</span><span class="sxs-lookup"><span data-stu-id="649f7-151">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="649f7-152">Fedora 29❌</span><span class="sxs-lookup"><span data-stu-id="649f7-152">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="649f7-153">Fedora 28❌</span><span class="sxs-lookup"><span data-stu-id="649f7-153">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="649f7-154">Fedora 27❌</span><span class="sxs-lookup"><span data-stu-id="649f7-154">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="649f7-155">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="649f7-155">Troubleshoot the package manager</span></span>

<span data-ttu-id="649f7-156">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="649f7-156">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="649f7-157">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="649f7-157">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="649f7-158">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="649f7-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="649f7-159">Závislosti</span><span class="sxs-lookup"><span data-stu-id="649f7-159">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="649f7-160">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="649f7-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="649f7-161">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="649f7-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="649f7-162">Další kroky</span><span class="sxs-lookup"><span data-stu-id="649f7-162">Next steps</span></span>

- [<span data-ttu-id="649f7-163">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="649f7-163">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
