---
title: Hostování složeného ovládacího prvku WPF v model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 59243e1810757ff0ff58a60ac3eb007bbc227be0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742682"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Návod: Hostování kompozitního ovládacího prvku WPF v rozhraní Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohatou prostředí pro vytváření aplikací. Pokud ale v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu máte významnou investici, může být efektivnější rozlišit vaši stávající aplikaci [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] místo toho, aby se přepsala od začátku. Běžným scénářem je, že chcete vložit jeden nebo více ovládacích prvků implementovaných pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci aplikace model Windows Forms. Další informace o přizpůsobení ovládacích prvků WPF naleznete v tématu [Control Customizing](../controls/control-customization.md).  
  
 Tento názorný postup vás provede aplikací, která je hostitelem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku, aby prováděla datovou položku v aplikaci model Windows Forms. Složený ovládací prvek je zabalen v knihovně DLL. Tento obecný postup se dá rozšířit na složitější aplikace a ovládací prvky. Tento návod je téměř identický v zobrazení a funkcionalita pro [Návod: hostování model Windows Forms složeného ovládacího prvku v](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)subsystému WPF. Hlavním rozdílem je, že hostující scénář je obrácený.  
  
 Návod je rozdělen do dvou částí. První část stručně popisuje implementaci složeného ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Druhá část podrobně popisuje, jak hostovat složený ovládací prvek v aplikaci model Windows Forms, přijímat události z ovládacího prvku a přistupovat k některým vlastnostem ovládacího prvku.  
  
 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:  
  
- Implementace složeného ovládacího prvku WPF  
  
- Implementace aplikace model Windows Forms Host.  
  
 Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, naleznete [v tématu hostování složeného ovládacího prvku WPF v model Windows Forms Sample](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Požadavky  

K dokončení tohoto Názorného postupu potřebujete Visual Studio.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementace složeného ovládacího prvku WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složený ovládací prvek použitý v tomto příkladu je jednoduchý formulář pro zadávání dat, který přebírá jméno a adresu uživatele. Když uživatel klikne na jedno ze dvou tlačítek, aby označovali, že úkol je dokončen, ovládací prvek vyvolá vlastní událost, která vrátí tyto informace hostiteli. Následující ilustrace znázorňuje vykreslený ovládací prvek. 

 Následující obrázek znázorňuje složený ovládací prvek WPF: 

 ![Snímek obrazovky, který zobrazuje jednoduchý ovládací prvek WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Spuštění projektu:  
  
1. Spusťte Visual Studio a otevřete dialogové okno **Nový projekt** .  
  
2. V kategorii C# vizuál a kategorie systému Windows vyberte šablonu **Knihovna uživatelských ovládacích prvků WPF** .  
  
3. Pojmenujte nový projekt `MyControls`.  
  
4. Pro umístění zadejte pohodlně pojmenovanou složku nejvyšší úrovně, například `WindowsFormsHostingWpfControl`. Později vložíte hostitelskou aplikaci do této složky.  
  
5. Kliknutím na tlačítko **OK** vytvořte projekt. Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.  
  
6. V Průzkumník řešení přejmenujte `UserControl1` na `MyControl1`.  
  
 Projekt by měl mít odkazy na následující systémové knihovny DLL. Pokud některá z těchto knihoven DLL není ve výchozím nastavení součástí, přidejte je do projektu.  
  
- PresentationCore  
  
- PresentationFramework  
  
- Systém  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>Vytvoření uživatelského rozhraní  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pro složený ovládací prvek je implementován pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Složený ovládací prvek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sestává z pěti <xref:System.Windows.Controls.TextBox> prvků. Každý prvek <xref:System.Windows.Controls.TextBox> má přidružený <xref:System.Windows.Controls.TextBlock> prvek, který slouží jako jmenovka. V dolní části jsou k dispozici dva prvky <xref:System.Windows.Controls.Button>, **OK** a **Zrušit**. Když uživatel klikne na tlačítko, ovládací prvek vyvolá vlastní událost, která vrátí informace hostiteli.  
  
#### <a name="basic-layout"></a>Základní rozložení  
 Různé prvky [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jsou obsaženy v <xref:System.Windows.Controls.Grid> elementu. Můžete použít <xref:System.Windows.Controls.Grid> k uspořádání obsahu složeného ovládacího prvku v podstatě stejným způsobem, jako byste používali `Table` prvek ve formátu HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má také prvek <xref:System.Windows.Documents.Table>, ale <xref:System.Windows.Controls.Grid> je jednodušší a lepší pro jednoduché úlohy rozložení.  
  
 Následující kód XAML znázorňuje základní rozložení. Tento kód XAML definuje celkovou strukturu ovládacího prvku zadáním počtu sloupců a řádků v prvku <xref:System.Windows.Controls.Grid>.  
  
 V souboru MyControl1. xaml nahraďte existující kód XAML následujícím XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Přidání elementů TextBlock a TextBox do mřížky  
 Do mřížky umístíte prvek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nastavením atributů <xref:System.Windows.Controls.Grid.RowProperty> a <xref:System.Windows.Controls.Grid.ColumnProperty> na příslušné číslo řádku a sloupce. Mějte na paměti, že číslování řádků a sloupců je založené na nule. Můžete mít prvek span více sloupců nastavením jeho <xref:System.Windows.Controls.Grid.ColumnSpanProperty> atributu. Další informace o <xref:System.Windows.Controls.Grid> prvky naleznete v tématu [Create a Grid element](../controls/how-to-create-a-grid-element.md).  
  
 Následující kód XAML ukazuje <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> prvky složeného ovládacího prvku s jejich atributy <xref:System.Windows.Controls.Grid.RowProperty> a <xref:System.Windows.Controls.Grid.ColumnProperty>, které jsou nastaveny tak, aby prvky správně umístily do mřížky.  
  
 V souboru MyControl1. XAML přidejte následující kód XAML do prvku <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Určení stylu prvků uživatelského rozhraní  
 Mnohé prvky formuláře pro zadávání dat mají podobný vzhled, což znamená, že mají stejné nastavení pro několik jejich vlastností. Místo nastavování atributů každého elementu samostatně, předchozí XAML používá <xref:System.Windows.Style> prvky pro definování standardních nastavení vlastností pro třídy prvků. Tento přístup omezuje složitost ovládacího prvku a umožňuje změnit vzhled více prvků prostřednictvím atributu s jedním stylem.  
  
 Prvky <xref:System.Windows.Style> jsou obsaženy ve vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A> elementu <xref:System.Windows.Controls.Grid>, takže je lze použít pro všechny prvky v ovládacím prvku. Pokud je styl pojmenován, můžete jej použít na prvek přidáním prvku <xref:System.Windows.Style> nastaveného na název stylu. Styly, které nejsou pojmenované, se stanou výchozím stylem pro element. Další informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stylů naleznete v tématu [stylování and šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Následující kód XAML ukazuje prvky <xref:System.Windows.Style> pro složený ovládací prvek. Chcete-li zjistit, jak jsou styly použity pro prvky, viz předchozí XAML. Například poslední <xref:System.Windows.Controls.TextBlock> prvek má styl `inlineText` a poslední <xref:System.Windows.Controls.TextBox> element používá výchozí styl.  
  
 V souboru MyControl1. XAML přidejte následující XAML hned za element <xref:System.Windows.Controls.Grid> Start.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Přidání tlačítek OK a Storno  
 Konečné prvky složeného ovládacího prvku jsou elementy **OK** a **Zrušit**<xref:System.Windows.Controls.Button>, které zabírají první dva sloupce posledního řádku <xref:System.Windows.Controls.Grid>. Tyto prvky používají společnou obslužnou rutinu události, `ButtonClicked`a výchozí styl <xref:System.Windows.Controls.Button> definovaný v předchozím kódu XAML.  
  
 V souboru MyControl1. XAML přidejte za poslední <xref:System.Windows.Controls.TextBox> prvek následující kód XAML. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] část složeného ovládacího prvku je teď dokončená.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementace souboru kódu na pozadí  
 Soubor kódu na pozadí MyControl1.xaml.cs implementuje tři základní úlohy:
  
1. Zpracovává událost, která nastane, když uživatel klikne na jedno z tlačítek.  
  
2. Načte data z prvků <xref:System.Windows.Controls.TextBox> a zabalí je do objektu vlastního argumentu události.  
  
3. Vyvolá vlastní událost `OnButtonClick`, která upozorní hostitele, že uživatel je dokončený, a předá data zpět hostiteli.  
  
 Ovládací prvek také zpřístupňuje počet barev a vlastností písma, které umožňují změnit vzhled. Na rozdíl od <xref:System.Windows.Forms.Integration.WindowsFormsHost> třídy, která se používá k hostování model Windows Formsho ovládacího prvku, třída <xref:System.Windows.Forms.Integration.ElementHost> zpřístupňuje pouze <xref:System.Windows.Controls.Panel.Background%2A> vlastnost ovládacího prvku. Chcete-li zachovat podobnost mezi tímto příkladem kódu a příkladem popsaným v [návodu: hostování model Windows Forms složeného ovládacího prvku v](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)subsystému WPF, ovládací prvek zpřístupní zbývající vlastnosti přímo.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Základní struktura souboru s kódem na pozadí  
 Soubor kódu na pozadí se skládá z jednoho oboru názvů `MyControls`, který bude obsahovat dvě třídy, `MyControl1` a `MyControlEventArgs`.  
  
```csharp  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
```  
  
 První třída, `MyControl1`, je částečná třída obsahující kód, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definované v souboru MyControl1. XAML. Při analýze souboru MyControl1. XAML je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] převedena na stejnou částečnou třídu a dvě částečné třídy jsou sloučeny pro vytvoření zkompilovaného ovládacího prvku. Z tohoto důvodu musí název třídy v souboru kódu na pozadí odpovídat názvu třídy přiřazenému k MyControl1. XAML a musí dědit z kořenového prvku ovládacího prvku. Druhá třída, `MyControlEventArgs`, je třída argumenty události, která se používá k odesílání dat zpět do hostitele.  
  
 Otevřete MyControl1.xaml.cs. Změňte existující deklaraci třídy tak, aby měla následující název a dědí z <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicializace ovládacího prvku  
 Následující kód implementuje několik základních úloh:  
  
- Deklaruje soukromou událost, `OnButtonClick`a jejího přidruženého delegáta `MyControlEventHandler`.  
  
- Vytvoří několik privátních globálních proměnných, které ukládají data uživatele. Tato data se zveřejňují prostřednictvím odpovídajících vlastností.  
  
- Implementuje obslužnou rutinu, `Init`pro událost <xref:System.Windows.FrameworkElement.Loaded> ovládacího prvku. Tato obslužná rutina inicializuje globální proměnné tak, že jim přiřadí hodnoty definované v souboru MyControl1. XAML. K tomuto účelu používá <xref:System.Windows.FrameworkElement.Name%2A> přiřazený k typickému <xref:System.Windows.Controls.TextBlock> prvku `nameLabel`pro přístup k nastavení vlastností tohoto prvku.  
  
 Odstraňte existující konstruktor a přidejte následující kód do třídy `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Zpracování tlačítek kliknutí na události  
 Uživatel indikuje, že úloha vstupu na data je dokončená kliknutím na tlačítko **OK** nebo na tlačítko **Storno** . Obě tlačítka používají stejnou <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události `ButtonClicked`. Obě tlačítka mají název, `btnOK` nebo `btnCancel`, který umožňuje obslužné rutině určit, na které tlačítko bylo kliknuto, prozkoumáním hodnoty argumentu `sender`. Obslužná rutina provede následující:  
  
- Vytvoří objekt `MyControlEventArgs`, který obsahuje data z prvků <xref:System.Windows.Controls.TextBox>.  
  
- Pokud uživatel klikl na tlačítko **Storno** , nastaví vlastnost `IsOK` objektu `MyControlEventArgs` na `false`.  
  
- Vyvolává `OnButtonClick` událost, která oznamuje hostiteli, že uživatel je dokončený, a předává zpět shromážděná data.  
  
 Po `Init` metodě přidejte následující kód do třídy `MyControl1`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Vytváření vlastností  
 Zbytek třídy jednoduše zveřejňuje vlastnosti, které odpovídají globálním proměnným, které jsou popsány dříve. Když se změní vlastnost, přistupující objekt set upraví vzhled ovládacího prvku změnou odpovídajících vlastností elementu a aktualizací základních globálních proměnných.  
  
 Do své `MyControl1` třídy přidejte následující kód.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Posílání dat zpět na hostitele  
 Poslední komponentou v souboru je `MyControlEventArgs` třída, která slouží k posílání shromážděných dat zpět na hostitele.  
  
 Do oboru názvů `MyControls` přidejte následující kód. Implementace je jednoduchá a není popsána dále.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Sestavte řešení. Sestavení vytvoří knihovnu DLL s názvem MyControls. dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implementace aplikace model Windows Forms Host  
 Hostitelská aplikace model Windows Forms používá objekt <xref:System.Windows.Forms.Integration.ElementHost> k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku. Aplikace zpracovává událost `OnButtonClick` pro příjem dat ze složeného ovládacího prvku. Aplikace má také sadu přepínačů, které lze použít pro úpravu vzhledu ovládacího prvku. Na následujícím obrázku je znázorněna aplikace.  

Následující obrázek ukazuje složený ovládací prvek WPF hostovaný v aplikaci model Windows Forms "  

 ![Scteenshot, která zobrazuje ovládací prvek Avalon hostování formuláře Windows.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Spuštění projektu:  
  
1. Spusťte Visual Studio a otevřete dialogové okno **Nový projekt** .  
  
2. V kategorii C# vizuál a kategorie systému Windows vyberte šablonu **model Windows Forms aplikace** .  
  
3. Pojmenujte nový projekt `WFHost`.  
  
4. Pro umístění zadejte stejnou složku nejvyšší úrovně, která obsahuje projekt MyControls.  
  
5. Kliknutím na tlačítko **OK** vytvořte projekt.  
  
 Také je nutné přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a další sestavení.  
  
1. Klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a vyberte **Přidat odkaz**.  
  
2. Klikněte na kartu **Procházet** a přejděte do složky, která obsahuje MyControls. dll. Pro tento návod je tato složka MyControls\bin\Debug.  
  
3. Vyberte MyControls. dll a pak klikněte na **OK**.  
  
4. Přidejte odkazy na následující sestavení.  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - System.Xaml  
  
    - WindowsBase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementace uživatelského rozhraní pro aplikaci  
 Uživatelské rozhraní pro formulářovou aplikaci Windows obsahuje několik ovládacích prvků pro interakci se složeným ovládacím prvkem WPF.  
  
1. Otevřete Form1 v Návrháři Windows Form.  
  
2. Zvětšete formulář tak, aby vyhovoval ovládacím prvkům.  
  
3. V pravém horním rohu formuláře přidejte ovládací prvek <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> pro uchování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku.  
  
4. Do formuláře přidejte následující ovládací prvky <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>.  
  
    |Name|Text|  
    |----------|----------|  
    |groupBox1|Barva pozadí|  
    |groupBox2|Barva popředí|  
    |groupBox3|Velikost písma|  
    |groupBox4|Rodina písem|  
    |groupBox5|Styl písma|  
    |groupBox6|Tloušťka písma|  
    |groupBox7|Data z ovládacího prvku|  
  
5. Do ovládacích prvků <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> přidejte následující ovládací prvky <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType>.  
  
    |GroupBox|Name|Text|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Původně|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Původně|  
    |groupBox2|radioForegroundRed|Červená|  
    |groupBox2|radioForegroundYellow|Opatřen|  
    |groupBox3|radioSizeOriginal|Původně|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Původně|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|Písm|  
    |groupBox5|radioStyleOriginal|Normální|  
    |groupBox5|radioStyleItalic|Kurzíva|  
    |groupBox6|radioWeightOriginal|Původně|  
    |groupBox6|radioWeightBold|Psaného|  
  
6. Do posledního <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>přidejte následující ovládací prvky <xref:System.Windows.Forms.Label?displayProperty=nameWithType>. Tyto ovládací prvky zobrazují data vrácená [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeným ovládacím prvkem.  
  
    |GroupBox|Name|Text|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Název:|  
    |groupBox7|lblAddress|Adresa ulice:|  
    |groupBox7|lblCity|Město:|  
    |groupBox7|lblState|Stav:|  
    |groupBox7|lblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Inicializuje se formulář.  
 Obecně implementujete hostující kód v obslužné rutině události <xref:System.Windows.Forms.Form.Load> formuláře. Následující kód ukazuje obslužnou rutinu události <xref:System.Windows.Forms.Form.Load>, obslužná rutina pro <xref:System.Windows.FrameworkElement.Loaded> událost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku a deklarace pro několik globálních proměnných, které jsou používány později.  
  
 V Návrhář formulářů dvakrát klikněte na formulář a vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Form.Load>. V horní části Form1.cs přidejte následující příkazy `using`.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Obsah existující třídy `Form1` nahraďte následujícím kódem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Metoda `Form1_Load` v předchozím kódu ukazuje obecný postup hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho ovládacího prvku:  
  
1. Vytvoří nový objekt <xref:System.Windows.Forms.Integration.ElementHost>.  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.Control.Dock%2A> ovládacího prvku na hodnotu <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3. Přidejte ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> do kolekce <xref:System.Windows.Forms.Control.Controls%2A> ovládacího prvku <xref:System.Windows.Forms.Panel>.  
  
4. Vytvořte instanci ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
5. Nahostování složeného ovládacího prvku na formuláři přiřazením ovládacího prvku k vlastnosti <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.  
  
 Zbývající dva řádky v metodě `Form1_Load` připojovat obslužné rutiny ke dvěma událostem ovládacího prvku:  
  
- `OnButtonClick` je vlastní událost, která je vyvolána složeným ovládacím prvkem, když uživatel klikne na tlačítko **OK** nebo **Storno** . Událost zpracujete, abyste získali odpověď uživatele a mohli shromažďovat všechna data, která uživatel zadal.  
  
- <xref:System.Windows.FrameworkElement.Loaded> je standardní událost, která je vyvolána [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacím prvkem, když je plně načtena. Zde se používá událost, protože příklad musí inicializovat několik globálních proměnných pomocí vlastností z ovládacího prvku. V době <xref:System.Windows.Forms.Form.Load> události formuláře ovládací prvek není zcela načten a tyto hodnoty jsou stále nastaveny na `null`. Než budete mít přístup k těmto vlastnostem, musíte počkat, dokud nedojde k události <xref:System.Windows.FrameworkElement.Loaded> ovládacího prvku.  
  
 V předchozím kódu je zobrazená obslužná rutina události <xref:System.Windows.FrameworkElement.Loaded>. Obslužná rutina `OnButtonClick` je popsána v následující části.  
  
### <a name="handling-onbuttonclick"></a>Zpracování OnButtonClick  
 K události `OnButtonClick` dojde, když uživatel klikne na tlačítko **OK** nebo **Storno** .  
  
 Obslužná rutina události zkontroluje pole `IsOK` argumentu události a určí, na které tlačítko bylo kliknuto. Proměnné `lbl`*dat* odpovídají ovládacím prvkům <xref:System.Windows.Forms.Label>, které byly popsány dříve. Pokud uživatel klikne na tlačítko **OK** , data z ovládacích prvků <xref:System.Windows.Controls.TextBox> ovládacího prvku jsou přiřazena k odpovídajícímu ovládacímu prvku <xref:System.Windows.Forms.Label>. Pokud uživatel klikne na **Storno**, hodnoty <xref:System.Windows.Forms.Label.Text%2A> jsou nastaveny na výchozí řetězce.  
  
 Do `Form1` třídy přidejte následující kód obslužné rutiny události kliknutí na tlačítko.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Sestavte a spusťte aplikaci. Do složeného ovládacího prvku WPF přidejte nějaký text a pak klikněte na **OK**. Text se zobrazí v popiscích. V tomto okamžiku nebyl kód přidán pro zpracování přepínačů.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Úprava vzhledu ovládacího prvku  
 Ovládací prvky <xref:System.Windows.Forms.RadioButton> ve formuláři umožní uživateli měnit barvy popředí a pozadí složeného ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a také několik vlastností písma. Barva pozadí je vystavena objektem <xref:System.Windows.Forms.Integration.ElementHost>. Zbývající vlastnosti jsou zveřejněny jako vlastní vlastnosti ovládacího prvku.  
  
 Dvojím kliknutím na každý ovládací prvek <xref:System.Windows.Forms.RadioButton> na formuláři vytvořte obslužné rutiny události <xref:System.Windows.Forms.RadioButton.CheckedChanged>. Pomocí následujícího kódu nahraďte obslužné rutiny událostí <xref:System.Windows.Forms.RadioButton.CheckedChanged>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Sestavte a spusťte aplikaci. Kliknutím na různé přepínače zobrazíte efekt na složeném ovládacím prvku WPF.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
