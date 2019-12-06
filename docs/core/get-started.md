---
title: Začínáme s .NET Core
description: Vyhledejte prostředky, které se naučíte sestavovat aplikace .NET Core v systémech Windows, Linux a macOS.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 89db6d79336c01315983133d9041904d88cba301
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884251"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="a966d-103">Začínáme s .NET Core</span><span class="sxs-lookup"><span data-stu-id="a966d-103">Get started with .NET Core</span></span>

<span data-ttu-id="a966d-104">Tento článek poskytuje informace o tom, jak začít s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a966d-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="a966d-105">.NET Core se dá nainstalovat na Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="a966d-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="a966d-106">Můžete kódovat ve svém oblíbeném textovém editoru a vytvářejte knihovny a aplikace pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="a966d-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="a966d-107">Pokud si nejste jistí, co je .NET Core nebo jak souvisí s dalšími technologiemi .NET, začněte s přehledem [co je .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="a966d-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="a966d-108">Jednoduše řečeno, .NET Core je open source implementace .NET pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="a966d-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="a966d-109">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="a966d-109">Create an application</span></span>

<span data-ttu-id="a966d-110">Nejprve Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download) do počítače.</span><span class="sxs-lookup"><span data-stu-id="a966d-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="a966d-111">Pak otevřete terminál, jako je například **PowerShell**, **příkazový řádek**nebo **bash**.</span><span class="sxs-lookup"><span data-stu-id="a966d-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="a966d-112">Zadejte následující `dotnet` příkazy pro vytvoření a spuštění C# aplikace:</span><span class="sxs-lookup"><span data-stu-id="a966d-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="a966d-113">Měli byste vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a966d-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="a966d-114">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="a966d-114">Congratulations!</span></span> <span data-ttu-id="a966d-115">Vytvořili jste jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a966d-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="a966d-116">K vytvoření aplikace .NET Core můžete použít taky [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (jenom Windows) nebo [Visual Studio pro Mac](tutorials/using-on-mac-vs.md) (jenom MacOS).</span><span class="sxs-lookup"><span data-stu-id="a966d-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="a966d-117">Kurzy</span><span class="sxs-lookup"><span data-stu-id="a966d-117">Tutorials</span></span>

<span data-ttu-id="a966d-118">Můžete začít vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů.</span><span class="sxs-lookup"><span data-stu-id="a966d-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="a966d-119">Windows</span><span class="sxs-lookup"><span data-stu-id="a966d-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="a966d-120">Sestavte aplikaci C# "Hello World" pomocí .NET Core v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a966d-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="a966d-121">Sestavte knihovnu C# tříd pomocí .NET Core v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a966d-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="a966d-122">Sestavte Visual Basic aplikaci Hello World pomocí .NET Core v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a966d-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)
- [<span data-ttu-id="a966d-123">Sestavte knihovnu tříd pomocí Visual Basic a .NET Core v aplikaci Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a966d-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  
- <span data-ttu-id="a966d-124">Podívejte se na video o [tom, jak nainstalovat a používat Visual Studio Code a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="a966d-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>
- <span data-ttu-id="a966d-125">Podívejte se na video o [instalaci a používání sady Visual Studio 2017 a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="a966d-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>
- [<span data-ttu-id="a966d-126">Začínáme s .NET Core pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a966d-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)

<span data-ttu-id="a966d-127">Seznam podporovaných verzí Windows najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="a966d-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="a966d-128">Linux</span><span class="sxs-lookup"><span data-stu-id="a966d-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="a966d-129">Můžete začít s vývojem aplikace .NET Core pomocí těchto podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="a966d-129">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="a966d-130">Začínáme s .NET Core pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a966d-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)
- <span data-ttu-id="a966d-131">Podívejte se na video o [zahájení práce s Visual Studio Code C# používání a .NET Core v Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="a966d-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="a966d-132">Seznam podporovaných distribuce a verzí pro Linux najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-linux) .</span><span class="sxs-lookup"><span data-stu-id="a966d-132">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="a966d-133">macOS</span><span class="sxs-lookup"><span data-stu-id="a966d-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="a966d-134">Můžete začít s vývojem aplikace .NET Core pomocí těchto podrobných kurzů:</span><span class="sxs-lookup"><span data-stu-id="a966d-134">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- <span data-ttu-id="a966d-135">Podívejte se na video o [zahájení práce s Visual Studio Code C# používání a .NET Core v MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="a966d-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>
- [<span data-ttu-id="a966d-136">Začínáme s .NET Core v macOS s využitím Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="a966d-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)
- [<span data-ttu-id="a966d-137">Začínáme s .NET Core pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a966d-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)
- [<span data-ttu-id="a966d-138">Začínáme s .NET Core v macOS pomocí Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="a966d-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="a966d-139">Sestavte kompletní řešení .NET Core na macOS pomocí Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="a966d-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="a966d-140">Seznam podporovaných verzí OS X/macOS najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-macos) .</span><span class="sxs-lookup"><span data-stu-id="a966d-140">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
