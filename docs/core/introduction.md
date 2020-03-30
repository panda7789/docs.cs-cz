---
title: Úvod a přehled .NET Core
description: .NET Core je modulární, vysoce výkonná implementace rozhraní .NET pro vytváření aplikací pro Windows, Linux a macOS. Další informace o .NET Core pro started a) začínáme.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a20cdda5cbd366d04e7ee9e8df3d1b15d10c1f4a
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391158"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="1a576-104">Úvod do rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="1a576-104">Introduction to .NET Core</span></span>

<span data-ttu-id="1a576-105">[.NET Core](about.md) je [open-source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)univerzální vývojová platforma.</span><span class="sxs-lookup"><span data-stu-id="1a576-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="1a576-106">Můžete vytvářet aplikace .NET Core pro procesory Windows, macOS a Linux pro procesory x64, x86, ARM32 a ARM64 pomocí více programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="1a576-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="1a576-107">Architektury a rozhraní API jsou k dispozici pro [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [klientské ui](/dotnet/desktop-wpf/overview/index)a [strojové učení](/dotnet/machine-learning/).</span><span class="sxs-lookup"><span data-stu-id="1a576-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](/dotnet/desktop-wpf/overview/index), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="1a576-108">[Stáhněte si sdk jádra .NET a](https://dotnet.microsoft.com/download) vyzkoušejte v počítači .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1a576-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="1a576-109">Nejnovější verze je [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="1a576-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="1a576-110">Stáhnout jádro rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="1a576-110">Download .NET Core</span></span>

<span data-ttu-id="1a576-111">Jádro .NET můžete získat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="1a576-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="1a576-112">Instalační programy pro Windows a macOS</span><span class="sxs-lookup"><span data-stu-id="1a576-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="1a576-113">Balíčky linuxu</span><span class="sxs-lookup"><span data-stu-id="1a576-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="1a576-114">Kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="1a576-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="1a576-115">Zipy a dehtové kuličky</span><span class="sxs-lookup"><span data-stu-id="1a576-115">Zips and tar balls</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="1a576-116">Instalace skriptů</span><span class="sxs-lookup"><span data-stu-id="1a576-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="1a576-117">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="1a576-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="1a576-118">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="1a576-118">Create your first application</span></span>

<span data-ttu-id="1a576-119">Po instalaci sady .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="1a576-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="1a576-120">K vytvoření a spuštění aplikace použijte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="1a576-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="1a576-121">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1a576-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="1a576-122">Přispět</span><span class="sxs-lookup"><span data-stu-id="1a576-122">Contribute</span></span>

<span data-ttu-id="1a576-123">.NET Core je otevřená platforma.</span><span class="sxs-lookup"><span data-stu-id="1a576-123">.NET Core is an open platform.</span></span> <span data-ttu-id="1a576-124">Všichni jsou vítáni k účasti.</span><span class="sxs-lookup"><span data-stu-id="1a576-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="1a576-125">Soubor problémy s produkty a otázky na [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="1a576-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="1a576-126">Příspěvky na produkt by měly být provedeny v jednom z úložišť projektů, jako je [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn)nebo [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="1a576-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="1a576-127">Další informace naleznete [v tématu úložiště jádra .NET](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="1a576-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="1a576-128">Podpora</span><span class="sxs-lookup"><span data-stu-id="1a576-128">Support</span></span>

<span data-ttu-id="1a576-129">.NET Core je podporován společností Microsoft v systémech Windows, macOS a Linux a Red Hat na Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="1a576-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1a576-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1a576-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1a576-131">Kurzy jádra .NET</span><span class="sxs-lookup"><span data-stu-id="1a576-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="1a576-132">Vyzkoušejte v prohlížeči rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="1a576-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
