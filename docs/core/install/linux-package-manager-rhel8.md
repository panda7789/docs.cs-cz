---
title: Nainstalovat .NET Core na Linux RHEL 8 Package Manager – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: 8829e842e920e6abd4184b5140f80bb016acace2
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728232"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="52d54-103">Správce balíčků RHEL 8 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="52d54-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="52d54-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Red Hat Enterprise Linux (RHEL) 8.</span><span class="sxs-lookup"><span data-stu-id="52d54-104">This article describes how to use a package manager to install .NET Core on Red Hat Enterprise Linux (RHEL) 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="52d54-105">Zaregistrujte si předplatné Red Hat</span><span class="sxs-lookup"><span data-stu-id="52d54-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="52d54-106">Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat.</span><span class="sxs-lookup"><span data-stu-id="52d54-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="52d54-107">Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="52d54-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="52d54-108">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="52d54-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="52d54-109">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="52d54-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="52d54-110">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="52d54-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="52d54-111">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="52d54-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="52d54-112">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="52d54-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="52d54-113">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="52d54-113">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="52d54-114">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="52d54-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="52d54-115">Po registraci pomocí Správce předplatného můžete nainstalovat a povolit modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="52d54-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="52d54-116">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="52d54-116">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="52d54-117">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="52d54-117">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="see-also"></a><span data-ttu-id="52d54-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="52d54-118">See also</span></span>

- [<span data-ttu-id="52d54-119">Použití .NET Core 3,1 na Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="52d54-119">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
