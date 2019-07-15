---
title: Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: a6d58d2a54ce9742542a3f7e5c9378be89b8f89a
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870516"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="10828-103">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="10828-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="10828-104">Visual Studio for Mac obsahuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10828-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="10828-105">Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10828-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="10828-106">Vaše zpětná vazba je vysoce Vážíme si toho.</span><span class="sxs-lookup"><span data-stu-id="10828-106">Your feedback is highly valued.</span></span> <span data-ttu-id="10828-107">Existují dva způsoby, jak můžete poskytnout zpětnou vazbu vývojovému týmu sady Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="10828-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="10828-108">V sadě Visual Studio pro Mac, vyberte **pomáhají** > **nahlásit problém** z nabídky nebo **nahlásit problém** na úvodní obrazovce. Tím se otevře okno pro Vyplňte hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="10828-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="10828-109">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="10828-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="10828-110">Máte nějaký návrh, vyberte **pomáhají** > **poslat návrh** z nabídky nebo **poslat návrh** z úvodní obrazovky, který se dostanete k [Visual Studio for Mac komunity vývojářů webová stránka](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="10828-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10828-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10828-111">Prerequisites</span></span>

<span data-ttu-id="10828-112">Najdete v článku [předpoklady pro .NET Core v počítačích Mac](../../core/macos-prerequisites.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="10828-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

<span data-ttu-id="10828-113">Zkontrolujte, [podpora platformy .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) návod vám pomůže zajistit, že používáte podporovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10828-113">Check the [.NET Core Support](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) guide to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="10828-114">Začínáme</span><span class="sxs-lookup"><span data-stu-id="10828-114">Get started</span></span>

<span data-ttu-id="10828-115">Pokud jste již nainstalovali požadované součásti a sady Visual Studio pro Mac, přeskočte tuto část a přejděte k [vytvoření projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="10828-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="10828-116">Postupujte podle těchto kroků nainstalujte požadované součásti a sady Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="10828-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="10828-117">Stáhněte si [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="10828-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="10828-118">Spusťte instalační program.</span><span class="sxs-lookup"><span data-stu-id="10828-118">Run the installer.</span></span> <span data-ttu-id="10828-119">Přečtěte si a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="10828-119">Read and accept the license agreement.</span></span> <span data-ttu-id="10828-120">Během instalace vyberte možnost instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10828-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="10828-121">Už jste zadali možnost nainstalujte si Xamarin, technologie pro vývoj multiplatformních mobilních aplikací.</span><span class="sxs-lookup"><span data-stu-id="10828-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="10828-122">Instalace Xamarinu a jeho souvisejících součástí je nepovinné pro vývoj v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10828-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="10828-123">Návod, jak Visual Studio for Mac instalační proces, naleznete v tématu [Visual Studio for Mac dokumentaci](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="10828-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="10828-124">Po dokončení instalace spusťte Visual Studio pro Mac integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="10828-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="10828-125">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="10828-125">Creating a project</span></span>

1. <span data-ttu-id="10828-126">Vyberte **nové** v okně Start.</span><span class="sxs-lookup"><span data-stu-id="10828-126">Select **New** on the Start Window.</span></span>

   ![Tlačítko Nová v sadě Visual Studio pro Mac úvodní obrazovku](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="10828-128">V **nový projekt** dialogového okna, vyberte **aplikace** pod **.NET Core** uzlu.</span><span class="sxs-lookup"><span data-stu-id="10828-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="10828-129">Vyberte **konzolovou aplikaci** šablony následovaný **Další**.</span><span class="sxs-lookup"><span data-stu-id="10828-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nový seznam šablon projektu](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="10828-131">Pokud máte více než jednu verzi .NET Core nainstalovaná, vyberte cílový rámec pro projekt.</span><span class="sxs-lookup"><span data-stu-id="10828-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="10828-132">Zadejte "HelloWorld" **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="10828-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="10828-133">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="10828-133">Select **Create**.</span></span>

   ![Konfigurace nových konzolovou aplikaci dialogové okno](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="10828-135">Počkejte, dokud se obnoví závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="10828-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="10828-136">Projekt má jeden C# souboru, *Program.cs*, obsahující `Program` třídy s `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="10828-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="10828-137">`Console.WriteLine` Příkaz bude output "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="10828-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="10828-138">do konzoly při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="10828-138">to the console when the app is run.</span></span>

   ![Hlavní okno s souboru Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="10828-140">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="10828-140">Run the application</span></span>

<span data-ttu-id="10828-141">Spusťte aplikaci v režimu ladění pomocí ⌘ ↵ (příkaz + enter) nebo v režimu vydání pomocí ⌥ ⌘ ↵ (možnost + příkaz + enter).</span><span class="sxs-lookup"><span data-stu-id="10828-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![V podokně výstup aplikace se zobrazí Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="10828-143">Další krok</span><span class="sxs-lookup"><span data-stu-id="10828-143">Next step</span></span>

<span data-ttu-id="10828-144">[Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac](using-on-mac-vs-full-solution.md) tématu se dozvíte, jak vytvořit kompletního řešení .NET Core, která obsahuje opakovaně použitelné knihovny a testování částí.</span><span class="sxs-lookup"><span data-stu-id="10828-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
