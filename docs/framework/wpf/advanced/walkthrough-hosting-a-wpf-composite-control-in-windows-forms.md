---
title: "Návod: Hostování kompozitního ovládacího prvku WPF v rozhraní Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 129d699455467679c86c803e6d3124e6a7dfa1f9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Návod: Hostování kompozitního ovládacího prvku WPF v rozhraní Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte významné investice [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu, může být efektivnější rozšířit stávající [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spíše než přepsání od začátku. Obvyklým scénářem je, když chcete vložit jeden nebo více ovládacích prvků implementováno s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci vaší [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikace. Další informace o přizpůsobení ovládacích prvků WPF najdete v tématu [přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md).  
  
 Tento názorný postup vás provede jednotlivými kroky aplikace který je hostitelem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku k zadávání dat v [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikace. Knihovny DLL je součástí složeného ovládacího prvku. Tento postup Obecné lze rozšířit na složitější aplikace a ovládací prvky. Tento názorný postup je navržený jako téměř shodná v vzhled a funkce [návod: hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Základní rozdíl je, že je obrácený scénáři pro hostování.  
  
 Průvodce je rozdělené na dvě části. V první části stručně popisuje provádění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku. Druhá část podrobně probírají řešení pro hostování složeného ovládacího prvku [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikace, přijímat události z ovládacího prvku a získat přístup k některým vlastností ovládacího prvku.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Implementace složeného ovládacího prvku WPF.  
  
-   Implementace hostitelskou aplikaci Windows Forms.  
  
 Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [hostování WPF složeného ovládacího prvku Windows Forms ukázka](http://go.microsoft.com/fwlink/?LinkID=159996).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementace složeného ovládacího prvku WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Složeného ovládacího prvku použité v tomto příkladu je jednoduchý zadávání dat formuláře, který přebírá název a adresu uživatele. Po kliknutí na jednu ze dvou tlačítek a označuje, že je úloha dokončena, vyvolá ovládací prvek vlastní události vrátit tyto informace k hostiteli. Následující obrázek znázorňuje vykreslené ovládacího prvku.  
  
 ![Jednoduché ovládací prvek WPF](../../../../docs/framework/wpf/advanced/media/avaloncontrol.png "AvalonControl")  
Složené ovládací prvek WPF  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Spuštění projektu:  
  
1.  Spusťte [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.  
  
2.  V jazyce Visual C# a kategorie Windows, vyberte **knihovny ovládací prvek WPF uživatelského** šablony.  
  
3.  Název nového projektu `MyControls`.  
  
4.  K umístění, zadejte pohodlně složka s názvem nejvyšší úrovně, jako například `WindowsFormsHostingWpfControl`. Později umístíte hostitelskou aplikaci v této složce.  
  
5.  Klikněte na tlačítko **OK** a vytvořte tak projekt. Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.  
  
6.  V Průzkumníku řešení, přejmenujte `UserControl1` k `MyControl1`.  
  
 Projekt by měl mít odkazy na následující systémové knihovny DLL. Pokud některý z těchto knihoven DLL se ve výchozím nastavení neobsahuje, přidejte je do projektu.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   Systém  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>Vytvoření uživatelského rozhraní  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Pro složeného ovládacího prvku je implementováno s [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Složeného ovládacího prvku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se skládá z pěti <xref:System.Windows.Controls.TextBox> elementy. Každý <xref:System.Windows.Controls.TextBox> element má přidruženou <xref:System.Windows.Controls.TextBlock> element, který slouží jako popisek. Existují dva <xref:System.Windows.Controls.Button> prvky v dolní části **OK** a **zrušit**. Když uživatel klikne buď tlačítko, vyvolá ovládací prvek vlastní události vrátit informace k hostiteli.  
  
#### <a name="basic-layout"></a>Základní rozložení  
 Různé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy jsou součástí <xref:System.Windows.Controls.Grid> elementu. Můžete použít <xref:System.Windows.Controls.Grid> uspořádat obsah složené řídit téměř stejný způsobem byste použili `Table` element ve formátu HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má také <xref:System.Windows.Documents.Table> elementu, ale <xref:System.Windows.Controls.Grid> je jednodušší a lépe vhodná pro jednoduché rozložení úlohy.  
  
 Následující XAML ukazuje základní rozložení. Tato XAML definuje celková struktura ovládacího prvku tak, že určíte počet sloupců a řádků v <xref:System.Windows.Controls.Grid> elementu.  
  
 V MyControl1.xaml nahraďte existující XAML následující XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Přidání TextBlock a elementy textové pole k mřížce.  
 Umístit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element v mřížce nastavením elementu <xref:System.Windows.Controls.Grid.RowProperty> a <xref:System.Windows.Controls.Grid.ColumnProperty> atributy odpovídající počtu řádků a sloupců. Pamatujte, že jsou číslování sloupců a řádků od nuly. Můžete mít element span více sloupců nastavením jeho <xref:System.Windows.Controls.Grid.ColumnSpanProperty> atribut. Další informace o <xref:System.Windows.Controls.Grid> elementy, najdete v části [vytvořit Element mřížky na](../../../../docs/framework/wpf/controls/how-to-create-a-grid-element.md).  
  
 Následující XAML ukazuje složeného ovládacího prvku <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> prvky s jejich <xref:System.Windows.Controls.Grid.RowProperty> a <xref:System.Windows.Controls.Grid.ColumnProperty> atributy, které jsou nastaveny správně umístit elementů v mřížce.  
  
 V MyControl1.xaml, přidejte následující XAML v rámci <xref:System.Windows.Controls.Grid> elementu.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Práce se styly prvky uživatelského rozhraní  
 Mnoho prvky na formuláři zadávání dat má podobný vzhled, což znamená, že mají stejné nastavení pro některé z jejich vlastnosti. Místo nastavení každý prvek atributy samostatně, používá předchozí XAML <xref:System.Windows.Style> elementy k definování nastavení standardní vlastností pro třídy elementů. Tento přístup snižuje složitost ovládacího prvku a umožňuje změnit vzhled více elementů prostřednictvím jediného stylu atributu.  
  
 <xref:System.Windows.Style> Elementy jsou součástí <xref:System.Windows.Controls.Grid> elementu <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost, takže je můžete použít všechny elementy v ovládacím prvku. Pokud je styl, můžete použít i pro element přidávání <xref:System.Windows.Style> element nastaven na hodnotu názvu stylu. Styly, které nejsou s názvem se jako výchozí styl pro element. Další informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] styly, najdete v části [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Následující XAML ukazuje <xref:System.Windows.Style> elementy složeného ovládacího prvku. Používání stylů na elementy najdete v sekci předchozí XAML. Například poslední <xref:System.Windows.Controls.TextBlock> má element `inlineText` style a poslední <xref:System.Windows.Controls.TextBox> element používá výchozí styl.  
  
 V MyControl1.xaml, přidejte následující XAML právě po <xref:System.Windows.Controls.Grid> počáteční prvek.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Přidání tlačítka Storno a OK  
 Poslední elementů na složeného ovládacího prvku **OK** a **zrušit** <xref:System.Windows.Controls.Button> prvky, které zabírají první dva sloupce poslední řádek <xref:System.Windows.Controls.Grid>. Tyto prvky používat běžné obslužné rutiny události, `ButtonClicked`a ve výchozím nastavení <xref:System.Windows.Controls.Button> styl definované v předchozích XAML.  
  
 V MyControl1.xaml, přidejte následující XAML za poslední <xref:System.Windows.Controls.TextBox> elementu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Součástí složeného ovládacího prvku je dokončena.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementace souboru kódu na pozadí  
 Soubor modelu code-behind, MyControl1.xaml.cs, implementuje tří základních úloh:
  
1.  Zpracovává událost, která nastane, když uživatel klikne na jedno z tlačítek.  
  
2.  Načte data z <xref:System.Windows.Controls.TextBox> prvky a balíčky v objektu argument vlastní události.  
  
3.  Vyvolá vlastní `OnButtonClick` událost, která upozorní hostitele, které uživatel dokončí a předá data zpět na hostitele.  
  
 Ovládací prvek také poskytuje počet barev a písem vlastností, které vám umožní změnit vzhled. Na rozdíl od <xref:System.Windows.Forms.Integration.WindowsFormsHost> třídy, která se používá k hostiteli [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] ovládací prvek, <xref:System.Windows.Forms.Integration.ElementHost> třída zpřístupňuje ovládacího prvku <xref:System.Windows.Controls.Panel.Background%2A> pouze vlastnost. Chcete-li zachovat podobnosti mezi tento příklad kódu a příklad popsané v [návod: hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), ovládacího prvku zpřístupní zbývající vlastnosti přímo.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Základní struktura souboru kódu na pozadí  
 Soubor kódu se skládá z jednoho oboru názvů, `MyControls`, který bude obsahovat dvě třídy `MyControl1` a `MyControlEventArgs`.  
  
```  
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
  
 První třída `MyControl1`, je konkrétní třídu obsahující kód, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definované v MyControl1.xaml. Při analýze MyControl1.xaml [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou převedeny na stejnou třídu, a dva částečné třídy jsou sloučeny do kompilovaného ovládacího prvku. Z tohoto důvodu název třídy v souboru kódu na pozadí musí odpovídat názvu třídy přiřazené MyControl1.xaml a musí dědit z kořenového elementu ovládacího prvku. Druhé třídy `MyControlEventArgs`, je třída argumentů události, která se používá k odesílání dat zpět na hostitele.  
  
 Open MyControl1.xaml.cs. Změnit existující deklaraci třídy tak, aby má následující název a dědí z <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicializace ovládacího prvku  
 Následující kód implementuje několik základní úlohy:  
  
-   Deklaruje Soukromá událost `OnButtonClick`a jeho přidružené delegáta `MyControlEventHandler`.  
  
-   Vytvoří několik privátní globální proměnné, které ukládají data uživatele. Tato data jsou dostupné prostřednictvím odpovídající vlastnosti.  
  
-   Implementuje obslužnou rutinu, `Init`, pro ovládací prvek <xref:System.Windows.FrameworkElement.Loaded> událostí. Tato obslužná rutina inicializuje globální proměnné přiřazením hodnoty definované v MyControl1.xaml. K tomu použije <xref:System.Windows.FrameworkElement.Name%2A> přiřazené typické <xref:System.Windows.Controls.TextBlock> elementu `nameLabel`, přístup k nastavení vlastností tohoto prvku.  
  
 Odstraňte existující konstruktor a přidejte následující kód do vaší `MyControl1` třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Zpracování tlačítka události kliknutí  
 Uživatel znamená, že úloha zadávání dat je dokončen kliknutím buď **OK** tlačítko nebo **zrušit** tlačítko. Obě tlačítka použít stejné <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události, `ButtonClicked`. Obě tlačítka mít název, `btnOK` nebo `btnCancel`, umožňující obslužná rutina k určení, které tlačítko bylo kliknuto prověřením hodnotu `sender` argument. Obslužná rutina provede následující akce:  
  
-   Vytvoří `MyControlEventArgs` objekt, který obsahuje data z <xref:System.Windows.Controls.TextBox> elementy.  
  
-   Pokud uživatel klikne **zrušit** tlačítko nastaví `MyControlEventArgs` objektu `IsOK` vlastnost `false`.  
  
-   Vyvolá `OnButtonClick` události označit k hostiteli, že uživatel je dokončen, a předává zpět na shromážděná data.  
  
 Přidejte následující kód do vaší `MyControl1` třídy po `Init` metoda.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Vytvoření vlastnosti  
 Zbývající část třída jednoduše zpřístupní vlastnosti, které odpovídají globální proměnné, jak jsme vysvětlili výše. Při změně vlastnosti přistupující objekt set upravuje vzhled ovládacího prvku tak, že změna odpovídající element vlastností a aktualizaci základní globální proměnné.  
  
 Přidejte následující kód do vaší `MyControl1` třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Odesílání dat zpět na hostitele  
 Poslední součást v souboru je `MyControlEventArgs` třídy, která se používá k odesílání shromážděná data zpět na hostitele.  
  
 Přidejte následující kód do vaší `MyControls` oboru názvů. Implementace je jednoduchá a není popsané dál.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Sestavte řešení. Sestavení způsobí knihovny DLL s názvem MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implementace hostitelskou aplikaci Windows Forms  
 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] Hostovat aplikace používá <xref:System.Windows.Forms.Integration.ElementHost> objekt hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku. Obslužné rutiny aplikace `OnButtonClick` událostí pro příjem dat z složeného ovládacího prvku. Aplikace také obsahuje sadu přepínačů, který můžete použít k úpravě vzhledu ovládacího prvku. Následující obrázek znázorňuje aplikace.  
  
 ![Hostování ovládacího prvku Avalon formuláře Windows](../../../../docs/framework/wpf/advanced/media/wfhost.png "WFHost")  
WPF složeného ovládacího prvku hostované v aplikaci Windows Forms  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Spuštění projektu:  
  
1.  Spusťte [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.  
  
2.  V jazyce Visual C# a kategorie Windows, vyberte **formulářové aplikace Windows** šablony.  
  
3.  Název nového projektu `WFHost`.  
  
4.  K umístění zadejte stejné nejvyšší úrovně složku, která obsahuje MyControls projektu.  
  
5.  Klikněte na tlačítko **OK** a vytvořte tak projekt.  
  
 Také je nutné přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a jiné sestavení.  
  
1.  Název projektu v Průzkumníku řešení klikněte pravým tlačítkem a vyberte **přidat odkaz na**.  
  
2.  Klikněte **Procházet** kartě a přejděte do složky, která obsahuje MyControls.dll. V tomto návodu je této složky MyControls\bin\Debug.  
  
3.  Vyberte MyControls.dll a pak klikněte na tlačítko **OK**.  
  
4.  Přidejte odkazy na následující sestavení.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementace uživatelského rozhraní pro aplikaci  
 Uživatelské rozhraní pro aplikace Windows Form obsahuje několik ovládacích prvků pro interakci s složeného ovládacího prvku WPF.  
  
1.  Otevřete Form1 v návrháři formuláře systému Windows.  
  
2.  Zvětší umístění ovládacích prvků formuláře.  
  
3.  V pravém horním rohu formuláře, přidejte <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> ovládací prvek pro uložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku.  
  
4.  Přidejte následující <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> ovládacích prvků formuláře.  
  
    |Název|Text|  
    |----------|----------|  
    |groupBox1|Barva pozadí|  
    |groupBox2|Barvy popředí|  
    |groupBox3|Velikost písma|  
    |groupBox4|Rodiny písem|  
    |groupBox5|Styl písma|  
    |groupBox6|Tloušťka písma|  
    |groupBox7|Data z ovládacího prvku|  
  
5.  Přidejte následující <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> prvky <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> ovládací prvky.  
  
    |GroupBox|Název|Text|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Původní|  
    |groupBox1|radioBackgroundLightGreen|Světle zelená|  
    |groupBox1|radioBackgroundLightSalmon|Světle lososová|  
    |groupBox2|radioForegroundOriginal|Původní|  
    |groupBox2|radioForegroundRed|červená|  
    |groupBox2|radioForegroundYellow|žlutý|  
    |groupBox3|radioSizeOriginal|Původní|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Původní|  
    |groupBox4|radioFamilyTimes|Hodnoty času Narrow|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normální|  
    |groupBox5|radioStyleItalic|Kurzíva|  
    |groupBox6|radioWeightOriginal|Původní|  
    |groupBox6|radioWeightBold|Bold|  
  
6.  Přidejte následující <xref:System.Windows.Forms.Label?displayProperty=nameWithType> ovládací prvky na poslední <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Tyto ovládací prvky zobrazení dat vrácených [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku.  
  
    |GroupBox|Název|Text|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Jméno:|  
    |groupBox7|lblAddress|Poštovní adresa:|  
    |groupBox7|lblCity|Město:|  
    |groupBox7|lblState|Stav:|  
    |groupBox7|lblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Inicializace formuláře  
 Obecně implementovat hostování kódu v formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události. Následující kód ukazuje <xref:System.Windows.Forms.Form.Load> obslužné rutiny události, obslužné rutiny pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku <xref:System.Windows.FrameworkElement.Loaded> událostí a deklarace pro několik globálních proměnných, které se používají později.  
  
 V Návrháři formulářů Windows, klikněte dvakrát na formulář pro vytvoření <xref:System.Windows.Forms.Form.Load> obslužné rutiny události. V horní části Form1.cs, přidejte následující `using` příkazy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Nahradit existující obsah `Form1` třídy následujícím kódem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load` Metoda v předchozím kódu zobrazuje obecný postup pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku:  
  
1.  Vytvořte novou <xref:System.Windows.Forms.Integration.ElementHost> objektu.  
  
2.  Nastavte ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3.  Přidat <xref:System.Windows.Forms.Integration.ElementHost> řídit k <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Control.Controls%2A> kolekce.  
  
4.  Vytvoření instance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku.  
  
5.  Hostování složeného ovládacího prvku na formuláři pomocí přiřazení do ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> vlastnost.  
  
 Zbývající dva řádky v `Form1_Load` metoda připojení obslužné rutiny na dvě události ovládacího prvku:  
  
-   `OnButtonClick`je vlastní událost, která je aktivována složeného ovládacího prvku, když uživatel klikne **OK** nebo **zrušit** tlačítko. Zpracování události získat odpovědi uživatele a shromažďovat žádná data, která uživatel zadal.  
  
-   <xref:System.Windows.FrameworkElement.Loaded>je standardní událost, která je aktivováno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení, pokud je plně načíst. Událost je zde použít, protože v příkladu musí inicializovat několik globální proměnné pomocí vlastnosti z ovládacího prvku. V době formuláře <xref:System.Windows.Forms.Form.Load> události ovládacího prvku není úplným načtením a tyto hodnoty jsou stále nastaveny na `null`. Budete muset počkat do ovládacího prvku <xref:System.Windows.FrameworkElement.Loaded> události dojde před přístupem k tyto vlastnosti.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Obslužné rutiny události se zobrazí v předchozí kód. `OnButtonClick` Obslužné rutiny popsané v další části.  
  
### <a name="handling-onbuttonclick"></a>Zpracování OnButtonClick  
 `OnButtonClick` Události dojde, když uživatel klikne **OK** nebo **zrušit** tlačítko.  
  
 Obslužné rutiny události kontroluje argumentu události `IsOK` k určení, které tlačítko bylo kliknuto. `lbl` *Data* proměnné odpovídají <xref:System.Windows.Forms.Label> ovládacích prvků, které byly dříve popsané. Pokud uživatel klikne **OK** data z ovládacího prvku tlačítko <xref:System.Windows.Controls.TextBox> ovládací prvky je přiřazena k příslušné <xref:System.Windows.Forms.Label> ovládacího prvku. Pokud uživatel klikne na **zrušit**, <xref:System.Windows.Forms.Label.Text%2A> hodnoty jsou nastavené na výchozí řetězce.  
  
 Přidat na následující tlačítko klikněte na tlačítko kód obslužné rutiny události pro `Form1` třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Sestavte a spusťte aplikaci. Přidejte nějaký text složeného ovládacího prvku WPF a pak klikněte na tlačítko **OK**. Text se zobrazí v štítky. V tomto okamžiku kód nebyl přidán do zpracování přepínačů.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Změna vzhledu ovládacího prvku  
 <xref:System.Windows.Forms.RadioButton> Ovládací prvky na formuláři umožní uživatelům změnit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku na popředí a pozadí barvy také jako několik vlastností písma. Barva pozadí je zveřejněný prostřednictvím <xref:System.Windows.Forms.Integration.ElementHost> objektu. Ostatní vlastnosti jsou zveřejněné jako vlastní vlastnosti ovládacího prvku.  
  
 Dvakrát klikněte na každou <xref:System.Windows.Forms.RadioButton> ovládacího prvku formuláře k vytvoření <xref:System.Windows.Forms.RadioButton.CheckedChanged> obslužné rutiny událostí. Nahraďte <xref:System.Windows.Forms.RadioButton.CheckedChanged> obslužné rutiny událostí s následujícím kódem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Sestavte a spusťte aplikaci. Klikněte na tlačítko různé přepínače zobrazíte vliv na složeného ovládacího prvku WPF.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
