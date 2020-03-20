---
title: Hostování složeného ovládacího prvku WPF ve formulářích Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: e3326f654e05ef7d487a76f076f8ad0da3637096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187250"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Návod: Hostování kompozitního ovládacího prvku WPF v rozhraní Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte značnou investici do kódu windows forms, může být [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] efektivnější rozšířit stávající aplikaci Windows Forms s spíše než přepsat od začátku. Běžným scénářem je, když chcete vložit jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo více ovládacích prvků implementovaných v rámci aplikace Windows Forms. Další informace o přizpůsobení ovládacích prvků WPF naleznete v [tématu Přizpůsobení ovládacího prvku](../controls/control-customization.md).  
  
 Tento návod vás provede aplikací, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] která je hostitelem složeného ovládacího prvku, a provede zadávání dat v aplikaci Windows Forms. Složený ovládací prvek je zabalen do dll. Tento obecný postup lze rozšířit na složitější aplikace a ovládací prvky. Tento návod je navržen tak, aby byl téměř totožný vzhledem a funkčností [návodu: Hostování složeného ovládacího prvku forem systému Windows ve wpf](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Hlavním rozdílem je, že scénář hostování je obrácen.  
  
 Návod je rozdělen do dvou částí. První část stručně popisuje implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku. Druhá část podrobně popisuje, jak hostovat složený ovládací prvek v aplikaci Windows Forms, přijímat události z ovládacího prvku a přístup k některé vlastnosti ovládacího prvku.  
  
 Mezi úkoly znázorněné v tomto návodu patří:  
  
- Implementace složeného ovládacího prvku WPF.  
  
- Implementace hostitelské aplikace Windows Forms.  
  
 Úplný seznam kódů úkolů znázorněných v tomto návodu naleznete v [tématu Hostování složeného ovládacího prvku WPF v ukázce formulářů systému Windows](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl).  
  
## <a name="prerequisites"></a>Požadavky  

K dokončení tohoto návodu potřebujete Visual Studio.  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementace kompozitního ovládacího prvku WPF  
 Složený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek použitý v tomto příkladu je jednoduchý formulář pro zadávání dat, který přebírá jméno a adresu uživatele. Když uživatel klepne na jedno ze dvou tlačítek označující, že úkol je dokončen, ovládací prvek vyvolá vlastní událost vrátit tyto informace na hostitele. Následující obrázek znázorňuje vykreslený ovládací prvek.

 Následující obrázek znázorňuje složený ovládací prvek WPF:

 ![Snímek obrazovky, který zobrazuje jednoduchý ovládací prvek WPF.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Zahájení projektu:  
  
1. Spusťte Visual Studio a otevřete dialogové okno **Nový projekt.**  
  
2. V jazyce Visual C# a v kategorii Windows vyberte šablonu **Knihovny uživatelského ovládacího prvku WPF.**  
  
3. Pojmenujte `MyControls`nový projekt .  
  
4. Pro umístění zadejte pohodlně pojmenovanou složku nejvyšší `WindowsFormsHostingWpfControl`úrovně, například . Později vložíte hostitelskou aplikaci do této složky.  
  
5. Kliknutím na tlačítko **OK** vytvořte projekt. Výchozí projekt obsahuje jeden `UserControl1`ovládací prvek s názvem .  
  
6. V Průzkumníku řešení `UserControl1` `MyControl1`přejmenujte na .  
  
 Projekt by měl mít odkazy na následující systémové knihovny DLL. Pokud některý z těchto knihoven DLL nejsou zahrnuty ve výchozím nastavení, přidejte je do projektu.  
  
- Presentationcore  
  
- Presentationframework  
  
- Systémový  
  
- Windowsbase  
  
### <a name="creating-the-user-interface"></a>Vytvoření uživatelského rozhraní  
 Pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kompozitní ovládací prvek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]je implementován s . Složený ovládací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvek se <xref:System.Windows.Controls.TextBox> skládá z pěti prvků. Každý <xref:System.Windows.Controls.TextBox> prvek má <xref:System.Windows.Controls.TextBlock> přidružený prvek, který slouží jako popisek. V dolní <xref:System.Windows.Controls.Button> části jsou dva prvky **OK** a **Zrušit**. Když uživatel klepne na jedno z tlačítek, ovládací prvek vyvolá vlastní událost a vrátí informace hostiteli.  
  
#### <a name="basic-layout"></a>Základní rozložení  
 Různé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky jsou obsaženy v <xref:System.Windows.Controls.Grid> prvku. Obsah složeného ovládacího prvku můžete uspořádat <xref:System.Windows.Controls.Grid> v podstatě `Table` stejným způsobem, jako byste použili prvek v html. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má také <xref:System.Windows.Documents.Table> prvek, <xref:System.Windows.Controls.Grid> ale je lehčí a vhodnější pro jednoduché úlohy rozložení.  
  
 Následující XAML ukazuje základní rozložení. Tento XAML definuje celkovou strukturu ovládacího prvku zadáním počtu <xref:System.Windows.Controls.Grid> sloupců a řádků v elementu.  
  
 V mycontrol1.xaml nahraďte existující XAML následujícím XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Přidání elementů TextBlock a TextBox do mřížky  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Prvek umístíte do mřížky nastavením <xref:System.Windows.Controls.Grid.RowProperty> atributů prvku a <xref:System.Windows.Controls.Grid.ColumnProperty> atributů na příslušné číslo řádku a sloupce. Mějte na paměti, že číslování řádků a sloupců je od nuly. Můžete mít prvek rozpětí více sloupců <xref:System.Windows.Controls.Grid.ColumnSpanProperty> nastavením jeho atribut. Další informace <xref:System.Windows.Controls.Grid> o prvcích naleznete [v tématu Vytvoření prvku mřížky](../controls/how-to-create-a-grid-element.md).  
  
 Následující XAML ukazuje složené ovládací <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBlock> prvky <xref:System.Windows.Controls.Grid.RowProperty> a <xref:System.Windows.Controls.Grid.ColumnProperty> prvky s jejich a atributy, které jsou nastaveny na umístění prvků správně v mřížce.  
  
 V mycontrol1.xaml, přidejte následující XAML v <xref:System.Windows.Controls.Grid> rámci prvku.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Styling prvků uživatelského rozhraní  
 Mnoho prvků ve formuláři pro zadávání dat má podobný vzhled, což znamená, že mají stejné nastavení pro několik svých vlastností. Místo nastavování atributů každého prvku samostatně používá <xref:System.Windows.Style> předchozí XAML prvky k definování standardních nastavení vlastností pro třídy prvků. Tento přístup snižuje složitost ovládacího prvku a umožňuje změnit vzhled více prvků prostřednictvím jednoho atributu stylu.  
  
 Prvky <xref:System.Windows.Style> jsou obsaženy <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.FrameworkElement.Resources%2A> vlastnosti prvku, takže mohou být použity všechny prvky v ovládacím prvku. Pokud je styl pojmenován, aplikujte ho na <xref:System.Windows.Style> prvek přidáním sady prvků k názvu stylu. Styly, které nejsou pojmenovány, se stanou výchozím stylem prvku. Další informace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o stylech naleznete v [tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Následující XAML ukazuje <xref:System.Windows.Style> prvky pro složený ovládací prvek. Chcete-li zjistit, jak se styly aplikují na prvky, podívejte se na předchozí XAML. Například poslední <xref:System.Windows.Controls.TextBlock> prvek má `inlineText` styl a <xref:System.Windows.Controls.TextBox> poslední prvek používá výchozí styl.  
  
 V mycontrol1.xaml přidejte následující XAML <xref:System.Windows.Controls.Grid> těsně za počáteční prvek.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Přidání tlačítek OK a Storno  
 Poslední prvky na složené ovládací prvky jsou **OK** a **Cancel** <xref:System.Windows.Controls.Button> prvky, <xref:System.Windows.Controls.Grid>které zabírají první dva sloupce posledního řádku . Tyto prvky používají běžnou `ButtonClicked`obslužnou rutinu události a výchozí <xref:System.Windows.Controls.Button> styl definovaný v předchozím xaml.  
  
 V mycontrol1.xaml přidejte následující XAML <xref:System.Windows.Controls.TextBox> za poslední prvek. Část [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] složeného ovládacího prvku je nyní dokončena.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementace souboru code-behind  
 Soubor s kódem na pozadí, MyControl1.xaml.cs, implementuje tři základní úkoly:
  
1. Zpracovává událost, ke které dojde, když uživatel klepne na jedno z tlačítek.  
  
2. Načte data z <xref:System.Windows.Controls.TextBox> prvků a zabalí je do objektu argumentu vlastní události.  
  
3. Vyvolá vlastní `OnButtonClick` událost, která upozorní hostitele, že uživatel je dokončena a předá data zpět do hostitele.  
  
 Ovládací prvek také zveřejňuje řadu vlastností barev a písma, které umožňují změnit vzhled. Na <xref:System.Windows.Forms.Integration.WindowsFormsHost> rozdíl od třídy, která se používá <xref:System.Windows.Forms.Integration.ElementHost> k hostování ovládacího <xref:System.Windows.Controls.Panel.Background%2A> prvku Windows Forms, třída zveřejňuje pouze vlastnost ovládacího prvku. Chcete-li zachovat podobnost mezi tento příklad kódu a příklad popsaný v [návodu: Hostování windows forms composite control v WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), ovládací prvek zpřístupňuje zbývající vlastnosti přímo.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Základní struktura souboru code-behind  
 Soubor s kódem na pozadí se `MyControls`skládá z jednoho oboru `MyControl1` `MyControlEventArgs`názvů , který bude obsahovat dvě třídy a .  
  
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
  
 První třída `MyControl1`, je částečná třída obsahující kód, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definované v MyControl1.xaml. Při myControl1.xaml je analyzován, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je převeden na stejnou částečnou třídu a dvě částečné třídy jsou sloučeny do tvoří zkompilovaný ovládací prvek. Z tohoto důvodu název třídy v souboru s kódem na pozadí musí odpovídat názvu třídy přiřazené myControl1.xaml a musí dědit z kořenového prvku ovládacího prvku. Druhá třída `MyControlEventArgs`, je třída argumentů události, která slouží k odeslání dat zpět hostiteli.  
  
 Otevřete MyControl1.xaml.cs. Změňte existující deklaraci třídy tak, aby <xref:System.Windows.Controls.Grid>měla následující název a dědí od .  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicializace ovládacího prvku  
 Následující kód implementuje několik základních úkolů:  
  
- Deklaruje `OnButtonClick`soukromou událost a `MyControlEventHandler`její přidružený delegát .  
  
- Vytvoří několik soukromých globálních proměnných, které ukládají data uživatele. Tato data jsou vystavena prostřednictvím odpovídajícívlastnosti.  
  
- Implementuje obslužnou rutinu , `Init`pro událost ovládacího <xref:System.Windows.FrameworkElement.Loaded> prvku. Tato obslužná rutina inicializuje globální proměnné přiřazením hodnot definovaných v mycontrol1.xaml. K tomu používá <xref:System.Windows.FrameworkElement.Name%2A> přiřazený typický <xref:System.Windows.Controls.TextBlock> prvek `nameLabel`, pro přístup k nastavení vlastností tohoto prvku.  
  
 Odstraňte existující konstruktor a přidejte `MyControl1` následující kód do třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Zpracování událostí kliknutí tlačítek  
 Uživatel označuje, že úloha zadávání dat je dokončena klepnutím na tlačítko **OK** nebo **tlačítko Storno.** Obě tlačítka používají <xref:System.Windows.Controls.Primitives.ButtonBase.Click> stejnou `ButtonClicked`obslužnou rutinu události . Obě tlačítka mají `btnOK` název `btnCancel`nebo , který umožňuje obslužné rutině určit, na které tlačítko bylo kliknuto kontrolou hodnoty argumentu. `sender` Obslužná rutina provádí následující akce:  
  
- Vytvoří `MyControlEventArgs` objekt, který obsahuje <xref:System.Windows.Controls.TextBox> data z prvků.  
  
- Pokud uživatel klepne na tlačítko `MyControlEventArgs` **Storno,** `false`nastaví `IsOK` vlastnost objektu na .  
  
- Vyvolá `OnButtonClick` událost, která hostiteli označí, že je uživatel dokončen, a předá shromážděná data zpět.  
  
 Přidejte následující kód `MyControl1` do třídy, za metodu. `Init`  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Vytváření vlastností  
 Zbytek třídy jednoduše zveřejňuje vlastnosti, které odpovídají globální proměnné popsané dříve. Když se změní vlastnost, přístupový objekt sady upraví vzhled ovládacího prvku změnou odpovídajících vlastností elementu a aktualizací základních globálních proměnných.  
  
 Přidejte do třídy `MyControl1` následující kód.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Odeslání dat zpět hostiteli  
 Poslední součástí souboru je `MyControlEventArgs` třída, která slouží k odeslání shromážděných dat zpět hostiteli.  
  
 Přidejte do `MyControls` oboru názvů následující kód. Implementace je přímočará a není dále diskutována.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Sestavte řešení. Sestavení vytvoří dll s názvem MyControls.dll.  
  
<a name="winforms_host_section"></a>
## <a name="implementing-the-windows-forms-host-application"></a>Implementace hostitelské aplikace formulářů systému Windows  
 Hostitelská aplikace Windows <xref:System.Windows.Forms.Integration.ElementHost> Forms používá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt k hostování složeného ovládacího prvku. Aplikace zpracovává `OnButtonClick` událost přijímat data z složené ho ovládacího prvku. Aplikace má také sadu přepínačů, které můžete použít k úpravě vzhledu ovládacího prvku. Následující obrázek znázorňuje aplikaci.  

Následující obrázek znázorňuje složený ovládací prvek WPF hostovaný v aplikaci Windows Forms."  

 ![Scteenshot, který zobrazuje ovládací prvek Windows Form Hosting Avalon.](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Zahájení projektu:  
  
1. Spusťte Visual Studio a otevřete dialogové okno **Nový projekt.**  
  
2. V jazyce Visual C# a v kategorii Systému Windows vyberte šablonu **aplikace Windows Forms Application.**  
  
3. Pojmenujte `WFHost`nový projekt .  
  
4. Pro umístění zadejte stejnou složku nejvyšší úrovně, která obsahuje projekt MyControls.  
  
5. Kliknutím na tlačítko **OK** vytvořte projekt.  
  
 Je také třeba přidat odkazy na dll, která obsahuje `MyControl1` a další sestavení.  
  
1. Klepněte pravým tlačítkem myši na název projektu v Průzkumníku řešení a vyberte **přidat odkaz**.  
  
2. Klikněte na kartu **Procházet** a vyhledejte složku, která obsahuje soubor MyControls.dll. Pro tento návod je tato složka MyControls\bin\Debug.  
  
3. Vyberte soubor MyControls.dll a klepněte na tlačítko **OK**.  
  
4. Přidejte odkazy na následující sestavení.  
  
    - Presentationcore  
  
    - Presentationframework  
  
    - System.xaml  
  
    - Windowsbase  
  
    - Integrace formulářů Windows  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementace uživatelského rozhraní pro aplikaci  
 Rozhraní pro aplikaci Windows Form obsahuje několik ovládacích prvků pro interakci s složeným ovládacím prvkem WPF.  
  
1. Otevřete formulář1 v Návrháři formulářů systému Windows.  
  
2. Zvětšete formulář tak, aby vyhovoval ovládacím prvkům.  
  
3. V pravém horním rohu formuláře přidejte <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro uložení složeného ovládacího prvku.  
  
4. Přidejte <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> do formuláře následující ovládací prvky.  
  
    |Name (Název)|Text|  
    |----------|----------|  
    |groupBox1|Barva pozadí|  
    |groupBox2|Barva popředí|  
    |groupBox3|Velikost písma|  
    |groupBox4|Rodina písem|  
    |groupBox5|Styl písma|  
    |groupBox6|Tloušťka písma|  
    |groupBox7|Data z ovládacího prvku|  
  
5. Přidejte <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> následující ovládací <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> prvky do ovládacích prvků.  
  
    |GroupBox|Name (Název)|Text|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Původní|  
    |groupBox1|rádioBackgroundLightGreen|Světle zelená|  
    |groupBox1|radioBackgroundLightLosos|LightSalmon|  
    |groupBox2|radioForegroundOriginal|Původní|  
    |groupBox2|radioForegroundRed|Červený|  
    |groupBox2|radioForegroundŽlutá|Žlutý|  
    |groupBox3|radioSizeOriginal|Původní|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Původní|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|Wingdings|  
    |groupBox5|radioStyleOriginal|Normální|  
    |groupBox5|radioStyleItalic|Kurzíva|  
    |groupBox6|radioWeightOriginal|Původní|  
    |groupBox6|rádioWeightBold|Tučný|  
  
6. Do posledního <xref:System.Windows.Forms.Label?displayProperty=nameWithType> <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>doplňku přidejte následující ovládací prvky . Tyto ovládací prvky zobrazují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data vrácená složeným ovládacím prvkem.  
  
    |GroupBox|Name (Název)|Text|  
    |--------------|----------|----------|  
    |groupBox7|název lbl|Název:|  
    |groupBox7|Adresa lbl|Ulice:|  
    |groupBox7|lblCity|Město:|  
    |groupBox7|lblState|Státu:|  
    |groupBox7|LblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Inicializace formuláře  
 Obecně implementovat kód hostování v <xref:System.Windows.Forms.Form.Load> obslužné rutině události formuláře. Následující kód zobrazuje <xref:System.Windows.Forms.Form.Load> obslužnou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rutinu události, obslužnou rutinu pro událost složeného ovládacího <xref:System.Windows.FrameworkElement.Loaded> prvku a deklarace pro několik globálních proměnných, které se používají později.  
  
 V Návrháři formulářů systému Windows poklepejte na formulář a vytvořte obslužnou rutinu <xref:System.Windows.Forms.Form.Load> události. V horní části Form1.cs přidejte následující `using` příkazy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Nahraďte obsah `Form1` existující třídy následujícím kódem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 Metoda `Form1_Load` v předchozím kódu zobrazuje obecný postup [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro hostování ovládacího prvku:  
  
1. Vytvořte <xref:System.Windows.Forms.Integration.ElementHost> nový objekt.  
  
2. Nastavte vlastnost ovládacího <xref:System.Windows.Forms.Control.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>prvku na .  
  
3. Přidejte <xref:System.Windows.Forms.Integration.ElementHost> ovládací <xref:System.Windows.Forms.Panel> prvek do <xref:System.Windows.Forms.Control.Controls%2A> kolekce ovládacího prvku.  
  
4. Vytvořte instanci ovládacího [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvku.  
  
5. Hostujte složený ovládací prvek ve formuláři <xref:System.Windows.Forms.Integration.ElementHost> přiřazením <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> ovládacího prvku k vlastnosti ovládacího prvku.  
  
 Zbývající dva řádky v `Form1_Load` metodě připojit obslužné rutiny na dvě události ovládacího prvku:  
  
- `OnButtonClick`je vlastní událost, která je aktivována složený ovládací prvek, když uživatel klepne na tlačítko **OK** nebo **Storno.** Zpracováváte událost získat odpověď uživatele a shromažďovat všechna data, která uživatel zadal.  
  
- <xref:System.Windows.FrameworkElement.Loaded>je standardní událost, která [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vyvolána ovládacím prvkem při plném načtení. Zde se používá událost, protože příklad potřebuje inicializovat několik globálních proměnných pomocí vlastností z ovládacího prvku. V době <xref:System.Windows.Forms.Form.Load> události formuláře ovládací prvek není plně načten a tyto hodnoty `null`jsou stále nastaveny na . Před přístupem k těmto vlastnostem je třeba počkat, dokud nedojde k události ovládacího <xref:System.Windows.FrameworkElement.Loaded> prvku.  
  
 Obslužná rutina <xref:System.Windows.FrameworkElement.Loaded> události je zobrazena v předchozím kódu. Obslužná rutina `OnButtonClick` je popsána v další části.  
  
### <a name="handling-onbuttonclick"></a>Manipulace s onbuttonclick  
 K `OnButtonClick` události dojde, když uživatel klepne na tlačítko **OK** nebo **Storno.**  
  
 Obslužná rutina `IsOK` události zkontroluje pole argumentu události a určí, na které tlačítko bylo kliknuto. `lbl` *Datové* proměnné odpovídají ovládací <xref:System.Windows.Forms.Label> prvky, které byly popsány dříve. Pokud uživatel klepne na tlačítko **OK,** data <xref:System.Windows.Controls.TextBox> z ovládacích prvků <xref:System.Windows.Forms.Label> ovládacího prvku jsou přiřazena odpovídajícímu ovládacímu prvku. Pokud uživatel klepne na <xref:System.Windows.Forms.Label.Text%2A> tlačítko **Storno**, jsou hodnoty nastaveny na výchozí řetězce.  
  
 Přidejte následující tlačítko klepněte `Form1` na kód obslužné rutiny události do třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Sestavte a spusťte aplikaci. Přidejte nějaký text do složeného ovládacího prvku WPF a klepněte na tlačítko **OK**. Text se zobrazí v popiscích. V tomto okamžiku kód nebyl přidán pro zpracování přepínacích tlačítek.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Změna vzhledu ovládacího prvku  
 Ovládací <xref:System.Windows.Forms.RadioButton> prvky ve formuláři umožní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživateli změnit barvy popředí a pozadí složeného ovládacího prvku a také několik vlastností písma. Barva pozadí je vystavena objektu. <xref:System.Windows.Forms.Integration.ElementHost> Zbývající vlastnosti jsou vystaveny jako vlastní vlastnosti ovládacího prvku.  
  
 Poklepáním <xref:System.Windows.Forms.RadioButton> na jednotlivé ovládací <xref:System.Windows.Forms.RadioButton.CheckedChanged> prvek ve formuláři vytvořte obslužné rutiny událostí. Nahraďte obslužné rutiny <xref:System.Windows.Forms.RadioButton.CheckedChanged> událostí následujícím kódem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Sestavte a spusťte aplikaci. Klepnutím na různá přepínací tlačítka zobrazíte efekt na složeném ovládacím prvku WPF.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
