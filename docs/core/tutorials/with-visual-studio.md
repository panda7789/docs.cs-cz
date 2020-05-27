---
title: Vytvoření konzolové aplikace pomocí .NET Core v aplikaci Visual Studio
description: Naučte se, jak vytvořit konzolovou aplikaci .NET Core pomocí jazyka C# nebo Visual Basic pomocí sady Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7dcd7957a9a160b3caf2692e9888c70a838bffc5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005021"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>Kurz: Vytvoření konzolové aplikace .NET Core v aplikaci Visual Studio 2019

V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core v aplikaci Visual Studio 2019.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019 verze 16,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** . Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.

  Další informace najdete v části [instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku [instalace .NET Core SDK](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Vytvoření aplikace

<!-- markdownlint-disable MD025 -->

1. Otevřete Visual Studio 2019.

1. Vytvořte nový projekt konzolové aplikace .NET Core s názvem HelloWorld.

   1. Na úvodní stránce vyberte možnost **vytvořit nový projekt**.

      ![Tlačítko vytvořit nový projekt vybráno na úvodní stránce sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **Console** . Dále v seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem. Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.

      ![Vytvoří nové okno projektu s vybranými filtry.](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Pokud nevidíte šablony .NET Core, pravděpodobně nebudete mít k dispozici požadované úlohy. V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Otevře se Instalační program pro Visual Studio. Ujistěte se, že máte nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** . Potom zvolte **Create** (Vytvořit).

      ![Konfigurovat nové okno projektu s názvem projektu, umístěním a poli s názvem řešení](./media/with-visual-studio/configure-new-project.png)

   Šablona konzolové aplikace pro .NET Core definuje třídu `Program` s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument. `Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace. Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .

   Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.

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

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   Šablona vytvoří jednoduchou aplikaci "Hello World". Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!" v okně konzoly.

## <a name="run-the-app"></a>Spuštění aplikace

1. Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.

   ![Panel nástrojů sady Visual Studio s vybraným tlačítkem spustit v HelloWorld](./media/with-visual-studio/run-program.png)

   Otevře se okno konzoly s textem "Hello World!". vytištěno na obrazovce a některé informace o ladění sady Visual Studio.

   ![Okno konzoly zobrazující Hello World pro pokračování stiskněte libovolnou klávesu](./media/with-visual-studio/hello-world-console.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

## <a name="enhance-the-app"></a>Vylepšení aplikace

Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem. Následující pokyny upraví aplikaci a znovu ji spusťte:

1. Nahraďte obsah `Main` metody, která je aktuálně pouze řádek, který volá `Console.WriteLine` , s následujícím kódem:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   Tento kód zobrazí "" Jaké je vaše jméno? " v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER. Tento řetězec je uložen v proměnné s názvem `name` . Načte také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` ( `currentDate` v Visual Basic). Nakonec tyto hodnoty zobrazí v okně konzoly.

   `\n`( `vbCrLf` V Visual Basic) představuje znak nového řádku.

   Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných. Hodnota výrazu je vložena do řetězce místo výrazu. Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).

1. Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.

1. Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili aplikaci .NET Core. V dalším kurzu ladění aplikace.

> [!div class="nextstepaction"]
> [Ladění konzolové aplikace .NET Core v aplikaci Visual Studio](debugging-with-visual-studio.md)
