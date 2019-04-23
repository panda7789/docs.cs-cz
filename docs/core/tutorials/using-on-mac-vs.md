---
title: Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.
author: guardrex
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: d99cabf15be63593b272474867359324a5892b04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980405"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="d2148-103">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="d2148-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="d2148-104">Visual Studio for Mac obsahuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2148-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="d2148-105">Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2148-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="d2148-106">Vaše zpětná vazba je vysoce Vážíme si toho.</span><span class="sxs-lookup"><span data-stu-id="d2148-106">Your feedback is highly valued.</span></span> <span data-ttu-id="d2148-107">Existují dva způsoby, jak můžete poskytnout zpětnou vazbu vývojovému týmu sady Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="d2148-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="d2148-108">V sadě Visual Studio pro Mac, vyberte **pomáhají** > **nahlásit problém** z nabídky nebo **nahlásit problém** na úvodní obrazovce. Tím se otevře okno pro Vyplňte hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="d2148-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="d2148-109">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="d2148-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="d2148-110">Máte nějaký návrh, vyberte **pomáhají** > **poslat návrh** z nabídky nebo **poslat návrh** z úvodní obrazovky, který se dostanete k [Visual Studio for Mac komunity vývojářů webová stránka](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="d2148-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2148-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2148-111">Prerequisites</span></span>

<span data-ttu-id="d2148-112">Najdete v článku [předpoklady pro .NET Core v počítačích Mac](../../core/macos-prerequisites.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="d2148-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="get-started"></a><span data-ttu-id="d2148-113">Začínáme</span><span class="sxs-lookup"><span data-stu-id="d2148-113">Get started</span></span>

<span data-ttu-id="d2148-114">Pokud jste již nainstalovali požadované součásti a sady Visual Studio pro Mac, přeskočte tuto část a přejděte k [vytvoření projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="d2148-114">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="d2148-115">Postupujte podle těchto kroků nainstalujte požadované součásti a sady Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="d2148-115">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="d2148-116">Stáhněte si [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="d2148-116">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="d2148-117">Spusťte instalační program.</span><span class="sxs-lookup"><span data-stu-id="d2148-117">Run the installer.</span></span> <span data-ttu-id="d2148-118">Přečtěte si a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="d2148-118">Read and accept the license agreement.</span></span> <span data-ttu-id="d2148-119">Během instalace zadáte možnost nainstalujte si Xamarin, technologie pro vývoj multiplatformních mobilních aplikací.</span><span class="sxs-lookup"><span data-stu-id="d2148-119">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="d2148-120">Instalace Xamarinu a jeho souvisejících součástí je nepovinné pro vývoj v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2148-120">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="d2148-121">Návod, jak Visual Studio for Mac instalační proces, naleznete v tématu [Visual Studio for Mac dokumentaci](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="d2148-121">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="d2148-122">Po dokončení instalace spusťte Visual Studio pro Mac integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="d2148-122">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="d2148-123">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="d2148-123">Creating a project</span></span>

1. <span data-ttu-id="d2148-124">Vyberte **nový projekt** na úvodní obrazovce.</span><span class="sxs-lookup"><span data-stu-id="d2148-124">Select **New Project** on the Welcome screen.</span></span>

   ![Tlačítko Nový projekt v sadě Visual Studio pro Mac úvodní obrazovka](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="d2148-126">V **nový projekt** dialogového okna, vyberte **aplikace** pod **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="d2148-126">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="d2148-127">Vyberte **konzolovou aplikaci** šablony následovaný **Další**.</span><span class="sxs-lookup"><span data-stu-id="d2148-127">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nový seznam šablon projektu](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="d2148-129">Zadejte "HelloWorld" **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="d2148-129">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="d2148-130">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="d2148-130">Select **Create**.</span></span>

   ![Konfigurace nových konzolovou aplikaci dialogové okno](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="d2148-132">Počkejte, dokud se obnoví závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="d2148-132">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="d2148-133">Projekt má jeden C# souboru, *Program.cs*, obsahující `Program` třídy s `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="d2148-133">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="d2148-134">`Console.WriteLine` Příkaz bude output "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="d2148-134">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="d2148-135">do konzoly při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2148-135">to the console when the app is run.</span></span>

   ![Hlavní okno s souboru Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="d2148-137">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="d2148-137">Run the application</span></span>

<span data-ttu-id="d2148-138">Spusťte aplikaci pomocí režimu ladění <kbd>F5</kbd> nebo v režimu pro vydávání pomocí <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d2148-138">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![V podokně výstup aplikace se zobrazí Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="d2148-140">Další krok</span><span class="sxs-lookup"><span data-stu-id="d2148-140">Next step</span></span>

<span data-ttu-id="d2148-141">[Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac](using-on-mac-vs-full-solution.md) tématu se dozvíte, jak vytvořit kompletního řešení .NET Core, která obsahuje opakovaně použitelné knihovny a testování částí.</span><span class="sxs-lookup"><span data-stu-id="d2148-141">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
