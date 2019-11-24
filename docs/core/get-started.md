---
title: Get started with .NET Core
description: Find resources to learn how to build .NET Core applications on Windows, Linux and macOS.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 78066f2904f6a874b71165e4fe1769b6b778ae41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428865"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="8f9f3-103">Get started with .NET Core</span><span class="sxs-lookup"><span data-stu-id="8f9f3-103">Get started with .NET Core</span></span>

<span data-ttu-id="8f9f3-104">This article provides information on getting started with .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="8f9f3-105">.NET Core can be installed on Windows, Linux, and macOS.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="8f9f3-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="8f9f3-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="8f9f3-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="8f9f3-109">Create an application</span><span class="sxs-lookup"><span data-stu-id="8f9f3-109">Create an application</span></span>

<span data-ttu-id="8f9f3-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="8f9f3-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="8f9f3-112">Type the following `dotnet` commands to create and run a C# application:</span><span class="sxs-lookup"><span data-stu-id="8f9f3-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="8f9f3-113">You should see the following output:</span><span class="sxs-lookup"><span data-stu-id="8f9f3-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="8f9f3-114">Congratulations!</span><span class="sxs-lookup"><span data-stu-id="8f9f3-114">Congratulations!</span></span> <span data-ttu-id="8f9f3-115">You've created a simple .NET Core application.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="8f9f3-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="8f9f3-117">Kurzy</span><span class="sxs-lookup"><span data-stu-id="8f9f3-117">Tutorials</span></span>

<span data-ttu-id="8f9f3-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="8f9f3-119">Windows</span><span class="sxs-lookup"><span data-stu-id="8f9f3-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="8f9f3-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="8f9f3-121">Build a C# class library with .NET Core in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="8f9f3-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)
- [<span data-ttu-id="8f9f3-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  
- <span data-ttu-id="8f9f3-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="8f9f3-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>
- <span data-ttu-id="8f9f3-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="8f9f3-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>
- [<span data-ttu-id="8f9f3-126">Getting started with .NET Core using the command-line.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="8f9f3-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="8f9f3-128">Linux</span><span class="sxs-lookup"><span data-stu-id="8f9f3-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="8f9f3-129">You can get started developing .NET Core application by following these step-by-step tutorials:</span><span class="sxs-lookup"><span data-stu-id="8f9f3-129">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="8f9f3-130">Getting started with .NET Core using the command-line.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)
- <span data-ttu-id="8f9f3-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="8f9f3-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="8f9f3-132">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) article for a list of the supported Linux distros and versions.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-132">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="8f9f3-133">macOS</span><span class="sxs-lookup"><span data-stu-id="8f9f3-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="8f9f3-134">You can get started developing .NET Core application by following these step-by-step tutorials:</span><span class="sxs-lookup"><span data-stu-id="8f9f3-134">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- <span data-ttu-id="8f9f3-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="8f9f3-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>
- [<span data-ttu-id="8f9f3-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)
- [<span data-ttu-id="8f9f3-137">Getting started with .NET Core using the command-line.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)
- [<span data-ttu-id="8f9f3-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="8f9f3-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="8f9f3-140">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) article for a list of the supported OS X / macOS versions.</span><span class="sxs-lookup"><span data-stu-id="8f9f3-140">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
