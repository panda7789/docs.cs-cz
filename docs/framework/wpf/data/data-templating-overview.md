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
ms.openlocfilehash: 7aed418fe5e2c7d8a217f3016655f39c99300d53
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172487"
---
# <a name="data-templating-overview"></a>Přehled datových šablon
Ukázka datový model WPF vám poskytuje flexibilitu k definování prezentace dat. Ovládacích prvků WPF mít integrovanou funkci pro podporu přizpůsobení prezentace dat. Toto téma nejprve ukazuje, jak definovat <xref:System.Windows.DataTemplate> a pak zavádí další funkce Ukázka dat, jako je výběr šablony založené na vlastní logiky a podpora pro zobrazení hierarchické data.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma se zaměřuje na funkce Ukázka dat a není Úvod datové vazby konceptů. Informace o konceptech vazby základní data, najdete v článku [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> je o prezentaci dat a je jednou z mnoha funkce poskytované službou WPF stylů a Ukázka modelu. Úvod WPF stylů a Ukázka modelu, jako je například používání <xref:System.Windows.Style> nastavení vlastností pro ovládací prvky, najdete v článku [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md) tématu.  
  
 Kromě toho je důležité si uvědomit, `Resources`, které jsou v podstatě co povolit objekty, jako <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate> možné použít opakovaně. Další informace o prostředcích, najdete v části [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Základy Ukázka dat  
  
 K předvedení důvod, proč <xref:System.Windows.DataTemplate> je důležité, projděme příklad vazby na data. V tomto příkladu máme <xref:System.Windows.Controls.ListBox> která je vázaná na seznam `Task` objekty. Každý `Task` objekt má `TaskName` (string) `Description` (string) `Priority` (int) a vlastnost typu `TaskType`, který je `Enum` s hodnotami `Home` a `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Bez šablonu DataTemplate  
 Bez <xref:System.Windows.DataTemplate>, naše <xref:System.Windows.Controls.ListBox> aktuálně vypadá takto:  
  
 ![Data ukázka – snímek obrazovky](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Co se děje je, že bez žádné zvláštní pokyny <xref:System.Windows.Controls.ListBox> voláním výchozí `ToString` při pokusu o zobrazení objektů v kolekci. Proto pokud `Task` objektu přepsání `ToString` metoda, pak se <xref:System.Windows.Controls.ListBox> zobrazí řetězcovou reprezentaci objektu každého zdroje v podkladové kolekci.  
  
 Například pokud `Task` třídy přepsání `ToString` metoda tímto způsobem, kde `name` je pole pro `TaskName` vlastnost:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Pak se <xref:System.Windows.Controls.ListBox> vypadá podobně jako následující:  
  
 ![Data ukázka – snímek obrazovky](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Který je ale limitující a pevná. Navíc pokud vytváříte vazbu na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat, nebude možné přepsat `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definování jednoduché DataTemplate  
 Řešení je k definování <xref:System.Windows.DataTemplate>. Jeden ze způsobů je nastavit <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost <xref:System.Windows.Controls.ListBox> k <xref:System.Windows.DataTemplate>. Zadejte ve vaší <xref:System.Windows.DataTemplate> stane visual strukturu datového objektu. Následující <xref:System.Windows.DataTemplate> je docela jednoduché. Nabízíme pokyny, které každá položka je zobrazena jako tři <xref:System.Windows.Controls.TextBlock> elementů v rámci <xref:System.Windows.Controls.StackPanel>. Každý <xref:System.Windows.Controls.TextBlock> element je vázána na vlastnost `Task` třídy.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Základní data v příkladech v tomto tématu jsou kolekce [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty. Pokud vytváříte vazbu k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat, základní koncepty jsou stejné, ale je mírné syntaktické rozdíl. Například místo nutnosti `Path=TaskName`, byste měli nastavit <xref:System.Windows.Data.Binding.XPath%2A> k `@TaskName` (Pokud `TaskName` je atributem vaší [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] uzlu).  
  
 Nyní naše <xref:System.Windows.Controls.ListBox> vypadá podobně jako následující:  
  
 ![Data ukázka – snímek obrazovky](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Vytváření DataTemplate jako prostředek  
 V předchozím příkladu jsme definovali <xref:System.Windows.DataTemplate> vložené. Je dnes běžné definovat v oddílu prostředků, aby ho bylo možné opakovaně použitelný objekt, jako v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Nyní můžete pomocí `myTaskTemplate` jako prostředek, jako v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Protože `myTaskTemplate` je prostředek, můžete ho teď můžete používat na další ovládací prvky, které mají vlastnost, která přebírá <xref:System.Windows.DataTemplate> typu. Uvedené výše, pro <xref:System.Windows.Controls.ItemsControl> objekty, jako <xref:System.Windows.Controls.ListBox>, je <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost. Pro <xref:System.Windows.Controls.ContentControl> objekty, je <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Vlastnost DataType  
 <xref:System.Windows.DataTemplate> Třída má <xref:System.Windows.DataTemplate.DataType%2A> vlastnost, která je velmi podobné <xref:System.Windows.Style.TargetType%2A> vlastnost <xref:System.Windows.Style> třídy. Proto místo zadávání `x:Key` pro <xref:System.Windows.DataTemplate> v předchozím příkladu, můžete provést následující:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 To <xref:System.Windows.DataTemplate> se automaticky použije na všechny `Task` objekty. Všimněte si, že v tomto případě `x:Key` nastavena implicitně. Proto pokud přiřadíte to <xref:System.Windows.DataTemplate> `x:Key` hodnotu, přepíšete implicitní `x:Key` a <xref:System.Windows.DataTemplate> nebude automaticky použije.  
  
 Pokud vytváříte vazbu <xref:System.Windows.Controls.ContentControl> do kolekce `Task` objekty, <xref:System.Windows.Controls.ContentControl> nepoužívá výše <xref:System.Windows.DataTemplate> automaticky. Důvodem je, že vazba na <xref:System.Windows.Controls.ContentControl> potřebuje další informace k rozlišení, zda chcete vytvořit vazbu na celou kolekci nebo jednotlivé objekty. Pokud vaše <xref:System.Windows.Controls.ContentControl> sledování výběr <xref:System.Windows.Controls.ItemsControl> typu, můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost <xref:System.Windows.Controls.ContentControl> vytvoření vazby na "`/`" k označení, že máte zájem s aktuální položkou. Příklad, naleznete v části [vytvořit vazbu na kolekce a zobrazení informací na základě výběru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Jinak, budete muset zadat <xref:System.Windows.DataTemplate> explicitně nastavením <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.  
  
 <xref:System.Windows.DataTemplate.DataType%2A> Vlastnost je zvláště užitečné, když máte <xref:System.Windows.Data.CompositeCollection> různých typů datových objektů. Příklad, naleznete v části [implementovat CompositeCollection](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Přidání více do DataTemplate  
 Aktuálně se zobrazí data s potřebné informace, ale je výborný prostor pro zlepšení. Umožňuje zvýšit na prezentaci přidáním <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>a některé <xref:System.Windows.Controls.TextBlock> prvky, které popisuje data, která se zobrazuje.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Následující snímek obrazovky ukazuje <xref:System.Windows.Controls.ListBox> s tímto upravit <xref:System.Windows.DataTemplate>:  
  
 ![Data ukázka – snímek obrazovky](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Můžete nastavit jsme <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> k <xref:System.Windows.HorizontalAlignment.Stretch> na <xref:System.Windows.Controls.ListBox> a ujistěte se, šířku položky zabírají celého prostoru:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Pomocí <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastnost nastavena na hodnotu <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> teď to vypadá jako:  
  
 ![Data ukázka – snímek obrazovky](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Pomocí DataTriggers použít hodnoty vlastností  
 Aktuální prezentace není Řekněte nám, jestli `Task` domácí úkol nebo úkol aplikace office. Nezapomeňte, že `Task` objekt má `TaskType` vlastnost typu `TaskType`, což je výčet s hodnotami `Home` a `Work`.  
  
 V následujícím příkladu <xref:System.Windows.DataTrigger> nastaví <xref:System.Windows.Controls.Border.BorderBrush%2A> elementu s názvem `border` k `Yellow` Pokud `TaskType` vlastnost je `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Naše aplikace teď vypadá takto. Se žlutou ohraničení objeví domovské úlohy a úkoly office se zobrazí s aqua ohraničení:  
  
 ![Data ukázka – snímek obrazovky](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 V tomto příkladu <xref:System.Windows.DataTrigger> používá <xref:System.Windows.Setter> nastavit hodnotu vlastnosti. Aktivační událost třídy mají také <xref:System.Windows.TriggerBase.EnterActions%2A> a <xref:System.Windows.TriggerBase.ExitActions%2A> vlastnosti, které umožňují spustit sadu akcí, například animace. Kromě toho je také <xref:System.Windows.MultiDataTrigger> třídu, která umožňuje použít změny podle více hodnot vlastností vázané na data.  
  
 Alternativní způsob k dosažení stejného efektu je vytvoření vazby <xref:System.Windows.Controls.Border.BorderBrush%2A> vlastnost, která má `TaskType` vlastnost a použití na základě převaděč hodnoty vrátit barvu `TaskType` hodnotu. Vytvoření výše účinek použití převaděč je mírně efektivnější z hlediska výkonu. Kromě toho vytváření vlastních převaděč umožňuje větší flexibilitu, protože jsou zadávání vlastní logiky. Nakonec technika, který zvolíte, závisí na váš scénář a vaši volbu. Informace o tom, jak psát převaděč najdete v tématu <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Co patří šablonu DataTemplate?  

V předchozím příkladu jsme aktivační události v rámci umístit <xref:System.Windows.DataTemplate> pomocí <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> Vlastnost. <xref:System.Windows.Setter> Aktivační události nastaví hodnotu vlastnosti elementu ( <xref:System.Windows.Controls.Border> element), je v rámci <xref:System.Windows.DataTemplate>. Ale pokud vlastnosti, vaše `Setters` se týká nejsou vlastností elementů, které jsou v aktuálním <xref:System.Windows.DataTemplate>, může být vhodnější pro nastavení vlastností pomocí <xref:System.Windows.Style> , je pro <xref:System.Windows.Controls.ListBoxItem> – třída (Pokud je jsou vazbu ovládacího prvku <xref:System.Windows.Controls.ListBox>). Například, pokud chcete, aby vaše <xref:System.Windows.Trigger> pro animaci <xref:System.Windows.UIElement.Opacity%2A> hodnotu položky při myši odkazuje na položku, můžete definovat aktivační události v rámci <xref:System.Windows.Controls.ListBoxItem> stylu. Příklad, naleznete v části [Úvod do stylů a ukázka ukázková](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Obecně platí, mějte na paměti, <xref:System.Windows.DataTemplate> se právě používá ke každému vygenerovaného <xref:System.Windows.Controls.ListBoxItem> (Další informace o tom, jak a kde se ve skutečnosti používá, najdete v článku <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> stránky.). Vaše <xref:System.Windows.DataTemplate> je se prezentace a vzhled datových objektů. Ve většině případů všechny aspekty prezentace, například jaké položku vypadá, když je vybraná nebo jak <xref:System.Windows.Controls.ListBox> vytvoří se položky, nejsou členy v definici <xref:System.Windows.DataTemplate>. Příklad, naleznete v části [stylů a ukázka ItemsControl](#DataTemplating_ItemsControl) části.  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Vybrat šablonu DataTemplate na základě vlastností datový objekt  
 V [The vlastnost DataType](#Styling_DataType) části jsme se bavili, můžete definovat různé datové šablony pro různé datové objekty. Který je obzvláště užitečná, když máte <xref:System.Windows.Data.CompositeCollection> různé typy nebo kolekce s položkami různých typů. V [použít DataTriggers použít hodnoty vlastností](#DataTrigger_to_Apply_Property_Values) části nám ukázaly, že pokud máte kolekce stejného typu datových objektů můžete vytvořit <xref:System.Windows.DataTemplate> a pak provést změny podle hodnoty vlastností pomocí aktivační události Každý datový objekt. Aktivační události umožňují použít hodnoty vlastností nebo spuštění animace ale budou nemáte poskytují flexibilitu pro rekonstrukci strukturu datových objektů. Některé scénáře mohou vyžadovat vytvoření jiné <xref:System.Windows.DataTemplate> pro data zadejte objekty, které jsou stejné, ale mají jiné vlastnosti.  
  
 Například když `Task` objekt má `Priority` hodnotu `1`, můžete chtít poskytněte vypadá a úplně jiné sloužit jako výstrahu sami. V takovém případě můžete vytvořit <xref:System.Windows.DataTemplate> pro zobrazení vysokou prioritou `Task` objekty. Umožňuje přidat následující <xref:System.Windows.DataTemplate> do části prostředky:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Všimněte si v tomto příkladu <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> Vlastnost. Prostředky, které jsou definované v tomto oddílu jsou sdíleny elementů v rámci <xref:System.Windows.DataTemplate>.  
  
 K poskytování logiku vybrat, které <xref:System.Windows.DataTemplate> používat na základě `Priority` hodnota datového objektu, vytvořte podtřídu <xref:System.Windows.Controls.DataTemplateSelector> a přepsat <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metoda. V následujícím příkladu <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metoda obsahuje logiku a vrátí příslušné šablony založené na hodnotu `Priority` vlastnost. Šablonu, kterou chcete vrátit se nachází v prostředků zahrnují <xref:System.Windows.Window> elementu.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Můžete pak deklarovat `TaskListDataTemplateSelector` jako prostředek:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Pokud chcete použít pro výběr prostředku šablony, přiřadit ho k <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> vlastnost <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> Volání <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metodu `TaskListDataTemplateSelector` pro každou položku v kolekci základní. Volání předá datový objekt jako parametr položky. <xref:System.Windows.DataTemplate> , Vrátí metoda se potom použije tento datový objekt.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Pomocí modulu pro výběr šablony na místě <xref:System.Windows.Controls.ListBox> nyní vypadat takto:  
  
 ![Data ukázka – snímek obrazovky](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Tato diskuse tohoto příkladu se ukončí. Kompletní příklad, najdete v části [Úvod do vzorek dat ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Styly a ukázka ItemsControl a  
 I když <xref:System.Windows.Controls.ItemsControl> není pouze typ ovládacího prvku, který můžete použít <xref:System.Windows.DataTemplate> , jedná o velmi běžný scénář vytvořit vazbu <xref:System.Windows.Controls.ItemsControl> do kolekce. V [co patří šablonu DataTemplate](#what_belongs_in_datatemplate) části jsme se bavili, definice vaší <xref:System.Windows.DataTemplate> by měly být jenom nevadí prezentaci dat. Chcete-li vědět, když není vhodné používat <xref:System.Windows.DataTemplate> je důležité pochopit různé vlastnosti stylu a šablony poskytované <xref:System.Windows.Controls.ItemsControl>. Následující příklad je určen k objasnění funkce každé z těchto vlastností. <xref:System.Windows.Controls.ItemsControl> v tomto příkladu je vázána na stejnou `Tasks` kolekce jako v předchozím příkladu. Pro demonstrační účely, styly a šablony v tomto příkladu jsou všechny deklarované v textu.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Zde je snímek obrazovky v příkladu je vykreslen:  
  
 ![Snímek obrazovky příklad ItemsControl](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Všimněte si, že místo použití <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, můžete použít <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Informace naleznete v sekci předchozí příklad. Podobně, místo použití <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, máte možnost k použití <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Dva další související se styly vlastnosti <xref:System.Windows.Controls.ItemsControl> , nejsou zobrazeny. tady jsou <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> a <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Podpora pro hierarchické dat  
 Zatím jsme mít hledá pouze v tom, jak vytvořit vazbu k a zobrazit jedna kolekce. Někdy je nutné kolekce, která obsahuje jiné kolekce. <xref:System.Windows.HierarchicalDataTemplate> Třída je určen k použití s <xref:System.Windows.Controls.HeaderedItemsControl> typy zobrazíte taková data. V následujícím příkladu `ListLeagueList` je seznam `League` objekty. Každý `League` objekt má `Name` a kolekce `Division` objekty. Každý `Division` má `Name` a kolekce `Team` objektů a každý `Team` objekt má `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 Tento příklad ukazuje, že s použitím <xref:System.Windows.HierarchicalDataTemplate>, můžete snadno zobrazit seznam dat, který obsahuje jiné seznamy. Zde je snímek obrazovky v příkladu.  
  
 ![Snímek obrazovky HierarchicalDataTemplate –](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Viz také  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Hledání elementů generovaných šablonou DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled stylů záhlaví sloupců a šablon GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)
