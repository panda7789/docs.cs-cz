---
title: Předpoklady pro .NET Core na Macu
description: Podporované verze macOS a závislosti rozhraní .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na macOS počítačích.
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 09/27/2019
ms.openlocfilehash: 13eea0043be9cf5d5574d6b38f144853c22e8d07
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591687"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="0152f-103">Předpoklady pro .NET Core v macOS</span><span class="sxs-lookup"><span data-stu-id="0152f-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="0152f-104">V tomto článku se dozvíte o podporovaných verzích macOS a závislostech .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core na počítačích s macOS.</span><span class="sxs-lookup"><span data-stu-id="0152f-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="0152f-105">Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core na Macu: prostřednictvím [příkazového řádku s oblíbeným editorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="0152f-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="downloads-and-dependencies"></a><span data-ttu-id="0152f-106">Soubory ke stažení a závislosti</span><span class="sxs-lookup"><span data-stu-id="0152f-106">Downloads and dependencies</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="0152f-107">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0152f-107">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="0152f-108">.NET Core 3,0 se podporuje na **MacOS vysokých Sierra (verze 10,13)** a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="0152f-108">.NET Core 3.0 is supported on **macOS High Sierra (version 10.13)** and later versions.</span></span> <span data-ttu-id="0152f-109">Je vyžadována architektura procesoru **x64** .</span><span class="sxs-lookup"><span data-stu-id="0152f-109">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="0152f-110">Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0) .</span><span class="sxs-lookup"><span data-stu-id="0152f-110">Download and install the .NET Core SDK from the [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) page.</span></span> <span data-ttu-id="0152f-111">[Podporované verze operačního systému .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pro úplný seznam podporovaných operačních systémů pro .net Core 3,0, distribucí a verzí, nepodporovaných verzí operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="0152f-111">[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="0152f-112">Seznam známých problémů najdete v tématu [známé problémy .NET Core](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="0152f-112">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="0152f-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="0152f-113">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="0152f-114">.NET Core 2,2 se podporuje na **MacOS Sierra (verze 10,12)** a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="0152f-114">.NET Core 2.2 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="0152f-115">Je vyžadována architektura procesoru **x64** .</span><span class="sxs-lookup"><span data-stu-id="0152f-115">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="0152f-116">Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) .</span><span class="sxs-lookup"><span data-stu-id="0152f-116">Download and install the .NET Core SDK from the [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) page.</span></span> <span data-ttu-id="0152f-117">[Podporované verze operačního systému .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pro úplný seznam podporovaných operačních systémů pro .net Core 2,2, distribucí a verzí, nepodporovaných verzí operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="0152f-117">[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="0152f-118">Seznam známých problémů najdete v tématu [známé problémy .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="0152f-118">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0152f-119">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0152f-119">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0152f-120">.NET Core 2,1 se podporuje na **MacOS Sierra (verze 10,12)** a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="0152f-120">.NET Core 2.1 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="0152f-121">Je vyžadována architektura procesoru **x64** .</span><span class="sxs-lookup"><span data-stu-id="0152f-121">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="0152f-122">Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) .</span><span class="sxs-lookup"><span data-stu-id="0152f-122">Download and install the .NET Core SDK from the [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1) page.</span></span> <span data-ttu-id="0152f-123">[Podporované verze operačního systému .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pro úplný seznam podporovaných operačních systémů pro .net Core 2,1, distribucí a verzí, nepodporovaných verzí operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="0152f-123">[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="0152f-124">Seznam známých problémů najdete v tématu [známé problémy .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="0152f-124">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).</span></span>

---

## <a name="visual-studio-for-mac"></a><span data-ttu-id="0152f-125">Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="0152f-125">Visual Studio for Mac</span></span>

<span data-ttu-id="0152f-126">K vývoji aplikací .NET Core pomocí .NET Core SDK můžete použít libovolný editor.</span><span class="sxs-lookup"><span data-stu-id="0152f-126">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="0152f-127">Pokud ale chcete vyvíjet aplikace .NET Core na Macu v integrovaném vývojovém prostředí, můžete použít [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="0152f-127">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>
