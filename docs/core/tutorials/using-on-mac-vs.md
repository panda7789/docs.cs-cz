---
title: Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: f751e7532e9627de3d3733476f7214654089e468
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744111"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="26a4c-103">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="26a4c-103">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="26a4c-104">Visual Studio for Mac obsahuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26a4c-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="26a4c-105">Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26a4c-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="26a4c-106">Vaše zpětná vazba je vysoce Vážíme si toho.</span><span class="sxs-lookup"><span data-stu-id="26a4c-106">Your feedback is highly valued.</span></span> <span data-ttu-id="26a4c-107">Existují dva způsoby, jak můžete poskytnout zpětnou vazbu vývojovému týmu sady Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="26a4c-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="26a4c-108">V sadě Visual Studio pro Mac, vyberte **pomáhají** > **nahlásit problém** z nabídky nebo **nahlásit problém** na úvodní obrazovce. Tím se otevře okno pro Vyplňte hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="26a4c-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="26a4c-109">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="26a4c-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="26a4c-110">Máte nějaký návrh, vyberte **pomáhají** > **poslat návrh** z nabídky nebo **poslat návrh** z úvodní obrazovky, který se dostanete k [Visual Studio for Mac komunity vývojářů webová stránka](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="26a4c-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26a4c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26a4c-111">Prerequisites</span></span>

<span data-ttu-id="26a4c-112">Najdete v článku [předpoklady pro .NET Core v počítačích Mac](../../core/macos-prerequisites.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="26a4c-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="26a4c-113">Začínáme</span><span class="sxs-lookup"><span data-stu-id="26a4c-113">Getting started</span></span>

<span data-ttu-id="26a4c-114">Pokud jste již nainstalovali požadované součásti a sady Visual Studio pro Mac, přeskočte tuto část a přejděte k [vytvoření projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="26a4c-114">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="26a4c-115">Postupujte podle těchto kroků nainstalujte požadované součásti a sady Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="26a4c-115">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="26a4c-116">Stáhněte si [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="26a4c-116">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="26a4c-117">Spusťte instalační program.</span><span class="sxs-lookup"><span data-stu-id="26a4c-117">Run the installer.</span></span> <span data-ttu-id="26a4c-118">Přečtěte si a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="26a4c-118">Read and accept the license agreement.</span></span> <span data-ttu-id="26a4c-119">Během instalace zadáte možnost nainstalujte si Xamarin, technologie pro vývoj multiplatformních mobilních aplikací.</span><span class="sxs-lookup"><span data-stu-id="26a4c-119">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="26a4c-120">Instalace Xamarinu a jeho souvisejících součástí je nepovinné pro vývoj v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26a4c-120">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="26a4c-121">Návod, jak Visual Studio for Mac instalační proces, naleznete v tématu [představení sady Visual Studio pro Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="26a4c-121">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="26a4c-122">Po dokončení instalace spusťte Visual Studio pro Mac integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="26a4c-122">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="26a4c-123">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="26a4c-123">Creating a project</span></span>

1. <span data-ttu-id="26a4c-124">Vyberte **nový projekt** na úvodní obrazovce.</span><span class="sxs-lookup"><span data-stu-id="26a4c-124">Select **New Project** on the Welcome screen.</span></span>

   ![Tlačítko Nový projekt v sadě Visual Studio pro Mac úvodní obrazovka](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="26a4c-126">V **nový projekt** dialogového okna, vyberte **aplikace** pod **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="26a4c-126">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="26a4c-127">Vyberte **konzolovou aplikaci** šablony následovaný **Další**.</span><span class="sxs-lookup"><span data-stu-id="26a4c-127">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nový seznam šablon projektu](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="26a4c-129">Zadejte "HelloWorld" **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="26a4c-129">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="26a4c-130">Vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="26a4c-130">Select **Create**.</span></span>

   ![Konfigurace nových konzolovou aplikaci dialogové okno](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="26a4c-132">Počkejte, dokud se obnoví závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="26a4c-132">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="26a4c-133">Projekt má jeden C# souboru, *Program.cs*, obsahující `Program` třídy s `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="26a4c-133">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="26a4c-134">`Console.WriteLine` Příkaz bude output "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="26a4c-134">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="26a4c-135">do konzoly při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="26a4c-135">to the console when the app is run.</span></span>

   ![Hlavní okno s souboru Program.cs](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="26a4c-137">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="26a4c-137">Run the application</span></span>

<span data-ttu-id="26a4c-138">Spusťte aplikaci pomocí režimu ladění <kbd>F5</kbd> nebo v režimu pro vydávání pomocí <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="26a4c-138">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![V podokně výstup aplikace se zobrazí Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="26a4c-140">Další krok</span><span class="sxs-lookup"><span data-stu-id="26a4c-140">Next step</span></span>

<span data-ttu-id="26a4c-141">[Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac](using-on-mac-vs-full-solution.md) tématu se dozvíte, jak vytvořit kompletního řešení .NET Core, která obsahuje opakovaně použitelné knihovny a testování částí.</span><span class="sxs-lookup"><span data-stu-id="26a4c-141">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
