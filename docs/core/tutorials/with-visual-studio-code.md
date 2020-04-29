---
title: Začínáme s jazykem C# a nástrojem Visual Studio Code
description: Naučte se, jak vytvořit a ladit svou první aplikaci .NET Core v jazyce C# pomocí Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506879"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Začínáme s jazykem C# a nástrojem Visual Studio Code

.NET Core poskytuje rychlou a modulární platformu pro vytváření aplikací, které běží na systémech Windows, Linux a macOS. Použijte Visual Studio Code s rozšířením C# k získání výkonného prostředí pro úpravy s plnou podporou pro C# IntelliSense (inteligentní dokončování kódu) a ladění.

## <a name="prerequisites"></a>Požadavky

1. Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).
2. Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).
3. Nainstalujte [rozšíření C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) pro Visual Studio Code. Další informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

Začínáme s jednoduchým programem "Hello World" v .NET Core:

1. Otevřete projekt:

    - Otevřete Visual Studio Code.
    - V hlavní nabídce vyberte **soubor** > **Otevřít složku** .
    - Vytvořte složku s názvem *HelloWorld*a klikněte na **Vybrat složku**. Název složky se ve výchozím nastavení zobrazí jako název projektu a název oboru názvů. Později do kurzu přidáte kód, který předpokládá, že je `HelloWorld`obor názvů projektu.

1. Inicializovat projekt C#:

    - Otevření terminálu z Visual Studio Code výběrem možnosti **Zobrazit** > **terminál** v hlavní nabídce.
    - V okně terminálu zadejte `dotnet new console`.

      Tento příkaz vytvoří soubor *program.cs* ve složce s jednoduchým již zapsaným programem "Hello World" společně se souborem projektu C# s názvem *HelloWorld. csproj*.

      ![Příkaz dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

1. Spusťte program "Hello World":

    - V okně terminálu zadejte `dotnet run`.

      ![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a>Ladit

1. Otevřete *program.cs* kliknutím na něj. Při prvním otevření souboru jazyka C# v Visual Studio Code se [OmniSharp](https://www.omnisharp.net/) načte v editoru.

    ![Otevřít soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code vás vyzve k přidání chybějících assetů pro sestavení a ladění vaší aplikace. Vyberte **Ano**.

    ![Vyzvat k chybějícím prostředkům](media/with-visual-studio-code/missing-assets.png)

1. Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.

    ![Otevřete kartu ladění v Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. Vyhledejte zelenou šipku v horní části podokna. Zajistěte, aby v rozevíracím seznamu vedle něho byla vybrána možnost **spuštění rozhraní .NET Core (konzola)** .

    ![Výběr .NET Core v Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. Přidejte do projektu zarážku kliknutím na **okraj editoru**, což je místo na levé straně čísel řádků v editoru, vedle řádku 9 nebo přesuňte kurzor myši na řádek 9 v editoru a stiskněte klávesu <kbd>F9</kbd>.

    ![Nastavení zarážky](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. Chcete-li spustit ladění, stiskněte klávesu <kbd>F5</kbd> nebo vyberte zelenou šipku. Ladicí program zastaví provádění programu při dosažení zarážky, kterou jste nastavili v předchozím kroku.
    - Během ladění můžete zobrazit místní proměnné v levém horním podokně nebo použít konzolu ladění.

1. Vyberte modrou šipku v horní části a pokračujte v ladění, nebo vyberte červené čtverce v horní části a zastavte.

    ![Spuštění a ladění v Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Další informace a tipy pro řešení potíží s laděním .NET Core pomocí OmniSharp v Visual Studio Code najdete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Přidání třídy

1. Chcete-li přidat novou třídu, klikněte pravým tlačítkem myši v Průzkumníkovi VSCode pod *program.cs* a vyberte možnost **nový soubor**. Tím se přidá nový soubor do složky, kterou jste otevřeli v VSCode.
1. Pojmenujte soubor *MyClass.cs*. Je nutné jej uložit s `.cs` příponou na konci, aby jej bylo možné rozpoznat jako CSharp soubor.
1. Přidejte následující kód k vytvoření první třídy.

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

1. Zavolejte svou novou třídu z `Main` metody tak, že nahradíte kód v *program.cs* pomocí následujícího kódu:

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

1. Uložte provedené změny.

1. Spusťte program znovu.

    ```dotnetcli
    dotnet run
    ```

    Nová zpráva se zobrazí spolu s připojovacím řetězcem.

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Nejčastější dotazy

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Chybí požadované prostředky pro sestavení a ladění C# v Visual Studio Code. Můj ladicí program říká "žádnou konfiguraci".

Rozšíření Visual Studio Code C# může generovat assety pro sestavení a ladění. Visual Studio Code se zobrazí výzva, abyste tyto prostředky vygenerovali při prvním otevření projektu v jazyce C#. Pokud jste nevytvořili prostředky, můžete přesto spustit tento příkaz otevřením palety příkazů (**zobrazení palety příkazů zobrazit >**) a zadáním "> .NET: generovat prostředky pro sestavení a ladění". Výběrem této možnosti se vytvoří konfigurační soubory *. VSCode*, *Launch. JSON*a *Tasks. JSON* , které potřebujete.

## <a name="see-also"></a>Viz také

- [Nastavení Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Ladění v Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
