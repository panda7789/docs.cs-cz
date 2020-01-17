---
title: Instalace .NET Core na Ubuntu 19,10 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Ubuntu 19,10.
author: thraka
ms.author: adegeo
ms.date: 01/16/2020
ms.openlocfilehash: afba761e2237ed84528157841e538a9b44d9a966
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164082"
---
# <a name="ubuntu-1910-package-manager---install-net-core"></a><span data-ttu-id="93edb-103">Správce balíčků Ubuntu 19,10 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="93edb-103">Ubuntu 19.10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="93edb-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Ubuntu 19,10.</span><span class="sxs-lookup"><span data-stu-id="93edb-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.10.</span></span> <span data-ttu-id="93edb-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="93edb-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="93edb-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="93edb-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="93edb-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="93edb-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="93edb-108">Zaregistrujte si klíč Microsoft.</span><span class="sxs-lookup"><span data-stu-id="93edb-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="93edb-109">Zaregistrujte úložiště produktu.</span><span class="sxs-lookup"><span data-stu-id="93edb-109">Register the product repository.</span></span>
- <span data-ttu-id="93edb-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="93edb-110">Install required dependencies.</span></span>

<span data-ttu-id="93edb-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="93edb-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="93edb-112">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="93edb-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="93edb-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="93edb-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="93edb-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="93edb-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="93edb-115">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="93edb-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="93edb-116">Pokud se zobrazí chybová zpráva podobná této chybě **nelze nalézt balíček dotnet-SDK-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="93edb-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="93edb-117">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="93edb-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="93edb-118">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="93edb-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="93edb-119">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="93edb-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="93edb-120">Pokud se zobrazí chybová zpráva podobná té, že **nejde najít Package aspnetcore-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="93edb-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="93edb-121">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="93edb-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="93edb-122">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="93edb-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="93edb-123">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="93edb-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="93edb-124">Pokud se zobrazí chybová zpráva podobná řetězci **nelze nalézt balíček dotnet-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="93edb-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="93edb-125">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="93edb-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="93edb-126">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="93edb-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="93edb-127">Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Package .NET Core}** , spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="93edb-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="93edb-128">Pokud to nefunguje, můžete spustit ruční instalaci pomocí následujících příkazů.</span><span class="sxs-lookup"><span data-stu-id="93edb-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
