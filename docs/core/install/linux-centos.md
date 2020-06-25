---
title: Instalace .NET Core na CentOS – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v CentOS.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9f4de70b4989be1d162f384518a015816a3e75a9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324891"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-centos"></a><span data-ttu-id="73073-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v CentOS</span><span class="sxs-lookup"><span data-stu-id="73073-103">Install .NET Core SDK or .NET Core Runtime on CentOS</span></span>

<span data-ttu-id="73073-104">Rozhraní .NET Core je podporováno v CentOS.</span><span class="sxs-lookup"><span data-stu-id="73073-104">.NET Core is supported on CentOS.</span></span> <span data-ttu-id="73073-105">Tento článek popisuje, jak nainstalovat .NET Core na CentOS.</span><span class="sxs-lookup"><span data-stu-id="73073-105">This article describes how to install .NET Core on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="73073-106">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="73073-106">Supported distributions</span></span>

<span data-ttu-id="73073-107">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na CentOS 7 a CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="73073-107">The following table is a list of currently supported .NET Core releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="73073-108">Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze CentOS.</span><span class="sxs-lookup"><span data-stu-id="73073-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="73073-109">✔️ označuje, že je stále podporovaná verze CentOS nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73073-109">A ✔️ indicates that the version of CentOS or .NET Core is still supported.</span></span>
- <span data-ttu-id="73073-110">❌Indikuje, že verze CentOS nebo .NET Core není v této verzi CentOS podporována.</span><span class="sxs-lookup"><span data-stu-id="73073-110">A ❌ indicates that the version of CentOS or .NET Core isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="73073-111">Pokud se ✔️á jak verze CentOS, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="73073-111">When both a version of CentOS and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="73073-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="73073-112">CentOS</span></span>                   | <span data-ttu-id="73073-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="73073-113">.NET Core 2.1</span></span> | <span data-ttu-id="73073-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="73073-114">.NET Core 3.1</span></span> | <span data-ttu-id="73073-115">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="73073-115">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="73073-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="73073-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="73073-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="73073-117">✔️ 2.1</span></span>        | <span data-ttu-id="73073-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="73073-118">✔️ 3.1</span></span>        | <span data-ttu-id="73073-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="73073-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="73073-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="73073-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="73073-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="73073-121">✔️ 2.1</span></span>        | <span data-ttu-id="73073-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="73073-122">✔️ 3.1</span></span>        | <span data-ttu-id="73073-123">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="73073-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="73073-124">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="73073-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="73073-125">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="73073-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="73073-126">3.0</span><span class="sxs-lookup"><span data-stu-id="73073-126">3.0</span></span>
- <span data-ttu-id="73073-127">2,2</span><span class="sxs-lookup"><span data-stu-id="73073-127">2.2</span></span>
- <span data-ttu-id="73073-128">2.0</span><span class="sxs-lookup"><span data-stu-id="73073-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="73073-129">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="73073-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="73073-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="73073-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="73073-131">.NET Core 3,1 je k dispozici ve výchozích úložištích balíčků pro CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="73073-131">.NET Core 3.1 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="73073-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="73073-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-31](includes/linux-install-31-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="73073-133">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="73073-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="73073-134">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73073-134">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="73073-135">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="73073-135">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="73073-136">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="73073-136">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="73073-137">Závislosti</span><span class="sxs-lookup"><span data-stu-id="73073-137">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="73073-138">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="73073-138">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="73073-139">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="73073-139">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="73073-140">Další kroky</span><span class="sxs-lookup"><span data-stu-id="73073-140">Next steps</span></span>

- [<span data-ttu-id="73073-141">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="73073-141">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
