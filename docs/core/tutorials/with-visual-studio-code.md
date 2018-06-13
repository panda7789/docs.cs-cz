---
title: Začínáme s C# a Visual Studio Code - průvodce v C#
description: Naučte se vytvářet a ladit první aplikaci .NET Core v C# s použitím Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 8958c39ba16cadbfab95e35fa36e8e85ce0a4ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213613"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Začínáme s C# a Visual Studio Code

.NET core poskytuje rychlou modulární platformu pro vytváření aplikací, které běží na systému Windows, Linux a systému macOS. Použijte Visual Studio Code s příponou C# získání výkonné možnosti s plnou podporu pro C# IntelliSense (doplňování kódu pro inteligentní) úprav a ladění.

## <a name="prerequisites"></a>Požadavky

1. Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).
2. Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/download/core).
3. Nainstalujte [C# rozšíření](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pro Visual Studio Code. Další informace o tom, jak nainstalovat rozšíření na Visual Studio Code najdete v tématu [VS kód rozšíření Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Můžeme začít pracovat s jednoduchý program "Hello World" na .NET Core:

1. Otevřete projekt:

    * Otevřete Visual Studio Code.
    * Klikněte na ikonu Explorer v levé nabídce a potom klikněte na **otevřít složku**.
    * Vyberte **soubor** > **otevřete složku** z hlavní nabídky otevření složky chcete projektu C# je v a klikněte na tlačítko **vyberte složku**. Pro náš příklad vytváříme složku pro naše projektu s názvem *HelloWorld*.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. Inicializace projektu C#:
    * Otevřete integrované terminál z Visual Studio Code výběrem **zobrazení** > **integrované Terminálové** z hlavní nabídky.
    * V okně terminálu zadejte `dotnet new console`.
    * Tento příkaz vytvoří `Program.cs` soubor ve složce s jednoduché "Hello, World" program již vytvořený, společně s C# projektu soubor s názvem `HelloWorld.csproj`.

      ![Nový příkaz dotnet.](media/with-visual-studio-code/dotnetnew.png)

3. Vyřešte prostředky sestavení:

    * Pro **.NET Core 1.x**, typ `dotnet restore`. Spuštění `dotnet restore` dává vám přístup k požadované balíčky .NET Core, které jsou potřebné k sestavení projektu.

      ![Příkaz restore dotnet.](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Spusťte program "Hello World":

    * Typ `dotnet run`. 

      ![Dotnet, spusťte příkaz](media/with-visual-studio-code/dotnetrun.png)

Můžete také shlédnout krátké video kurz pro další pomoc instalační program na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [systému macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Ladit

1. Otevřete *Program.cs* kliknutím na. Při prvním otevření souboru C# v sadě Visual Studio Code [OmniSharp](http://www.omnisharp.net/) načte v editoru.

    ![Otevřete soubor Program.cs](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code by se zobrazit výzva k přidání chybějící prostředky pro sestavení a ladění aplikace. Vyberte **Ano**. 

    ![Výzva k zadání chybějící prostředky](media/with-visual-studio-code/missing-assets.png)

3. Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v levé nabídce.

    ![Otevřete kartu ladění](media/with-visual-studio-code/opendebug.png)

4. Vyhledejte na zelenou šipku v horní části podokna. Ověřte, zda má rozevíracího seznamu vedle `.NET Core Launch (console)` vybrané.

    ![Výběr .NET Core](media/with-visual-studio-code/selectcore.png)

5. Do projektu přidejte zarážku kliknutím na **okraj editoru**, což je místo na levé straně čísla řádků v editoru vedle řádku 9.

    ![Nastavení boru přerušení](media/with-visual-studio-code/setbreakpoint.png)

6. Chcete-li začít, ladění, vyberte <kbd>F5</kbd> nebo zelenou šipku. Ladicí program zastaví programu, když dorazí do zarážek, které jste nastavili v předchozím kroku.
    * Při ladění, můžete zobrazit místní proměnné v levém horním podokně nebo použít konzolu pro ladění.

    ![Spuštění a ladění](media/with-visual-studio-code/rundebug.png)

7. Vyberte zelenou šipku v horní části, chcete-li pokračovat, ladění, nebo červený čtvereček v horní části zastavit.

> [!TIP] 
> Další informace a tipy na .NET Core ladění pomocí OmniSharp v kódu Visual Studio pro odstraňování potíží naleznete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="see-also"></a>Viz také
[Nastavení kódu v jazyce Visual Studio](https://code.visualstudio.com/docs/setup/setup-overview)   
[Ladění v sadě Visual Studio kódu](https://code.visualstudio.com/Docs/editor/debugging)
