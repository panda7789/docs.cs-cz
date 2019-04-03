---
title: Začínáme s C# a Visual Studio Code
description: Zjistěte, jak vytvářet a ladit vaši první aplikaci .NET Core v jazyce C# pomocí nástroje Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: d91427197662d61c1c3ffc242de9b1128b81b9c6
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890550"
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

    * Otevřete Visual Studio Code.
    * Klikněte na ikonu Průzkumníka v nabídce vlevo a pak klikněte na tlačítko **otevřít složku**.
    * Vyberte **souboru** > **otevřít složku** v hlavní nabídce otevřete složku projektu C# v a klikněte na tlačítko chcete **vybrat složku**. V našem příkladu vytváříme složku pro náš projekt s názvem *HelloWorld*.

      ![Visual Studio Code, otevřít složku](media/with-visual-studio-code/vs-code-open-folder.png)

2. Inicializace projektu v jazyce C#:
    * Otevřít integrovaný terminál z Visual Studio Code tak, že vyberete **zobrazení** > **integrovaný terminál** z hlavní nabídky.
    * V okně terminálu zadejte `dotnet new console`.
    * Tento příkaz vytvoří `Program.cs` souboru ve složce s jednoduchou "Hello World" program již vytvořený, spolu s C# soubor projektu s názvem `HelloWorld.csproj`.

      ![Nový příkaz dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. Vyřešte prostředky sestavení:

    * Pro **.NET Core 1.x**, typ `dotnet restore`. Spuštění `dotnet restore` dává vám přístup k požadované balíčky .NET Core, které jsou potřebné k sestavení projektu.

      ![Příkaz dotnet restore](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Spusťte program "Hello World":

    * Typ `dotnet run`.

      ![Spusťte příkaz dotnet](media/with-visual-studio-code/dotnet-run-command.png)

Můžete také zhlédnout krátké Výukové video o další pomoc instalační program na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Ladit

1. Otevřít *Program.cs* kliknutím na ni. Při prvním otevření souboru C# v sadě Visual Studio Code [OmniSharp](https://www.omnisharp.net/) načte v editoru.

    ![Otevřete soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code by se zobrazit výzva k přidání chybějící prostředky pro sestavení a ladění aplikace. Vyberte **Ano**.

    ![Výzva k zadání chybějících prostředků](media/with-visual-studio-code/missing-assets.png)

3. Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.

    ![Otevřete kartu ladění ve Visual Studio Codee](media/with-visual-studio-code/open-debug-tab.png)

4. Vyhledejte na zelenou šipku v horní části podokna. Ujistěte se, že má rozevíracího seznamu vedle něj `.NET Core Launch (console)` vybrané.

    ![Výběr platformy .NET Core v sadě Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. Přidejte zarážku do svého projektu kliknutím na **okraj editoru**, což je místo na levé straně čísla řádků v editoru vedle řádku 9, nebo textový kurzor na řádku 9 v editoru a stiskněte klávesu <kbd>F9</kbd>.

    ![Nastavením zarážky](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Chcete-li spustit ladění, vyberte <kbd>F5</kbd> nebo zelenou šipku. Ladicí program se zastaví provádění programu při dosažení zarážky, které jste nastavili v předchozím kroku.
    * Při ladění, můžete zobrazit místní proměnné v horním levém podokně nebo použít konzolu pro ladění.

7. Vyberte modrou šipkou v horní části stránky pro pokračování v ladění, nebo vyberte červený čtvereček v horní části zastavit.

    ![Spustit a ladit ve Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Další informace a řešení potíží s tipy k ladění rozhraní .NET Core s OmniSharp ve Visual Studio Code najdete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Přidat třídu

1. Vyberte a přidejte nové třídy, klikněte pravým tlačítkem v Průzkumníku VSCode **nový soubor**. To přidá nový soubor do složky, otevřeného ve VSCode.
2. Název souboru `MyClass.cs`. Musíte ji uložit `.cs` rozšíření na straně, chcete-li rozpoznán jako soubor csharp.
3. Přidejte kód uvedený níže pro vytvoření vaší první třídy. Ujistěte se, že obsahují správný obor názvů, takže můžete na něj mohli odkazovat z vaší `Program.cs` souboru.
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

4. Volání nové třídy z hlavní metodu v `Program.cs` tak, že přidáte kód uvedený níže.

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            MyClass c1 = new MyClass();
            Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
        }
    }
}
```

5. Uložte změny a spusťte program znovu. S připojený řetězec by se zobrazit nová zpráva.
```console
> dotnet run
Hello World! Happy coding!
```

## <a name="faq"></a>Nejčastější dotazy

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Chybí požadované prostředky pro sestavení a ladění jazyka C# ve Visual Studio Code. Moje ladicí program říká "Žádná konfigurace."

Rozšíření Visual Studio kódu C# může generovat prostředky pro sestavení a ladění za vás. Visual Studio Code zobrazí výzvu ke generování těchto prostředků, při prvním otevření projektu v jazyce C#. Pokud nebyl vygenerujte prostředky, a spustíte tento příkaz můžete stále tak, že otevřete paletu příkazů (**zobrazení > paletu příkazů**) a zadejte text "> .NET: Generovat prostředky pro sestavování a ladění". Tento výběr generuje .vscode launch.json a tasks.json konfigurační soubory, které potřebujete.

## <a name="see-also"></a>Viz také:

- [Nastavení aplikace Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Ladění ve Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
