---
title: "Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac"
description: "Toto téma vás provede procesem vytvoření jednoduché konzolové aplikace pomocí sady Visual Studio pro Mac a .NET Core."
keywords: "Rozhraní .NET, .NET core systému macOS, Mac"
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8902e849-dd17-42c0-8264-cc7ae3927a0c
ms.openlocfilehash: 893999f9abcc299da4fb0923fe47c371079f695c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="ce75c-104">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="ce75c-104">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="ce75c-105">Visual Studio pro Mac poskytuje plné integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce75c-105">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="ce75c-106">Toto téma vás provede procesem vytvoření jednoduché konzolové aplikace pomocí sady Visual Studio pro Mac a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce75c-106">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="ce75c-107">Vaše zpětná vazba je vysoce hodnot.</span><span class="sxs-lookup"><span data-stu-id="ce75c-107">Your feedback is highly valued.</span></span> <span data-ttu-id="ce75c-108">Existují dva způsoby, kterými zajistíte názor na vývojový tým v sadě Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="ce75c-108">There are a two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="ce75c-109">V sadě Visual Studio pro Mac, vyberte **pomoci** > **nahlásit problém** z nabídky nebo **nahlásit problém** z úvodní obrazovky, který se otevře okno pro vyplnění sestavy chyb.</span><span class="sxs-lookup"><span data-stu-id="ce75c-109">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="ce75c-110">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="ce75c-110">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="ce75c-111">Námět, vyberte **pomoci** > **poskytují zlepšení** z nabídky nebo **poskytují zlepšení** z úvodní obrazovky, který se dostanete k [Visual Studio pro webovou stránku Mac UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="ce75c-111">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce75c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce75c-112">Prerequisites</span></span>

<span data-ttu-id="ce75c-113">Najdete v článku [požadavky pro .NET Core v systému Mac](../../core/macos-prerequisites.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="ce75c-113">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="ce75c-114">Začínáme</span><span class="sxs-lookup"><span data-stu-id="ce75c-114">Getting started</span></span>

<span data-ttu-id="ce75c-115">Pokud jste již nainstalovali požadované součásti a Visual Studio pro Mac, tuto část přeskočte a přejděte k [vytvoření projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="ce75c-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="ce75c-116">Postupujte podle těchto kroků nainstalujte požadované součásti a Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="ce75c-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="ce75c-117">Stažení [Visual Studio pro Mac – instalační program](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="ce75c-117">Download the [Visual Studio for Mac installer](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="ce75c-118">Spusťte instalační program.</span><span class="sxs-lookup"><span data-stu-id="ce75c-118">Run the installer.</span></span> <span data-ttu-id="ce75c-119">Přečtěte si a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="ce75c-119">Read and accept the license agreement.</span></span> <span data-ttu-id="ce75c-120">Během instalace že poskytuje možnost nainstalovat Xamarin, technologie vývoj pro různé platformy mobilních aplikací.</span><span class="sxs-lookup"><span data-stu-id="ce75c-120">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="ce75c-121">Instalace Xamarin a jeho souvisejících součástí je volitelné pro vývoj .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce75c-121">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="ce75c-122">Návod sady Visual Studio pro Mac procesu instalace, najdete v části [představení Visual Studio pro Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="ce75c-122">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="ce75c-123">Po dokončení instalace spusťte Visual Studio pro Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="ce75c-123">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="ce75c-124">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="ce75c-124">Creating a project</span></span>

1. <span data-ttu-id="ce75c-125">Vyberte **nový projekt** na úvodní obrazovce.</span><span class="sxs-lookup"><span data-stu-id="ce75c-125">Select **New Project** on the Welcome screen.</span></span>

   ![Tlačítko Nový projekt v sadě Visual Studio pro Mac úvodní obrazovce](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="ce75c-127">V **nový projekt** dialogovém okně, vyberte **aplikace** pod **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce75c-127">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="ce75c-128">Vyberte **konzolové aplikace** šablony následuje **Další**.</span><span class="sxs-lookup"><span data-stu-id="ce75c-128">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nový seznam šablon projektu](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="ce75c-130">Zadejte "HelloWorld" **projektu název**.</span><span class="sxs-lookup"><span data-stu-id="ce75c-130">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="ce75c-131">Vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="ce75c-131">Select **Create**.</span></span>

   ![Konfigurace dialogové okno Nový v konzolové aplikace](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="ce75c-133">Počkejte, až se obnoví závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="ce75c-133">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="ce75c-134">Projekt má jeden soubor jazyka C#, *Program.cs*, obsahující `Program` třídy s `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="ce75c-134">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="ce75c-135">`Console.WriteLine` Příkaz výstup "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="ce75c-135">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="ce75c-136">ke konzole, při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce75c-136">to the console when the app is run.</span></span>

   ![Hlavní okno s souboru Program.cs otevřete](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="ce75c-138">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ce75c-138">Run the application</span></span>

<span data-ttu-id="ce75c-139">Spuštění aplikace v režimu ladění pomocí <kbd>F5</kbd> nebo v režimu vydání pomocí <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ce75c-139">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![V podokně výstupu aplikace se zobrazují Hello, World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="ce75c-141">Další krok</span><span class="sxs-lookup"><span data-stu-id="ce75c-141">Next step</span></span>

<span data-ttu-id="ce75c-142">[Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac](using-on-mac-vs-full-solution.md) téma ukazuje, jak sestavit kompletní .NET Core řešení, které obsahuje opakovaně použitelné knihovny a testování částí.</span><span class="sxs-lookup"><span data-stu-id="ce75c-142">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
