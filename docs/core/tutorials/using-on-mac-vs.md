---
title: Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: feaed88e902080c5c3b07578b78f8437489a690c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428581"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="c7021-103">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="c7021-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="c7021-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span><span class="sxs-lookup"><span data-stu-id="c7021-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="c7021-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7021-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="c7021-106">Your feedback is highly valued.</span><span class="sxs-lookup"><span data-stu-id="c7021-106">Your feedback is highly valued.</span></span> <span data-ttu-id="c7021-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span><span class="sxs-lookup"><span data-stu-id="c7021-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="c7021-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span><span class="sxs-lookup"><span data-stu-id="c7021-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="c7021-109">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="c7021-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="c7021-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="c7021-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7021-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7021-111">Prerequisites</span></span>

<span data-ttu-id="c7021-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-macos) topic.</span><span class="sxs-lookup"><span data-stu-id="c7021-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-macos) topic.</span></span>

<span data-ttu-id="c7021-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7021-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="c7021-114">Začínáme</span><span class="sxs-lookup"><span data-stu-id="c7021-114">Get started</span></span>

<span data-ttu-id="c7021-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="c7021-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="c7021-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span><span class="sxs-lookup"><span data-stu-id="c7021-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="c7021-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="c7021-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="c7021-118">Run the installer.</span><span class="sxs-lookup"><span data-stu-id="c7021-118">Run the installer.</span></span> <span data-ttu-id="c7021-119">Read and accept the license agreement.</span><span class="sxs-lookup"><span data-stu-id="c7021-119">Read and accept the license agreement.</span></span> <span data-ttu-id="c7021-120">During the install, select the option to install .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7021-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="c7021-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span><span class="sxs-lookup"><span data-stu-id="c7021-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="c7021-122">Installing Xamarin and its related components is optional for .NET Core development.</span><span class="sxs-lookup"><span data-stu-id="c7021-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="c7021-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="c7021-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="c7021-124">When the install is complete, start the Visual Studio for Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="c7021-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="c7021-125">Creating a project</span><span class="sxs-lookup"><span data-stu-id="c7021-125">Creating a project</span></span>

1. <span data-ttu-id="c7021-126">Select **New** on the Start Window.</span><span class="sxs-lookup"><span data-stu-id="c7021-126">Select **New** on the Start Window.</span></span>

   ![New button on the Visual Studio for Mac Start screen](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="c7021-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span><span class="sxs-lookup"><span data-stu-id="c7021-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="c7021-129">Select the **Console Application** template followed by **Next**.</span><span class="sxs-lookup"><span data-stu-id="c7021-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![New project templates list](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="c7021-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span><span class="sxs-lookup"><span data-stu-id="c7021-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="c7021-132">Type "HelloWorld" for the **Project Name**.</span><span class="sxs-lookup"><span data-stu-id="c7021-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="c7021-133">Select **Create**.</span><span class="sxs-lookup"><span data-stu-id="c7021-133">Select **Create**.</span></span>

   ![Configure your new Console Application dialog](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="c7021-135">Wait while the project's dependencies are restored.</span><span class="sxs-lookup"><span data-stu-id="c7021-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="c7021-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span><span class="sxs-lookup"><span data-stu-id="c7021-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="c7021-137">The `Console.WriteLine` statement will output "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c7021-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="c7021-138">to the console when the app is run.</span><span class="sxs-lookup"><span data-stu-id="c7021-138">to the console when the app is run.</span></span>

   ![Main window with the Program.cs file open](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="c7021-140">Run the application</span><span class="sxs-lookup"><span data-stu-id="c7021-140">Run the application</span></span>

<span data-ttu-id="c7021-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span><span class="sxs-lookup"><span data-stu-id="c7021-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![The Application Output pane shows Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="c7021-143">Další krok</span><span class="sxs-lookup"><span data-stu-id="c7021-143">Next step</span></span>

<span data-ttu-id="c7021-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span><span class="sxs-lookup"><span data-stu-id="c7021-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
