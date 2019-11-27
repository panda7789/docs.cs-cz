---
title: Aplikace .NET Core Hello World s Visual Basic v aplikaci Visual Studio 2017
description: Naučte se vytvořit jednoduchou konzolovou aplikaci .NET Core s Visual Basic pomocí sady Visual Studio 2017.
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 63f5b422f1d5c4843d6fadb5973eaf16e50ee961
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428567"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Sestavení Hello World aplikace Visual Basic s .NET Core SDK v aplikaci Visual Studio 2017

Toto téma poskytuje podrobný Úvod k sestavování, ladění a publikování jednoduché konzolové aplikace .NET Core pomocí Visual Basic v aplikaci Visual Studio 2017. Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vytváření aplikací .NET Core. Pokud aplikace nemá závislosti specifické pro platformu, aplikace může běžet na libovolné platformě, kterou .NET Core cílí a na jakémkoli systému, ve kterém je nainstalováno rozhraní .NET Core.

## <a name="prerequisites"></a>Požadavky

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) s nainstalovanou úlohou vývoj ".NET Core pro různé platformy". Svou aplikaci můžete vyvíjet pomocí .NET Core 2,1 nebo novějších verzí.

Další informace najdete v tématu [závislosti a požadavky .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-windows).

## <a name="a-simple-hello-world-application"></a>Jednoduchá aplikace Hello World

Začněte vytvořením jednoduché konzolové aplikace "Hello World". Postupujte následovně:

1. Spusťte Visual Studio 2017. Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** . V dialogovém okně *Nový projekt** vyberte uzel **Visual Basic** následovaný uzlem **.NET Core** . Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** . Do textového pole **název** zadejte "HelloWorld". Klikněte na tlačítko **OK** .

   ![Dialog Nový projekt s vybranou konzolovou aplikací](./media/vb-with-visual-studio/visual-studio-new-project.png)

1. Visual Studio používá šablonu k vytvoření projektu. Šablona konzolové aplikace Visual Basic pro .NET Core automaticky definuje třídu, `Program`s jedinou metodou, `Main`, která jako argument přijímá <xref:System.String> Array. `Main` je vstupní bod aplikace, metoda, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .

   ![Visual Studio a nový HelloWorld projekt](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Šablona vytvoří jednoduchou aplikaci "Hello World". Volá metodu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pro zobrazení řetězcového literálu "Hello World!". v okně konzoly. Výběrem tlačítka **HelloWorld** se zelenou šipkou na panelu nástrojů můžete spustit program v režimu ladění. V takovém případě je okno konzoly viditelné pouze v krátkém časovém intervalu před jeho zavřením. K tomu dochází, protože metoda `Main` končí a aplikace skončí ihned po spuštění jednoho příkazu v metodě `Main`.

1. Chcete-li způsobit pozastavení aplikace před zavřením okna konzoly, přidejte následující kód hned za volání metody <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

   Tento kód vyzve uživatele, aby stiskne libovolný klíč, a pak program pozastaví, dokud nestiskne klávesu.

1. Na panelu nabídek vyberte **sestavení** **řešení**Build > . Tím se program zkompiluje do mezilehlého jazyka (IL), který je převeden do binárního kódu pomocí kompilátoru JIT (just-in-time).

1. Spusťte program tak, že vyberete tlačítko **HelloWorld** se zelenou šipkou na panelu nástrojů.

   ![Okno konzoly zobrazující Hello World pro pokračování stiskněte libovolnou klávesu](./media/with-visual-studio/hello-world-console.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

## <a name="enhancing-the-hello-world-application"></a>Vylepšení aplikace Hello World

Vylepšete aplikaci, aby se uživateli zobrazila výzva k jejímu jménu a zobrazila ji spolu s datem a časem. Chcete-li program upravit a otestovat, postupujte následovně:

1. V okně kódu zadejte následující kód Visual Basic hned za levou hranatou závorku, která následuje `Sub Main(args As String())` čára a před první pravou závorkou:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Tento kód nahrazuje obsah metody `Main`.

   ![Soubor programu Visual Studio s aktualizovanou hlavní metodou](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Tento kód zobrazí "" Jaké je vaše jméno? " v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER. Tento řetězec je uložen do proměnné s názvem `name`. Načte také hodnotu vlastnosti <xref:System.DateTime.Now?displayProperty=nameWithType>, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `currentDate`. Nakonec používá [interpolované řetězce](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) k zobrazení těchto hodnot v okně konzoly.

1. Zkompilujte program výběrem možnosti **sestavit** > **Sestavit řešení**.

1. Spusťte program v režimu ladění v sadě Visual Studio tak, že vyberete zelenou šipku na panelu nástrojů, stisknete klávesu F5 nebo vyberete položku nabídky **ladění** > **Spustit ladění** . Zadáním názvu a stisknutím klávesy ENTER odpovězte na výzvu.

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

Aplikaci jste vytvořili a spustili. Pro vývoj profesionální aplikace proveďte několik dalších kroků, aby vaše aplikace byla připravena k vydání:

- Chcete-li ladit aplikaci, přečtěte si téma [ladění aplikace Hello World .NET Core pomocí sady Visual Studio 2017](debugging-with-visual-studio.md).

- Chcete-li publikovat Distribuovatelný verzi aplikace, přečtěte si téma [publikování aplikace Hello World .NET Core pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Související témata

Namísto konzolové aplikace můžete také vytvořit .NET Standard knihovny tříd pomocí Visual Basic, .NET Core a Visual Studio 2017. Podrobný Úvod naleznete v tématu [Vytvoření knihovny .NET Standard s Visual Basic a .NET Core SDK v aplikaci Visual Studio 2017](vb-library-with-visual-studio.md).
