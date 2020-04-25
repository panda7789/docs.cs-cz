---
title: Instalace .NET Core na Ubuntu 20,04 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Ubuntu 20,04.
author: thraka
ms.author: adegeo
ms.date: 04/15/2020
ms.openlocfilehash: b99dcbab3305bffdcc9202bb2a09e3061abca95b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82148378"
---
# <a name="ubuntu-2004-package-manager---install-net-core"></a><span data-ttu-id="25272-103">Správce balíčků Ubuntu 20,04 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="25272-103">Ubuntu 20.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="25272-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Ubuntu 20,04.</span><span class="sxs-lookup"><span data-stu-id="25272-104">This article describes how to use a package manager to install .NET Core on Ubuntu 20.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="25272-105">Přidat klíč a kanál úložiště Microsoftu</span><span class="sxs-lookup"><span data-stu-id="25272-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="25272-106">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="25272-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="25272-107">Přidejte podpisový klíč Microsoft Package do seznamu důvěryhodných klíčů.</span><span class="sxs-lookup"><span data-stu-id="25272-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="25272-108">Přidejte úložiště do Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="25272-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="25272-109">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="25272-109">Install required dependencies.</span></span>

<span data-ttu-id="25272-110">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="25272-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="25272-111">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25272-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="25272-112">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="25272-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="25272-113">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="25272-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="25272-114">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25272-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="25272-115">Pokud se zobrazí chybová zpráva podobná této chybě **nelze nalézt balíček dotnet-SDK-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="25272-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="25272-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25272-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="25272-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="25272-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="25272-118">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25272-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="25272-119">Pokud se zobrazí chybová zpráva podobná té, že **nejde najít Package aspnetcore-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="25272-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="25272-120">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="25272-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="25272-121">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25272-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="25272-122">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25272-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="25272-123">Pokud se zobrazí chybová zpráva podobná řetězci **nelze nalézt balíček dotnet-runtime-3,1**, přečtěte si téma [Poradce při potížích s částí správce balíčků](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="25272-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="25272-124">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="25272-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="25272-125">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="25272-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="25272-126">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25272-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="25272-127">Nejde najít.</span><span class="sxs-lookup"><span data-stu-id="25272-127">Unable to locate</span></span>

<span data-ttu-id="25272-128">Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Package .NET Core}**, spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25272-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="25272-129">Pokud to nefunguje, můžete spustit ruční instalaci pomocí následujících příkazů.</span><span class="sxs-lookup"><span data-stu-id="25272-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/20.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="25272-130">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="25272-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
