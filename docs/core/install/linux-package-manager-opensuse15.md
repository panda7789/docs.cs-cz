---
title: Instalace .NET Core na openSUSE 15 - správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte .NET Core SDK a runtime na openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 3b5f51161dad4b0d7851421810506d6ed9f676f9
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134235"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="4b887-103">openSUSE 15 Správce balíčků - Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b887-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="4b887-104">Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="4b887-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="4b887-105">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="4b887-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="4b887-106">Před instalací rozhraní .NET budete muset:</span><span class="sxs-lookup"><span data-stu-id="4b887-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="4b887-107">Zaregistrujte klíč Společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4b887-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="4b887-108">Zaregistrujte úložiště produktů.</span><span class="sxs-lookup"><span data-stu-id="4b887-108">Register the product repository.</span></span>
- <span data-ttu-id="4b887-109">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="4b887-109">Install required dependencies.</span></span>

<span data-ttu-id="4b887-110">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="4b887-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="4b887-111">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="4b887-111">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4b887-112">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4b887-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="4b887-113">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4b887-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="4b887-114">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="4b887-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4b887-115">ASP.NET Instalace core runtime</span><span class="sxs-lookup"><span data-stu-id="4b887-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="4b887-116">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="4b887-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="4b887-117">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="4b887-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4b887-118">Instalace runtime jádra .NET</span><span class="sxs-lookup"><span data-stu-id="4b887-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="4b887-119">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b887-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="4b887-120">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="4b887-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4b887-121">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="4b887-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="4b887-122">Poradce při potížích se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="4b887-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="4b887-123">Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="4b887-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="4b887-124">Načtení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="4b887-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
