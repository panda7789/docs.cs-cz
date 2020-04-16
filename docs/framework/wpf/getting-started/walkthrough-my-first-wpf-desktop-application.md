---
title: Vytvoření první aplikace WPF ve Visual Studiu 2019 – rozhraní .NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: facb9ebebd9ce1904886a946277185ac2c2e4bc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463927"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Kurz: Vytvoření první aplikace WPF v Sadě Visual Studio 2019

Tento článek ukazuje, jak vyvinout desktopovou aplikaci WPF (Windows Presentation Foundation), která obsahuje prvky, které jsou společné pro většinu aplikací WPF: značky Xml (XAML) extensible Application Markup Language (XAML), kód na pozadí, definice aplikací, ovládací prvky, rozložení, datové vazby a styly. K vývoji aplikace budete používat Visual Studio.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte projekt WPF.
> - Pomocí XAML navrhnout vzhled uživatelského rozhraní aplikace (UI).
> - Napište kód pro sestavení chování aplikace.
> - Vytvořte definici aplikace pro správu aplikace.
> - Přidejte ovládací prvky a vytvořte rozložení pro vytvoření uživatelského rozhraní aplikace.
> - Vytvořte styly pro konzistentní vzhled v celém ui aplikace.
> - Svázat ui s daty, a to jak k naplnění ui z dat a zachovat data a ui synchronizovány.

Na konci kurzu budete mít vytvořenou samostatnou aplikaci systému Windows, která uživatelům umožňuje zobrazit vyúčtování výdajů pro vybrané uživatele. Aplikace se skládá z několika stránek WPF, které jsou hostovány v okně stylu prohlížeče.

> [!TIP]
> Ukázkový kód, který se používá v tomto kurzu je k dispozici pro visual basic a C# v [kurzu WPF ukázkový kód aplikace](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Jazyk kódu ukázkového kódu mezi jazyky C# a Visual Basic můžete přepnout pomocí voliče jazyka v horní části této stránky.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou **úlohou pro vývoj desktopů .NET.**

   Další informace o instalaci nejnovější verze sady Visual Studio naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Vytvoření projektu aplikace

Prvním krokem je vytvoření aplikační infrastruktury, která zahrnuje definici aplikace, dvě stránky a bitovou kopii.

1. Vytvořte nový projekt aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem **`ExpenseIt`**:

   1. V nabídce **Začínáme** otevřete Visual Studio a vyberte **Vytvořit nový projekt.**

      Otevře se dialogové okno **Vytvořit nový projekt.**

   2. V rozevíracím **souboru Jazyk** vyberte **c#** nebo **visual basic**.

   3. Vyberte šablonu **aplikace WPF (.NET Framework)** a pak vyberte **Další**.

      ![Vytvořit dialogové okno vytvořit nový projekt](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      Otevře se dialogové okno **Konfigurovat nový projekt.**

   4. Zadejte název **`ExpenseIt`** projektu a pak vyberte **Vytvořit**.

      ![Konfigurace dialogového okna nového projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio vytvoří projekt a otevře návrháře pro výchozí okno aplikace s názvem **MainWindow.xaml**.

2. Otevřete *soubor Application.xaml* (Visual Basic) nebo *Soubor App.xaml* (C#).

    Tento soubor XAML definuje aplikaci WPF a všechny prostředky aplikace. Tento soubor můžete také použít k určení uživatelského uživatelského okna, v tomto případě *MainWindow.xaml*, který se automaticky zobrazí při spuštění aplikace.

    XAML by měl vypadat takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    A stejně jako následující v C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otevřete *soubor MainWindow.xaml*.

    Tento soubor XAML je hlavním oknem vaší aplikace a zobrazuje obsah vytvořený na stránkách. Třída <xref:System.Windows.Window> definuje vlastnosti okna, jako je jeho název, velikost nebo ikona, a zpracovává události, jako je například zavření nebo skrytí.

4. Změňte <xref:System.Windows.Window> prvek <xref:System.Windows.Navigation.NavigationWindow>na , jak je znázorněno v následujícím xaml:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele. To je důvod, proč hlavní <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>je třeba změnit na . <xref:System.Windows.Navigation.NavigationWindow>dědí všechny vlastnosti . <xref:System.Windows.Window> Prvek <xref:System.Windows.Navigation.NavigationWindow> v souboru XAML vytvoří <xref:System.Windows.Navigation.NavigationWindow> instanci třídy. Další informace naleznete v tématu [Navigační přehled](../app-development/navigation-overview.md).

5. Odstraňte <xref:System.Windows.Controls.Grid> prvky <xref:System.Windows.Navigation.NavigationWindow> mezi značkami.

6. Změňte následující vlastnosti v kódu <xref:System.Windows.Navigation.NavigationWindow> XAML pro prvek:

    - Nastavte <xref:System.Windows.Window.Title%2A> vlastnost na`ExpenseIt`" ".

    - Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost na 350 pixelů.

    - Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na 500 pixelů.

    XAML by měl vypadat takto pro Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    A stejně jako následující pro C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Otevřete *soubor MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.

    Tento soubor je soubor s kódem na pozadí, který obsahuje kód pro zpracování událostí deklarovaných v *MainWindow.xaml*. Tento soubor obsahuje částečnou třídu pro okno definované v XAML.

8. Pokud používáte C#, změňte třídu, `MainWindow` která má být odvozena od <xref:System.Windows.Navigation.NavigationWindow>. (V jazyce Visual Basic k tomu dojde automaticky při změně okna v XAML.) Kód jazyka C# by nyní měl vypadat takto:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Přidání souborů do aplikace

V této části přidáte do aplikace dvě stránky a obrázek.

1. Přidejte do projektu novou stránku *`ExpenseItHome.xaml`* a pojmenujte ji :

   1. V **Průzkumníku řešení**klikněte **`ExpenseIt`** pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **stránku**.

   1. V dialogovém okně **Přidat novou položku** je šablona **Stránka (WPF)** již vybraná. Zadejte **`ExpenseItHome`** název a pak vyberte **Přidat**.

    Tato stránka je první stránka, která se zobrazí při spuštění aplikace. Zobrazí se seznam osob, ze kterých je třeba vybrat, pro které se zobrazí vyúčtování výdajů.

1. Otevřít *`ExpenseItHome.xaml`*.

1. Nastavte <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - Home`" ".

1. Nastavte `DesignHeight` 350 pixelů a `DesignWidth` 500 pixelů.

    XAML se nyní zobrazí takto pro visual basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    A stejně jako následující pro C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Otevřete *soubor MainWindow.xaml*.

1. Přidejte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> do prvku a`ExpenseItHome.xaml`nastavte ji na " ".

    To *`ExpenseItHome.xaml`* nastaví první stránku otevřenou při spuštění aplikace.

    Příklad XAML v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    A v C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Můžete také nastavit **Source** vlastnost v různé **kategorie** okna **Vlastnosti.**
   >
   > ![Zdrojová vlastnost v okně Vlastnosti](./media/properties-source.png)

1. Přidejte do projektu další novou stránku WPF a pojmenujte ji *ExpenseReportPage.xaml*::

   1. V **Průzkumníku řešení**klikněte **`ExpenseIt`** pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **stránku**.

   1. V dialogovém okně **Přidat novou položku** vyberte šablonu **Stránky (WPF).** Zadejte název **ExpenseReportPage**a pak vyberte **Přidat**.

    Na této stránce se zobrazí vyúčtování výdajů **`ExpenseItHome`** pro osobu, která je na stránce vybrána.

1. Otevřete *soubor ExpenseReportPage.xaml*.

1. Nastavte <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - View Expense`" ".

1. Nastavte `DesignHeight` 350 pixelů a `DesignWidth` 500 pixelů.

    *ExpenseReportPage.xaml* teď vypadá takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    A stejně jako následující v C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Otevřete *stránku ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.

    Když vytvoříte nový soubor Stránky, Visual Studio automaticky vytvoří jeho soubor *s kódem na pozadí.* Tyto soubory s kódem na pozadí zpracovávají logiku pro reakci na vstup uživatele.

    Váš kód by měl **`ExpenseItHome`** vypadat takto pro :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    A stejně jako následující pro **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Přidejte do projektu obrázek s názvem *vodoznak.png.* Můžete vytvořit vlastní bitovou kopii, zkopírovat soubor z ukázkového kódu nebo jej získat z úložiště [GitHub microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)

    1. Klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat** > **existující položku**nebo stiskněte **Shift**+**Alt**+**A**.

    2. V dialogovém okně **Přidat existující položku** nastavte filtr souborů na **všechny soubory** nebo **obrazové soubory**, vyhledejte soubor obrazu, který chcete použít, a pak vyberte **Přidat**.

## <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

1. Chcete-li vytvořit a spustit aplikaci, stiskněte **klávesu F5** nebo v yberte **Spustit ladění** z nabídky **Ladění.**

    Následující obrázek znázorňuje <xref:System.Windows.Navigation.NavigationWindow> aplikaci s tlačítky:

    ![Aplikace po sestavení a spuštění.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Zavřete aplikaci a vraťte se do sady Visual Studio.

## <a name="create-the-layout"></a>Vytvoření rozložení

Rozložení poskytuje seřazený způsob umístění prvků uživatelského rozhraní a také spravuje velikost a umístění těchto prvků při změně velikosti uživatelského rozhraní. Obvykle vytvoříte rozložení s jedním z následujících ovládacích prvků rozložení:

- <xref:System.Windows.Controls.Canvas>- Definuje oblast, ve které můžete explicitně umístit podřízené prvky pomocí souřadnic, které jsou vzhledem k oblasti Plátno.
- <xref:System.Windows.Controls.DockPanel>- Definuje oblast, kde můžete uspořádat podřízené prvky buď vodorovně nebo svisle, vzhledem k sobě navzájem.
- <xref:System.Windows.Controls.Grid>- Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.
- <xref:System.Windows.Controls.StackPanel>- Uspořádá podřízené prvky do jedné čáry, která může být orientována vodorovně nebo svisle.
- <xref:System.Windows.Controls.VirtualizingStackPanel>- Uspořádá a virtualizuje obsah na jednom řádku, který je orientován vodorovně nebo svisle.
- <xref:System.Windows.Controls.WrapPanel>- Umístí podřízené prvky v sekvenční poloze zleva doprava, čímž přeruší obsah na další řádek na okraji obsahující krabice. Následné řazení probíhá postupně shora dolů nebo zprava doleva, v závislosti na hodnotě Orientation vlastnost.

Každý z těchto ovládacích prvků rozložení podporuje určitý typ rozložení pro jeho podřízené prvky. `ExpenseIt`stránky lze velikost a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle jiných prvků. V tomto příkladu <xref:System.Windows.Controls.Grid> se používá jako prvek rozložení pro aplikaci.

> [!TIP]
> Další informace <xref:System.Windows.Controls.Panel> o prvcích naleznete v [tématu Přehled panelů](../controls/panels-overview.md). Další informace o rozložení naleznete v [tématu Layout](../advanced/layout.md).

V této části vytvoříte tabulku s jedním sloupcem se třemi řádky a okrajem <xref:System.Windows.Controls.Grid> 10 pixelů přidáním definic sloupců a řádků do v *`ExpenseItHome.xaml`*.

1. V *`ExpenseItHome.xaml`* <xref:System.Windows.FrameworkElement.Margin%2A> nastavíte vlastnost <xref:System.Windows.Controls.Grid> prvku na "10,0,10,10", což odpovídá levému, hornímu, pravému a dolnímu okraji:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Hodnoty **okraje** můžete také nastavit v okně **Vlastnosti** v kategorii **Rozložení:**
   >
   > ![Hodnoty okrajů v okně Vlastnosti](./media/properties-margin.png)

2. Chcete-li vytvořit definice <xref:System.Windows.Controls.Grid> řádků a sloupců, přidejte mezi značky xaml následující:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    Dva <xref:System.Windows.Controls.RowDefinition.Height%2A> řádky je nastavena na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že řádky jsou velikosti na základě obsahu v řádcích. Výchozí <xref:System.Windows.Controls.RowDefinition.Height%2A> hodnota <xref:System.Windows.GridUnitType.Star> je velikost, což znamená, že výška řádku je vážený majem k dispozici. Například pokud dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> každý z "*", každý z nich má výšku, která je polovina dostupného místa.

    Nyní <xref:System.Windows.Controls.Grid> byste měli obsahovat následující XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Přidání ovládacích prvků

V této části aktualizujete ui domovské stránky tak, aby zobrazovalo seznam lidí, kde vyberete jednu osobu, která zobrazí vyúčtování výdajů. Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům pracovat s vaší aplikací. Další informace naleznete v [tématu Controls](../controls/index.md).

Chcete-li vytvořit toto uživatelské rozhraní, *`ExpenseItHome.xaml`* přidáte do aplikace :

- A <xref:System.Windows.Controls.ListBox> (pro seznam lidí).
- A <xref:System.Windows.Controls.Label> (pro záhlaví seznamu).
- A <xref:System.Windows.Controls.Button> (kliknutím zobrazíte vyúčtování výdajů pro osobu, která je vybrána v seznamu).

Každý ovládací prvek je umístěn <xref:System.Windows.Controls.Grid> v <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> řádku nastavením připojené vlastnosti. Další informace o připojených vlastnostech naleznete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).

1. V *`ExpenseItHome.xaml`* aplikace přidejte mezi značky <xref:System.Windows.Controls.Grid> přibližně následující xaml:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Ovládací prvky můžete také vytvořit přetažením z okna **panelu nástrojů** do okna návrhu a potom nastavením jejich vlastností v okně **Vlastnosti.**

2. Sestavte a spusťte aplikaci.

    Následující obrázek znázorňuje ovládací prvky, které jste vytvořili:

![ExpenseIt ukázkový snímek obrazovky se seznamem jmen](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Přidání obrázku a názvu

V této části aktualizujete hlavní nastavení domovské stránky pomocí obrázku a názvu stránky.

1. V *`ExpenseItHome.xaml`*, přidejte <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> další sloupec <xref:System.Windows.Controls.ColumnDefinition.Width%2A> s pevnou 230 pixelů:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. Přidejte další <xref:System.Windows.Controls.Grid.RowDefinitions%2A>řádek do , pro celkem čtyři řádky:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. Přesuňte ovládací prvky do <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> druhého sloupce nastavením vlastnosti na 1 v každém ze tří ovládacích prvků (Border, ListBox a Button).

4. Přesuňte každý ovládací prvek dolů řádek <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> zvýšením jeho hodnotu o 1 pro každý ze tří ovládacích prvků (Border, ListBox a Button) a border element.

   XAML pro tři ovládací prvky nyní vypadá takto:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Nastavte <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> vlastnost na obrazový soubor *vodoznak.png* přidáním následujícího XAML kdekoli mezi `<Grid>` `</Grid>` a tagy:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Před <xref:System.Windows.Controls.Border> prvek přidejte <xref:System.Windows.Controls.Label> a s obsahem "Zobrazit vyúčtování výdajů". Tento popisek je název stránky.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Sestavte a spusťte aplikaci.

Následující obrázek znázorňuje výsledky toho, co jste právě přidali:

![ExpenseIt ukázkový snímek obrazovky s novým pozadím obrázku a názvem stránky](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Přidání kódu pro zpracování událostí

1. V *`ExpenseItHome.xaml`* souboru <xref:System.Windows.Controls.Primitives.ButtonBase.Click> přidejte <xref:System.Windows.Controls.Button> do prvku obslužnou rutinu události. Další informace naleznete v [tématu Postup: Vytvoření jednoduché obslužné rutiny události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Otevřít *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* nebo .

3. Přidejte do třídy následující kód a `ExpenseItHome` přidejte obslužnou rutinu události kliknutí na tlačítko. Obslužná rutina události otevře stránku **ExpenseReportPage.**

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Vytvoření ui pro ExpenseReportPage

*ExpenseReportPage.xaml* zobrazí vyúčtování výdajů pro osobu, **`ExpenseItHome`** která je vybrána na stránce. V této části vytvoříte ui pro **ExpenseReportPage**. Do různých prvků uživatelského rozhraní také přidáte barvy pozadí a výplně.

1. Otevřete *soubor ExpenseReportPage.xaml*.

2. Mezi značky <xref:System.Windows.Controls.Grid> přidejte následující xaml:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Toto ui *`ExpenseItHome.xaml`* je podobné , s výjimkou <xref:System.Windows.Controls.DataGrid>data sestavy je zobrazena v .

3. Sestavte a spusťte aplikaci.

4. Vyberte tlačítko **Zobrazit.**

    Zobrazí se stránka vyúčtování výdajů. Všimněte si také, že je povoleno navigační tlačítko Zpět.

Následující obrázek znázorňuje prvky uživatelského rozhraní přidané do *souboru ExpenseReportPage.xaml*.

![Ukázkový snímek obrazovky zobrazující právě vytvořené rozhraní pro expensereportpage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Ovládací prvky stylu

Vzhled různých prvků je často stejný pro všechny prvky stejného typu v uživatelském rozhraní. Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) k opakovanému použití vzhledu ve více prvcích. Opětovná použitelnost stylů pomáhá zjednodušit vytváření a správu XAML. Tato část nahrazuje atributy za prvek, které byly definovány v předchozích krocích, styly.

1. Otevřete *soubor Application.xaml* nebo *App.xaml*.

2. Mezi značky <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> přidejte následující xaml:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Tento XAML přidává následující styly:

    - `headerTextStyle`: Formátování názvu <xref:System.Windows.Controls.Label>stránky .

    - `labelStyle`: Formátování <xref:System.Windows.Controls.Label> ovládacích prvků.

    - `columnHeaderStyle`: Formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Formátování ovládacích <xref:System.Windows.Controls.Border> prvků záhlaví seznamu.

    - `listHeaderTextStyle`: Formátování záhlaví <xref:System.Windows.Controls.Label>seznamu .

    - `buttonStyle`: Formátování <xref:System.Windows.Controls.Button> zapnuté `ExpenseItHome.xaml`funkce .

    Všimněte si, že styly <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> jsou prostředky a podřízené prvku vlastnosti. V tomto umístění jsou styly použity na všechny prvky v aplikaci. Příklad použití prostředků v aplikaci .NET najdete v tématu [Použití prostředků aplikace](../advanced/how-to-use-application-resources.md).

3. V *`ExpenseItHome.xaml`*, nahradit <xref:System.Windows.Controls.Grid> vše mezi prvky s následujícími XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Vlastnosti, <xref:System.Windows.VerticalAlignment> jako <xref:System.Windows.Media.FontFamily> je například a které definují vzhled každého ovládacího prvku, jsou odebrány a nahrazeny použitím stylů. Například `headerTextStyle` je použita na "Zobrazit <xref:System.Windows.Controls.Label>vyúčtování výdajů" .

4. Otevřete *soubor ExpenseReportPage.xaml*.

5. Nahraďte <xref:System.Windows.Controls.Grid> vše mezi prvky následujícím XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Tento XAML přidává <xref:System.Windows.Controls.Label> styly a <xref:System.Windows.Controls.Border> prvky.

6. Sestavte a spusťte aplikaci. Vzhled okna je stejný jako dříve.

    ![ExpenseIt ukázkový snímek obrazovky se stejným vzhledem jako v poslední části.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Zavřete aplikaci a vraťte se do sady Visual Studio.

## <a name="bind-data-to-a-control"></a>Vazba dat s ovládacím prvkem

V této části vytvoříte data XML, která jsou vázána na různé ovládací prvky.

1. V *`ExpenseItHome.xaml`* aplikaci <xref:System.Windows.Controls.Grid> za otevření elementu přidejte následující <xref:System.Windows.Data.XmlDataProvider> xaml a vytvořte tak, že obsahuje data pro každou osobu:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Data jsou vytvořena <xref:System.Windows.Controls.Grid> jako prostředek. Za normálních okolností by tato data byla načtena jako soubor, ale pro jednoduchost jsou data přidána vložena.

2. V `<Grid.Resources>` rámci prvku přidejte následující `<xref:System.Windows.DataTemplate>` prvek, který definuje, <xref:System.Windows.Controls.ListBox>jak zobrazit `<XmlDataProvider>` data v , za element:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Další informace o šablonách dat naleznete v [tématu Přehled šablon dat](../data/data-templating-overview.md).

3. Nahraďte <xref:System.Windows.Controls.ListBox> existující pomocí následujícího XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Tento XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnosti <xref:System.Windows.Controls.ListBox> zdroje dat a použije šablonu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>dat jako .

## <a name="connect-data-to-controls"></a>Připojení dat k ovládacím prvkům

Dále přidáte kód k načtení názvu, který je **`ExpenseItHome`** vybrán na stránce a předat jej konstruktoru **ExpenseReportPage**. **ExpenseReportPage** nastaví svůj kontext dat s předanou položkou, což je to, co ovládací prvky definované v *ExpenseReportPage.xaml* vázat.

1. Otevřete *soubor ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.

2. Přidejte konstruktor, který převezme objekt, takže můžete předat data vyúčtování výdajů vybrané osoby.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otevřít *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* nebo .

4. Změňte <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události tak, aby volala nového konstruktoru, který předává data vyúčtování výdajů vybrané osoby.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Data stylu se šablonami dat

V této části aktualizujete uživatelské tlačítko pro každou položku v seznamech vázaných na data pomocí šablon dat.

1. Otevřete *soubor ExpenseReportPage.xaml*.

2. Svázat obsah "Název" a "Oddělení" <xref:System.Windows.Controls.Label> prvky příslušné vlastnosti zdroje dat. Další informace o datové vazbě naleznete v [tématu Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Za otevírací <xref:System.Windows.Controls.Grid> prvek přidejte následující šablony dat, které definují, jak zobrazit data vyúčtování výdajů:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Nahraďte <xref:System.Windows.Controls.DataGridTemplateColumn> prvky <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.DataGridTextColumn> pod elementem a aplikujte na ně šablony.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Sestavte a spusťte aplikaci.

6. Vyberte osobu a pak vyberte tlačítko **Zobrazit.**

Následující obrázek znázorňuje `ExpenseIt` obě stránky aplikace s použitými ovládacími prvky, rozložením, styly, datovou vazbou a šablonami dat:

![Obě stránky aplikace zobrazující seznam jmen a vyúčtování výdajů.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Tato ukázka ukazuje konkrétní funkci WPF a nedodržuje všechny osvědčené postupy pro věci, jako je zabezpečení, lokalizace a usnadnění přístupu. Komplexní pokrytí WPF a osvědčených postupů pro vývoj aplikací .NET najdete v následujících tématech:
>
> - [Usnadnění](../../ui-automation/accessibility-best-practices.md)
> - [Zabezpečení](../security-wpf.md)
> - [WPF globalizace a lokalizace](../advanced/wpf-globalization-and-localization-overview.md)
> - [WPF výkon](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Další kroky

V tomto návodu jste se naučili řadu technik pro vytvoření ui pomocí Windows Presentation Foundation (WPF). Nyní byste měli mít základní znalosti o stavebních blocích aplikace .NET vázané na data. Další informace o architektuře WPF a programovacích modelech naleznete v následujících tématech:

- [Architektura WPF](../advanced/wpf-architecture.md)
- [Přehled XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Přehled vlastností závislostí](../advanced/dependency-properties-overview.md)
- [Rozložení](../advanced/layout.md)

Další informace o vytváření aplikací naleznete v následujících tématech:

- [Vývoj aplikací](../app-development/index.md)
- [Ovládací prvky](../controls/index.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Grafika a multimédia](../graphics-multimedia/index.md)
- [Dokumenty v platformě WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Viz také

- [Panely – přehled](../controls/panels-overview.md)
- [Přehled šablon ování dat](../data/data-templating-overview.md)
- [Vytvoření aplikace WPF](../app-development/building-a-wpf-application-wpf.md)
- [Styly a šablony](../controls/styles-and-templates.md)
