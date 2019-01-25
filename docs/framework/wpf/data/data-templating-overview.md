---
title: Přehled datových šablon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
ms.openlocfilehash: 5f5a821a05c36a8672c68caf2b31971bbf9be724
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680985"
---
# <a name="data-templating-overview"></a>Přehled datových šablon
Datový model šablonování WPF vám poskytuje flexibilitu pro definování prezentace dat. Ovládací prvky WPF mít integrovanou funkci podporující přizpůsobení prezentace dat. Toto téma nejprve ukazuje, jak definovat <xref:System.Windows.DataTemplate> a potom zavádí další funkce šablon dat, jako je například výběr šablony založené na vlastní logiku a podporu pro zobrazení hierarchická data.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma se zaměřuje na funkce šablon dat a není Úvod koncepty vazeb data. Informace o základní datové vazby koncepty, najdete v článku [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> spočívá v prezentaci dat a je jedním z mnoha funkcím, které poskytuje model WPF styly a šablony. Úvod WPF styly a šablony modelu, jako je například použití <xref:System.Windows.Style> nastavit vlastnosti v ovládacích prvcích, najdete v článku [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md) tématu.  
  
 Kromě toho je důležité pochopit `Resources`, které jsou v podstatě co povolit objektů, jako <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> bude opakovaně použitelné. Další informace o prostředcích naleznete v tématu [prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Základy šablon dat  
  
 K předvedení důvod, proč <xref:System.Windows.DataTemplate> je důležité, projděme si příklad vazby dat. V tomto příkladu máme <xref:System.Windows.Controls.ListBox> , který je vázán na seznam `Task` objekty. Každý `Task` objekt má `TaskName` (řetězec), `Description` (řetězec), `Priority` (int) a vlastnost typu `TaskType`, což je `Enum` s hodnotami `Home` a `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Bez šablonu DataTemplate  
 Bez <xref:System.Windows.DataTemplate>, naše <xref:System.Windows.Controls.ListBox> aktuálně vypadá přibližně takto:  
  
 ![Snímek obrazovky ukázky šablon dat](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Co se děje, který nemá žádné zvláštní pokyny <xref:System.Windows.Controls.ListBox> voláním výchozí `ToString` při pokusu o zobrazení objektů v kolekci. Proto pokud `Task` objektu přepsání `ToString` metoda, pak bude <xref:System.Windows.Controls.ListBox> řetězcovou reprezentaci objektu každého zdroje se zobrazí v zdrojové kolekce.  
  
 Například pokud `Task` třídy přepsání `ToString` metoda tímto způsobem, kde `name` je pole pro `TaskName` vlastnost:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Pak bude <xref:System.Windows.Controls.ListBox> vypadá následovně:  
  
 ![Snímek obrazovky ukázky šablon dat](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Ale to je omezující tak pevná. Navíc pokud se vazba na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat, nebude možné přepsat `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definování jednoduchý DataTemplate  
 Toto řešení je k definování <xref:System.Windows.DataTemplate>. Provedete to jedním ze způsobů je nastavit <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost <xref:System.Windows.Controls.ListBox> k <xref:System.Windows.DataTemplate>. Zadejte ve vaší <xref:System.Windows.DataTemplate> stane vizuální struktury datový objekt. Následující <xref:System.Windows.DataTemplate> je docela jednoduché. Nabízíme pokyny, které každá položka zobrazuje jako tři <xref:System.Windows.Controls.TextBlock> elementů v rámci <xref:System.Windows.Controls.StackPanel>. Každý <xref:System.Windows.Controls.TextBlock> element je vázána na vlastnost `Task` třídy.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Podkladová data pro příklady v tomto tématu je kolekce [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty. Pokud se vazba na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat, základní koncepty jsou stejné, ale není lehké syntaktické rozdíly. Například namísto toho, aby `Path=TaskName`, nastavíte <xref:System.Windows.Data.Binding.XPath%2A> k `@TaskName` (Pokud `TaskName` je atributem vaše [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] uzlu).  
  
 Teď naše <xref:System.Windows.Controls.ListBox> vypadá následovně:  
  
 ![Snímek obrazovky ukázky šablon dat](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Vytváří šablonou DataTemplate jako prostředek  
 V předchozím příkladu jsme definovali <xref:System.Windows.DataTemplate> vložené. Je běžné definovat v části prostředky, proto to může být opakovaně použitelný objekt, jako v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Nyní můžete pomocí `myTaskTemplate` jako prostředek, jako v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Protože `myTaskTemplate` je prostředek, můžete ho teď můžete používat na další ovládací prvky, které mají vlastnost, která přijímá <xref:System.Windows.DataTemplate> typu. Uvedeno výše pro <xref:System.Windows.Controls.ItemsControl> objekty, jako <xref:System.Windows.Controls.ListBox>, je <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost. Pro <xref:System.Windows.Controls.ContentControl> objekty, je <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Vlastnost DataType objektu  
 <xref:System.Windows.DataTemplate> Třída nemá <xref:System.Windows.DataTemplate.DataType%2A> vlastnost, která je velmi podobný <xref:System.Windows.Style.TargetType%2A> vlastnost <xref:System.Windows.Style> třídy. Proto se místo určení `x:Key` pro <xref:System.Windows.DataTemplate> v předchozím příkladu můžete dělat tyto věci:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 To <xref:System.Windows.DataTemplate> se automaticky použije na všechny `Task` objekty. Všimněte si, že v tomto případě `x:Key` je implicitně nastaven. Proto pokud přiřadíte tyto <xref:System.Windows.DataTemplate> `x:Key` hodnotu, přepíšete implicitní `x:Key` a <xref:System.Windows.DataTemplate> by použije automaticky.  
  
 Pokud vytváříte vazbu <xref:System.Windows.Controls.ContentControl> na kolekci `Task` objekty, <xref:System.Windows.Controls.ContentControl> nepoužívá výše <xref:System.Windows.DataTemplate> automaticky. Důvodem je, že vazba na <xref:System.Windows.Controls.ContentControl> potřebuje více informací k rozlišení, zda chcete vytvořit vazbu na celou kolekci nebo jednotlivé objekty. Pokud vaše <xref:System.Windows.Controls.ContentControl> sleduje výběr <xref:System.Windows.Controls.ItemsControl> typ, můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost <xref:System.Windows.Controls.ContentControl> vytvoření vazby na "`/`" k označení, že máte zájem o aktuální položky. Příklad najdete v tématu [připojení ke kolekci a zobrazení informací podle výběru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md). V opačném případě budete muset zadat <xref:System.Windows.DataTemplate> explicitně nastavením <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.  
  
 <xref:System.Windows.DataTemplate.DataType%2A> Vlastnost je zvláště užitečná v případě, že máte <xref:System.Windows.Data.CompositeCollection> různé typy datových objektů. Příklad najdete v tématu [implementace CompositeCollection](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Přidání více DataTemplate  
 Aktuálně se zobrazí data potřebné informace, ale je jednoznačně volného místa pro zlepšení. Můžeme zlepšit v prezentaci tak, že přidáte <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>a některé <xref:System.Windows.Controls.TextBlock> prvky, které popisují data, která se zobrazí.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Následující snímek obrazovky ukazuje <xref:System.Windows.Controls.ListBox> to změnit <xref:System.Windows.DataTemplate>:  
  
 ![Snímek obrazovky ukázky šablon dat](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Můžete nastavíme <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> k <xref:System.Windows.HorizontalAlignment.Stretch> na <xref:System.Windows.Controls.ListBox> k Ujistěte se, že šířku položky zabírá celé místo:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 S <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastnost nastavena na hodnotu <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> teď vypadá přibližně takto:  
  
 ![Snímek obrazovky ukázky šablon dat](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Pomocí DataTriggers použít hodnoty vlastností  
 Aktuální prezentaci není Řekněte nám, jestli `Task` domácí úkol nebo úkol aplikace office. Nezapomeňte, že `Task` má objekt `TaskType` vlastnost typu `TaskType`, což je výčet s hodnotami `Home` a `Work`.  
  
 V následujícím příkladu <xref:System.Windows.DataTrigger> nastaví <xref:System.Windows.Controls.Border.BorderBrush%2A> elementu s názvem `border` k `Yellow` Pokud `TaskType` vlastnost `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Naší aplikace teď bude vypadat nějak takto. Domovské úlohy zobrazí žluté ohraničení a úlohy sady office s akvamarínový ohraničení:  
  
 ![Snímek obrazovky ukázky šablon dat](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 V tomto příkladu <xref:System.Windows.DataTrigger> používá <xref:System.Windows.Setter> nastavit hodnotu vlastnosti. Aktivační událost třídy také mají <xref:System.Windows.TriggerBase.EnterActions%2A> a <xref:System.Windows.TriggerBase.ExitActions%2A> vlastnosti, které umožňují spustit sadu akcí, jako je například animace. Kromě toho je také <xref:System.Windows.MultiDataTrigger> třídu, která vám umožní použít změny podle několika hodnot vlastností vázané na data.  
  
 Alternativní způsob k dosažení stejného výsledku je vytvořit vazbu <xref:System.Windows.Controls.Border.BorderBrush%2A> vlastnost `TaskType` vlastnost a použití převaděč hodnot ke vrátí barvu na základě `TaskType` hodnotu. Vytvoření výše účinek použití převaděče je efektivnější z hlediska výkonu. Kromě toho vytváření vlastních převaděč vám zajistí větší flexibilitu vzhledem k tomu, že zadáváte vlastní logiku. Nakonec technika, kterou zvolíte, závisí na váš scénář a dáváte přednost. Informace o tom, jak psát konvertor najdete v tématu <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Co patří šablonu DataTemplate?  

V předchozím příkladu jsme aktivační události v rámci umístěn <xref:System.Windows.DataTemplate> pomocí <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> Vlastnost. <xref:System.Windows.Setter> Triggeru nastaví hodnotu vlastnosti elementu ( <xref:System.Windows.Controls.Border> prvek), který je v rámci <xref:System.Windows.DataTemplate>. Ale pokud vlastnosti, která vaše `Setters` se týká nejsou vlastnosti prvků, které jsou v aktuálním <xref:System.Windows.DataTemplate>, může být vhodnější pro nastavení vlastnosti pomocí <xref:System.Windows.Style> , který je pro <xref:System.Windows.Controls.ListBoxItem> třídy (Pokud ovládací prvek svážete <xref:System.Windows.Controls.ListBox>). Například, pokud chcete, aby vaše <xref:System.Windows.Trigger> pro animaci <xref:System.Windows.UIElement.Opacity%2A> hodnotu položky při myši odkazuje na položku, můžete definovat aktivační události v rámci <xref:System.Windows.Controls.ListBoxItem> style. Příklad najdete v tématu [Úvod do používání stylů a šablon ukázková](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Obecně platí, mějte na paměti, která <xref:System.Windows.DataTemplate> platí pro každý z generované <xref:System.Windows.Controls.ListBoxItem> (Další informace o tom, jak a kde je skutečně používají, najdete v článku <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> stránky.). Vaše <xref:System.Windows.DataTemplate> se zabývají prezentace a vzhled datových objektů. Ve většině případů, všechny ostatní aspekty prezentací, jako je například jaké položky vypadá, když je zaškrtnuto nebo jak <xref:System.Windows.Controls.ListBox> stanoví položek, nepatří do definice <xref:System.Windows.DataTemplate>. Příklad najdete v tématu [styly a šablony prvku ItemsControl](#DataTemplating_ItemsControl) oddílu.  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Výběr DataTemplate na základě vlastností datového objektu  
 V [vlastnost DataType](#Styling_DataType) části jsme probírali, že můžete definovat různé datové šablony pro různé datové objekty. Který je obzvláště užitečné, pokud máte <xref:System.Windows.Data.CompositeCollection> různé typy nebo kolekce s položkami různých typů. V [použít DataTriggers použít hodnoty vlastností](#DataTrigger_to_Apply_Property_Values) části nám ukázaly, že pokud máte kolekci stejný typ datových objektů můžete vytvořit <xref:System.Windows.DataTemplate> a pak provést změny podle hodnoty vlastností pomocí aktivační události Každý datový objekt. Aktivační události vám umožňují použít hodnoty vlastností nebo spuštění animace ale není poskytují flexibilitu pro rekonstrukci strukturu vašich datových objektů. Některé scénáře mohou vyžadovat vytvoření jiného <xref:System.Windows.DataTemplate> pro data objekty, které jsou stejného typu, ale mají různé vlastnosti.  
  
 Například, když `Task` má objekt `Priority` hodnotu `1`, možná budete chtít jí úplně jiné najdete sloužit jako upozornění pro sebe. V takovém případě můžete vytvořit <xref:System.Windows.DataTemplate> pro zobrazení Vysoká priorita `Task` objekty. Přidejte následující <xref:System.Windows.DataTemplate> do části prostředky:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Všimněte si, že v tomto příkladu <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> Vlastnost. Prostředky, které jsou definovány v tom, že část sdílí elementů v rámci <xref:System.Windows.DataTemplate>.  
  
 Slouží k poskytování logiky vybrat, které <xref:System.Windows.DataTemplate> používat na základě `Priority` hodnotu datového objektu, vytvořit podtřídu <xref:System.Windows.Controls.DataTemplateSelector> a přepsat <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metoda. V následujícím příkladu <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metoda obsahuje logiku a vrátí odpovídající šablony založené na hodnotě `Priority` vlastnost. Šablonu, kterou chcete vrátit se nachází v prostředků fakturovaly <xref:System.Windows.Window> elementu.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 My pak může deklarovat `TaskListDataTemplateSelector` jako prostředek:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Použít prostředek selektor šablony, přiřadit ji ke <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> vlastnost <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> Volání <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metodu `TaskListDataTemplateSelector` pro každou z položek v zdrojové kolekce. Volání předá jako parametr položky datový objekt. <xref:System.Windows.DataTemplate> , Který je vrácen metodu se následně použije na tento datový objekt.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Pomocí selektoru šablon na místě <xref:System.Windows.Controls.ListBox> nyní vypadat takto:  
  
 ![Snímek obrazovky ukázky šablon dat](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Tím končí naše diskuse tohoto příkladu. Úplnou ukázku najdete v tématu [Úvod do šablon ukázková Data](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Styly a šablony prvku ItemsControl  
 I v případě, <xref:System.Windows.Controls.ItemsControl> není jediný typ ovládacího prvku, který vám pomůže <xref:System.Windows.DataTemplate> , je velmi běžný scénář, kdy vytvořit vazbu <xref:System.Windows.Controls.ItemsControl> do kolekce. V [co patří šablonu DataTemplate](#what_belongs_in_datatemplate) oddílu, který jsme probírali definici vaší <xref:System.Windows.DataTemplate> by měly být jenom obeznámeni s prezentaci dat. Pokud chcete zjistit, kdy není vhodné používat <xref:System.Windows.DataTemplate> je důležité pochopit různé vlastnosti stylu a šablon poskytnutých <xref:System.Windows.Controls.ItemsControl>. V následujícím příkladu je určen k objasnění funkce každého z těchto vlastností. <xref:System.Windows.Controls.ItemsControl> v tomto příkladu je vázán na stejnou `Tasks` kolekce jako v předchozím příkladu. Pro demonstrační účely, styly a šablony v tomto příkladu jsou všechny deklarované v textu.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Toto je snímek obrazovky v příkladu, při vykreslení:  
  
 ![Ukázkový snímek ItemsControl](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Všimněte si, že místo použití <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, můžete použít <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Přečtěte si část předchozí příklad. Podobně, namísto použití <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, máte možnost k použití <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Dvě další související se stylem vlastnosti <xref:System.Windows.Controls.ItemsControl> , který se nezobrazují, tady jsou <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> a <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Podpora hierarchických dat  
 Zatím jste pouze zvažovali jsme jak svázat a zobrazit jednu kolekci. Někdy je nutné kolekci, která obsahuje jiné kolekce. <xref:System.Windows.HierarchicalDataTemplate> Třídy je určen pro použití s <xref:System.Windows.Controls.HeaderedItemsControl> typů, který chcete zobrazit tyto údaje. V následujícím příkladu `ListLeagueList` je seznam `League` objekty. Každý `League` má objekt `Name` a kolekce `Division` objekty. Každý `Division` má `Name` a kolekce `Team` objektů a každý `Team` má objekt `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 Tento příklad ukazuje, že s použitím <xref:System.Windows.HierarchicalDataTemplate>, můžete snadno zobrazit seznam dat, který obsahuje jiné seznamy. Zde je snímek obrazovky v příkladu.  
  
 ![Snímek obrazovky ukázkové HierarchicalDataTemplate –](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Viz také:
- [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Hledání elementů generovaných šablonou DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Přehled stylů záhlaví sloupců a šablon GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)
