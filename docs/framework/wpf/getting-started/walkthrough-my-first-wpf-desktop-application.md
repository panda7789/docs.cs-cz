---
title: Vytvoření aplikace WPF v sadě Visual Studio
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: c3440ddf6cdae6b24bcf1059ab2c76d8fb957263
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003853"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Návod: Moje první desktopová aplikace WPF

V tomto článku se dozvíte, jak vyvíjet desktopové aplikace Windows Presentation Foundation (WPF), která obsahuje elementy, které jsou společné pro většinu aplikací WPF: Extensible Application Markup Language (XAML) značky, použití modelu code-behind, definice aplikací, ovládací prvky, rozložení, datové vazby a styly. K vývoji aplikace, používáte sadu Visual Studio. 

Tento návod zahrnuje následující kroky:

- Umožňuje navrhnout vzhled uživatelského rozhraní (UI) pro aplikace XAML.

- Napsání kódu pro sestavení chování aplikace.

- Vytvořte definici aplikace ke správě aplikace.

- Přidání ovládacích prvků a vytvořit rozložení k vytvoření uživatelského rozhraní aplikace.

- Vytvoření styly pro konzistentní vzhled uživatelského rozhraní aplikace.

- Připojení k datům, k naplnění uživatelského rozhraní z dat a vaše data uživatelského rozhraní a synchronizovány uživatelského rozhraní.

Na konci návodu budete sestavíte samostatnou aplikaci Windows, která umožňuje uživatelům zobrazit vyúčtování pro vybraného uživatele. Aplikace se skládá z několika stránek WPF, které jsou hostované v okně prohlížeče – vizuální styl.

> [!TIP]
> Ukázkový kód, který se používá k vytvoření tohoto návodu je k dispozici i v jazyce Visual Basic a C# na [ukázkového kódu aplikace WPF návod](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Můžete přepínat na jazyk kódu ukázek kódu mezi C# a Visual Basic pomocí **\< />** rozevíracího seznamu v horní pravé části tohoto článku.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější (Tento článek používá Visual Studio 2019)

   Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Vytvoření projektu aplikace

Prvním krokem je vytvoření aplikační infrastruktury, který obsahuje definici aplikace, dvě stránky a bitovou kopii.

1. Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem **`ExpenseIt`**:

   1. Otevřít Visual Studio a vyberte **vytvořte nový projekt** pod **Začínáme** nabídky.

      **Vytvořte nový projekt** otevře se dialogové okno.

   2. V **jazyk** rozevírací seznam, vyberte buď **C#** nebo **jazyka Visual Basic**.
      
   3. Vyberte **aplikace WPF (.NET Framework)** šablonu a pak vyberte **Další**. 
     
      ![Vytvořit dialogové okno nového projektu](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      **Konfigurovat nový projekt** otevře se dialogové okno.

   4. Zadejte název projektu **`ExpenseIt`** a pak vyberte **vytvořit**.

      ![Konfigurace dialogové okno nového projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio vytvoří projekt a otevře se návrhář pro výchozí okno aplikace s názvem **souboru MainWindow.xaml**.

2. Otevřít *Application.xaml* (Visual Basic) nebo *App.xaml* (C#).

    Tento soubor XAML definuje aplikace WPF a všechny prostředky, aplikace. Tento soubor k zadání uživatelského rozhraní, v tomto případě použijete také *souboru MainWindow.xaml*, která automaticky zobrazí při spuštění aplikace.

    Vaše XAML by měl vypadat nějak takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    A stejně jako v následující C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otevřít *souboru MainWindow.xaml*.

    Tento soubor XAML je hlavní okno aplikace a zobrazí obsah vytvořený na stránkách. <xref:System.Windows.Window> Třídy definuje vlastnosti okna, například jeho název, velikost nebo ikonu a zpracovává události, jako je například zavření nebo skrytí.

4. Změnit <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>, jak je znázorněno v následující XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele. To je důvod, proč hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> zdědí všechny vlastnosti <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Vytvoří instanci prvku v souboru XAML <xref:System.Windows.Navigation.NavigationWindow> třídy. Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).

5. Odeberte <xref:System.Windows.Controls.Grid> prvky z mezi <xref:System.Windows.Navigation.NavigationWindow> značky.

6. Změňte následující vlastnosti v kódu XAML <xref:System.Windows.Navigation.NavigationWindow> element:

    - Nastavte <xref:System.Windows.Window.Title%2A> vlastnost "`ExpenseIt`".

    - Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost na 350 pixelů.

    - Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na šířku 500 pixelů.

    Vaše XAML by měl vypadat nějak takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    A podobně jako následující C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Otevřít *soubor MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.

    Tento soubor je soubor kódu na pozadí, který obsahuje kód pro zpracování události deklarované v *souboru MainWindow.xaml*. Tento soubor obsahuje částečné třídy pro okno definované v XAML.

8. Pokud používáte C#, změnit `MainWindow` třídy odvozovat z <xref:System.Windows.Navigation.NavigationWindow>. (V jazyce Visual Basic, tomu automaticky dojde při změně okna v XAML.) Vaše C# kódu by teď měl vypadat takto:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Přidání souborů do aplikace

V této části přidáte dvě stránky a obrázku do aplikace.

1. Přidejte novou stránku do projektu a pojmenujte ho *`ExpenseItHome.xaml`*:

   1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.

   1. V **přidat novou položku** dialogového okna, **stránky (WPF)** šablony je už vybraná. Zadejte název **`ExpenseItHome`** a pak vyberte **přidat**.

    Tato stránka je první stránka, která se zobrazí při spuštění aplikace. Zobrazí seznam uživatelů vyberte, chcete-li zobrazit sestavy výdajů pro.

1. Otevřít *`ExpenseItHome.xaml`*.

1. Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - Home`".

1. Nastavte `DesignHeight` a `DesignWidth` hodnoty prvku na 300 pixelů.

    XAML se teď zobrazí následujícím způsobem v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    A podobně jako následující C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Otevřít *souboru MainWindow.xaml*.

1. Přidat <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> elementu a nastavte ho na "`ExpenseItHome.xaml`".

    Tím se nastaví *`ExpenseItHome.xaml`* bude první stránka otevře při spuštění aplikace. 

    Příklad XAML v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    A v jazyce C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Můžete také nastavit **zdroj** vlastnost **různé** kategorii **vlastnosti** okna.
   >
   > ![Source – vlastnost v okně Vlastnosti](./media/properties-source.png)

1. Do projektu přidejte další novou stránku WPF a pojmenujte ho *ExpenseReportPage.xaml*::

   1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.

   1. V **přidat novou položku** dialogového okna, vyberte **stránky (WPF)** šablony. Zadejte název **ExpenseReportPage**a pak vyberte **přidat**.

    Na této stránce se zobrazí vyúčtování pro osoby, která je vybrán na **`ExpenseItHome`** stránky.

1. Otevřít *ExpenseReportPage.xaml*.

1. Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - View Expense`".

1. Nastavte `DesignHeight` a `DesignWidth` hodnoty prvku na 300 pixelů.

    *ExpenseReportPage.xaml* teď vypadá podobně jako následující v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    A stejně jako v následující C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Otevřít *ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*, nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.

    Když vytvoříte nový soubor stránky, sada Visual Studio automaticky vytvoří jeho *použití modelu code-behind* souboru. Tyto soubory použití modelu code-behind zpracování logiky reagovat na vstup uživatele.

    Váš kód by měl vypadat jako následující **`ExpenseItHome`**:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    A podobně jako následující **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Přidání obrázku s názvem *watermark.png* do projektu. Můžete vytvořit vlastní image, zkopírujte soubor ve vzorku kódu nebo získat [tady](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).

    1. Klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **existující položku**, nebo stiskněte klávesu **Shift**+**Alt** + **A**.

    2. V **přidat existující položku** dialogové okno, nastavte filtr souboru buď **všechny soubory** nebo **soubory bitových kopií**, přejděte k souboru bitové kopie, kterou chcete použít a potom vyberte **přidat** .

## <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

1. Chcete-li sestavit a spustit aplikaci, stiskněte **F5** nebo vyberte **spustit ladění** z **ladění** nabídky.

    Následující obrázek znázorňuje aplikaci <xref:System.Windows.Navigation.NavigationWindow> tlačítka:

    ![Aplikace po sestavení a spustíme ji.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Ukončete aplikaci se vraťte do sady Visual Studio.

## <a name="create-the-layout"></a>Vytvořit rozložení

Rozložení poskytuje seřazený umožňuje umístit prvky uživatelského rozhraní a také spravuje velikost a umístění těchto prvků při změně velikosti uživatelského rozhraní. Rozložení se obvykle vytvoříte pomocí jednoho z následujících ovládacích prvků rozložení:

- <xref:System.Windows.Controls.Canvas> -Vymezuje oblast, ve kterém můžete explicitně umísťovat podřízené prvky použitím souřadnic, které jsou relativní k oblasti plátna.
- <xref:System.Windows.Controls.DockPanel> -Vymezuje oblast, ve kterém můžete uspořádat podřízené elementy vodorovně nebo svisle, relativně vůči sobě navzájem.
- <xref:System.Windows.Controls.Grid> -Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.
- <xref:System.Windows.Controls.StackPanel> -Uspořádává podřízené prvky do jednoho řádku, který může být orientovaný vodorovně nebo svisle.
- <xref:System.Windows.Controls.VirtualizingStackPanel> -Uspořádá a Virtualizuje obsah na jednom řádku, který je orientovaný buď vodorovně nebo svisle.
- <xref:System.Windows.Controls.WrapPanel> -Umísťuje podřízené prvky do sekvenční Pozice zleva doprava, zásadní obsahu na další řádek na okraji obsahujícího pole. Následné řazení se děje sekvenčně shora dolů nebo zprava doleva v závislosti na hodnotě vlastnosti Orientation.

Každá z těchto ovládacích prvků rozložení podporuje konkrétního typu rozložení pro jeho podřízené prvky. `ExpenseIt` změnit velikost stránky, a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle dalších prvků. V tomto příkladu <xref:System.Windows.Controls.Grid> slouží jako prvek rozložení pro aplikaci.

> [!TIP]
> Další informace o <xref:System.Windows.Controls.Panel> prvky, naleznete v tématu [přehled panelů](../controls/panels-overview.md). Další informace o rozložení najdete v tématu [rozložení](../advanced/layout.md).

V této části vytvoříte tabulku s jedním sloupcem se třemi řádky a 10 pixel okraj přidáním řádků a sloupců definice <xref:System.Windows.Controls.Grid> v *`ExpenseItHome.xaml`*.

1. V *`ExpenseItHome.xaml`*, nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> prvku "10,0,10,10", která odpovídá na levé straně, horní, pravé a dolní okraj:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Můžete také nastavit **okraj** hodnoty v **vlastnosti** okně v části **rozložení** kategorie:
   >
   > ![Hodnoty vlastnosti okraj v okně Vlastnosti](./media/properties-margin.png)

2. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky vytvářet definice řádků a sloupců:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> Dva řádky se nastaví na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že je nastavena velikost řádků na základě obsahu v řádcích. Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> velikosti, což znamená, že vážený poměr volného místa výšku řádku. Například pokud máte dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> z "*", každý z nich výška polovinu dostupné místo.

    Vaše <xref:System.Windows.Controls.Grid> by měl nyní obsahovat následující XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Přidání ovládacích prvků

V této části budete aktualizovat na domovské stránce uživatelského rozhraní, zobrazí se seznam lidí, kde vyberete jedna osoba zobrazíte jejich vyúčtování. Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům, aby komunikovali s vaší aplikací. Další informace najdete v tématu [ovládací prvky](../controls/index.md).

K vytvoření tohoto uživatelského rozhraní, přidejte následující prvky, které mají *`ExpenseItHome.xaml`*:

- A <xref:System.Windows.Controls.ListBox> (pro seznam lidí, kteří).
- A <xref:System.Windows.Controls.Label> (pro hlavičku seznamu).
- A <xref:System.Windows.Controls.Button> (Chcete-li kliknutím zobrazíte vyúčtování pro osobu, která je v seznamu vyberete).

Každý ovládací prvek nachází v řádku <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost. Další informace o přidružené vlastnosti najdete v tématu [přehled připojených vlastností](../advanced/attached-properties-overview.md).

1. V *`ExpenseItHome.xaml`*, přidejte následující XAML někde mezi <xref:System.Windows.Controls.Grid> značky:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Ovládací prvky můžete vytvořit také z jejich přetažením **nástrojů** okna do okna návrhu a nastavte jejich vlastnosti **vlastnosti** okna.

2. Sestavte a spusťte aplikaci.

    Následující obrázek znázorňuje ovládací prvky, že kterou jste vytvořili:

![Snímek obrazovky ukázkové ExpenseIt – zobrazuje seznam názvů](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Přidat obrázek a název

V této části budete aktualizovat Uživatelském rozhraní domovské stránky s bitovou kopii a název stránky.

1. V *`ExpenseItHome.xaml`*, přidejte jiný sloupec <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevnou <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Přidat další řádek <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, celkem čtyři řádky:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Přesuňte ovládací prvky na druhý sloupec tak, že nastavíte <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost na hodnotu 1 v každé tři ovládací prvky (hranice ListBox a tlačítko).

4. Každý ovládací prvek dolů řádek zvýšením jeho <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> hodnotu 1 pro všechny tři ovládací prvky (hranice ListBox a tlačítko) a ohraničení prvku.

   XAML pro tři ovládací prvky nyní vypadá takto:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Nastavte <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> vlastnost *watermark.png* soubor obrázku, přidáním následující XAML kdekoli mezi `<Grid>` a `</Grid>` značky:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Před <xref:System.Windows.Controls.Border> prvku, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazení vyúčtování". Tento popisek je název stránky.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Sestavte a spusťte aplikaci.

Následující obrázek ukazuje výsledky co jste právě přidali:

![ExpenseIt – ukázka snímek obrazovky ukazující nový obrázek na pozadí a nadpis stránky](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Přidejte kód pro zpracování událostí

1. V *`ExpenseItHome.xaml`*, přidejte <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události <xref:System.Windows.Controls.Button> elementu. Další informace najdete v tématu [jak: Vytvořte obslužnou rutinu události jednoduché](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.

3. Přidejte následující kód, který `ExpenseItHome` třídy přidejte tlačítko klikněte na obslužnou rutinu události. Obslužná rutina události otevře **ExpenseReportPage** stránky.

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Vytvoření uživatelského rozhraní pro ExpenseReportPage

*ExpenseReportPage.xaml* zobrazí vyúčtování pro osobu, která je vybrán na **`ExpenseItHome`** stránky. V této části vytvoříte uživatelské rozhraní pro **ExpenseReportPage**. Budete také přidat na pozadí a vyplnit barev pro různé elementy uživatelského rozhraní.

1. Otevřít *ExpenseReportPage.xaml*.

2. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Toto uživatelské rozhraní je podobný *`ExpenseItHome.xaml`*, s výjimkou data sestavy se zobrazí v <xref:System.Windows.Controls.DataGrid>.

3. Sestavte a spusťte aplikaci.

4. Vyberte **zobrazení** tlačítko.

    Zobrazí se stránka sestavy výdajů. Všimněte si také, zda je povoleno tlačítko zpětné navigace.

Následující obrázek znázorňuje prvky uživatelského rozhraní, které jsou přidány do *ExpenseReportPage.xaml*.

![ExpenseIt – ukázka snímek obrazovky uživatelského rozhraní pro ExpenseReportPage právě vytvořili.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Ovládací prvky stylu

Vzhled různé prvky je často stejný pro všechny prvky v uživatelském rozhraní stejného typu. Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) k zajištění vzhled opakovaně použitelné napříč více prvků. Opětovné použití stylů pomáhá zjednodušit XAML vytváření a správu. Tato část nahradí atributy na element, definované v předchozích krocích se styly.

1. Otevřít *Application.xaml* nebo *App.xaml*.

2. Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Tento XAML přidá následující styly:

    - `headerTextStyle`: Formátování názvu stránky <xref:System.Windows.Controls.Label>.

    - `labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládacích prvků.

    - `columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládacích prvků.

    - `listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.

    Všimněte si, že se styly prostředky a podřízené objekty daného <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti. V tomto umístění se styly použijí na všechny prvky v aplikaci. Příklad použití prostředků v aplikaci .NET, naleznete v tématu [využití prostředků aplikace](../advanced/how-to-use-application-resources.md).

3. V *`ExpenseItHome.xaml`*, nahradit všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> , které definují vzhled každého ovládacího prvku odebrán a nahrazen o aplikování stylů. Například `headerTextStyle` platí pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>.

4. Otevřít *ExpenseReportPage.xaml*.

5. Nahradit vše mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Styly přidá tento XAML <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy.

6. Sestavte a spusťte aplikaci. Vzhled okno je stejný jako dříve.

    ![Snímek obrazovky ukázkové ExpenseIt – s vzhled stejné jako v předchozí části.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Ukončete aplikaci se vraťte do sady Visual Studio.

## <a name="bind-data-to-a-control"></a>Vytvoření vazby dat k ovládacímu prvku

V této části vytvoříte data XML, který je vázán na různé ovládací prvky.

1. V *`ExpenseItHome.xaml`*, po zahájení <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML vytvořit <xref:System.Windows.Data.XmlDataProvider> , která pro každou osobu, která obsahuje data:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Data se vytvoří jako <xref:System.Windows.Controls.Grid> prostředků. Normálně by tato data načíst jako soubor, ale pro zjednodušení se přidat data vložené.

2. V rámci `<Grid.Resources>` element, přidejte následující `<xref:System.Windows.DataTemplate>` element, který určuje způsob zobrazení dat v <xref:System.Windows.Controls.ListBox>, poté, co `<XmlDataProvider>` element:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Další informace o šablonách dat, naleznete v tématu [přehled datových šablon](../data/data-templating-overview.md).

3. Nahraďte existující <xref:System.Windows.Controls.ListBox> s následující XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Tento XAML naváže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Připojení dat k ovládacím prvkům

V dalším kroku přidáte kód pro načtení název, který je vybrán na **`ExpenseItHome`** stránku a předat konstruktoru **ExpenseReportPage**. **ExpenseReportPage** nastaví jeho kontext dat s předaným položka, která se, co ovládací prvky definované v *ExpenseReportPage.xaml* svázat.

1. Otevřít *ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.

2. Přidáte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů z vybraného uživatele.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.

4. Změnit <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události volaná nový konstruktor předávání dat sestavy výdajů z vybraného uživatele.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Styl dat s využitím šablon dat

V této části budete aktualizovat uživatelské rozhraní pro každou položku v seznamu vázaných na data pomocí šablony.

1. Otevřít *ExpenseReportPage.xaml*.

2. Vytvoření vazby obsah "Name" a "Oddělení" <xref:System.Windows.Controls.Label> prvků, které se příslušná data source – vlastnost. Další informace o datové vazbě naleznete v tématu [přehled datových vazeb](../data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po zahájení <xref:System.Windows.Controls.Grid> prvku, přidejte následující datové šablony, které definují způsob zobrazení dat sestavy výdajů:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Nahraďte <xref:System.Windows.Controls.DataGridTextColumn> prvky s <xref:System.Windows.Controls.DataGridTemplateColumn> pod <xref:System.Windows.Controls.DataGrid> elementu a použijte šablony k nim.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Sestavte a spusťte aplikaci.

6. Vybrat osobu a pak vyberte **zobrazení** tlačítko.

Následující obrázek ukazuje obě stránky `ExpenseIt` aplikace s ovládacími prvky, rozložení, styly, vazby dat a použitých šablon dat:

![Obě stránky aplikace zobrazuje seznam názvů a sestavy výdajů.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Tato ukázka předvádí konkrétní funkce WPF a nebude použijte všechny osvědčené postupy pro takové věci, jako je zabezpečení, lokalizace a přístupnost. Komplexní pokrytí WPF a osvědčené postupy vývoje aplikací .NET najdete v následujících tématech:
>
> - [Usnadnění](../../ui-automation/accessibility-best-practices.md)
>
> - [Zabezpečení](../security-wpf.md)
>
> - [WPF globalizace a lokalizace](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [Výkonu WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Další kroky

V tomto návodu jste zjistili několik technik pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF). Nyní byste měli mít základní znalosti o stavební kameny nástroje aplikace .NET vázané na data. Další informace o WPF architekturu a programovací modely naleznete v následujících tématech:

- [Architektura WPF](../advanced/wpf-architecture.md)
- [Přehled XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md)
- [Rozložení](../advanced/layout.md)

Další informace o vytváření aplikací naleznete v následujících tématech:

- [Vývoj aplikací](../app-development/index.md)
- [Ovládací prvky](../controls/index.md)
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Grafika a multimédia](../graphics-multimedia/index.md)
- [Dokumenty v platformě WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Viz také:

- [Přehled panelů](../controls/panels-overview.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Sestavení aplikace WPF](../app-development/building-a-wpf-application-wpf.md)
- [Styly a šablony](../controls/styles-and-templates.md)
