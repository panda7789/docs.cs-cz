---
title: Začínáme s .NET Core
description: Vyhledejte prostředky, které se naučíte sestavovat aplikace .NET Core v systémech Windows, Linux a macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bcf9ea0bb9a8346284c49060786afefa0f77745e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341401"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="04fa2-103">Začínáme s .NET Core</span><span class="sxs-lookup"><span data-stu-id="04fa2-103">Get started with .NET Core</span></span>

<span data-ttu-id="04fa2-104">Tento článek poskytuje informace o tom, jak začít s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="04fa2-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="04fa2-105">.NET Core se dá nainstalovat na Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="04fa2-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="04fa2-106">Můžete kódovat ve svém oblíbeném textovém editoru a vytvářejte knihovny a aplikace pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="04fa2-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="04fa2-107">Pokud si nejste jistí, co je .NET Core nebo jak souvisí s dalšími technologiemi .NET, začněte s přehledem [co je .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="04fa2-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="04fa2-108">Jednoduše řečeno, .NET Core je open source implementace .NET pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="04fa2-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="04fa2-109">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="04fa2-109">Create an application</span></span>

<span data-ttu-id="04fa2-110">Nejprve Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download) do počítače.</span><span class="sxs-lookup"><span data-stu-id="04fa2-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="04fa2-111">Pak otevřete terminál, jako je například **PowerShell**, **příkazový řádek**nebo **bash**.</span><span class="sxs-lookup"><span data-stu-id="04fa2-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="04fa2-112">Zadejte následující `dotnet` příkazy pro vytvoření a spuštění C# aplikace:</span><span class="sxs-lookup"><span data-stu-id="04fa2-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="04fa2-113">Měli byste vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="04fa2-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="04fa2-114">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="04fa2-114">Congratulations!</span></span> <span data-ttu-id="04fa2-115">Vytvořili jste jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="04fa2-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="04fa2-116">K vytvoření aplikace .NET Core můžete použít taky [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (jenom Windows) nebo [Visual Studio pro Mac](./tutorials/using-on-mac-vs.md) (jenom MacOS).</span><span class="sxs-lookup"><span data-stu-id="04fa2-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="04fa2-117">Kurzy</span><span class="sxs-lookup"><span data-stu-id="04fa2-117">Tutorials</span></span>

<span data-ttu-id="04fa2-118">Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="04fa2-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="04fa2-119">Windows</span><span class="sxs-lookup"><span data-stu-id="04fa2-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="04fa2-120">Vytvoření první konzolové aplikace .NET Core v aplikaci Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="04fa2-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="04fa2-121">Sestavení knihovny tříd pomocí .NET Standard v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="04fa2-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="04fa2-122">Začínáme s .NET Core s využitím .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="04fa2-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="04fa2-123">![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="04fa2-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="04fa2-124">Podívejte se, [Jak nainstalovat a používat Visual Studio Code a video .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) na Channel 9.</span><span class="sxs-lookup"><span data-stu-id="04fa2-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="04fa2-125">![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="04fa2-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="04fa2-126">Podívejte se na videa k [platformě .NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) na YouTube.</span><span class="sxs-lookup"><span data-stu-id="04fa2-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="04fa2-127">Seznam podporovaných verzí Windows najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="04fa2-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span></span>

<span data-ttu-id="04fa2-128">Seznam podporovaných verzí Windows najdete v článku [.NET Core SDK a závislosti modulu runtime](install/dependencies.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="04fa2-128">See the [.NET Core SDK and runtime dependencies](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="04fa2-129">Linux</span><span class="sxs-lookup"><span data-stu-id="04fa2-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="04fa2-130">Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="04fa2-130">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="04fa2-131">Začínáme s .NET Core s využitím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="04fa2-131">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="04fa2-132">![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="04fa2-132">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="04fa2-133">Podívejte se na video o [zahájení práce s Visual Studio Code C# používání a .NET Core v Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="04fa2-133">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="04fa2-134">Seznam podporovaných distribuce a verzí pro Linux najdete v článku věnovaném [.NET Core SDK a závislostem modulu runtime](install/dependencies.md?pivots=os-linux) .</span><span class="sxs-lookup"><span data-stu-id="04fa2-134">See the [.NET Core SDK and runtime dependencies](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="04fa2-135">macOS</span><span class="sxs-lookup"><span data-stu-id="04fa2-135">macOS</span></span>](#tab/macos)

<span data-ttu-id="04fa2-136">Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="04fa2-136">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="04fa2-137">Začínáme s .NET Core v macOS pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="04fa2-137">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="04fa2-138">Začínáme s .NET Core s využitím příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="04fa2-138">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="04fa2-139">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="04fa2-139">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="04fa2-140">Sestavení kompletního řešení .NET Core na macOS pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="04fa2-140">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| <span data-ttu-id="04fa2-141">![ikona filmové kamery pro video](media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="04fa2-141">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="04fa2-142">Podívejte se na video o [zahájení práce s Visual Studio Code C# používání a .NET Core v MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="04fa2-142">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="04fa2-143">Seznam podporovaných verzí OS X/macOS najdete v článku věnovaném [.NET Core SDK a závislostem modulu runtime](install/dependencies.md?pivots=os-macos) .</span><span class="sxs-lookup"><span data-stu-id="04fa2-143">See the [.NET Core SDK and runtime dependencies](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
