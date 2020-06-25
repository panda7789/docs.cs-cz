---
title: Instalace .NET Core na openSUSE – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 3a2ff1ca1519428f42c88048dde22aa11baaaa01
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324754"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="63658-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v openSUSE</span><span class="sxs-lookup"><span data-stu-id="63658-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="63658-104">Rozhraní .NET Core je podporováno v openSUSE.</span><span class="sxs-lookup"><span data-stu-id="63658-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="63658-105">Tento článek popisuje, jak nainstalovat .NET Core na openSUSE.</span><span class="sxs-lookup"><span data-stu-id="63658-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="63658-106">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="63658-106">Supported distributions</span></span>

<span data-ttu-id="63658-107">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="63658-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="63658-108">Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze openSUSE.</span><span class="sxs-lookup"><span data-stu-id="63658-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="63658-109">✔️ označuje, že je stále podporovaná verze openSUSE nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63658-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="63658-110">❌Indikuje, že verze openSUSE nebo .NET Core není v této verzi openSUSE podporována.</span><span class="sxs-lookup"><span data-stu-id="63658-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="63658-111">Pokud se ✔️á jak verze openSUSE, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="63658-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="63658-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="63658-112">openSUSE</span></span>                   | <span data-ttu-id="63658-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="63658-113">.NET Core 2.1</span></span> | <span data-ttu-id="63658-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="63658-114">.NET Core 3.1</span></span> | <span data-ttu-id="63658-115">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="63658-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="63658-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="63658-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="63658-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="63658-117">✔️ 2.1</span></span>        | <span data-ttu-id="63658-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="63658-118">✔️ 3.1</span></span>        | <span data-ttu-id="63658-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="63658-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="63658-120">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="63658-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="63658-121">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="63658-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="63658-122">3.0</span><span class="sxs-lookup"><span data-stu-id="63658-122">3.0</span></span>
- <span data-ttu-id="63658-123">2,2</span><span class="sxs-lookup"><span data-stu-id="63658-123">2.2</span></span>
- <span data-ttu-id="63658-124">2.0</span><span class="sxs-lookup"><span data-stu-id="63658-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="63658-125">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="63658-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="63658-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="63658-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="63658-127">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="63658-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="63658-128">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63658-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="63658-129">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="63658-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="63658-130">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="63658-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="63658-131">Závislosti</span><span class="sxs-lookup"><span data-stu-id="63658-131">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="63658-132">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="63658-132">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="63658-133">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="63658-133">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="63658-134">Další kroky</span><span class="sxs-lookup"><span data-stu-id="63658-134">Next steps</span></span>

- [<span data-ttu-id="63658-135">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="63658-135">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
