---
title: Začínáme s jazykem C# a nástrojem Visual Studio Code
description: Naučte se, jak vytvořit a ladit první aplikaci .NET Core v jazyce C# pomocí kódu sady Visual Studio.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 49a1271f2bf74224e189e70bebf0d22c49408e5d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111059"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Začínáme s jazykem C# a nástrojem Visual Studio Code

.NET Core nabízí rychlou a modulární platformu pro vytváření aplikací, které běží na Windows, Linux a macOS. Použijte Visual Studio Kód s rozšířením C# získat výkonné prostředí pro úpravy s plnou podporou pro C# IntelliSense (inteligentní dokončení kódu) a ladění.

## <a name="prerequisites"></a>Požadavky

1. Nainstalujte [kód sady Visual Studio](https://code.visualstudio.com/).
2. Nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download).
3. Nainstalujte [rozšíření C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) pro kód sady Visual Studio. Další informace o instalaci rozšíření v kódu sady Visual Studio naleznete v [tématu VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Začněme s jednoduchým programem "Hello World" na .NET Core:

1. Otevření projektu:

    - Otevřete Visual Studio Code.
    - Klikněte na ikonu Průzkumníka v levé nabídce a potom klikněte na **Otevřít složku**.
    - Vyberte Otevřít složku **souboru** > **Open Folder** z hlavní nabídky, chcete-li otevřít složku, ve které má být projekt C#, a klepněte na tlačítko **Vybrat složku**. Pro náš příklad vytváříme složku pro náš projekt s názvem *HelloWorld*.

      ![Otevřená složka kódu Visual Studia](media/with-visual-studio-code/vs-code-open-folder.png)

2. Inicializovat projekt Jazyka C#:

    - Otevřete integrovaný terminál z visual studio kódu výběrem **zobrazit** > **integrovaný terminál** z hlavní nabídky.
    - Do okna terminálu `dotnet new console`zadejte příkaz .
    - Tento příkaz vytvoří *Program.cs* soubor ve složce s jednoduchým programem "Hello World", který je již napsán, spolu s souborem projektu C# s názvem *HelloWorld.csproj*.

      ![Dotnet new příkaz](media/with-visual-studio-code/dotnet-new-command.png)

3. Vyřešte datové zdroje sestavení:

    - Pro **rozhraní .NET Core 1.x**zadejte `dotnet restore`. Spuštění `dotnet restore` umožňuje přístup k požadované balíčky .NET Core, které jsou potřebné k sestavení projektu.

      ![Příkaz dotnet restore](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Spusťte program "Hello World":

    - Zadejte `dotnet run`.

      ![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

Můžete také sledovat krátké instruktážní video pro další nastavení nápovědy pro [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Ladění

1. Otevřete *Program.cs* kliknutím na něj. Při prvním otevření souboru C# v kódu sady Visual Studio [omnisharp](https://www.omnisharp.net/) načte v editoru.

    ![Otevření souboru Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code by vás měl vyzvat k přidání chybějících prostředků pro sestavení a ladění aplikace. Vyberte **ano**.

    ![Dotázat se na chybějící datové zdroje](media/with-visual-studio-code/missing-assets.png)

3. Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.

    ![Otevření karty Ladění v kódu Sady Visual Studio](media/with-visual-studio-code/open-debug-tab.png)

4. Vyhledejte zelenou šipku v horní části podokna. Ujistěte se, že rozbalovací rozbalovací soubor vedle něj má **vybranou .NET Core Launch (konzolu).**

    ![Výběr jádra rozhraní .NET v kódu sady Visual Studio](media/with-visual-studio-code/select-net-core.png)

5. Přidejte do projektu zarážku kliknutím na **okraj editoru**, což je mezera vlevo od čísel řádků v editoru vedle řádku 9, nebo přesuňte textový kurzor na řádek 9 v editoru a stiskněte <kbd>klávesu F9</kbd>.

    ![Nastavení zarážky](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Chcete-li zahájit ladění, stiskněte <kbd>klávesu F5</kbd> nebo vyberte zelenou šipku. Ladicí program zastaví provádění programu, když dosáhne zarážky, kterou nastavíte v předchozím kroku.
    - Při ladění můžete zobrazit místní proměnné v levém horním podokně nebo použít ladicí konzolu.

7. Chcete-li pokračovat v ladění, vyberte modrou šipku nahoře, nebo vyberte červený čtverec v horní části, který chcete zastavit.

    ![Spustit a ladit v kódu sady Visual Studio](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Další informace a tipy pro řešení potíží s laděním jádra .NET pomocí omnisharpu v kódu visual studia naleznete v [pokynech k nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Přidání třídy

1. Chcete-li přidat novou třídu, klepněte pravým tlačítkem myši do průzkumníka VSCode exploreru a vyberte **nový soubor**. Tím přidáte nový soubor do složky, kterou máte otevřenou ve VSCode.
2. Pojmenujte soubor *MyClass.cs*. Musíte jej uložit `.cs` s příponou na konci, aby byl rozpoznán jako soubor csharp.
3. Přidejte níže uvedený kód a vytvořte si první třídu. Nezapomeňte zahrnout správný obor názvů, abyste na něj mohli odkazovat ze *Program.cs* souboru:

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. Zavolejte do své nové třídy z hlavní metody v *Program.cs* přidáním níže uvedeného kódu:

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. Uložte změny a znovu spusťte program. Nová zpráva by se měla zobrazit s připojeným řetězcem.

    ```dotnetcli
    dotnet run
    ```

    Zobrazí se následující výstup:

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Nejčastější dotazy

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Chybí mi požadované prostředky k sestavení a ladění jazyka C# v kódu sady Visual Studio. V ladicím programu je uvedeno "Žádná konfigurace".

Rozšíření visual studio kód C# můžete generovat prostředky pro sestavení a ladění pro vás. Visual Studio Code vás vyzve ke generování těchto prostředků při prvním otevření projektu Jazyka C#. Pokud jste negenerovali datové zdroje, můžete tento příkaz spustit otevřením palety příkazů **(Zobrazit paletu příkazů >)** a zadáním příkazu ">.NET: Generovat datové zdroje pro sestavení a ladění". Výběrem této možnosti se vygenerují konfigurační soubory *.vscode*, *launch.json*a *tasks.json,* které potřebujete.

## <a name="see-also"></a>Viz také

- [Nastavení kódu sady Visual Studio](https://code.visualstudio.com/docs/setup/setup-overview)
- [Ladění v kódu sady Visual Studio](https://code.visualstudio.com/Docs/editor/debugging)
