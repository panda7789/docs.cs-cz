---
title: Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede procesem vytvoření jednoduché konzolové aplikace pomocí sady Visual Studio pro Mac a .NET Core.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: 82cd7c09dd595a8273eb88a4caaf34782fa10ac4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214540"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio pro Mac poskytuje plné integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Toto téma vás provede procesem vytvoření jednoduché konzolové aplikace pomocí sady Visual Studio pro Mac a .NET Core.

> [!NOTE]
> Vaše zpětná vazba je vysoce hodnot. Existují dva způsoby, kterými zajistíte názor na vývojový tým v sadě Visual Studio pro Mac:
> * V sadě Visual Studio pro Mac, vyberte **pomoci** > **nahlásit problém** z nabídky nebo **nahlásit problém** z úvodní obrazovky, který se otevře okno pro vyplnění sestavy chyb. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Námět, vyberte **pomoci** > **poskytují zlepšení** z nabídky nebo **poskytují zlepšení** z úvodní obrazovky, který se dostanete k [Visual Studio pro webovou stránku Mac UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Požadavky

Najdete v článku [požadavky pro .NET Core v systému Mac](../../core/macos-prerequisites.md) tématu.

## <a name="getting-started"></a>Začínáme

Pokud jste již nainstalovali požadované součásti a Visual Studio pro Mac, tuto část přeskočte a přejděte k [vytvoření projektu](#creating-a-project). Postupujte podle těchto kroků nainstalujte požadované součásti a Visual Studio pro Mac:

Stažení [Visual Studio pro Mac – instalační program](https://www.visualstudio.com/vs/visual-studio-mac/). Spusťte instalační program. Přečtěte si a přijměte licenční smlouvu. Během instalace že poskytuje možnost nainstalovat Xamarin, technologie vývoj pro různé platformy mobilních aplikací. Instalace Xamarin a jeho souvisejících součástí je volitelné pro vývoj .NET Core. Návod sady Visual Studio pro Mac procesu instalace, najdete v části [představení Visual Studio pro Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Po dokončení instalace spusťte Visual Studio pro Mac IDE.

## <a name="creating-a-project"></a>Vytvoření projektu

1. Vyberte **nový projekt** na úvodní obrazovce.

   ![Tlačítko Nový projekt v sadě Visual Studio pro Mac úvodní obrazovce](./media/using-on-mac-vs/vsmac1.png)

1. V **nový projekt** dialogovém okně, vyberte **aplikace** pod **.NET Core** uzlu. Vyberte **konzolové aplikace** šablony následuje **Další**.

   ![Nový seznam šablon projektu](./media/using-on-mac-vs/vsmac2.png)

1. Zadejte "HelloWorld" **projektu název**. Vyberte **vytvořit**.

   ![Konfigurace dialogové okno Nový v konzolové aplikace](./media/using-on-mac-vs/vsmac3.png)

1. Počkejte, až se obnoví závislosti projektu. Projekt má jeden soubor jazyka C#, *Program.cs*, obsahující `Program` třídy s `Main` metoda. `Console.WriteLine` Příkaz výstup "Hello, World!" ke konzole, při spuštění aplikace.

   ![Hlavní okno s souboru Program.cs otevřete](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>Spuštění aplikace

Spuštění aplikace v režimu ladění pomocí <kbd>F5</kbd> nebo v režimu vydání pomocí <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![V podokně výstupu aplikace se zobrazují Hello, World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>Další krok

[Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac](using-on-mac-vs-full-solution.md) téma ukazuje, jak sestavit kompletní .NET Core řešení, které obsahuje opakovaně použitelné knihovny a testování částí.
