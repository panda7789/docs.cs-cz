---
title: Instalace rozhraní .NET Core do správce balíčků Ubuntu 16.04 - .NET Core
description: Pomocí správce balíčků nainstalujte do Ubuntu 16.04 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 9e99cd8649e907fbbf8ffac7bfc008610396a31c
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134167"
---
# <a name="ubuntu-1604-package-manager---install-net-core"></a><span data-ttu-id="59e8c-103">Ubuntu 16.04 Správce balíčků - Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="59e8c-103">Ubuntu 16.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="59e8c-104">Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="59e8c-104">This article describes how to use a package manager to install .NET Core on Ubuntu 16.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="59e8c-105">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="59e8c-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="59e8c-106">Před instalací rozhraní .NET budete muset:</span><span class="sxs-lookup"><span data-stu-id="59e8c-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="59e8c-107">Zaregistrujte klíč Společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59e8c-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="59e8c-108">Zaregistrujte úložiště produktů.</span><span class="sxs-lookup"><span data-stu-id="59e8c-108">Register the product repository.</span></span>
- <span data-ttu-id="59e8c-109">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="59e8c-109">Install required dependencies.</span></span>

<span data-ttu-id="59e8c-110">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="59e8c-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="59e8c-111">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="59e8c-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="59e8c-112">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="59e8c-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="59e8c-113">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="59e8c-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="59e8c-114">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="59e8c-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="59e8c-115">Pokud se zobrazí chybová zpráva podobná **možnosti Nelze vyhledat balíček dotnet-sdk-3.1**, [přečtěte si část Poradce při potížích se správcem balíčků.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="59e8c-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="59e8c-116">ASP.NET Instalace core runtime</span><span class="sxs-lookup"><span data-stu-id="59e8c-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="59e8c-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET core runtime.</span><span class="sxs-lookup"><span data-stu-id="59e8c-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="59e8c-118">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="59e8c-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="59e8c-119">Pokud se zobrazí chybová zpráva podobná **nelze najít balíček aspnetcore-runtime-3.1**, naleznete [v části Poradce při potížích s správcem balíčků.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="59e8c-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="59e8c-120">Instalace runtime jádra .NET</span><span class="sxs-lookup"><span data-stu-id="59e8c-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="59e8c-121">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59e8c-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="59e8c-122">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="59e8c-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="59e8c-123">Pokud se zobrazí chybová zpráva podobná **nelze najít balíček dotnet-runtime-3.1**, naleznete [v části Poradce při potížích s správcem balíčků.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="59e8c-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="59e8c-124">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="59e8c-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="59e8c-125">Poradce při potížích se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="59e8c-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="59e8c-126">Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="59e8c-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="59e8c-127">Nelze najít</span><span class="sxs-lookup"><span data-stu-id="59e8c-127">Unable to locate</span></span>

<span data-ttu-id="59e8c-128">Pokud se zobrazí chybová zpráva podobná **příkazu Nelze najít balíček {balíček .NET Core}**, spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="59e8c-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="59e8c-129">Pokud to nepomůže, můžete spustit ruční instalaci pomocí následujících příkazů.</span><span class="sxs-lookup"><span data-stu-id="59e8c-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/16.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="59e8c-130">Načtení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="59e8c-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
