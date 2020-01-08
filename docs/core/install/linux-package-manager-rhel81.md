---
title: Nainstalovat .NET Core na Linux RHEL 8,1 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8674b5d9d0f0ee384ca6798a7ea699bad67c5e5e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341195"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="e4c31-103">Správce balíčků RHEL 8,1 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="e4c31-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="e4c31-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="e4c31-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="e4c31-105">.NET Core 3,1 není ještě k dispozici pro RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="e4c31-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="e4c31-106">RHEL 8,0 nezahrnuje .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e4c31-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="e4c31-107">K aktualizaci na RHEL 8,1 použijte příkaz `yum upgrade`.</span><span class="sxs-lookup"><span data-stu-id="e4c31-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="e4c31-108">Zaregistrujte si předplatné Red Hat</span><span class="sxs-lookup"><span data-stu-id="e4c31-108">Register your Red Hat subscription</span></span>

<span data-ttu-id="e4c31-109">Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat.</span><span class="sxs-lookup"><span data-stu-id="e4c31-109">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="e4c31-110">Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="e4c31-110">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e4c31-111">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e4c31-111">Install the .NET Core SDK</span></span>

<span data-ttu-id="e4c31-112">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e4c31-112">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="e4c31-113">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="e4c31-113">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e4c31-114">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e4c31-114">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="e4c31-115">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4c31-115">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="e4c31-116">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="e4c31-116">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e4c31-117">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="e4c31-117">Install the .NET Core Runtime</span></span>

<span data-ttu-id="e4c31-118">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4c31-118">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="e4c31-119">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="e4c31-119">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="e4c31-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4c31-120">See also</span></span>

- [<span data-ttu-id="e4c31-121">Použití .NET Core 3,0 na Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="e4c31-121">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
