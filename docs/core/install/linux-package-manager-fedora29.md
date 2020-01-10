---
title: Instalace .NET Core v Fedora 29 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Fedora 29.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 750952229297ae069c0e8465bf83333d86b38dbd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740679"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="42fea-103">Správce balíčků Fedora 29 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="42fea-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="42fea-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Fedora 29.</span><span class="sxs-lookup"><span data-stu-id="42fea-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span> <span data-ttu-id="42fea-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="42fea-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="42fea-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="42fea-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="42fea-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="42fea-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="42fea-108">Zaregistrujte si klíč Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42fea-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="42fea-109">Zaregistrujte úložiště produktu.</span><span class="sxs-lookup"><span data-stu-id="42fea-109">Register the product repository.</span></span>
- <span data-ttu-id="42fea-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="42fea-110">Install required dependencies.</span></span>

<span data-ttu-id="42fea-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="42fea-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="42fea-112">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="42fea-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="42fea-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="42fea-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="42fea-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="42fea-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="42fea-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="42fea-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="42fea-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="42fea-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="42fea-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="42fea-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="42fea-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="42fea-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="42fea-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="42fea-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="42fea-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42fea-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="42fea-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="42fea-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="42fea-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="42fea-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
