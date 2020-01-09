---
title: Vytvoření aplikace Hello World pomocí .NET Core v aplikaci Visual Studio
description: Naučte se, jak vytvořit svou první konzolovou aplikaci C# .NET Core pomocí nebo Visual Basic pomocí sady Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714002"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Kurz: Vytvoření první konzolové aplikace .NET Core v aplikaci Visual Studio 2019

Tento článek popisuje podrobný Úvod k vytvoření a spuštění Hello World konzolové aplikace .NET Core v aplikaci Visual Studio 2019. Aplikace Hello World se tradičně používá k zavedení začátečníků do nového programovacího jazyka. Tento program jednoduše zobrazí frázi "Hello World!" .

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019 verze 16,4 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** . Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.

Další informace najdete v části [instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku [instalace .NET Core SDK](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Vytvoření aplikace

V následujících pokynech je vytvořená jednoduchá Hello World Konzolová aplikace:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Otevřete Visual Studio 2019.

1. Vytvořte nový C# projekt konzolové aplikace .NET Core s názvem HelloWorld.

   1. V okně Start vyberte možnost **vytvořit nový projekt**.

      ![Tlačítko vytvořit nový projekt vybráno v okně Start sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **Console** . Dále zvolte **C#** ze seznamu jazyk a v seznamu platforma zvolte možnost **všechny platformy** . Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.

      ![Vytvoří nové okno projektu s vybranými filtry.](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Pokud nevidíte šablony .NET Core, pravděpodobně nemáte nainstalovanou požadovanou úlohu. V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Otevře se Instalační program pro Visual Studio. Ujistěte se, že máte nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** . Pak zvolte **vytvořit**.

      ![Konfigurovat nové okno projektu s názvem projektu, umístěním a poli s názvem řešení](./media/with-visual-studio/configure-new-project.png)

   Šablona C# konzolové aplikace pro .NET Core automaticky definuje třídu `Program`s jedinou metodou, `Main`, která přebírá <xref:System.String> pole jako argument. `Main` je vstupní bod aplikace, metoda, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .

   ![Visual Studio a nový HelloWorld projekt](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Otevřete Visual Studio 2019.

1. Vytvořte nový Visual Basic projekt konzolové aplikace .NET Core s názvem "HelloWorld".

   1. V okně Start vyberte možnost **vytvořit nový projekt**.

      ![Tlačítko vytvořit nový projekt vybráno v okně Start sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **Console** . Dále v seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **všechny platformy** . Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.

      ![Zvolit šablonu Visual Basic pro konzolovou aplikaci (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Pokud nevidíte šablony .NET Core, pravděpodobně nemáte nainstalovanou požadovanou úlohu. V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Otevře se Instalační program pro Visual Studio. Ujistěte se, že máte nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** . Pak zvolte **vytvořit**.

   Šablona konzolové aplikace pro .NET Core automaticky definuje třídu `Program`s jedinou metodou, `Main`, která přebírá <xref:System.String> pole jako argument. `Main` je vstupní bod aplikace, metoda, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v parametru `args`.

   ![Visual Studio a nový HelloWorld projekt](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Šablona vytvoří jednoduchou aplikaci "Hello World". Volá metodu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pro zobrazení řetězcového literálu "Hello World!". v okně konzoly.

## <a name="run-the-app"></a>Spuštění aplikace

1. Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.

   ![Panel nástrojů sady Visual Studio s vybraným tlačítkem spustit v HelloWorld](./media/with-visual-studio/run-program.png)

   Otevře se okno konzoly s textem "Hello World!". vytištěno na obrazovce a některé informace o ladění sady Visual Studio.

   ![Okno konzoly zobrazující Hello World pro pokračování stiskněte libovolnou klávesu](./media/with-visual-studio/hello-world-console.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

## <a name="enhance-the-app"></a>Vylepšení aplikace

Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem. Následující pokyny upravují a spouštějí aplikaci znovu:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Nahraďte obsah metody `Main`, která je aktuálně pouze řádek, který volá `Console.WriteLine`, s následujícím kódem:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Tento kód zobrazí "" Jaké je vaše jméno? " v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER. Tento řetězec je uložen do proměnné s názvem `name`. Načte také hodnotu vlastnosti <xref:System.DateTime.Now?displayProperty=nameWithType>, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date`. Nakonec používá [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) k zobrazení těchto hodnot v okně konzoly.

1. Zkompilujte program výběrem možnosti **sestavit** > **Sestavit řešení**.

1. Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.

1. Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Nahraďte obsah metody `Main`, která je aktuálně pouze řádek, který volá `Console.WriteLine`, s následujícím kódem:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Tento kód zobrazí "" Jaké je vaše jméno? " v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER. Tento řetězec je uložen do proměnné s názvem `name`. Načte také hodnotu vlastnosti <xref:System.DateTime.Now?displayProperty=nameWithType>, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date`. Nakonec používá [interpolované řetězce](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) k zobrazení těchto hodnot v okně konzoly.

1. Zkompilujte program výběrem možnosti **sestavit** > **Sestavit řešení**.

1. Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.

1. Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

---

## <a name="next-steps"></a>Další kroky

V tomto článku jste vytvořili a spustili svou první aplikaci .NET Core. V dalším kroku budete ladit aplikaci.

> [!div class="nextstepaction"]
> [Ladění aplikace Hello World .NET Core v aplikaci Visual Studio](debugging-with-visual-studio.md)
