---
title: Instalace .NET Core na openSUSE 15 - správce balíčků - .NET Core
description: Pomocí správce balíčků nainstalujte .NET Core SDK a runtime na openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: fc4c9e30ddb0cfd3e6fe79fa4f78206f4700eeee
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645666"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="e052b-103">openSUSE 15 Správce balíčků - Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="e052b-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e052b-104">Tento článek popisuje, jak pomocí správce balíčků nainstalovat .NET Core na openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="e052b-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="e052b-105">Přidání klíče a informačního kanálu úložiště Microsoft</span><span class="sxs-lookup"><span data-stu-id="e052b-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="e052b-106">Před instalací rozhraní .NET budete muset:</span><span class="sxs-lookup"><span data-stu-id="e052b-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e052b-107">Přidejte podpisový klíč balíčku Microsoft do seznamu důvěryhodných klíčů.</span><span class="sxs-lookup"><span data-stu-id="e052b-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="e052b-108">Přidejte úložiště do správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="e052b-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="e052b-109">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="e052b-109">Install required dependencies.</span></span>

<span data-ttu-id="e052b-110">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="e052b-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e052b-111">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="e052b-111">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e052b-112">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e052b-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="e052b-113">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e052b-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e052b-114">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e052b-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e052b-115">ASP.NET Instalace core runtime</span><span class="sxs-lookup"><span data-stu-id="e052b-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e052b-116">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="e052b-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="e052b-117">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e052b-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e052b-118">Instalace runtime jádra .NET</span><span class="sxs-lookup"><span data-stu-id="e052b-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="e052b-119">Aktualizujte produkty, které jsou k dispozici pro instalaci, a nainstalujte za běhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e052b-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e052b-120">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e052b-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e052b-121">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="e052b-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="e052b-122">Poradce při potížích se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="e052b-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="e052b-123">Tato část obsahuje informace o běžných chybách, které se mohou stát při instalaci rozhraní .NET Core pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="e052b-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="e052b-124">Načtení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e052b-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
