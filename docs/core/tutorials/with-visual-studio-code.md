---
title: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code
description: Naučte se vytvořit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI.
ms.date: 05/22/2020
ms.openlocfilehash: e936c23d8525e42a9d2781cc680067c9da2ce42f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811923"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a>Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code

V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI. Úkoly projektu, jako je vytváření, kompilování a spuštění projektu, jsou prováděny pomocí .NET Core CLI. Pokud chcete, můžete postupovat podle tohoto kurzu v jiném editoru kódu a v terminálu spustit příkazy.

## <a name="prerequisites"></a>Předpoklady

1. [Visual Studio Code](https://code.visualstudio.com/) s nainstalovaným [rozšířením C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) . Informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [.NET Core 3,1 SDK nebo novější](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>Vytvoření aplikace

Vytvořte projekt konzolové aplikace .NET Core s názvem HelloWorld.

1. Spuštění nástroje Visual Studio Code

1. V hlavní nabídce vyberte **soubor**  >  **Otevřít složku** (**soubor**  >  **otevřít...** v MacOS).

1. V dialogovém okně **Otevřít složku** vytvořte složku *HelloWorld* a klikněte na **Vybrat složku** (**otevřít** v MacOS).

   Název složky se ve výchozím nastavení zobrazí jako název projektu a název oboru názvů. Později do kurzu přidáte kód, který předpokládá, že je obor názvů projektu `HelloWorld` .

1. Kliknutím na **Terminal** **Zobrazit**  >  **terminál** v hlavní nabídce otevřete terminál v Visual Studio Code.

   **Terminál** se otevře s příkazovým řádkem ve složce *HelloWorld* .

1. V **terminálu**zadejte následující příkaz:

   ```dotnetcli
   dotnet new console
   ```

Šablona vytvoří jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení " :::no-loc text="Hello World!"::: " v okně konzoly.

Kód šablony definuje třídu, `Program` , s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument:

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

`Main` je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .

## <a name="run-the-app"></a>Spuštění aplikace

V **terminálu**spusťte následující příkaz:

```dotnetcli
dotnet run
```

Program zobrazí "Hello World!" a končí.

![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>Vylepšení aplikace

Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.

1. Otevřete *program.cs* kliknutím na něj.

   Při prvním otevření souboru jazyka C# v Visual Studio Code se [OmniSharp](https://www.omnisharp.net/) načte v editoru.

   ![Otevřít soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Pokud vás Visual Studio Code vyzve k přidání chybějících assetů k sestavení a ladění vaší aplikace, vyberte **Ano** .

   ![Vyzvat k chybějícím prostředkům](media/with-visual-studio-code/missing-assets.png)

1. Nahraďte obsah `Main` metody v *program.cs*, což je řádek, který volá `Console.WriteLine` , s následujícím kódem:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Tento kód zobrazí příkazový řádek v okně konzoly a počká, dokud uživatel nezadá řetězec následovaný klávesou <kbd>ENTER</kbd> . Tento řetězec je uložen v proměnné s názvem `name` . Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` . V okně konzoly se zobrazí tyto hodnoty. Nakonec se zobrazí výzva v okně konzoly a volá <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> metodu, která čeká na vstup uživatele.

   `\n`Představuje znak nového řádku.

   Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných. Hodnota výrazu je vložena do řetězce místo výrazu. Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).

1. Uložte provedené změny.

   > [!IMPORTANT]
   > V Visual Studio Code musíte explicitně uložit změny. Na rozdíl od sady Visual Studio se změny souborů při sestavení a spuštění aplikace automaticky neuloží.

1. Spusťte program znovu:

   ```dotnetcli
   dotnet run
   ```

1. Zadáním názvu a stisknutím klávesy <kbd>ENTER</kbd> odpovězte na výzvu.

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Okno terminálu s upraveným výstupem programu":::

1. Ukončete program stisknutím libovolné klávesy.

## <a name="additional-resources"></a>Další zdroje

- [Nastavení Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili konzolovou aplikaci .NET Core. V dalším kurzu ladění aplikace.

> [!div class="nextstepaction"]
> [Ladění konzolové aplikace .NET Core pomocí Visual Studio Code](debugging-with-visual-studio-code.md)
