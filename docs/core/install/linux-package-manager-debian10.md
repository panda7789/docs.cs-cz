---
title: Instalace .NET Core na Debian 10 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v Debian 10.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 038f5579f99f700ce47dc67be2fd344f01cf800c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595613"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="1894f-103">Správce balíčků Debian 10 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="1894f-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="1894f-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na Debian 10.</span><span class="sxs-lookup"><span data-stu-id="1894f-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="1894f-105">Přidat klíč a kanál úložiště Microsoftu</span><span class="sxs-lookup"><span data-stu-id="1894f-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="1894f-106">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="1894f-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="1894f-107">Přidejte podpisový klíč Microsoft Package do seznamu důvěryhodných klíčů.</span><span class="sxs-lookup"><span data-stu-id="1894f-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="1894f-108">Přidejte úložiště do Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="1894f-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="1894f-109">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="1894f-109">Install required dependencies.</span></span>

<span data-ttu-id="1894f-110">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="1894f-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="1894f-111">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="1894f-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="1894f-112">Nainstalujte sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1894f-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="1894f-113">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1894f-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="1894f-114">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="1894f-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="1894f-115">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1894f-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="1894f-116">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1894f-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="1894f-117">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="1894f-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="1894f-118">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="1894f-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="1894f-119">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1894f-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="1894f-120">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="1894f-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1894f-121">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="1894f-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="1894f-122">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="1894f-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="1894f-123">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1894f-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="1894f-124">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="1894f-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
