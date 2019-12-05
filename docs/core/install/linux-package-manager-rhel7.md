---
title: Nainstalovat .NET Core na Linux RHEL 7 Package Manager – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: cc7865727927eda1406da26e64b89325fd5665a4
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801959"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="d82dc-103">Správce balíčků RHEL 7 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="d82dc-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="d82dc-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="d82dc-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="d82dc-105">Zaregistrujte si předplatné Red Hat</span><span class="sxs-lookup"><span data-stu-id="d82dc-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="d82dc-106">Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat.</span><span class="sxs-lookup"><span data-stu-id="d82dc-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="d82dc-107">Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="d82dc-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="d82dc-108">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d82dc-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="d82dc-109">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d82dc-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="d82dc-110">V terminálu spuštěním následujících příkazů povolte kanál dotnet RHEL 7 a nainstalujte.</span><span class="sxs-lookup"><span data-stu-id="d82dc-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install .</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="d82dc-111">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d82dc-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="d82dc-112">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d82dc-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="d82dc-113">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="d82dc-113">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="d82dc-114">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="d82dc-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="d82dc-115">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d82dc-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="d82dc-116">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="d82dc-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a><span data-ttu-id="d82dc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d82dc-117">See also</span></span>

- [<span data-ttu-id="d82dc-118">Použití .NET Core 3,0 na Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d82dc-118">Using .NET Core 3.0 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
