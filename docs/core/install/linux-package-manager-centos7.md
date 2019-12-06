---
title: Instalace .NET Core na CentOS 7 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: cb65811d5cae5c747c2660b4b10486f3162b9f33
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836939"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="79767-103">Správce balíčků CentOS 7 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="79767-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="79767-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="79767-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="79767-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="79767-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="79767-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="79767-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="79767-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="79767-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="79767-108">Registrace klíče Microsoftu</span><span class="sxs-lookup"><span data-stu-id="79767-108">Register the Microsoft key</span></span>
- <span data-ttu-id="79767-109">registrace úložiště produktu</span><span class="sxs-lookup"><span data-stu-id="79767-109">register the product repository</span></span>
- <span data-ttu-id="79767-110">Nainstalovat požadované závislosti</span><span class="sxs-lookup"><span data-stu-id="79767-110">Install required dependencies</span></span>

<span data-ttu-id="79767-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="79767-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="79767-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="79767-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="79767-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="79767-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="79767-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="79767-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="79767-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="79767-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="79767-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="79767-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="79767-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="79767-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="79767-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="79767-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="79767-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="79767-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="79767-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79767-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="79767-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="79767-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="79767-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="79767-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
