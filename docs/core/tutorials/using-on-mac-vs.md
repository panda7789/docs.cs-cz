---
title: Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením jednoduché konzolové aplikace pomocí Visual Studio pro Mac a .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: 7dd8d5e8828c5337a52e9d1ea207aa5ef568556e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660492"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="f6c1f-103">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="f6c1f-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="f6c1f-104">Visual Studio pro Mac poskytuje integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="f6c1f-105">Toto téma vás provede vytvořením jednoduché konzolové aplikace pomocí Visual Studio pro Mac a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="f6c1f-106">Vaše zpětná vazba je vysoce ohodnocená.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-106">Your feedback is highly valued.</span></span> <span data-ttu-id="f6c1f-107">Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="f6c1f-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="f6c1f-108">V Visual Studio pro Mac vyberte v nabídce **nápovědu** > **nahlásit problém** nebo nahlásit **problém** z úvodní obrazovky. tím otevřete okno pro podání zprávy o chybě.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="f6c1f-109">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="f6c1f-110">Chcete-li vytvořit návrh, > vyberte v nabídce možnost**poskytnout návrh** z nabídky nebo **Poskytněte návrh** z úvodní obrazovky, který vás převezme na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6c1f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6c1f-111">Prerequisites</span></span>

<span data-ttu-id="f6c1f-112">Podívejte se na téma [požadavky pro .NET Core na Macu](../macos-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="f6c1f-112">See the [Prerequisites for .NET Core on Mac](../macos-prerequisites.md) topic.</span></span>

<span data-ttu-id="f6c1f-113">Podívejte se na průvodce [podporou .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) , abyste měli jistotu, že používáte podporovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-113">Check the [.NET Core Support](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) guide to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="f6c1f-114">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f6c1f-114">Get started</span></span>

<span data-ttu-id="f6c1f-115">Pokud jste již nainstalovali požadované součásti a Visual Studio pro Mac, přeskočte tuto část a pokračujte v [vytváření projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="f6c1f-116">Pomocí těchto kroků nainstalujete požadované součásti a Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="f6c1f-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="f6c1f-117">Stáhněte [instalační program Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="f6c1f-118">Spusťte instalační program.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-118">Run the installer.</span></span> <span data-ttu-id="f6c1f-119">Přečtěte si a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-119">Read and accept the license agreement.</span></span> <span data-ttu-id="f6c1f-120">Během instalace vyberte možnost instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="f6c1f-121">Máte možnost nainstalovat Xamarin, technologii pro vývoj mobilních aplikací pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="f6c1f-122">Instalace Xamarin a její související součásti je pro vývoj pro .NET Core volitelná.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="f6c1f-123">Návod k instalaci Visual Studio pro Mac procesu instalace najdete v [dokumentaci k Visual Studio pro Mac](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="f6c1f-124">Po dokončení instalace spusťte Visual Studio pro Mac integrované vývojové prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="f6c1f-125">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="f6c1f-125">Creating a project</span></span>

1. <span data-ttu-id="f6c1f-126">V okně Start vyberte **Nový** .</span><span class="sxs-lookup"><span data-stu-id="f6c1f-126">Select **New** on the Start Window.</span></span>

   ![Tlačítko Nový na úvodní obrazovce Visual Studio pro Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="f6c1f-128">V dialogovém okně **Nový projekt** vyberte v uzlu **.NET Core** možnost **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="f6c1f-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="f6c1f-129">Vyberte šablonu **Konzolová aplikace** a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Seznam nových šablon projektů](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="f6c1f-131">Pokud máte nainstalovanou více než jednu verzi .NET Core, vyberte cílovou architekturu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="f6c1f-132">Jako **název projektu**zadejte HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="f6c1f-133">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-133">Select **Create**.</span></span>

   ![Dialogové okno Konfigurovat novou konzolovou aplikaci](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="f6c1f-135">Počkejte, než se obnoví závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="f6c1f-136">Projekt obsahuje C# jeden soubor *program.cs* `Program` , který obsahuje třídu s `Main` metodou.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="f6c1f-137">`Console.WriteLine` Příkaz zobrazí výstup "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f6c1f-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="f6c1f-138">do konzoly nástroje při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-138">to the console when the app is run.</span></span>

   ![Hlavní okno s otevřeným souborem Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="f6c1f-140">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="f6c1f-140">Run the application</span></span>

<span data-ttu-id="f6c1f-141">Spusťte aplikaci v režimu ladění pomocí ⌘ ↵ (Command + ENTER) nebo v režimu vydaných verzí s použitím ⌥ ⌘ ↵ (Option + Command + ENTER).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![Podokno výstup aplikace zobrazuje Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="f6c1f-143">Další krok</span><span class="sxs-lookup"><span data-stu-id="f6c1f-143">Next step</span></span>

<span data-ttu-id="f6c1f-144">[Vytvoření kompletního řešení .NET Core v MacOS s využitím Visual Studio pro Mac](using-on-mac-vs-full-solution.md) tématu ukazuje, jak sestavit kompletní řešení .NET Core, které zahrnuje opakovaně použitelnou knihovnu a testování částí.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
