---
title: "Přehled datových vazeb"
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
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
caps.latest.revision: "78"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbf731504022cb25e0cdeff5e0a557b67b987fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="data-binding-overview"></a>Přehled datových vazeb
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Datová vazba poskytuje jednoduchý a konzistentní způsob pro aplikace pro práci s daty a k dispozici. Elementy lze vázat na data z různých zdrojů dat ve formě [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty a [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s jako <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.ItemsControl>s jako <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ListView> mít integrovanou funkci, aby flexibilní stylů jeden datových položek, nebo kolekce datových položek. Třídění, filtrování a zobrazení skupiny lze vygenerovat nad data.  
  
 Funkce vazby dat v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má několik výhod oproti tradičním modely, včetně širokou škálu vlastnosti, které ze své podstaty podporují datovou vazbu, flexibilní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] reprezentace dat a vyčištění oddělení firmy logiku z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Toto téma popisuje nejprve koncepty, které jsou nezbytné, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby a pak přejde do využití <xref:System.Windows.Data.Binding> třídy a další funkce datové vazby.  
  
  
<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Co je datové vazby?  
 Datová vazba je proces, který naváže připojení mezi aplikací [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a obchodní logiku. Pokud vazby má správná nastavení a data poskytuje správné oznámení, pak při změně dat jeho hodnota elementy, které jsou vázané na data projeví změny automaticky. Datová vazba může také znamenat, že pokud se změní vnější reprezentace dat v elementu, pak v základních datech lze automaticky aktualizovat, aby odrážely změny. Například, pokud uživatel upravuje hodnotu v <xref:System.Windows.Controls.TextBox> elementu, základní hodnota dat se automaticky aktualizuje, aby odrážely tuto změnu.  
  
 Typické použití datová vazba je umístit server nebo místní konfigurační data do formulářů nebo jiné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tento koncept je rozšířit, aby obsahovaly vazba širokou škálu vlastnosti do různých datových zdrojů. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vlastnosti závislosti elementů mohou být vázány na [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty (včetně [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] objekty nebo objekty přidružené k webové služby a webových vlastnosti) a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.  
  
 Příklad vazby dat, podívejte se na následující aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [ukázku vazby dat](http://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Datové vazby – snímek obrazovky](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Výše je [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikace, která zobrazí seznam aukce položky. Aplikace ukazuje následující funkce vazby dat:  
  
-   Obsah <xref:System.Windows.Controls.ListBox> je vázána na kolekci *AuctionItem* objekty. *AuctionItem* objekt, jako má vlastnosti *popis*, *StartPrice*, *počátečním*, *kategorie*, *SpecialFeatures*atd.  
  
-   Data (*AuctionItem* objekty) v zobrazí <xref:System.Windows.Controls.ListBox> je šablonované tak, aby popis a aktuální ceny pro každou položku. To se provádí pomocí <xref:System.Windows.DataTemplate>. Kromě toho vzhled každé položky závisí na *SpecialFeatures* hodnotu *AuctionItem* zobrazení. Pokud *SpecialFeatures* hodnotu *AuctionItem* je *barva*, položka má modré ohraničení. Pokud je hodnota *zvýrazněte*, položka má oranžové ohraničení a hvězdu. [Data ukázka](#data_templating) část obsahuje informace o ukázka data.  
  
-   Uživatele můžete seskupit, třídit nebo filtrovat data pomocí <xref:System.Windows.Controls.CheckBox>es zadat. V na obrázku výše, "Seskupit podle kategorie" a "Seřadit podle kategorie a datum" <xref:System.Windows.Controls.CheckBox>es jsou vybrány. Jste si všimli, že data jsou seskupena podle kategorie produktu a název kategorie je v abecedním pořadí. Je obtížné Všimněte si z bitové kopie, ale položky jsou také seřazené podle počáteční datum v rámci každé kategorie. To se provádí pomocí *zobrazení kolekce*. [Vazbu na kolekce](#binding_to_collections) část se věnuje zobrazení kolekcí.  
  
-   Když uživatel vybere položku, <xref:System.Windows.Controls.ContentControl> zobrazí podrobnosti o vybrané položky. To se označuje jako *hlavní-podrobné scénář*. [Hlavní-podrobné scénář](#master_detail_scenario) část obsahuje informace o tomto typu vazby scénáře.  
  
-   Typ *počátečním* vlastnost je <xref:System.DateTime>, která vrací data, která zahrnuje dobu milisekundách. V této aplikaci se používá vlastní převaděč tak, aby se zobrazí kratší řetězec datum. [Převod dat](#data_conversion) část obsahuje informace o převaděče.  
  
 Když uživatel klikne *přidat produktu* tlačítko zobrazí následující tvar:  
  
 ![Přidat stránku produktu výpis](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Uživatele můžete upravte pole ve formuláři, zobrazte náhled výpis produktu pomocí krátké preview a podrobnější podokna náhledu a pak klikněte na tlačítko *odeslání* přidat nový výpis produktu. Všechny existující seskupení, filtrování a řazení funkce budou platit pro nový záznam. V tomto případě konkrétní položky zadali je výše uvedený obrázek se zobrazí jako druhý položky v rámci *počítače* kategorie.  
  
 Na tomto obrázku to není znázorněné je logiku ověřování, které jsou součástí *počáteční datum* <xref:System.Windows.Controls.TextBox>. Pokud uživatel zadá neplatnou datum (neplatný formátování nebo na datum v minulosti), bude se uživateli upozornění, s <xref:System.Windows.Controls.ToolTip> a červený vykřičník vedle <xref:System.Windows.Controls.TextBox>. [Ověření dat](#data_validation) část popisuje postup vytvoření logiku ověření.  
  
 Před přechodem do různých funkcí vazby dat uvedených výše, nejprve probereme v další části základní koncepty, které jsou důležité k porozumění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby.  
  
## <a name="basic-data-binding-concepts"></a>Základní datové vazby koncepty  
  
 Bez ohledu na to, jaký element jsou vazby a povaha zdroje dat, každý vazby vždy odpovídá modelu vidíte na následujícím obrázku:  
  
 ![Diagram základní datové vazby](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 Jak vidíte na obrázku výše, datové vazby je v podstatě most cílových vazby a zdroje vazby. Obrázek ukazuje následující základní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncepty vazby dat:  
  
-   Obvykle každou vazbu má tyto čtyři komponenty: cílový objekt vazby, vlastnost target, zdroj vazby a cestu k hodnotě ve zdroji vazby použít. Například, pokud chcete vytvořit vazbu obsah <xref:System.Windows.Controls.TextBox> k *název* vlastnost *zaměstnanec* objektu, cílový objekt je <xref:System.Windows.Controls.TextBox>, vlastnost target je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, je hodnota, která má použít *název*, a je zdrojový objekt *zaměstnanec* objektu.  
  
-   Vlastnost target musí být vlastnost závislosti. Většina <xref:System.Windows.UIElement> vlastnosti jsou vlastnosti závislosti a většina vlastnosti závislosti, s výjimkou těch jen pro čtení podporují datové vazby ve výchozím nastavení. (Jenom <xref:System.Windows.DependencyObject> typy můžete definovat vlastností závislostí a všechny <xref:System.Windows.UIElement>s odvozena od <xref:System.Windows.DependencyObject>.)  
  
-   I když není zadaný na obrázku, je třeba poznamenat, že vazba zdrojový objekt není omezena na probíhá vlastní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Datová vazba podporuje data ve formě [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Pokud chcete zadat některé příklady, může být zdrojem vazby <xref:System.Windows.UIElement>, libovolného objektu seznamu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt, který je přidružen [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] data nebo webové služby nebo XmlNode, který obsahuje vaše [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data. Další informace najdete v tématu [vazby Přehled zdrojů](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Během čtení prostřednictvím dalších [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] témata, je důležité mít na paměti, když vytvoříte vazbu, jsou vazby cíl vazby *k* zdroji vazby. Například, pokud jsou zobrazení některé základní [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data v <xref:System.Windows.Controls.ListBox> použití datových vazeb, jsou vazby vaše <xref:System.Windows.Controls.ListBox> k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.  
  
 Chcete-li vytvořit vazbu, použijte <xref:System.Windows.Data.Binding> objektu. Zbývající část tohoto tématu popisuje řadu koncepce aplikace a některých vlastností a jejich používání <xref:System.Windows.Data.Binding> objektu.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Směr toku dat  
 Jak je uvedeno nahoře a označeno šipkou na výše uvedeném obrázku, tok dat vazby můžete přejít z cíle vazby ke zdroji vazby (například zdrojové hodnoty změní, když uživatel upravuje hodnotu <xref:System.Windows.Controls.TextBox>) nebo ze zdroje vazby Cíl vazby (například vaše <xref:System.Windows.Controls.TextBox> získá obsah aktualizován se změnami ve zdroji vazba) Pokud zdroji vazby poskytuje správné oznámení.  
  
 Můžete vaše aplikace umožňuje uživatelům změnit data a rozšířit zpět ke zdrojovému objektu. Nebo možná chcete povolit uživatelům aktualizovat zdrojová data. To můžete ovládat nastavením <xref:System.Windows.Data.Binding.Mode%2A> vlastnost vaší <xref:System.Windows.Data.Binding> objektu. Následující obrázek ukazuje různé typy toku dat:  
  
 ![Datové vazby tok dat](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode.OneWay>Vazba způsobí, že změny vlastnosti zdroj k automatické aktualizaci vlastnost target, ale pro vlastnost target nepřenese zpět na vlastnost zdroje. Tento typ vazby je vhodné v případě vázaného ovládacího prvku implicitně jen pro čtení. Například může svázat se zdrojem například běžícími nebo možná cílovou vlastnost nemá žádné rozhraní ovládacího prvku zadaná pro provádění změn, jako je například barvu pozadí vázané na data tabulky. Pokud není nutné ke sledování změn vlastnost target, pomocí <xref:System.Windows.Data.BindingMode.OneWay> vazby režimu zabraňuje nároky na <xref:System.Windows.Data.BindingMode.TwoWay> vazby režimu.  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay>Vazba způsobí, že změny vlastnosti zdroj nebo vlastnost target automaticky aktualizovat na druhý. Tento typ vazby je vhodný pro upravovatelné formuláře nebo jiné plně interaktivní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře. Většinu vlastností výchozí <xref:System.Windows.Data.BindingMode.OneWay> vazby, ale některé vlastnosti závislosti (obvykle vlastností ovládacích prvků uživatele nelze upravit, jako <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> vlastnost <xref:System.Windows.Controls.CheckBox>) výchozí nastavení <xref:System.Windows.Data.BindingMode.TwoWay> vazby. Programový způsob, jak určit, zda vlastnost závislosti váže jednosměrné nebo obousměrné ve výchozím nastavení je získat metadata vlastnosti vlastnost použití <xref:System.Windows.DependencyProperty.GetMetadata%2A> a zkontrolujte logickou hodnotu <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> vlastnost.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource>je opakem <xref:System.Windows.Data.BindingMode.OneWay> vazby; aktualizuje vlastnosti zdroj při změně vlastnost target. Jeden příklad scénáře je, pokud potřebujete jenom znovu vyhodnotit zdrojové hodnoty z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Nejsou zobrazené na obrázku je <xref:System.Windows.Data.BindingMode.OneTime> vazby, což způsobí, že zdrojová vlastnost k chybě při inicializaci vlastnost target, ale nejsou rozšířena následné změny. To znamená, že pokud kontextu dat zde nevyskytlo změnu nebo objekt v kontextu změny dat, pak tato změna se nereflektují v vlastnost target. Tento typ vazby je vhodné, pokud používáte data, kde buď snímek aktuální stav je vhodné použít nebo data je skutečně statické. Tento typ vazby je také užitečné, pokud chcete inicializovat vaší vlastnost target s některé hodnoty z vlastnosti zdroje a kontextu dat není známa předem. To je v podstatě jednodušší forma <xref:System.Windows.Data.BindingMode.OneWay> vazby, který poskytuje lepší výkon v případech, kde zdrojové hodnoty nezmění.  
  
 Všimněte si, že ke zjištění změny zdrojů (platí pro <xref:System.Windows.Data.BindingMode.OneWay> a <xref:System.Windows.Data.BindingMode.TwoWay> vazby), zdroj musí implementovat, jako vhodný mechanismus oznámení změn vhodný vlastnost <xref:System.ComponentModel.INotifyPropertyChanged>. V tématu [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) příklad <xref:System.ComponentModel.INotifyPropertyChanged> implementace.  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Stránka vlastností poskytuje další informace o vytvoření vazby režimy a příklad k určení směru vazby.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Co aktivační události zdroje aktualizace  
 Vazby, které jsou <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> naslouchat změny v vlastnost target a šířit je zpět do zdroje. To se označuje jako zdroj aktualizace. Například můžete upravovat text do textového pole. Chcete-li změnit základní zdrojové hodnoty. Jak je popsáno v poslední části, směr toku dat je dáno hodnotu <xref:System.Windows.Data.Binding.Mode%2A> vlastnost vazby.  
  
 Však zdrojové hodnoty aktualizovat při úpravách text nebo po ukončení úprav textu a přesunutí ukazatele myši směrem od textového pole? <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Vlastnost vazby Určuje, co se aktivuje aktualizace zdroje. Role ilustrují tečkami vpravo šipek na následujícím obrázku <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost:  
  
 ![UpdateSourceTrigger diagram](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 Pokud <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, pak hodnota ukazující na pravou šipku <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby získá aktualizovat co nejdříve změny vlastnost target. Ale pokud <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota je <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, pak tuto hodnotu pouze získá aktualizovat na novou hodnotu, když vlastnost target ztratí fokus.  
  
 Podobně jako <xref:System.Windows.Data.Binding.Mode%2A> vlastnost různých závislostí vlastnosti mají různé výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnoty. Výchozí hodnota pro většinu vlastností závislostí je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. To znamená, že zdroj aktualizace obvykle dojít vždy, když cíl změny vlastností, které je vhodná pro <xref:System.Windows.Controls.CheckBox>es a dalších jednoduchý ovládacích prvků. Však u textových polí aktualizace po každém stisknutí může snížit výkon a zakazuje uživateli obvykle možnost backspace a opravte chyby zadáním před potvrzením na novou hodnotu. Proto <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> místo <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Najdete v článku <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stránku vlastností informace o tom, jak najít výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu vlastnosti závislosti.  
  
 Následující tabulka uvádí příklad scénáře pro každou <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu pomocí <xref:System.Windows.Controls.TextBox> jako příklad:  
  
|Hodnota UpdateSourceTrigger|Při aktualizaci zdrojové hodnoty|Příklad scénáře TextBox|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (výchozí pro <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Když TextBox – ovládací prvek ztratí fokus|A <xref:System.Windows.Controls.TextBox> je spojeno s logiku ověření (viz oddíl ověření dat)|  
|PropertyChanged.|Při psaní do<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>ovládací prvky v okně chatovací místnosti|  
|Explicitní|Pokud aplikace zavolá<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>ovládací prvky ve formuláři upravovat (aktualizuje hodnoty zdroje jenom v případě, že uživatel klikne na tlačítko pro odeslání)|  
  
 Příklad, naleznete v části [řízení, když TextBox Text aktualizuje zdroj](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Vytváření vazby  
  
 K skladovaná některé koncepty, které jsou popsané v předchozí části, je vytvořit vazbu pomocí <xref:System.Windows.Data.Binding> objektu a každý vazby obvykle má čtyři součásti: vazby cíl, vlastnost target, vazba zdroje a cestu k hodnotě zdroje používat. Tato část popisuje, jak nastavit vazbu.  
  
 Podívejte se na následující příklad, ve kterém je zdrojový objekt vazby třídy s názvem *Mojedata* definovaný v *SDKSample* oboru názvů. Pro demonstrační účely *Mojedata* třída má vlastnost řetězec s názvem *ColorName*, ze které je hodnota nastavená na "Red". Proto tento příklad vytvoří tlačítko s červeným pozadím.  
  
 [!code-xaml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Další informace o syntaxe deklarace vazby a příklady, jak nastavit vazby v kódu najdete v části [vazby deklarace přehled](../../../../docs/framework/wpf/data/binding-declarations-overview.md).  
  
 Pokud jsme použít tento příklad do našich základní diagramu, výsledná obrázek vypadá jako následující. Toto je <xref:System.Windows.Data.BindingMode.OneWay> vazby, protože vlastnost pozadí podporuje <xref:System.Windows.Data.BindingMode.OneWay> vazby ve výchozím nastavení.  
  
 ![Diagram datové vazby](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 Může zajímat, proč to funguje i když *ColorName* je vlastnost typu řetězec při <xref:System.Windows.Controls.Control.Background%2A> vlastnost je typu <xref:System.Windows.Media.Brush>. Toto je výchozí převod typů v práci a je podrobněji [převod dat](#data_conversion) části.  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Zadání zdroje vazby  
 Všimněte si, že v předchozím příkladu je vazba zdroj určený nastavením <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.Button> Pak dědí <xref:System.Windows.FrameworkElement.DataContext%2A> z hodnoty <xref:System.Windows.Controls.DockPanel>, což je jeho nadřazený element. Chcete-li znovu opakují, zdrojového objektu vazby je jedním z čtyři nezbytné komponenty položky vazbu. Proto bez vazby zdrojový objekt specifikované vazba by nic nestane.  
  
 Zadejte zdrojový objekt vazba několika způsoby. Pomocí <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost na nadřazený element je užitečné, když vytváříte vazbu více vlastností ke stejnému zdroji. Ale v některých případech může být vhodnější zadat zdroj vazby na jednotlivé vazby deklarace. Pro předchozí příklad, místo použití <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost, můžete určit zdroj vazby nastavením <xref:System.Windows.Data.Binding.Source%2A> vlastnost přímo na deklaraci vazby tlačítko, jako v následujícím příkladu:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Jiné než nastavení <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost v elementu přímo, dědění <xref:System.Windows.FrameworkElement.DataContext%2A> hodnotu z nadřazeným (například tlačítko v prvním příkladu) a explicitně určit zdroj vazby nastavením <xref:System.Windows.Data.Binding.Source%2A> vlastnost <xref:System.Windows.Data.Binding> (například na tlačítko poslední příkladu), můžete také použít <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost nebo <xref:System.Windows.Data.Binding.RelativeSource%2A> vlastnost zadat zdroj vazby. <xref:System.Windows.Data.Binding.ElementName%2A> Vlastnost je užitečná, když se vytvoření vazby na další prvky v aplikaci, například při použití jezdce nastavte šířku tlačítko. <xref:System.Windows.Data.Binding.RelativeSource%2A> Vlastnost je užitečná, pokud vazba je zadaný v <xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.Style>. Další informace najdete v tématu [určit zdroj vazby](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Určení cesty k hodnotě  
 Pokud vaše zdrojová vazba je objekt, můžete použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost zadejte hodnotu pro vaše vazby. Pokud vytváříte vazbu na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, můžete použít <xref:System.Windows.Data.Binding.XPath%2A> vlastnost zadejte hodnotu. V některých případech může být pro použití <xref:System.Windows.Data.Binding.Path%2A> vlastnost i v případě, že vaše data jsou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Například pokud chcete pro přístup k vlastnosti název vrácený XmlNode (v důsledku dotaz XPath), používejte <xref:System.Windows.Data.Binding.Path%2A> vlastnost kromě <xref:System.Windows.Data.Binding.XPath%2A> vlastnost.  
  
 Informace ze syntaxe a příklady naleznete v tématu <xref:System.Windows.Data.Binding.Path%2A> a <xref:System.Windows.Data.Binding.XPath%2A> stránky vlastností.  
  
 Všimněte si, že i když budeme mít zdůrazňují, který <xref:System.Windows.Data.Binding.Path%2A> na hodnotu sloužící je jednou ze čtyř nezbytné komponenty položky vazbu ve scénářích, které chcete vytvořit vazbu na celý objekt, hodnotu, která se použije by být stejný jako zdrojový objekt vazby. V takových případech se vztahuje k není uveden <xref:System.Windows.Data.Binding.Path%2A>. Podívejte se na následující příklad:  
  
 [!code-xaml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Výše uvedený příklad používá syntaxi prázdný vazby: {vazba}. V takovém případě <xref:System.Windows.Controls.ListBox> DataContext dědí z nadřazeného prvku DockPanel (v tomto příkladu není znázorněné). Pokud není zadána cesta, ve výchozím nastavení se vytvořit vazbu na celý objekt. Jinými slovy, v tomto příkladu cesta byla ponechána vzhledem k tomu, že jsme vazby <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost celý objekt. (Viz [vazbu na kolekce](#binding_to_collections) části Podrobné informace.)  
  
 Než vazby ke kolekci, tento scénář je také užitečné, když chcete vytvořit vazbu na celý objekt místo právě jednu vlastnost objektu. Například pokud je zdrojový objekt typu řetězec a jednoduše chcete vytvořit vazbu na vlastní řetězec. Další z typických možností je, pokud chcete vytvořit vazbu elementu pro objekt s několik vlastností.  
  
 Všimněte si, že budete muset použít vlastní logiku, aby byla data smysl vázané cílovou vlastnost. Vlastní logika může být ve tvaru vlastní převaděč (Pokud je výchozí typ převodu neexistuje). V tématu [převod dat](#data_conversion) informace o převaděče.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Vazba a BindingExpression  
 Před získáním do dalších funkcích a použití vazby dat, je vhodné zavést <xref:System.Windows.Data.BindingExpression> třídy. Jak jste mohli vidět v předchozích částech <xref:System.Windows.Data.Binding> třída je základní třída pro deklaraci vazby; <xref:System.Windows.Data.Binding> třída poskytuje mnoho vlastností, které vám umožní určit vlastnosti vazbu. Související třídy, <xref:System.Windows.Data.BindingExpression>, je základní objekt, který udržuje propojení mezi zdrojem a cílem. Vazba obsahuje všechny informace, které je možné sdílet napříč několika výrazy vazby. A <xref:System.Windows.Data.BindingExpression> je výraz instance, které nemohou být sdíleny a obsahuje všechny instance informace <xref:System.Windows.Data.Binding>.  
  
 Zvažte například následující příkaz, kde *myDataObject* je instance *Mojedata* třídy, *myBinding* je zdrojem <xref:System.Windows.Data.Binding> objekt a *Mojedata* třída je definovaný třídu, která obsahuje řetězec vlastnost s názvem *MyDataProperty*. Tento příklad vytvoří vazbu obsah textu *mytext*, instanci <xref:System.Windows.Controls.TextBlock>do *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Můžete použít stejné *myBinding* objekt k vytvoření dalších vazby. Například můžete použít *myBinding* objekt, který chcete vytvořit vazbu textového obsahu zaškrtnutím políčka *MyDataProperty*. V tomto scénáři budou existovat dvě instance <xref:System.Windows.Data.BindingExpression> sdílení *myBinding* objektu.  
  
 A <xref:System.Windows.Data.BindingExpression> objekt můžete získat prostřednictvím návratovou hodnotu volání <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> na objekt vázané na data. Následující témata ukazují některé z použití <xref:System.Windows.Data.BindingExpression> třídy:  
  
-   [Získání objektu vazby z vázané cílovou vlastnost](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [Ovládací prvek, když TextBox Text aktualizuje zdroj](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Převod dat  
 V předchozím příkladu je červené tlačítko protože jeho <xref:System.Windows.Controls.Control.Background%2A> vlastnost je vázána na vlastnost řetězec s hodnotou "Red". Toto funguje, protože se nachází na převaděče typů <xref:System.Windows.Media.Brush> převést hodnotu řetězce na typ <xref:System.Windows.Media.Brush>.  
  
 Přidat tato informace o obrázku v [vytváření vazby](#creating_a_binding) části diagramu vypadat takhle:  
  
 ![Diagram datové vazby](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 Co když, ale místo nutnosti vlastnosti typu řetězec má váš zdrojový objekt vazby *barva* vlastnost typu <xref:System.Windows.Media.Color>? V takovém případě v pořadí vazba fungovala museli byste první zapnout *barva* hodnotu vlastnosti na něco jiného, který <xref:System.Windows.Controls.Control.Background%2A> tato vlastnost přijímá parametry. Budete muset vytvořit vlastní převaděč implementací <xref:System.Windows.Data.IValueConverter> rozhraní, jako v následujícím příkladu:  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> Stránka s referencemi poskytuje další informace.  
  
 Nyní je používán vlastní převaděč místo výchozí převod a naše diagram vypadá takto:  
  
 ![Diagram datové vazby](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 Znovu opakují, výchozí převody mohou být k dispozici z důvodu převaděče typů, které se nacházejí v typu je vázána na. Toto chování bude záviset na které převaděče typů jsou k dispozici na cíli. Pokud máte pochybnosti, vytvořte vlastní převaděč.  
  
 Následují některé typické scénáře, kde má smysl implementaci převaděče dat:  
  
-   Data budou zobrazeny odlišně, v závislosti na jazykové verzi. Například můžete chtít implementovat Převaděč měny nebo převaděč kalendáře datum a čas na základě hodnoty nebo standardů používaných v konkrétní jazykové verzi.  
  
-   Data používá není určen nutně změnit textové hodnoty vlastnosti, ale místo toho má jinou hodnotu, jako je například zdroj pro bitovou kopii, barvu nebo styl textu zobrazení změnit. Převaděče lze použít u této instance převedením vazby vlastnosti, která nemusí se zdá, že se potřeby, třeba vazby textové pole pro vlastnost pozadí buňky tabulky.  
  
-   Více než jeden ovládací prvek nebo na více vlastností ovládacích prvků jsou svázané s ke stejným datům. V takovém případě primární vazby může jenom zobrazit text, zatímco jiné vazby zpracování konkrétní zobrazení problémy, ale stále používat stejnou vazbu jako informace o zdroji.  
  
-   Pokud jsme nebyly dosud popsané <xref:System.Windows.Data.MultiBinding>, kde má vlastnost target kolekci vazby. U <xref:System.Windows.Data.MultiBinding>, používat vlastní <xref:System.Windows.Data.IMultiValueConverter> k vytvoření konečná hodnota z hodnoty vazby. Barva může například počítaný z červené, modré a zelená hodnoty, které může být hodnoty ze zdrojové objekty stejný nebo jiný vazby. Najdete v článku <xref:System.Windows.Data.MultiBinding> třída stránky informace a příklady.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Vytvoření vazby na kolekce  
  
 Ke zdrojovému objektu vazby lze zacházet jako jeden objekt, jehož vlastnosti obsahovat data, nebo jako shromažďování dat polymorfní objektů, které jsou často seskupeny dohromady (například výsledek dotazu do databáze). Pokud jsme pouze probrali vazby na jednotlivé objekty, ale vazby ke shromažďování dat je běžný scénář. Například typických možností je použít <xref:System.Windows.Controls.ItemsControl> například <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, nebo <xref:System.Windows.Controls.TreeView> zobrazíte shromažďování dat, například v aplikaci ukazuje [co je datová vazba?](#what_is_data_binding) části.  
  
 Naštěstí naše základní diagram stále platí. Pokud vytváříte vazbu <xref:System.Windows.Controls.ItemsControl> do kolekce, diagram vypadá takto:  
  
 ![Datová vazba ItemsControl diagram](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 Jak je znázorněno v tomto diagramu pro vazbu <xref:System.Windows.Controls.ItemsControl> na objekt kolekce <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> je vlastnost použít. Si můžete představit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost jako obsah <xref:System.Windows.Controls.ItemsControl>. Všimněte si, že je vazba <xref:System.Windows.Data.BindingMode.OneWay> protože <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> podporuje vlastnost <xref:System.Windows.Data.BindingMode.OneWay> vazby ve výchozím nastavení.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Postupy pro implementaci kolekce  
 Můžete vytvořit výčet přes jakoukoli kolekci, která implementuje <xref:System.Collections.IEnumerable> rozhraní. Ale nastavit dynamické vazby tak, aby vložení nebo odstranění v kolekci aktualizovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticky, kolekce musí implementovat <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Toto rozhraní zpřístupní událost, která by měla být zvýšena při každé změně zdrojové kolekce.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje <xref:System.Collections.ObjectModel.ObservableCollection%601> třída, která je na předdefinované implementace shromažďování dat, která zveřejňuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Všimněte si, že aby plně podporoval přenášení hodnot dat ze zdrojové objekty k cílům, také musí implementovat každý objekt v kolekci, která podporuje vlastnosti vazbu <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [vazby Přehled zdrojů](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Před implementací vlastní kolekce, zvažte použití <xref:System.Collections.ObjectModel.ObservableCollection%601> nebo jeden z existující kolekci třídy, jako například <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, a <xref:System.ComponentModel.BindingList%601>, mezi mnohé další. Pokud máte složitější scénář a chcete implementovat vlastní kolekci, zvažte použití <xref:System.Collections.IList>, který poskytuje negenerická kolekce objektů, které můžete individuálně získávat přístup index a proto nejlepší výkon.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Zobrazení kolekce  
 Jednou vaše <xref:System.Windows.Controls.ItemsControl> je vázán k shromažďování dat, můžete chtít řazení, filtr nebo skupinu data. To lze provést, použijte zobrazení kolekcí, které jsou třídy, které implementují <xref:System.ComponentModel.ICollectionView> rozhraní.  
  
  
#### <a name="what-are-collection-views"></a>Jaké jsou zobrazení kolekcí?  
 Zobrazení kolekce je vrstva nad kolekce zdroj vazby, která vám umožní přejděte a zobrazit zdrojové kolekci na základě řazení, filtru a skupiny dotazů, bez nutnosti změny základní zdrojové kolekci sám sebe. Zobrazení kolekce také udržuje ukazatel na aktuální položky v kolekci. Pokud implementuje zdrojové kolekci <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní, změny aktivováno <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> událostí rozšířeny zobrazení.  
  
 Protože zobrazení se nemění základní kolekce zdroj, může mít každý zdrojové kolekci přidruženo více zobrazení. Například můžete mít kolekce *úloh* objekty. Používání zobrazení, se můžete zobrazit tato data různými způsoby. Na levé straně stránky můžete například zobrazit úlohy, které jsou seřazené podle priority a na pravé straně, seskupené podle oblasti.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Postup vytvoření zobrazení  
 Jeden způsob, jak vytvořit a použít zobrazení je přímo doložit objekt zobrazení a potom ho použít jako zdroj vazby. Představte si třeba [ukázku vazby dat](http://go.microsoft.com/fwlink/?LinkID=163703) aplikace uvedené v [co je datová vazba?](#what_is_data_binding) části. Aplikace je implementováno tak, aby <xref:System.Windows.Controls.ListBox> váže k zobrazení nad shromažďováním dat místo shromažďování dat přímo. V následujícím příkladu se extrahují z [ukázku vazby dat](http://go.microsoft.com/fwlink/?LinkID=163703) aplikace. <xref:System.Windows.Data.CollectionViewSource> Třída je [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] proxy serveru, který dědí z třídy <xref:System.Windows.Data.CollectionView>. V tomto konkrétním příkladu <xref:System.Windows.Data.CollectionViewSource.Source%2A> zobrazení je vázána *AuctionItems* kolekce (typu <xref:System.Collections.ObjectModel.ObservableCollection%601>) aktuálního objektu aplikace.  
  
 [!code-xaml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 Prostředek *listingDataView* pak slouží jako zdroj vazby pro prvky v aplikaci, například <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Vytvořit další zobrazení pro stejné kolekci, můžete vytvořit jiný <xref:System.Windows.Data.CollectionViewSource> instance a pojmenujte ho jiné `x:Key` název.  
  
 V následující tabulce jsou uvedeny typy zobrazení dat, které jsou vytvořeny jako výchozí zobrazení kolekce nebo pomocí <xref:System.Windows.Data.CollectionViewSource> podle typu kolekce zdroje.  
  
|Typ kolekce zdroje|Typ zobrazení kolekce|Poznámky|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Na základě vnitřní typ<xref:System.Windows.Data.CollectionView>|Nelze seskupit položky.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Nejrychlejší.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Pomocí výchozí zobrazení  
 Určení zobrazení kolekce jako zdroj vazba je jedním ze způsobů, jak vytvořit a používat zobrazení kolekce. WPF vytvoří také výchozí zobrazení kolekce pro každou kolekci použít jako zdroj vazby. Pokud můžete vytvořit vazbu přímo do kolekce, vytvoří vazbu WPF jeho výchozí zobrazení. Všimněte si, že toto výchozí zobrazení, je sdílen všechny vazby ke stejné kolekci, tak, aby ke změně výchozí zobrazení pomocí jednoho připojeného ovládacího prvku nebo kód (například řazení nebo ke změně aktuálního ukazatele položky popsané později) se projeví ve všech vazby ke stejné kolekci.  
  
 Výchozí zobrazení získáte pomocí <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metoda. Příklad, naleznete v části [získat výchozí zobrazení shromažďování dat](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Zobrazení kolekcí s ADO.NET DataTables  
 Chcete-li zvýšit výkon, kolekce zobrazení pro technologii ADO.NET <xref:System.Data.DataTable> nebo <xref:System.Data.DataView> objekty delegovat řazení a filtrování, abyste <xref:System.Data.DataView>. To způsobí, že řazení a filtrování na všechny kolekce zobrazení zdroje dat, sdílet. Povolit jednotlivých zobrazení kolekce k řazení a filtrování nezávisle, inicializovat jednotlivých zobrazení kolekce s vlastním <xref:System.Data.DataView> objektu.  
  
#### <a name="sorting"></a>Řazení  
 Jak je uvedeno nahoře, můžete zobrazení použít pořadí řazení do kolekce. Protože existuje v podkladové kolekci, vaše data může nebo nemusí mít relevantní, vyplývajících pořadí. Zobrazení nad shromažďováním umožňuje ukládat pořadí, nebo změňte výchozí pořadí, na základě kritérií porovnání, které zadáte. Protože je na základě klienta zobrazení dat, je běžný scénář, uživatel může chtít řadit sloupce tabulkové dat pro hodnotu, která odpovídá sloupci. Použití zobrazení, tento uživatel řízené řazení lze použít, znovu bez jakýchkoli změn ke kolekci základní nebo i museli znovu spustit dotaz pro obsah, kolekce. Příklad, naleznete v části [seřadit, rutina GridView sloupce při záhlaví po kliknutí na](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 Následující příklad ukazuje řazení logiku "Seřadit podle kategorie a datum" <xref:System.Windows.Controls.CheckBox> aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) části:  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrování  
 Zobrazení můžete také použít filtr do kolekce. To znamená, že i když položka může existovat v kolekci, toto konkrétní zobrazení je zaměřena na zobrazit jenom určité podmnožiny úplné kolekce. Můžete filtrovat na podmínce v datech. Pro instanci, jako je aplikace provádí [co je datová vazba?](#what_is_data_binding) části "Zobrazit pouze bargains" <xref:System.Windows.Controls.CheckBox> obsahuje logiku a filtrovat položky, které náklady 25 nebo více. Následující kód je provést, chcete-li nastavit *ShowOnlyBargainsFilter* jako <xref:System.Windows.Data.CollectionViewSource.Filter> obslužné rutiny události při který <xref:System.Windows.Controls.CheckBox> je vybrán:  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* má následující implementaci obslužné rutiny události:  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Pokud použijete jednu z <xref:System.Windows.Data.CollectionView> třídy přímo místo z <xref:System.Windows.Data.CollectionViewSource>, byste použili <xref:System.Windows.Data.CollectionView.Filter%2A> vlastnosti k určení zpětného volání. Příklad, naleznete v části [filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Seskupování  
 S výjimkou vnitřní třídu, která zobrazení <xref:System.Collections.IEnumerable> kolekce, všechna zobrazení kolekce podporu funkcí seskupení, které umožňuje uživatelům oddílu kolekce v zobrazení kolekce do logických skupin. Skupiny může být explicitní, kde uživatel zadává seznam skupin, nebo implicitní, kde skupiny jsou generována dynamicky v závislosti na data.  
  
 Následující příklad ukazuje logiku "Seskupit podle kategorie" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Další příklad seskupení, najdete v části [seskupení položek v ListView, implementuje GridView](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Aktuální položka ukazatele  
 Zobrazení také podporují představu o aktuální položky. Můžete procházet objekty v zobrazení kolekce. Lze při procházení, přesouváte k položky ukazatele, který vám umožní načíst objekt, který existuje v tomto konkrétní umístění v kolekci. Příklad, naleznete v části [přejděte prostřednictvím objekty v Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Protože WPF váže na kolekci, mají všechny vazby kolekce pouze pomocí zobrazení (zobrazení, které zadáte, nebo kolekci výchozí zobrazení), aktuální položky ukazatel. Při vytváření vazby k zobrazení, v znak lomítko ("/") `Path` hodnotu označí aktuální položky zobrazení. V následujícím příkladu je kontextu dat zobrazení kolekce. První řádek váže ke kolekci. Druhý řádek vytvoří vazbu aktuální položky v kolekci. Ve třetím řádku váže `Description` vlastnosti aktuální položky v kolekci.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Syntaxe lomítko a vlastnost může být také skládaný procházení hierarchie kolekce. Následující příklad vytvoří vazbu s aktuální položkou kolekci s názvem `Offices`, což je vlastnost s aktuální položkou zdrojové kolekci.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Aktuální položka ukazatele mohou být ovlivněny žádné řazení nebo filtrování, který se použije ke kolekci. Řazení zachová aktuální položky ukazatel na poslední položka vybrána, ale zobrazení kolekce je nyní změnili kolem něj. (Případně vybrané položky se na začátku seznamu před, ale teď může vybrané položky se někde uprostřed.) Filtrování zachovává vybranou položku, pokud výběr zůstane v zobrazení po filtrování. Ukazatel aktuální položky, jinak hodnota je nastaven na první položku zobrazení filtrované kolekce.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Hlavní tabulka a podrobnosti vazba scénář  
 Představu o aktuální položka je užitečné, nejen pro navigaci položek v kolekci, ale také pro scénář hlavní podrobné vazby. Vezměte v úvahu aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) části znovu. V této aplikaci, vybrat v rámci <xref:System.Windows.Controls.ListBox> určuje obsah ukazuje <xref:System.Windows.Controls.ContentControl>. Uvést jiným způsobem, když <xref:System.Windows.Controls.ListBox> je vybraná položka, <xref:System.Windows.Controls.ContentControl> zobrazuje podrobnosti o vybranou položku.  
  
 Hlavní tabulka a podrobnosti scénář můžete implementovat jednoduše tak, že dvě nebo více ovládací prvky vázané na stejném zobrazení. V následujícím příkladu z [ukázku vazby dat](http://go.microsoft.com/fwlink/?LinkID=163703) ukazuje z kódu <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> uvidíte na aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) části:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Všimněte si, že oba ovládací prvky jsou vázány na stejný zdroj, *listingDataView* statické prostředků (viz definice tento prostředek [postup vytvoření zobrazení části](#how_to_create_a_view)). Toto funguje, protože při vytvoření typu singleton objektu ( <xref:System.Windows.Controls.ContentControl> v tomto případě) je vázán k zobrazení a kolekce, se automaticky váže k <xref:System.Windows.Data.CollectionView.CurrentItem%2A> zobrazení. Všimněte si, že <xref:System.Windows.Data.CollectionViewSource> objekty budou automaticky synchronizovat měny a výběr. Pokud vaše ovládací prvek seznamu není vázán na <xref:System.Windows.Data.CollectionViewSource> objektu jako v následujícím příkladu, je nutné nastavit jeho <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` pro tento postup.  
  
 Další příklady najdete v tématu [vytvořit vazbu na kolekce a zobrazení informací na základě výběru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) a [použití vzoru seznam-podrobnosti s hierarchické Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Jste si všimli, že výše uvedený příklad používá šablonu. Ve skutečnosti, nebude se zobrazí data způsob, jakým jsme chcete bez použití šablony (explicitně používají <xref:System.Windows.Controls.ContentControl> a jeden implicitně používané <xref:System.Windows.Controls.ListBox>). Zapněte jsme teď k ukázka data v další části.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Ukázka dat  
 Bez použití šablon data, aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [co je datová vazba?](#what_is_data_binding) části by vypadat třeba takto:  
  
 ![Ukázka datové vazby bez dat šablony](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 Jak je znázorněno v příkladu v předchozí části, jak <xref:System.Windows.Controls.ListBox> řízení a <xref:System.Windows.Controls.ContentControl> je vázána na objekt celou kolekci (nebo přesněji řečeno, zobrazení přes objekt kolekce) *AuctionItem*s. Bez konkrétní pokyny o tom, jak zobrazit shromažďování dat <xref:System.Windows.Controls.ListBox> je zobrazení řetězcovou reprezentaci každý objekt v kolekci základní a <xref:System.Windows.Controls.ContentControl> je řetězcová reprezentace objektu je vázán k zobrazení.  
  
 Pokud chcete tento problém vyřešit, aplikace definuje <xref:System.Windows.DataTemplate>s. Jak je znázorněno v příkladu v předchozí části, <xref:System.Windows.Controls.ContentControl> explicitně používá *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. <xref:System.Windows.Controls.ListBox> Řízení implicitně používá následující <xref:System.Windows.DataTemplate> při zobrazení *AuctionItem* objekty v kolekci:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 S použitím těchto dvou <xref:System.Windows.DataTemplate>s, výsledná uživatelské rozhraní je uvedeno v [co je datová vazba?](#what_is_data_binding) části. Jak je vidět na tomto snímku obrazovky, kromě povolení můžete umístit data vaše ovládací prvky <xref:System.Windows.DataTemplate>s umožňují definovat zajímavé vizuální prvky pro svá data. Například <xref:System.Windows.DataTrigger>s se používají v výše <xref:System.Windows.DataTemplate> tak, aby *AuctionItem*s s *SpecialFeatures* hodnotu *zvýrazněte* by se mělo zobrazit oranžové ohraničení a hvězdu.  
  
 Další informace o šablonách dat najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Ověřování dat  
  
 Většina aplikací, které získávají uživatelský vstup musí být logiku ověření a ujistěte se, že uživatel zadal očekávané informace. Ověřovací kontroly může být založená na typ, rozsah, formát nebo jiné požadavky na konkrétní aplikace. Tato část popisuje, jak funguje ověřování dat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Přidružení pravidla ověřování s vazbou  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vazby modelu dat umožňuje přiřadit <xref:System.Windows.Data.Binding.ValidationRules%2A> s vaší <xref:System.Windows.Data.Binding> objektu. Například následující příklad vytvoří vazbu <xref:System.Windows.Controls.TextBox> na vlastnost s názvem `StartPrice` a přidá <xref:System.Windows.Controls.ExceptionValidationRule> do objektu <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> vlastnost.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 A <xref:System.Windows.Controls.ValidationRule> objekt zkontroluje, zda hodnota vlastnosti je platný. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má následující dva typy integrovanou <xref:System.Windows.Controls.ValidationRule> objekty:  
  
-   A <xref:System.Windows.Controls.ExceptionValidationRule> kontroluje pro výjimky vydané během aktualizace zdrojová vlastnost vazby. V předchozím příkladu `StartPrice` je typu integer. Když uživatel zadá hodnotu, kterou nelze převést na celé číslo, je vyvolána výjimka, způsobuje vazby označen jako neplatný. Alternativní syntaxe nastavení <xref:System.Windows.Controls.ExceptionValidationRule> je explicitně nastavit <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> vlastnost `true` na vaše <xref:System.Windows.Data.Binding> nebo <xref:System.Windows.Data.MultiBinding> objektu.  
  
-   A <xref:System.Windows.Controls.DataErrorValidationRule> objekt zkontroluje chyby, které jsou vydané objekty, které implementují <xref:System.ComponentModel.IDataErrorInfo> rozhraní. Příklad použití této ověřovací pravidlo, najdete v části <xref:System.Windows.Controls.DataErrorValidationRule>. Alternativní syntaxe nastavení <xref:System.Windows.Controls.DataErrorValidationRule> je explicitně nastavit <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> vlastnost `true` na vaše <xref:System.Windows.Data.Binding> nebo <xref:System.Windows.Data.MultiBinding> objektu.  
  
 Můžete také vytvořit vlastní pravidla ověřování odvozené z <xref:System.Windows.Controls.ValidationRule> třídy a implementace <xref:System.Windows.Controls.ValidationRule.Validate%2A> metoda. Následující příklad ukazuje pravidlem, které používá *přidat výpis produktu* "Počáteční datum" <xref:System.Windows.Controls.TextBox> z [co je datová vazba?](#what_is_data_binding) části:  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> používá toto *FutureDateRule*, jak je znázorněno v následujícím příkladu:  
  
 [!code-xaml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Všimněte si, že <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, modul vazby aktualizuje zdrojové hodnoty na každém stisknutí, což znamená, že také kontroluje každé pravidlo v <xref:System.Windows.Data.Binding.ValidationRules%2A> kolekce na každém stisknutí. To dál probereme v části procesu ověřování.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Poskytnutí zpětné vazby Visual  
 Pokud uživatel zadá neplatnou hodnotu, můžete chtít poskytnout některé zpětnou vazbu o této chybě u aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Jedním ze způsobů, k poskytování zpětné vazby je nastavit <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> přidružená vlastnost pro vlastní <xref:System.Windows.Controls.ControlTemplate>. Jak je uvedeno v předchozí část, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> používá <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> názvem *validationTemplate*. Následující příklad zobrazuje definici *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Element určuje, kde má být umístěn ovládacího prvku se ozdobené.  
  
 Kromě toho můžete také používat <xref:System.Windows.Controls.ToolTip> zobrazíte chybovou zprávu. Obě *StartDateEntryForm* a *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es použít styl *textStyleTextBox*, která vytvoří <xref:System.Windows.Controls.ToolTip> , Zobrazí se chybová zpráva. Následující příklad zobrazuje definici *textStyleTextBox*. Připojená vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je `true` když jedna nebo více vazeb ve vlastnostech vázané elementu je chyba.  
  
 [!code-xaml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 S vlastním <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a <xref:System.Windows.Controls.ToolTip>, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> vypadá jako následující, když dojde k chybě ověření:  
  
 ![Chyba ověřování datové vazby](../../../../docs/framework/wpf/data/media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Pokud vaše <xref:System.Windows.Data.Binding> přidruženy ověřovacích pravidel, ale není zadán <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> na připojeného ovládacího prvku, výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> se použije k upozornit uživatele, když dochází k chybě ověření. Výchozí hodnota <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> je ovládací prvek šablonu, která definuje ve vrstvě adorner červené ohraničení. S výchozím <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a <xref:System.Windows.Controls.ToolTip>, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> vypadá jako následující, když dojde k chybě ověření:  
  
 ![Chyba ověřování datové vazby](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Příklad toho, jak zajistit logiku ověření všech ovládacích prvků v dialogovém okně najdete v části vlastní dialogových oknech v [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Proces ověření  
 Ověření se obvykle dochází, když hodnota cíle se přenese do zdrojová vlastnost vazby. K tomu dochází na <xref:System.Windows.Data.BindingMode.TwoWay> a <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby. K opakují, co způsobí, že zdroj aktualizace závisí na hodnotu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnost, jak je popsáno v [co aktivační události zdroj aktualizací](#what_triggers_source_updates) části.  
  
 Následující text popisuje *ověření* procesu. Všimněte si, že pokud chyba ověření nebo jiný typ chyby dojde k kdykoli během tohoto procesu, je zastavit proces.  
  
1.  Modul vazby kontroluje, zda neexistují žádné vlastní <xref:System.Windows.Controls.ValidationRule> objekty definované, jehož <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven na <xref:System.Windows.Controls.ValidationStep.RawProposedValue> pro tento <xref:System.Windows.Data.Binding>, v takovém případě zavolá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metoda na každém <xref:System.Windows.Controls.ValidationRule> dokud jeden z nich běží došlo k chybě nebo dokud se všechny z nich předat.  
  
2.  Modul vazby pak zavolá převaděč, pokud existuje.  
  
3.  Pokud převaděč úspěšné, modul vazby kontroluje, zda neexistují žádné vlastní <xref:System.Windows.Controls.ValidationRule> objekty definované, jehož <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> pro tento <xref:System.Windows.Data.Binding>, v takovém případě zavolá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metoda na každém <xref:System.Windows.Controls.ValidationRule> s <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> dokud jeden z nich běží došlo k chybě nebo všechny z nich předat.  
  
4.  Modul vazby nastaví vlastnost zdroje.  
  
5.  Modul vazby kontroluje, zda neexistují žádné vlastní <xref:System.Windows.Controls.ValidationRule> objekty definované, jehož <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> pro tento <xref:System.Windows.Data.Binding>, v takovém případě zavolá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metoda na každém <xref:System.Windows.Controls.ValidationRule> s <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> dokud jeden z nich běží došlo k chybě nebo všechny z nich předat. Pokud <xref:System.Windows.Controls.DataErrorValidationRule> souvisí s vazbu a jeho <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena možnost výchozí, <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, <xref:System.Windows.Controls.DataErrorValidationRule> v tomto okamžiku je zaškrtnuté. Toto je také bodem při vazby, které mají <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nastavena na `true` jsou zaškrtnutá políčka.  
  
6.  Modul vazby kontroluje, zda neexistují žádné vlastní <xref:System.Windows.Controls.ValidationRule> objekty definované, jehož <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven na <xref:System.Windows.Controls.ValidationStep.CommittedValue> pro tento <xref:System.Windows.Data.Binding>, v takovém případě zavolá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metoda na každém <xref:System.Windows.Controls.ValidationRule> s <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.CommittedValue> dokud jeden z nich běží došlo k chybě nebo všechny z nich předat.  
  
 Pokud <xref:System.Windows.Controls.ValidationRule> nepředává kdykoli během tohoto procesu vytvoří modul vazby <xref:System.Windows.Controls.ValidationError> objektu a přidává ji k <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> prvku vázané kolekce. Před vazby modul spustí <xref:System.Windows.Controls.ValidationRule> objekty v kterémkoliv daného kroku, se odeberou všechny <xref:System.Windows.Controls.ValidationError> který byl přidán do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> přidružená vlastnost prvku vázané během tohoto kroku. Například pokud <xref:System.Windows.Controls.ValidationRule> jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> se nezdařilo, při příštím procesu ověření dojde, odebere modul vazby, který <xref:System.Windows.Controls.ValidationError> bezprostředně před volání žádné <xref:System.Windows.Controls.ValidationRule> s <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Když <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> není prázdná, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojené elementu je nastavena na `true`. Navíc pokud <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> vlastnost <xref:System.Windows.Data.Binding> je nastaven na `true`, pak vyvolá modul vazby <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> přidružená událost v elementu.  
  
 Také Upozorňujeme, že vymaže přenos platnou hodnotu v obou směrech (cílová na zdroj nebo zdroj cíl) <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> přidružená vlastnost.  
  
 Pokud má vazbu <xref:System.Windows.Controls.ExceptionValidationRule> s ním spojená, nebo neměl <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> je nastavena na `true` a když modul vazby nastaví zdroj, je vyvolána výjimka, modul vazby zkontroluje, jestli je <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Máte možnost k použití <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> zpětného volání zajistit vlastní obslužnou rutinu pro zpracování výjimek. Pokud <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> není zadaný v <xref:System.Windows.Data.Binding>, vytvoří modul vazby <xref:System.Windows.Controls.ValidationError> s výjimkou a přidává ji k <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> prvku vázané kolekce.  
  
## <a name="debugging-mechanism"></a>Ladění mechanismus  
 Připojená vlastnost můžete nastavit <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> u objektu vazby související získat informace o stavu konkrétní vazby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DataErrorValidationRule>  
 [Co je nového ve verzi WPF 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Vazby do výsledků dotazu LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Ukázku datové vazby](http://go.microsoft.com/fwlink/?LinkID=163703)  
 [Postupy: témata](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Vytvoření vazby ke zdroji dat ADO.NET](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)
