---
title: Instalace .NET Core na Fedora – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v Fedora.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 52aa9409ec876e0d1eaef22fb739046941fda897
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603088"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a><span data-ttu-id="d069c-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v Fedora</span><span class="sxs-lookup"><span data-stu-id="d069c-103">Install .NET Core SDK or .NET Core Runtime on Fedora</span></span>

<span data-ttu-id="d069c-104">Rozhraní .NET Core je podporováno v Fedora.</span><span class="sxs-lookup"><span data-stu-id="d069c-104">.NET Core is supported on Fedora.</span></span> <span data-ttu-id="d069c-105">Tento článek popisuje, jak nainstalovat .NET Core na Fedora.</span><span class="sxs-lookup"><span data-stu-id="d069c-105">This article describes how to install .NET Core on Fedora.</span></span> <span data-ttu-id="d069c-106">Pokud je verze Fedora mimo podporu, rozhraní .NET Core již není s touto verzí podporováno.</span><span class="sxs-lookup"><span data-stu-id="d069c-106">When a Fedora version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="d069c-107">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="d069c-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="d069c-108">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="d069c-108">Supported distributions</span></span>

<span data-ttu-id="d069c-109">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Fedora, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="d069c-109">The following table is a list of currently supported .NET Core releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="d069c-110">Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Fedora dosáhne konce životnosti](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="d069c-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="d069c-111">✔️ označuje, že je stále podporovaná verze Fedora nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d069c-111">A ✔️ indicates that the version of Fedora or .NET Core is still supported.</span></span>
- <span data-ttu-id="d069c-112">❌Indikuje, že verze Fedora nebo .NET Core není v této verzi Fedora podporována.</span><span class="sxs-lookup"><span data-stu-id="d069c-112">A ❌ indicates that the version of Fedora or .NET Core isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="d069c-113">Pokud se ✔️á jak verze Fedora, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="d069c-113">When both a version of Fedora and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="d069c-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="d069c-114">Fedora</span></span>                   | <span data-ttu-id="d069c-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d069c-115">.NET Core 2.1</span></span> | <span data-ttu-id="d069c-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="d069c-116">.NET Core 3.1</span></span> | <span data-ttu-id="d069c-117">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="d069c-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="d069c-118">✔️ [32](linux-fedora.md#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="d069c-118">✔️ [32](linux-fedora.md#fedora-32-)</span></span> | <span data-ttu-id="d069c-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d069c-119">✔️ 2.1</span></span>        | <span data-ttu-id="d069c-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d069c-120">✔️ 3.1</span></span>        | <span data-ttu-id="d069c-121">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="d069c-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="d069c-122">✔️ [31](linux-fedora.md#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="d069c-122">✔️ [31](linux-fedora.md#fedora-31-)</span></span> | <span data-ttu-id="d069c-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d069c-123">✔️ 2.1</span></span>        | <span data-ttu-id="d069c-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d069c-124">✔️ 3.1</span></span>        | <span data-ttu-id="d069c-125">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="d069c-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="d069c-126">❌[30](linux-fedora.md#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="d069c-126">❌ [30](linux-fedora.md#fedora-30-)</span></span> | <span data-ttu-id="d069c-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d069c-127">✔️ 2.1</span></span>        | <span data-ttu-id="d069c-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d069c-128">✔️ 3.1</span></span>        | <span data-ttu-id="d069c-129">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="d069c-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d069c-130">❌[29](linux-fedora.md#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="d069c-130">❌ [29](linux-fedora.md#fedora-29-)</span></span> | <span data-ttu-id="d069c-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d069c-131">✔️ 2.1</span></span>        | <span data-ttu-id="d069c-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d069c-132">✔️ 3.1</span></span>        | <span data-ttu-id="d069c-133">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="d069c-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d069c-134">❌[28](linux-fedora.md#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="d069c-134">❌ [28](linux-fedora.md#fedora-28-)</span></span> | <span data-ttu-id="d069c-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d069c-135">✔️ 2.1</span></span>        | <span data-ttu-id="d069c-136">❌3,1</span><span class="sxs-lookup"><span data-stu-id="d069c-136">❌ 3.1</span></span>        | <span data-ttu-id="d069c-137">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="d069c-137">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d069c-138">❌[27](linux-fedora.md#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="d069c-138">❌ [27](linux-fedora.md#fedora-27-)</span></span> | <span data-ttu-id="d069c-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d069c-139">✔️ 2.1</span></span>        | <span data-ttu-id="d069c-140">❌3,1</span><span class="sxs-lookup"><span data-stu-id="d069c-140">❌ 3.1</span></span>        | <span data-ttu-id="d069c-141">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="d069c-141">❌ 5.0 Preview</span></span> |

<span data-ttu-id="d069c-142">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="d069c-142">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="d069c-143">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="d069c-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="d069c-144">3.0</span><span class="sxs-lookup"><span data-stu-id="d069c-144">3.0</span></span>
- <span data-ttu-id="d069c-145">2,2</span><span class="sxs-lookup"><span data-stu-id="d069c-145">2.2</span></span>
- <span data-ttu-id="d069c-146">2.0</span><span class="sxs-lookup"><span data-stu-id="d069c-146">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="d069c-147">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="d069c-147">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a><span data-ttu-id="d069c-148">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="d069c-148">Fedora 32 ✔️</span></span>

<span data-ttu-id="d069c-149">.NET Core 3,1 je k dispozici ve výchozích úložištích balíčků pro Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="d069c-149">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="d069c-150">Fedora 31 ✔️</span><span class="sxs-lookup"><span data-stu-id="d069c-150">Fedora 31 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="d069c-151">Fedora 30❌</span><span class="sxs-lookup"><span data-stu-id="d069c-151">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="d069c-152">Fedora 29❌</span><span class="sxs-lookup"><span data-stu-id="d069c-152">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="d069c-153">Fedora 28❌</span><span class="sxs-lookup"><span data-stu-id="d069c-153">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="d069c-154">Fedora 27❌</span><span class="sxs-lookup"><span data-stu-id="d069c-154">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="d069c-155">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="d069c-155">Troubleshoot the package manager</span></span>

<span data-ttu-id="d069c-156">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d069c-156">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="d069c-157">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="d069c-157">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="d069c-158">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="d069c-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="d069c-159">Závislosti</span><span class="sxs-lookup"><span data-stu-id="d069c-159">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="d069c-160">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="d069c-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="d069c-161">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="d069c-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="d069c-162">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d069c-162">Next steps</span></span>

- [<span data-ttu-id="d069c-163">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d069c-163">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
