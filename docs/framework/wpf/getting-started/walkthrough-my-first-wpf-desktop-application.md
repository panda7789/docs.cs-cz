---
title: "Návod: Můj první grafický subsystém WPF aplikace pracovní plochy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9818231a68f5c2ac2a6852f27e4876baa9728e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Návod: Můj první grafický subsystém WPF aplikace pracovní plochy
Tento názorný postup obsahuje úvod do vývoje [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikace, která obsahuje prvky, které jsou společné pro většinu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] značek, kódu, definice aplikace, ovládací prvky, rozložení Datová vazba a stylů. 
  
 Tento postup vás provede vývoj jednoduchou [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace pomocí následujících kroků. 
  
-   Definování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] návrhu vzhled aplikace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. 
  
-   Psaní kódu k sestavení chování aplikace. 
  
-   Vytvoření definice aplikace ke správě aplikace. 
  
-   Přidání ovládacích prvků a vytváření rozložení k vytvoření aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Vytváření stylů pro vytvoření konzistentní vzhled aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Vazba [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] k datům a obě naplnit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z data a zachovat data a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronizovány. 
  
 Na konci průvodce, který bude jste vytvořili samostatnou [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikace, která umožňuje uživatelům zobrazit sestavy výdajů pro vybrané osoby. Aplikace se skládá z několika [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stránek, které jsou hostované v okně prohlížeče stylu. 
  
 Ukázkový kód, který je použit k vytvoření tohoto návodu je dostupná pro [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] a [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] v [Úvod do vytváření grafického subsystému WPF aplikací](http://go.microsoft.com/fwlink/?LinkID=160008). 

## <a name="prerequisites"></a>Požadavky  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]nebo novější

Další informace o instalaci nejnovější verze sady Visual Studio najdete v tématu [instalaci sady Visual Studio](/visualstudio/install/install-visual-studio).
  
## <a name="creating-the-application-project"></a>Vytvoření projektu aplikace  
 V této části vytvoříte infrastrukturu aplikace, která zahrnuje definice aplikace, dvě stránky a bitovou kopii. 
  
1. Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem `ExpenseIt`. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82). 
  
    > [!NOTE]
    >  Tento návod používá <xref:System.Windows.Controls.DataGrid> ovládací prvek, který je k dispozici v rozhraní .NET Framework 4. Být jisti, že cílem vašeho projektu je .NET Framework 4 nebo novější. Další informace najdete v tématu[postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
2. Otevřete Application.xaml (Visual Basic) nebo App.xaml (C#). 
  
     To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor definuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace a všechny prostředky aplikace. Tento soubor můžete taky použít k určení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] která automaticky zobrazí při spuštění aplikace; v tomto případě MainWindow.xaml. 
  
     Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     Nebo podobně jako v C#:  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. Otevřete MainWindow.xaml. 
  
     To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor je hlavním okně aplikace a zobrazí obsah vytvořený v stránky. <xref:System.Windows.Window> Třídy definuje vlastnosti časového období, například jeho název, velikost nebo ikonu a zpracovává události, například zavření nebo skrytí. 
  
4. Změna <xref:System.Windows.Window> elementu, který chcete <xref:System.Windows.Navigation.NavigationWindow>. 
  
     Tato aplikace bude přejděte na jiný obsah, v závislosti na interakci s uživatelem. Proto hlavní <xref:System.Windows.Window> musí změnit tak, aby <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>dědí všechny vlastnosti <xref:System.Windows.Window>. <xref:System.Windows.Navigation.NavigationWindow> Element v souboru XAML vytvoří instanci <xref:System.Windows.Navigation.NavigationWindow> třídy. Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md). 
  
5. Změnit na následující vlastnosti <xref:System.Windows.Navigation.NavigationWindow> element:  
  
    -   Nastavte <xref:System.Windows.Window.Title%2A> vlastnost ExpenseIt "–". 
  
    -   Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na 500 pixelů. 
  
    -   Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost 350 pixelů. 
  
    -   Odeberte <xref:System.Windows.Controls.Grid> prvky mezi <xref:System.Windows.Navigation.NavigationWindow> značky. 
  
     Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     Nebo podobně jako v C#:  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. Otevřete MainWindow.xaml.vb nebo MainWindow.xaml.cs. 
  
     Tento soubor je soubor kódu, který obsahuje kód pro zpracování události deklarované v MainWindow.xaml. Tento soubor obsahuje konkrétní třídu pro okno definované v jazyce XAML. 
  
7. Pokud používáte C#, změňte `MainWindow` odvozena od třídy <xref:System.Windows.Navigation.NavigationWindow>. 
  
     V jazyce Visual Basic tomu automaticky dojde při změně okna v jazyce XAML. 
  
     Váš kód by měl vypadat takto. 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a>Přidávání souborů do aplikace  
 V této části přidáte dvě stránky a bitovou kopii do aplikace. 
  
1. Přidat nové stránky (WPF) do projektu s názvem `ExpenseItHome.xaml`. Další informace najdete v tématu [postupy: přidání nových položek do projektu WPF](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad). 
  
     Tato stránka je první stránka, která se zobrazí, když je aplikace spuštěna. Zobrazí seznam uživatelů, ze kterého může uživatel vybrat uživatele, který bude zobrazit sestavu výdajů pro. 
  
2. Otevřete ExpenseItHome.xaml. 
  
3. Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - domovské". 
  
     Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     Nebo to v jazyce C#:  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. Otevřete MainWindow.xaml. 
  
5. Nastavte <xref:System.Windows.Navigation.NavigationWindow.Source%2A> vlastnost <xref:System.Windows.Navigation.NavigationWindow> na "ExpenseItHome.xaml". 
  
     Toto nastaví ExpenseItHome.xaml na první stránce otevřelo při spuštění aplikace. Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     Nebo to v jazyce C#:  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. Přidat nové stránky (WPF) do projektu s názvem `ExpenseReportPage.xaml`. 
  
     Tato stránka se zobrazí vyúčtování pro osobě, která je vybrána na ExpenseItHome.xaml. 
  
7. Otevřete ExpenseReportPage.xaml. 
  
8. Nastavte <xref:System.Windows.Controls.Page.Title%2A> k "ExpenseIt – - zobrazení výdajů". 
  
     Vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] by mělo vypadat jako v jazyce Visual Basic:  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     Nebo to v jazyce C#:  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. Otevřete ExpenseItHome.xaml.vb a ExpenseReportPage.xaml.vb, nebo ExpenseItHome.xaml.cs a ExpenseReportPage.xaml.cs. 
  
     Když vytvoříte nový soubor stránky, Visual Studio automaticky vytvoří souboru kódu. Tyto soubory kódu zpracování logiky reagovat na vstup uživatele. 
  
     Váš kód by měl vypadat takto. 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. Přidejte bitovou kopii s názvem watermark.png do projektu. Můžete vytvořit vlastní image, nebo zkopírovat soubor z ukázkového kódu. Další informace najdete v tématu [NIB: postupy: Přidání existujících položek do projektu](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3). 

## <a name="building-and-running-the-application"></a>Vytváření a spouštění aplikace  
 V této části sestavíte a spustíte aplikaci. 
  
1. Sestavte a spusťte aplikaci stisknutím klávesy F5 nebo vyberte **spustit ladění** z **ladění** nabídky. 
  
     Následující obrázek znázorňuje aplikace s <xref:System.Windows.Navigation.NavigationWindow> tlačítka. 
  
     ![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2. Zavřete aplikaci se vraťte do [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. 
  
## <a name="creating-the-layout"></a>Vytváření rozložení  
 Rozložení poskytuje seřazené způsob, jak umístit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky a také spravuje velikost a umístění těchto elementů při [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se změnila velikost. Obvykle vytvoříte rozložení s jedním z následujících rozložení ovládacích prvků:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Každý z těchto prvků rozložení podporuje zvláštním typem rozložení pro její podřízené elementy. Stránky ExpenseIt – jde změnit, a každé stránce má prvky, které jsou uspořádány vodorovně a svisle u jiných prvků. V důsledku toho <xref:System.Windows.Controls.Grid> je ideální rozložení elementu pro danou aplikaci. 
  
> [!NOTE]
>  Další informace o <xref:System.Windows.Controls.Panel> elementy, najdete v části [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md). Další informace o rozložení najdete v tématu [rozložení](../../../../docs/framework/wpf/advanced/layout.md). 
  
 V části vytvoříte tabulku s jedním sloupcem s tři řádky a okraj 10 pixelů přidáním sloupce a řádku definice, které <xref:System.Windows.Controls.Grid> v ExpenseItHome.xaml. 
  
1. Otevřete ExpenseItHome.xaml. 
  
2. Nastavte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.Grid> element "10,0,10,10", který odpovídá na levé straně, horní, pravé a dolní okraj. 
  
3. Přidejte následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mezi <xref:System.Windows.Controls.Grid> značek k vytvoření definice řádků a sloupců. 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <xref:System.Windows.Controls.RowDefinition.Height%2A> Dvou řádků je nastaven na <xref:System.Windows.GridLength.Auto%2A> to znamená, že bude mít velikost řádky založit na obsah v řádcích. Výchozí hodnota <xref:System.Windows.Controls.RowDefinition.Height%2A> je <xref:System.Windows.GridUnitType.Star> nastavení velikosti, což znamená, že řádek bude vyvážené podíl volné místo. Například pokud dva řádky mít výšku "*", budou mít obě výška, který je polovinu dostupné místo.  
  
     Vaše <xref:System.Windows.Controls.Grid> by teď měl vypadat jako následující XAML:  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a>Přidání ovládacích prvků  
 V této části se na domovskou stránku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zobrazí seznam lidí, že uživatelé mohou vybírat z zobrazíte vyúčtování pro vybraného uživatele. Ovládací prvky jsou objekty uživatelského rozhraní, které umožňují uživatelům interakci s vaší aplikací. Další informace najdete v tématu [ovládací prvky](../../../../docs/framework/wpf/controls/index.md). 
  
 K vytvoření tohoto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], tyto prvky jsou přidány do ExpenseItHome.xaml:  
  
-   <xref:System.Windows.Controls.ListBox>(pro seznam lidí, kteří). 
  
-   <xref:System.Windows.Controls.Label>(pro hlavičku seznamu). 
  
-   <xref:System.Windows.Controls.Button>(Chcete-li kliknutím zobrazíte vyúčtování osoby, který je vybraný v seznamu). 
  
 Každý ovládací prvek je umístěn v řádek <xref:System.Windows.Controls.Grid> nastavením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> přidružená vlastnost. Další informace o přidružené vlastnosti najdete v tématu [připojen přehled vlastností](../../../../docs/framework/wpf/advanced/attached-properties-overview.md). 
  
1. Otevřete ExpenseItHome.xaml. 
  
2. Přidejte následující [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mezi <xref:System.Windows.Controls.Grid> značky. 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. Sestavte a spusťte aplikaci. 
  
 Následující obrázek znázorňuje ovládacích prvků, které jsou vytvořené pomocí XAML v této části. 
  
 ![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
## <a name="adding-an-image-and-a-title"></a>Přidání obrázku a název  
 V této části se na domovskou stránku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se aktualizují bitovou kopii a název stránky. 
  
1. Otevřete ExpenseItHome.xaml. 
  
2. Přidejte jiný sloupec pro <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> s pevným <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pixelů. 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. Přidejte jiný řádek na <xref:System.Windows.Controls.Grid.RowDefinitions%2A>. 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. Přesunout ovládacích prvků na druhý sloupec nastavením <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> na 1. Každý ovládací prvek dolů řádek, zvýšením <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> o 1. 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. Nastavte <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> být watermark.png soubor bitové kopie. 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. Před <xref:System.Windows.Controls.Border>, přidejte <xref:System.Windows.Controls.Label> s obsahem "Zobrazit sestavu výdajů" jako nadpis stránky. 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. Sestavte a spusťte aplikaci. 
  
 Následující obrázek znázorňuje výsledky v této části. 
  
 ![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
## <a name="adding-code-to-handle-events"></a>Přidání kódu ke zpracování událostí  
  
1. Otevřete ExpenseItHome.xaml. 
  
2. Přidat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události <xref:System.Windows.Controls.Button> elementu. Další informace najdete v tématu [postupy: vytvoření jednoduché obslužné rutiny události](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480). 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. Otevřete ExpenseItHome.xaml.vb nebo ExpenseItHome.xaml.cs. 
  
4. Přidejte následující kód, který <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události, což způsobí, že okno a přejděte k souboru ExpenseReportPage.xaml. 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a>Vytvoření uživatelského rozhraní pro ExpenseReportPage  
 ExpenseReportPage.xaml zobrazí vyúčtování osoby, která byla vybrána na ExpenseItHome.xaml. Tato část přidá ovládací prvky a vytvoří [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro ExpenseReportPage.xaml. Tato část také přidá barvy pozadí a výplně na různé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy. 
  
1. Otevřete ExpenseReportPage.xaml. 
  
2. Přidejte následující XAML mezi <xref:System.Windows.Controls.Grid> značky. 
  
     Toto uživatelské rozhraní je podobná na ExpenseItHome.xaml vytvořit, s výjimkou data sestavy se zobrazí v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid>. 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. Sestavte a spusťte aplikaci. 
  
    > [!NOTE]
    >  Pokud dojde k chybě <xref:System.Windows.Controls.DataGrid> nebyl nalezen nebo neexistuje, ujistěte se, že cílem vašeho projektu je .NET Framework 4 nebo novější. Další informace najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
4. Klikněte **zobrazení** tlačítko. 
  
     Zobrazí se stránka sestavy výdajů. 
  
 Následující obrázek ukazuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy přidané do ExpenseReportPage.xaml. Všimněte si, že je povolena back navigační tlačítko. 
  
 ![Snímek obrazovky ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
## <a name="styling-controls"></a>Ovládací prvky stylů  
 Vzhled různé prvky může být často stejný pro všechny elementy v stejného typu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]používá styly vzhledy opakovaně použitelné napříč více elementů. – Opětovné použití stylů umožňuje zjednodušit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vytváření a správu. Další informace o styly najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md). Tato část nahradí za element atributy, které byly definovány v předchozích krocích se styly. 
  
1. Otevřete Application.xaml nebo App.xaml. 
  
2. Přidejte následující XAML mezi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> značky:  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] přidá následující styly:  
  
    -  `headerTextStyle`: Chcete-li formát názvu stránky <xref:System.Windows.Controls.Label>. 
  
    -  `labelStyle`: K formátování <xref:System.Windows.Controls.Label> ovládací prvky. 
  
    -  `columnHeaderStyle`: K formátování <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>. 
  
    -  `listHeaderStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Border> ovládací prvky. 
  
    -  `listHeaderTextStyle`: K formátování záhlaví seznamu <xref:System.Windows.Controls.Label>. 
  
    -  `buttonStyle`: K formátování <xref:System.Windows.Controls.Button> na ExpenseItHome.xaml. 
  
     Všimněte si, že stylů jsou prostředky a podřízené objekty <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> element vlastnosti. V tomto umístění stylů platí pro všechny elementy v aplikaci. Příklad použití prostředků v [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikace, najdete v části [prostředky aplikace použijte](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md). 
  
3. Otevřete ExpenseItHome.xaml. 
  
4. Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML. 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     Vlastnosti, jako <xref:System.Windows.VerticalAlignment> a <xref:System.Windows.Media.FontFamily> které definují, jak vypadá každý ovládací prvek se odeberou a nahrazuje použití stylů. Například `headerTextStyle` se použije pro "Zobrazení vyúčtování" <xref:System.Windows.Controls.Label>. 
  
5. Otevřete ExpenseReportPage.xaml. 
  
6. Nahraďte všechno mezi <xref:System.Windows.Controls.Grid> prvky s následující XAML. 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     Tento postup přidá stylů pro <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Border> elementy. 
  
7. Sestavte a spusťte aplikaci. 
  
     Po přidání [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v této části aplikace vypadá stejně jako předtím aktualizace se styly. 
  
## <a name="binding-data-to-a-control"></a>Vazba dat k ovládacímu prvku  
 V této části vytvoříte [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data, která je vázána na různé ovládací prvky. 
  
1. Otevřete ExpenseItHome.xaml. 
  
2. Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující XAML pro vytvoření <xref:System.Windows.Data.XmlDataProvider> obsahující data pro každou osobu. 
  
     Data je vytvořen jako <xref:System.Windows.Controls.Grid> prostředků. Obvykle to by načíst jako soubor, ale pro zjednodušení je přidat data vložené. 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. V <xref:System.Windows.Controls.Grid> prostředků, přidejte následující <xref:System.Windows.DataTemplate>, který definuje, jak zobrazit data v <xref:System.Windows.Controls.ListBox>. Další informace o šablonách dat najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md). 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. Nahradit existující <xref:System.Windows.Controls.ListBox> s následující XAML. 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     Tato XAML váže <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> ke zdroji dat a použije šablona dat jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. 
  
## <a name="connecting-data-to-controls"></a>Připojení dat k ovládacím prvkům  
 V této části můžete psát kód, který načte aktuální položky, který je vybrán v seznamu uživatelů na stránce ExpenseItHome.xaml a předá jeho odkaz na konstruktoru `ExpenseReportPage` během vytváření instancí. `ExpenseReportPage`Nastaví jeho kontext dat s předaný položky, které je ovládací prvky určené ve ExpenseReportPage.xaml vytvoří vazbu k. 
  
1. Otevřete ExpenseReportPage.xaml.vb nebo ExpenseReportPage.xaml.cs. 
  
2. Přidejte konstruktor, který přebírá objekt, abyste mohli předat data sestavy výdajů vybrané osoby. 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. Otevřete ExpenseItHome.xaml.vb nebo ExpenseItHome.xaml.cs. 
  
4. Změna <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události pro volání konstruktoru new předávání dat sestavy výdajů vybrané osoby. 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a>Data stylů se šablonami dat  
 V této části můžete aktualizovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro každou položku v datech vázaný seznamy pomocí šablon data. 
  
1. Otevřete ExpenseReportPage.xaml. 
  
2. Vytvoření vazby obsah "Název" a "Oddělení" <xref:System.Windows.Controls.Label> vlastnost zdroje elementy, aby příslušná data. Další informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md). 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. Po otevření <xref:System.Windows.Controls.Grid> elementu, přidejte následující data šablon, které definují způsob, jak zobrazit data sestavy výdajů.  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. Používat šablony pro <xref:System.Windows.Controls.DataGrid> sloupce, které zobrazují nákladů data sestavy. 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. Sestavte a spusťte aplikaci. 
  
6. Vyberte osoby a klikněte na **zobrazení** tlačítko. 
  
 Následující obrázek znázorňuje obě stránky aplikace ExpenseIt – ovládací prvky, rozložení, styly, datové vazby a šablony dat použít. 
  
 ![Snímky obrazovky ukázkové ExpenseIt –](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>Doporučené postupy  
 Tato ukázka představuje konkrétní funkce WPF a v důsledku toho nedodrží osvědčené postupy pro vývoj aplikací. Pro komplexní přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikace vývoj osvědčené postupy, podle potřeby najdete v následujících tématech:  
  
-   Usnadnění – [usnadnění – doporučené postupy](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   Zabezpečení – [zabezpečení](../../../../docs/framework/wpf/security-wpf.md)  
  
-   Lokalizace - [WPF globalizace a lokalizace – přehled](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   Výkon – [optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
## <a name="whats-next"></a>Co je další  
 Nyní máte několik technik k dispozici pro vytváření [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Teď byste měli mít široký přehled o základní stavební bloky vázané na data [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikace. Toto téma je rozhodně není vyčerpávající, ale zpravidla nyní také mít smysl pro některé možnosti, které můžete zjistit, na vlastní nad rámec techniky v tomto tématu. 
  
 Další informace o modelech WPF architektura a programování najdete v následujících tématech:  
  
-   [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [Přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)  
  
 Další informace o vytváření aplikací najdete v následujících tématech:  
  
-   [Vývoj aplikací](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)  
  
-   [Přehled vazba dat](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [Grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [Dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Ukázka dat – přehled](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Vytvoření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styles-and-templates.md)
