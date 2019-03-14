---
title: Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.
author: guardrex
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: ed6c25f424e1b87c1a18a3654f756500af9f78de
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788619"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio for Mac obsahuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Toto téma vás provede vytvořením jednoduchou konzolovou aplikaci pomocí sady Visual Studio pro Mac a .NET Core.

> [!NOTE]
> Vaše zpětná vazba je vysoce Vážíme si toho. Existují dva způsoby, jak můžete poskytnout zpětnou vazbu vývojovému týmu sady Visual Studio pro Mac:
> * V sadě Visual Studio pro Mac, vyberte **pomáhají** > **nahlásit problém** z nabídky nebo **nahlásit problém** na úvodní obrazovce. Tím se otevře okno pro Vyplňte hlášení o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Máte nějaký návrh, vyberte **pomáhají** > **poslat návrh** z nabídky nebo **poslat návrh** z úvodní obrazovky, který se dostanete k [Visual Studio for Mac komunity vývojářů webová stránka](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Požadavky

Najdete v článku [předpoklady pro .NET Core v počítačích Mac](../../core/macos-prerequisites.md) tématu.

## <a name="get-started"></a>Začínáme

Pokud jste již nainstalovali požadované součásti a sady Visual Studio pro Mac, přeskočte tuto část a přejděte k [vytvoření projektu](#creating-a-project). Postupujte podle těchto kroků nainstalujte požadované součásti a sady Visual Studio pro Mac:

Stáhněte si [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/visual-studio-mac/). Spusťte instalační program. Přečtěte si a přijměte licenční smlouvu. Během instalace zadáte možnost nainstalujte si Xamarin, technologie pro vývoj multiplatformních mobilních aplikací. Instalace Xamarinu a jeho souvisejících součástí je nepovinné pro vývoj v .NET Core. Návod, jak Visual Studio for Mac instalační proces, naleznete v tématu [představení sady Visual Studio pro Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Po dokončení instalace spusťte Visual Studio pro Mac integrovaného vývojového prostředí.

## <a name="creating-a-project"></a>Vytvoření projektu

1. Vyberte **nový projekt** na úvodní obrazovce.

   ![Tlačítko Nový projekt v sadě Visual Studio pro Mac úvodní obrazovka](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. V **nový projekt** dialogového okna, vyberte **aplikace** pod **.NET Core** uzlu. Vyberte **konzolovou aplikaci** šablony následovaný **Další**.

   ![Nový seznam šablon projektu](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Zadejte "HelloWorld" **název projektu**. Vyberte **Vytvořit**.

   ![Konfigurace nových konzolovou aplikaci dialogové okno](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Počkejte, dokud se obnoví závislosti projektu. Projekt má jeden C# souboru, *Program.cs*, obsahující `Program` třídy s `Main` metoda. `Console.WriteLine` Příkaz bude output "Hello World!" do konzoly při spuštění aplikace.

   ![Hlavní okno s souboru Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Spuštění aplikace

Spusťte aplikaci pomocí režimu ladění <kbd>F5</kbd> nebo v režimu pro vydávání pomocí <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![V podokně výstup aplikace se zobrazí Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Další krok

[Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac](using-on-mac-vs-full-solution.md) tématu se dozvíte, jak vytvořit kompletního řešení .NET Core, která obsahuje opakovaně použitelné knihovny a testování částí.
