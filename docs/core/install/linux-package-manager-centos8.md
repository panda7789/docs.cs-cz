---
title: Nainstalovat .NET Core na Linux CentOS 8 Package Manager – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v CentOS 8.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: b4cf5975e18aa8dfa8649c0d038caf38d648ad86
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728517"
---
# <a name="centos-8-package-manager---install-net-core"></a><span data-ttu-id="b2b40-103">Správce balíčků CentOS 8 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2b40-103">CentOS 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="b2b40-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="b2b40-104">This article describes how to use a package manager to install .NET Core on CentOS 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="b2b40-105">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b2b40-105">Install the .NET Core SDK</span></span>

<span data-ttu-id="b2b40-106">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="b2b40-106">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="b2b40-107">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2b40-107">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="b2b40-108">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="b2b40-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="b2b40-109">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2b40-109">Install the .NET Core Runtime</span></span>

<span data-ttu-id="b2b40-110">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="b2b40-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b2b40-111">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="b2b40-111">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
