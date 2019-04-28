---
title: Začínáme s .NET Core
description: Najděte si materiály pro další informace o vytváření aplikací .NET Core ve Windows, Linuxu a macOS.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: 2ec7f57250db8779552305b2ee69cbcf1db55d0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614155"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="90704-103">Začínáme s .NET Core</span><span class="sxs-lookup"><span data-stu-id="90704-103">Get started with .NET Core</span></span>

<span data-ttu-id="90704-104">Tento článek obsahuje informace o zahájení práce s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90704-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="90704-105">.NET core je nainstalovat ve Windows, Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="90704-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="90704-106">Můžete kód ve svém oblíbeném textovém editoru a vytvářet multiplatformní knihovny a aplikace.</span><span class="sxs-lookup"><span data-stu-id="90704-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="90704-107">Pokud si nejste jisti, co je .NET Core nebo toho, jak souvisí jiné technologie .NET, začínat [co je .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) Přehled.</span><span class="sxs-lookup"><span data-stu-id="90704-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="90704-108">Jednoduše řečeno, .NET Core je open source, napříč platformami implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="90704-108">Put simply, .NET Core is an open-source, cross-platform, implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="90704-109">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="90704-109">Create an application</span></span>

<span data-ttu-id="90704-110">Nejprve stáhnout a nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download/) ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="90704-110">First, download and install the [.NET Core SDK](https://www.microsoft.com/net/download/) on your computer.</span></span>

<span data-ttu-id="90704-111">Dále otevřete terminál **PowerShell**, **příkazového řádku**, nebo **bash**.</span><span class="sxs-lookup"><span data-stu-id="90704-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="90704-112">Zadejte následující příkaz `dotnet` příkazy k vytvoření a spuštění aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="90704-112">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="90704-113">Byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="90704-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="90704-114">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="90704-114">Congratulations!</span></span> <span data-ttu-id="90704-115">Vytvoříte jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90704-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="90704-116">Můžete také použít [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio 2017](tutorials/with-visual-studio.md) (jenom Windows), nebo [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS pouze), chcete-li vytvořit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="90704-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio 2017](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="90704-117">Kurzy</span><span class="sxs-lookup"><span data-stu-id="90704-117">Tutorials</span></span>

<span data-ttu-id="90704-118">Můžete začít vyvíjet aplikace .NET Core pomocí následujících tyto podrobné kurzy.</span><span class="sxs-lookup"><span data-stu-id="90704-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="90704-119">Windows</span><span class="sxs-lookup"><span data-stu-id="90704-119">Windows</span></span>](#tab/windows)

* [<span data-ttu-id="90704-120">Vytvořte aplikaci "Hello World" C# pomocí .NET Core v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="90704-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)

* [<span data-ttu-id="90704-121">Vytvoření knihovny tříd jazyka C# pomocí platformy .NET Core v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="90704-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)

* [<span data-ttu-id="90704-122">Vytvořte si aplikaci Visual Basic "Hello World" pomocí .NET Core v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="90704-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)

* [<span data-ttu-id="90704-123">Vytvoření knihovny tříd pomocí jazyka Visual Basic a .NET Core v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="90704-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  

* <span data-ttu-id="90704-124">Podívejte se na video na [jak nainstalovat a používat Visual Studio Code a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="90704-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>

* <span data-ttu-id="90704-125">Podívejte se na video na [jak nainstalovat a používat Visual Studio 2017 a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="90704-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>

* [<span data-ttu-id="90704-126">Začínáme s .NET Core pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="90704-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="90704-127">Najdete v článku [požadavky pro Windows. vývojové](windows-prerequisites.md) článku pro seznam podporovaných verzí Windows.</span><span class="sxs-lookup"><span data-stu-id="90704-127">See the [Prerequisites for Windows development](windows-prerequisites.md) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="90704-128">Linux</span><span class="sxs-lookup"><span data-stu-id="90704-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="90704-129">Můžete začít vyvíjet aplikace .NET Core pomocí následujících tyto podrobné kurzy.</span><span class="sxs-lookup"><span data-stu-id="90704-129">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* [<span data-ttu-id="90704-130">Začínáme s .NET Core pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="90704-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* <span data-ttu-id="90704-131">Podívejte se na video na [Začínáme se službou Visual Studio Code pomocí jazyka C# a .NET Core na Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="90704-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="90704-132">Najdete v článku [předpoklady pro vývoj pro Linux](linux-prerequisites.md) článku pro seznam podporovaných distribucích systému Linux a verze.</span><span class="sxs-lookup"><span data-stu-id="90704-132">See the [Prerequisites for Linux development](linux-prerequisites.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="90704-133">macOS</span><span class="sxs-lookup"><span data-stu-id="90704-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="90704-134">Můžete začít vyvíjet aplikace .NET Core pomocí následujících tyto podrobné kurzy.</span><span class="sxs-lookup"><span data-stu-id="90704-134">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* <span data-ttu-id="90704-135">Podívejte se na video na [Začínáme se službou Visual Studio Code pomocí jazyka C# a .NET Core v systému macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="90704-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>

* [<span data-ttu-id="90704-136">Začínáme s .NET Core v systému macOS, pomocí nástroje Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="90704-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)

* [<span data-ttu-id="90704-137">Začínáme s .NET Core pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="90704-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* [<span data-ttu-id="90704-138">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="90704-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)

* [<span data-ttu-id="90704-139">Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="90704-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="90704-140">Najdete v článku [předpoklady pro vývoj v macOS](macos-prerequisites.md) článku pro seznam podporovaných OS X / macOS verze.</span><span class="sxs-lookup"><span data-stu-id="90704-140">See the [Prerequisites for macOS development](macos-prerequisites.md) article for a list of the supported OS X / macOS versions.</span></span>

---
