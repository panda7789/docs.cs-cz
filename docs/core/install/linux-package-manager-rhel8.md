---
title: Instalace .NET Core na Linux RHEL 8 správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte sadu .NET Core SDK a runtime na RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849808"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="695c9-103">Správce balíčků RHEL 8 – instalace jádra .NET</span><span class="sxs-lookup"><span data-stu-id="695c9-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="695c9-104">Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="695c9-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="695c9-105">Registrace předplatného Red Hatu</span><span class="sxs-lookup"><span data-stu-id="695c9-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="695c9-106">Chcete-li nainstalovat .NET Core z Red Hat na RHEL, musíte se nejprve zaregistrovat pomocí Správce předplatného Red Hat.</span><span class="sxs-lookup"><span data-stu-id="695c9-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="695c9-107">Pokud se tak v systému nestalo nebo si nejste jisti, přečtěte si [dokumentaci k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="695c9-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="695c9-108">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="695c9-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="695c9-109">Po registraci ve Správci předplatného jste připraveni k instalaci a povolení sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="695c9-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="695c9-110">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="695c9-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="695c9-111">Instalace ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="695c9-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="695c9-112">Po registraci u Správce předplatného jste připraveni nainstalovat a povolit ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="695c9-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="695c9-113">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="695c9-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="695c9-114">Instalace rozhraní .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="695c9-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="695c9-115">Po registraci ve Správci předplatného jste připraveni k instalaci a povolení rozhraní .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="695c9-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="695c9-116">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="695c9-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="695c9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="695c9-117">See also</span></span>

- [<span data-ttu-id="695c9-118">Použití rozhraní .NET Core 3.1 na Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="695c9-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
