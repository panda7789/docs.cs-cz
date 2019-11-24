---
title: Install .NET Core on SLES 12 - package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on SLES 12.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 23578baacaf3b739f57bdf860d980e2921e2c7ef
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450959"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="e5043-103">SLES 12 Package Manager - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5043-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e5043-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span><span class="sxs-lookup"><span data-stu-id="e5043-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span> <span data-ttu-id="e5043-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span><span class="sxs-lookup"><span data-stu-id="e5043-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="e5043-106">Register Microsoft key and feed</span><span class="sxs-lookup"><span data-stu-id="e5043-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="e5043-107">Before installing .NET, you'll need to:</span><span class="sxs-lookup"><span data-stu-id="e5043-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e5043-108">Register the Microsoft key</span><span class="sxs-lookup"><span data-stu-id="e5043-108">Register the Microsoft key</span></span>
- <span data-ttu-id="e5043-109">register the product repository</span><span class="sxs-lookup"><span data-stu-id="e5043-109">register the product repository</span></span>
- <span data-ttu-id="e5043-110">Install required dependencies</span><span class="sxs-lookup"><span data-stu-id="e5043-110">Install required dependencies</span></span>

<span data-ttu-id="e5043-111">This only needs to be done once per machine.</span><span class="sxs-lookup"><span data-stu-id="e5043-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e5043-112">Open a terminal and run the following command.</span><span class="sxs-lookup"><span data-stu-id="e5043-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e5043-113">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e5043-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="e5043-114">Update the products available for installation, then install the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e5043-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e5043-115">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="e5043-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e5043-116">Install the ASP.NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="e5043-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e5043-117">Update the products available for installation, then install the ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="e5043-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="e5043-118">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="e5043-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e5043-119">Install the .NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="e5043-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="e5043-120">Update the products available for installation, then install the .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="e5043-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e5043-121">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="e5043-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e5043-122">How to install other versions</span><span class="sxs-lookup"><span data-stu-id="e5043-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
