---
title: Instalace rozhraní .NET Core do správce balíčků Ubuntu 18.04 - .NET Core
description: Pomocí správce balíčků nainstalujte do Ubuntu 18.04 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: e36116d357b8fcd5ced328a574e12c558dd9e2f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920695"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="a1348-103">Ubuntu 18.04 Správce balíčků - Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="a1348-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="a1348-104">Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na Ubuntu 18.04.</span><span class="sxs-lookup"><span data-stu-id="a1348-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span> <span data-ttu-id="a1348-105">Pokud instalujete runtime, doporučujeme nainstalovat [ASP.NET core runtime](#install-the-aspnet-core-runtime), protože zahrnuje rozhraní .NET Core i ASP.NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="a1348-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="a1348-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="a1348-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="a1348-107">Před instalací rozhraní .NET budete muset:</span><span class="sxs-lookup"><span data-stu-id="a1348-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="a1348-108">Zaregistrujte klíč Společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a1348-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="a1348-109">Zaregistrujte úložiště produktů.</span><span class="sxs-lookup"><span data-stu-id="a1348-109">Register the product repository.</span></span>
- <span data-ttu-id="a1348-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="a1348-110">Install required dependencies.</span></span>

<span data-ttu-id="a1348-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="a1348-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="a1348-112">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="a1348-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="a1348-113">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a1348-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="a1348-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a1348-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="a1348-115">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="a1348-115">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="a1348-116">Pokud se zobrazí chybová zpráva podobná **možnosti Nelze vyhledat balíček dotnet-sdk-3.1**, [přečtěte si část Poradce při potížích se správcem balíčků.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="a1348-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="a1348-117">ASP.NET Instalace core runtime</span><span class="sxs-lookup"><span data-stu-id="a1348-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="a1348-118">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET core runtime.</span><span class="sxs-lookup"><span data-stu-id="a1348-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="a1348-119">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="a1348-119">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="a1348-120">Pokud se zobrazí chybová zpráva podobná **nelze najít balíček aspnetcore-runtime-3.1**, naleznete [v části Poradce při potížích s správcem balíčků.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="a1348-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="a1348-121">Instalace runtime jádra .NET</span><span class="sxs-lookup"><span data-stu-id="a1348-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="a1348-122">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1348-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="a1348-123">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="a1348-123">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="a1348-124">Pokud se zobrazí chybová zpráva podobná **nelze najít balíček dotnet-runtime-3.1**, naleznete [v části Poradce při potížích s správcem balíčků.](#troubleshoot-the-package-manager)</span><span class="sxs-lookup"><span data-stu-id="a1348-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a1348-125">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="a1348-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a1348-126">Poradce při potížích se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="a1348-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="a1348-127">Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="a1348-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="a1348-128">Nelze najít</span><span class="sxs-lookup"><span data-stu-id="a1348-128">Unable to locate</span></span>

<span data-ttu-id="a1348-129">Pokud se zobrazí chybová zpráva podobná **příkazu Nelze najít balíček {balíček .NET Core}**, spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="a1348-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="a1348-130">Pokud to nepomůže, můžete spustit ruční instalaci pomocí následujících příkazů.</span><span class="sxs-lookup"><span data-stu-id="a1348-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="a1348-131">Načtení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="a1348-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
