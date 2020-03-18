---
title: Vytvoření aplikace Hello World s rozhraním .NET Core v sadě Visual Studio
description: Zjistěte, jak vytvořit první aplikaci konzoly .NET Core pomocí jazyka C# nebo Visual Basic pomocí sady Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714002"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Kurz: Vytvoření první aplikace konzoly .NET Core ve Visual Studiu 2019

Tento článek obsahuje podrobný úvod k vytvoření a spuštění aplikace konzoly Hello World .NET Core v sadě Visual Studio 2019. Aplikace Hello World se tradičně používá k zavedení začátečníků do nového programovacího jazyka. Tento program jednoduše zobrazuje frázi "Hello World!" .

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019 verze 16.4 nebo novější verze](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou **úlohou pro vývoj napříč platformami .NET Core.** Sada .NET Core 3.1 SDK se automaticky nainstaluje, když vyberete tuto úlohu.

Další informace naleznete v části [Instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku Instalace [jádra .NET SDK.](../install/sdk.md?pivots=os-windows)

## <a name="create-the-app"></a>Vytvoření aplikace

Následující pokyny vytvořit jednoduchou aplikaci Hello World konzoly:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Otevřete Visual Studio 2019.

1. Vytvořte nový projekt konzoly C# .NET Core s názvem "HelloWorld".

   1. V počátečním okně zvolte **Vytvořit nový projekt**.

      ![Vytvoření nového tlačítka projektu vybraného v počátečním okně sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stránce **Vytvořit nový projekt** zadejte **konzolu** do vyhledávacího pole. Dále zvolte **C#** ze seznamu jazyk a pak zvolte **všechny platformy** ze seznamu Platform. Zvolte šablonu **Konzola aplikace (.NET Core)** a pak zvolte **Další**.

      ![Vytvoření nového okna projektu s vybranými filtry](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Pokud nevidíte šablony .NET Core, pravděpodobně vám chybí nainstalované požadované zatížení. V části **Install more tools and features** **Nenajít to, co hledáte?** Otevře se instalační program sady Visual Studio. Ujistěte se, že máte nainstalovanou **úlohu pro vývoj napříč platformami .NET Core.**

   1. Na stránce **Konfigurace nového projektu** zadejte **HelloWorld** do pole **Název projektu.** Potom zvolte **Vytvořit**.

      ![Konfigurace nového okna projektu s poli Název projektu, umístění a název řešení](./media/with-visual-studio/configure-new-project.png)

   Šablona aplikace konzoly Jazyka C# pro .NET Core automaticky definuje třídu , `Program`s jedinou metodou , `Main`která bere <xref:System.String> pole jako argument. `Main`je vstupní bod aplikace, metoda, která je volána automaticky runtime při spuštění aplikace. Všechny argumenty příkazového řádku zadané při spuštění aplikace jsou k dispozici v poli *args.*

   ![Visual Studio a nový projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Otevřete Visual Studio 2019.

1. Vytvořte nový projekt konzoly Jazyka .NET Core s názvem "HelloWorld".

   1. V počátečním okně zvolte **Vytvořit nový projekt**.

      ![Vytvoření nového tlačítka projektu vybraného v počátečním okně sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stránce **Vytvořit nový projekt** zadejte **konzolu** do vyhledávacího pole. Dále zvolte **Visual Basic** ze seznamu Jazyk a pak ze seznamu Platforma zvolte **Všechny platformy.** Zvolte šablonu **Konzola aplikace (.NET Core)** a pak zvolte **Další**.

      ![Volba šablony jazyka Visual Basic pro konzolovou aplikaci (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Pokud nevidíte šablony .NET Core, pravděpodobně vám chybí nainstalované požadované zatížení. V části **Install more tools and features** **Nenajít to, co hledáte?** Otevře se instalační program sady Visual Studio. Ujistěte se, že máte nainstalovanou **úlohu pro vývoj napříč platformami .NET Core.**

   1. Na stránce **Konfigurace nového projektu** zadejte **HelloWorld** do pole **Název projektu.** Potom zvolte **Vytvořit**.

   Šablona konzolové aplikace pro rozhraní .NET `Program`Core automaticky definuje `Main`třídu <xref:System.String> , pomocí jediné metody , která bere pole jako argument. `Main`je vstupní bod aplikace, metoda, která je volána automaticky runtime při spuštění aplikace. Všechny argumenty příkazového řádku zadané při spuštění `args` aplikace jsou k dispozici v parametru.

   ![Visual Studio a nový projekt HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Šablona vytvoří jednoduchou aplikaci "Hello World". Volá metodu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pro zobrazení literálu řetězec "Hello World!" v okně konzoly.

## <a name="run-the-app"></a>Spuštění aplikace

1. Chcete-li program spustit, zvolte **helloworld** na panelu nástrojů nebo stiskněte **klávesu F5**.

   ![Panel nástrojů Sady Visual Studio s vybraným tlačítkem Spustit HelloWorld](./media/with-visual-studio/run-program.png)

   Otevře se okno konzoly s textem "Hello World!" vytištěny na obrazovce a některé informace o ladění sady Visual Studio.

   ![Okno konzoly zobrazující Hello World Stisknutím libovolné klávesy pokračujte](./media/with-visual-studio/hello-world-console.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

## <a name="enhance-the-app"></a>Vylepšete aplikaci

Vylepšete svou aplikaci tak, aby se uživateli vyzývala k zadání jeho jména a zobrazila ji spolu s datem a časem. Následující pokyny upravte a spusťte aplikaci znovu:

# <a name="c"></a>[C #](#tab/csharp)

1. Nahraďte obsah `Main` metody, která je aktuálně pouze `Console.WriteLine`řádek, který volá , s následujícím kódem:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Tento kód zobrazuje "Jaké je vaše jméno?" v okně konzoly a čeká, až uživatel zadá řetězec následovaný klávesou Enter. Ukládá tento řetězec do `name`proměnné s názvem . Také načte hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji proměnné s názvem `date`. Nakonec používá [interpolovaný řetězec](../../csharp/language-reference/tokens/interpolated.md) k zobrazení těchto hodnot v okně konzoly.

1. Zkompilujte program výběrem **možnosti Sestavení** > **sestavení řešení**.

1. Chcete-li program spustit, zvolte **helloworld** na panelu nástrojů nebo stiskněte **klávesu F5**.

1. Na výzvu odpovíte zadáním názvu a stisknutím klávesy **Enter.**

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Nahraďte obsah `Main` metody, která je aktuálně pouze `Console.WriteLine`řádek, který volá , s následujícím kódem:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Tento kód zobrazuje "Jaké je vaše jméno?" v okně konzoly a čeká, až uživatel zadá řetězec následovaný klávesou Enter. Ukládá tento řetězec do `name`proměnné s názvem . Také načte hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji proměnné s názvem `date`. Nakonec používá [interpolovaný řetězec](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) k zobrazení těchto hodnot v okně konzoly.

1. Zkompilujte program výběrem **možnosti Sestavení** > **sestavení řešení**.

1. Chcete-li program spustit, zvolte **helloworld** na panelu nástrojů nebo stiskněte **klávesu F5**.

1. Na výzvu odpovíte zadáním názvu a stisknutím klávesy **Enter.**

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

---

## <a name="next-steps"></a>Další kroky

V tomto článku jste vytvořili a spusťte první aplikaci .NET Core. V dalším kroku ladíte aplikaci.

> [!div class="nextstepaction"]
> [Ladění aplikace .NET Core Hello World v sadě Visual Studio](debugging-with-visual-studio.md)
