---
title: Instalace .NET Core v Fedora 32 – Správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Fedora 32.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624964"
---
# <a name="fedora-32-package-manager---install-net-core"></a><span data-ttu-id="51b45-103">Správce balíčků Fedora 32 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="51b45-103">Fedora 32 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="51b45-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="51b45-104">This article describes how to use a package manager to install .NET Core on Fedora 32.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

<span data-ttu-id="51b45-105">Od Fedora 32 je .NET Core 3,1 k dispozici ve výchozích úložištích balíčků v Fedora.</span><span class="sxs-lookup"><span data-stu-id="51b45-105">Starting with Fedora 32, .NET Core 3.1 is available in the default package repositories in Fedora.</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="51b45-106">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="51b45-106">Install the .NET Core SDK</span></span>

<span data-ttu-id="51b45-107">Nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="51b45-107">Install the .NET Core SDK.</span></span> <span data-ttu-id="51b45-108">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="51b45-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="51b45-109">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="51b45-109">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="51b45-110">Nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="51b45-110">Install the ASP.NET runtime.</span></span> <span data-ttu-id="51b45-111">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="51b45-111">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="51b45-112">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="51b45-112">Install the .NET Core runtime</span></span>

<span data-ttu-id="51b45-113">Nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51b45-113">Install the .NET Core runtime.</span></span> <span data-ttu-id="51b45-114">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="51b45-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="51b45-115">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="51b45-115">How to install other versions</span></span>

<span data-ttu-id="51b45-116">Pokud chcete nainstalovat další verze .NET Core, nainstalujte [.NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) nebo [modul runtime .NET Core](runtime.md?pivots=os-linux#download-and-manually-install)ručně.</span><span class="sxs-lookup"><span data-stu-id="51b45-116">To install other versions of .NET Core, manually install [the .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) or [the .NET Core Runtime](runtime.md?pivots=os-linux#download-and-manually-install).</span></span>
