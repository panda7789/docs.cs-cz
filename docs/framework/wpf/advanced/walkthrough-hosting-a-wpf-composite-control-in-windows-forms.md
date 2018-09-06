---
title: 'Návod: Hostování kompozitního ovládacího prvku WPF v rozhraní Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 09f634c870eb78c16192ed30ffbbfdc71fdd5142
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735472"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>Návod: Hostování kompozitního ovládacího prvku WPF v rozhraní Windows Forms
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte značné investice [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kódu, může být mnohem efektivnější Rozšiřte svoje stávající [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] namísto jeho přepsání úplně od začátku. Běžný scénář, kdy je, když chcete vložit jednu nebo více ovládacích prvků implementovaný pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci vaší aplikace Windows Forms. Další informace o přizpůsobení ovládacích prvků WPF v tématu [přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md).  
  
 Tento názorný postup vás provede aplikace, který je hostitelem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složený ovládací prvek pro zadávání dat v aplikaci Windows Forms. Složený ovládací prvek je zabalený ve knihovny DLL. Tento obecný postup je možné rozšířit na složitější aplikace a ovládací prvky. Tento názorný postup je navržený jako téměř identické v vzhled a funkce, které [návod: hostování složeného ovládacího Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md). Hlavní rozdíl je, že je obrácený scénáři hostování.  
  
 Návod je rozdělen do dvou částí. V první části stručně popisuje provádění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku. Druhá část podrobně popisuje, jak pro hostování složeného ovládacího prvku v aplikaci Windows Forms, příjem událostí z ovládacího prvku a přístup k některé z vlastností ovládacího prvku.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Implementace složeného ovládacího prvku WPF.  
  
-   Implementace hostitele aplikace Windows Forms.  
  
 Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [hostování složeného ovládacího prvku WPF ve Windows Forms vzorku](https://go.microsoft.com/fwlink/?LinkID=159996).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-wpf-composite-control"></a>Implementace složeného ovládacího prvku WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Složeného ovládacího prvku použitého v tomto příkladu je jednoduché zadávání dat formuláře, který přebírá uživatelské jméno a adresa. Když uživatel klikne dvě tlačítka k označení, že je úloha dokončena, ovládací prvek vyvolá vlastní událost, vrátí tyto informace k hostiteli. Následující obrázek ukazuje ovládací prvek vykreslené.  
  
 ![Jednoduché ovládací prvek WPF](../../../../docs/framework/wpf/advanced/media/avaloncontrol.png "AvalonControl")  
Složeného ovládacího prvku WPF  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Ke spuštění projektu:  
  
1.  Spuštění [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.  
  
2.  V jazyce Visual C# a kategorie Windows, vyberte **Knihovna uživatelských ovládacích prvků WPF** šablony.  
  
3.  Název nového projektu `MyControls`.  
  
4.  K umístění, zadejte jednoduše pojmenované složku nejvyšší úrovně, například `WindowsFormsHostingWpfControl`. Hostitelská aplikace později, budou umístili do této složky.  
  
5.  Klikněte na tlačítko **OK** pro vytvoření projektu. Výchozí projekt obsahuje jeden ovládací prvek s názvem `UserControl1`.  
  
6.  V Průzkumníku řešení, přejmenujte `UserControl1` k `MyControl1`.  
  
 Váš projekt by měl zahrnovat odkazy na tyto systémové knihovny DLL. Pokud některý z těchto knihoven DLL nejsou zahrnuty ve výchozím nastavení, můžete je přidáte do projektu.  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   Systém  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>Vytvoření uživatelského rozhraní  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Pro složeného ovládacího prvku je implementováno s [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Složený ovládací prvek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se skládá z pěti <xref:System.Windows.Controls.TextBox> elementy. Každý <xref:System.Windows.Controls.TextBox> element má přiřazený <xref:System.Windows.Controls.TextBlock> element, který slouží jako popisek. Existují dva <xref:System.Windows.Controls.Button> prvky v dolní části, **OK** a **zrušit**. Když uživatel klikne na tlačítko buď tlačítko, ovládací prvek vyvolá vlastní události k vrácení informací k hostiteli.  
  
#### <a name="basic-layout"></a>Základní rozložení  
 Různé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky jsou obsaženy v <xref:System.Windows.Controls.Grid> elementu. Můžete použít <xref:System.Windows.Controls.Grid> uspořádat obsah složeného řídit prakticky stejné stejně, jako byste použili `Table` prvku ve formátu HTML. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má také <xref:System.Windows.Documents.Table> elementu, ale <xref:System.Windows.Controls.Grid> je odlehčenější a lépe hodí pro úlohy s jednoduchým rozložením.  
  
 Následující XAML ukazuje základní rozložení. Tento XAML definuje strukturu celkové ovládacího prvku tak, že určíte počet sloupců a řádků v <xref:System.Windows.Controls.Grid> elementu.  
  
 V MyControl1.xaml nahraďte existující XAML následující XAML.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>Přidávání TextBlock a textové pole prvků do mřížky  
 Umístíte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvek v mřížce nastavením elementu <xref:System.Windows.Controls.Grid.RowProperty> a <xref:System.Windows.Controls.Grid.ColumnProperty> atributy odpovídající počtu řádků a sloupců. Mějte na paměti, že řádek a číslování pro identifikátory sloupce jsou počítány od nuly. Můžete mít element přesahují do více sloupců tak, že nastavíte její <xref:System.Windows.Controls.Grid.ColumnSpanProperty> atribut. Další informace o <xref:System.Windows.Controls.Grid> prvky, naleznete v tématu [vytvoření elementu mřížky](../../../../docs/framework/wpf/controls/how-to-create-a-grid-element.md).  
  
 Složený ovládací prvek zobrazuje následující XAML <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.TextBlock> prvky s jejich <xref:System.Windows.Controls.Grid.RowProperty> a <xref:System.Windows.Controls.Grid.ColumnProperty> atributy, které jsou nastavené správně umístit prvky v mřížce.  
  
 V MyControl1.xaml, přidejte následující XAML v rámci <xref:System.Windows.Controls.Grid> elementu.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>Používání stylů pro prvky uživatelského rozhraní  
 Řadu prvků ve formuláři pro zadávání dat mají podobný vzhled, což znamená, že mají stejné nastavení pro některé z jejich vlastností. Místo nastavování atributů každý prvek samostatně, používá předchozí XAML <xref:System.Windows.Style> můžete definovat nastavení standardní vlastnosti třídy prvků. Tento přístup snižuje složitost ovládacího prvku a umožňuje změnit vzhled více elementů prostřednictvím atributu jednoho style.  
  
 <xref:System.Windows.Style> Prvky jsou obsaženy v <xref:System.Windows.Controls.Grid> elementu <xref:System.Windows.FrameworkElement.Resources%2A> vlastnosti, takže mohou využívat všechny prvky v ovládacím prvku. Pokud je styl, použijete ho na element tak, že přidáte <xref:System.Windows.Style> element nastaven na hodnotu názvu stylu. Styly, které nejsou s názvem stane výchozí styl pro element. Další informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stylů, najdete v článku [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Zobrazí se následující XAML <xref:System.Windows.Style> prvky složeného ovládacího prvku. Používání stylů pro prvky, najdete v předchozí XAML. Například poslední <xref:System.Windows.Controls.TextBlock> element má `inlineText` styl a poslední <xref:System.Windows.Controls.TextBox> prvek používá výchozí styl.  
  
 V MyControl1.xaml, přidejte následující XAML hned za <xref:System.Windows.Controls.Grid> počáteční prvek.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>Přidání OK a tlačítka Storno  
 Poslední prvky na složeného ovládacího prvku **OK** a **zrušit** <xref:System.Windows.Controls.Button> elementy, které zabírají první dva sloupce posledním řádku <xref:System.Windows.Controls.Grid>. Společný obslužnou rutinu události, použijte tyto prvky `ButtonClicked`a ve výchozím nastavení <xref:System.Windows.Controls.Button> styl definované v předchozích XAML.  
  
 V MyControl1.xaml, přidejte následující XAML za poslední <xref:System.Windows.Controls.TextBox> elementu. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Součástí složeného ovládacího prvku je nyní dokončený.  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>Implementace souboru kódu na pozadí  
 Soubor kódu na pozadí, MyControl1.xaml.cs, implementuje tři základní úlohy:
  
1.  Zpracovává událost, ke které dojde po kliknutí na jedno z tlačítek.  
  
2.  Načte data z <xref:System.Windows.Controls.TextBox> elementy a balíčky v argumentu objektu vlastní události.  
  
3.  Vyvolá vlastní `OnButtonClick` událost, která upozorňuje hostitele, že uživatel je dokončena a předá data zpět do hostitele.  
  
 Ovládací prvek také poskytuje počet barev a písma vlastnosti, které vám umožní změnit vzhled. Na rozdíl od <xref:System.Windows.Forms.Integration.WindowsFormsHost> třídu, která se používá k hostování ovládacího prvku Windows Forms, <xref:System.Windows.Forms.Integration.ElementHost> třída zveřejňuje ovládacího prvku <xref:System.Windows.Controls.Panel.Background%2A> pouze vlastnost. Zachovat podobnosti tento příklad kódu a ukázkové podrobněji [návod: hostování složeného ovládacího Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md), ovládací prvek poskytuje zbývající vlastnosti přímo.  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>Základní struktura souboru kódu na pozadí  
 Soubor kódu na pozadí se skládá z jednoho oboru názvů, `MyControls`, která bude obsahovat dvě třídy `MyControl1` a `MyControlEventArgs`.  
  
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
  
 První třída `MyControl1`, je částečná třída obsahující kód, který implementuje funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definované v MyControl1.xaml. Při analýze MyControl1.xaml [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je převedena na stejné částečné třídy a dvě částečné třídy jsou sloučeny do kompilovaného ovládacího prvku. Z tohoto důvodu název třídy v souboru kódu na pozadí musí odpovídat názvu třídy, které jsou přiřazené MyControl1.xaml a musí dědit z kořenový element ovládacího prvku. Druhá třída `MyControlEventArgs`, je třída argumentů události, která se používá k odesílání dat zpět do hostitele.  
  
 Otevřete MyControl1.xaml.cs. Změnit existující deklaraci třídy tak, aby má následující název a dědí z <xref:System.Windows.Controls.Grid>.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>Inicializuje se ovládací prvek  
 Následující kód implementuje několik základní úlohy:  
  
-   Deklaruje Soukromá událost `OnButtonClick`a její přidružené delegáta `MyControlEventHandler`.  
  
-   Vytvoří několik privátních globální proměnné, které ukládají data uživatele. Tato data je přístupný prostřednictvím odpovídající vlastnosti.  
  
-   Implementuje obslužnou rutinu `Init`, ovládacího prvku <xref:System.Windows.FrameworkElement.Loaded> událostí. Tato obslužná rutina inicializuje přiřazením hodnoty definované v MyControl1.xaml globální proměnné. K tomu použije <xref:System.Windows.FrameworkElement.Name%2A> přiřazená typické <xref:System.Windows.Controls.TextBlock> elementu `nameLabel`, pro přístup k nastavení vlastností tohoto prvku.  
  
 Odstraňte existující konstruktor a přidejte následující kód, který vaše `MyControl1` třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>Zpracování na tlačítka události kliknutí  
 Uživatel označuje dokončení úkolu zadávání dat kliknutím na možnost **OK** tlačítko nebo **zrušit** tlačítko. Obě tlačítka použít stejné <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události `ButtonClicked`. Obě tlačítka mít název, `btnOK` nebo `btnCancel`, umožňující obslužnou rutinu k určení, které tlačítko došlo ke kliknutí na porovnáním hodnoty `sender` argument. Obslužná rutina provede následující akce:  
  
-   Vytvoří `MyControlEventArgs` objekt, který obsahuje data z <xref:System.Windows.Controls.TextBox> elementy.  
  
-   Pokud uživatel klikne **zrušit** tlačítko, nastaví `MyControlEventArgs` objektu `IsOK` vlastnost `false`.  
  
-   Vyvolá `OnButtonClick` událost označující na hostitele, že uživatel dokončil a předá zpět shromážděná data.  
  
 Přidejte následující kód, který vaše `MyControl1` třídy po `Init` metody.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>Vytvoření vlastnosti  
 Zbývající část třídy jednoduše zpřístupní vlastnosti, které odpovídají globální proměnné, jak jsme vysvětlili výše. Když se změní vlastnost, přístupový objekt set změní vzhled ovládacího prvku změnou odpovídající vlastnosti elementu a aktualizace základního globální proměnné.  
  
 Přidejte následující kód, který vaše `MyControl1` třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>Odesílání dat zpět k hostiteli  
 Je konečný komponenty v souboru `MyControlEventArgs` třídu, která slouží k posílání shromážděných dat zpět do hostitele.  
  
 Přidejte následující kód, který vaše `MyControls` oboru názvů. Implementace je jednoduchá a není popsaných dále.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 Sestavte řešení. Sestavení vytvoří knihovnu DLL s názvem MyControls.dll.  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>Implementace hostitelskou aplikaci Windows Forms  
 Windows Forms hostovat aplikace používá <xref:System.Windows.Forms.Integration.ElementHost> objekt hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku. Aplikace zpracovává `OnButtonClick` události pro příjem dat ze složeného ovládacího prvku. Aplikace má také sada přepínačů, můžete použít k úpravě vzhledu ovládacího prvku. Následující obrázek znázorňuje aplikaci.  
  
 ![Formuláře Windows hostování ovládacího prvku Avalon](../../../../docs/framework/wpf/advanced/media/wfhost.png "WFHost")  
WPF složený ovládací prvek je hostován v aplikaci Windows Forms  
  
### <a name="creating-the-project"></a>Vytvoření projektu  
 Ke spuštění projektu:  
  
1.  Spuštění [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]a otevřete **nový projekt** dialogové okno.  
  
2.  V jazyce Visual C# a kategorie Windows, vyberte **formulářová aplikace Windows** šablony.  
  
3.  Název nového projektu `WFHost`.  
  
4.  Pro umístění zadejte stejnou složku nejvyšší úrovně, obsahující projekt MyControls.  
  
5.  Klikněte na tlačítko **OK** pro vytvoření projektu.  
  
 Musíte také přidat odkazy na knihovnu DLL, která obsahuje `MyControl1` a jiná sestavení.  
  
1.  Klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a vyberte **přidat odkaz**.  
  
2.  Klikněte na tlačítko **Procházet** kartu a přejděte do složky, která obsahuje MyControls.dll. V tomto návodu je této složky MyControls\bin\Debug.  
  
3.  Vyberte MyControls.dll a potom klikněte na tlačítko **OK**.  
  
4.  Přidáte odkazy na následující sestavení.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>Implementace uživatelského rozhraní pro aplikaci  
 Uživatelské rozhraní pro aplikace Windows Form obsahuje několik ovládacích prvků pro interakci s složeného ovládacího prvku WPF.  
  
1.  Form1 otevřete v Návrháři formulářů Windows.  
  
2.  Zvětšete formuláře pro přizpůsobení ovládacích prvků.  
  
3.  V pravém horním rohu formuláře, přidejte <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> ovládací prvek pro uchování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku.  
  
4.  Přidejte následující <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> ovládací prvky do formuláře.  
  
    |Název|Text|  
    |----------|----------|  
    |groupBox1|Barva pozadí|  
    |groupBox2|Barva popředí|  
    |groupBox3|Velikost písma|  
    |groupBox4|Rodina písem|  
    |groupBox5|Styl písma|  
    |groupBox6|Tloušťka písma|  
    |groupBox7|Data z ovládacího prvku|  
  
5.  Přidejte následující <xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType> ovládacích prvků <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType> ovládacích prvků.  
  
    |GroupBox|Název|Text|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|Původní|  
    |groupBox1|radioBackgroundLightGreen|Světle zelená|  
    |groupBox1|radioBackgroundLightSalmon|Světle lososová|  
    |groupBox2|radioForegroundOriginal|Původní|  
    |groupBox2|radioForegroundRed|Červená|  
    |groupBox2|radioForegroundYellow|Žlutá|  
    |groupBox3|radioSizeOriginal|Původní|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|Původní|  
    |groupBox4|radioFamilyTimes|Georgia|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normální|  
    |groupBox5|radioStyleItalic|Kurzíva|  
    |groupBox6|radioWeightOriginal|Původní|  
    |groupBox6|radioWeightBold|Tučné|  
  
6.  Přidejte následující <xref:System.Windows.Forms.Label?displayProperty=nameWithType> ovládací prvky na poslední <xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>. Tyto ovládací prvky zobrazení dat vrácených [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku.  
  
    |GroupBox|Název|Text|  
    |--------------|----------|----------|  
    |groupBox7|lblName|Jméno:|  
    |groupBox7|lblAddress|Poštovní adresa:|  
    |groupBox7|lblCity|Město:|  
    |groupBox7|lblState|Stav:|  
    |groupBox7|lblZip|Zip:|  
  
### <a name="initializing-the-form"></a>Formuláře inicializace  
 Obecně implementovat kód hostování v formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události. Následující kód ukazuje <xref:System.Windows.Forms.Form.Load> obslužná rutina události, obslužné rutiny pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složeného ovládacího prvku <xref:System.Windows.FrameworkElement.Loaded> událostí a deklarace pro několik globální proměnné, které se později použijí.  
  
 V Návrháři formulářů Windows, klikněte dvakrát na formulář pro vytvoření <xref:System.Windows.Forms.Form.Load> obslužné rutiny události. V horní části stránky Form1.cs, přidejte následující `using` příkazy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 Nahraďte obsah stávající `Form1` třídy následujícím kódem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load` Metoda v předchozím kódu ukazuje obecný postup pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku:  
  
1.  Vytvořte nový <xref:System.Windows.Forms.Integration.ElementHost> objektu.  
  
2.  Nastavit u tohoto prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>.  
  
3.  Přidat <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.Control.Controls%2A> kolekce.  
  
4.  Vytvoření instance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku.  
  
5.  Hostování složeného ovládacího prvku ve formuláři přiřazením ovládacího prvku, aby <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> vlastnost.  
  
 Zbývající dva řádky v `Form1_Load` obslužné rutiny metoda připojit dvě události ovládacích prvků:  
  
-   `OnButtonClick` je vlastní událost, která se aktivuje pomocí složeného ovládacího prvku, když uživatel klikne **OK** nebo **zrušit** tlačítko. Zpracování události odpovědi uživatele a shromažďovat žádná data, která uživatel zadal.  
  
-   <xref:System.Windows.FrameworkElement.Loaded> je standardní událost, která je vyvolána [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řídit, kdy je plně načteno. Událost je zde použita, protože v příkladu je potřeba inicializovat několika globální proměnné pomocí vlastnosti z ovládacího prvku. V době formuláře <xref:System.Windows.Forms.Form.Load> událostí, ovládací prvek není plně načten a tyto hodnoty jsou stále nastaveny na `null`. Budete muset počkat až do ovládacího prvku <xref:System.Windows.FrameworkElement.Loaded> pro přístup k těmto vlastnostem dojde k události.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Obslužná rutina události se zobrazí v předchozím kódu. `OnButtonClick` Obslužná rutina je popsáno v další části.  
  
### <a name="handling-onbuttonclick"></a>Zpracování OnButtonClick  
 `OnButtonClick` Události dojde, když uživatel klikne **OK** nebo **zrušit** tlačítko.  
  
 Obslužná rutina události ověří argumentu události `IsOK` pole k určení, které tlačítko došlo ke kliknutí na. `lbl` *Data* proměnné odpovídají <xref:System.Windows.Forms.Label> ovládací prvky, které byly zmíněny dříve. Pokud uživatel klikne **OK** tlačítko, data z ovládacího prvku <xref:System.Windows.Controls.TextBox> ovládacích prvků je přiřazena odpovídající <xref:System.Windows.Forms.Label> ovládacího prvku. Pokud uživatel klikne **zrušit**, <xref:System.Windows.Forms.Label.Text%2A> hodnoty jsou nastavené na výchozí řetězce.  
  
 Na následující tlačítko Přidat kód obslužných rutin událostí k klikněte na `Form1` třídy.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 Sestavte a spusťte aplikaci. Přidejte nějaký text do složeného ovládacího prvku WPF a potom klikněte na tlačítko **OK**. Text se zobrazí v popiscích. V tomto okamžiku kódu nebyla přidána ke zpracování přepínačů.  
  
### <a name="modifying-the-appearance-of-the-control"></a>Změna vzhledu ovládacího prvku  
 <xref:System.Windows.Forms.RadioButton> Ovládacích prvků na formuláři vám umožní uživateli změnit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také několik vlastností písma barvy popředí a pozadí složeného ovládacího prvku. Barva pozadí je zveřejněný prostřednictvím <xref:System.Windows.Forms.Integration.ElementHost> objektu. Zbývající vlastnosti jsou vystaveny jako vlastní vlastnosti ovládacího prvku.  
  
 Klikněte dvakrát na každé <xref:System.Windows.Forms.RadioButton> ovládacího prvku na formulář pro vytvoření <xref:System.Windows.Forms.RadioButton.CheckedChanged> obslužných rutin událostí. Nahradit <xref:System.Windows.Forms.RadioButton.CheckedChanged> obslužné rutiny události s následujícím kódem.  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 Sestavte a spusťte aplikaci. Klikněte na různé přepínače a vidět její účinek na složeného ovládacího prvku WPF.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
