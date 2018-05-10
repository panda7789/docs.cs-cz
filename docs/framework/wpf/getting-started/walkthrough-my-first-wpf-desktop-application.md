---
title: Vytvoření aplikace WPF v sadě Visual Studio
ms.date: 04/12/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ceb4d79bb88e41e62f3ee136b6beb3324b3dbd7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Návod: Můj první grafický subsystém WPF aplikace pracovní plochy

V tomto článku se dozvíte, jak vyvíjet jednoduchou aplikaci Windows Presentation Foundation (WPF), která obsahuje prvky, které jsou společné pro většinu grafického subsystému WPF aplikací: kód rozšiřitelné aplikace Markup Language (XAML), kódu, definice aplikace ovládací prvky, rozložení, datové vazby a stylů.

Tento názorný postup obsahuje následující kroky:

- Pomocí XAML můžete navrhnout vzhled aplikace uživatelské rozhraní (UI).

- Napište kód pro sestavení chování aplikace.

- Vytvořte definici aplikace ke správě aplikace.

- Přidání ovládacích prvků a vytvořte rozložení k vytvoření aplikace uživatelského rozhraní.

- Vytvořte styly konzistentní vzhled uživatelského rozhraní aplikace.

- Vytvoření vazby uživatelského rozhraní k datům pro naplnění rozhraní z dat i zachovat data a uživatelského rozhraní, které jsou synchronizovány.

Na konci průvodce budete mít vytvořené samostatné aplikace Windows, která umožňuje uživatelům zobrazit sestavy výdajů pro vybrané osoby. Aplikace se skládá z několika grafického subsystému WPF stránek, které jsou hostované v okně prohlížeče stylu.

> [!TIP]
> Ukázkový kód, který je použit k vytvoření tohoto návodu je k dispozici pro Visual Basic a C# na [Úvod do vytváření grafického subsystému WPF aplikací](http://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2012 nebo novější

Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalaci sady Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Vytvořte projekt aplikace

Prvním krokem je vytvoření infrastrukturu aplikace, která zahrnuje definice aplikace, dvě stránky a bitovou kopii.

1. Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem **ExpenseIt –**:

   1. Otevřete Visual Studio a vyberte **soubor** > **nový** > **projektu**.

      **Nový projekt** otevře se dialogové okno.

   2. V části **nainstalovaná** kategorie, rozbalte **Visual C#** nebo **jazyka Visual Basic** uzel a potom vyberte **Windows Classic Desktop**.

   3. Vyberte **aplikace WPF (rozhraní .NET Framework)** šablony. Zadejte název **ExpenseIt –** a pak vyberte **OK**.

      ![Dialogové okno Nový projekt s vybrané aplikaci WPF](media/new-project-dialog.png)

      Visual Studio vytvoří projekt a otevře designer pro výchozím okně aplikace s názvem **MainWindow.xaml**.

   > [!NOTE]
   > Tento návod používá <xref:System.Windows.Controls.DataGrid> ovládací prvek, který je k dispozici v rozhraní .NET Framework 4 a novější. Být jisti, že cílem vašeho projektu je .NET Framework 4 nebo novější. Další informace najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Otevřete *Application.xaml* (Visual Basic) nebo *App.xaml* (C#).

    Tento soubor XAML definuje aplikace WPF a všechny prostředky aplikace. Tento soubor můžete taky použít k určení rozhraní, které se automaticky zobrazí při spuštění aplikace; v takovém případě *MainWindow.xaml*.

    Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Nebo podobně jako v C#:

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otevřete *MainWindow.xaml*.

    Tento soubor XAML hlavní okno vaší aplikace a zobrazí obsah vytvořený v stránky. <xref:System.Windows.Window> Třídy definuje vlastnosti časového období, například jeho název, velikost nebo ikonu a zpracovává události, například zavření nebo skrytí.

4. Změna <xref:System.Windows.Window> elementu, který chcete <xref:System.Windows.Navigation.NavigationWindow>, jak je znázorněno v následujícím XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Tato aplikace přejde na jiný obsah, v závislosti na vstup uživatele. To je důvod, proč hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> dědí všechny vlastnosti <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Element v souboru XAML vytvoří instanci <xref:System.Windows.Navigation.NavigationWindow> třídy. Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Změnit na následující vlastnosti <xref:System.Windows.Navigation.NavigationWindow> element:

    - Nastavte <xref:System.Windows.Window.Title%2A> vlastnost ExpenseIt "–".

    - Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na 500 pixelů.

    - Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost 350 pixelů.

    - Odeberte <xref:System.Windows.Controls.Grid> prvky mezi <xref:System.Windows.Navigation.NavigationWindow> značky.

    Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Nebo podobně jako v C#:

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Otevřete *MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.

    Tento soubor je soubor kódu, který obsahuje kód pro zpracování události deklarované v *MainWindow.xaml*. Tento soubor obsahuje konkrétní třídu pro okno definované v jazyce XAML.

7. Pokud používáte C#, změňte `MainWindow` odvozena od třídy <xref:System.Windows.Navigation.NavigationWindow>. (V jazyce Visual Basic tomu automaticky dojde při změně okna v jazyce XAML.)

   Váš kód by měl vypadat takto:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > Můžete přepínat jazyk kódu ukázkový kód mezi C# a Visual Basic v **jazyk** rozevíracího seznamu v pravé horní části tohoto článku.

## <a name="add-files-to-the-application"></a>Přidání souborů do aplikace

V této části přidáte dvě stránky a bitovou kopii do aplikace.

1. Do projektu přidejte novou stránku WPF a pojmenujte ji *ExpenseItHome.xaml*:

   1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ExpenseIt –** uzel projektu a zvolte **přidat** > **stránky**.

   1. V **přidat novou položku** dialogové okno, **stránky (WPF)** šablony je již vybrána. Zadejte název **ExpenseItHome**a potom vyberte **přidat**.

    Tato stránka je první stránka, která se zobrazí, když je aplikace spuštěna. Zobrazí seznam uživatelů a vyberte, chcete-li zobrazit sestavu výdajů pro.

2. Otevřete *ExpenseItHome.xaml*.

3. Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - domovské".

    Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Nebo to v jazyce C#:

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Otevřete *MainWindow.xaml*.

5. Nastavte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> na "ExpenseItHome.xaml".

    Nastaví tato *ExpenseItHome.xaml* na první stránce otevřelo při spuštění aplikace. Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Nebo to v jazyce C#:

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Můžete také nastavit **zdroj** vlastnost **různé** kategorii **vlastnosti** okno.
   >
   > ![Zdrojová vlastnost ve vlastnosti – okno](media/properties-source.png)

6. Do projektu přidejte další novou stránku grafického subsystému WPF a pojmenujte ji *ExpenseReportPage.xaml*::

   1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ExpenseIt –** uzel projektu a zvolte **přidat** > **stránky**.

   1. V **přidat novou položku** dialogové okno, **stránky (WPF)** šablony je již vybrána. Zadejte název **ExpenseReportPage**a potom vyberte **přidat**.

    Tato stránka se zobrazí vyúčtování pro osobě, která je vybrána na **ExpenseItHome** stránky.

7. Otevřete *ExpenseReportPage.xaml*.

8. Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - zobrazení výdajů".

    Vaše XAML by měl vypadat přibližně takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Nebo to v jazyce C#:

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Otevřete *ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*, nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.

    Když vytvoříte nový soubor stránky, Visual Studio automaticky vytvoří *kódu* souboru. Tyto soubory kódu zpracování logiky reagovat na vstup uživatele.

    Váš kód by měl vypadat takto pro **ExpenseItHome**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    A takto pro **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Přidání image s názvem *watermark.png* do projektu. Můžete vytvořit vlastní image, zkopírujte soubor z ukázkového kódu nebo jim [zde](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **existující položka**, nebo stiskněte klávesu **Shift**+**Alt** + **A**.

   2. V **přidat existující položku** dialogové okno, přejděte k souboru bitové kopie, kterou chcete použít a potom vyberte **přidat**.

## <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

1. Sestavení a spuštění aplikace, stiskněte klávesu **F5** nebo vyberte **spustit ladění** z **ladění** nabídky.

    Následující obrázek znázorňuje aplikace s <xref:System.Windows.Navigation.NavigationWindow> tlačítka:

    ![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Zavřete aplikaci se vraťte do sady Visual Studio.

## <a name="create-the-layout"></a>Vytvoření rozložení

Rozložení poskytuje seřazené způsob, jak umístit prvky uživatelského rozhraní a také spravuje velikost a umístění těchto elementů při změně velikosti uživatelského rozhraní. Obvykle vytvoříte rozložení s jedním z následujících rozložení ovládacích prvků:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Každý z těchto prvků rozložení podporuje zvláštním typem rozložení pro její podřízené elementy. Stránky ExpenseIt – jde změnit, a každé stránce má prvky, které jsou uspořádány vodorovně a svisle u jiných prvků. V důsledku toho <xref:System.Windows.Controls.Grid> je ideální rozložení elementu pro danou aplikaci.

> [!TIP]
> Další informace o <xref:System.Windows.Controls.Panel> elementy, najdete v části [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md). Další informace o rozložení najdete v tématu [rozložení](../../../../docs/framework/wpf/advanced/layout.md).

V části vytvoříte tabulku s jedním sloupcem s tři řádky a okraj 10 pixelů přidáním sloupce a řádku definice, které <xref:System.Windows.Controls.Grid> v *ExpenseItHome.xaml*.

1. Otevřete *ExpenseItHome.xaml*.

2. Nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> element "10,0,10,10", který odpovídá na levé straně, horní, pravé a dolní okraj:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Můžete také nastavit **okraj** hodnoty ve **vlastnosti** okno, v části **rozložení** kategorie:
   >
   > ![Okraj hodnoty vlastnosti – okno](media/properties-margin.png)

3. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značek k vytvoření definice řádků a sloupců:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> Dvou řádků je nastaven na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že se velikost řádky založit na obsah v řádcích. Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> nastavení velikosti, což znamená, že výška řádku je vyvážené podíl volné místo. Například pokud mají dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> z "*", každá má výška, který je polovinu dostupné místo.

    Vaše <xref:System.Windows.Controls.Grid> by teď měl vypadat jako následující XAML:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Přidání ovládacích prvků

V této části aktualizujete domovské stránce uživatelského rozhraní, zobrazí se seznam osob, které může uživatel vybrat z zobrazíte vyúčtování pro. Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům interakci s vaší aplikací. Další informace najdete v tématu [ovládací prvky](../../../../docs/framework/wpf/controls/index.md).

Pokud chcete vytvořit toto uživatelské rozhraní, přidáte následující elementy pro *ExpenseItHome.xaml*:

- <xref:System.Windows.Controls.ListBox> (pro seznam lidí, kteří).
- <xref:System.Windows.Controls.Label> (pro hlavičku seznamu).
- <xref:System.Windows.Controls.Button> (Chcete-li kliknutím zobrazíte vyúčtování osoby, který je vybraný v seznamu).

Každý ovládací prvek je umístěn v řádek <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost. Další informace o přidružené vlastnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Otevřete *ExpenseItHome.xaml*.

2. Přidejte následující XAML někde mezi <xref:System.Windows.Controls.Grid> značky:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Můžete také vytvořit ovládací prvky je přetáhnete z **sada nástrojů** okna do okna návrhu a pak nastavování jejich vlastností **vlastnosti** okno.

3. Sestavte a spusťte aplikaci.

Následující obrázek znázorňuje ovládací prvky, že kterou jste právě vytvořili:

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Přidejte bitovou kopii a název

V této části aktualizujete uživatelském rozhraní domovské stránky s bitovou kopii a název stránky.

1. Otevřete *ExpenseItHome.xaml*.

2. Přidejte jiný sloupec pro <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevným <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Přidat další řádek, abyste <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, celkem čtyři řádky:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Přesunout ovládacích prvků na druhý sloupec nastavením <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost na hodnotu 1 v každé tři ovládacích prvků (ohraničení, ListBox a tlačítko).

5. Přesunout dolů řádek, každý ovládací prvek zvyšování jeho <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> hodnoty 1.

   XAML pro ovládací prvky, tři nyní vypadat třeba takto:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Nastavte <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> jako *watermark.png* soubor obrázku, přidáním následující XAML někde mezi `<Grid>` a `<\/Grid>` značky:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Před <xref:System.Windows.Controls.Border> elementu, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazení vyúčtování". Toto je název stránky.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Sestavte a spusťte aplikaci.

Následující obrázek znázorňuje, co jste právě přidali výsledky:

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Přidat kód pro zpracování událostí

1. Otevřete *ExpenseItHome.xaml*.

2. Přidat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události <xref:System.Windows.Controls.Button> elementu. Další informace najdete v tématu [postupy: vytvoření jednoduché události obslužná rutina](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Otevřete *ExpenseItHome.xaml.vb* nebo *ExpenseItHome.xaml.cs*.

4. Přidejte následující kód, který `ExpenseItHome` třída pro přidání tlačítka klikněte na obslužnou rutinu události. Obslužné rutiny události otevře **ExpenseReportPage** stránky.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Vytvoření uživatelského rozhraní pro ExpenseReportPage

*ExpenseReportPage.xaml* zobrazí vyúčtování pro osobě, která je vybrána na **ExpenseItHome** stránky. V této části budete ovládací prvky a vytvoření uživatelského rozhraní pro **ExpenseReportPage**. Budete také přidat pozadí a barvy k různým elementům uživatelského rozhraní výplně.

1. Otevřete *ExpenseReportPage.xaml*.

2. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Toto uživatelské rozhraní je podobná *ExpenseItHome.xaml*, s výjimkou v se zobrazí data sestavy <xref:System.Windows.Controls.DataGrid>.

3. Sestavte a spusťte aplikaci.

    > [!NOTE]
    > Pokud dojde k chybě <xref:System.Windows.Controls.DataGrid> nebyl nalezen nebo neexistuje, ujistěte se, že cílem vašeho projektu je .NET Framework 4 nebo novější. Další informace najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Vyberte **zobrazení** tlačítko.

    Zobrazí se stránka sestavy výdajů. Všimněte si také, zda je povoleno back navigační tlačítko.

Následující obrázek znázorňuje prvky uživatelského rozhraní, které jsou přidány do *ExpenseReportPage.xaml*.

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Ovládací prvky stylu

Vzhled různé prvky mezi sebou, je často stejný pro všechny elementy stejného typu v uživatelského rozhraní. Uživatelské rozhraní používá [styly](../../../../docs/framework/wpf/controls/styling-and-templating.md) aby vzhledy opakovaně použitelné napříč více elementů. – Opětovné použití stylů pomáhá zjednodušit XAML vytváření a správu. Tato část nahradí za element atributy, které byly definovány v předchozích krocích se styly.

1. Otevřete *Application.xaml* nebo *App.xaml*.

2. Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Tato XAML přidá následující styly:

    - `headerTextStyle`: Chcete-li formát názvu stránky <xref:System.Windows.Controls.Label>.

    - `labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládací prvky.

    - `columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládací prvky.

    - `listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na ExpenseItHome.xaml.

    Všimněte si, že stylů jsou prostředky a podřízené objekty <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti. V tomto umístění stylů platí pro všechny elementy v aplikaci. Příklad používání prostředků ve aplikace rozhraní .NET Framework, naleznete v části [prostředky aplikace použijte](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Otevřete *ExpenseItHome.xaml*.

4. Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> které definují, jak vypadá každý ovládací prvek se odeberou a nahrazuje použití stylů. Například `headerTextStyle` se použije pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>.

5. Otevřete *ExpenseReportPage.xaml*.

6. Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Tento postup přidá stylů pro <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy.

## <a name="bind-data-to-a-control"></a>Vázání dat k ovládacímu prvku

V této části vytvoříte data XML, který je vázaný na různé ovládací prvky.

1. Otevřete *ExpenseItHome.xaml*.

2. Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML pro vytvoření <xref:System.Windows.Data.XmlDataProvider> obsahující data pro každou osobu:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Data je vytvořen jako <xref:System.Windows.Controls.Grid> prostředků. Obvykle to by načíst jako soubor, ale pro zjednodušení je přidat data vložené.

3. V rámci `<Grid.Resources>` elementu, přidejte následující <xref:System.Windows.DataTemplate>, který definuje, jak zobrazit data v <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Další informace o šablonách dat najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Nahradit existující <xref:System.Windows.Controls.ListBox> s následující XAML:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Tato XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Připojení dat k ovládacím prvkům

Dále přidáte kód načíst název, který je vybrán na **ExpenseItHome** stránky a předejte ji do konstruktoru **ExpenseReportPage**. **ExpenseReportPage** nastaví jeho kontext dat s předaný položky, které je co ovládací prvky určené ve *ExpenseReportPage.xaml* vytvořit vazbu.

1. Otevřete *ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.

2. Přidejte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů vybrané osoby.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otevřete *ExpenseItHome.xaml.vb* nebo *ExpenseItHome.xaml.cs*.

4. Změna <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události pro volání konstruktoru new předávání dat sestavy výdajů vybrané osoby.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Styl dat pomocí šablony dat

V této části aktualizujete uživatelského rozhraní pro každou položku v seznamech vázané na data pomocí šablon data.

1. Otevřete *ExpenseReportPage.xaml*.

2. Vytvoření vazby obsah "Název" a "Oddělení" <xref:System.Windows.Controls.Label> vlastnost zdroje elementy, aby příslušná data. Další informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující data šablon, které definují způsob, jak zobrazit data sestavy výdajů:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Používat šablony pro <xref:System.Windows.Controls.DataGrid> sloupce, které zobrazují nákladů data sestavy.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Sestavte a spusťte aplikaci.

6. Vyberte osoby a pak vyberte **zobrazení** tlačítko.

Následující obrázek znázorňuje obě stránky ExpenseIt – aplikace s ovládací prvky, rozložení, styly, vazby dat a dat šablony použít:

![Snímky obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Tato ukázka ukazuje konkrétní funkce WPF a nemá použijte všechny osvědčené postupy pro takové věci, jako zabezpečení, lokalizace a usnadnění přístupu. Úplný přehled WPF a osvědčené postupy vývoj aplikací rozhraní .NET Framework najdete v následujících tématech:
>
> - [Usnadnění](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Zabezpečení](../../../../docs/framework/wpf/security-wpf.md)
>
> - [WPF globalizace a lokalizace](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [Výkon WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Další kroky

V tomto návodu jste se dozvěděli počet techniky pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF). Teď byste měli mít základní znalosti o stavební bloky vázané na data, aplikace rozhraní .NET Framework. Další informace o modelech WPF architektura a programování najdete v následujících tématech:

- [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)

Další informace o vytváření aplikací najdete v následujících tématech:

- [Vývoj aplikací](../../../../docs/framework/wpf/app-development/index.md)
- [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)
- [Přehled vazba dat](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>Viz také

- [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Ukázka dat – přehled](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Vytvoření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styles-and-templates.md)
