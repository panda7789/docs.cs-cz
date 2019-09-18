---
title: Sestavení aplikace C# Hello World pomocí .NET Core v aplikaci Visual Studio 2017
description: Naučte se vytvářet jednoduché konzolové aplikace .NET Core pomocí C# sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: b42a71993cb120c88b90e867b7af23873b99d280
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039601"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Sestavení aplikace C# Hello World pomocí .NET Core SDK v aplikaci Visual Studio 2017

Toto téma poskytuje podrobný Úvod k sestavování, ladění a publikování jednoduché konzolové aplikace .NET Core pomocí C# sady Visual Studio 2017. Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vytváření aplikací .NET Core. Pokud aplikace nemá závislosti specifické pro platformu, aplikace může běžet na libovolné platformě, kterou .NET Core cílí a na jakémkoli systému, ve kterém je nainstalováno rozhraní .NET Core.

## <a name="prerequisites"></a>Požadavky

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) s nainstalovanou úlohou vývoj ".NET Core pro různé platformy". Svou aplikaci můžete vyvíjet pomocí .NET Core 2,1 nebo novějších verzí.

Další informace najdete v tématu [požadavky pro .NET Core v systému Windows](../windows-prerequisites.md) .

## <a name="a-simple-hello-world-application"></a>Jednoduchá aplikace Hello World

Začněte vytvořením jednoduché konzolové aplikace "Hello World". Postupujte podle těchto kroků:

1. Spusťte Visual Studio 2017. Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** . V dialogovém okně *Nový projekt** vyberte uzel  **C# vizuálu** následovaný uzlem **.NET Core** . Pak vyberte šablonu projektu **aplikace konzoly (.NET Core)** . Do textového pole **název** zadejte "HelloWorld". Vyberte tlačítko **OK**.

   ![Dialog Nový projekt s vybranou konzolovou aplikací](./media/with-visual-studio/visual-studio-new-project.png)

1. Visual Studio používá šablonu k vytvoření projektu. Šablona C# konzolové aplikace pro .NET Core automaticky definuje třídu `Program`s jedinou metodou `Main`, která přijímá <xref:System.String> pole jako argument. `Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .

   ![Visual Studio a nový HelloWorld projekt](./media/with-visual-studio/visual-studio-main-window.png)

   Šablona vytvoří jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello World!" v okně konzoly. Výběrem tlačítka **HelloWorld** se zelenou šipkou na panelu nástrojů můžete spustit program v režimu ladění. V takovém případě je okno konzoly viditelné pouze v krátkém časovém intervalu před jeho zavřením. K tomu dochází, `Main` protože metoda končí a aplikace končí, jakmile se `Main` v metodě spustí jediný příkaz.

1. Chcete-li způsobit pozastavení aplikace před zavřením okna konzoly, přidejte následující kód hned za volání <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   Tento kód vyzve uživatele, aby stiskne libovolný klíč, a pak program pozastaví, dokud nestiskne klávesu.

1. Na řádku nabídek vyberte **sestavení** > **sestavení**. Tím se program zkompiluje do mezilehlého jazyka (IL), který je převeden do binárního kódu pomocí kompilátoru JIT (just-in-time).

1. Spusťte program tak, že vyberete tlačítko **HelloWorld** se zelenou šipkou na panelu nástrojů.

   ![Okno konzoly zobrazující Hello World pro pokračování stiskněte libovolnou klávesu](./media/with-visual-studio/hello-world-console.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

## <a name="enhancing-the-hello-world-application"></a>Vylepšení aplikace Hello World

Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem. Chcete-li program upravit a otestovat, postupujte následovně:

1. V okně kódu C# zadejte následující kód hned za levou závorku, která následuje `static void Main(string[] args)` po řádku a před první pravou závorkou:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Tento kód nahrazuje obsah `Main` metody.

   ![Visual Studio program c-ostrý soubor s aktualizovanou hlavní metodou](./media/with-visual-studio/visual-csharp-code-window.png)

   Tento kód zobrazí "" Jaké je vaše jméno? " v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER. Tento řetězec je uložen do proměnné s názvem `name`. Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date`. Nakonec používá [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) k zobrazení těchto hodnot v okně konzoly.

1. Zkompilujte program tím, že kliknete na **sestavit** > sestavení**řešení**.

1. Spusťte program v režimu ladění v sadě Visual Studio tak, že vyberete zelenou šipku na panelu nástrojů, stisknete klávesu F5 nebo > kliknete na položku nabídky**Spustit ladění** ladění. Zadáním názvu a stisknutím klávesy ENTER odpovězte na výzvu.

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

Aplikaci jste vytvořili a spustili. Pro vývoj profesionální aplikace proveďte několik dalších kroků, aby vaše aplikace byla připravena k vydání:

- Informace o ladění aplikace naleznete v tématu [ladění aplikace Hello World .NET Core pomocí sady Visual Studio 2017](debugging-with-visual-studio.md).

- Informace o vývoji a publikování Distribuovatelný verze aplikace naleznete v tématu [publikování aplikace Hello World .NET Core pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Související témata

Namísto konzolové aplikace můžete také vytvořit knihovnu tříd pomocí .NET Core a sady Visual Studio 2017. Podrobný Úvod naleznete [v tématu sestavování knihovny tříd pomocí C# a .NET Core v aplikaci Visual Studio 2017](library-with-visual-studio.md).

Konzolovou aplikaci .NET Core můžete také vyvíjet v systému Mac, Linux a Windows pomocí [Visual Studio Code](https://code.visualstudio.com/), editoru kódu ke stažení. Podrobný kurz najdete v tématu [Začínáme s Visual Studio Code](with-visual-studio-code.md).
