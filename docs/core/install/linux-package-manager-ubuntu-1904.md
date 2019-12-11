---
title: Instalace .NET Core na Ubuntu 19,04 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Ubuntu 19,04.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 69bfc3395f5cd92ed54850e5ea8b76eba7f27d83
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959744"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="5e023-103">Správce balíčků Ubuntu 19,04 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e023-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="5e023-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Ubuntu 19,04.</span><span class="sxs-lookup"><span data-stu-id="5e023-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span> <span data-ttu-id="5e023-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e023-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="5e023-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="5e023-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="5e023-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="5e023-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="5e023-108">Registrace klíče Microsoftu</span><span class="sxs-lookup"><span data-stu-id="5e023-108">Register the Microsoft key</span></span>
- <span data-ttu-id="5e023-109">registrace úložiště produktu</span><span class="sxs-lookup"><span data-stu-id="5e023-109">register the product repository</span></span>
- <span data-ttu-id="5e023-110">Nainstalovat požadované závislosti</span><span class="sxs-lookup"><span data-stu-id="5e023-110">Install required dependencies</span></span>

<span data-ttu-id="5e023-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="5e023-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="5e023-112">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5e023-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="5e023-113">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5e023-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="5e023-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5e023-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="5e023-115">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5e023-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="5e023-116">Pokud se zobrazí chybová zpráva podobná této chybě **nelze nalézt balíček dotnet-SDK-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="5e023-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="5e023-117">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5e023-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="5e023-118">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e023-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="5e023-119">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5e023-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="5e023-120">Pokud se zobrazí chybová zpráva podobná té, že **nejde najít Package aspnetcore-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="5e023-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="5e023-121">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e023-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="5e023-122">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e023-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="5e023-123">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5e023-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="5e023-124">Pokud se zobrazí chybová zpráva podobná řetězci **nelze nalézt balíček dotnet-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="5e023-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5e023-125">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="5e023-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="5e023-126">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="5e023-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="5e023-127">Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Package .NET Core}** , spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="5e023-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="5e023-128">Pokud to nefunguje, můžete spustit ruční instalaci pomocí následujících příkazů.</span><span class="sxs-lookup"><span data-stu-id="5e023-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
