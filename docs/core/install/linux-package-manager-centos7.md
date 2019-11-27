---
title: Instalace .NET Core na CentOS 7 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 62b07342197addaa5c7d962c08c4ff1d7121eff8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451078"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="7019b-103">Správce balíčků CentOS 7 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="7019b-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7019b-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="7019b-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="7019b-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7019b-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="7019b-106">Registrace klíče a kanálu Microsoft</span><span class="sxs-lookup"><span data-stu-id="7019b-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="7019b-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="7019b-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7019b-108">Registrace klíče Microsoftu</span><span class="sxs-lookup"><span data-stu-id="7019b-108">Register the Microsoft key</span></span>
- <span data-ttu-id="7019b-109">registrace úložiště produktu</span><span class="sxs-lookup"><span data-stu-id="7019b-109">register the product repository</span></span>
- <span data-ttu-id="7019b-110">Nainstalovat požadované závislosti</span><span class="sxs-lookup"><span data-stu-id="7019b-110">Install required dependencies</span></span>

<span data-ttu-id="7019b-111">Tento postup je třeba provést pouze jednou pro každý počítač.</span><span class="sxs-lookup"><span data-stu-id="7019b-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7019b-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="7019b-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7019b-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7019b-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="7019b-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7019b-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7019b-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="7019b-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7019b-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7019b-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7019b-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7019b-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="7019b-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="7019b-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7019b-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="7019b-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="7019b-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7019b-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7019b-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="7019b-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7019b-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="7019b-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
