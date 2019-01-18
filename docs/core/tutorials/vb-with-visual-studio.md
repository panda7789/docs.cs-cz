---
title: .NET core aplikace Hello World v jazyce Visual Basic v sadě Visual Studio 2017
description: Zjistěte, jak vytvořit jednoduchou konzolovou aplikaci .NET Core pomocí sady Visual Basic pomocí sady Visual Studio 2017.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: de7a423bb3e9a288d17c86e9e0afc3b00f6fd80b
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362259"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Vytvořit aplikaci Hello World jazyka Visual Basic pomocí .NET Core SDK v sadě Visual Studio 2017

Toto téma obsahuje podrobný Úvod k vytváření, ladění a publikování jednoduchou konzolovou aplikaci .NET Core pomocí jazyka Visual Basic v sadě Visual Studio 2017. Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro sestavování aplikací .NET Core. Za předpokladu, aplikace nemá závislosti pro konkrétní platformu, aplikaci můžete spustit na libovolné platformě, který cílí na .NET Core a na jakémkoli počítači, který má nainstalovaný .NET Core.

## <a name="prerequisites"></a>Požadavky

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) s úlohou "Vývoj pro různé platformy .NET Core" nainstalované. Můžete vyvíjet aplikace s využitím .NET Core 2.0.

Další informace najdete v tématu [předpoklady pro .NET Core ve Windows](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Jednoduchou aplikaci Hello World

Začněte vytvořením jednoduché konzolové aplikace "Hello World". Postupujte podle těchto kroků:

1. Spusťte Visual Studio 2017. Vyberte **souboru** > **nový** > **projektu** z řádku nabídek. V *nový projekt** dialogového okna, vyberte **jazyka Visual Basic** uzel, za nímž následuje **.NET Core** uzlu. Vyberte **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textové pole, zadejte "Hello World". Vyberte tlačítko **OK**.

   ![Dialogové okno nového projektu s vybraná aplikace konzoly](./media/vb-with-visual-studio/visual-studio-new-project.png)
   
1. Visual Studio používá šablony k vytvoření projektu. Šablona konzolové aplikace jazyka Visual Basic pro .NET Core automaticky definuje třídu, `Program`, s jedinou metodu, `Main`, která přijímá <xref:System.String> pole jako argument. `Main` je vstupní bod aplikace metodu, která je automaticky volána modulem runtime při spuštění aplikace. Jsou k dispozici v jakékoli argumenty příkazového řádku při spuštění aplikace *args* pole.

   ![Visual Studio a nový projekt Hello World](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Šablona vytvoří jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcový literál "Hello World!" v okně konzoly. Výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů můžete spustit program v režimu ladění. Pokud tak učiníte, v okně konzoly je viditelná pro jenom stručný časový interval předtím, než se toto okno zavře. K tomu dochází, `Main` metoda se ukončí a ukončení aplikace co nejdříve jeden příkaz v `Main` metody.

1. Aby v aplikaci k pozastavení před zavřením okna konzoly, přidejte následující kód bezprostředně po volání <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Tento kód zobrazí výzvu k stisknutím libovolné klávesy a potom program pozastaví, dokud se stiskne klávesa.

1. Na panelu nabídek vyberte **sestavení** > **sestavit řešení**. Tento program zkompiluje do intermediate language (IL), která se převádí do binárního kódu, kompilátor just-in-time (JIT).

1. Spusťte program tak, že vyberete **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů.

   ![Okna konzoly zobrazuje Hello World stisknutím libovolné klávesy pokračovat](./media/with-visual-studio/hello-world-console.png)

1. Stisknutím jakékoli klávesy zavřete okno konzoly.

## <a name="enhancing-the-hello-world-application"></a>Vylepšení aplikace Hello World

Vylepšete vaše aplikace vyzve uživatele k jeho název a zobrazit společně s datum a čas. Upravit a otestujte aplikaci, postupujte takto:

1. Zadejte následující kód jazyka Visual Basic v okně kódu ihned po levá hranatá závorka, která následuje `Sub Main(args As String())` řádku a před první uzavírací závorku:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Tento kód nahradí stávající <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, a <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> příkazy.

   ![Visual Studio programový soubor s aktualizovanou metodu Main](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Tento kód zobrazí "Jaký je název vašeho?" v okně konzoly a počká, dokud uživatel zadá řetězec, za nímž následuje klávesu Enter. Ukládají se tento řetězec do proměnné s názvem `name`. Také načte hodnota <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost, která obsahuje aktuálním místním časem a přiřadí ji k proměnné s názvem `currentDate`. Nakonec se používá [interpolovaný řetězec](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) k zobrazení tyto hodnoty v okně konzoly.

1. Kompilovat program výběrem **sestavení** > **sestavit řešení**.

1. Spusťte program v režimu ladění v sadě Visual Studio vyberte zelenou šipku na panelu nástrojů, stisknutím klávesy F5 nebo výběrem položky **ladění** > **spustit ladění** položky nabídky. Na výzvy odpovíte zadáním názvu a stisknutím klávesy Enter.

   ![Okno konzoly s výstupem upravené programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím jakékoli klávesy zavřete okno konzoly.

Jste vytvořili a spustili aplikaci. K vývoji profesionální aplikace, proveďte některé další kroky pro zajištění připraven k vydání aplikace:

- Chcete-li ladit aplikaci, najdete v článku [ladit aplikaci .NET Core Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md).

- K publikování distribuovatelná verze aplikace, najdete v článku [publikování aplikace .NET Core Hello World pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
