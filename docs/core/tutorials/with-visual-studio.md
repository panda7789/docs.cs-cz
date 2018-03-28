---
title: Vytvoření aplikace Hello World s .NET Core a C# v Visual Studio 2017
description: Naučte se vytvářet jednoduché konzolové aplikace .NET Core pomocí C# s použitím Visual Studio 2017.
keywords: .NET core, aplikace konzoly .NET Core, Visual Studio 2017
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
ms.workload:
- dotnetcore
ms.openlocfilehash: 7042a7356fa1b65f7a152208dbfaa9ba27081a8d
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Sestavení C# Hello, World aplikace s .NET Core v Visual Studio 2017

Toto téma obsahuje podrobné Úvod do vytváření, ladění a publikování pomocí jazyka C# v aplikaci Visual Studio 2017 jednoduché aplikace konzoly .NET Core. Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vytváření aplikací .NET Core. Tak dlouho, dokud aplikace nemá závislosti specifické pro platformu, aplikace můžete spustit na jakékoli platformě s cílem .NET Core a systému, který má nainstalovaný .NET Core.

## <a name="prerequisites"></a>Požadavky

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) se zatížením "Vývoj pro různé platformy .NET Core" nainstalována. Můžete vyvíjet aplikace s .NET Core 1.1 nebo .NET Core 2.0.

Další informace najdete v tématu [požadavky pro .NET Core v systému Windows](../../core/windows-prerequisites.md) tématu.

## <a name="a-simple-hello-world-application"></a>Jednoduché aplikace Hello World

Začněte tím, že vytvoření jednoduché aplikace konzoly "Hello World". Postupujte podle těchto kroků:

1. Spusťte Visual Studio 2017. Vyberte **soubor** > **nový** > **projektu** z řádku nabídek. V *nový projekt** dialogovém okně, vyberte **Visual C#** následuje uzlu **.NET Core** uzlu. Vyberte **konzolové aplikace (.NET Core)** šablona projektu. V **název** textové pole, zadejte "Hello World". Vyberte **OK** tlačítko.

   ![Dialogové okno Nový projekt s vybrané konzolové aplikace](./media/with-visual-studio/newproject.png)
   
1. Visual Studio používá šablonu pro vytvoření projektu. Šablona konzolovou aplikaci C# pro .NET Core automaticky definuje třídu, `Program`, s jedinou metodu `Main`, které nepřijímá <xref:System.String> pole jako argument. `Main` je vstupní bod aplikace, metoda, která je automaticky volána modulem runtime při jeho spuštění aplikace. Jsou k dispozici v žádných argumentů příkazového řádku zadán při spuštění aplikace *argumentů* pole.

   ![Visual Studio a nový projekt HelloWorld](./media/with-visual-studio/devenv.png)

   Šablona vytvoří jednoduchou aplikaci "Hello World". Zavolá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello, World!" v okně konzoly. Výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů můžete spustit program v režimu ladění. Pokud tak učiníte, v okně konzoly je viditelná pouze stručný časový interval před toto okno zavře. K tomu dochází, protože `Main` metoda ukončí a co nejdříve jeden příkaz v ukončení aplikace `Main` metody.

1. Aby aplikace pozastavit předtím, než toto okno zavře okno konzoly, přidejte následující kód ihned po volání <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metoda:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Tento kód zobrazí výzvu k stisknutím libovolné klávesy a potom program pozastaví, dokud není stisknuta klíč.

1. Na panelu nabídek vyberte **sestavení** > **sestavit řešení**. To zkompiluje vaším programem do převodní jazyk (IL), který je převést na binární kód kompilátorem v běhu (JIT).

1. Spusťte program výběrem **HelloWorld** tlačítko s zelenou šipku na panelu nástrojů.

   ![Okno konzoly zobrazující Hello World stisknutím libovolné klávesy pokračovat](./media/with-visual-studio/helloworld1.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

## <a name="enhancing-the-hello-world-application"></a>Rozšíření aplikace Hello World

Vylepšení aplikace vyzve uživatele k zadání názvu a zobrazit ji společně s datum a čas. Upravit a otestujte aplikaci, postupujte takto:

1. Zadejte následující kód C# v okně kód ihned po levá hranatá závorka, která následuje `static void Main(string[] args)` řádku a před první pravá závorka:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Tento kód nahradí existující <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, a <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> příkazy.

   ![Visual Studio programu c ostré soubor s aktualizované Main – metoda](./media/with-visual-studio/codewindow.png)

   Tento kód zobrazí "Jaký je název vaší?" v okně konzoly a počká, dokud nebude uživatel zadá řetězec následuje klávesu Enter. Ukládají se tento řetězec do proměnné s názvem `name`. Také načte hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnost, která obsahuje aktuálním místním časem a přiřadí ji k proměnné s názvem `date`. Nakonec se používá [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) k zobrazení těchto hodnot v okně konzoly.

1. Kompilace programu výběrem **sestavení** > **sestavit řešení**.

1. Spusťte program v režimu ladění v sadě Visual Studio vyberete zelenou šipku na panelu nástrojů, Stisknutím F5 nebo výběrem položky **ladění** > **spustit ladění** položku nabídky. Odpověď na výzvu zadáním názvu a stisknutím klávesy Enter.

   ![Okno konzoly výstup je upravený program](./media/with-visual-studio/helloworld2.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

Po vytvoření a spuštění aplikace. K vývoji professional aplikace, proveďte některé další kroky, aby vaše aplikace připravené pro verze:

- Informace o ladění aplikace najdete v tématu [ladění aplikace C# Hello, World s Visual Studio 2017](debugging-with-visual-studio.md).

- Informace o vývoji a publikování distribuovatelného verzi vaší aplikace, najdete v části [publikování aplikace C# Hello, World s Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Související témata

Místo konzolovou aplikaci můžete také vytvořit knihovny tříd s .NET Core a Visual Studio 2017. Krok za krokem úvod naleznete v tématu [vytvoření knihovny tříd s C# a .NET Core ve Visual Studio 2017](library-with-visual-studio.md).

Také můžete vyvíjet aplikace konzoly .NET Core na Mac, Linux a Windows pomocí [Visual Studio Code](https://code.visualstudio.com/), editor ke stažení kódu. Podrobný kurz, najdete v části [Začínáme s Visual Studio Code](with-visual-studio-code.md).
