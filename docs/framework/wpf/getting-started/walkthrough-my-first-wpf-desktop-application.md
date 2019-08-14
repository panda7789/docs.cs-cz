---
title: Vytvoření aplikace WPF v aplikaci Visual Studio
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
ms.openlocfilehash: 9d5b5b8a479efd3918dc23616aa331cc07a901ac
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972138"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Návod: Moje první desktopová aplikace WPF

V tomto článku se dozvíte, jak vyvíjet desktopovou aplikaci Windows Presentation Foundation (WPF), která obsahuje prvky, které jsou společné pro většinu aplikací WPF: Jazyk Extensible Application Markup Language (XAML) (XAML) značky, kódu na pozadí, definice aplikací, ovládací prvky, rozložení, datové vazby a styly. K vývoji aplikace použijete Visual Studio. 

Tento návod obsahuje následující kroky:

- Použijte XAML pro návrh vzhledu uživatelského rozhraní (UI) aplikace.

- Napíšete kód pro sestavení chování aplikace.

- Vytvořte definici aplikace pro správu aplikace.

- Přidejte ovládací prvky a vytvořte rozložení, abyste mohli vytvořit uživatelské rozhraní aplikace.

- Vytvářejte styly pro konzistentní vzhled v celém uživatelském rozhraní aplikace.

- Navažte uživatelské rozhraní na data a naplňte uživatelské rozhraní z dat a Udržujte data a uživatelské rozhraní synchronizované.

Na konci tohoto návodu budete mít vytvořenou samostatnou aplikaci pro Windows, která uživatelům umožňuje zobrazit sestavy výdajů pro vybrané lidi. Aplikace se skládá z několika stránek WPF, které jsou hostovány v okně ve stylu prohlížeče.

> [!TIP]
> Vzorový kód, který se používá k sestavení tohoto návodu, je k dispozici pro C# Visual Basic i v [podrobném ukázkovém kódu aplikace WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> C# **Pomocí \< rozevíracího seznamu v pravé horní části tohoto článku můžete přepínat jazyk kódu ukázkového kódu mezi a Visual Basic. />**

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější (Tento článek používá Visual Studio 2019)

   Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Vytvoření projektu aplikace

Prvním krokem je vytvoření infrastruktury aplikace, která zahrnuje definici aplikace, dvě stránky a obrázek.

1. Vytvoření nového projektu aplikace WPF v Visual Basic nebo vizuálu C# s názvem **`ExpenseIt`** :

   1. Otevřete Visual Studio a v nabídce Začínáme vyberte **vytvořit nový projekt** .

      Otevře se dialogové okno **vytvořit nový projekt** .

   2. V rozevíracím seznamu **jazyk** vyberte možnost **C#** nebo **Visual Basic**.
      
   3. Vyberte šablonu **aplikace WPF (.NET Framework)** a pak vyberte **Další**. 
     
      ![Vytvořit nový projekt – dialogové okno](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      Otevře se dialogové okno **Konfigurovat nový projekt** .

   4. Zadejte název **`ExpenseIt`** projektu a pak vyberte **vytvořit**.

      ![Dialogové okno Konfigurovat nový projekt](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio vytvoří projekt a otevře návrháře pro výchozí okno aplikace s názvem **MainWindow. XAML**.

2. Otevřete *Application. XAML* (Visual Basic) nebo *App. XAML* (C#).

    Tento soubor XAML definuje aplikaci WPF a všechny prostředky aplikace. Tento soubor můžete také použít k určení uživatelského rozhraní, v tomto případě *MainWindow. XAML*, který se automaticky zobrazí při spuštění aplikace.

    Váš kód XAML by měl vypadat jako na následujícím Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    A podobně jako v C#následujícím seznamu:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Otevřete *MainWindow. XAML*.

    Tento soubor XAML je hlavním oknem vaší aplikace a zobrazuje obsah vytvořený na stránkách. <xref:System.Windows.Window> Třída definuje vlastnosti okna, například jeho název, velikost nebo ikonu, a zpracovává události, jako je například zavření nebo skrytí.

4. <xref:System.Windows.Window> Změňte element<xref:System.Windows.Navigation.NavigationWindow>na, jak je znázorněno v následujícím kódu XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele. To je důvod, proč <xref:System.Windows.Window> je hlavní nutné změnit <xref:System.Windows.Navigation.NavigationWindow>na. <xref:System.Windows.Navigation.NavigationWindow>dědí všechny vlastnosti <xref:System.Windows.Window>. Prvek v souboru XAML vytvoří instanci <xref:System.Windows.Navigation.NavigationWindow> třídy. <xref:System.Windows.Navigation.NavigationWindow> Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).

5. Odebere prvky z <xref:System.Windows.Navigation.NavigationWindow> značek mezi značkami. <xref:System.Windows.Controls.Grid>

6. Změňte následující vlastnosti v kódu <xref:System.Windows.Navigation.NavigationWindow> XAML elementu:

    - <xref:System.Windows.Window.Title%2A> Nastavtevlastnost`ExpenseIt`na hodnotu.

    - <xref:System.Windows.FrameworkElement.Height%2A> Nastavte vlastnost na 350 pixelů.

    - <xref:System.Windows.FrameworkElement.Width%2A> Nastavte vlastnost na 500 pixelů.

    Váš kód XAML by měl vypadat jako u Visual Basic následujících:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    A podobně jako následující pro C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Otevřete *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs*.

    Tento soubor je soubor kódu na pozadí, který obsahuje kód pro zpracování událostí deklarované v souboru *MainWindow. XAML*. Tento soubor obsahuje částečnou třídu pro okno definované v jazyce XAML.

8. Pokud používáte C#, změňte `MainWindow` třídu, ze <xref:System.Windows.Navigation.NavigationWindow>které má být odvozena. (V Visual Basic k tomu dochází automaticky při změně okna v jazyce XAML.) Váš C# kód by teď měl vypadat takto:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Přidat soubory do aplikace

V této části přidáte do aplikace dvě stránky a image.

1. Přidejte do projektu novou stránku a pojmenujte ji *`ExpenseItHome.xaml`* :

   1. V **Průzkumník řešení**klikněte pravým tlačítkem myši **`ExpenseIt`** na uzel projektu a vyberte možnost **Přidat** > **stránku**.

   1. V dialogovém okně **Přidat novou položku** je již vybrána šablona **Stránka (WPF)** . Zadejte název **`ExpenseItHome`** a pak vyberte **Přidat**.

    Tato stránka je první stránkou, která se zobrazí při spuštění aplikace. Zobrazí se seznam lidí, ze kterých se má vybrat, aby se zobrazila sestava výdajů pro.

1. Otevřete *`ExpenseItHome.xaml`* .

1. <xref:System.Windows.Controls.Page.Title%2A> Nastavtena`ExpenseIt - Home`.

1. Nastavte hodnoty prvku `DesignWidth`ana 300 pixelů. `DesignHeight`

    XAML se teď zobrazí jako Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    A podobně jako následující pro C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Otevřete *MainWindow. XAML*.

1. Přidejte k elementu vlastnost a nastavte ji na hodnotu "".`ExpenseItHome.xaml` <xref:System.Windows.Navigation.NavigationWindow.Source%2A> <xref:System.Windows.Navigation.NavigationWindow>

    Tato sada *`ExpenseItHome.xaml`* nastaví jako první stránku otevřenou při spuštění aplikace. 

    Příklad XAML v Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    A v jazyce C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Vlastnost **source** můžete nastavit také v kategorii **různé** v okně **vlastnosti** .
   >
   > ![Vlastnost source v okno Vlastnosti](./media/properties-source.png)

1. Do projektu přidejte další novou stránku WPF a pojmenujte ji *ExpenseReportPage. XAML*::

   1. V **Průzkumník řešení**klikněte pravým tlačítkem myši **`ExpenseIt`** na uzel projektu a vyberte možnost **Přidat** > **stránku**.

   1. V dialogovém okně **Přidat novou položku** vyberte šablonu **Stránka (WPF)** . Zadejte název **ExpenseReportPage**a pak vyberte **Přidat**.

    Na této stránce se zobrazí sestava výdajů pro osobu, která je vybrána na **`ExpenseItHome`** stránce.

1. Otevřete *ExpenseReportPage. XAML*.

1. <xref:System.Windows.Controls.Page.Title%2A> Nastavtena`ExpenseIt - View Expense`.

1. Nastavte hodnoty prvku `DesignWidth`ana 300 pixelů. `DesignHeight`

    *ExpenseReportPage. XAML* teď vypadá jako na následujícím Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    A podobně jako v C#následujícím seznamu:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Otevřete *ExpenseItHome. XAML. vb* a *ExpenseReportPage. XAML. vb*nebo *ExpenseItHome.XAML.cs* a *ExpenseReportPage.XAML.cs*.

    Při vytváření nového stránkovacího souboru aplikace Visual Studio automaticky vytvoří svůj soubor *kódu na pozadí* . Tyto soubory s kódem na pozadí zpracovávají logiku pro reagování na vstup uživatele.

    Váš kód by měl vypadat **`ExpenseItHome`** takto:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    A podobně jako v případě **ExpenseReportPage**postupujte takto:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Přidejte do projektu obrázek s názvem *vodotisk. png* . Můžete vytvořit vlastní image, zkopírovat soubor z ukázkového kódu nebo ho získat [sem](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).

    1. Klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat** > **existující položku**nebo stiskněte klávesu **SHIFT**+**ALT**+**A**.

    2. V dialogovém okně **Přidat existující položku** nastavte filtr File buď na **všechny soubory** , nebo na **soubory obrázků**, vyhledejte soubor obrázku, který chcete použít, a pak vyberte **Přidat**.

## <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

1. Chcete-li sestavit a spustit aplikaci, stiskněte klávesu **F5** nebo vyberte možnost **Spustit ladění** z nabídky **ladění** .

    Následující ilustrace znázorňuje aplikaci s <xref:System.Windows.Navigation.NavigationWindow> tlačítky:

    ![Aplikace po sestavení a spuštění.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Zavřete aplikaci a vraťte se do sady Visual Studio.

## <a name="create-the-layout"></a>Vytvoření rozložení

Rozložení poskytuje uspořádaný způsob, jak umístit prvky uživatelského rozhraní a také spravuje velikost a polohu těchto prvků při změně velikosti uživatelského rozhraní. Rozložení obvykle vytvoříte pomocí jednoho z následujících ovládacích prvků rozložení:

- <xref:System.Windows.Controls.Canvas>-Definuje oblast, ve které můžete explicitně umístit podřízené prvky pomocí souřadnic, které jsou relativní k oblasti plátna.
- <xref:System.Windows.Controls.DockPanel>– Definuje oblast, kde můžete uspořádat podřízené prvky buď vodorovně, nebo svisle, relativně k sobě navzájem.
- <xref:System.Windows.Controls.Grid>– Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.
- <xref:System.Windows.Controls.StackPanel>– Uspořádá podřízené prvky na jeden řádek, který může být orientovaný vodorovně nebo svisle.
- <xref:System.Windows.Controls.VirtualizingStackPanel>– Uspořádá a virtualizuje obsah na jednom řádku, který je orientovaný buď vodorovně, nebo svisle.
- <xref:System.Windows.Controls.WrapPanel>-Umístí podřízené elementy v sekvenčním umístění zleva doprava a oddělí obsah na další řádek na okraji obsahujícího pole. Následné řazení probíhá postupně shora dolů nebo zprava doleva v závislosti na hodnotě vlastnosti orientace.

Každé z těchto ovládacích prvků rozložení podporuje konkrétní typ rozložení pro jeho podřízené prvky. `ExpenseIt`lze změnit velikost stránek a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle ostatních prvků. V tomto příkladu <xref:System.Windows.Controls.Grid> se používá jako element rozložení pro aplikaci.

> [!TIP]
> Další informace o <xref:System.Windows.Controls.Panel> prvcích najdete v tématu [Přehled panelů](../controls/panels-overview.md). Další informace o rozložení najdete v tématu [layout](../advanced/layout.md).

V této části vytvoříte tabulku s jedním sloupcem se třemi řádky a okrajem 10 pixelů přidáním definice sloupců a řádků do <xref:System.Windows.Controls.Grid> v. *`ExpenseItHome.xaml`*

1. V *`ExpenseItHome.xaml`* saděnastavte<xref:System.Windows.Controls.Grid>vlastnostelementu na "10, 0, 10, 10", což odpovídá levému, hornímu a dolnímu okraji: <xref:System.Windows.FrameworkElement.Margin%2A>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Hodnoty okrajů můžete nastavit také v okně **vlastnosti** v kategorii **rozložení** :
   >
   > ![Hodnoty okrajů v okno Vlastnosti](./media/properties-margin.png)

2. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značkami k vytvoření definice řádků a sloupců:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    U dvou řádků je nastaven na <xref:System.Windows.GridLength.Auto%2A>hodnotu, což znamená, že řádky mají velikost na základě obsahu v řádcích. <xref:System.Windows.Controls.RowDefinition.Height%2A> Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> velikost, což znamená, že výška řádku je Vážený podíl dostupného místa. Pokud například dva řádky mají <xref:System.Windows.Controls.RowDefinition.Height%2A> "*", mají každý z nich výšku, která je polovinu dostupného místa.

    Teď <xref:System.Windows.Controls.Grid> by měl obsahovat následující kód XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Přidat ovládací prvky

V této části aktualizujete uživatelské rozhraní domovské stránky tak, aby zobrazovalo seznam lidí, kde vyberete jednu osobu k zobrazení své sestavy výdajů. Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům pracovat s vaší aplikací. Další informace najdete v tématu [ovládací prvky](../controls/index.md).

Chcete-li vytvořit toto uživatelské rozhraní, přidejte následující prvky do *`ExpenseItHome.xaml`* :

- A <xref:System.Windows.Controls.ListBox> (pro seznam lidí).
- A <xref:System.Windows.Controls.Label> (pro záhlaví seznamu).
- A <xref:System.Windows.Controls.Button> (Kliknutím zobrazíte sestavu výdajů pro osobu, která je vybrána v seznamu).

Každý ovládací prvek je umístěn v řádku <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> nastavení připojené vlastnosti. Další informace o připojených vlastnostech najdete v tématu [Přehled připojených vlastností](../advanced/attached-properties-overview.md).

1. Do *`ExpenseItHome.xaml`* přidejte následující XAML <xref:System.Windows.Controls.Grid> mezi značkami:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Ovládací prvky lze také vytvořit přetažením z okna **panelu nástrojů** do okna návrh a následně nastavením jejich vlastností v okně **vlastnosti** .

2. Sestavte a spusťte aplikaci.

    Následující ilustrace znázorňuje ovládací prvky, které jste vytvořili:

![Ukázka ExpenseIt obrazovky zobrazující seznam názvů](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Přidání obrázku a názvu

V této části aktualizujete uživatelské rozhraní domovské stránky s obrázkem a nadpisem stránky.

1. Do *`ExpenseItHome.xaml`* přidejte další sloupec <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevným <xref:System.Windows.Controls.ColumnDefinition.Width%2A> počtem 230 pixelů:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Přidejte další řádek do, <xref:System.Windows.Controls.Grid.RowDefinitions%2A>který bude celkem čtyři řádky:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Přesuňte ovládací prvky na druhý sloupec nastavením <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnosti na hodnotu 1 v každém ze tří ovládacích prvků (Border, ListBox a Button).

4. Každé tři ovládací prvky (ohraničení, seznam a tlačítko <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ) a pro prvek ohraničení přesuňte každý prvek dolů o jednu řadu.

   XAML pro tři ovládací prvky nyní vypadá takto:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Nastavte vlastnost na soubor bitové kopie s *vodotiskem. png* přidáním následujícího `<Grid>` XAML kamkoli mezi značky a `</Grid>`: <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Před element přidejte a <xref:System.Windows.Controls.Label> pomocí obsahu zobrazit sestavu výdajů. <xref:System.Windows.Controls.Border> Tento popisek je název stránky.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Sestavte a spusťte aplikaci.

Následující ilustrace znázorňuje výsledky toho, co jste právě přidali:

![Ukázka snímku obrazovky ExpenseIt zobrazující nové pozadí obrázku a nadpis stránky](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Přidat kód pro zpracování událostí

1. V *`ExpenseItHome.xaml`* přidejtek<xref:System.Windows.Controls.Button> elementu obslužnou rutinu události.<xref:System.Windows.Controls.Primitives.ButtonBase.Click> Další informace najdete v tématu [jak: Vytvořte jednoduchou obslužnou rutinu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))události.

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Otevřete *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`* .

3. Přidejte následující kód do `ExpenseItHome` třídy pro přidání obslužné rutiny události kliknutí na tlačítko. Obslužná rutina události otevře stránku **ExpenseReportPage** .

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Vytvoření uživatelského rozhraní pro ExpenseReportPage

*ExpenseReportPage. XAML* zobrazí sestavu výdajů pro osobu, která je vybrána na **`ExpenseItHome`** stránce. V této části vytvoříte uživatelské rozhraní pro **ExpenseReportPage**. Do různých prvků uživatelského rozhraní také přidáte barvy pozadí a výplně.

1. Otevřete *ExpenseReportPage. XAML*.

2. Do <xref:System.Windows.Controls.Grid> značek přidejte následující kód XAML:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Toto uživatelské rozhraní je podobné *`ExpenseItHome.xaml`* , s výjimkou toho, že se data <xref:System.Windows.Controls.DataGrid>sestavy zobrazují v.

3. Sestavte a spusťte aplikaci.

4. Vyberte tlačítko **Zobrazit** .

    Zobrazí se stránka Sestava výdajů. Všimněte si také, že je povoleno tlačítko zpět navigace.

Následující ilustrace znázorňuje prvky uživatelského rozhraní přidané do souboru *ExpenseReportPage. XAML*.

![Ukázka snímku obrazovky ExpenseIt zobrazující uživatelské rozhraní, které jste právě vytvořili pro ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Ovládací prvky stylu

Vzhled různých prvků je často stejný pro všechny prvky stejného typu v uživatelském rozhraní. Uživatelské rozhraní používá [styly](../controls/styling-and-templating.md) , aby bylo možné vzhledy opakovaně použít napříč více prvky. Opětovné použitelnost stylů pomáhá zjednodušit vytváření a správu XAML. Tato část nahrazuje atributy jednotlivých prvků, které byly definovány v předchozích krocích se styly.

1. Otevřete *Application. XAML* nebo *App. XAML*.

2. Do <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značek přidejte následující kód XAML:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Tento kód XAML přidá následující styly:

    - `headerTextStyle`: Pro naformátování nadpisu <xref:System.Windows.Controls.Label>stránky.

    - `labelStyle`: Pro formátování <xref:System.Windows.Controls.Label> ovládacích prvků.

    - `columnHeaderStyle`: K naformátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Chcete-li naformátovat ovládací prvky záhlaví <xref:System.Windows.Controls.Border> seznamu.

    - `listHeaderTextStyle`: K naformátování záhlaví <xref:System.Windows.Controls.Label>seznamu.

    - `buttonStyle`: Pro <xref:System.Windows.Controls.Button> naformátování `ExpenseItHome.xaml`na.

    Všimněte si, že styly jsou prostředky a podřízené <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> prvky elementu Property. V tomto umístění se styly aplikují na všechny prvky v aplikaci. Příklad používání prostředků v aplikaci .NET najdete v tématu [použití prostředků aplikace](../advanced/how-to-use-application-resources.md).

3. V *`ExpenseItHome.xaml`* , nahraďte vše <xref:System.Windows.Controls.Grid> mezi prvky následujícím XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Vlastnosti <xref:System.Windows.VerticalAlignment> , jako jsou a <xref:System.Windows.Media.FontFamily> definující vzhled jednotlivých ovládacích prvků, jsou odebrány a nahrazeny použitím stylů. Například `headerTextStyle` se použije na <xref:System.Windows.Controls.Label>sestavu zobrazit výdaje.

4. Otevřete *ExpenseReportPage. XAML*.

5. Nahraďte vše mezi <xref:System.Windows.Controls.Grid> prvky následujícím XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Tento XAML přidá styly do <xref:System.Windows.Controls.Label> prvků a. <xref:System.Windows.Controls.Border>

6. Sestavte a spusťte aplikaci. Vzhled okna je stejný jako dříve.

    ![ExpenseIt ukázkový snímek obrazovky se stejným vzhledem jako v poslední části.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Zavřete aplikaci a vraťte se do sady Visual Studio.

## <a name="bind-data-to-a-control"></a>Vázání dat k ovládacímu prvku

V této části vytvoříte data XML, která jsou svázána s různými ovládacími prvky.

1. V *`ExpenseItHome.xaml`* rámci, po otevření <xref:System.Windows.Controls.Grid> elementu přidejte <xref:System.Windows.Data.XmlDataProvider> následující XAML pro vytvoření obsahující data pro každou osobu:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Data se vytvoří jako <xref:System.Windows.Controls.Grid> prostředek. Obvykle by se tato data načítala jako soubor, ale pro zjednodušení se data přidávají jako vložená.

2. V rámci `<xref:System.Windows.DataTemplate>` <xref:System.Windows.Controls.ListBox>elementu přidejte následující prvek, který definuje, jak zobrazit data `<XmlDataProvider>` v, za prvkem: `<Grid.Resources>`

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).

3. Nahraďte existující <xref:System.Windows.Controls.ListBox> kód následujícím XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Tento kód XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> na zdroj dat a použije šablonu dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Připojení dat k ovládacím prvkům

Dále přidáte kód, který načte název, který je vybrán na **`ExpenseItHome`** stránce, a předáte ho konstruktoru třídy **ExpenseReportPage**. **ExpenseReportPage** nastaví svůj kontext dat s předanou položkou, která určuje ovládací prvky definované v rámci vazby *ExpenseReportPage. XAML* na.

1. Otevřete *ExpenseReportPage. XAML. vb* nebo *ExpenseReportPage.XAML.cs*.

2. Přidejte konstruktor, který převezme objekt, abyste mohli předat data sestavy výdajů vybrané osobě.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otevřete *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`* .

4. Změňte obslužnou rutinu události tak, aby volala nový konstruktor, který předává data sestavy výdajů vybrané osobě. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Data stylu pomocí datových šablon

V této části aktualizujete uživatelské rozhraní pro každou položku v seznamech vázaných na data pomocí datových šablon.

1. Otevřete *ExpenseReportPage. XAML*.

2. Navažte obsah prvků "název" a "oddělení" <xref:System.Windows.Controls.Label> na odpovídající vlastnost zdroje dat. Další informace o datové vazbě najdete v tématu [Přehled datových vazeb](../data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po otevření <xref:System.Windows.Controls.Grid> elementu přidejte následující šablony dat, které definují, jak zobrazit data sestavy výdajů:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Nahraďte<xref:System.Windows.Controls.DataGridTemplateColumn> elementy<xref:System.Windows.Controls.DataGrid> elementem a použijte pro ně šablony. <xref:System.Windows.Controls.DataGridTextColumn>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Sestavte a spusťte aplikaci.

6. Vyberte osobu a pak vyberte tlačítko **Zobrazit** .

Následující ilustrace znázorňuje obě stránky `ExpenseIt` aplikace s ovládacími prvky, rozložením, styly, datovými vazbami a použitými šablonami dat:

![Obě stránky aplikace zobrazují seznam názvů a sestavu výdajů.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Tato ukázka demonstruje konkrétní funkci WPF a nedodržuje všechny osvědčené postupy pro věci, jako je zabezpečení, lokalizace a přístupnost. Pro komplexní pokrytí prostředí WPF a osvědčených postupů vývoje aplikací .NET si přečtěte následující témata:
>
> - [Usnadnění](../../ui-automation/accessibility-best-practices.md)
>
> - [Zabezpečení](../security-wpf.md)
>
> - [Globalizace a lokalizace WPF](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [Výkon WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Další postup

V tomto návodu jste se naučili řadou postupů pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF). Nyní byste měli mít základní znalosti stavebních bloků aplikace .NET vázané na data. Další informace o architektuře a programovacích modelech WPF naleznete v následujících tématech:

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
- [Přehled šablonování dat](../data/data-templating-overview.md)
- [Sestavení aplikace WPF](../app-development/building-a-wpf-application-wpf.md)
- [Styly a šablony](../controls/styles-and-templates.md)
