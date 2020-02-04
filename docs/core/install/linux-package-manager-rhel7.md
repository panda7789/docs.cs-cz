---
title: Nainstalovat .NET Core na Linux RHEL 7 Package Manager – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980181"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="7b806-103">Správce balíčků RHEL 7 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b806-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="7b806-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="7b806-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="7b806-105">Zaregistrujte si předplatné Red Hat</span><span class="sxs-lookup"><span data-stu-id="7b806-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="7b806-106">Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat.</span><span class="sxs-lookup"><span data-stu-id="7b806-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="7b806-107">Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="7b806-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7b806-108">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7b806-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="7b806-109">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7b806-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="7b806-110">V terminálu spuštěním následujících příkazů povolte kanál dotnet RHEL 7 a nainstalujte.</span><span class="sxs-lookup"><span data-stu-id="7b806-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7b806-111">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7b806-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="7b806-112">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b806-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="7b806-113">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="7b806-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7b806-114">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b806-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="7b806-115">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b806-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="7b806-116">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="7b806-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="7b806-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b806-117">See also</span></span>

- [<span data-ttu-id="7b806-118">Použití .NET Core 3,1 na Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="7b806-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
