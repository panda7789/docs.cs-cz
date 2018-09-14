---
title: Vytvoření aplikace Hello World pomocí .NET Core a C# v sadě Visual Studio 2017
description: Zjistěte, jak vytvořit jednoduchou konzolovou aplikaci .NET Core pomocí jazyka C# pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet
ms.openlocfilehash: 031c0a433391fbe4cdd40f6ce648f476787baf48
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594351"
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Vytvořte si aplikaci C# Hello World pomocí .NET Core v sadě Visual Studio 2017

Toto téma obsahuje podrobný Úvod k vytváření, ladění a publikování jednoduchou konzolovou aplikaci .NET Core pomocí jazyka C# v sadě Visual Studio 2017. Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro sestavování aplikací .NET Core. Za předpokladu, aplikace nemá závislosti pro konkrétní platformu, aplikaci můžete spustit na libovolné platformě, který cílí na .NET Core a na jakémkoli počítači, který má nainstalovaný .NET Core.

## <a name="prerequisites"></a>Požadavky

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované. Můžete vyvíjet aplikace s využitím .NET Core 1.1 nebo .NET Core 2.0.

Další informace najdete v tématu [předpoklady pro .NET Core ve Windows](../../core/windows-prerequisites.md) tématu.

## <a name="a-simple-hello-world-application"></a>Jednoduchou aplikaci Hello World

Začněte vytvořením jednoduché konzolové aplikace "Hello World". Postupujte podle těchto kroků:

1. Spusťte Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V *nový projekt** dialogového okna, vyberte **Visual C#** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textové pole, zadejte "Hello World". Vyberte **OK** tlačítko.

   ![Dialogové okno nového projektu s vybraná aplikace konzoly](./media/with-visual-studio/newproject.png)
   
1. Visual Studio používá šablony k vytvoření projektu. Šablona konzolové aplikace jazyka C# pro .NET Core automaticky definuje třídu, `Program`, s jedinou metodu, `Main`, která přijímá <xref:System.String> pole jako argument. `Main` je vstupní bod aplikace metodu, která je automaticky volána modulem runtime při spuštění aplikace. Jsou k dispozici v jakékoli argumenty příkazového řádku při spuštění aplikace *args* pole.

   ![Visual Studio a nový projekt Hello World](./media/with-visual-studio/devenv.png)

   Šablona vytvoří jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcový literál "Hello World!" v okně konzoly. Výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů můžete spustit program v režimu ladění. Pokud tak učiníte, v okně konzoly je viditelná pro jenom stručný časový interval předtím, než se toto okno zavře. K tomu dochází, `Main` metoda se ukončí a ukončení aplikace co nejdříve jeden příkaz v `Main` metody.

1. Aby v aplikaci k pozastavení před zavřením okna konzoly, přidejte následující kód bezprostředně po volání <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Tento kód zobrazí výzvu k stisknutím libovolné klávesy a potom program pozastaví, dokud se stiskne klávesa.

1. Na panelu nabídek vyberte **sestavení** > **sestavit řešení**. Tento program zkompiluje do intermediate language (IL), která se převádí do binárního kódu, kompilátor just-in-time (JIT).

1. Spusťte program tak, že vyberete **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů.

   ![Okna konzoly zobrazuje Hello World stisknutím libovolné klávesy pokračovat](./media/with-visual-studio/helloworld1.png)

1. Stisknutím jakékoli klávesy zavřete okno konzoly.

## <a name="enhancing-the-hello-world-application"></a>Vylepšení aplikace Hello World

Vylepšete vaše aplikace výzva k zadání názvu a zobrazit je spolu se datum a čas. Upravit a otestujte aplikaci, postupujte takto:

1. Zadejte následující kód jazyka C# v okně kódu ihned po levá hranatá závorka, která následuje `static void Main(string[] args)` řádku a před první uzavírací závorku:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Tento kód nahradí stávající <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, a <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> příkazy.

   ![Visual Studio programu jazyka c sharp soubor s aktualizovanou metodu Main](./media/with-visual-studio/codewindow.png)

   Tento kód zobrazí "Jaký je název vašeho?" v okně konzoly a počká, dokud uživatel zadá řetězec, za nímž následuje klávesu Enter. Ukládají se tento řetězec do proměnné s názvem `name`. Také načte hodnota <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost, která obsahuje aktuálním místním časem a přiřadí ji k proměnné s názvem `date`. Nakonec se používá [interpolovaný řetězec](../../csharp/language-reference/tokens/interpolated.md) k zobrazení tyto hodnoty v okně konzoly.

1. Kompilovat program výběrem **sestavení** > **sestavit řešení**.

1. Spusťte program v režimu ladění v sadě Visual Studio vyberte zelenou šipku na panelu nástrojů, stisknutím klávesy F5 nebo výběrem položky **ladění** > **spustit ladění** položky nabídky. Na výzvy odpovíte zadáním názvu a stisknutím klávesy Enter.

   ![Okno konzoly s výstupem upravené programu](./media/with-visual-studio/helloworld2.png)

1. Stisknutím jakékoli klávesy zavřete okno konzoly.

Jste vytvořili a spustili aplikaci. K vývoji profesionální aplikace, proveďte některé další kroky pro zajištění připraven k vydání aplikace:

- Informace o ladění vaší aplikace najdete v tématu [ladění jazyka C# aplikace Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md).

- Informace o vývoji a publikování distribuovatelná verze vaší aplikace najdete v tématu [publikování C# aplikace Hello World pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Související témata

Místo konzolovou aplikaci můžete také vytvořit knihovnu tříd s .NET Core a Visual Studio 2017. Podrobný úvod naleznete zde [vytvoření knihovny tříd pomocí jazyka C# a .NET Core v sadě Visual Studio 2017](library-with-visual-studio.md).

Můžete také vyvíjet konzolovou aplikaci .NET Core na Mac, Linux a Windows s použitím [Visual Studio Code](https://code.visualstudio.com/), editor kódu ke stažení. Podrobný návod najdete v části [Začínáme se službou Visual Studio Code](with-visual-studio-code.md).
