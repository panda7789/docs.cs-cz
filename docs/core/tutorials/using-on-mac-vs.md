---
title: Začínáme s .NET Core pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením jednoduché konzolové aplikace pomocí Visual Studio pro Mac a .NET Core.
author: mairaw
ms.date: 12/19/2019
ms.custom: seodec18
ms.openlocfilehash: f6faf5519109202a2865b0f316251bd2c85a5606
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342964"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio pro Mac poskytuje integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Tento článek vás provede vytvořením jednoduché konzolové aplikace pomocí Visual Studio pro Mac a .NET Core.

> [!NOTE]
> Vaše zpětná vazba je vysoce ohodnocená. Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:
>
> * V Visual Studio pro Mac vyberte možnost **Help** > **nahlásit problém** z nabídky nebo **nahlásit problém** z úvodní obrazovky, čímž se otevře okno pro podání zprávy o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Chcete-li vytvořit návrh, vyberte možnost **Help** > **poskytnout návrh** z nabídky nebo **Poskytněte návrh** z úvodní obrazovky, který vás převezme na [webovou stránku komunity pro vývojáře Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Požadavky

Viz článek [.NET Core závislosti a požadavky](../install/dependencies.md?pivots=os-macos) .

Podívejte se na článek o [podpoře .NET Core](/visualstudio/mac/net-core-support) , abyste měli jistotu, že používáte podporovanou verzi .NET Core.

## <a name="get-started"></a>Začínáme

Pokud jste již nainstalovali požadované součásti a Visual Studio pro Mac, přeskočte tuto část a pokračujte v [vytváření projektu](#creating-a-project). Pomocí těchto kroků nainstalujete požadované součásti a Visual Studio pro Mac:

Stáhněte [instalační program Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Spusťte instalační program. Přečtěte si a přijměte licenční smlouvu. Během instalace vyberte možnost instalace .NET Core. Máte možnost nainstalovat Xamarin, technologii pro vývoj mobilních aplikací pro různé platformy. Instalace Xamarin a její související součásti je pro vývoj pro .NET Core volitelná. Návod k instalaci Visual Studio pro Mac procesu instalace najdete v [dokumentaci k Visual Studio pro Mac](/visualstudio/mac/). Po dokončení instalace spusťte Visual Studio pro Mac integrované vývojové prostředí (IDE).

## <a name="creating-a-project"></a>Vytvoření projektu

1. V okně Start vyberte **Nový** .

   ![Tlačítko Nový na úvodní obrazovce Visual Studio pro Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. V dialogovém okně **Nový projekt** vyberte v uzlu **.NET Core** možnost **aplikace** . Vyberte šablonu **Konzolová aplikace** a potom klikněte na tlačítko **Další**.

   ![Seznam nových šablon projektů](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Pokud máte nainstalovanou více než jednu verzi .NET Core, vyberte cílovou architekturu pro váš projekt.

1. Jako **název projektu**zadejte HelloWorld. Vyberte **vytvořit**.

   ![Dialogové okno Konfigurovat novou konzolovou aplikaci](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Počkejte, než se obnoví závislosti projektu. Projekt obsahuje jeden C# soubor *program.cs*, který obsahuje třídu `Program` s metodou `Main`. Příkaz `Console.WriteLine` zobrazí výstup "Hello World!" do konzoly nástroje při spuštění aplikace.

   ![Hlavní okno s otevřeným souborem Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Spuštění aplikace

Spusťte aplikaci v režimu ladění pomocí ⌘ ↵ (Command + ENTER) nebo v režimu vydaných verzí s použitím ⌥ ⌘ ↵ (Option + Command + ENTER).

![Podokno výstup aplikace zobrazuje Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Další krok

[Vytvoření kompletního řešení .NET Core v MacOS s využitím Visual Studio pro Mac](using-on-mac-vs-full-solution.md) tématu ukazuje, jak sestavit kompletní řešení .NET Core, které zahrnuje opakovaně použitelnou knihovnu a testování částí.
