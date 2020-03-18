---
title: Začínáme s .NET Core pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením jednoduché konzolové aplikace pomocí sady Visual Studio for Mac a .NET Core.
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740488"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="06ffd-103">Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="06ffd-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="06ffd-104">Visual Studio for Mac poskytuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj základních aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="06ffd-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="06ffd-105">Tento článek vás provede vytvářením jednoduché konzolové aplikace pomocí sady Visual Studio for Mac a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06ffd-105">This article walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="06ffd-106">Vaše zpětná vazba je vysoce ceněna.</span><span class="sxs-lookup"><span data-stu-id="06ffd-106">Your feedback is highly valued.</span></span> <span data-ttu-id="06ffd-107">Vývojový tým Visual Studia for Mac může poskytnout zpětnou vazbu dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="06ffd-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="06ffd-108">V Visual Studiu pro Mac vyberte **nápovědu** > **nahlásit problém** z nabídky nebo **Nahlásit problém** na úvodní obrazovce, která otevře okno pro podání hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="06ffd-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="06ffd-109">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="06ffd-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="06ffd-110">Chcete-li vytvořit návrh, vyberte **v** > nabídce**možnost Poskytnout návrh** nebo **Poskytněte návrh** na úvodní obrazovce, která vás přenese na [webovou stránku komunity vývojářů sady Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="06ffd-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="06ffd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06ffd-111">Prerequisites</span></span>

<span data-ttu-id="06ffd-112">Podívejte se na článek [o závislostech a požadavcích jádra .NET.](../install/dependencies.md?pivots=os-macos)</span><span class="sxs-lookup"><span data-stu-id="06ffd-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-macos) article.</span></span>

<span data-ttu-id="06ffd-113">V článku [základní podpory rozhraní .NET](/visualstudio/mac/net-core-support) se ujistěte, že používáte podporovanou verzi jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="06ffd-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="06ffd-114">Začínáme</span><span class="sxs-lookup"><span data-stu-id="06ffd-114">Get started</span></span>

<span data-ttu-id="06ffd-115">Pokud jste už nainstalovali požadavky a Visual Studio pro Mac, přeskočte tuto část a pokračujte [k vytvoření projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="06ffd-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="06ffd-116">Podle následujících kroků nainstalujte požadavky a Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="06ffd-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="06ffd-117">Stáhněte si [instalační program Sady Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="06ffd-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="06ffd-118">Spusťte instalační program.</span><span class="sxs-lookup"><span data-stu-id="06ffd-118">Run the installer.</span></span> <span data-ttu-id="06ffd-119">Přečtěte si a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="06ffd-119">Read and accept the license agreement.</span></span> <span data-ttu-id="06ffd-120">Během instalace vyberte možnost instalace jádra .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06ffd-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="06ffd-121">Máte možnost nainstalovat Xamarin, multiplatformní technologii vývoje mobilních aplikací.</span><span class="sxs-lookup"><span data-stu-id="06ffd-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="06ffd-122">Instalace Xamarinu a jeho souvisejících součástí je volitelná pro vývoj jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="06ffd-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="06ffd-123">Návod k procesu instalace Visual Studia pro Mac najdete v [dokumentaci k Visual Studiu for Mac](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="06ffd-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="06ffd-124">Po dokončení instalace spusťte ide Visual Studio for Mac.</span><span class="sxs-lookup"><span data-stu-id="06ffd-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="06ffd-125">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="06ffd-125">Creating a project</span></span>

1. <span data-ttu-id="06ffd-126">V počátečním okně vyberte **Nový.**</span><span class="sxs-lookup"><span data-stu-id="06ffd-126">Select **New** on the start window.</span></span>

   ![Nové tlačítko na úvodní obrazovce Visual Studia for Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="06ffd-128">V dialogovém okně **Nový projekt** vyberte **aplikaci** pod uzu **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="06ffd-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="06ffd-129">Vyberte šablonu **konzolové aplikace** následované položkou **Další**.</span><span class="sxs-lookup"><span data-stu-id="06ffd-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Seznam nových šablon projektů](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="06ffd-131">Pokud máte nainstalovanou více než jednu verzi rozhraní .NET Core, vyberte cílovou architekturu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="06ffd-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="06ffd-132">Zadejte název **projektu**"HelloWorld" .</span><span class="sxs-lookup"><span data-stu-id="06ffd-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="06ffd-133">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="06ffd-133">Select **Create**.</span></span>

   ![Konfigurace nového dialogového okna Konzolové aplikace](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="06ffd-135">Počkejte, než se obnoví závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="06ffd-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="06ffd-136">Projekt má jeden soubor Jazyka *Program.cs*C#, `Program` Program.cs , `Main` obsahující třídu s metodou.</span><span class="sxs-lookup"><span data-stu-id="06ffd-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="06ffd-137">Prohlášení `Console.WriteLine` bude výstup "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="06ffd-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="06ffd-138">ke konzoli při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="06ffd-138">to the console when the app is run.</span></span>

   ![Hlavní okno s otevřeným Program.cs souborem](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="06ffd-140">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="06ffd-140">Run the application</span></span>

<span data-ttu-id="06ffd-141">Spusťte aplikaci v režimu ladění pomocí啦中 (příkaz + enter) nebo v režimu vydání pomocí - 啦中 (option + command + enter).</span><span class="sxs-lookup"><span data-stu-id="06ffd-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![Podokno Výstup aplikace zobrazuje Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="06ffd-143">Další krok</span><span class="sxs-lookup"><span data-stu-id="06ffd-143">Next step</span></span>

<span data-ttu-id="06ffd-144">[Vytvoření kompletní .NET Core řešení na macOS pomocí Visual Studio pro Mac](using-on-mac-vs-full-solution.md) téma ukazuje, jak vytvořit kompletní .NET Core řešení, které zahrnuje opakovaně použitelné knihovny a testování částí.</span><span class="sxs-lookup"><span data-stu-id="06ffd-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
