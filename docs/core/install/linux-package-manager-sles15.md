---
title: Instalace .NET Core na SLES 15 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v SLES 15.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: be5a21db8c3942bfe8827dfbce41bcf88aec342a
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595606"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="2ca6f-103">Správce balíčků SLES 15 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ca6f-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="2ca6f-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na SLES 15.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="2ca6f-105">Přidat klíč a kanál úložiště Microsoftu</span><span class="sxs-lookup"><span data-stu-id="2ca6f-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="2ca6f-106">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="2ca6f-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="2ca6f-107">Přidejte podpisový klíč Microsoft Package do seznamu důvěryhodných klíčů.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="2ca6f-108">Přidejte úložiště do Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="2ca6f-109">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-109">Install required dependencies.</span></span>

<span data-ttu-id="2ca6f-110">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="2ca6f-111">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="2ca6f-112">V současné době balíček pro nastavení úložiště Microsoft SLES 15 nainstaluje soubor *Microsoft-prod. úložiště* do nesprávného adresáře, takže zypperu nebude vyhledávat balíčky .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-112">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="2ca6f-113">Chcete-li tento problém vyřešit, vytvořte symlink ve správném adresáři.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-113">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="2ca6f-114">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-114">Install the .NET Core SDK</span></span>

<span data-ttu-id="2ca6f-115">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-115">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="2ca6f-116">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-116">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="2ca6f-117">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2ca6f-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="2ca6f-118">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-118">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="2ca6f-119">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-119">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="2ca6f-120">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ca6f-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="2ca6f-121">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="2ca6f-122">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-122">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2ca6f-123">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="2ca6f-123">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="2ca6f-124">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="2ca6f-124">Troubleshoot the package manager</span></span>

<span data-ttu-id="2ca6f-125">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ca6f-125">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="2ca6f-126">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="2ca6f-126">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
