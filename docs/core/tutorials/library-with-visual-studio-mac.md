---
title: Vytvoření .NET Standard knihovny tříd pomocí Visual Studio pro Mac
description: Naučte se vytvářet .NET Standard knihovny tříd pomocí Visual Studio pro Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 3a107fff2fd6aef5e06d9af3eac334fbf5688fa5
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713740"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a>Kurz: Vytvoření knihovny .NET Standard pomocí Visual Studio pro Mac

V tomto kurzu vytvoříte jednoduchou knihovnu tříd, která obsahuje jedinou metodu zpracování řetězce. Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem <xref:System.String> třídy.

*Knihovna tříd* definuje typy a metody, které jsou volány aplikací. Knihovna tříd, která cílí na .NET Standard 2,1, může být použita aplikací, která cílí na jakoukoli implementaci rozhraní .NET, která podporuje .NET Standard verze 2,1. Po dokončení knihovny tříd ji můžete distribuovat jako součást třetí strany nebo jako součást balíčku s jednou nebo více aplikacemi.

> [!NOTE]
> Vaše zpětná vazba je vysoce ohodnocená. Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:
>
> - V Visual Studio pro Mac vyberte v nabídce **nápovědu**  >  **nahlásit problém** nebo **nahlásit problém** z úvodní obrazovky, která otevře okno pro podání zprávy o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Chcete-li vytvořit návrh, vyberte v nabídce **možnost**  >  **poskytnout návrh** nebo **Poskytněte návrh** z úvodní obrazovky, který vás přesměruje na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Požadavky

* [Nainstalujte Visual Studio pro Mac verze 8,6 nebo novější](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Vyberte možnost instalace .NET Core. Instalace Xamarin je volitelná pro vývoj v .NET Core. Další informace najdete v následujících materiálech:

  * [Kurz: instalace Visual Studio pro Mac](/visualstudio/mac/installation).
  * [Podporované verze MacOS](../install/dependencies.md?pivots=os-macos)
  * [Verze .NET Core podporované nástrojem Visual Studio pro Mac](/visualstudio/mac/net-core-support).

## <a name="create-a-solution-with-a-class-library-project"></a>Vytvoření řešení pomocí projektu knihovny tříd

Řešení sady Visual Studio slouží jako kontejner pro jeden nebo více projektů. Vytvořte řešení a projekt knihovny tříd v řešení. Další související projekty přidáte do stejného řešení později.

1. Spusťte Visual Studio pro Mac.

1. V okně Start vyberte **Nový projekt**.

1. V dialogovém okně **Nový projekt** pod uzlem **více platforem** vyberte možnost **knihovna**, vyberte šablonu **knihovny .NET Standard** a vyberte možnost **Další**.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Dialogové okno Nový projekt":::

1. V dialogovém okně **Konfigurovat novou knihovnu .NET Standard** zvolte .NET Standard 2,1 a vyberte **Další**.

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="Vyberte .NET Standard 2,1":::

1. Pojmenujte projekt "StringLibrary" a řešení "ClassLibraryProjects". Ponechte položku **vytvořit adresář projektu v rámci vybraného adresáře řešení** . Vyberte **Vytvořit**.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio pro Mac možnosti dialogového okna Nový projekt":::

1. V hlavní nabídce vyberte možnost **Zobrazit**panel  >  **Pads**  >  **řešení**a vyberte ikonu ukotvit, aby se panel otevřel.

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Ikona ukotvení pro panel řešení":::

1. Na panelu **řešení** rozbalte uzel, aby se zobrazil `StringLibrary` soubor třídy poskytnutý šablonou, *Class1.cs*. <kbd>podržte klávesu CTRL</kbd>a klikněte na soubor, v místní nabídce vyberte **Přejmenovat** a přejmenujte soubor na *StringLibrary.cs*. Otevřete soubor a nahraďte jeho obsah následujícím kódem:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. Uložte soubor stisknutím <kbd>⌘</kbd><kbd>S</kbd> (<kbd>Commands</kbd> + <kbd>S</kbd>).

1. V dolní části okna IDE vyberte **chyby** a otevřete panel **chyby** . Vyberte tlačítko **výstup sestavení** .

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Spodní okraj integrovaného vývojového prostředí (IDE) sady Visual Studio zobrazující tlačítko chyby":::

1. V nabídce vyberte **sestavit**  >  **vše** .

   Řešení vytvoří. Na panelu výstup sestavení se zobrazí, že sestavení proběhlo úspěšně.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Podokno výstupu sestavení Mac sady Visual Studio na panelu chyby se zprávou úspěšné sestavení":::

## <a name="add-a-console-app-to-the-solution"></a>Přidání konzolové aplikace do řešení

Přidejte konzolovou aplikaci, která používá knihovnu tříd. Aplikace vyzve uživatele, aby zadal řetězec a nahlásil, jestli řetězec začíná velkým znakem.

1. Na panelu **řešení** <kbd>stiskněte klávesu CTRL</kbd>a klikněte na `ClassLibraryProjects` řešení. Přidejte nový projekt **konzolové aplikace** tak, že vyberete šablonu z šablon **webové a konzolové**  >  **aplikace** a kliknete na tlačítko **Další**.

1. Jako **cílovou architekturu** vyberte **.NET Core 3,1** a vyberte **Další**.

1. Pojmenujte si **prezentující**projekt. Vyberte **vytvořit** a vytvořte projekt v řešení.

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Přidat projekt prezentace":::

1. Otevřete soubor *program.cs* . Nahraďte kód následujícím kódem:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Program vyzve uživatele k zadání řetězce. Označuje, zda řetězec začíná velkým znakem. Pokud uživatel stiskne klávesu <kbd>ENTER</kbd> bez zadání řetězce, aplikace skončí a okno konzoly se zavře.

   Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly. Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd. Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd.

1. Na panelu **řešení** <kbd>stiskněte CTRL</kbd>a klikněte na uzel **závislosti** nového projektu **prezentace** . V místní nabídce vyberte možnost **Přidat odkaz**.

1. V dialogovém okně **odkazy** vyberte **StringLibrary** a vyberte **OK**.

## <a name="run-the-app"></a>Spuštění aplikace

1. <kbd>stiskněte klávesu CTRL</kbd>a klikněte na projekt prezentace a v místní nabídce vyberte **spustit projekt** .

1. Vyzkoušejte program zadáním řetězců a stisknutím klávesy <kbd>ENTER</kbd>a stisknutím klávesy <kbd>ENTER</kbd> ukončete.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Okno konzoly Visual Studio pro Mac znázorňující spuštěnou aplikaci":::

## <a name="additional-resources"></a>Další zdroje

* [Vývoj knihoven pomocí .NET Core CLI](libraries.md)
* [.NET Standard verze a podporované platformy](../../standard/net-standard.md).
* [Zpráva k vydání verze pro Visual Studio 2019 pro Mac](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili řešení a projekt knihovny a Přidali jste projekt konzolové aplikace, který používá knihovnu. V dalším kurzu přidáte do řešení projekt testování částí.

> [!div class="nextstepaction"]
> [Testování knihovny .NET Standard pomocí .NET Core s využitím Visual Studio pro Mac](testing-library-with-visual-studio-mac.md)
