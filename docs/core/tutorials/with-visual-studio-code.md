---
title: Začínáme s jazykem C# a nástrojem Visual Studio Code
description: Naučte se, jak vytvořit a ladit první aplikaci .NET Core C# pomocí Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: acd1c300545bc6c107552576180afd7dec6b7382
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503517"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Začínáme s jazykem C# a nástrojem Visual Studio Code

.NET Core poskytuje rychlou a modulární platformu pro vytváření aplikací, které běží na systémech Windows, Linux a macOS. Pomocí Visual Studio Code s C# rozšířením můžete získat výkonné prostředí pro C# úpravy s plnou podporou technologie IntelliSense (inteligentní dokončování kódu) a ladění.

## <a name="prerequisites"></a>Předpoklady

1. Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).
2. Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).
3. Nainstalujte [ C# rozšíření](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pro Visual Studio Code. Další informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Pojďme začít jednoduchý program Hello World v .NET Core:

1. Otevřete projekt:

    - Otevřete Visual Studio Code.
    - V levé nabídce klikněte na ikonu Průzkumníka a pak klikněte na **Otevřít složku**.
    - Vyberte **soubor** > **Otevřít složku** v hlavní nabídce a otevřete složku, ve které chcete mít C# projekt, a klikněte na **Vybrat složku**. V našem příkladu vytvoříme složku pro náš projekt s názvem *HelloWorld*.

      ![Visual Studio Code otevření složky](media/with-visual-studio-code/vs-code-open-folder.png)

2. Inicializovat C# projekt:

    - Otevřete integrovaný terminál z Visual Studio Code výběrem možnosti **zobrazit** > **integrovaného terminálu** z hlavní nabídky.
    - V okně terminálu zadejte `dotnet new console`.
    - Tento příkaz vytvoří soubor *program.cs* ve složce s jednoduchým již zapsaným programem "Hello World" společně se souborem C# projektu s názvem *HelloWorld. csproj*.

      ![Příkaz dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

3. Vyřešte prostředky sestavení:

    - Pro **.NET Core 1. x**zadejte `dotnet restore`. Spuštění `dotnet restore` umožňuje přístup k požadovaným balíčkům .NET Core, které jsou potřeba k sestavení projektu.

      ![Příkaz dotnet restore](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Spusťte program "Hello World":

    - Zadejte `dotnet run`.

      ![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

Můžete si také prohlédnout krátký video kurz pro další nápovědu k instalaci ve [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Ladění

1. Otevřete *program.cs* kliknutím na něj. Při prvním otevření C# souboru v Visual Studio Code [OmniSharp](https://www.omnisharp.net/) načte v editoru.

    ![Otevřít soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code by se vám měla zobrazit výzva k přidání chybějících assetů pro sestavení a ladění vaší aplikace. Vyberte **Ano**.

    ![Vyzvat k chybějícím prostředkům](media/with-visual-studio-code/missing-assets.png)

3. Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.

    ![Otevřete kartu ladění v Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. Vyhledejte zelenou šipku v horní části podokna. Zajistěte, aby v rozevíracím seznamu vedle něho byla vybrána možnost **spuštění rozhraní .NET Core (konzola)** .

    ![Výběr .NET Core v Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. Přidejte do projektu zarážku kliknutím na **okraj editoru**, což je místo na levé straně čísel řádků v editoru, vedle řádku 9 nebo přesuňte kurzor myši na řádek 9 v editoru a stiskněte klávesu <kbd>F9</kbd>.

    ![Nastavení zarážky](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Chcete-li spustit ladění, stiskněte klávesu <kbd>F5</kbd> nebo vyberte zelenou šipku. Ladicí program zastaví provádění programu při dosažení zarážky, kterou jste nastavili v předchozím kroku.
    - Během ladění můžete zobrazit místní proměnné v levém horním podokně nebo použít konzolu ladění.

7. Vyberte modrou šipku v horní části a pokračujte v ladění, nebo vyberte červené čtverce v horní části a zastavte.

    ![Spuštění a ladění v Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Další informace a tipy pro řešení potíží s laděním .NET Core pomocí OmniSharp v Visual Studio Code najdete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Přidání třídy

1. Pokud chcete přidat novou třídu, klikněte pravým tlačítkem na VSCode Explorer a vyberte **nový soubor**. Tím se přidá nový soubor do složky, kterou jste otevřeli v VSCode.
2. Pojmenujte soubor *MyClass.cs*. Je nutné jej uložit s příponou `.cs` na konci, aby jej bylo možné rozpoznat jako soubor CSharp.
3. Přidejte následující kód k vytvoření první třídy. Ujistěte se, že jste zahrnuli správný obor názvů, abyste na něj mohli odkazovat ze souboru *program.cs* :

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

4. Zavolejte svou novou třídu z metody Main v *program.cs* přidáním kódu níže:

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

5. Uložte změny a spusťte program znovu. Nová zpráva by se měla zobrazit spolu s připojovacím řetězcem.

    ```dotnetcli
    dotnet run
    ```

    Zobrazí se následující výstup:

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Nejčastější dotazy

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Chybí požadované prostředky pro sestavení a ladění C# v Visual Studio Code. Můj ladicí program říká "žádnou konfiguraci".

Rozšíření Visual Studio Code C# může generovat assety pro sestavení a ladění. Visual Studio Code vás vyzve k vygenerování těchto assetů při prvním otevření C# projektu. Pokud jste nevytvořili prostředky, můžete přesto spustit tento příkaz otevřením palety příkazů (**zobrazení palety příkazů zobrazit >** ) a zadáním "> .NET: generovat prostředky pro sestavení a ladění". Výběrem této možnosti se vytvoří konfigurační soubory *. VSCode*, *Launch. JSON*a *Tasks. JSON* , které potřebujete.

## <a name="see-also"></a>Viz také

- [Nastavení Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Ladění v Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
