---
title: 'Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991888"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohatý prostředí pro vytváření aplikací. Nicméně pokud máte v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu značnou investici, může být výhodnější znovu použít alespoň část kódu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v aplikaci, nikoli přepsat od začátku. Nejběžnějším scénářem je, když máte existující model Windows Forms ovládací prvky. V některých případech nemusíte mít ani přístup ke zdrojovému kódu pro tyto ovládací prvky. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje jednoduchý postup pro hostování takových ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci. Například můžete použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro většinu vašeho programování při hostování specializovaných <xref:System.Windows.Forms.DataGridView> ovládacích prvků.  
  
 Tento názorný postup vás provede aplikací, která je hostitelem model Windows Forms složeného ovládacího prvku pro provádění zadávání [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dat v aplikaci. Složený ovládací prvek je zabalen v knihovně DLL. Tento obecný postup se dá rozšířit na složitější aplikace a ovládací prvky. Tento názorný postup je navržený tak, aby byl skoro stejný [jako v podrobném zobrazení a funkci: Hostování složeného ovládacího prvku WPF v](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)model Windows Forms. Hlavním rozdílem je, že hostující scénář je obrácený.  
  
 Návod je rozdělen do dvou částí. První část stručně popisuje implementaci složeného ovládacího prvku model Windows Forms. Druhá část podrobně popisuje, jak hostovat složený ovládací prvek v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci, přijímat události z ovládacího prvku a přistupovat k některým vlastnostem ovládacího prvku.  
  
 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:  
  
- Implementace složeného ovládacího prvku model Windows Forms  
  
- Implementace hostitelské aplikace WPF.  
  
 Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, naleznete v tématu [hostování model Windows Forms složeného ovládacího prvku v UKÁZCE WPF](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Požadavky  

K dokončení tohoto Názorného postupu potřebujete Visual Studio.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementace složeného ovládacího prvku model Windows Forms  
 Model Windows Forms složený ovládací prvek použitý v tomto příkladu je jednoduchý formulář pro zadávání dat. Tento formulář přebírá jméno a adresu uživatele a pak používá vlastní událost k vrácení těchto informací hostiteli. Následující ilustrace znázorňuje vykreslený ovládací prvek.  

 Následující obrázek ukazuje model Windows Forms složený ovládací prvek:  

 ![Snímek obrazovky, který zobrazuje jednoduchý ovládací prvek model Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Spuštění projektu:  
  
1. Spusťte [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a otevřete dialogové okno **Nový projekt** .  
  
2. V kategorii okna vyberte šablonu **Knihovna ovládacích prvků model Windows Forms** .  
  
3. Pojmenujte nový `MyControls`projekt.  
  
4. Pro umístění zadejte pohodlně pojmenovanou složku nejvyšší úrovně, například `WpfHostingWindowsFormsControl`. Později vložíte hostitelskou aplikaci do této složky.  
  
5. Kliknutím na tlačítko **OK** vytvořte projekt. Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.  
  
6. V Průzkumník řešení `UserControl1` přejmenujte `MyControl1`na.  
  
 Projekt by měl mít odkazy na následující systémové knihovny DLL. Pokud některá z těchto knihoven DLL není ve výchozím nastavení součástí, přidejte je do projektu.  
  
- Systém  
  
- System.Data  
  
- System. Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Přidávání ovládacích prvků do formuláře  
 Chcete-li přidat ovládací prvky do formuláře:  
  
- Otevřete `MyControl1` v návrháři.  
  
 Přidejte pět <xref:System.Windows.Forms.Label> ovládacích prvků a jejich <xref:System.Windows.Forms.TextBox> odpovídající ovládací prvky, velikosti a uspořádání tak, jak jsou na předchozím obrázku, ve formuláři. V příkladu <xref:System.Windows.Forms.TextBox> jsou ovládací prvky pojmenovány:  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 Přidejte dva <xref:System.Windows.Forms.Button> ovládací prvky označené jako **OK** a **Zrušit**. V příkladu jsou `btnOK` názvy tlačítek a `btnCancel`, v uvedeném pořadí.  
  
### <a name="implementing-the-supporting-code"></a>Implementace podpůrného kódu  
 Otevřete formulář v zobrazení kódu. Ovládací prvek vrátí shromážděná data do hostitele tím, že vyvyvolává `OnButtonClick` vlastní událost. Data jsou obsažena v objektu argumentu události. Následující kód ukazuje deklaraci události a delegáta.  
  
 Do `MyControl1` třídy přidejte následující kód.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs` Třída obsahuje informace, které mají být vráceny do hostitele.

 Do formuláře přidejte následující třídu.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Když uživatel klikne <xref:System.Windows.Forms.Control.Click> na tlačítko **OK** nebo **Storno** , obslužné rutiny události vytvoří `MyControlEventArgs` objekt, který obsahuje data a vyvolá `OnButtonClick` událost. Jediným rozdílem mezi těmito dvěma obslužnými rutinami je `IsOK` vlastnost argumentu události. Tato vlastnost umožňuje hostiteli určit, na které tlačítko bylo kliknuto. Je nastavená na `true` tlačítko **OK** a `false` pro tlačítko **Storno** . Následující kód ukazuje dvě obslužné rutiny tlačítek.

 Do `MyControl1` třídy přidejte následující kód.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Předání sestavení silnému názvu a sestavení sestavení
 Aby toto sestavení odkazovalo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na aplikaci, musí mít silný název. Chcete-li vytvořit silný název, vytvořte soubor klíče s SN. exe a přidejte jej do projektu.

1. [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] Otevřete příkazový řádek. Provedete to tak, že kliknete na nabídku **Start** a pak vyberete **všechny programy/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**. Tím se spustí okno konzoly s přizpůsobenými proměnnými prostředí.

2. Na příkazovém řádku použijte `cd` příkaz pro přechod do složky projektu.

3. Spuštěním následujícího příkazu vygenerujte soubor klíče s názvem MyControls. snk.

    ```console
    Sn.exe -k MyControls.snk
    ```

4. Chcete-li zahrnout soubor klíče do projektu, klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a potom klikněte na příkaz **vlastnosti**. V Návrháři projektu klikněte na kartu **podepisování** , zaškrtněte políčko **podepsat sestavení** a potom přejděte k souboru klíče.

5. Sestavte řešení. Sestavení vytvoří knihovnu DLL s názvem MyControls. dll.

## <a name="implementing-the-wpf-host-application"></a>Implementace hostitelské aplikace WPF
 Hostitelská aplikace <xref:System.Windows.Forms.Integration.WindowsFormsHost> používá ovládací prvek k hostování `MyControl1`. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aplikace zpracovává `OnButtonClick` událost pro příjem dat z ovládacího prvku. Má také kolekci přepínačů, které umožňují změnit některé z vlastností ovládacího prvku z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Na následujícím obrázku je znázorněna dokončená aplikace.

Následující obrázek ukazuje kompletní aplikaci, včetně ovládacího prvku vloženého do aplikace WPF:

 ![Snímek obrazovky, který zobrazuje ovládací prvek vložený na stránce WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Vytvoření projektu
 Spuštění projektu:

1. Otevřete [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]a vyberte **Nový projekt**.

2. V kategorii okna vyberte šablonu **aplikace WPF** .

3. Pojmenujte nový `WpfHost`projekt.

4. Pro umístění zadejte stejnou složku nejvyšší úrovně, která obsahuje projekt MyControls.

5. Kliknutím na tlačítko **OK** vytvořte projekt.

 Také je nutné přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a další sestavení.

1. Klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a vyberte možnost **Přidat odkaz**.

2. Klikněte na kartu **Procházet** a přejděte do složky, která obsahuje MyControls. dll. Pro tento návod je tato složka MyControls\bin\Debug.

3. Vyberte MyControls. dll a pak klikněte na **OK**.

4. Přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.

### <a name="implementing-the-basic-layout"></a>Implementace základního rozložení
 Hostitelská aplikace je implementována v souboruMainWindow.XAML.[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Tento soubor obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód, který definuje rozložení a hostuje ovládací prvek model Windows Forms. Aplikace je rozdělená do tří oblastí:

- Panel **vlastností ovládacího prvku** , který obsahuje kolekci přepínačů, které lze použít k úpravě různých vlastností hostovaného ovládacího prvku.

- **Data z ovládacích** panelů, která obsahují několik <xref:System.Windows.Controls.TextBlock> prvků, které zobrazují data vrácená z hostovaného ovládacího prvku.

- Samotný hostující ovládací prvek.

 Základní rozložení je znázorněno v následujícím kódu XAML. Kód, který je potřeba pro hostování `MyControl1` , je v tomto příkladu vynechán, ale bude popsán později.

 Nahraďte XAML v souboru MainWindow. XAML následujícím. Pokud používáte Visual Basic, změňte třídu na `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 První <xref:System.Windows.Controls.StackPanel> prvek obsahuje několik <xref:System.Windows.Controls.RadioButton> sad ovládacích prvků, které umožňují upravit různé výchozí vlastnosti hostovaného ovládacího prvku. Následováno <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvkem, který je hostitelem `MyControl1`. Konečný <xref:System.Windows.Controls.StackPanel> element obsahuje několik <xref:System.Windows.Controls.TextBlock> prvků, které zobrazují data, která jsou vrácena hostovaným ovládacím prvkem. Pořadí prvků a <xref:System.Windows.Controls.DockPanel.Dock%2A> nastavení atributů a <xref:System.Windows.FrameworkElement.Height%2A> vloží hostovaný ovládací prvek do okna bez mezer nebo zkreslení.

#### <a name="hosting-the-control"></a>Hostování ovládacího prvku
 Následující upravená verze předchozího XAML se zaměřuje na prvky, které jsou nutné pro hostování `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `MyControls` Atribut mapování `xmlns` oboru názvů vytvoří odkaz na obor názvů, který obsahuje hostovaný ovládací prvek. Toto mapování umožňuje znázornit `MyControl1` v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.

 Dva prvky v jazyce XAML zpracovávají hostování:

- `WindowsFormsHost`představuje prvek, který umožňuje hostování ovládacího prvku model Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v aplikaci. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

- `mcl:MyControl1`, který představuje `MyControl1`, je přidán <xref:System.Windows.Forms.Integration.WindowsFormsHost> do podřízené kolekce elementu. V důsledku toho je tento ovládací prvek model Windows Forms vykreslen jako součást [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna a můžete komunikovat s ovládacím prvkem z aplikace.

### <a name="implementing-the-code-behind-file"></a>Implementace souboru kódu na pozadí
 Soubor kódu na pozadí MainWindow. XAML. vb nebo MainWindow.XAML.cs obsahuje kód procedurální, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] popsané v předchozí části. Primární úlohy jsou:

- Připojení obslužné rutiny události k `MyControl1` `OnButtonClick` události.

- Změna různých vlastností `MyControl1`na základě toho, jak jsou nastaveny kolekce přepínačů.

- Zobrazení dat shromažďovaných ovládacím prvkem.

#### <a name="initializing-the-application"></a>Inicializuje se aplikace.
 Inicializační kód je obsažen v obslužné rutině události pro <xref:System.Windows.FrameworkElement.Loaded> událost okna a připojí obslužnou rutinu události k `OnButtonClick` události ovládacího prvku.

 V souboru MainWindow. XAML. vb nebo MainWindow.XAML.cs přidejte do `MainWindow` třídy následující kód.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1` `MyControl1`Vzhledem k tomu, že <xref:System.Windows.Forms.Integration.WindowsFormsHost> popsaný dříve přidaný do kolekce podřízených elementů elementu, můžete přetypovat na element a získat odkaz na. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Pak můžete použít tento odkaz k připojení obslužné rutiny `OnButtonClick`události.

 Kromě poskytnutí odkazu na samotný <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek zpřístupňuje řadu vlastností ovládacího prvku, které lze manipulovat z aplikace. Inicializační kód přiřadí tyto hodnoty privátním globálním proměnným pro pozdější použití v aplikaci.

 Aby bylo možné snadno získat přístup k typům v `MyControls` knihovně DLL, přidejte následující `Imports` příkaz `using` nebo na začátek souboru.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Zpracování události OnButtonClick
 `MyControl1`vyvolá událost `OnButtonClick` , když uživatel klikne na kterékoli z tlačítek ovládacího prvku.

 Do `MainWindow` třídy přidejte následující kód.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Data v textových polích jsou zabalena do `MyControlEventArgs` objektu. Pokud uživatel klikne na tlačítko **OK** , obslužná rutina události extrahuje data a zobrazí je na panelu níže `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Úprava vlastností ovládacího prvku
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element zveřejňuje několik výchozích vlastností hostovaného ovládacího prvku. V důsledku toho můžete změnit vzhled ovládacího prvku tak, aby odpovídal stylu vaší aplikace přesněji. Sady přepínačů na levém panelu umožňují uživateli upravovat několik vlastností barev a písem. Každá sada tlačítek obsahuje obslužnou rutinu pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která detekuje výběry přepínačů uživatele a mění odpovídající vlastnost ovládacího prvku.

 Do `MainWindow` třídy přidejte následující kód.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Sestavte a spusťte aplikaci. Do složeného ovládacího prvku model Windows Forms přidejte nějaký text a pak klikněte na **OK**. Text se zobrazí v popiscích. Kliknutím na jiné přepínače zobrazíte efekt na ovládacím prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku model Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF v model Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
