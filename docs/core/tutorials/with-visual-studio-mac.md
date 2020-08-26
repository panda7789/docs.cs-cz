---
title: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac
description: Naučte se vytvořit konzolovou aplikaci .NET Core pomocí Visual Studio pro Mac.
ms.date: 06/02/2020
ms.openlocfilehash: 8ffcb05ad85f53180ca1aaefbd2dfc7496946142
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867656"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a>Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac

V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core pomocí Visual Studio pro Mac.

> [!NOTE]
> Vaše zpětná vazba je vysoce ohodnocená. Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:
>
> * V Visual Studio pro Mac vyberte v nabídce **nápovědu**  >  **nahlásit problém** nebo **nahlásit problém** z úvodní obrazovky. tím otevřete okno pro podání zprávy o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Chcete-li vytvořit návrh, **vyberte v**  >  nabídce možnost**poskytnout návrh** z nabídky nebo **Poskytněte návrh** z úvodní obrazovky, který vás převezme na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Předpoklady

* [Visual Studio pro Mac verze 8,6 nebo novější](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Vyberte možnost instalace .NET Core. Instalace Xamarin je volitelná pro vývoj v .NET Core. Další informace naleznete v následujících zdrojích:

  * [Kurz: instalace Visual Studio pro Mac](/visualstudio/mac/installation).
  * [Podporované verze MacOS](../install/dependencies.md?pivots=os-macos)
  * [Verze .NET Core podporované nástrojem Visual Studio pro Mac](/visualstudio/mac/net-core-support).

## <a name="create-the-app"></a>Vytvoření aplikace

Vytvořte projekt konzolové aplikace .NET Core s názvem HelloWorld.

1. Spusťte Visual Studio pro Mac.

1. V úvodním okně vyberte **Nový** .

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Tlačítko Nový na úvodní obrazovce Visual Studio pro Mac":::

1. V dialogovém okně **Nový projekt** vyberte **aplikace** v uzlu **web a konzola** . Vyberte šablonu **Konzolová aplikace** a vyberte možnost **Další**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Seznam nových šablon projektů":::

1. V rozevíracím seznamu **Cílová architektura** v dialogovém okně **Konfigurovat novou konzolovou aplikaci** vyberte **.NET Core 3,1**a vyberte **Další**.

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Vybrat cílové rozhraní .NET Framework":::

1. Zadejte "HelloWorld" pro **název projektu**a vyberte **vytvořit**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Dialogové okno Konfigurovat novou konzolovou aplikaci":::

Šablona vytvoří jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!" v okně terminálu.

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

`Main` je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v `args` poli.

## <a name="run-the-app"></a>Spuštění aplikace

1. Stiskněte <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>ENTER</kbd>), aby se aplikace spouštěla bez ladění.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="V terminálu se zobrazí Hello World!":::

1. Zavřete okno **terminálu** .

## <a name="enhance-the-app"></a>Vylepšení aplikace

Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.

1. V *program.cs*nahraďte obsah `Main` metody, což je řádek, který volá `Console.WriteLine` , s následujícím kódem:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Tento kód zobrazí příkazový řádek v okně konzoly a počká, dokud uživatel nezadá řetězec následovaný klávesou <kbd>ENTER</kbd> . Tento řetězec je uložen v proměnné s názvem `name` . Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` . V okně konzoly se zobrazí tyto hodnoty. Nakonec se zobrazí výzva v okně konzoly a volá <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> metodu, která čeká na vstup uživatele.

   `\n`Představuje znak nového řádku.

   Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných. Hodnota výrazu je vložena do řetězce místo výrazu. Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).

1. Spusťte aplikaci stisknutím <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>ENTER</kbd>).

1. Zadáním názvu a stisknutím klávesy <kbd>ENTER</kbd>odpovězte na výzvu.

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Terminál zobrazuje upravený výstup programu":::

1. Zavřete terminál.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili konzolovou aplikaci .NET Core. V dalším kurzu ladění aplikace.

> [!div class="nextstepaction"]
> [Ladění konzolové aplikace .NET Core pomocí Visual Studio pro Mac](debugging-with-visual-studio-mac.md)
