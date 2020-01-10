---
title: Instalace .NET Core v SLES 12 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v SLES 12.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a40180881ec0962d89f03c2c9d7aad9bbb052d2a
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740664"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="5f23b-103">Správce balíčků SLES 12 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f23b-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="5f23b-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na SLES 12.</span><span class="sxs-lookup"><span data-stu-id="5f23b-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span> <span data-ttu-id="5f23b-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f23b-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="5f23b-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="5f23b-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="5f23b-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="5f23b-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="5f23b-108">Zaregistrujte si klíč Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5f23b-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="5f23b-109">Zaregistrujte úložiště produktu.</span><span class="sxs-lookup"><span data-stu-id="5f23b-109">Register the product repository.</span></span>
- <span data-ttu-id="5f23b-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="5f23b-110">Install required dependencies.</span></span>

<span data-ttu-id="5f23b-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="5f23b-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="5f23b-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="5f23b-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="5f23b-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5f23b-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="5f23b-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5f23b-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="5f23b-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="5f23b-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="5f23b-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5f23b-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="5f23b-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5f23b-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="5f23b-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="5f23b-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="5f23b-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f23b-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="5f23b-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f23b-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="5f23b-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="5f23b-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5f23b-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="5f23b-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
