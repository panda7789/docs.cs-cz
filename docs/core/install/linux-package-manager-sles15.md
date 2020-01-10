---
title: Instalace .NET Core na SLES 15 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v SLES 15.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 18a0068e5494d6a25e9cd278ce88f5915e2000b8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740641"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="e9653-103">Správce balíčků SLES 15 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="e9653-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e9653-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na SLES 15.</span><span class="sxs-lookup"><span data-stu-id="e9653-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="e9653-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e9653-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="e9653-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="e9653-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="e9653-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="e9653-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e9653-108">Zaregistrujte si klíč Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e9653-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="e9653-109">Zaregistrujte úložiště produktu.</span><span class="sxs-lookup"><span data-stu-id="e9653-109">Register the product repository.</span></span>
- <span data-ttu-id="e9653-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="e9653-110">Install required dependencies.</span></span>

<span data-ttu-id="e9653-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="e9653-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e9653-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9653-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e9653-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e9653-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="e9653-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e9653-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e9653-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9653-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e9653-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e9653-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e9653-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e9653-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="e9653-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9653-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e9653-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="e9653-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="e9653-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e9653-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e9653-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9653-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e9653-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="e9653-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
