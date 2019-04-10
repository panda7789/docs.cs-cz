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
ms.openlocfilehash: 90d0e2f3c6ebab070809a4813c87da3539fd14f1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337848"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte značné investice [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu, může být efektivnější opakovaně používat alespoň některé tohoto kódu v vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace namísto jeho přepsání úplně od začátku. Nejběžnější scénář je, pokud máte existující ovládací prvky Windows Forms. V některých případech nemusí mít i přístup ke zdrojovému kódu pro tyto ovládací prvky. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje jednoduchý postup pro hostování těchto ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Například můžete použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] u většiny vašich programování při hostování vaší specializované <xref:System.Windows.Forms.DataGridView> ovládacích prvků.  
  
 Tento názorný postup vás provede jednotlivými kroky, který je hostitelem složený ovládací prvek Windows Forms pro zadávání dat v aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Složený ovládací prvek je zabalený ve knihovny DLL. Tento obecný postup je možné rozšířit na složitější aplikace a ovládací prvky. Tento názorný postup je navržený jako téměř identické v vzhled a funkce, které [názorný postup: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md). Hlavní rozdíl je, že je obrácený scénáři hostování.  
  
 Návod je rozdělen do dvou částí. V první části stručně popisuje implementaci složeného ovládacího prvku Windows Forms. Druhá část podrobně probírají postupy hostování složeného ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace přijímat události z ovládacího prvku a přístup k některé z vlastností ovládacího prvku.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Implementace složeného ovládacího prvku Windows Forms.  
  
-   Implementace hostitelskou aplikaci WPF.  
  
 Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [hostování Windows Forms složeného ovládacího prvku v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159999).  
  
## <a name="prerequisites"></a>Požadavky  

Visual Studio k dokončení tohoto návodu potřebujete.
  
## <a name="implementing-the-windows-forms-composite-control"></a>Implementace složeného ovládacího prvku Windows Forms  
 Složeného ovládacího prvku Windows Forms použitý v tomto příkladu je jednoduché zadávání dat formuláře. Tento formulář přebírá uživatelské jméno a adresa a pak se vraťte tyto informace do hostitele používá vlastní událost. Následující obrázek ukazuje ovládací prvek vykreslené.  

 Následující obrázek ukazuje složeného ovládacího prvku formuláře Windows:  

 ![Snímek obrazovky, který ukazuje jednoduchý ovládací prvek Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Ke spuštění projektu:  
  
1. Spuštění [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.  
  
2. V okně kategorii, vyberte **Knihovna ovládacích prvků Windows Forms** šablony.  
  
3. Název nového projektu `MyControls`.  
  
4. K umístění, zadejte jednoduše pojmenované složku nejvyšší úrovně, například `WpfHostingWindowsFormsControl`. Hostitelská aplikace později, budou umístili do této složky.  
  
5. Klikněte na tlačítko **OK** pro vytvoření projektu. Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.  
  
6. V Průzkumníku řešení, přejmenujte `UserControl1` k `MyControl1`.  
  
 Váš projekt by měl zahrnovat odkazy na tyto systémové knihovny DLL. Pokud některý z těchto knihoven DLL nejsou zahrnuty ve výchozím nastavení, můžete je přidáte do projektu.  
  
-   Systém  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>Přidávání ovládacích prvků do formuláře  
 Chcete-li přidat ovládací prvky do formuláře:  
  
-   Otevřít `MyControl1` v návrháři.  
  
 Přidat pět <xref:System.Windows.Forms.Label> ovládací prvky a jejich odpovídající <xref:System.Windows.Forms.TextBox> ovládací prvky, velikost a uspořádání stejně jako v předchozí ilustraci ve formuláři. V tomto příkladu <xref:System.Windows.Forms.TextBox> jsou pojmenovány ovládacích prvků:  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 Přidejte dva <xref:System.Windows.Forms.Button> kontrolní prvky **OK** a **zrušit**. V tomto příkladu jsou názvy tlačítek `btnOK` a `btnCancel`v uvedeném pořadí.  
  
### <a name="implementing-the-supporting-code"></a>Implementace podpůrný kód  
 Otevřete formulář v zobrazení kódu. Ovládací prvek vrátí shromážděná data do svého hostitele vyvoláním vlastní `OnButtonClick` událostí. Data je obsažen v objektu argumentu události. Následující kód ukazuje deklaraci události a delegátem.  
  
 Přidejte následující kód, který `MyControl1` třídy.  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs` Třída obsahuje informace, který se má vrátit k hostiteli.

 Přidejte následující třídu do formuláře.

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 Pokud uživatel klikne **OK** nebo **zrušit** tlačítko, <xref:System.Windows.Forms.Control.Click> vytvoření obslužné rutiny událostí `MyControlEventArgs` objekt, který obsahuje data a vyvolá `OnButtonClick` událostí. Jediný rozdíl mezi dvě obslužné rutiny je argument události `IsOK` vlastnost. Tato vlastnost umožňuje určit, které tlačítko došlo ke kliknutí na hostiteli. Je nastavený na `true` pro **OK** tlačítko, a `false` pro **zrušit** tlačítko. Následující kód ukazuje dvě tlačítka obslužné rutiny.

 Přidejte následující kód, který `MyControl1` třídy.

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>Poskytuje tak sestavení silným názvem a vytváření sestavení
 Pro toto sestavení může odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, musí mít silný název. Chcete-li vytvořit silným názvem, vytvořit soubor klíče se Sn.exe a přidejte do projektu.

1. Otevřít [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] příkazového řádku. Chcete-li tak učinit, klikněte na tlačítko **spustit** nabídky a pak vyberte **všechny programy nebo Microsoft Studio 2010 a Visual Studio Tools/Visual příkazový řádek Visual Studio**. Otevře se okno konzoly s proměnnými přizpůsobené prostředí.

2. Na příkazovém řádku, použijte `cd` příkazu přejděte do složky vašeho projektu.

3. Generovat soubor s klíčem s názvem MyControls.snk spuštěním následujícího příkazu.

    ```
    Sn.exe -k MyControls.snk
    ```

4. Zahrnout soubor klíče ve vašem projektu, klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a potom klikněte na tlačítko **vlastnosti**. V Návrháři projektu, klikněte na tlačítko **podepisování** kartu, vyberte **podepsat sestavení** zaškrtněte políčko a potom přejděte k vašemu souboru s klíčem.

5. Sestavte řešení. Sestavení vytvoří knihovnu DLL s názvem MyControls.dll.

## <a name="implementing-the-wpf-host-application"></a>Implementace hostitele aplikace WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hostovat aplikace používá <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku na hostitele `MyControl1`. Aplikace zpracovává `OnButtonClick` události přijímat data z ovládacího prvku. Má také kolekce, která vám umožní změnit některé vlastnosti ovládacího prvku z přepínačů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Následující obrázek ukazuje dokončenou aplikaci.

Následující obrázek ukazuje hotové aplikace včetně ovládací prvek vložený do aplikace WPF:

 ![Snímek obrazovky zobrazující ovládací prvek vložený na stránce WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>Vytvoření projektu
 Ke spuštění projektu:

1. Otevřít [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]a vyberte **nový projekt**.

2. V okně kategorii, vyberte **aplikace WPF** šablony.

3. Název nového projektu `WpfHost`.

4. Pro umístění zadejte stejnou složku nejvyšší úrovně, obsahující projekt MyControls.

5. Klikněte na tlačítko **OK** pro vytvoření projektu.

 Musíte také přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a jiná sestavení.

1. Klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a vyberte **přidat odkaz**.

2. Klikněte na tlačítko **Procházet** kartu a přejděte do složky, která obsahuje MyControls.dll. V tomto návodu je této složky MyControls\bin\Debug.

3. Vyberte MyControls.dll a potom klikněte na tlačítko **OK**.

4. Přidáte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.

### <a name="implementing-the-basic-layout"></a>Implementace základní rozložení
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hostitele je příslušná aplikace implementovaná v souboru MainWindow.xaml. Tento soubor obsahuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód, který definuje rozložení a hostuje ovládací prvek Windows Forms. Aplikaci je rozdělené do tří oblastí:

-   **Vlastností ovládacího prvku** panel, který obsahuje kolekci prvků přepínačů, můžete použít k úpravě různé vlastnosti objektu hostovaného ovládacího prvku.

-   **Dat z ovládacího prvku** panel, který obsahuje několik <xref:System.Windows.Controls.TextBlock> prvky, které zobrazují data vrácená z hostovaného ovládacího prvku.

-   Hostované samotný ovládací prvek.

 Základní rozložení je znázorněno v následující XAML. Kód, který je nutný k hostiteli `MyControl1` vynecháte z tohoto příkladu, ale bude prodiskutována později.

 XAML v souboru MainWindow.xaml nahraďte následujícím kódem. Pokud používáte Visual Basic, změňte třídu `x:Class="MainWindow"`.

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 První <xref:System.Windows.Controls.StackPanel> prvek obsahuje několik sad <xref:System.Windows.Controls.RadioButton> ovládací prvky, které vám umožní změnit různé výchozí vlastnosti hostovaného ovládacího prvku. Který je následován <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, které hostitele `MyControl1`. Finální <xref:System.Windows.Controls.StackPanel> prvek obsahuje několik <xref:System.Windows.Controls.TextBlock> prvky, které zobrazují data, která je vrácena hostovaného ovládacího prvku. Pořadí prvků a <xref:System.Windows.Controls.DockPanel.Dock%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení atributů vložit hostovaného ovládacího prvku do okna s žádné mezery ani narušení.

#### <a name="hosting-the-control"></a>Hostování ovládacího prvku
 Následující upravená verze předchozího XAML se zaměřuje na prvky, které jsou potřeba k hostiteli `MyControl1`.

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `xmlns` Vytvoří odkaz na atribut mapování oboru názvů `MyControls` obor názvů, který obsahuje hostovaného ovládacího prvku. Toto mapování umožňuje představují `MyControl1` v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.

 Dva prvky v XAML zpracování hostování:

-   `WindowsFormsHost` představuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, který můžete použít k hostování ovládacího prvku Windows Forms v umožňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.

-   `mcl:MyControl1`, která představuje `MyControl1`, se přidá do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené kolekce. V důsledku toho je tento ovládací prvek Windows Forms vykreslit jako součást [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna a může komunikovat s ovládacím prvkem z aplikace.

### <a name="implementing-the-code-behind-file"></a>Implementace souboru kódu na pozadí
 Použití modelu code-behind souboru, soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs, obsahuje kód procedury, která implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] popsané v předchozí části. Primární úlohy jsou:

-   Připojení obslužnou rutinu události pro `MyControl1`společnosti `OnButtonClick` událostí.

-   Úprava různé vlastnosti objektu `MyControl1`podle nastavení kolekce přepínačů.

-   Zobrazení dat shromažďovaných ovládacího prvku.

#### <a name="initializing-the-application"></a>Inicializace aplikace
 Inicializační kód je obsažen v obslužné rutině události pro okna <xref:System.Windows.FrameworkElement.Loaded> událostí a připojí obslužnou rutinu události ovládacího prvku `OnButtonClick` událostí.

 V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs přidejte následující kód, který `MainWindow` třídy.

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 Protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] popsané dříve přidanými `MyControl1` k <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podřízené elementu kolekce, můžete přetypovat <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> získat odkaz na `MyControl1`. Potom můžete tento odkaz připojte obslužné rutiny události pro `OnButtonClick`.

 Kromě toho, že odkaz na tento ovládací prvek, <xref:System.Windows.Forms.Integration.WindowsFormsHost> vystavuje určitý počet vlastností ovládacího prvku, které můžete upravit z aplikace. Inicializační kód přiřadí tyto hodnoty privátní globálních proměnných pro pozdější použití v aplikaci.

 Takže můžete snadno přístup k typům v `MyControls` knihovny DLL, přidejte následující `Imports` nebo `using` příkaz do horní části souboru.

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>Zpracování události OnButtonClick
 `MyControl1` Vyvolá `OnButtonClick` událost, když uživatel klikne na tlačítko buď z tlačítek ovládacího prvku.

 Přidejte následující kód, který `MainWindow` třídy.

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 Data do textových polí je zabalena do `MyControlEventArgs` objektu. Pokud uživatel klikne **OK** tlačítko, obslužná rutina události, extrahuje data a zobrazí jej v panelu níže `MyControl1`.

#### <a name="modifying-the-controls-properties"></a>Úprava vlastností ovládacího prvku
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element zpřístupňuje řadu hostované ovládací prvek výchozí vlastnosti. V důsledku toho můžete změnit vzhled ovládacího prvku tak, aby lépe odpovídaly styl vaší aplikace. Sadu tlačítek možností v levém panelu povolit uživateli změnit několik vlastností barev a písma. Má obslužné rutiny pro každou sadu tlačítek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která zjistí tlačítko Možnosti uživatele a změní vlastnost odpovídající na ovládacím prvku.

 Přidejte následující kód, který `MainWindow` třídy.

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 Sestavte a spusťte aplikaci. Přidejte nějaký text do složeného ovládacího prvku Windows Forms a potom klikněte na tlačítko **OK**. Text se zobrazí v popiscích. Klikněte na různé přepínače a vidět její účinek na ovládacím prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms ve WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
