---
title: Přehled datových vazeb
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
ms.openlocfilehash: 1b34b3369e5a045f45251d3285f10bf74b6f0d33
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080849"
---
# <a name="data-binding-overview"></a>Přehled datových vazeb
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vytváření datových vazeb nabízí jednoduchý a konzistentní způsob pro aplikace k zobrazení a interakci s daty. Elementy mohou být vázány na data z různých zdrojů dat ve formě [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty a [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s jako <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.ItemsControl>s jako <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ListView> mají integrované funkce, které umožňují flexibilní styly jednotlivých datových položek nebo kolekce datových položek. Řazení, filtrování a zobrazení skupiny můžete generovat na data.  
  
 Funkci datové vazby v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má několik výhod oproti tradičním modelů, včetně celou řadu vlastností, které ze své podstaty podporují flexibilní datová vazba [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vyjádření data a obchodní oddělit logiku z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Toto téma popisuje první koncepty na základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pak přejde do použití a datové vazby <xref:System.Windows.Data.Binding> třídy a další funkce datovou vazbu.  
  
  
<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Co je datové vazby?  
 Datová vazba je proces, který vytvoří připojení mezi aplikací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a obchodní logiky. Pokud data poskytuje správné oznámení vazbu se správným nastavením, potom, když se data změní jeho hodnotu prvky, které jsou vázány na data změny projeví automaticky. Datové vazby může také znamenat, že pokud se změní vnější znázornění dat v elementu, pak podkladová data mohly automaticky aktualizovat tak, aby odrážely změny. Například, pokud uživatel upravuje hodnotu v <xref:System.Windows.Controls.TextBox> element podkladové hodnoty dat se automaticky aktualizuje tak, aby odrážela tuto změnu.  
  
 Typické použití datových vazeb se umístí do formuláře nebo jiný server nebo místní konfigurační data [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládacích prvků. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tento koncept je rozšířen, aby zahrnoval vazby celou řadu vlastností k řadě zdrojů dat. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vlastnosti závislosti prvků může být vázaný na [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty (včetně [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] objekty nebo objekty přidružené k webových služeb a webových vlastnosti) a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.  
  
 Příklad datové vazby, podívejte se na následující aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [ukázku vazby dat](https://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Snímek obrazovky ukázkové vazby dat](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Výše je uvedeno [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikace, která zobrazuje seznam položek aukce. Aplikace ukazuje následující funkce datové vazby:  
  
-   Obsah <xref:System.Windows.Controls.ListBox> je vázán na kolekci *AuctionItem* objekty. *AuctionItem* objekty mají vlastnosti, jako *popis*, *StartPrice*, *StartDate*, *kategorie*, *SpecialFeatures*atd.  
  
-   Data (*AuctionItem* objekty) zobrazí v <xref:System.Windows.Controls.ListBox> je bez vizuálního vzhledu, tak, aby popis a aktuální ceny jsou platné pro každou položku. To se provádí pomocí <xref:System.Windows.DataTemplate>. Kromě toho vzhled každé položky závisí na *SpecialFeatures* hodnotu *AuctionItem* zobrazení. Pokud *SpecialFeatures* hodnotu *AuctionItem* je *barva*, položka má modrým ohraničením. Pokud je hodnota *zvýrazněte*, položka má oranžovou ohraničení a hvězdičku. [Data Šablonování](#data_templating) část obsahuje informace o data šablon.  
  
-   Uživatel může skupině, filtrování nebo seřadit data s využitím <xref:System.Windows.Controls.CheckBox>es k dispozici. Na obrázku výše, "Seskupit podle kategorie" a "Řazení podle kategorie a datum" <xref:System.Windows.Controls.CheckBox>es jsou vybrány. Mohli jste si všimnout, že data jsou seskupena podle kategorie produktu a název kategorie je v abecedním pořadí. Je obtížné Všimněte si, že z bitové kopie, ale položky jsou také seřazené podle počáteční datum v rámci každé kategorie. To se provádí pomocí *zobrazení kolekce*. [Připojení ke kolekcím](#binding_to_collections) část popisuje zobrazení kolekcí.  
  
-   Když uživatel vybere položku, <xref:System.Windows.Controls.ContentControl> zobrazí podrobnosti vybrané položky. Tento postup se nazývá *hlavní-podrobnosti scénář*. [Hlavní-podrobnosti scénář](#master_detail_scenario) část obsahuje informace o tomto typu scénáře vazby.  
  
-   Typ *StartDate* vlastnost <xref:System.DateTime>, která vrací datum, které zahrnuje dobu milisekundách. V této aplikaci vlastní převaděč se použil tak, aby se zobrazí kratší řetězec data. [Převod dat](#data_conversion) část obsahuje informace o převaděče.  
  
 Pokud uživatel klikne *přidat produkt* tlačítko, následující formulář se zobrazí:  
  
 ![Přidat stránku výpis produktů](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Uživatel, upravte pole ve formuláři, ve verzi preview výpis produktů pomocí podrobnější podokna ve verzi preview a krátký ve verzi preview a klikněte na *odeslat* přidat nový výpis produktů. Všechny existující seskupování, filtrování a řazení funkce bude vztahovat na nové položky. V tomto konkrétním případě se zobrazí položka zadaná ve výše uvedeném jako druhá položka v rámci *počítače* kategorie.  
  
 Nezobrazují se na tomto obrázku je logiku ověřování k dispozici v *datum zahájení* <xref:System.Windows.Controls.TextBox>. Pokud uživatel zadá neplatný datum (neplatné formátováním nebo na datum v minulosti), budete upozorněni uživatele s <xref:System.Windows.Controls.ToolTip> a červeným vykřičníkem vedle <xref:System.Windows.Controls.TextBox>. [Ověření dat](#data_validation) část popisuje, jak vytvořit logiku ověřování.  
  
 Před přechodem do různých funkcí datové vazby uvedeno výš, se nejprve probereme v další části základní koncepty, které jsou důležité k porozumění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby.  
  
## <a name="basic-data-binding-concepts"></a>Koncepty vazeb základní Data  
  
 Bez ohledu na to, jaký element jsou vazby a povaze zdroje dat, každý vazby vždy řídí modelem návodu na následujícím obrázku:  
  
 ![Diagram základní datové vazby](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 Vidíte na obrázku výše, datové vazby je v podstatě most mezi vaší cíl vazby a zdrojem vazby. Na obrázku ukazuje následující základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncepty vazeb dat:  
  
-   Obvykle má každá vazba těmto čtyřem komponentám: cílový objekt binding, cílová vlastnost, zdrojem vazby, který a cestu k hodnotě ve zdroji vazby použít. Například, pokud chcete vytvořit vazbu obsah <xref:System.Windows.Controls.TextBox> k *název* vlastnost *zaměstnance* objektu, cílový objekt má <xref:System.Windows.Controls.TextBox>, je vlastnost target <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, je hodnota, která má použít *název*, a je zdrojovým objektem *zaměstnance* objektu.  
  
-   Vlastnost target musí být vlastnost závislosti. Většina <xref:System.Windows.UIElement> vlastnosti jsou vlastnosti závislosti a většina vlastnosti závislosti, s výjimkou těch jen pro čtení podporují datové vazby ve výchozím nastavení. (Pouze <xref:System.Windows.DependencyObject> typy můžete definovat vlastnosti závislosti a všechny <xref:System.Windows.UIElement>s jsou odvozeny z <xref:System.Windows.DependencyObject>.)  
  
-   I když není zadaný obrázek, je třeba poznamenat, že vazba zdrojový objekt není omezena na právě vlastní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Datová vazba podporuje data ve formě [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Poskytnout příklady, může být váš zdroj vazby <xref:System.Windows.UIElement>, libovolný objekt seznamu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt, který je přidružený [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] dat nebo webové služby nebo XmlNode, který obsahuje vaše [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data. Další informace najdete v tématu [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Při prohlížení prostřednictvím jiné [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] témat, je dobré si uvědomit, že pokud vytvoříte vazbu, jsou vazby cíl vazby *k* zdroj vazby. Například, pokud zobrazujete některé základní [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data v <xref:System.Windows.Controls.ListBox> použití datových vazeb, jsou vazby vaše <xref:System.Windows.Controls.ListBox> k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.  
  
 K vytvoření vazby, můžete použít <xref:System.Windows.Data.Binding> objektu. Zbývající část tohoto tématu popisuje řadu konceptům spojeným s a některé vlastnosti a využití <xref:System.Windows.Data.Binding> objektu.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Směr toku dat  
 Jak už bylo zmíněno dříve a je uvedené šipka na obrázku výše, tok dat vazbu může přecházet od cíl vazby ke zdroji vazby (například zdrojová hodnota změní, když uživatel upraví hodnotu <xref:System.Windows.Controls.TextBox>) a/nebo ze zdroje vazby pro cíl vazby (například vaší <xref:System.Windows.Controls.TextBox> obsah získá aktualizovaný o změny ve zdroji vazby) Pokud zdroj vazby obsahuje správné oznámení.  
  
 Můžete chtít vaše aplikace umožňuje uživatelům změnit data a šíří zpět do zdrojového objektu. Nebo možná chcete povolit uživatelům aktualizovat zdroj dat. To můžete řídit tak, že nastavíte <xref:System.Windows.Data.Binding.Mode%2A> vlastnictví vaší <xref:System.Windows.Data.Binding> objektu. Následující obrázek znázorňuje různé typy toku dat:  
  
 ![Tok dat datové vazby](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> Vazba způsobí, že změny zdrojové vlastnosti se automaticky aktualizovat vlastnost target, ale změny cílové vlastnosti nejsou šířeny zpět do vlastnost source. Tento typ vazby je vhodné v případě vázaného ovládacího prvku je implicitně jen pro čtení. Například může vytvoření vazby ke zdroji, jako je například běžícími nebo možná cílovou vlastnost nemá žádný ovládací prvek rozhraní pro provádění změn, jako je například barvu pozadí vázané na data v tabulce. Pokud není nutné ke sledování změn vlastnost target, pomocí <xref:System.Windows.Data.BindingMode.OneWay> vazby režimu zabraňuje nároky <xref:System.Windows.Data.BindingMode.TwoWay> režimu vazby.  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> Vazba způsobí, že změny vlastnost source nebo vlastnost target automaticky aktualizovat druhý. Tento typ vazby je vhodný pro upravitelné formuláře nebo jiných plně interaktivní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře. Většina vlastností ve výchozím nastavení <xref:System.Windows.Data.BindingMode.OneWay> vazby, ale některé vlastnosti závislostí (obvykle vlastnosti upravovat uživatelské ovládací prvky, jako <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> vlastnost <xref:System.Windows.Controls.CheckBox>) výchozí <xref:System.Windows.Data.BindingMode.TwoWay> vazby. Programový způsob, jak určit, zda vlastnost závislosti váže jednosměrné nebo obousměrné ve výchozím nastavení je zobrazíte vlastnosti metadat pomocí vlastnosti <xref:System.Windows.DependencyProperty.GetMetadata%2A> a zkontrolujte logickou hodnotu <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> vlastnost.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> je opakem <xref:System.Windows.Data.BindingMode.OneWay> vazby; aktualizuje vlastnost source při změně vlastnosti cíl. Jeden příklad scénáře je, pokud je potřeba jenom znovu vyhodnotit hodnotu zdroje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Není znázorněné na obrázku je <xref:System.Windows.Data.BindingMode.OneTime> vazby, což způsobí, že vlastnost source inicializovat vlastnost target, ale následné změny nejsou rozšířena. To znamená, že pokud kontext dat při změně nebo objektu v kontextu změny dat, pak tato změna se neprojeví v vlastnost target. Tento typ vazby je vhodný, pokud používáte dat, kde je vhodné použít snímek aktuálního stavu nebo je skutečně statická data. Tento typ vazby je také užitečné, pokud chcete inicializovat vaše cílová vlastnost s některá z hodnot z vlastnosti zdroje a kontext dat není předem známý. To je v podstatě jednodušší forma <xref:System.Windows.Data.BindingMode.OneWay> vazby, která poskytuje lepší výkon v případech, kde zdrojové hodnoty nezmění.  
  
 Všimněte si, že ke zjištění změny zdroje (pro <xref:System.Windows.Data.BindingMode.OneWay> a <xref:System.Windows.Data.BindingMode.TwoWay> vazby), zdroj musí implementovat mechanismus oznámení změn vhodné vlastnosti, jako <xref:System.ComponentModel.INotifyPropertyChanged>. Zobrazit [implementace oznámení změn vlastností](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) příklad <xref:System.ComponentModel.INotifyPropertyChanged> implementace.  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Stránka vlastností poskytuje další informace o vazbách režimech a příklad toho, jak k určení směru vazby.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Co aktualizací zdroje triggery  
 Vazby, které jsou <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> naslouchání v cílové vlastnosti a jejich šíření zpět do zdroje. To se označuje jako zdroj aktualizace. Například může upravit text do textového pole. Chcete-li změnit hodnotu podkladového zdroje. Jak je popsáno v předchozí části, směr toku dat je určen hodnotou <xref:System.Windows.Data.Binding.Mode%2A> vlastnost vazby.  
  
 Však zdrojovou hodnotu aktualizován při úpravách text nebo po dokončení úprav textu a přesuňte ukazatel myši mimo textového pole? <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost vazby Určuje, co spustí aktualizaci zdroje. Tečky vpravo šipky na následujícím obrázku ukazují role <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost:  
  
 ![UpdateSourceTrigger diagram](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 Pokud <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, pak hodnota odkazuje pravou šipku <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> co nejdříve změny vlastností cílové aktualizuje vazby. Ale pokud <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, pak tato hodnota pouze získá aktualizováno s novou hodnotu, pokud vlastnost target ztratí fokus.  
  
 Podobně jako <xref:System.Windows.Data.Binding.Mode%2A> vlastnost různých závislostí vlastnosti mají různé výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnoty. Výchozí hodnota pro většinu vlastností závislostí je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. To znamená, že zdroj aktualizacím obvykle dochází vždy, když cíl změny vlastností, které je v pořádku pro <xref:System.Windows.Controls.CheckBox>es a jiných jednoduché ovládací prvky. Ale pro textová pole, aktualizace po každém stisknutí klávesy může snížit výkon a zakazuje uživateli obvykle příležitost backspace a oprava překlepů před potvrzením na novou hodnotu. To je důvod, proč <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> místo <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Najdete v článku <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránku vlastností pro informace o tom, jak najít výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> změní hodnota vlastnosti závislosti.  
  
 Následující tabulka uvádí příklad scénáře pro každou <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu pomocí <xref:System.Windows.Controls.TextBox> jako příklad:  
  
|Hodnota UpdateSourceTrigger|Pokud zdrojová hodnota aktualizována|Ukázkový scénář pro textové pole|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (výchozí pro <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Když ovládací prvek textové pole ztratí fokus.|A <xref:System.Windows.Controls.TextBox> , který je přidružen logiku ověřování (viz část ověření dat)|  
|PropertyChanged|Při psaní do <xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox> ovládací prvky v okně chatovací místnosti|  
|explicitní|Když aplikace volá <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox> ovládací prvky v Upravitelný formulář (aktualizace zdrojové hodnoty pouze v případě, že uživatel klikne na tlačítko Odeslat)|  
  
 Příklad najdete v tématu [řídit, kdy k aktualizaci textu TextBox zdroji](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Vytvoření vazby  
  
 Skladovaná některé koncepty popsané v předchozích částech, je vytvořit vazbu pomocí <xref:System.Windows.Data.Binding> objektu a každý vazby obvykle má čtyř komponent: vazba cíl, cílová vlastnost, zdroj vazby a cestu na zdrojové hodnoty použití. Tato část popisuje, jak vytvořit vazbu.  
  
 Podívejte se na následující příklad, ve kterém je zdrojový objekt vazby třídu s názvem *Mojedata* , která je definována v *SDKSample* oboru názvů. Pro demonstrační účely *Mojedata* třída nemá řetězcovou vlastnost s názvem *ColorName*, ze které je hodnota nastavena na hodnotu "Red". Proto tento příklad vygeneruje tlačítko s červenou na pozadí.  
  
 [!code-xaml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Podrobné informace o syntaxi deklarace vazby a příklady, jak vytvořit vazby v kódu najdete v tématu [přehled deklarací vazeb](../../../../docs/framework/wpf/data/binding-declarations-overview.md).  
  
 Pokud používáme v tomto příkladu pro naši základní diagram, výsledná hodnota vypadá takto. Jedná se <xref:System.Windows.Data.BindingMode.OneWay> vazby, protože vlastnost pozadí podporuje <xref:System.Windows.Data.BindingMode.OneWay> vazby ve výchozím nastavení.  
  
 ![Diagram datové vazby](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 Budete divit, proč tento postup funguje, i když *ColorName* je vlastnost typu řetězec při <xref:System.Windows.Controls.Control.Background%2A> vlastnost je typu <xref:System.Windows.Media.Brush>. Toto je výchozí převod typů v práci a je podrobněji popsána [převod dat](#data_conversion) oddílu.  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Určení zdroje připojení  
 Všimněte si, že v předchozím příkladu je zdroj vazby určený nastavením <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.Button> Poté dědí <xref:System.Windows.FrameworkElement.DataContext%2A> hodnotu <xref:System.Windows.Controls.DockPanel>, což je svého nadřízeného elementu. Zdůrazňujeme, zdrojového objektu vazby je jedním z čtyři nezbytné komponenty položky vazbu. Proto bez vazby zdrojového objektu na zadané, vazba by Neprovádět žádnou akci.  
  
 Existuje několik způsobů určení zdrojového objektu vazby. Použití <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti nadřazeného elementu je užitečné, když vytváříte vazbu více vlastností ke stejnému zdroji. Ale v některých případech může být vhodnější k určení zdroje připojení na deklarace jednotlivých připojení. Předchozí příklad, namísto použití <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost, můžete určit zdroje připojení tak, že nastavíte <xref:System.Windows.Data.Binding.Source%2A> vlastnost přímo u vazby deklarace tlačítka, jako v následujícím příkladu:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Kromě nastavení <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost v elementu přímo, dědění <xref:System.Windows.FrameworkElement.DataContext%2A> hodnotu nadřazeným (jako je například tlačítko v prvním příkladu) a nastavením explicitního určení zdroje připojení <xref:System.Windows.Data.Binding.Source%2A> vlastnost <xref:System.Windows.Data.Binding> (například tlačítko v poslední příkladu), můžete použít také <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost nebo <xref:System.Windows.Data.Binding.RelativeSource%2A> vlastnosti k určení zdroje připojení. <xref:System.Windows.Data.Binding.ElementName%2A> Vlastnost je užitečná, pokud se vazba na další prvky v aplikaci, třeba když používáte ovládací prvek posuvník šířku tlačítka. <xref:System.Windows.Data.Binding.RelativeSource%2A> Vlastnost je užitečná, pokud vazba je zadaný v <xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.Style>. Další informace najdete v tématu [určení zdroje vazby](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Zadání cesty k hodnotě  
 Pokud je zdrojem vazby objektu, můžete použít <xref:System.Windows.Data.Binding.Path%2A> vlastnosti a určit tak hodnota, která má použít pro vaše připojení. Pokud se vazba na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, použijete <xref:System.Windows.Data.Binding.XPath%2A> vlastnosti a určit tak hodnotu. V některých případech může být platných pro používání <xref:System.Windows.Data.Binding.Path%2A> vlastnost i v případě, že vaše data jsou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Například pokud chcete získat přístup vlastnost Name atributu vrácené XmlNode (jako výsledek dotazu XPath), měli byste použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost kromě <xref:System.Windows.Data.Binding.XPath%2A> vlastnost.  
  
 Informace o syntaxi a příklady najdete v tématu <xref:System.Windows.Data.Binding.Path%2A> a <xref:System.Windows.Data.Binding.XPath%2A> stránky vlastností.  
  
 Všimněte si, že i když budeme mít oznámil, <xref:System.Windows.Data.Binding.Path%2A> hodnotu použití je jedním z čtyři nezbytné komponenty položky vazby ve scénářích, které chcete vytvořit vazbu na celý objekt, hodnotu by být stejný jako zdrojový objekt vazby. V těchto případech se vztahuje k není zadán <xref:System.Windows.Data.Binding.Path%2A>. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-xaml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Výše uvedený příklad používá syntaxi prázdné vazby: {Binding}. V takovém případě <xref:System.Windows.Controls.ListBox> DataContext dědí z nadřazeného elementu DockPanel (není vidět v tomto příkladu). Když se cesta nezadá, výchozí hodnota je vytvořit vazbu na celý objekt. Jinými slovy, v tomto příkladu cesta byla ponechána protože jsme vazby <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost na celý objekt. (Viz [připojení ke kolekcím](#binding_to_collections) části Podrobné informace.)  
  
 Než vazby ke kolekci, tento scénář je také vhodný Pokud chcete vytvořit vazbu na celý objekt namísto pouze jedné vlastnosti objektu. Například pokud zdrojový objekt je typu řetězec a můžete jednoduše chtít vytvořit vazbu na samotný řetězec. Další z typických možností je, pokud chcete vytvořit vazbu prvek na objekt s více vlastnostmi.  
  
 Všimněte si, že budete muset použít vlastní logiku, aby data má smysl pro vaše vlastností cíle. Vlastní logiky může být v podobě vlastního převaděče (pokud ještě neexistuje výchozí typ převodu). Zobrazit [převod dat](#data_conversion) informace o převaděče.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Vazby a BindingExpression  
 Před získáním do dalších funkcích a použití datových vazeb, bylo by užitečné zavést <xref:System.Windows.Data.BindingExpression> třídy. Protože jste viděli v předchozích částech <xref:System.Windows.Data.Binding> třída je základní třídou pro deklaraci vazbu; <xref:System.Windows.Data.Binding> třída poskytuje mnoho vlastností, které vám umožňují určit vlastnosti vazby. Související třídy <xref:System.Windows.Data.BindingExpression>, je základní objekt, který udržuje propojení mezi zdrojem a cílem. Vazba obsahuje všechny informace, které mohou být sdíleny napříč několika výrazy vazby. A <xref:System.Windows.Data.BindingExpression> je výraz instance, které nemohou být sdíleny a obsahuje všechny instance informace <xref:System.Windows.Data.Binding>.  
  
 Představte si třeba následující příkaz, kde *myDataObject* je instance *Mojedata* třídy *myBinding* je zdrojem <xref:System.Windows.Data.Binding> objektu a *Mojedata* třída je definované třídou, která obsahuje řetězec vlastnost s názvem *MyDataProperty*. Tento příklad vytvoří vazbu obsah textu *mytext*, instance <xref:System.Windows.Controls.TextBlock>do *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Můžete použít stejný *myBinding* objekt k vytvoření jiných vazbách. Například můžete použít *myBinding* objekt k vytvoření vazby textový obsah zaškrtnutím políčka *MyDataProperty*. V tomto scénáři bude existovat dvě instance <xref:System.Windows.Data.BindingExpression> sdílení *myBinding* objektu.  
  
 A <xref:System.Windows.Data.BindingExpression> objektu můžete získat prostřednictvím vrácenou hodnotu volání funkce <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> na objekt vázaný na data. Následující témata ukazují některé z použití <xref:System.Windows.Data.BindingExpression> třídy:  
  
-   [Získání objektu vazby ze svázané cílové vlastnosti](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [Určení, kdy dojde k aktualizaci zdroje textem TextBox](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Převod dat  
 V předchozím příkladu je červené tlačítko protože jeho <xref:System.Windows.Controls.Control.Background%2A> vlastnost je vázána na řetězcovou vlastnost s hodnotou "Red". Tento postup funguje, protože konvertor typu je k dispozici na <xref:System.Windows.Media.Brush> typ převést na hodnotu řetězce <xref:System.Windows.Media.Brush>.  
  
 Chcete-li přidat tyto informace pro obrázek v [vytváření vazby](#creating_a_binding) části diagramu vypadá takto:  
  
 ![Diagram datové vazby](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 Co když, ale namísto toho, aby vlastnost typu řetězec má váš zdrojový objekt vazby *barva* vlastnost typu <xref:System.Windows.Media.Color>? V takovém případě v pořadí pro vytvoření vazby na pracovní je třeba do prvního zapnutí *barva* hodnotu vlastnosti na něco jiného, který <xref:System.Windows.Controls.Control.Background%2A> tato vlastnost přijímá parametry. Je třeba vytvořit vlastní převaděč implementací <xref:System.Windows.Data.IValueConverter> rozhraní, jako v následujícím příkladu:  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> Referenční stránce poskytuje další informace.  
  
 Teď se používá vlastní převaděč namísto výchozí převod a naše diagram vypadá takto:  
  
 ![Diagram datové vazby](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 Zdůrazňujeme, mohou být převody výchozí k dispozici z důvodu převaděče typů, které se nacházejí v typu svázaný s. Toto chování bude záviset na které převaděče typů jsou dostupné na cíli. Pokud máte pochybnosti, vytvořte vlastní převaděče.  
  
 Toto jsou některé typické scénáře, kdy je vhodné implementovat převaděč dat.:  
  
-   Vaše data budou zobrazeny odlišně, v závislosti na jazykové verzi. Například můžete chtít implementovat konvertor měny nebo převaděč kalendáře datum a čas na základě hodnoty nebo standardy používaných pro konkrétní jazykovou verzi.  
  
-   Data se používají není nutně určené ke změně textu hodnoty vlastnosti, ale je místo toho v úmyslu změnit jinou hodnotu, jako je například zdroj bitové kopie, nebo barva nebo styl zobrazení textu. Převaděče je možné v tomto případě převedením vazby vlastnosti, která nemusí být vhodný, jako je například vytváření vazby textové pole na vlastnost pozadí buňky tabulky.  
  
-   Více než jeden ovládací prvek nebo na více vlastností ovládacích prvků jsou vázány na stejná data. V takovém případě primární vazby může být jen zobrazení textu, že jiných vazbách zpracování problémů konkrétního zobrazení, ale dál používat stejné vazbě jako informace o zdroji.  
  
-   Zatím jsme ještě se nezabývali <xref:System.Windows.Data.MultiBinding>, kde má cílovou vlastnost kolekce vazby. V případě třídy <xref:System.Windows.Data.MultiBinding>, používat vlastní <xref:System.Windows.Data.IMultiValueConverter> vytvoří konečnou hodnotu z hodnoty vazby. Například mohou být vypočítány barvu z červené, modré a zelená hodnoty, které můžou být hodnoty z objektů vazby stejného nebo jiného zdroje. Zobrazit <xref:System.Windows.Data.MultiBinding> třídy stránky příklady a informace.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Připojení ke kolekcím  
  
 Zdrojový objekt vazby lze zacházet, jako jednoho objektu z nichž všechny vlastnosti obsahují data nebo jako shromažďování dat polymorfní objektů, které jsou často seskupeny dohromady (například výsledek dotazu do databáze). Zatím pouze výše vazby pro jednotlivé objekty, však vazba pro shromažďování dat je běžný scénář. Příklad typických možností je použít <xref:System.Windows.Controls.ItemsControl> , jako <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, nebo <xref:System.Windows.Controls.TreeView> zobrazíte shromažďování dat, například v aplikaci zobrazí v [co je datová vazba?](#what_is_data_binding) části.  
  
 Naštěstí naše základní diagram stále platí. Pokud vytváříte vazbu <xref:System.Windows.Controls.ItemsControl> do kolekce, diagram vypadá takto:  
  
 ![Vytváření datových vazeb ItemsControl diagram](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 Jak je znázorněno v tomto diagramu pro vytvoření vazby <xref:System.Windows.Controls.ItemsControl> na objekt kolekce <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> je vlastnost použít. Můžete si představit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost jako obsah <xref:System.Windows.Controls.ItemsControl>. Všimněte si, že je vazba <xref:System.Windows.Data.BindingMode.OneWay> vzhledem k tomu, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> podporuje vlastnost <xref:System.Windows.Data.BindingMode.OneWay> vazby ve výchozím nastavení.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Implementace kolekce  
 Můžete zobrazit výčet přes jakoukoli kolekci, která implementuje <xref:System.Collections.IEnumerable> rozhraní. Však nastavení dynamické vazby, vložení nebo odstranění v kolekci aktualizovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticky, kolekce musí implementovat <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Toto rozhraní poskytuje událost, která by měla být vyvolána při každé změně zdrojové kolekce.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy, která je integrovaná provádění shromažďování dat, který zpřístupňuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Všimněte si, že pro úplnou podporu přenášení dat hodnotami z objekty zdroje do cíle, každý objekt v kolekci, která podporuje vlastnosti umožňující vazbu musí implementovat taky <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Před implementací vlastní kolekce, zvažte použití <xref:System.Collections.ObjectModel.ObservableCollection%601> nebo jeden z existující kolekce tříd, například <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, a <xref:System.ComponentModel.BindingList%601>, mezi mnoha dalších. Pokud jste pokročilý scénář a chcete implementovat vlastní kolekci, zvažte použití <xref:System.Collections.IList>, která poskytuje negenerická kolekce objektů, které je jednotlivě přístupný index a tím zajištění nejlepšího výkonu.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Zobrazení kolekcí  
 Jakmile vaše <xref:System.Windows.Controls.ItemsControl> je vázán na shromažďování dat, můžete chtít třídění, filtrování nebo skupiny data. K tomuto účelu použijte zobrazení kolekcí, které jsou třídy, které implementují <xref:System.ComponentModel.ICollectionView> rozhraní.  
  
  
#### <a name="what-are-collection-views"></a>Jaké jsou zobrazení kolekcí?  
 Zobrazení kolekce je vrstva nad zdrojovou kolekci vazby, který umožňuje procházení a zobrazení zdrojové kolekce založené na řazení, filtrování a skupiny dotazů, aniž byste museli změnit základní zdrojové kolekce. Zobrazení kolekce také uchovává ukazatel na aktuální položku v kolekci. Pokud zdrojové kolekce implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní, změny vyvolané <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> události se rozšíří na zobrazení.  
  
 Protože zobrazení neměňte základní zdrojové kolekce, kolekce každý zdroj může mít více zobrazení s ním spojená. Například může mít kolekce *úloh* objekty. S použitím zobrazení můžete zobrazit ke stejným datům různými způsoby. Na levé straně stránky můžete například zobrazit úkoly seřazené podle priority a na pravé straně, seskupené podle oblasti.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Postup vytvoření zobrazení  
 Jedním ze způsobů, jak vytvořit a používat zobrazení je přímo vytvořit instanci objektu view a použít je jako zdroj vazby. Představte si třeba [ukázku vazby dat](https://go.microsoft.com/fwlink/?LinkID=163703) aplikace znázorněný [co je datová vazba?](#what_is_data_binding) části. Aplikace je implementováno tak, aby <xref:System.Windows.Controls.ListBox> váže k zobrazení nad shromažďováním dat namísto shromažďování dat přímo. V následujícím příkladu se extrahují z [ukázku vazby dat](https://go.microsoft.com/fwlink/?LinkID=163703) aplikace. <xref:System.Windows.Data.CollectionViewSource> Třída je [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] proxy, která dědí z třídy <xref:System.Windows.Data.CollectionView>. V tomto konkrétním příkladu <xref:System.Windows.Data.CollectionViewSource.Source%2A> zobrazení je vázán *AuctionItems* kolekce (typu <xref:System.Collections.ObjectModel.ObservableCollection%601>) aktuálního objektu aplikace.  
  
 [!code-xaml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 Prostředek *listingDataView* pak slouží jako zdroj vazby pro prvky v aplikaci, jako <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Chcete-li vytvořit další zobrazení pro jednu kolekci, můžete vytvořit jiný <xref:System.Windows.Data.CollectionViewSource> instance a zadejte pro něj jiný `x:Key` název.  
  
 V následující tabulce jsou uvedeny typy dat zobrazení, které jsou vytvořeny jako výchozí zobrazení kolekce nebo za <xref:System.Windows.Data.CollectionViewSource> podle typu kolekce zdroje.  
  
|Zdrojový typ kolekce|Typ zobrazení kolekce|Poznámky|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Vnitřní typ na základě <xref:System.Windows.Data.CollectionView>|Nelze seskupit položky.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Nejrychlejší.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Použití výchozí zobrazení  
 Zadání zobrazení kolekce jako zdrojem vazby, který je jedním ze způsobů, jak vytvořit a používat zobrazení kolekce. WPF také vytvoří výchozí kolekci zobrazení pro každou kolekci se používá jako zdroj vazby. Pokud svážete přímo do kolekce, WPF se váže k jeho výchozí zobrazení. Všimněte si, že toto výchozí zobrazení sdílí všechny vazby do stejné kolekce, takže ke změně výchozího zobrazení podle jednoho vázaného ovládacího prvku nebo kódu (jako je například řazení nebo ke změně aktuální položky ukazatel prodiskutována později) se projeví v jiných vazbách do stejné kolekce.  
  
 Načtení výchozího zobrazení, použijte <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metody. Příklad najdete v tématu [získat výchozí zobrazení datové kolekce](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Zobrazení kolekcí s ADO.NET DataTables  
 Kvůli zvýšení výkonu se zobrazení kolekce pro technologii ADO.NET <xref:System.Data.DataTable> nebo <xref:System.Data.DataView> objekty delegovat, řazení a filtrování, abyste <xref:System.Data.DataView>. To způsobí, že řazení a filtrování, abyste sdílet mezi všechny kolekce zobrazení zdroje dat. Povolit zobrazení jednotlivých kolekcí k řazení a filtrováni nezávisle na sobě, inicializovat každé kolekci zobrazení vlastní <xref:System.Data.DataView> objektu.  
  
#### <a name="sorting"></a>Řazení  
 Jak už bylo uvedeno dříve, můžete zobrazení použít pořadí řazení kolekce. Protože existuje ve zdrojové kolekce, vaše data může nebo nemusí mít odpovídající vlastní pořadí. Zobrazení nad shromažďováním umožňuje ukládat objednávky, nebo změňte výchozí pořadí na základě kritérií porovnání, které zadáte. Protože je na základě klienta zobrazení dat, běžný scénář, kdy se uživatel může chtít řadit sloupce tabulkových dat na hodnotu, která odpovídá sloupci. Použití zobrazení, tento uživatel řízené řazení lze použít, znovu bez jakýchkoli změn zdrojová kolekce nebo dokonce museli dotaz na obsah kolekce. Příklad najdete v tématu [řazení GridView sloupce při kliknutí na záhlaví](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 Následující příklad ukazuje logiku řazení "Řazení podle kategorie a datum" <xref:System.Windows.Controls.CheckBox> aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) části:  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrování  
 Zobrazení můžete také použít filtr do kolekce. To znamená, že i když položka mohou existovat v kolekci, toto konkrétní zobrazení slouží k zobrazení jenom určité podmnožiny na plné kolekci. Můžete filtrovat na podmínky v datech. Například tak, jak se provádí aplikace v [co je datová vazba?](#what_is_data_binding) části "Zobrazit pouze bargains" <xref:System.Windows.Controls.CheckBox> obsahuje logiku a vyfiltrovat položky, které nákladů 25 USD nebo více. Následující kód se spustí, chcete-li nastavit *ShowOnlyBargainsFilter* jako <xref:System.Windows.Data.CollectionViewSource.Filter> obslužné rutiny události při, který <xref:System.Windows.Controls.CheckBox> je vybrán:  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* obslužná rutina události má následující implementaci:  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Pokud používáte některou <xref:System.Windows.Data.CollectionView> třídy přímo namísto tohoto <xref:System.Windows.Data.CollectionViewSource>, můžete využít <xref:System.Windows.Data.CollectionView.Filter%2A> vlastnosti a určit tak zpětné volání. Příklad najdete v tématu [filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Seskupování  
 S výjimkou vnitřní třída, která se zobrazí <xref:System.Collections.IEnumerable> kolekce, všechna zobrazení kolekce podporují funkce pro seskupení, který umožňuje uživateli oddílu kolekce v zobrazení kolekce do logických skupin. Skupiny můžou být explicitní, pokud uživatel zadává seznam skupin, nebo implicitní, přičemž skupiny jsou dynamicky generované v závislosti na data.  
  
 Následující příklad ukazuje logiky "Seskupit podle kategorie" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Další příklad seskupení, naleznete v tématu [seskupení položek v ListView, že implementuje GridView](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Ukazatele na aktuální položku  
 Zobrazení také podporují pojem s aktuální položkou. Můžete procházet objekty v zobrazení kolekce. Lze při procházení, přesouváte položky ukazatel, který vám umožní načíst objekt, který v této konkrétní umístění v kolekci existuje. Příklad najdete v tématu [přejít přes objektů v datech CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Protože WPF vytvoří vazbu na kolekce, mají všechny vazby na kolekce pouze pomocí zobrazení (zobrazení, které zadáte, nebo kolekci výchozí zobrazení), aktuální položky ukazatel. Při vytváření vazeb k zobrazení, v znak lomítka ("/") `Path` hodnota označuje aktuální položky zobrazení. V následujícím příkladu je kontext dat zobrazení kolekce. První řádek vytvoří vazbu na kolekce. Druhý řádek vytvoří vazbu na aktuální položku v kolekci. Třetí řádek vytvoří vazbu `Description` vlastnosti aktuální položky v kolekci.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Syntaxe lomítko a vlastnost může být také skládaný k procházení hierarchie kolekce. Následující příklad vytvoří vazbu na aktuální položku kolekce s názvem `Offices`, který je součástí aktuální položky zdrojové kolekce.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Ukazatel na aktuální položky mohou být ovlivněny žádné řazení nebo filtrování, který se použije ke kolekci. Řazení zachová aktuální položky ukazatel na poslední položka vybrána, ale zobrazení kolekcí je teď změnili kolem něj. (Možná se vybraná položka byla na začátku seznamu před, ale teď může být vybrané položky se někde uprostřed.) Filtrování zachová vybrané položky, pokud výběr zůstává v zobrazení po filtrování. V opačném případě ukazatel na aktuální položku nastavena na první položky zobrazení filtrované kolekcí.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Scénář vazby seznam podrobnosti  
 Pojem s aktuální položkou je užitečné, nejen pro navigaci položek v kolekci, ale také pro scénář vazby seznam podrobnosti. Vezměte v úvahu aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) části znovu. V této aplikaci, vybrat v rámci <xref:System.Windows.Controls.ListBox> určuje obsahu je znázorněno <xref:System.Windows.Controls.ContentControl>. Vložit jiným způsobem, při <xref:System.Windows.Controls.ListBox> výběru položky <xref:System.Windows.Controls.ContentControl> zobrazuje podrobnosti o vybrané položce.  
  
 Scénář hlavní podrobnosti můžete implementovat jednoduše tak, že dva nebo více ovládacích prvků vázaných na stejném zobrazení. Následující příklad z [ukázku vazby dat](https://go.microsoft.com/fwlink/?LinkID=163703) ukazuje z kódu <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> se zobrazí v aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) části:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Všimněte si, že oba ovládací prvky jsou vázána ke stejnému zdroji *listingDataView* statický prostředek (viz definice tohoto prostředku v [postup vytvoření zobrazení části](#how_to_create_a_view)). Tento postup funguje, protože když je objekt typu singleton ( <xref:System.Windows.Controls.ContentControl> v tomto případě) je vázán na kolekci zobrazení, se automaticky váže k <xref:System.Windows.Data.CollectionView.CurrentItem%2A> zobrazení. Všimněte si, že <xref:System.Windows.Data.CollectionViewSource> objekty automaticky synchronizovat, měny a výběr. Pokud váš ovládací prvek seznamu není vázán na <xref:System.Windows.Data.CollectionViewSource> objektu jako v následujícím příkladu, je nutné nastavit jeho <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` aby to fungovalo.  
  
 Další příklady najdete v tématu [připojení ke kolekci a zobrazení informací podle výběru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) a [použití vzoru seznam-podrobnosti s hierarchickými daty](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Mohli jste si všimnout, že výše uvedený příklad používá šablonu. Data by ve skutečnosti zobrazí tak, jak bychom ale bez použití šablony (explicitně používají <xref:System.Windows.Controls.ContentControl> a, která implicitně používá <xref:System.Windows.Controls.ListBox>). Nyní jsme zapnout na šablonování data v další části.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Šablon dat  
 Bez použití šablony, naši aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) oddílu by vypadat nějak takto:  
  
 ![Ukázka datové vazby bez datové šablony](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 Jak je znázorněno v příkladu v předchozí části, jak <xref:System.Windows.Controls.ListBox> ovládacího prvku a <xref:System.Windows.Controls.ContentControl> je vázána na objekt celou kolekci (nebo přesněji řečeno, zobrazení přes objekt kolekce) z *AuctionItem*s. Bez konkrétní pokyny o tom, jak zobrazit shromažďování dat <xref:System.Windows.Controls.ListBox> zobrazuje řetězcovou reprezentaci jednotlivých objektů v kolekci základní a <xref:System.Windows.Controls.ContentControl> zobrazena řetězcová reprezentace je vázán na objekt.  
  
 Pro vyřešení tohoto problému je aplikace definuje <xref:System.Windows.DataTemplate>s. Jak je znázorněno v příkladu v předchozí části, <xref:System.Windows.Controls.ContentControl> explicitně používá *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. <xref:System.Windows.Controls.ListBox> Ovládací prvek implicitně používá následující <xref:System.Windows.DataTemplate> při zobrazení *AuctionItem* objektů v kolekci:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Pomocí těchto dvou <xref:System.Windows.DataTemplate>s, je výsledný uživatelské rozhraní z článku [co je datová vazba?](#what_is_data_binding) části. Jak vidíte z tohoto snímku obrazovky, kromě povolení umístit data ve své ovládací prvky <xref:System.Windows.DataTemplate>s umožňují definovat zajímavé vizuály pro vaše data. Například <xref:System.Windows.DataTrigger>s se používají v uvedeném <xref:System.Windows.DataTemplate> tak, aby *AuctionItem*s *SpecialFeatures* hodnotu *zvýrazněte* by se mělo zobrazit oranžové ohraničení a hvězdičku.  
  
 Další informace o šablonách dat, najdete v článku [přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Ověřování dat  
  
 Většina aplikací, které přijímají uživatelský vstup musí být logiku ověřování k zajištění, aby uživatel zadal očekávané informace. Ověřovací kontroly můžete podle typu, rozsah, formát nebo další požadavky specifické pro aplikaci. Tato část popisuje, jak funguje ověřování dat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Přidružení pravidel ověřování s vazbou  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vazby modelu dat vám umožní přidružit <xref:System.Windows.Data.Binding.ValidationRules%2A> s vaší <xref:System.Windows.Data.Binding> objektu. Například následující příklad vytvoří vazbu <xref:System.Windows.Controls.TextBox> vlastnost s názvem `StartPrice` a přidá <xref:System.Windows.Controls.ExceptionValidationRule> objektu <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> vlastnost.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 A <xref:System.Windows.Controls.ValidationRule> objekt kontroluje, zda je platná hodnota vlastnosti. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má následující dva typy integrovanou <xref:System.Windows.Controls.ValidationRule> objekty:  
  
-   A <xref:System.Windows.Controls.ExceptionValidationRule> kontroluje výjimky vyvolané při aktualizaci vlastnosti zdroje vazby. V předchozím příkladu `StartPrice` je typu integer. Když uživatel zadá hodnotu, která se nedá převést na celé číslo, je vyvolána výjimka, způsobí vazby označen jako neplatný. Alternativní syntaxi nastavení <xref:System.Windows.Controls.ExceptionValidationRule> explicitně, je nastavit <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> vlastnost `true` na vaše <xref:System.Windows.Data.Binding> nebo <xref:System.Windows.Data.MultiBinding> objektu.  
  
-   A <xref:System.Windows.Controls.DataErrorValidationRule> objekt kontroluje chyby, které jsou generovány objekty, které implementují <xref:System.ComponentModel.IDataErrorInfo> rozhraní. Příklad použití toto ověřovací pravidlo, najdete v části <xref:System.Windows.Controls.DataErrorValidationRule>. Alternativní syntaxi nastavení <xref:System.Windows.Controls.DataErrorValidationRule> explicitně, je nastavit <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> vlastnost `true` na vaše <xref:System.Windows.Data.Binding> nebo <xref:System.Windows.Data.MultiBinding> objektu.  
  
 Můžete také vytvořit vlastní ověřovací pravidlo odvozené z <xref:System.Windows.Controls.ValidationRule> třídy a implementace <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody. Následující příklad ukazuje pravidlem, které používá *přidat produkt výpis* "Datum zahájení" <xref:System.Windows.Controls.TextBox> z [co je datová vazba?](#what_is_data_binding) části:  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> používá toto *FutureDateRule*, jak je znázorněno v následujícím příkladu:  
  
 [!code-xaml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Upozorňujeme, že <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, aktualizuje modul vazby zdrojovou hodnotu při každém stisknutí klávesy, což znamená, že ho také kontroly v každé pravidlo <xref:System.Windows.Data.Binding.ValidationRules%2A> kolekce při každém stisknutí klávesy. To dál probereme v části procesu ověřování.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Poskytuje vizuální zpětnou vazbu  
 Pokud uživatel zadá neplatnou hodnotu, můžete zadat svůj názor. o chybu v aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Jedním ze způsobů, k poskytování zpětné vazby, je nastavit <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> přidružená vlastnost vlastní <xref:System.Windows.Controls.ControlTemplate>. Jak je znázorněno v předchozí pododdílu *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> používá <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> volá *validationTemplate*. Následující příklad ukazuje definici *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Prvek určuje umístění ovládacího prvku se opatřený.  
  
 Kromě toho můžete také použít <xref:System.Windows.Controls.ToolTip> zobrazíte chybovou zprávu. Obě *StartDateEntryForm* a *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es použít styl *textStyleTextBox*, která vytvoří <xref:System.Windows.Controls.ToolTip> , který Zobrazí se chybová zpráva. Následující příklad ukazuje definici *textStyleTextBox*. Připojená vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je `true` když jeden nebo více vazby na vlastnosti elementu vazby jsou chybné.  
  
 [!code-xaml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 S vlastním <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a <xref:System.Windows.Controls.ToolTip>, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> vypadá podobně jako následující, když dojde k chybě ověřování:  
  
 ![Chyba ověřování dat vazby](../../../../docs/framework/wpf/data/media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Pokud vaše <xref:System.Windows.Data.Binding> má přidruženou ověřovacích pravidel, ale nezadáte <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> na vázaného ovládacího prvku, výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> se použije k upozornit uživatele, když dojde k chybě ověřování. Výchozí hodnota <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> je šablonu ovládacího prvku, který definuje červené ohraničení ve vrstvě doplněk pro úpravy. S výchozím <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a <xref:System.Windows.Controls.ToolTip>, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> vypadá podobně jako následující, když dojde k chybě ověřování:  
  
 ![Chyba ověřování dat vazby](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Příklad toho, jak poskytnout logiku pro ověření všechny ovládací prvky v dialogovém okně, najdete v části vlastní dialogová okna v [přehled dialogových oken](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Proces ověření  
 Ověření obvykle dochází při převodu hodnoty cílové vlastnosti zdroje vazby. Tato akce probíhá v <xref:System.Windows.Data.BindingMode.TwoWay> a <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby. Zdůrazňujeme, co způsobí, že zdroj aktualizace závisí na hodnotě <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost, jak je popsáno v [co triggery zdroje aktualizací](#what_triggers_source_updates) oddílu.  
  
 Následující text popisuje *ověření* procesu. Všimněte si, že pokud kdykoli během tohoto procesu dojde k chybě ověření nebo jiný typ chyby, je zastavení procesu.  
  
1.  Vazby zkontroluje, jestli jsou všechny vlastní <xref:System.Windows.Controls.ValidationRule> definované objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena na <xref:System.Windows.Controls.ValidationStep.RawProposedValue> pro daný <xref:System.Windows.Data.Binding>, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu na každý <xref:System.Windows.Controls.ValidationRule> dokud jeden z nich spustí došlo k chybě nebo dokud všechny z nich předejte.  
  
2.  Vazby pak zavolá převaděč, pokud existuje.  
  
3.  Pokud bude úspěšné převaděč, vazby kontroluje, pokud neexistují žádné vlastní <xref:System.Windows.Controls.ValidationRule> definované objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> pro daný <xref:System.Windows.Data.Binding>, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu na každý <xref:System.Windows.Controls.ValidationRule> , který má <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> dokud jeden z nich spustí došlo k chybě nebo všechny z nich předejte.  
  
4.  Vazby nastaví vlastnost source.  
  
5.  Vazby zkontroluje, jestli jsou všechny vlastní <xref:System.Windows.Controls.ValidationRule> definované objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> pro daný <xref:System.Windows.Data.Binding>, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu na každý <xref:System.Windows.Controls.ValidationRule> , který má <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> dokud jeden z nich spustí došlo k chybě nebo všechny z nich předejte. Pokud <xref:System.Windows.Controls.DataErrorValidationRule> souvisí s vazbou a jeho <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena na výchozí hodnotu <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, <xref:System.Windows.Controls.DataErrorValidationRule> se v tuto chvíli kontroluje. Toto je také bod při vazeb, které mají <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nastavena na `true` nebyly zvoleny.  
  
6.  Vazby zkontroluje, jestli jsou všechny vlastní <xref:System.Windows.Controls.ValidationRule> definované objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena na <xref:System.Windows.Controls.ValidationStep.CommittedValue> pro daný <xref:System.Windows.Data.Binding>, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu na každý <xref:System.Windows.Controls.ValidationRule> , který má <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.CommittedValue> dokud jeden z nich spustí došlo k chybě nebo všechny z nich předejte.  
  
 Pokud <xref:System.Windows.Controls.ValidationRule> nepředává kdykoli během tohoto procesu vytvoří modul vazby <xref:System.Windows.Controls.ValidationError> objektu a přidá jej do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekce elementu vazby. Před vazby modul spouští <xref:System.Windows.Controls.ValidationRule> objekty na libovolný daný krok se odebere všechny <xref:System.Windows.Controls.ValidationError> , který byl přidán do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> přidružená vlastnost elementu vazby během tohoto kroku. Například pokud <xref:System.Windows.Controls.ValidationRule> jehož <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> se nezdařilo, při příštím procesu ověření dojde, vazby, který odebere <xref:System.Windows.Controls.ValidationError> bezprostředně před volání některé <xref:System.Windows.Controls.ValidationRule> , který má <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Když <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> není prázdná, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojená vlastnost elementu, který je nastavená na `true`. Také pokud <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> vlastnost <xref:System.Windows.Data.Binding> je nastavena na `true`, pak vydá modul vazby <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> připojené události u elementu.  
  
 Všimněte si také, vymaže přenos platnou hodnotu v obou směrech (cílový zdroj nebo zdroje do cíle) <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> přidružená vlastnost.  
  
 Pokud má vazbu <xref:System.Windows.Controls.ExceptionValidationRule> s ním spojená, nebo měl <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> je nastavena na `true` a při vazba modul nastaví zdroj, je vyvolána výjimka, modul vazby zkontroluje, jestli je <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Máte možnost k použití <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> zpětné volání, které poskytují vlastní obslužné rutiny pro zpracování výjimek. Pokud <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> není zadaná v <xref:System.Windows.Data.Binding>, vytvoří modul vazby <xref:System.Windows.Controls.ValidationError> s výjimkou a přidá jej do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekce elementu vazby.  
  
## <a name="debugging-mechanism"></a>Mechanismus ladění  
 Připojená vlastnost lze nastavit <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> související vazby objektu získat informace o stavu konkrétní vazby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DataErrorValidationRule>  
 [Novinky ve verzi 4.5 grafického subsystému WPF](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Vytvoření vazby k výsledkům dotazu LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Ukázka vazby dat](https://go.microsoft.com/fwlink/?LinkID=163703)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Vytvoření vazby ke zdroji dat ADO.NET](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)
