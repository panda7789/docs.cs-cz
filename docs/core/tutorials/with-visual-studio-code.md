---
title: Začínáme s C# a Visual Studio Code – průvodce v C#
description: Zjistěte, jak vytvářet a ladit vaši první aplikaci .NET Core v jazyce C# pomocí nástroje Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 321edcebdea141b7290fa57b47c8d9fc91d3521c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063664"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Začínáme s C# a Visual Studio Code

.NET core nabízí rychlou modulární platformu pro vytváření aplikací, které běží ve Windows, Linuxu a macOS. Získání výkonné prostředí s plnou podporu pro C# IntelliSense (inteligentního dokončování kódu) pro úpravy a ladění pomocí Visual Studio Code s rozšířením C#.

## <a name="prerequisites"></a>Požadavky

1. Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).
2. Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/download/core).
3. Nainstalujte [rozšíření jazyka C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pro Visual Studio Code. Další informace o tom, jak rozšíření nainstalovat Visual Studio Code najdete v tématu [VS Code příponou Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Pusťme se do práce s jednoduchý program "Hello World" v rozhraní .NET Core:

1. Otevřete projekt:

    * Otevřít Visual Studio Code.
    * Klikněte na ikonu Průzkumníka v nabídce vlevo a pak klikněte na tlačítko **otevřít složku**.
    * Vyberte **souboru** > **otevřít složku** v hlavní nabídce otevřete složku projektu C# v a klikněte na tlačítko chcete **vybrat složku**. V našem příkladu vytváříme složku pro náš projekt s názvem *HelloWorld*.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. Inicializace projektu v jazyce C#:
    * Otevřít integrovaný terminál z Visual Studio Code tak, že vyberete **zobrazení** > **integrovaný terminál** z hlavní nabídky.
    * V okně terminálu zadejte `dotnet new console`.
    * Tento příkaz vytvoří `Program.cs` souboru ve složce s jednoduchou "Hello World" program již vytvořený, spolu s C# soubor projektu s názvem `HelloWorld.csproj`.

      ![Nový příkaz dotnet](media/with-visual-studio-code/dotnetnew.png)

3. Vyřešte prostředky sestavení:

    * Pro **.NET Core 1.x**, typ `dotnet restore`. Spuštění `dotnet restore` dává vám přístup k požadované balíčky .NET Core, které jsou potřebné k sestavení projektu.

      ![Příkaz dotnet restore](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Spusťte program "Hello World":

    * Typ `dotnet run`.

      ![Spusťte příkaz dotnet](media/with-visual-studio-code/dotnetrun.png)

Můžete také zhlédnout krátké Výukové video o další pomoc instalační program na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Ladit

1. Otevřít *Program.cs* kliknutím na ni. Při prvním otevření souboru C# v sadě Visual Studio Code [OmniSharp](http://www.omnisharp.net/) načte v editoru.

    ![Otevřete soubor Program.cs](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code by se zobrazit výzva k přidání chybějící prostředky pro sestavení a ladění aplikace. Vyberte **Ano**.

    ![Výzva k zadání chybějících prostředků](media/with-visual-studio-code/missing-assets.png)

3. Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.

    ![Otevřete kartu ladění](media/with-visual-studio-code/opendebug.png)

4. Vyhledejte na zelenou šipku v horní části podokna. Ujistěte se, že má rozevíracího seznamu vedle něj `.NET Core Launch (console)` vybrané.

    ![Výběr .NET Core](media/with-visual-studio-code/selectcore.png)

5. Přidejte zarážku do svého projektu kliknutím na **okraj editoru**, což je místo na levé straně čísla řádků v editoru vedle řádku 9, nebo textový kurzor na řádku 9 v editoru a stiskněte klávesu <kbd>F9</kbd>.

    ![Nastavením zarážky](media/with-visual-studio-code/setbreakpoint.png)

6. Chcete-li spustit ladění, vyberte <kbd>F5</kbd> nebo zelenou šipku. Ladicí program se zastaví provádění programu při dosažení zarážky, které jste nastavili v předchozím kroku.
    * Při ladění, můžete zobrazit místní proměnné v horním levém podokně nebo použít konzolu pro ladění.

    ![Spuštění a ladění](media/with-visual-studio-code/rundebug.png)

7. Vyberte zelenou šipku v horní části stránky pro pokračování v ladění, nebo vyberte červený čtvereček v horní části zastavit.

> [!TIP]
> Další informace a řešení potíží s tipy k ladění rozhraní .NET Core s OmniSharp ve Visual Studio Code najdete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="faq"></a>Nejčastější dotazy

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Chybí požadované prostředky pro sestavení a ladění jazyka C# ve Visual Studio Code. Moje ladicí program říká "Žádná konfigurace."

Rozšíření Visual Studio kódu C# může generovat prostředky pro sestavení a ladění za vás. Visual Studio Code zobrazí výzvu ke generování těchto prostředků, při prvním otevření projektu v jazyce C#. Pokud nebyl vygenerujte prostředky, a spustíte tento příkaz můžete stále tak, že otevřete paletu příkazů (**zobrazení > paletu příkazů**) a zadejte text "> .NET: generovat prostředky pro sestavování a ladění". Tento výběr generuje .vscode launch.json a tasks.json konfigurační soubory, které potřebujete.

## <a name="see-also"></a>Viz také:

* [Nastavení aplikace Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
* [Ladění ve Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
