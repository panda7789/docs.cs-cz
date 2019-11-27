---
title: Instalace .NET Core na SLES 15 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v SLES 15.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 8e773dbc63ad8c969ae5c85c05ba9ed0c67311ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450966"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="e56f7-103">Správce balíčků SLES 15 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="e56f7-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e56f7-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na SLES 15.</span><span class="sxs-lookup"><span data-stu-id="e56f7-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="e56f7-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e56f7-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="e56f7-106">Registrace klíče a kanálu Microsoft</span><span class="sxs-lookup"><span data-stu-id="e56f7-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="e56f7-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="e56f7-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e56f7-108">Registrace klíče Microsoftu</span><span class="sxs-lookup"><span data-stu-id="e56f7-108">Register the Microsoft key</span></span>
- <span data-ttu-id="e56f7-109">registrace úložiště produktu</span><span class="sxs-lookup"><span data-stu-id="e56f7-109">register the product repository</span></span>
- <span data-ttu-id="e56f7-110">Nainstalovat požadované závislosti</span><span class="sxs-lookup"><span data-stu-id="e56f7-110">Install required dependencies</span></span>

<span data-ttu-id="e56f7-111">Tento postup je třeba provést pouze jednou pro každý počítač.</span><span class="sxs-lookup"><span data-stu-id="e56f7-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e56f7-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e56f7-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e56f7-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e56f7-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="e56f7-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e56f7-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e56f7-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e56f7-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e56f7-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e56f7-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e56f7-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e56f7-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="e56f7-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e56f7-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e56f7-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="e56f7-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="e56f7-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e56f7-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e56f7-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e56f7-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e56f7-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="e56f7-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
