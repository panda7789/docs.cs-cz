---
title: Úvod k .NET Core a přehled
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a macOS. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226579"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="9f0f2-104">Úvod do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f0f2-104">Introduction to .NET Core</span></span>

<span data-ttu-id="9f0f2-105">[.NET Core](about.md) je [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely.</span><span class="sxs-lookup"><span data-stu-id="9f0f2-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="9f0f2-106">Můžete vytvářet aplikace .NET Core pro Windows, macOS a Linux pro procesory x64, x86, ARM32 a ARM64 pomocí několika programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="9f0f2-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="9f0f2-107">K dispozici jsou architektury a rozhraní API pro [Cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [klientské uživatelské rozhraní](../desktop-wpf/overview/index.md)a [strojové učení](/dotnet/machine-learning/).</span><span class="sxs-lookup"><span data-stu-id="9f0f2-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="9f0f2-108">[Stáhněte si .NET Core SDK](https://dotnet.microsoft.com/download) a vyzkoušejte na svém počítači .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f0f2-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="9f0f2-109">Nejnovější verze je [.NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="9f0f2-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="9f0f2-110">Stáhnout .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f0f2-110">Download .NET Core</span></span>

<span data-ttu-id="9f0f2-111">.NET Core můžete získat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="9f0f2-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="9f0f2-112">Instalační programy pro Windows a macOS</span><span class="sxs-lookup"><span data-stu-id="9f0f2-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="9f0f2-113">Balíčky Linux</span><span class="sxs-lookup"><span data-stu-id="9f0f2-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="9f0f2-114">Kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="9f0f2-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="9f0f2-115">Zips a tarballs</span><span class="sxs-lookup"><span data-stu-id="9f0f2-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="9f0f2-116">Nainstalovat skripty</span><span class="sxs-lookup"><span data-stu-id="9f0f2-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="9f0f2-117">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="9f0f2-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="9f0f2-118">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="9f0f2-118">Create your first application</span></span>

<span data-ttu-id="9f0f2-119">Po instalaci .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="9f0f2-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="9f0f2-120">K vytvoření a spuštění aplikace použijte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="9f0f2-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="9f0f2-121">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9f0f2-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="9f0f2-122">Přispět</span><span class="sxs-lookup"><span data-stu-id="9f0f2-122">Contribute</span></span>

<span data-ttu-id="9f0f2-123">.NET Core je otevřená platforma.</span><span class="sxs-lookup"><span data-stu-id="9f0f2-123">.NET Core is an open platform.</span></span> <span data-ttu-id="9f0f2-124">Všichni uživatelé jsou vítají účast.</span><span class="sxs-lookup"><span data-stu-id="9f0f2-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="9f0f2-125">Problémy se souborovým produktem a dotazy na [komunitě vývojářů](https://developercommunity.visualstudio.com/spaces/61/index.html).</span><span class="sxs-lookup"><span data-stu-id="9f0f2-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="9f0f2-126">Příspěvky na produkt by se měly provádět v jednom z úložišť projektů, jako je například [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/SDK](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn)nebo [aspnetcore](https://github.com/dotnet/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="9f0f2-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="9f0f2-127">Další informace najdete v tématu [úložišť .NET Core](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="9f0f2-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="9f0f2-128">Podpora</span><span class="sxs-lookup"><span data-stu-id="9f0f2-128">Support</span></span>

<span data-ttu-id="9f0f2-129">.NET Core podporuje Microsoft na Windows, macOS a Linux a Red Hat na Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="9f0f2-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9f0f2-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9f0f2-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f0f2-131">Kurzy k .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f0f2-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f0f2-132">Vyzkoušejte .NET Core v prohlížeči</span><span class="sxs-lookup"><span data-stu-id="9f0f2-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
