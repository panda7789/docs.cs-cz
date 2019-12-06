---
title: Nainstalovat .NET Core na Linux RHEL 8,1 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 3ef639d5b76e81856ec8370d10e098c455ca8b3d
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836925"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="25901-103">Správce balíčků RHEL 8,1 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="25901-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="25901-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="25901-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="25901-105">.NET Core 3,1 není ještě k dispozici pro RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="25901-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="25901-106">RHEL 8,0 nezahrnuje .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="25901-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="25901-107">K aktualizaci na RHEL 8,1 použijte příkaz `yum upgrade`.</span><span class="sxs-lookup"><span data-stu-id="25901-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="25901-108">RHEL 8,0 nezahrnuje .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="25901-108">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="25901-109">K aktualizaci na RHEL 8,1 použijte příkaz `yum upgrade`.</span><span class="sxs-lookup"><span data-stu-id="25901-109">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="25901-110">Zaregistrujte si předplatné Red Hat</span><span class="sxs-lookup"><span data-stu-id="25901-110">Register your Red Hat subscription</span></span>

<span data-ttu-id="25901-111">Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat.</span><span class="sxs-lookup"><span data-stu-id="25901-111">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="25901-112">Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="25901-112">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="25901-113">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="25901-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="25901-114">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="25901-114">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="25901-115">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25901-115">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="25901-116">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25901-116">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="25901-117">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="25901-117">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="25901-118">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25901-118">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="25901-119">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="25901-119">Install the .NET Core Runtime</span></span>

<span data-ttu-id="25901-120">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25901-120">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="25901-121">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25901-121">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="25901-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25901-122">See also</span></span>

- [<span data-ttu-id="25901-123">Použití .NET Core 3,0 na Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="25901-123">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
