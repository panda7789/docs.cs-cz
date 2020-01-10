---
title: Instalace .NET Core na openSUSE 15 – správce balíčků – .NET Core
description: Pomocí Správce balíčků nainstalujte .NET Core SDK a modul runtime v openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740667"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="25c45-103">Správce balíčků openSUSE 15 – instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="25c45-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="25c45-104">Tento článek popisuje, jak pomocí Správce balíčků nainstalovat .NET Core na openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="25c45-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="25c45-105">Pokud instalujete modul runtime, doporučujeme nainstalovat modul [runtime ASP.NET Core](#install-the-aspnet-core-runtime), protože zahrnuje modul runtime .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="25c45-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="25c45-106">Registrace klíče Microsoft a informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="25c45-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="25c45-107">Před instalací .NET budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="25c45-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="25c45-108">Zaregistrujte si klíč Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25c45-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="25c45-109">Zaregistrujte úložiště produktu.</span><span class="sxs-lookup"><span data-stu-id="25c45-109">Register the product repository.</span></span>
- <span data-ttu-id="25c45-110">Nainstalujte požadované závislosti.</span><span class="sxs-lookup"><span data-stu-id="25c45-110">Install required dependencies.</span></span>

<span data-ttu-id="25c45-111">Stačí to provést jednou na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="25c45-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="25c45-112">Otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="25c45-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a><span data-ttu-id="25c45-113">Chyba závislosti s .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="25c45-113">Dependency error with .NET Core 3.1</span></span>

<span data-ttu-id="25c45-114">Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** .</span><span class="sxs-lookup"><span data-stu-id="25c45-114">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="25c45-115">Před instalací .NET Core 3,1 nebo ASP.NET Core 3,1 nainstalujte správné závislosti pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="25c45-115">Use the following command to install the correct dependencies prior to installing .NET Core 3.1 or ASP.NET Core 3.1.</span></span>

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="25c45-116">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="25c45-116">Install the .NET Core SDK</span></span>

<span data-ttu-id="25c45-117">Aktualizujte produkty, které jsou k dispozici pro instalaci, a poté nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="25c45-117">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="25c45-118">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="25c45-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="25c45-119">Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** .</span><span class="sxs-lookup"><span data-stu-id="25c45-119">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="25c45-120">Pomocí následujícího příkazu nainstalujte správné závislosti a pak nainstalujte sadu .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="25c45-120">Use the following command to install the correct dependencies, then install the .NET Core 3.1 SDK.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="25c45-121">Instalace modulu runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25c45-121">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="25c45-122">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="25c45-122">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="25c45-123">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="25c45-123">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="25c45-124">Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** .</span><span class="sxs-lookup"><span data-stu-id="25c45-124">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="25c45-125">Pomocí následujícího příkazu nainstalujte správné závislosti a pak nainstalujte modul runtime ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="25c45-125">Use the following command to install the correct dependencies, then install the ASP.NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="25c45-126">Instalace modulu runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="25c45-126">Install the .NET Core runtime</span></span>

<span data-ttu-id="25c45-127">Aktualizujte produkty, které jsou k dispozici pro instalaci, a pak nainstalujte modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25c45-127">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="25c45-128">V terminálu spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="25c45-128">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="25c45-129">Informační kanál balíčku .NET Core 3,1 pro openSUSE má problém se závislostí **krb5** .</span><span class="sxs-lookup"><span data-stu-id="25c45-129">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="25c45-130">Pomocí následujícího příkazu nainstalujte správné závislosti a pak nainstalujte modul runtime .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="25c45-130">Use the following command to install the correct dependencies, then install the .NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="25c45-131">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="25c45-131">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
