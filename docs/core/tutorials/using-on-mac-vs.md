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
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio pro Mac poskytuje integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Toto téma vás provede vytvořením jednoduché konzolové aplikace pomocí Visual Studio pro Mac a .NET Core.

> [!NOTE]
> Vaše zpětná vazba je vysoce ohodnocená. Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:
> * V Visual Studio pro Mac vyberte v nabídce **nápovědu** > **nahlásit problém** nebo nahlásit **problém** z úvodní obrazovky. tím otevřete okno pro podání zprávy o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Chcete-li vytvořit návrh, > vyberte v nabídce možnost**poskytnout návrh** z nabídky nebo **Poskytněte návrh** z úvodní obrazovky, který vás převezme na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Požadavky

Podívejte se na téma [požadavky pro .NET Core na Macu](../macos-prerequisites.md) .

Podívejte se na průvodce [podporou .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) , abyste měli jistotu, že používáte podporovanou verzi .NET Core.

## <a name="get-started"></a>Začínáme

Pokud jste již nainstalovali požadované součásti a Visual Studio pro Mac, přeskočte tuto část a pokračujte v [vytváření projektu](#creating-a-project). Pomocí těchto kroků nainstalujete požadované součásti a Visual Studio pro Mac:

Stáhněte [instalační program Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Spusťte instalační program. Přečtěte si a přijměte licenční smlouvu. Během instalace vyberte možnost instalace .NET Core. Máte možnost nainstalovat Xamarin, technologii pro vývoj mobilních aplikací pro různé platformy. Instalace Xamarin a její související součásti je pro vývoj pro .NET Core volitelná. Návod k instalaci Visual Studio pro Mac procesu instalace najdete v [dokumentaci k Visual Studio pro Mac](/visualstudio/mac/). Po dokončení instalace spusťte Visual Studio pro Mac integrované vývojové prostředí (IDE).

## <a name="creating-a-project"></a>Vytvoření projektu

1. V okně Start vyberte **Nový** .

   ![Tlačítko Nový na úvodní obrazovce Visual Studio pro Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. V dialogovém okně **Nový projekt** vyberte v uzlu **.NET Core** možnost **aplikace** . Vyberte šablonu **Konzolová aplikace** a potom klikněte na tlačítko **Další**.

   ![Seznam nových šablon projektů](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Pokud máte nainstalovanou více než jednu verzi .NET Core, vyberte cílovou architekturu pro váš projekt.

1. Jako **název projektu**zadejte HelloWorld. Vyberte **Vytvořit**.

   ![Dialogové okno Konfigurovat novou konzolovou aplikaci](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Počkejte, než se obnoví závislosti projektu. Projekt obsahuje C# jeden soubor *program.cs* `Program` , který obsahuje třídu s `Main` metodou. `Console.WriteLine` Příkaz zobrazí výstup "Hello World!" do konzoly nástroje při spuštění aplikace.

   ![Hlavní okno s otevřeným souborem Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Spuštění aplikace

Spusťte aplikaci v režimu ladění pomocí ⌘ ↵ (Command + ENTER) nebo v režimu vydaných verzí s použitím ⌥ ⌘ ↵ (Option + Command + ENTER).

![Podokno výstup aplikace zobrazuje Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Další krok

[Vytvoření kompletního řešení .NET Core v MacOS s využitím Visual Studio pro Mac](using-on-mac-vs-full-solution.md) tématu ukazuje, jak sestavit kompletní řešení .NET Core, které zahrnuje opakovaně použitelnou knihovnu a testování částí.
