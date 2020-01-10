---
title: Instalace .NET Core na CentOS 7 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a7b4a76d780714850fe0792f51f1fa1282f6525d
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740740"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="96c69-103">Správce balíčků CentOS 7 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="96c69-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="96c69-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="96c69-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="96c69-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="96c69-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="96c69-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="96c69-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="96c69-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="96c69-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="96c69-108">Zaregistrujte si klíč Microsoft.</span><span class="sxs-lookup"><span data-stu-id="96c69-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="96c69-109">Zaregistrujte úložiště produktu.</span><span class="sxs-lookup"><span data-stu-id="96c69-109">Register the product repository.</span></span>
- <span data-ttu-id="96c69-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="96c69-110">Install required dependencies.</span></span>

<span data-ttu-id="96c69-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="96c69-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="96c69-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="96c69-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="96c69-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="96c69-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="96c69-114">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="96c69-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="96c69-115">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="96c69-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="96c69-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="96c69-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="96c69-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="96c69-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="96c69-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="96c69-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="96c69-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="96c69-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="96c69-120">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96c69-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="96c69-121">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="96c69-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="96c69-122">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="96c69-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
