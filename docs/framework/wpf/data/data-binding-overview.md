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
ms.openlocfilehash: 44a35131273c6f191ab5da5bc1639d97bd961ff1
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567515"
---
# <a name="data-binding-overview"></a>Přehled datových vazeb
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]datové vazby poskytují jednoduchý a konzistentní způsob, jak aplikace prezentovat a interagovat s daty. Prvky mohou být vázány na data z nejrůznějších zdrojů dat ve formě objektů modulu CLR (Common Language Runtime) a [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>například <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.ItemsControl>mají integrovanoufunkcionalitu,kteráumožňujeflexibilnístyljednotlivýchdatovýchpoložeknebokolekcídatovýchpoložek.<xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView> Zobrazení řazení, filtrování a seskupování lze vytvořit nad daty.  
  
 Funkce datové vazby v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má několik výhod oproti tradičním modelům, včetně široké škály vlastností, které v podstatě podporují datové vazby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , flexibilní reprezentace dat a čisté oddělení podnikání. logika z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 V tomto tématu se nejdřív pojednává [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o konceptech základu datových vazeb a následném <xref:System.Windows.Data.Binding> použití třídy a dalších funkcí vazby dat.  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Co je datová vazba?  
 Datová vazba je proces, který vytváří propojení mezi aplikací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a obchodní logikou. Pokud má vazba správné nastavení a data poskytují správná oznámení, pak při změně své hodnoty prvky, které jsou vázány na data, se automaticky projeví změny v prvcích svázaných s daty. Vazba dat také znamená, že pokud se změní vnější reprezentace dat v prvku, pak se podkladová data dají automaticky aktualizovat, aby odrážela změnu. Například pokud uživatel upraví hodnotu v <xref:System.Windows.Controls.TextBox> prvku, podkladová datová hodnota se automaticky aktualizuje, aby odrážela tuto změnu.  
  
 Typickým použitím datové vazby je umístit data serveru nebo místní konfigurační data do formulářů nebo jiných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládacích prvků. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]je tento koncept rozbalený tak, aby zahrnoval vazby široké škály vlastností do nejrůznějších zdrojů dat. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroji mohou být vlastnosti závislosti prvků svázány s objekty CLR (včetně objektů ADO.NET nebo objektů spojených s webovými službami a webovými vlastnostmi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ) a daty.  
  
 Příklad datové vazby najdete v následující aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [ukázce datové vazby](https://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Snímek obrazovky ukázek datových vazeb](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Výše je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikace, která zobrazuje seznam položek aukce. Aplikace demonstruje následující funkce datové vazby:  
  
- Obsah objektu <xref:System.Windows.Controls.ListBox> je svázán s kolekcí objektů *AuctionItem* . Objekt *AuctionItem* má vlastnosti, jako je *Popis*, *StartPrice*, *StartDate*, *kategorie*, *SpecialFeatures*atd.  
  
- Data (objekty*AuctionItem* ) zobrazená v <xref:System.Windows.Controls.ListBox> je šablonovaná tak, aby se pro každou položku zobrazoval popis a aktuální cena. To se provádí pomocí <xref:System.Windows.DataTemplate>. Kromě toho vzhled každé položky závisí na hodnotě *SpecialFeatures* *AuctionItem* , která se zobrazuje. Pokud je hodnota *SpecialFeatures* pro *AuctionItem* *Color*, položka má modrý okraj. Pokud je hodnota *zvýrazněna*, má položka oranžové ohraničení a hvězdičku. Část [data šablonování](#data_templating) poskytuje informace o šablonování dat.  
  
- Uživatel může data seskupit, filtrovat nebo seřadit pomocí <xref:System.Windows.Controls.CheckBox>poskytnutých ES. Na obrázku výše jsou vybrány "seskupit podle kategorie" a "seřadit podle kategorie a datum" <xref:System.Windows.Controls.CheckBox>ES. Možná jste si všimli, že se data seskupují podle kategorie produktu a název kategorie je v abecedním pořadí. Z obrázku je obtížné si všimnout, ale položky jsou také seřazené podle počátečního data v rámci každé kategorie. To se provádí pomocí *zobrazení kolekce*. Část [vazba na kolekce](#binding_to_collections) popisuje zobrazení kolekcí.  
  
- Když uživatel vybere položku, zobrazí se <xref:System.Windows.Controls.ContentControl> podrobnosti o vybrané položce. Toto se nazývá *scénář hlavní-podrobnosti*. V části [scénář hlavní-podrobnosti](#master_detail_scenario) najdete informace o tomto typu scénáře vazby.  
  
- Typ vlastnosti *StartDate* je <xref:System.DateTime>, což vrátí datum, které obsahuje čas do milisekundy. V této aplikaci se použil vlastní převaděč, aby se zobrazil kratší řetězec data. V části [Převod dat](#data_conversion) jsou k dispozici informace o převaděčích.  
  
 Když uživatel klikne na tlačítko *Přidat produkt* , dojde k následujícímu formuláři:  
  
 ![Přidat stránku se seznamem produktů](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Uživatel může upravit pole ve formuláři, zobrazit náhled seznamu produktů pomocí krátké verze Preview a podrobnějších podoken náhledu a potom kliknutím na *Odeslat* přidat nový seznam produktů. Veškeré existující funkce seskupování, filtrování a řazení budou platit pro novou položku. V tomto konkrétním případě se položka zadaná do výše uvedeného obrázku zobrazí jako druhá položka v kategorii *počítač* .  
  
 Nezobrazuje se v tomto obrázku je logika ověřování poskytnutá v *počátečním datu* <xref:System.Windows.Controls.TextBox>. Pokud uživatel zadá neplatné datum (neplatné formátování nebo minulé datum), bude uživatel upozorněn s <xref:System.Windows.Controls.ToolTip> a červeným vykřičníkem vedle. <xref:System.Windows.Controls.TextBox> Část [ověření dat](#data_validation) popisuje, jak vytvořit logiku ověřování.  
  
 Předtím, než přejdete k různým funkcím datových vazeb, které jsou uvedené výše, se nejprve podíváme v další části základních konceptů, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou důležité pro porozumění datové vazbě.  
  
## <a name="basic-data-binding-concepts"></a>Základní koncepty datových vazeb  
  
 Bez ohledu na to, který prvek vytvoříte, a povaze zdroje dat, každá vazba vždy následuje za modelem znázorněným následujícím obrázkem:  
  
 ![Diagram, který zobrazuje model základní datové vazby.](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 Jak je znázorněno na obrázku výše, vazba dat je v podstatě most mezi cílem vaší vazby a zdrojem vazby. Obrázek ukazuje následující základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncepty vázání dat:  
  
- Každá vazba obvykle má tyto čtyři komponenty: objekt cíle vazby, cílovou vlastnost, zdroj vazby a cestu k hodnotě ve zdroji vazby, která se má použít. Například pokud chcete vytvořit svázání <xref:System.Windows.Controls.TextBox> obsahu s vlastností *Name* objektu *Employee* <xref:System.Windows.Controls.TextBox>, cílový objekt je, vlastnost <xref:System.Windows.Controls.TextBox.Text%2A> target je vlastnost, která se má použít, je hodnota *název*a zdrojový objekt je objekt *zaměstnance* .  
  
- Vlastnost target musí být vlastnost závislosti. Většina <xref:System.Windows.UIElement> vlastností je vlastnosti závislosti a většina vlastností závislosti, s výjimkou oprávnění jen pro čtení, ve výchozím nastavení podporují datové vazby. (Vlastnosti <xref:System.Windows.DependencyObject> závislostí můžou definovat jenom typy a <xref:System.Windows.UIElement>všechny s odvozenými z <xref:System.Windows.DependencyObject>.)  
  
- Přestože není zadáno na obrázku, je třeba poznamenat, že zdrojový objekt vazby není omezen na vlastní objekt CLR. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]datová vazba podporuje data ve formě objektů CLR a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Chcete-li poskytnout několik příkladů, váš zdroj vazby může <xref:System.Windows.UIElement>být objektem typu list, objektem CLR, který je spojen s ADO.NET daty nebo webovými službami nebo XmlNode obsahující vaše [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data. Další informace najdete v tématu [Přehled zdrojů vazby](binding-sources-overview.md).  
  
 Při čtení pomocí jiných témat sady SDK je důležité si uvědomit, že při vytváření vazby je nutné svázat cíl vazby *se* zdrojem vazby. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Například pokud zobrazujete některá podkladová data <xref:System.Windows.Controls.ListBox> v datové vazbě, budete mít <xref:System.Windows.Controls.ListBox> k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] datům vazbu.  
  
 Chcete-li vytvořit vazbu, použijte <xref:System.Windows.Data.Binding> objekt. Zbývající část tohoto tématu popisuje mnoho konceptů přidružených k a některé z vlastností a použití <xref:System.Windows.Data.Binding> objektu.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Směr toku dat  
 Jak už bylo uvedeno výše a na obrázku výše vidíte, tok dat vazby může přejít z cíle vazby na zdroj vazby (například když uživatel upraví hodnotu a <xref:System.Windows.Controls.TextBox>) a/nebo ze zdroje vazby. do cíle vazby (například když se obsah bude <xref:System.Windows.Controls.TextBox> aktualizovat se změnami ve zdroji vazby), pokud zdroj vazby poskytuje správná oznámení.  
  
 Můžete chtít, aby vaše aplikace uživatelům povolila změnu dat a rozšířila ji zpátky do zdrojového objektu. Nebo možná nebudete chtít povolit uživatelům aktualizovat zdrojová data. To můžete řídit nastavením <xref:System.Windows.Data.Binding.Mode%2A> vlastnosti <xref:System.Windows.Data.Binding> objektu. Následující obrázek znázorňuje různé typy toku dat:  
  
 ![Tok dat datových vazeb](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay>vazba způsobí, že změny vlastnosti source automaticky aktualizují cílovou vlastnost, ale změny vlastnosti target nejsou rozšířeny zpět do vlastnosti source. Tento typ vazby je vhodný v případě, že ovládací prvek, který je svázán, je implicitně určen jen pro čtení. Například můžete vytvořit vazbu ke zdroji, jako je burzovní, nebo možná vaše cílová vlastnost nemá žádné řídicí rozhraní pro provádění změn, jako je například barva pozadí vázané na data tabulky. Pokud nepotřebujete monitorovat změny vlastnosti target, vyhněte se režii v <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> režimu vytváření vazeb pomocí režimu vazby.  
  
- <xref:System.Windows.Data.BindingMode.TwoWay>Při vytvoření vazby dojde ke změně vlastnosti source nebo vlastnosti target na hodnotu automaticky aktualizovat druhou. Tento typ vazby je vhodný pro upravitelné formuláře nebo jiné plně interaktivní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře. <xref:System.Windows.Data.BindingMode.OneWay> Většina vlastností má výchozí hodnotu Binding, ale některé vlastnosti závislosti (obvykle vlastnosti ovládacích prvků upravitelných uživatelem, jako <xref:System.Windows.Controls.TextBox.Text%2A> je vlastnost <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> vlastnost <xref:System.Windows.Controls.CheckBox>), jsou nastavené jako výchozí .<xref:System.Windows.Data.BindingMode.TwoWay> vazba. Programový způsob, jak určit, zda je vlastnost závislosti svázána jednosměrná nebo obousměrná ve výchozím nastavení, získá metadata vlastnosti vlastnosti pomocí <xref:System.Windows.DependencyProperty.GetMetadata%2A> a poté zkontroluje logickou hodnotu <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> vlastnosti.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource>je opakem <xref:System.Windows.Data.BindingMode.OneWay> vazby. při změně vlastnosti target aktualizuje vlastnost source. Jedním z příkladů scénářů je, že pokud potřebujete znovu vyhodnotit zdrojovou hodnotu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]z.  
  
- Není znázorněno na obrázku je <xref:System.Windows.Data.BindingMode.OneTime> vazba, což způsobí, že vlastnost source inicializuje cílovou vlastnost, ale následné změny se nešíří. To znamená, že pokud se v datovém kontextu nahraje změna nebo dojde ke změně objektu v kontextu dat, změna se neprojeví ve vlastnosti target. Tento typ vazby je vhodný v případě, že používáte data, která jsou vhodná pro použití snímku aktuálního stavu, nebo jsou data skutečně statická. Tento typ vazby je vhodný také v případě, že chcete inicializovat cílovou vlastnost s určitou hodnotou ze zdrojové vlastnosti a datový kontext není známý předem. To je v podstatě jednodušší forma <xref:System.Windows.Data.BindingMode.OneWay> vazby, která poskytuje lepší výkon v případech, kdy se zdrojová hodnota nemění.  
  
 Všimněte si, že pro detekci změn ve <xref:System.Windows.Data.BindingMode.OneWay> zdroji <xref:System.Windows.Data.BindingMode.TwoWay> (platí pro a vazby) musí zdroj implementovat vhodný mechanismus pro oznamování změn <xref:System.ComponentModel.INotifyPropertyChanged>vlastností, jako je například. Příklad<xref:System.ComponentModel.INotifyPropertyChanged> implementace naleznete v tématu [implementace oznámení o změně vlastností](how-to-implement-property-change-notification.md) .  
  
 Stránka <xref:System.Windows.Data.Binding.Mode%2A> vlastností poskytuje další informace o režimech vazby a příklad, jak určit směr vazby.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Jaké aktualizace zdroje triggerů  
 Vazby, které <xref:System.Windows.Data.BindingMode.TwoWay> jsou <xref:System.Windows.Data.BindingMode.OneWayToSource> nebo naslouchají změnám ve vlastnosti target a šíří je zpátky do zdroje. Tento postup se označuje jako aktualizace zdroje. Můžete například upravit text textového pole, aby se změnila zdrojová hodnota zdroje. Jak je popsáno v poslední části, směr toku dat je určen hodnotou <xref:System.Windows.Data.Binding.Mode%2A> vlastnosti vazby.  
  
 Při úpravách textu nebo po dokončení úprav textu a přesunutí ukazatele myši z textového pole se ale vaše zdrojová hodnota aktualizuje. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost vazby Určuje, která aktivuje aktualizaci zdroje. V bodech pravé šipky vpravo na následujícím obrázku je znázorněna role <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnosti:  
  
 ![Diagram, který zobrazuje roli vlastnosti UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 <xref:System.Windows.Data.BindingMode.TwoWay> Pokud je <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota, pak hodnota, na kterou se odkazuje šipka vpravo, nebo se budou <xref:System.Windows.Data.BindingMode.OneWayToSource> aktualizovat, jakmile se změní cílová vlastnost. <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> Pokud <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> je<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>však hodnota, pak tato hodnota bude aktualizována pouze s novou hodnotou, pokud cílová vlastnost ztratí fokus.  
  
 Podobně jako <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> u vlastnostimajírůznévlastnostizávislosti<xref:System.Windows.Data.Binding.Mode%2A> jiné výchozí hodnoty. Výchozí hodnota pro většinu vlastností závislosti je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, <xref:System.Windows.Controls.TextBox.Text%2A> zatímco vlastnost <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>má výchozí hodnotu. To znamená, že ke zdrojovým aktualizacím obvykle dochází vždy při změně vlastnosti target, <xref:System.Windows.Controls.CheckBox>což je dobré pro ES a další jednoduché ovládací prvky. Nicméně pro textová pole, která se aktualizují po stisku klávesy, se může snížit výkon a uživatel bude odepřít normální možnost Backspace a opravit chyby před potvrzením nové hodnoty. Proto <xref:System.Windows.Controls.TextBox.Text%2A> má vlastnost výchozí <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> hodnotu místo <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Informace o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> tom, jak najít výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vlastnosti závislosti, najdete na stránce vlastností.  
  
 Následující tabulka uvádí vzorový scénář pro každou <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu <xref:System.Windows.Controls.TextBox> pomocí příkladu jako příklad:  
  
|Hodnota UpdateSourceTrigger|Když se zdrojová hodnota aktualizuje|Ukázkový scénář pro textové pole|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (výchozí pro <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Když ovládací prvek TextBox ztratí fokus|<xref:System.Windows.Controls.TextBox> Přidružený k logice ověřování (viz část ověření dat)|  
|PropertyChanged|Při psaní do<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>ovládací prvky v okně chatovací místnosti|  
|Explicitně|Při volání aplikace<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>ovládací prvky ve upravitelném formuláři (aktualizuje zdrojové hodnoty jenom v případě, že uživatel klikne na tlačítko Odeslat)|  
  
 Příklad naleznete v tématu [Control When a text TextBox Update source](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Vytvoření vazby  
  
 Chcete-li recapitulate některé z konceptů popsaných v předchozích částech, vytvořte vazbu pomocí <xref:System.Windows.Data.Binding> objektu a každá vazba obvykle má čtyři součásti: cíl vazby, cílovou vlastnost, zdroj vazby a cestu ke zdrojové hodnotě, která se má použít. Tato část popisuje, jak nastavit vazbu.  
  
 Vezměte v úvahu následující příklad, ve kterém je zdrojový objekt vazby třída s názvem *Mojedata* , která je definována v oboru názvů *SDKSample* . Pro demonstrační účely má třída *Mojedata* vlastnost String s názvem *Color*, jejíž hodnota je nastavená na Red. Proto tento příklad vygeneruje tlačítko s červeným pozadím.  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Další podrobnosti o syntaxi deklarace vazby a příklady, jak nastavit vazbu v kódu, najdete v tématu [Přehled deklarací vazeb](binding-declarations-overview.md).  
  
 Pokud tento příklad použijeme pro náš základní diagram, bude výsledný obrázek vypadat jako na následujícím obrázku. Toto je <xref:System.Windows.Data.BindingMode.OneWay> vazba, protože vlastnost Background podporuje <xref:System.Windows.Data.BindingMode.OneWay> ve výchozím nastavení vazby.  
  
 ![Diagram, který zobrazuje vlastnost pozadí datové vazby.](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 <xref:System.Windows.Media.Brush> Pokud<xref:System.Windows.Controls.Control.Background%2A> je vlastnost Color typu String, je možné, že budete chtít, aby to fungovalo i v případě, že je vlastnost typu řetězec. Toto je výchozí převod typu v práci a je popsán v části [Převod dat](#data_conversion) .  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Určení zdroje vazby  
 Všimněte si, že v předchozím příkladu je zdroj vazby určen nastavením <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti <xref:System.Windows.Controls.DockPanel> prvku. Pak zdědí hodnotu z<xref:System.Windows.Controls.DockPanel>, která je jeho nadřazeným prvkem. <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.Button> Pro opakování iterace je zdrojový objekt vazby jednou ze čtyř nezbytných komponent vazby. Proto bez zadání zdrojového objektu vazby neprovede vazba nic.  
  
 Existuje několik způsobů, jak zadat zdrojový objekt vazby. <xref:System.Windows.FrameworkElement.DataContext%2A> Použití vlastnosti u nadřazeného elementu je užitečné, pokud vytváříte vazbu více vlastností ke stejnému zdroji. V některých případech ale může být vhodnější zadat zdroj vazby u jednotlivých deklarací vazeb. Pro předchozí příklad namísto použití <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti lze určit zdroj vazby <xref:System.Windows.Data.Binding.Source%2A> nastavením vlastnosti přímo na deklaraci vazby tlačítka, jako v následujícím příkladu:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Kromě nastavení <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti u prvku přímo, dědění <xref:System.Windows.FrameworkElement.DataContext%2A> hodnoty z předchůdce (například tlačítko v prvním příkladu) a explicitní určení zdroje <xref:System.Windows.Data.Binding.Source%2A> vazby nastavením vlastnosti na <xref:System.Windows.Data.Binding> (například tlačítko v posledním příkladu), můžete také použít <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost <xref:System.Windows.Data.Binding.RelativeSource%2A> nebo vlastnost k určení zdroje vazby. Tato <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost je užitečná, pokud vytváříte vazbu na jiné prvky ve vaší aplikaci, například při použití posuvníku k úpravě šířky tlačítka. Vlastnost je užitečná, pokud je vazba určena <xref:System.Windows.Controls.ControlTemplate> v nebo <xref:System.Windows.Style>. <xref:System.Windows.Data.Binding.RelativeSource%2A> Další informace najdete v tématu [určení zdroje vazby](how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Zadání cesty k hodnotě  
 Pokud je zdrojem vazby objekt, použijte <xref:System.Windows.Data.Binding.Path%2A> vlastnost k určení hodnoty, která se má použít pro vazbu. Pokud vytváříte vazbu na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, <xref:System.Windows.Data.Binding.XPath%2A> použijte vlastnost k určení hodnoty. V některých případech může být vhodné použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost i v případě, že jsou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]vaše data. Například pokud chcete získat přístup k vlastnosti název vráceného objektu XmlNode (jako výsledek dotazu XPath), měli byste použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost kromě <xref:System.Windows.Data.Binding.XPath%2A> vlastnosti.  
  
 Informace o syntaxi a příklady naleznete na <xref:System.Windows.Data.Binding.Path%2A> stránkách vlastností a. <xref:System.Windows.Data.Binding.XPath%2A>  
  
 Všimněte si, že i když jsme zdůraznili <xref:System.Windows.Data.Binding.Path%2A> , že hodnota, která se má použít, je jedna ze čtyř nezbytných komponent vazby, ve scénářích, které chcete svázat s celým objektem, by hodnota, která se má použít, byla stejná jako zdrojový objekt vazby. V těchto případech platí, že se nedá zadat <xref:System.Windows.Data.Binding.Path%2A>. Vezměte v úvahu v následujícím příkladu:  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Výše uvedený příklad používá prázdnou syntaxi vazby: {Binding}. V tomto případě <xref:System.Windows.Controls.ListBox> dědí objekt DataContext z nadřazeného elementu DockPanel (nezobrazuje se v tomto příkladu). Není-li zadána cesta, výchozí hodnota je svázána s celým objektem. Jinými slovy, v tomto příkladu byla cesta ponechána, protože je <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost svázána s celým objektem. (Podrobné informace najdete v části [vazba na kolekce](#binding_to_collections) .)  
  
 Kromě vazby ke kolekci je tento scénář také užitečný, pokud chcete vytvořit vazbu k celému objektu místo pouze jediné vlastnosti objektu. Například, pokud je zdrojový objekt typu String a jednoduše chcete vytvořit vazby k samotnému řetězci. Dalším běžným scénářem je, když chcete vytvořit vazby prvku k objektu s několika vlastnostmi.  
  
 Všimněte si, že možná budete muset použít vlastní logiku, aby data byla smysluplná na vlastnost cíle vazby. Vlastní logika může být ve formě vlastního převaděče (pokud převod výchozího typu neexistuje). Informace o převaděčích najdete v tématu [Převod dat](#data_conversion) .  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Vytváření vazeb a pokoušel obnovit BindingExpression  
 Předtím, než se dostanete k dalším funkcím a používání datových vazeb, by bylo užitečné zavést <xref:System.Windows.Data.BindingExpression> třídu. Jak jste viděli v předchozích částech, <xref:System.Windows.Data.Binding> třída je třída vysoké úrovně pro deklaraci vazby <xref:System.Windows.Data.Binding> ; Třída poskytuje mnoho vlastností, které umožňují určit charakteristiky vazby. Související třída <xref:System.Windows.Data.BindingExpression>je základní objekt, který udržuje spojení mezi zdrojem a cílem. Vazba obsahuje všechny informace, které lze sdílet mezi několika výrazy vazby. Je výraz instance, který nelze sdílet a obsahuje všechny informace o <xref:System.Windows.Data.Binding>instanci. <xref:System.Windows.Data.BindingExpression>  
  
 Zvažte například následující, kde *myDataObject* je instancí třídy *Mojedata* , *myBinding* je zdrojový <xref:System.Windows.Data.Binding> objekt a *Mojedata* třída je definována třída, která obsahuje řetězcovou vlastnost s názvem  *MyDataProperty*. Tento příklad váže textový obsah *MyText*, instance <xref:System.Windows.Controls.TextBlock>, na *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Stejný objekt *myBinding* můžete použít k vytvoření dalších vazeb. Například můžete použít objekt *myBinding* k navázání textového obsahu zaškrtávacího políčka na *MyDataProperty*. V takovém případě budou k dispozici dvě instance <xref:System.Windows.Data.BindingExpression> sdílení objektu *myBinding* .  
  
 Objekt lze získat prostřednictvím návratové hodnoty volání <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> objektu vázaného na data. <xref:System.Windows.Data.BindingExpression> Následující témata ukazují některé z použití <xref:System.Windows.Data.BindingExpression> třídy:  
  
- [Získání objektu vazby ze svázané cílové vlastnosti](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [Určení, kdy dojde k aktualizaci zdroje textem TextBox](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Převod dat  
 V předchozím příkladu je tlačítko červené, protože jeho <xref:System.Windows.Controls.Control.Background%2A> vlastnost je svázána s vlastností řetězce s hodnotou "Red". To funguje, protože konvertor typu je přítomen na <xref:System.Windows.Media.Brush> typu pro převod řetězcové hodnoty <xref:System.Windows.Media.Brush>na.  
  
 Chcete-li přidat tyto informace na obrázek v oddílu [vytvoření vazby](#creating_a_binding) , vypadá to, že diagram vypadá takto:  
  
 ![Diagram, který zobrazuje výchozí vlastnost datové vazby.](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 Ale co když místo abyste měli vlastnost typu String, váš zdrojový objekt vazby má vlastnost *Color* typu <xref:System.Windows.Media.Color>? V takovém případě, aby vazba fungovala, musíte nejprve změnit hodnotu vlastnosti *Color* na objekt, který <xref:System.Windows.Controls.Control.Background%2A> vlastnost přijímá. Je nutné vytvořit vlastní převaděč implementací <xref:System.Windows.Data.IValueConverter> rozhraní, jako v následujícím příkladu:  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 Na <xref:System.Windows.Data.IValueConverter> referenční stránce najdete další informace.  
  
 Místo výchozího převodu se teď používá vlastní převaděč a náš diagram vypadá takto:  
  
 ![Diagram znázorňující vlastní převaděč datových vazeb](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 K opakování iterací mohou být výchozí převody k dispozici z důvodu konvertorů typu, které jsou k dispozici v typu vázaného na. Toto chování bude záviset na tom, které převaděče typů jsou v cíli k dispozici. Pokud máte pochybnosti, vytvořte vlastní převaděč.  
  
 Níže jsou uvedeny některé typické scénáře, kdy je vhodné implementovat převaděč dat:  
  
- Vaše data by se měla zobrazit odlišně v závislosti na jazykové verzi. Například můžete chtít implementovat převodník měny nebo převaděč data/času kalendáře na základě hodnot nebo standardů používaných v konkrétní jazykové verzi.  
  
- Použitá data nemusí nutně mít za cíl změnit textovou hodnotu vlastnosti, ale místo toho je třeba změnit jinou hodnotu, jako je například zdroj obrázku nebo barva nebo styl zobrazovaného textu. Převaděče lze v této instanci použít převodem vazby vlastnosti, která pravděpodobně není vhodná, jako je například vazba textového pole na vlastnost pozadí buňky tabulky.  
  
- Více než jeden ovládací prvek nebo více vlastností ovládacích prvků je svázán se stejnými daty. V takovém případě může primární vazba pouze zobrazit text, zatímco jiné vazby zpracovávají konkrétní problémy se zobrazením, ale stále používají stejnou vazbu jako informace o zdroji.  
  
- Zatím jsme ještě nebrali <xref:System.Windows.Data.MultiBinding>na to, kde cílová vlastnost má kolekci vazeb. V případě a <xref:System.Windows.Data.MultiBinding>použijte vlastní <xref:System.Windows.Data.IMultiValueConverter> pro vytvoření konečné hodnoty z hodnot vazeb. Barvy lze například vypočítat z hodnot červené, modré a zelené, což může být hodnoty ze stejných nebo odlišných zdrojových objektů vazby. Příklady a <xref:System.Windows.Data.MultiBinding> informace naleznete na stránce třídy.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Vazba na kolekce  
  
 Zdrojový objekt vazby lze považovat buď za jeden objekt, který vlastnosti obsahují data nebo jako kolekci dat polymorfních objektů, které jsou často seskupeny (například výsledek dotazu do databáze). Zatím jsme probrali pouze vazbu na jednotlivé objekty, ale vazba na shromažďování dat je běžným scénářem. Například běžným scénářem <xref:System.Windows.Controls.ItemsControl> je použít <xref:System.Windows.Controls.ListBox>například, <xref:System.Windows.Controls.ListView>nebo <xref:System.Windows.Controls.TreeView> k zobrazení kolekce dat, například v aplikaci zobrazené v části [co je datová vazba?](#what_is_data_binding) .  
  
 Naštěstí je náš základní diagram stále použit. Pokud vytváříte vazbu <xref:System.Windows.Controls.ItemsControl> ke kolekci, diagram vypadá takto:  
  
 ![Diagram, který zobrazuje objekt ItemsControl datové vazby.](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 Jak je znázorněno v tomto diagramu, pro <xref:System.Windows.Controls.ItemsControl> svázání s objektem kolekce <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , vlastnost je vlastnost, která má být použita. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Vlastnost si můžete představit jako obsah <xref:System.Windows.Controls.ItemsControl>. Všimněte si, že vazba <xref:System.Windows.Data.BindingMode.OneWay> je <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> způsobená tím <xref:System.Windows.Data.BindingMode.OneWay> , že vlastnost ve výchozím nastavení podporuje vazby.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Implementace kolekcí  
 Můžete vytvořit výčet pro libovolnou kolekci, která implementuje <xref:System.Collections.IEnumerable> rozhraní. Chcete-li však nastavit dynamické vazby tak, aby se vložení nebo odstranění v kolekci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticky aktualizovalo, kolekce musí <xref:System.Collections.Specialized.INotifyCollectionChanged> implementovat rozhraní. Toto rozhraní zpřístupňuje událost, která by měla být vyvolána při každé změně příslušné kolekce.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje třídu, která je vestavěnou implementací kolekce dat, která <xref:System.Collections.Specialized.INotifyCollectionChanged> zpřístupňuje rozhraní. <xref:System.Collections.ObjectModel.ObservableCollection%601> Všimněte si, že pro plnou podporu přenosu hodnot dat ze zdrojových objektů na cíle, každý objekt v kolekci, který podporuje vlastnosti s možností vazby, <xref:System.ComponentModel.INotifyPropertyChanged> musí implementovat také rozhraní. Další informace najdete v tématu [Přehled zdrojů vazby](binding-sources-overview.md).  
  
 Před <xref:System.Collections.ObjectModel.ObservableCollection%601> implementací vlastní kolekce zvažte použití nebo jednu z existujících tříd kolekce, <xref:System.Collections.Generic.List%601>například, <xref:System.Collections.ObjectModel.Collection%601>a <xref:System.ComponentModel.BindingList%601>, mezi mnoho dalších. Máte-li pokročilý scénář a chcete implementovat vlastní kolekci, zvažte použití <xref:System.Collections.IList>, které poskytuje neobecnou kolekci objektů, které mohou být jednotlivě k dispozici pomocí indexu a tudíž nejlepšího výkonu.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Zobrazení kolekcí  
 <xref:System.Windows.Controls.ItemsControl> Po navázání na shromažďování dat můžete chtít data řadit, filtrovat nebo seskupovat. K tomu je třeba použít zobrazení kolekce, což jsou třídy, které implementují <xref:System.ComponentModel.ICollectionView> rozhraní.  

#### <a name="what-are-collection-views"></a>Co jsou zobrazení kolekcí?  
 Zobrazení kolekce je vrstva nad kolekcí zdrojů vazby, která umožňuje procházet a zobrazovat zdrojovou kolekci na základě dotazů řazení, filtrování a seskupování, aniž by bylo nutné měnit podkladovou zdrojovou kolekci. Zobrazení kolekce také udržuje ukazatel na aktuální položku v kolekci. Pokud zdrojová kolekce implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní, jsou změny vyvolané <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> událostí rozšířeny do zobrazení.  
  
 Vzhledem k tomu, že zobrazení nemění zdrojové kolekce, ke každé zdrojové kolekci může být přidruženo více zobrazení. Například můžete mít kolekci objektů *Task* . Pomocí zobrazení můžete stejná data zobrazit různými způsoby. Například na levé straně stránky můžete chtít zobrazit úkoly seřazené podle priority a na pravé straně seskupené podle oblasti.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Postup vytvoření zobrazení  
 Jedním ze způsobů, jak vytvořit a použít zobrazení, je vytvořit instanci objektu zobrazení přímo a pak ho použít jako zdroj vazby. Zvažte například ukázkovou aplikaci [datové vazby](https://go.microsoft.com/fwlink/?LinkID=163703) , která je zobrazena v části [co je datová vazba?](#what_is_data_binding) . Aplikace je implementována tak, aby <xref:System.Windows.Controls.ListBox> se místo kolekce dat přímo navázala na zobrazení v rámci shromažďování dat. Následující příklad je extrahován z ukázkové aplikace [datové vazby](https://go.microsoft.com/fwlink/?LinkID=163703) . Třída je proxy třídy, která dědí z <xref:System.Windows.Data.CollectionView>. <xref:System.Windows.Data.CollectionViewSource> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] V tomto konkrétním příkladu <xref:System.Windows.Data.CollectionViewSource.Source%2A> je v zobrazení svázána s kolekcí *AuctionItems* (typu <xref:System.Collections.ObjectModel.ObservableCollection%601>) aktuálního objektu aplikace.  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 *ListingDataView* prostředků pak slouží jako zdroj vazby pro prvky v aplikaci, například <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Chcete-li vytvořit další zobrazení pro stejnou kolekci, můžete vytvořit jinou <xref:System.Windows.Data.CollectionViewSource> instanci a přidělit jí `x:Key` jiný název.  
  
 Následující tabulka ukazuje, které typy dat zobrazení jsou vytvořeny jako výchozí zobrazení kolekce, nebo podle <xref:System.Windows.Data.CollectionViewSource> typu zdrojové kolekce.  
  
|Typ zdrojové kolekce|Typ zobrazení kolekce|Poznámky|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Interní typ založený na<xref:System.Windows.Data.CollectionView>|Položky nelze seskupit.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Způsobem.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Použití výchozího zobrazení  
 Zadání zobrazení kolekce jako zdroje vazby je jedním ze způsobů, jak vytvořit a použít zobrazení kolekce. WPF také vytvoří výchozí zobrazení kolekce pro každou kolekci použitou jako zdroj vazby. Pokud vytváříte vazby přímo ke kolekci, WPF se váže k výchozímu zobrazení. Všimněte si, že toto výchozí zobrazení je sdíleno všemi vazbami stejné kolekce, takže změna ve výchozím zobrazení podle jednoho vázaného ovládacího prvku nebo kódu (například řazení nebo změna na ukazatel aktuální položky, popsaná dále) se projeví ve všech ostatních vazbách ke stejné kolekci.  
  
 Chcete-li získat výchozí zobrazení, použijte <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu. Příklad najdete v tématu [získání výchozího zobrazení sběru dat](how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Zobrazení kolekcí s ADO.NET datatabulkami  
 Pro zlepšení výkonu, zobrazení kolekce pro ADO.NET <xref:System.Data.DataTable> nebo <xref:System.Data.DataView> objekty delegovat <xref:System.Data.DataView>řazení a filtrování na. To způsobí, že řazení a filtrování budou sdíleny napříč všemi zobrazeními kolekce zdroje dat. Chcete-li každé zobrazení kolekce Povolit řazení a filtrování nezávisle, inicializujte každé zobrazení <xref:System.Data.DataView> kolekce vlastním objektem.  
  
#### <a name="sorting"></a>Řazení  
 Jak bylo zmíněno dříve, zobrazení mohou použít řazení do kolekce. V případě, že v příslušné kolekci existuje, vaše data mohou nebo nemusí mít příslušné vlastní pořadí. Zobrazení přes kolekci umožňuje stanovit objednávku nebo změnit výchozí pořadí na základě porovnávacích kritérií, která zadáte. Vzhledem k tomu, že se jedná o zobrazení dat na základě klienta, je běžným scénářem, že uživatel může chtít seřadit sloupce tabulkových dat podle hodnoty, se kterou sloupec odpovídá. Pomocí zobrazení lze toto řazení řízené uživatelem použít, a to bez provedení jakýchkoli změn v podkladové kolekci nebo při opakovaném dotazování na obsah kolekce. Příklad naleznete v tématu [seřazení sloupce GridView při kliknutí na záhlaví](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 Následující příklad ukazuje logiku řazení příkazu "seřadit podle kategorie a data" <xref:System.Windows.Controls.CheckBox> aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v části [co je datová vazba?](#what_is_data_binding) .  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrování  
 Zobrazení mohou také použít filtr na kolekci. To znamená, že i když položka může existovat v kolekci, je toto konkrétní zobrazení určeno k zobrazení pouze určité podmnožiny celé kolekce. Můžete filtrovat podmínku v datech. Například, jak je provedeno aplikací v části [co je datová vazba?](#what_is_data_binding) , <xref:System.Windows.Controls.CheckBox> obsahuje logiku pro odfiltrování položek, které jsou $25 nebo více. Následující kód je spuštěn pro nastavení *ShowOnlyBargainsFilter* jako <xref:System.Windows.Data.CollectionViewSource.Filter> obslužné rutiny události, <xref:System.Windows.Controls.CheckBox> Pokud je vybrána možnost:  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Obslužná rutina události *ShowOnlyBargainsFilter* má následující implementaci:  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Pokud používáte jednu z <xref:System.Windows.Data.CollectionView> tříd přímo <xref:System.Windows.Data.CollectionViewSource>namísto <xref:System.Windows.Data.CollectionView.Filter%2A> , měli byste použít vlastnost k určení zpětného volání. Příklad naleznete [v tématu Filtrování dat v zobrazení](how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Seskupování  
 S výjimkou interní třídy, která zobrazí <xref:System.Collections.IEnumerable> kolekci, všechna zobrazení kolekcí podporují funkci seskupení, která umožňuje uživateli rozdělit kolekci v zobrazení kolekce do logických skupin. Skupiny můžou být explicitní, kde uživatel zadá seznam skupin nebo implicitně, kde se skupiny generují dynamicky v závislosti na datech.  
  
 Následující příklad ukazuje logiku "Group by Category" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Další příklad seskupení naleznete v tématu [Group items in ListView, který implementuje prvek GridView](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Ukazatele aktuální položky  
 Zobrazení také podporují pojem aktuální položky. Můžete procházet objekty v zobrazení kolekce. Při procházení přesunete ukazatel myši na položku, která umožňuje načíst objekt, který existuje v daném umístění v kolekci. Příklad naleznete v tématu [Navigace skrze objekty v CollectionView dat](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Vzhledem k tomu, že WPF váže ke kolekci pouze pomocí zobrazení (buď zadané zobrazení, nebo výchozího zobrazení kolekce), mají všechny vazby na kolekce aktuální ukazatel na položku. Při vytváření vazby k zobrazení označuje znak lomítka ("/") v `Path` hodnotě aktuální položku zobrazení. V následujícím příkladu je kontext dat zobrazením kolekce. První řádek se váže ke kolekci. Druhý řádek vytvoří vazby na aktuální položku v kolekci. Třetí řádek se váže k `Description` vlastnosti aktuální položky v kolekci.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Lomítko a vlastnost lze také navrstveny pro procházení hierarchie kolekcí. V následujícím příkladu se váže k aktuální položce kolekce s názvem `Offices`, která je vlastností aktuální položky zdrojové kolekce.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Ukazatel na aktuální položku může být ovlivněn jakýmkoli řazením nebo filtrováním, které je použito pro kolekci. Při řazení se zachová ukazatel aktuální položky na poslední vybrané položce, ale zobrazení kolekce se teď znovu rozstrukturuje. (Možná vybraná položka byla na začátku seznamu, ale teď může být vybraná položka někde uprostřed.) Filtrování zachová vybranou položku, pokud tento výběr po filtrování zůstane v zobrazení. V opačném případě je ukazatel aktuální položky nastaven na první položku filtrovaného zobrazení kolekce.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Scénář vázání hlavní-podrobnosti  
 Pojem aktuální položky je užitečný nejen pro navigaci položek v kolekci, ale také pro scénář vázání hlavní-podrobnosti. Vezměte v úvahu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikaci v části [co je datová vazba?](#what_is_data_binding) . V této aplikaci výběr v rámci <xref:System.Windows.Controls.ListBox> určuje obsah zobrazený <xref:System.Windows.Controls.ContentControl>v. Chcete-li jej vložit jiným způsobem, je <xref:System.Windows.Controls.ListBox> -li vybrána položka, <xref:System.Windows.Controls.ContentControl> zobrazí se podrobnosti o vybrané položce.  
  
 Scénář hlavní-podrobnosti můžete implementovat jednoduše tak, že se dva nebo více ovládacích prvků sváže se stejným zobrazením. Následující příklad v [ukázce vázání dat](https://go.microsoft.com/fwlink/?LinkID=163703) ukazuje značky <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> , které se zobrazí v aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v části [co je datová vazba?](#what_is_data_binding) .  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Všimněte si, že oba ovládací prvky jsou svázány se stejným zdrojem, statickým prostředkem *listingDataView* (viz definice tohoto prostředku v [části jak vytvořit zobrazení](#how_to_create_a_view)). To je způsobeno tím, že když je <xref:System.Windows.Controls.ContentControl> objekt singleton (v tomto případě) svázán se zobrazením kolekce, je automaticky <xref:System.Windows.Data.CollectionView.CurrentItem%2A> svázán se zobrazením. Všimněte si <xref:System.Windows.Data.CollectionViewSource> , že objekty automaticky synchronizují měnu a výběr. Pokud ovládací prvek seznam není svázán <xref:System.Windows.Data.CollectionViewSource> s objektem jako v tomto příkladu, pak byste museli nastavit jeho <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost na `true` hodnotu, aby fungovala.  
  
 Další příklady naleznete v tématu [vazba na kolekci a zobrazení informací na základě výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) a [použití vzoru hlavní-podrobnosti s hierarchickými daty](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Možná jste si všimli, že výše uvedený příklad používá šablonu. Ve skutečnosti by se data nezobrazovala způsobem, který chceme, bez použití šablon (to <xref:System.Windows.Controls.ContentControl> je explicitně použito a implicitně používaného rozhraním <xref:System.Windows.Controls.ListBox>). Nyní se v další části změní data šablonování.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Šablonování dat  
 Bez použití datových šablon by naše aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v části [co je datová vazba?](#what_is_data_binding) vypadala takto:  
  
 ![Ukázka datových vazeb bez datových šablon](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 Jak je znázorněno v příkladu v předchozí části, <xref:System.Windows.Controls.ListBox> ovládací prvek <xref:System.Windows.Controls.ContentControl> i je svázán s celým objektem kolekce (nebo se konkrétně jedná o zobrazení nad objektem kolekce) pro *AuctionItem*s. Bez konkrétních pokynů k zobrazení shromažďování <xref:System.Windows.Controls.ListBox> dat se zobrazuje řetězcová reprezentace každého objektu v podkladové kolekci <xref:System.Windows.Controls.ContentControl> a zobrazuje řetězcovou reprezentaci objektu, ke kterému je vázáno.  
  
 Chcete-li tento problém vyřešit, aplikace <xref:System.Windows.DataTemplate>definuje s. Jak je znázorněno v příkladu v předchozí části, <xref:System.Windows.Controls.ContentControl> explicitně používá *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. Ovládací prvek implicitně používá následující <xref:System.Windows.DataTemplate> při zobrazení objektů AuctionItem v kolekci: <xref:System.Windows.Controls.ListBox>  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 S použitím těchto dvou <xref:System.Windows.DataTemplate>prvků je výsledné uživatelské rozhraní, které se zobrazuje v části [co je datová vazba?](#what_is_data_binding) . Jak vidíte z tohoto snímku obrazovky, kromě toho, abyste mohli umístit data do ovládacích prvků, <xref:System.Windows.DataTemplate>vám umožní definovat přesvědčivé vizuály pro vaše data. <xref:System.Windows.DataTrigger>Například s se používají ve výše uvedeném <xref:System.Windows.DataTemplate> případě, že *AuctionItem*s s hodnotou *SpecialFeatures* *zvýraznění* by se zobrazila s oranžovým ohraničením a hvězdičkou.  
  
 Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Ověření dat  
  
 Většina aplikací, které přijímají uživatelský vstup, musí mít logiku ověřování, aby bylo zajištěno, že uživatel zadal očekávané informace. Kontroly ověřování mohou být založeny na typu, rozsahu, formátu nebo jiných požadavcích specifických pro aplikace. Tato část popisuje, jak ověřování dat funguje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Přidružení ověřovacích pravidel k vazbě  
 Model vázání <xref:System.Windows.Data.Binding.ValidationRules%2A> dat umožňuje přidružení <xref:System.Windows.Data.Binding> k objektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Například <xref:System.Windows.Controls.TextBox> následující příklad váže spojení s vlastností s názvem `StartPrice` a <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> přidá <xref:System.Windows.Controls.ExceptionValidationRule> objekt do vlastnosti.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 <xref:System.Windows.Controls.ValidationRule> Objekt ověří, zda je hodnota vlastnosti platná. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má následující dva typy předdefinovaných <xref:System.Windows.Controls.ValidationRule> objektů:  
  
- <xref:System.Windows.Controls.ExceptionValidationRule> Kontroluje výjimky vyvolané během aktualizace vlastnosti zdroje vazby. V předchozím příkladu `StartPrice` je typu Integer. Když uživatel zadá hodnotu, kterou nelze převést na celé číslo, je vyvolána výjimka, což způsobí, že vazba bude označena jako neplatná. Alternativní <xref:System.Windows.Controls.ExceptionValidationRule> syntaxí explicitního nastavení je <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> nastavení vlastnosti `true` <xref:System.Windows.Data.Binding> na objekt nebo <xref:System.Windows.Data.MultiBinding> .  
  
- Objekt kontroluje chyby, které jsou vyvolány objekty, které <xref:System.ComponentModel.IDataErrorInfo> implementují rozhraní. <xref:System.Windows.Controls.DataErrorValidationRule> Příklad použití tohoto ověřovacího pravidla naleznete v tématu <xref:System.Windows.Controls.DataErrorValidationRule>. Alternativní <xref:System.Windows.Controls.DataErrorValidationRule> syntaxí explicitního nastavení je <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nastavení vlastnosti `true` <xref:System.Windows.Data.Binding> na objekt nebo <xref:System.Windows.Data.MultiBinding> .  
  
 Můžete také vytvořit vlastní ověřovací pravidlo odvozením z <xref:System.Windows.Controls.ValidationRule> třídy a <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementací metody. Následující příklad ukazuje pravidlo používané v *seznamu přidat produkt* "počáteční datum" <xref:System.Windows.Controls.TextBox> z části [co je datová vazba?](#what_is_data_binding) .  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 StartDateEntryForm<xref:System.Windows.Controls.TextBox> používá tento *FutureDateRule*, jak je znázorněno v následujícím příkladu:  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Všimněte si, že <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vzhledem k <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>tomu, že se jedná o hodnotu, modul vazby aktualizuje zdrojovou hodnotu při každém stisknutí klávesy, což <xref:System.Windows.Data.Binding.ValidationRules%2A> znamená, že také kontroluje všechna pravidla v kolekci při každém stisknutí klávesy. Tato diskuze probereme dále v části proces ověřování.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Poskytování vizuálních názorů  
 Pokud uživatel zadá neplatnou hodnotu, možná budete chtít zadat zpětnou vazbu k chybě v aplikaci [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Jedním ze způsobů, jak tuto zpětnou vazbu poskytnout <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> , je nastavení připojené vlastnosti <xref:System.Windows.Controls.ControlTemplate>na vlastní. Jak je znázorněno v předchozí části, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> používá *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> s názvem *validationTemplate*. Následující příklad ukazuje definici *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Element určuje, kde by měl být umístěn ovládací prvek, který je upravován.  
  
 Kromě toho můžete také použít <xref:System.Windows.Controls.ToolTip> k zobrazení chybové zprávy. *StartDateEntryForm* i *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>ES používají *styl textStyleTextBox*, který vytvoří azobrazíchybovouzprávu.<xref:System.Windows.Controls.ToolTip> Následující příklad ukazuje definici *textStyleTextBox*. Připojená vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je `true` v případě, že jedna nebo více vazeb vlastností vázaného prvku je v chybě.  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Pokud dojde <xref:System.Windows.Controls.TextBox> k chybě ověřování ,budemítStartDateEntryFormvpřípadě,žesezobrazí<xref:System.Windows.Controls.ToolTip>Chyba: <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>  
  
 ![Chyba ověření datové vazby](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Pokud máte přidružená ověřovací pravidla, ale <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> u vázaného ovládacího prvku neurčíte, použije se výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> nastavení pro upozorňování uživatelů, když dojde k chybě ověření. <xref:System.Windows.Data.Binding> Výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> je šablona ovládacího prvku, která definuje červené ohraničení ve vrstvě doplňků. Ve výchozím nastavení <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.ToolTip>a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] má StartPriceEntryForm přiověřovánívypadattakto<xref:System.Windows.Controls.TextBox> :  
  
 ![Chyba ověření datové vazby](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Příklad toho, jak poskytnout logiku pro ověření všech ovládacích prvků v dialogovém okně, naleznete v části vlastní dialogová okna v tématu [Přehled](../app-development/dialog-boxes-overview.md)dialogových oken.  
  
### <a name="validation-process"></a>Proces ověření  
 K ověření obvykle dochází při přenosu hodnoty cíle do vlastnosti zdroje vazby. K tomu dojde <xref:System.Windows.Data.BindingMode.TwoWay> u <xref:System.Windows.Data.BindingMode.OneWayToSource> vazeb a. K opakování iterace dojde k tomu, že aktualizace zdroje závisí na hodnotě <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnosti, jak je popsáno v oddílu [co Triggers source aktualizace](#what_triggers_source_updates) .  
  
 Následující popis popisuje proces *ověřování* . Všimněte si, že pokud během tohoto procesu dojde k chybě ověřování nebo k jinému typu chyby, proces se zastaví.  
  
1. Modul vazby kontroluje, zda jsou <xref:System.Windows.Controls.ValidationRule> definovány vlastní objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.RawProposedValue> hodnotu pro <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> to, v takovém případě volá metodu na každý <xref:System.Windows.Controls.ValidationRule> , dokud jedna z nich nespustí chybu. nebo až do všech těchto průchodů.  
  
2. Modul vazby pak volá konvertor, pokud existuje.  
  
3. Pokud je převaděč úspěšný, modul vazby zkontroluje, zda jsou <xref:System.Windows.Controls.ValidationRule> definovány vlastní objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> hodnotu pro <xref:System.Windows.Controls.ValidationRule.Validate%2A> to <xref:System.Windows.Data.Binding>, v takovém případě volá metodu na každé <xref:System.Windows.Controls.ValidationRule> , která má Nastavte na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> hodnotu, dokud jedna z nich nespustí chybu nebo dokud všechna neprojde. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
4. Modul vazby nastaví vlastnost source.  
  
5. Modul vazby kontroluje, zda jsou <xref:System.Windows.Controls.ValidationRule> definovány vlastní objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> hodnotu pro <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> to, v takovém případě volá metodu pro každý <xref:System.Windows.Controls.ValidationRule> , který <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> má nastaven na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> dokud jedna z nich nespustí chybu nebo dokud všechny nepřejdou. Pokud je přidružen k vazbě <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a je nastaven na výchozí hodnotu, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule> je v tomto okamžiku zaškrtnuto. <xref:System.Windows.Controls.DataErrorValidationRule> To je také bod, kdy jsou zaškrtnuta vazba <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> , které `true` mají nastavenu na hodnotu.  
  
6. Modul vazby kontroluje, zda jsou <xref:System.Windows.Controls.ValidationRule> definovány vlastní objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.CommittedValue> hodnotu pro <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> to, v takovém případě volá metodu pro každý <xref:System.Windows.Controls.ValidationRule> , který <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> má nastaven na <xref:System.Windows.Controls.ValidationStep.CommittedValue> dokud jedna z nich nespustí chybu nebo dokud všechny nepřejdou.  
  
 Pokud v <xref:System.Windows.Controls.ValidationRule> průběhu tohoto procesu nedojde k žádnému předání, modul vazby <xref:System.Windows.Controls.ValidationError> vytvoří objekt <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> a přidá jej do kolekce vázaného elementu. Předtím, než modul vazby modul <xref:System.Windows.Controls.ValidationRule> spustí objekty v kterémkoli daném kroku, odebere všechny <xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> , které byly přidány do vlastnosti připojené prvku vázaného elementu v průběhu tohoto kroku. Například pokud <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je v případě <xref:System.Windows.Controls.ValidationRule> , že je nastavena <xref:System.Windows.Controls.ValidationStep.UpdatedValue> neúspěšná, při příštím procesu ověřování, vytvoří modul vazby ten <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> , který <xref:System.Windows.Controls.ValidationError> bezprostředně před tím, než zavolá všechny <xref:System.Windows.Controls.ValidationRule> , které nastavily na <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Pokud <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> není prázdné <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> , připojená vlastnost prvku je nastavena na `true`. Pokud <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> <xref:System.Windows.Data.Binding> je vlastnost ovládacího prvku nastavena na `true`, pak modul vazby vyvolá <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> připojenou událost na elementu.  
  
 Všimněte si také, že platný přenos hodnoty v obou směrech (cíl do zdroje nebo zdroj do cíle) vymaže <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> připojenou vlastnost.  
  
 <xref:System.Windows.Controls.ExceptionValidationRule> Pokud vazba buď obsahuje přidruženou, nebo <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> má vlastnost nastavenou na `true` a výjimka je vyvolána, když modul vazby nastaví zdroj, <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>modul vazby zkontroluje, zda existuje. Máte možnost použít <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> zpětné volání k poskytnutí vlastní obslužné rutiny pro zpracování výjimek. Pokud není zadán <xref:System.Windows.Data.Binding>, vytvoří <xref:System.Windows.Controls.ValidationError> modul vazby modul <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> s výjimkou a přidá jej do kolekce vázaného elementu. <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>  
  
## <a name="debugging-mechanism"></a>Mechanismus ladění  
 Můžete nastavit připojenou vlastnost <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> objektu souvisejícího s vazbou pro příjem informací o stavu konkrétní vazby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Novinky ve verzi 4.5 grafického subsystému WPF](../getting-started/whats-new.md)
- [Vytvoření vazby k výsledkům dotazu LINQ](how-to-bind-to-the-results-of-a-linq-query.md)
- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
- [Ukázka datových vazeb](https://go.microsoft.com/fwlink/?LinkID=163703)
- [Témata s postupy](data-binding-how-to-topics.md)
- [Vytvoření vazby ke zdroji dat ADO.NET](how-to-bind-to-an-ado-net-data-source.md)
