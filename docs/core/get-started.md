---
title: Začínáme s .NET Core
description: Vyhledejte prostředky, které se naučíte sestavovat aplikace .NET Core v systémech Windows, Linux a macOS.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 56eebc0fc5bad6f57d93358cbbef389d6355d66b
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656687"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="87744-103">Začínáme s .NET Core</span><span class="sxs-lookup"><span data-stu-id="87744-103">Get started with .NET Core</span></span>

<span data-ttu-id="87744-104">Tento článek poskytuje informace o tom, jak začít s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87744-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="87744-105">.NET Core se dá nainstalovat na Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="87744-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="87744-106">Můžete kódovat ve svém oblíbeném textovém editoru a vytvářejte knihovny a aplikace pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="87744-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="87744-107">Pokud si nejste jistí, co je .NET Core nebo jak souvisí s dalšími technologiemi .NET, začněte s přehledem [co je .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="87744-107">If you're unsure what .NET Core is or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="87744-108">Jednoduše řečeno, .NET Core je open source implementace .NET pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="87744-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="87744-109">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="87744-109">Create an application</span></span>

<span data-ttu-id="87744-110">Nejprve Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download) do počítače.</span><span class="sxs-lookup"><span data-stu-id="87744-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="87744-111">Pak otevřete terminál, jako je například **PowerShell**, **příkazový řádek**nebo **bash**.</span><span class="sxs-lookup"><span data-stu-id="87744-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="87744-112">Zadejte následující `dotnet` příkazy pro vytvoření a spuštění aplikace v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="87744-112">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="87744-113">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="87744-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="87744-114">Congratulations!</span><span class="sxs-lookup"><span data-stu-id="87744-114">Congratulations!</span></span> <span data-ttu-id="87744-115">Vytvořili jste jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87744-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="87744-116">K vytvoření aplikace .NET Core můžete použít taky [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (jenom Windows) nebo [Visual Studio pro Mac](tutorials/with-visual-studio-mac.md) (jenom MacOS).</span><span class="sxs-lookup"><span data-stu-id="87744-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="87744-117">Kurzy</span><span class="sxs-lookup"><span data-stu-id="87744-117">Tutorials</span></span>

<span data-ttu-id="87744-118">Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="87744-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="87744-119">Windows</span><span class="sxs-lookup"><span data-stu-id="87744-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="87744-120">Vytvoření první konzolové aplikace .NET Core v aplikaci Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="87744-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="87744-121">Sestavení knihovny tříd pomocí .NET Standard v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87744-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="87744-122">Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="87744-122">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="87744-123">![ikona filmové kamery pro video](./media/video-icon.png "Přehrát video")</span><span class="sxs-lookup"><span data-stu-id="87744-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="87744-124">Podívejte se, [Jak nainstalovat a používat Visual Studio Code a video .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) na Channel 9.</span><span class="sxs-lookup"><span data-stu-id="87744-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="87744-125">![ikona filmové kamery pro video](./media/video-icon.png "Přehrát video")</span><span class="sxs-lookup"><span data-stu-id="87744-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="87744-126">Podívejte se na videa k [platformě .NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) na YouTube.</span><span class="sxs-lookup"><span data-stu-id="87744-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="87744-127">Seznam podporovaných verzí Windows najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="87744-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="87744-128">Linux</span><span class="sxs-lookup"><span data-stu-id="87744-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="87744-129">Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="87744-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="87744-130">Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="87744-130">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="87744-131">![ikona filmové kamery pro video](./media/video-icon.png "Přehrát video")</span><span class="sxs-lookup"><span data-stu-id="87744-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="87744-132">Podívejte se na video o [zahájení práce s Visual Studio Code pomocí C# a .NET Core v Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="87744-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="87744-133">Seznam podporovaných distribuce a verzí pro Linux najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-linux) .</span><span class="sxs-lookup"><span data-stu-id="87744-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="87744-134">macOS</span><span class="sxs-lookup"><span data-stu-id="87744-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="87744-135">Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="87744-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="87744-136">Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="87744-136">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)
- [<span data-ttu-id="87744-137">Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="87744-137">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>](tutorials/with-visual-studio-mac.md)
- [<span data-ttu-id="87744-138">Sestavení knihovny .NET Standard v macOS pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="87744-138">Build a .NET Standard library on macOS using Visual Studio for Mac</span></span>](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| <span data-ttu-id="87744-139">![ikona filmové kamery pro video](media/video-icon.png "Přehrát video")</span><span class="sxs-lookup"><span data-stu-id="87744-139">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="87744-140">Podívejte se na video o [zahájení práce s Visual Studio Code pomocí C# a .NET Core v MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="87744-140">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="87744-141">Seznam podporovaných verzí OS X/macOS najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-macos) .</span><span class="sxs-lookup"><span data-stu-id="87744-141">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
