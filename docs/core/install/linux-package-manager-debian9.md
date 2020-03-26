---
title: Instalace .NET Core na Debian 9 - správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte na Debian 9 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: cfe28d04edfac97938612537986498636c141be0
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134296"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="86e19-103">Správce balíčků Debianu 9 – instalace rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="86e19-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="86e19-104">Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na Debian 9.</span><span class="sxs-lookup"><span data-stu-id="86e19-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="86e19-105">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="86e19-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="86e19-106">Před instalací rozhraní .NET budete muset:</span><span class="sxs-lookup"><span data-stu-id="86e19-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="86e19-107">Zaregistrujte klíč Společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="86e19-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="86e19-108">Zaregistrujte úložiště produktů.</span><span class="sxs-lookup"><span data-stu-id="86e19-108">Register the product repository.</span></span>
- <span data-ttu-id="86e19-109">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="86e19-109">Install required dependencies.</span></span>

<span data-ttu-id="86e19-110">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="86e19-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="86e19-111">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="86e19-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="86e19-112">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="86e19-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="86e19-113">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="86e19-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="86e19-114">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="86e19-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="86e19-115">ASP.NET Instalace core runtime</span><span class="sxs-lookup"><span data-stu-id="86e19-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="86e19-116">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="86e19-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="86e19-117">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="86e19-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="86e19-118">Instalace runtime jádra .NET</span><span class="sxs-lookup"><span data-stu-id="86e19-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="86e19-119">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86e19-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="86e19-120">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="86e19-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="86e19-121">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="86e19-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="86e19-122">Poradce při potížích se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="86e19-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="86e19-123">Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="86e19-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="86e19-124">Načtení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="86e19-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
