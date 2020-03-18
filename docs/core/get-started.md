---
title: Začínáme s rozhraním .NET Core
description: Najděte materiály, kde se dozvíte, jak vytvářet aplikace .NET Core ve Windows, Linuxu a macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714394"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="b6ad1-103">Začínáme s rozhraním .NET Core</span><span class="sxs-lookup"><span data-stu-id="b6ad1-103">Get started with .NET Core</span></span>

<span data-ttu-id="b6ad1-104">Tento článek obsahuje informace o začínáme s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="b6ad1-105">.NET Core lze nainstalovat do Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="b6ad1-106">Můžete kódovat ve svém oblíbeném textovém editoru a vytvářet knihovny a aplikace pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="b6ad1-107">Pokud si nejste jisti, co je jádro .NET core nebo jak se vztahuje k jiným technologiím .NET, začněte s přehledem [What is .NET.](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet)</span><span class="sxs-lookup"><span data-stu-id="b6ad1-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="b6ad1-108">Jednoduše řečeno, .NET Core je open source implementace .NET napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="b6ad1-109">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="b6ad1-109">Create an application</span></span>

<span data-ttu-id="b6ad1-110">Nejprve stáhněte a nainstalujte do počítače sadu [.NET Core SDK.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="b6ad1-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="b6ad1-111">Dále otevřete terminál, například **PowerShell**, **Příkazový řádek**nebo **bash**.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="b6ad1-112">Zadejte `dotnet` následující příkazy pro vytvoření a spuštění aplikace jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="b6ad1-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="b6ad1-113">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b6ad1-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="b6ad1-114">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="b6ad1-114">Congratulations!</span></span> <span data-ttu-id="b6ad1-115">Vytvořili jste jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="b6ad1-116">K vytvoření aplikace .NET Core můžete také použít [kód sady Visual Studio](./tutorials/with-visual-studio-code.md), Visual [Studio](./tutorials/with-visual-studio.md) (jenom windows) nebo Visual Studio [pro Mac](./tutorials/using-on-mac-vs.md) (pouze macOS).</span><span class="sxs-lookup"><span data-stu-id="b6ad1-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="b6ad1-117">Kurzy</span><span class="sxs-lookup"><span data-stu-id="b6ad1-117">Tutorials</span></span>

<span data-ttu-id="b6ad1-118">Začínáme s vývojem základních aplikací .NET podle těchto podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="b6ad1-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="b6ad1-119">Windows</span><span class="sxs-lookup"><span data-stu-id="b6ad1-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="b6ad1-120">Vytvoření první aplikace konzoly .NET Core ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="b6ad1-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="b6ad1-121">Vytvoření knihovny tříd se standardem .NET standard v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b6ad1-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="b6ad1-122">Začínáme s rozhraním .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="b6ad1-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="b6ad1-123">![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="b6ad1-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="b6ad1-124">Podívejte [se, jak nainstalovat a používat visual studio kód a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video na kanálu 9.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="b6ad1-125">![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="b6ad1-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="b6ad1-126">Podívejte se na videa [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) na YouTube.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="b6ad1-127">Seznam podporovaných verzí systému Windows naleznete v článku [závislosti a požadavky jádra .NET.](install/dependencies.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="b6ad1-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="b6ad1-128">Linux</span><span class="sxs-lookup"><span data-stu-id="b6ad1-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="b6ad1-129">Začínáme s vývojem základních aplikací .NET podle těchto podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="b6ad1-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="b6ad1-130">Začínáme s rozhraním .NET Core pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b6ad1-130">Get started with .NET Core using the command line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="b6ad1-131">![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="b6ad1-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="b6ad1-132">Podívejte se na video o [tom, jak začít s visual studio kód pomocí C# a .NET Core na Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="b6ad1-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="b6ad1-133">Seznam podporovaných distribucí a verzí linuxu naleznete v článku [o závislostech a požadavcích jádra .NET.](install/dependencies.md?pivots=os-linux)</span><span class="sxs-lookup"><span data-stu-id="b6ad1-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="b6ad1-134">Macos</span><span class="sxs-lookup"><span data-stu-id="b6ad1-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="b6ad1-135">Začínáme s vývojem základních aplikací .NET podle těchto podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="b6ad1-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="b6ad1-136">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b6ad1-136">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="b6ad1-137">Začínáme s rozhraním .NET Core pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b6ad1-137">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="b6ad1-138">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="b6ad1-138">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="b6ad1-139">Vytvoření kompletního řešení .NET Core na macOS pomocí Visual Studia pro Mac</span><span class="sxs-lookup"><span data-stu-id="b6ad1-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| <span data-ttu-id="b6ad1-140">![ikona filmové kamery pro video](media/video-icon.png "Podívejte se na video")</span><span class="sxs-lookup"><span data-stu-id="b6ad1-140">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="b6ad1-141">Podívejte se na video o [tom, jak začít s visual studio kód pomocí C# a .NET Core na macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="b6ad1-141">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="b6ad1-142">Seznam podporovaných verzí OS X / macOS najdete v článku [o závislostech a požadavcích jádra .NET.](install/dependencies.md?pivots=os-macos)</span><span class="sxs-lookup"><span data-stu-id="b6ad1-142">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
