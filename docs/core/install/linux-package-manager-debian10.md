---
title: Instalace .NET Core na Debian 10 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Debian 10.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 2c24a02423f5aa8f011cfb4705efb51d97cfaf1e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836946"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="fa74b-103">Správce balíčků Debian 10 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa74b-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="fa74b-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Debian 10.</span><span class="sxs-lookup"><span data-stu-id="fa74b-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span> <span data-ttu-id="fa74b-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa74b-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="fa74b-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="fa74b-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="fa74b-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="fa74b-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="fa74b-108">Registrace klíče Microsoftu</span><span class="sxs-lookup"><span data-stu-id="fa74b-108">Register the Microsoft key</span></span>
- <span data-ttu-id="fa74b-109">registrace úložiště produktu</span><span class="sxs-lookup"><span data-stu-id="fa74b-109">register the product repository</span></span>
- <span data-ttu-id="fa74b-110">Nainstalovat požadované závislosti</span><span class="sxs-lookup"><span data-stu-id="fa74b-110">Install required dependencies</span></span>

<span data-ttu-id="fa74b-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="fa74b-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="fa74b-112">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="fa74b-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="fa74b-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="fa74b-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="fa74b-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="fa74b-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="fa74b-115">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="fa74b-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="fa74b-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fa74b-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="fa74b-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fa74b-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="fa74b-118">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="fa74b-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="fa74b-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa74b-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="fa74b-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa74b-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="fa74b-121">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="fa74b-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fa74b-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="fa74b-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
