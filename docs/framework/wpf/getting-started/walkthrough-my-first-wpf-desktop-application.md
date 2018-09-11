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
ms.openlocfilehash: a8f806a1f1f7840f21e82d77d1b639b9318259e7
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271387"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Návod: Moje první desktopová aplikace WPF

V tomto článku se dozvíte, jak vyvíjet jednoduchou aplikaci Windows Presentation Foundation (WPF), která obsahuje elementy, které jsou společné pro většinu aplikací WPF: značek Extensible Application Markup Language (XAML), použití modelu code-behind, definice aplikací ovládací prvky, rozložení, datové vazby a styly.

Tento návod zahrnuje následující kroky:

- Umožňuje navrhnout vzhled uživatelského rozhraní (UI) pro aplikace XAML.

- Napsání kódu pro sestavení chování aplikace.

- Vytvořte definici aplikace ke správě aplikace.

- Přidání ovládacích prvků a vytvořit rozložení k vytvoření uživatelského rozhraní aplikace.

- Vytvoření styly pro konzistentní vzhled uživatelského rozhraní aplikace.

- Svázat data pro naplnění uživatelského rozhraní z dat i chránit data a synchronizované uživatelské rozhraní uživatelského rozhraní.

Na konci návodu budete sestavíte samostatnou aplikaci Windows, která umožňuje uživatelům zobrazit vyúčtování pro vybraného uživatele. Aplikace se skládá z několika stránek WPF, které jsou hostované v okně prohlížeče – vizuální styl.

> [!TIP]
> Ukázkový kód, který se používá k vytvoření tohoto návodu je k dispozici pro Visual Basic a C# na [Úvod do vytváření aplikací WPF](https://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2012 nebo novější

Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Vytvoření projektu aplikace

Prvním krokem je vytvoření aplikační infrastruktury, který obsahuje definici aplikace, dvě stránky a bitovou kopii.

1. Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem **`ExpenseIt`**:

   1. Otevřít Visual Studio a vyberte **souboru** > **nový** > **projektu**.

      **Nový projekt** otevře se dialogové okno.

   2. V části **nainstalováno** kategorie, rozbalte buď **Visual C#** nebo **jazyka Visual Basic** uzlu a pak vyberte **klasická plocha Windows**.

   3. Vyberte **aplikace WPF (.NET Framework)** šablony. Zadejte název **`ExpenseIt`** a pak vyberte **OK**.

      ![Dialogové okno nového projektu s vybraná aplikace WPF](media/new-project-dialog.png)

      Visual Studio vytvoří projekt a otevře se návrhář pro výchozí okno aplikace s názvem **souboru MainWindow.xaml**.

   > [!NOTE]
   > Tento návod používá <xref:System.Windows.Controls.DataGrid> ovládací prvek, který je k dispozici v rozhraní .NET Framework 4 a novější. Být jisti, že váš projekt cílí na rozhraní .NET Framework 4 nebo novější. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Otevřít *Application.xaml* (Visual Basic) nebo *App.xaml* (C#).

    Tento soubor XAML definuje aplikace WPF a všechny prostředky, aplikace. Tento soubor je využít taky k určení rozhraní, které se automaticky zobrazí při spuštění aplikace; v takovém případě *souboru MainWindow.xaml*.

    Vaše XAML by měl vypadat takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Nebo takto v jazyce C#:

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

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

   Tato aplikace přejde na jiný obsah v závislosti na vstupu uživatele. To je důvod, proč hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> zdědí všechny vlastnosti <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Vytvoří instanci prvku v souboru XAML <xref:System.Windows.Navigation.NavigationWindow> třídy. Další informace najdete v tématu [Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Změňte následující vlastnosti na <xref:System.Windows.Navigation.NavigationWindow> element:

    - Nastavte <xref:System.Windows.Window.Title%2A> vlastnost "`ExpenseIt`".

    - Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na šířku 500 pixelů.

    - Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost na 350 pixelů.

    - Odeberte <xref:System.Windows.Controls.Grid> prvky mezi <xref:System.Windows.Navigation.NavigationWindow> značky.

    Vaše XAML by měl vypadat takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Nebo takto v jazyce C#:

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Otevřít *soubor MainWindow.xaml.vb* nebo *MainWindow.xaml.cs*.

    Tento soubor je soubor kódu na pozadí, který obsahuje kód pro zpracování události deklarované v *souboru MainWindow.xaml*. Tento soubor obsahuje částečné třídy pro okno definované v XAML.

7. Pokud používáte C#, změňte `MainWindow` třídy odvozovat z <xref:System.Windows.Navigation.NavigationWindow>. (V jazyce Visual Basic, tomu automaticky dojde při změně okna v XAML.)

   Váš kód by měl vypadat takto:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > Můžete přepínat na jazyk kódu ukázek kódu mezi C# a Visual Basic v **jazyk** rozevíracího seznamu v horní pravé části tohoto článku.

## <a name="add-files-to-the-application"></a>Přidání souborů do aplikace

V této části přidáte dvě stránky a obrázku do aplikace.

1. Do projektu přidejte novou stránku WPF a pojmenujte ho *`ExpenseItHome.xaml`*:

   1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.

   1. V **přidat novou položku** dialogového okna, **stránky (WPF)** šablony je už vybraná. Zadejte název **`ExpenseItHome`** a pak vyberte **přidat**.

    Tato stránka je první stránka, která se zobrazí při spuštění aplikace. Zobrazí seznam uživatelů vyberte, chcete-li zobrazit sestavy výdajů pro.

2. Otevřít *`ExpenseItHome.xaml`*.

3. Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - Home`".

    Vaše XAML by měl vypadat takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Nebo to v jazyce C#:

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Otevřít *souboru MainWindow.xaml*.

5. Nastavte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> na "`ExpenseItHome.xaml`".

    Tím se nastaví *`ExpenseItHome.xaml`* bude první stránka otevře při spuštění aplikace. Vaše XAML by měl vypadat takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Nebo to v jazyce C#:

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Můžete také nastavit **zdroj** vlastnost **různé** kategorii **vlastnosti** okna.
   >
   > ![Source – vlastnost v okně Vlastnosti](media/properties-source.png)

6. Do projektu přidejte další novou stránku WPF a pojmenujte ho *ExpenseReportPage.xaml*::

   1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **`ExpenseIt`** uzel projektu a zvolte **přidat** > **stránky**.

   1. V **přidat novou položku** dialogového okna, **stránky (WPF)** šablony je už vybraná. Zadejte název **ExpenseReportPage**a pak vyberte **přidat**.

    Na této stránce se zobrazí vyúčtování pro osoby, která je vybrán na **`ExpenseItHome`** stránky.

7. Otevřít *ExpenseReportPage.xaml*.

8. Nastavte <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - View Expense`".

    Vaše XAML by měl vypadat takto v jazyce Visual Basic:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Nebo to v jazyce C#:

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Otevřít *ExpenseItHome.xaml.vb* a *ExpenseReportPage.xaml.vb*, nebo *ExpenseItHome.xaml.cs* a *ExpenseReportPage.xaml.cs*.

    Když vytvoříte nový soubor stránky, sada Visual Studio automaticky vytvoří *použití modelu code-behind* souboru. Tyto soubory použití modelu code-behind zpracování logiky reagovat na vstup uživatele.

    Váš kód by měl vypadat takto pro **`ExpenseItHome`**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    A takhle pro **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Přidání obrázku s názvem *watermark.png* do projektu. Můžete vytvořit vlastní image, zkopírujte soubor ve vzorku kódu nebo získat [tady](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **existující položku**, nebo stiskněte klávesu **Shift**+**Alt** + **A**.

   2. V **přidat existující položku** dialogové okno, přejděte k souboru bitové kopie, kterou chcete použít a potom vyberte **přidat**.

## <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

1. Chcete-li sestavit a spustit aplikaci, stiskněte **F5** nebo vyberte **spustit ladění** z **ladění** nabídky.

    Následující obrázek znázorňuje aplikaci <xref:System.Windows.Navigation.NavigationWindow> tlačítka:

    ![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Ukončete aplikaci se vraťte do sady Visual Studio.

## <a name="create-the-layout"></a>Vytvořit rozložení

Rozložení poskytuje seřazený umožňuje umístit prvky uživatelského rozhraní a také spravuje velikost a umístění těchto prvků při změně velikosti uživatelského rozhraní. Rozložení se obvykle vytvoříte pomocí jednoho z následujících ovládacích prvků rozložení:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Každá z těchto ovládacích prvků rozložení podporuje zvláštní druh rozložení pro jeho podřízené prvky. `ExpenseIt` změnit velikost stránky, a každá stránka obsahuje prvky, které jsou uspořádány vodorovně a svisle vedle dalších prvků. V důsledku toho <xref:System.Windows.Controls.Grid> je prvek ideální rozložení pro aplikaci.

> [!TIP]
> Další informace o <xref:System.Windows.Controls.Panel> prvky, naleznete v tématu [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md). Další informace o rozložení najdete v tématu [rozložení](../../../../docs/framework/wpf/advanced/layout.md).

V části vytvoříte tabulku s jedním sloupcem se třemi řádky a 10 pixel okraj přidáním řádků a sloupců definice <xref:System.Windows.Controls.Grid> v *`ExpenseItHome.xaml`*.

1. Otevřít *`ExpenseItHome.xaml`*.

2. Nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> prvku "10,0,10,10", která odpovídá na levé straně, horní, pravé a dolní okraj:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Můžete také nastavit **okraj** hodnoty v **vlastnosti** okně v části **rozložení** kategorie:
   >
   > ![Hodnoty vlastnosti okraj v okně Vlastnosti](media/properties-margin.png)

3. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky vytvářet definice řádků a sloupců:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A> Dva řádky se nastaví na <xref:System.Windows.GridLength.Auto%2A>, což znamená, že je nastavena velikost řádků založit na obsah v řádcích. Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> velikosti, což znamená, že vážený poměr volného místa výšku řádku. Například pokud máte dva řádky <xref:System.Windows.Controls.RowDefinition.Height%2A> z "*", každý z nich výška polovinu dostupné místo.

    Vaše <xref:System.Windows.Controls.Grid> by teď měl vypadat podobně jako následující XAML:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Přidání ovládacích prvků

V této části budete aktualizovat na domovské stránce uživatelského rozhraní, zobrazí se seznam lidí, se může uživatel vybrat z zobrazíte vyúčtování pro. Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům, aby komunikovali s vaší aplikací. Další informace najdete v tématu [ovládací prvky](../../../../docs/framework/wpf/controls/index.md).

K vytvoření tohoto uživatelského rozhraní, přidejte následující prvky, které mají *`ExpenseItHome.xaml`*:

- <xref:System.Windows.Controls.ListBox> (pro seznam lidí, kteří).
- <xref:System.Windows.Controls.Label> (pro záhlaví seznamu).
- <xref:System.Windows.Controls.Button> (Chcete-li kliknutím zobrazíte vyúčtování pro osobu, která je v seznamu vyberete).

Každý ovládací prvek nachází v řádku <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost. Další informace o přidružené vlastnosti najdete v tématu [přehled připojených vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Otevřít *`ExpenseItHome.xaml`*.

2. Přidejte následující XAML někde mezi <xref:System.Windows.Controls.Grid> značky:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Ovládací prvky můžete vytvořit také z jejich přetažením **nástrojů** okna do okna návrhu a nastavte jejich vlastnosti **vlastnosti** okna.

3. Sestavte a spusťte aplikaci.

Následující obrázek znázorňuje ovládací prvky, že kterou jste právě vytvořili:

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Přidat obrázek a název

V této části budete aktualizovat Uživatelském rozhraní domovské stránky s bitovou kopii a název stránky.

1. Otevřít *`ExpenseItHome.xaml`*.

2. Přidat jiný sloupec <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevnou <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Přidat další řádek <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, celkem čtyři řádky:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Přesuňte ovládací prvky na druhý sloupec tak, že nastavíte <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost na hodnotu 1 v každé tři ovládací prvky (hranice ListBox a tlačítko).

5. Každý ovládací prvek dolů řádek zvýšením jeho <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> hodnotu o 1.

   XAML pro tři ovládací prvky nyní vypadá takto:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Nastavte <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> bude *watermark.png* soubor obrázku, přidáním následující XAML někde mezi `<Grid>` a `</Grid>` značky:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Před <xref:System.Windows.Controls.Border> prvku, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazení vyúčtování". Toto je název stránky.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Sestavte a spusťte aplikaci.

Následující obrázek ukazuje výsledky co jste právě přidali:

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Přidejte kód pro zpracování událostí

1. Otevřít *`ExpenseItHome.xaml`*.

2. Přidat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události <xref:System.Windows.Controls.Button> elementu. Další informace najdete v tématu [postupy: vytvoření jednoduché obslužnou](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.

4. Přidejte následující kód, který `ExpenseItHome` třídy přidejte tlačítko klikněte na obslužnou rutinu události. Obslužná rutina události otevře **ExpenseReportPage** stránky.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Vytvoření uživatelského rozhraní pro ExpenseReportPage

*ExpenseReportPage.xaml* zobrazí vyúčtování pro osobu, která je vybrán na **`ExpenseItHome`** stránky. V této části vytvoříte uživatelské rozhraní pro **ExpenseReportPage**. Budete také přidat na pozadí a vyplnit barev pro různé elementy uživatelského rozhraní.

1. Otevřít *ExpenseReportPage.xaml*.

2. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Toto uživatelské rozhraní je podobný *`ExpenseItHome.xaml`*, s výjimkou data sestavy se zobrazí v <xref:System.Windows.Controls.DataGrid>.

3. Sestavte a spusťte aplikaci.

    > [!NOTE]
    > Pokud dojde k chybě <xref:System.Windows.Controls.DataGrid> se nepovedlo najít nebo neexistuje, ujistěte se, že váš projekt cílí na .NET Framework 4 nebo novější. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Vyberte **zobrazení** tlačítko.

    Zobrazí se stránka sestavy výdajů. Všimněte si také, zda je povoleno tlačítko zpětné navigace.

Následující obrázek znázorňuje prvky uživatelského rozhraní, které jsou přidány do *ExpenseReportPage.xaml*.

![Snímek obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Ovládací prvky stylu

Vzhled různé prvky je často stejný pro všechny prvky v uživatelském rozhraní stejného typu. Uživatelské rozhraní používá [styly](../../../../docs/framework/wpf/controls/styling-and-templating.md) k zajištění vzhled opakovaně použitelné napříč více prvků. Opětovné použití stylů pomáhá zjednodušit XAML vytváření a správu. Tato část nahradí atributy na element, definované v předchozích krocích se styly.

1. Otevřít *Application.xaml* nebo *App.xaml*.

2. Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Tento XAML přidá následující styly:

    - `headerTextStyle`: K formátování se název stránky <xref:System.Windows.Controls.Label>.

    - `labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládacích prvků.

    - `columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládacích prvků.

    - `listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.

    Všimněte si, že se styly prostředky a podřízené objekty daného <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti. V tomto umístění se styly použijí na všechny prvky v aplikaci. Příklad použití prostředků v aplikaci .NET Framework, naleznete v tématu [využití prostředků aplikace](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Otevřít *`ExpenseItHome.xaml`*.

4. Nahradit vše mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> , které definují vzhled každého ovládacího prvku odebrán a nahrazen o aplikování stylů. Například `headerTextStyle` platí pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>.

5. Otevřít *ExpenseReportPage.xaml*.

6. Nahradit vše mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Tento postup přidá stylů <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy.

## <a name="bind-data-to-a-control"></a>Vytvoření vazby dat k ovládacímu prvku

V této části vytvoříte data XML, který je vázán na různé ovládací prvky.

1. Otevřít *`ExpenseItHome.xaml`*.

2. Po zahájení <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML vytvořit <xref:System.Windows.Data.XmlDataProvider> , která pro každou osobu, která obsahuje data:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Data se vytvoří jako <xref:System.Windows.Controls.Grid> prostředků. Obvykle to budou načteny jako soubor, ale pro zjednodušení je přidat data vložené.

3. V rámci `<Grid.Resources>` elementu, přidejte následující <xref:System.Windows.DataTemplate>, který definuje způsob zobrazení dat v <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Další informace o šablonách dat, naleznete v tématu [přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Nahraďte existující <xref:System.Windows.Controls.ListBox> s následující XAML:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Tento XAML naváže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Připojení dat k ovládacím prvkům

V dalším kroku přidáte kód pro načtení název, který je vybrán na **`ExpenseItHome`** stránku a předat konstruktoru **ExpenseReportPage**. **ExpenseReportPage** nastaví jeho kontext dat s předaným položka, která se, co ovládací prvky definované v *ExpenseReportPage.xaml* svázat.

1. Otevřít *ExpenseReportPage.xaml.vb* nebo *ExpenseReportPage.xaml.cs*.

2. Přidáte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů z vybraného uživatele.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Otevřít *`ExpenseItHome.xaml.vb`* nebo *`ExpenseItHome.xaml.cs`*.

4. Změnit <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události volaná nový konstruktor předávání dat sestavy výdajů z vybraného uživatele.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Styl dat s využitím šablon dat

V této části budete aktualizovat uživatelské rozhraní pro každou položku v seznamu vázaných na data pomocí šablony.

1. Otevřít *ExpenseReportPage.xaml*.

2. Vytvoření vazby obsah "Name" a "Oddělení" <xref:System.Windows.Controls.Label> prvků, které se příslušná data source – vlastnost. Další informace o datové vazbě naleznete v tématu [přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Po zahájení <xref:System.Windows.Controls.Grid> prvku, přidejte následující datové šablony, které definují způsob zobrazení dat sestavy výdajů:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Nahraďte <xref:System.Windows.Controls.DataGridTextColumn> prvky s <xref:System.Windows.Controls.DataGridTemplateColumn> pod <xref:System.Windows.Controls.DataGrid> elementu a použijte šablony k nim.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Sestavte a spusťte aplikaci.

6. Vybrat osobu a pak vyberte **zobrazení** tlačítko.

Následující obrázek ukazuje obě stránky `ExpenseIt` aplikace s ovládacími prvky, rozložení, styly, vazby dat a použitých šablon dat:

![Snímky obrazovky ExpenseIt – ukázka](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Tato ukázka předvádí konkrétní funkce WPF a nebude použijte všechny osvědčené postupy pro takové věci, jako je zabezpečení, lokalizace a přístupnost. Pro komplexní pokrytí WPF a osvědčené postupy vývoje aplikací rozhraní .NET Framework naleznete v následujících tématech:
>
> - [Usnadnění](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Zabezpečení](../../../../docs/framework/wpf/security-wpf.md)
>
> - [WPF globalizace a lokalizace](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [Výkonu WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Další kroky

V tomto návodu jste zjistili několik technik pro vytvoření uživatelského rozhraní pomocí Windows Presentation Foundation (WPF). Nyní byste měli mít základní znalosti o stavební bloky vázané na data, aplikace rozhraní .NET Framework. Další informace o WPF architekturu a programovací modely naleznete v následujících tématech:

- [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)

Další informace o vytváření aplikací naleznete v následujících tématech:

- [Vývoj aplikací](../../../../docs/framework/wpf/app-development/index.md)
- [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>Viz také:

- [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styles-and-templates.md)
