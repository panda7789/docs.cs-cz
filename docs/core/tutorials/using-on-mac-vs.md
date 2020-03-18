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
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio for Mac poskytuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj základních aplikací .NET. Tento článek vás provede vytvářením jednoduché konzolové aplikace pomocí sady Visual Studio for Mac a .NET Core.

> [!NOTE]
> Vaše zpětná vazba je vysoce ceněna. Vývojový tým Visual Studia for Mac může poskytnout zpětnou vazbu dvěma způsoby:
>
> * V Visual Studiu pro Mac vyberte **nápovědu** > **nahlásit problém** z nabídky nebo **Nahlásit problém** na úvodní obrazovce, která otevře okno pro podání hlášení o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Chcete-li vytvořit návrh, vyberte **v** > nabídce**možnost Poskytnout návrh** nebo **Poskytněte návrh** na úvodní obrazovce, která vás přenese na [webovou stránku komunity vývojářů sady Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Požadavky

Podívejte se na článek [o závislostech a požadavcích jádra .NET.](../install/dependencies.md?pivots=os-macos)

V článku [základní podpory rozhraní .NET](/visualstudio/mac/net-core-support) se ujistěte, že používáte podporovanou verzi jádra .NET.

## <a name="get-started"></a>Začínáme

Pokud jste už nainstalovali požadavky a Visual Studio pro Mac, přeskočte tuto část a pokračujte [k vytvoření projektu](#creating-a-project). Podle následujících kroků nainstalujte požadavky a Visual Studio pro Mac:

Stáhněte si [instalační program Sady Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Spusťte instalační program. Přečtěte si a přijměte licenční smlouvu. Během instalace vyberte možnost instalace jádra .NET Core. Máte možnost nainstalovat Xamarin, multiplatformní technologii vývoje mobilních aplikací. Instalace Xamarinu a jeho souvisejících součástí je volitelná pro vývoj jádra .NET. Návod k procesu instalace Visual Studia pro Mac najdete v [dokumentaci k Visual Studiu for Mac](/visualstudio/mac/). Po dokončení instalace spusťte ide Visual Studio for Mac.

## <a name="creating-a-project"></a>Vytvoření projektu

1. V počátečním okně vyberte **Nový.**

   ![Nové tlačítko na úvodní obrazovce Visual Studia for Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. V dialogovém okně **Nový projekt** vyberte **aplikaci** pod uzu **.NET Core.** Vyberte šablonu **konzolové aplikace** následované položkou **Další**.

   ![Seznam nových šablon projektů](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Pokud máte nainstalovanou více než jednu verzi rozhraní .NET Core, vyberte cílovou architekturu pro váš projekt.

1. Zadejte název **projektu**"HelloWorld" . Vyberte **Vytvořit**.

   ![Konfigurace nového dialogového okna Konzolové aplikace](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Počkejte, než se obnoví závislosti projektu. Projekt má jeden soubor Jazyka *Program.cs*C#, `Program` Program.cs , `Main` obsahující třídu s metodou. Prohlášení `Console.WriteLine` bude výstup "Hello World!" ke konzoli při spuštění aplikace.

   ![Hlavní okno s otevřeným Program.cs souborem](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Spuštění aplikace

Spusťte aplikaci v režimu ladění pomocí啦中 (příkaz + enter) nebo v režimu vydání pomocí - 啦中 (option + command + enter).

![Podokno Výstup aplikace zobrazuje Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Další krok

[Vytvoření kompletní .NET Core řešení na macOS pomocí Visual Studio pro Mac](using-on-mac-vs-full-solution.md) téma ukazuje, jak vytvořit kompletní .NET Core řešení, které zahrnuje opakovaně použitelné knihovny a testování částí.
