---
title: Instalace .NET Core na SLES – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v SLES.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9816e1f0253be58dc04c1302f334a7ea0b810810
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768392"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="6e833-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v SLES</span><span class="sxs-lookup"><span data-stu-id="6e833-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="6e833-104">Rozhraní .NET Core je podporováno v SLES.</span><span class="sxs-lookup"><span data-stu-id="6e833-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="6e833-105">Tento článek popisuje, jak nainstalovat .NET Core na SLES.</span><span class="sxs-lookup"><span data-stu-id="6e833-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="6e833-106">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="6e833-106">Supported distributions</span></span>

<span data-ttu-id="6e833-107">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na SLES 12 SP2 a SLES 15.</span><span class="sxs-lookup"><span data-stu-id="6e833-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="6e833-108">Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze SLES.</span><span class="sxs-lookup"><span data-stu-id="6e833-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="6e833-109">✔️ označuje, že je stále podporovaná verze SLES nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e833-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="6e833-110">❌Indikuje, že verze SLES nebo .NET Core není v této verzi SLES podporována.</span><span class="sxs-lookup"><span data-stu-id="6e833-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="6e833-111">Pokud se ✔️á jak verze SLES, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="6e833-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="6e833-112">SLES</span><span class="sxs-lookup"><span data-stu-id="6e833-112">SLES</span></span>                   | <span data-ttu-id="6e833-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6e833-113">.NET Core 2.1</span></span> | <span data-ttu-id="6e833-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="6e833-114">.NET Core 3.1</span></span> | <span data-ttu-id="6e833-115">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="6e833-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="6e833-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="6e833-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="6e833-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6e833-117">✔️ 2.1</span></span>        | <span data-ttu-id="6e833-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6e833-118">✔️ 3.1</span></span>        | <span data-ttu-id="6e833-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="6e833-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="6e833-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="6e833-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="6e833-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6e833-121">✔️ 2.1</span></span>        | <span data-ttu-id="6e833-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6e833-122">✔️ 3.1</span></span>        | <span data-ttu-id="6e833-123">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="6e833-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="6e833-124">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="6e833-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="6e833-125">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="6e833-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="6e833-126">3.0</span><span class="sxs-lookup"><span data-stu-id="6e833-126">3.0</span></span>
- <span data-ttu-id="6e833-127">2,2</span><span class="sxs-lookup"><span data-stu-id="6e833-127">2.2</span></span>
- <span data-ttu-id="6e833-128">2.0</span><span class="sxs-lookup"><span data-stu-id="6e833-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="6e833-129">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="6e833-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="6e833-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="6e833-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="6e833-131">V současné době balíček pro nastavení úložiště Microsoft SLES 15 nainstaluje soubor *Microsoft-prod. úložiště* do nesprávného adresáře, takže zypperu nebude vyhledávat balíčky .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e833-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="6e833-132">Chcete-li tento problém vyřešit, vytvořte symlink ve správném adresáři.</span><span class="sxs-lookup"><span data-stu-id="6e833-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="6e833-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="6e833-133">SLES 12 ✔️</span></span>

<span data-ttu-id="6e833-134">.NET Core vyžaduje pro SLES 12 Family minimální verzi SP2.</span><span class="sxs-lookup"><span data-stu-id="6e833-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="6e833-135">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="6e833-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="6e833-136">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e833-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="6e833-137">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="6e833-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="6e833-138">Závislosti</span><span class="sxs-lookup"><span data-stu-id="6e833-138">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="6e833-139">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="6e833-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="6e833-140">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="6e833-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="6e833-141">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6e833-141">Next steps</span></span>

- [<span data-ttu-id="6e833-142">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6e833-142">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
