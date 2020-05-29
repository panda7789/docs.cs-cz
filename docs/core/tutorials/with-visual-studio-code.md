---
title: Vytvoření konzolové aplikace pomocí .NET Core pomocí Visual Studio Code
description: Naučte se vytvořit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI.
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201709"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a>Kurz: Vytvoření konzolové aplikace pomocí .NET Core pomocí Visual Studio Code

V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI. Úkoly projektu, jako je vytváření, kompilování a spuštění projektu, jsou prováděny pomocí rozhraní příkazového řádku, takže můžete postupovat podle tohoto kurzu v jiném editoru kódu a v případě potřeby spustit příkazy v terminálu.

## <a name="prerequisites"></a>Požadavky

1. [Visual Studio Code](https://code.visualstudio.com/) s nainstalovaným [rozšířením C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) . Informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [.NET Core 3,1 SDK nebo novější](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>Vytvoření aplikace

1. Otevřete Visual Studio Code.

1. Vytvořte projekt.

   1. V hlavní nabídce vyberte **soubor**  >  **Otevřít složku** / **otevřít...** , vytvořte složku *HelloWorld* a klikněte na **Vybrat složku** / **otevřít**.

      Název složky se ve výchozím nastavení zobrazí jako název projektu a název oboru názvů. Později do kurzu přidáte kód, který předpokládá, že je obor názvů projektu `HelloWorld` .

   1. Kliknutím na **Terminal** **Zobrazit**  >  **terminál** v hlavní nabídce otevřete terminál v Visual Studio Code.

      **Terminál** se otevře s příkazovým řádkem ve složce *HelloWorld* .

   1. V **terminálu**zadejte následující příkaz:

      ```dotnetcli
      dotnet new console
      ```

Šablona konzolové aplikace pro .NET Core definuje třídu `Program` s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument. Soubor *program.cs* má následující kód:

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

`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .

Šablona vytvoří jednoduchou aplikaci, která volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!" v okně konzoly.

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

1. Nahraďte obsah `Main` metody v *program.cs*, což je aktuálně pouze řádek, který volá `Console.WriteLine` , s následujícím kódem:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   Tento kód zobrazí "" Jaké je vaše jméno? " v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou **ENTER** . Tento řetězec je uložen v proměnné s názvem `name` . Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` . Nakonec tyto hodnoty zobrazí v okně konzoly.

   `\n`Představuje znak nového řádku.

   Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných. Hodnota výrazu je vložena do řetězce místo výrazu. Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).

1. Uložte provedené změny.

   > [!IMPORTANT]
   > V Visual Studio Code musíte explicitně uložit změny. Na rozdíl od sady Visual Studio se změny souborů při sestavení a spuštění aplikace automaticky neuloží.

1. Spusťte program znovu:

   ```dotnetcli
   dotnet run
   ```

1. Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Okno terminálu s upraveným výstupem programu":::

1. Ukončete program stisknutím libovolné klávesy.

## <a name="additional-resources"></a>Další zdroje

- [Nastavení Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili aplikaci .NET Core. V dalším kurzu ladění aplikace.

> [!div class="nextstepaction"]
> [Ladění konzolové aplikace .NET Core pomocí Visual Studio Code](debugging-with-visual-studio-code.md)
