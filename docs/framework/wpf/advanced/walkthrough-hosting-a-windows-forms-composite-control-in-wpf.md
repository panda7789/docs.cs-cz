---
title: 'Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 5868ee8c5b781d5af75349a5950f7e1e1680d74d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte významné investice [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu, může být efektivnější opakovaně používat alespoň některé tento kód v vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace místo přepsání od začátku. Nejběžnější scénáře je, pokud máte existující Windows Forms – ovládací prvky. V některých případech nemusí mít ani přístup ke zdrojovému kódu pro tyto ovládací prvky. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Poskytuje přehledné postup pro hostování těchto ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Například můžete použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro většinu vaše programování při hostování vaší specializované <xref:System.Windows.Forms.DataGridView> ovládací prvky.  
  
 Tento názorný postup vás provede jednotlivými kroky aplikace, který je hostitelem složeného ovládacího prvku Windows Forms k zadávání dat v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Knihovny DLL je součástí složeného ovládacího prvku. Tento postup Obecné lze rozšířit na složitější aplikace a ovládací prvky. Tento názorný postup je navržený jako téměř shodná v vzhled a funkce [návod: hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Základní rozdíl je, že je obrácený scénáři pro hostování.  
  
 Průvodce je rozdělené na dvě části. V první části stručně popisuje provádění složeného ovládacího prvku Windows Forms. Druhá část podrobně probírají řešení pro hostování složeného ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, přijímat události z ovládacího prvku a získat přístup k některým vlastností ovládacího prvku.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Implementace složeného ovládacího prvku Windows Forms.  
  
-   Implementace hostitelskou aplikaci WPF.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [hostování ovládacího prvku Windows Forms složené v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementace složeného ovládacího prvku Windows Forms  
 Složeného ovládacího prvku Windows Forms použité v tomto příkladu je jednoduchý zadávání dat formuláře. Tento formulář přebírá uživatelské jméno a adresa a pak používá vlastní události vrátit tyto informace k hostiteli. Následující obrázek znázorňuje vykreslené ovládacího prvku.  
  
 ![Ovládací prvek Windows Forms jednoduché](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")  
Složeného ovládacího prvku Windows Forms  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Spuštění projektu:  
  
1.  Spusťte [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.  
  
2.  V okně kategorii, vyberte **knihovny ovládacích prvků Windows Forms** šablony.  
  
3.  Název nového projektu `MyControls`.  
  
4.  K umístění, zadejte pohodlně složka s názvem nejvyšší úrovně, jako například `WpfHostingWindowsFormsControl`. Později umístíte hostitelskou aplikaci v této složce.  
  
5.  Klikněte na tlačítko **OK** a vytvořte tak projekt. Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.  
  
6.  V Průzkumníku řešení, přejmenujte `UserControl1` k `MyControl1`.  
  
 Projekt by měl mít odkazy na následující systémové knihovny DLL. Pokud některý z těchto knihoven DLL se ve výchozím nastavení neobsahuje, přidejte je do projektu.  
  
-   Systém  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Přidávání ovládacích prvků do formuláře  
 K přidávání ovládacích prvků formuláře:  
  
-   Otevřete `MyControl1` v návrháři.  
  
 Přidat pět <xref:System.Windows.Forms.Label> ovládací prvky a jejich odpovídajících <xref:System.Windows.Forms.TextBox> ovládací prvky, velikosti a uspořádané jako v předchozí ilustraci na formuláři. V příkladu <xref:System.Windows.Forms.TextBox> jsou pojmenované ovládací prvky:  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 Přidejte dva <xref:System.Windows.Forms.Button> ovládací prvky s názvem bez přípony **OK** a **zrušit**. V příkladu jsou názvy tlačítko `btnOK` a `btnCancel`, v uvedeném pořadí.  
  
### <a name="implementing-the-supporting-code"></a>Implementace podpůrné kódu  
 Otevřete formulář v zobrazení kódu. Ovládací prvek vrátí shromážděná data do jeho hostitel zvýšením vlastní `OnButtonClick` událostí. Data jsou obsaženy v objektu argumentu události. Následující kód ukazuje deklaraci události a delegáta.  
  
 Přidejte následující kód, který `MyControl1` třídy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 `MyControlEventArgs` Třída obsahuje informace, které mají být vráceny do hostitele.  
  
 Přidejte následující třídy formuláře.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 Když uživatel klikne **OK** nebo **zrušit** tlačítko <xref:System.Windows.Forms.Control.Click> vytvoření obslužné rutiny událostí `MyControlEventArgs` objekt, který obsahuje data a vyvolá `OnButtonClick` událostí. Jediným rozdílem mezi dvě obslužné rutiny je argumentu události `IsOK` vlastnost. Tato vlastnost umožňuje určit, které tlačítko bylo kliknuto hostiteli. Je nastaven na hodnotu `true` pro **OK** tlačítko a `false` pro **zrušit** tlačítko. Následující kód ukazuje dva tlačítko obslužné rutiny.  
  
 Přidejte následující kód, který `MyControl1` třídy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Poskytnutí sestavení silným názvem a vytváření sestavení  
 Pro toto sestavení do odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, musí mít silným názvem. Chcete-li vytvořit silným názvem, vytvořte soubor klíče s Sn.exe a přidejte do projektu.  
  
1.  Otevřete [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] příkazového řádku. Chcete-li to provést, klikněte na tlačítko **spustit** nabídce a potom vyberte **všechny programy nebo Microsoft Visual Studio 2010 nebo Visual Studio nástroje/Visual Studio – příkazový řádek**. Spustí se do okna konzoly s proměnné přizpůsobené prostředí.  
  
2.  Na příkazovém řádku použít `cd` příkazu přejděte do složky projektu.  
  
3.  Generovat soubor klíče s názvem MyControls.snk spuštěním následujícího příkazu.  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  Zahrnout soubor klíče ve vašem projektu, klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a pak klikněte na tlačítko **vlastnosti**. V Návrháři projektu, klikněte na tlačítko **podpisování** vyberte **podepsání sestavení** zaškrtněte políčko a potom vyhledejte soubor s klíčem.  
  
5.  Sestavte řešení. Sestavení způsobí knihovny DLL s názvem MyControls.dll.  
  
## <a name="implementing-the-wpf-host-application"></a>Implementace hostitelskou aplikaci WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hostitele používá aplikace <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení hostitele `MyControl1`. Obslužné rutiny aplikace `OnButtonClick` událostí pro příjem dat z ovládacího prvku. Je také kolekce tlačítek možností, které vám umožní změnit některé vlastnosti ovládacího prvku z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Následující obrázek znázorňuje dokončení aplikace.  
  
 ![Ovládací prvek vložený na stránce WPF](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")  
Hotové aplikace zobrazuje ovládacího prvku vloženy do aplikace WPF  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Spuštění projektu:  
  
1.  Otevřete [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]a vyberte **nový projekt**.  
  
2.  V okně kategorii, vyberte **aplikaci WPF** šablony.
  
3.  Název nového projektu `WpfHost`.  
  
4.  K umístění zadejte stejné nejvyšší úrovně složku, která obsahuje MyControls projektu.  
  
5.  Klikněte na tlačítko **OK** a vytvořte tak projekt.  
  
 Také je nutné přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a jiné sestavení.  
  
1.  Název projektu v Průzkumníku řešení klikněte pravým tlačítkem a vyberte **přidat odkaz na**.  
  
2.  Klikněte **Procházet** kartě a přejděte do složky, která obsahuje MyControls.dll. V tomto návodu je této složky MyControls\bin\Debug.  
  
3.  Vyberte MyControls.dll a pak klikněte na tlačítko **OK**.  
  
4.  Přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.  
  
### <a name="implementing-the-basic-layout"></a>Implementace základní rozložení  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hostitele aplikací je implementována ve MainWindow.xaml. Tento soubor obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód, který definuje rozložení a hostitelem ovládacího prvku Windows Forms. Aplikace je rozdělené do tří oblastí:  
  
-   **– Vlastnosti ovládacích prvků** panel, který obsahuje kolekci přepínačů, který můžete použít k úpravě různé vlastnosti hostované ovládacího prvku.  
  
-   **Dat z ovládacího prvku** panel, který obsahuje několik <xref:System.Windows.Controls.TextBlock> elementy, které zobrazují data vrácená z hostovaného ovládacího prvku.  
  
-   Hostované samotném ovládacím prvku.  
  
 Základní rozložení se zobrazí v následujícím XAML. Kód, který je nutný k hostiteli `MyControl1` v tomto příkladu vynecháte, ale bude probírat později.  
  
 Nahraďte XAML v MainWindow.xaml následující. Pokud používáte Visual Basic, změňte třídu k `x:Class="MainWindow"`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 První <xref:System.Windows.Controls.StackPanel> element obsahuje několik sad <xref:System.Windows.Controls.RadioButton> ovládací prvky, které vám umožní změnit různé výchozí vlastnosti hostované ovládacího prvku. Které následuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, které hostitele `MyControl1`. Konečné <xref:System.Windows.Controls.StackPanel> element obsahuje několik <xref:System.Windows.Controls.TextBlock> elementy, které zobrazují data, která je vrácena hostované řízení. Řazení elementů a <xref:System.Windows.Controls.DockPanel.Dock%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení atributů vložit hostovaného ovládacího prvku do okna s žádné mezery ani narušení.  
  
#### <a name="hosting-the-control"></a>Hostování ovládacího prvku  
 Následující upravenou verzi předchozí XAML se zaměřuje na elementy, které jsou potřebné k hostiteli `MyControl1`.  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 `xmlns` Vytvoří odkaz na atribut mapování oboru názvů `MyControls` obor názvů, který obsahuje hostovaného ovládacího prvku. Toto mapování umožňuje představují `MyControl1` v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.  
  
 Dva elementy v XAML zpracování, který je hostitelem:  
  
-   `WindowsFormsHost` představuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, který umožňuje hostování ovládacího prvku Windows Forms v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
-   `mcl:MyControl1`, které představuje `MyControl1`, je přidán do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené kolekce. V důsledku toho je tento ovládací prvek Windows Forms vykresleno jako součást [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okno a může komunikovat s ovládacím prvkem z aplikace.  
  
### <a name="implementing-the-code-behind-file"></a>Implementace souboru kódu na pozadí  
 Soubor modelu code-behind, MainWindow.xaml.vb nebo MainWindow.xaml.cs, obsahuje procedurální kód, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] popsané v předchozí části. Primární úlohy jsou:  
  
-   Připojení obslužné rutiny události pro `MyControl1`na `OnButtonClick` událostí.  
  
-   Úprava vlastností různých `MyControl1`, závislosti na tom, jak jsou nastavené kolekci přepínačů.  
  
-   Zobrazení dat shromažďovaných pomocí ovládacího prvku.  
  
#### <a name="initializing-the-application"></a>Inicializace aplikace  
 Inicializace kódu je součástí obslužné rutiny události pro okna <xref:System.Windows.FrameworkElement.Loaded> událostí a připojí obslužné rutiny události ovládacího prvku `OnButtonClick` událostí.  
  
 V MainWindow.xaml.vb nebo MainWindow.xaml.cs, přidejte následující kód, který `MainWindow` třídy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] popsané dříve přidané `MyControl1` k <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené elementu kolekce, můžete převést <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> získat odkaz na `MyControl1`. Pak můžete tento odkaz připojit obslužné rutiny události pro `OnButtonClick`.  
  
 Kromě odkaz na tento ovládací prvek, <xref:System.Windows.Forms.Integration.WindowsFormsHost> vystavuje určitý počet vlastností ovládacího prvku, které můžete upravit z aplikace. Kód inicializace přiřadí tyto hodnoty privátní globálních proměnných pro pozdější použití v aplikaci.  
  
 Tak, aby měli snadný přístup typy v `MyControls` knihovny DLL, přidejte následující `Imports` nebo `using` příkaz do horní části souboru.  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a>Zpracování události OnButtonClick  
 `MyControl1` Vyvolá `OnButtonClick` událost, když uživatel klikne na některý z ovládacího prvku tlačítka.  
  
 Přidejte následující kód, který `MainWindow` třídy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 Data v textových polích je zabalit do `MyControlEventArgs` objektu. Pokud uživatel klikne **OK** tlačítko, obslužné rutiny události extrahuje data a zobrazí v panelu níže `MyControl1`.  
  
#### <a name="modifying-the-controls-properties"></a>Úprava vlastností ovládacího prvku  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element zveřejňuje řadu hostované ovládacího prvku výchozí vlastnosti. V důsledku toho můžete změnit vzhled ovládacího prvku tak, aby lépe odpovídaly styl vaší aplikace. Sady tlačítek možností v levém panelu povolit uživatelům změnit několik vlastností barev a písem. Má obslužná rutina pro každou sadu tlačítek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která zjišťuje uživatele možnost tlačítko Výběr a změní odpovídající vlastnost na ovládací prvek.  
  
 Přidejte následující kód, který `MainWindow` třídy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Sestavte a spusťte aplikaci. Přidejte nějaký text složeného ovládacího prvku Windows Forms a pak klikněte na tlačítko **OK**. Text se zobrazí v štítky. Klikněte na tlačítko různé přepínače zobrazíte vliv na ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrhář WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
