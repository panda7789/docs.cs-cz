---
title: Instalace .NET Core na Fedoru 31 - správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte na Fedoru 31 .NET Core SDK a runtime.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 28bda3676f99037e565080e1ff3f9d89a67d0d69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920785"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="27e68-103">Správce balíčků Fedora 31 – instalace jádra .NET</span><span class="sxs-lookup"><span data-stu-id="27e68-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="27e68-104">Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na Fedoru 31.</span><span class="sxs-lookup"><span data-stu-id="27e68-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="27e68-105">Pokud instalujete runtime, doporučujeme nainstalovat [ASP.NET core runtime](#install-the-aspnet-core-runtime), protože zahrnuje rozhraní .NET Core i ASP.NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="27e68-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="27e68-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="27e68-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="27e68-107">Před instalací rozhraní .NET budete muset:</span><span class="sxs-lookup"><span data-stu-id="27e68-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="27e68-108">Zaregistrujte klíč Společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="27e68-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="27e68-109">Zaregistrujte úložiště produktů.</span><span class="sxs-lookup"><span data-stu-id="27e68-109">Register the product repository.</span></span>
- <span data-ttu-id="27e68-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="27e68-110">Install required dependencies.</span></span>

<span data-ttu-id="27e68-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="27e68-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="27e68-112">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="27e68-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="27e68-113">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="27e68-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="27e68-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="27e68-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="27e68-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="27e68-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="27e68-116">ASP.NET Instalace core runtime</span><span class="sxs-lookup"><span data-stu-id="27e68-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="27e68-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="27e68-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="27e68-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="27e68-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="27e68-119">Instalace runtime jádra .NET</span><span class="sxs-lookup"><span data-stu-id="27e68-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="27e68-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="27e68-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="27e68-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="27e68-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="27e68-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="27e68-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="27e68-123">Poradce při potížích se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="27e68-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="27e68-124">Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="27e68-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="27e68-125">Načtení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="27e68-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
