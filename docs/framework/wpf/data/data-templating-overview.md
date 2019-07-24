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
ms.openlocfilehash: 556ce7b42f13d7c5ba7fba36b09277cda9bcae5d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400662"
---
# <a name="data-templating-overview"></a>Přehled datových šablon
Model dat šablonování WPF poskytuje skvělou flexibilitu pro definování prezentace vašich dat. Ovládací prvky WPF mají integrovanou funkcionalitu, která podporuje přizpůsobení prezentace dat. Toto téma nejprve ukazuje, jak definovat <xref:System.Windows.DataTemplate> a následně zavádí další funkce šablonování dat, jako je například výběr šablon založených na vlastní logice a podpora zobrazení hierarchických dat.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma se zaměřuje na funkce šablonování dat a není Úvod k konceptům datových vazeb. Informace o základních konceptech datových vazeb najdete v tématu [Přehled datové vazby](data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate>je o prezentaci dat a je jednou z mnoha funkcí poskytovaných stylem WPF a modelem šablonování. Základní informace o stylu WPF a modelu šablonování, například jak použít <xref:System.Windows.Style> k nastavení vlastností ovládacích prvků, naleznete v tématu [stylování a šablonování](../controls/styling-and-templating.md) .  
  
 Kromě toho je důležité pochopit `Resources`, co je v podstatě to, co je potřeba k opakovanému použití objektů <xref:System.Windows.Style> , jako jsou a <xref:System.Windows.DataTemplate> . Další informace o prostředcích najdete v tématu věnovaném [prostředkům XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Základy šablonování dat  
  
 Abychom ukázali <xref:System.Windows.DataTemplate> , proč je důležité, Podívejme se na příklad datové vazby. V tomto příkladu máme <xref:System.Windows.Controls.ListBox> objekt vázaný na `Task` seznam objektů. Každý `Task` objekt `Priority` `TaskType` `Home` `Enum` `Work`má `TaskName` (řetězec),(String),a(int)avlastnosttypu,cožje`Description` s hodnotami a.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Bez šablony DataTemplate  
 Bez a <xref:System.Windows.DataTemplate>by náš <xref:System.Windows.Controls.ListBox> v současnosti vypadal takto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 To se děje proto, že bez jakýchkoli specifických instrukcí <xref:System.Windows.Controls.ListBox> ve výchozím nastavení `ToString` volá při pokusu o zobrazení objektů v kolekci. Proto pokud `Task` objekt `ToString` přepisuje metodu, pak <xref:System.Windows.Controls.ListBox> zobrazí řetězcovou reprezentaci každého zdrojového objektu v příslušné kolekci.  
  
 Například pokud `Task` třída `ToString` přepíše metodu tímto způsobem, kde `name` je pole pro `TaskName` vlastnost:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 <xref:System.Windows.Controls.ListBox> Pak vypadá jako toto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 To však omezuje a neflexibilní. Pokud vytváříte vazbu na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, nebudete moct přepsat. `ToString`  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definování jednoduché šablony DataTemplate  
 Řešením je definování <xref:System.Windows.DataTemplate>. Jedním ze způsobů, jak to provést, je <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> nastavit vlastnost <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>na. To, co zadáte <xref:System.Windows.DataTemplate> v rámci, se bude vizuálně strukturou datového objektu. <xref:System.Windows.DataTemplate> Toto je poměrně jednoduché. Poskytujeme pokyny, že se každá položka zobrazí jako <xref:System.Windows.Controls.TextBlock> tři prvky <xref:System.Windows.Controls.StackPanel>v rámci. Každý <xref:System.Windows.Controls.TextBlock> prvek je svázán s vlastností `Task` třídy.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Podkladová data pro příklady v tomto tématu jsou kolekce objektů CLR. Pokud vytváříte vazbu na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, základní koncepty jsou stejné, ale je to mírně syntaktický rozdíl. Například místo `Path=TaskName`toho byste měli `@TaskName` nastavit <xref:System.Windows.Data.Binding.XPath%2A> (Pokud `TaskName` je atribut vašeho [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] uzlu).  
  
 <xref:System.Windows.Controls.ListBox> Teď vypadá to, že by to vypadalo takto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Vytvoření DataTemplate jako prostředku  
 Ve výše uvedeném příkladu jsme definovali <xref:System.Windows.DataTemplate> inline. Je běžnější ji definovat v části Resources (prostředky), takže se může jednat o opakovaně použitelný objekt, jak je uvedeno v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Nyní můžete použít `myTaskTemplate` jako prostředek, jako v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Vzhledem `myTaskTemplate` k tomu, že je prostředek, můžete jej nyní použít na jiné ovládací prvky, které mají vlastnost <xref:System.Windows.DataTemplate> , která přebírá typ. Jak je uvedeno výše, <xref:System.Windows.Controls.ItemsControl> pro objekty, <xref:System.Windows.Controls.ListBox>jako například, je <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> to vlastnost. Pro <xref:System.Windows.Controls.ContentControl> objekty<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> je to vlastnost.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Vlastnost DataType  
 Třída má vlastnost, která <xref:System.Windows.Style.TargetType%2A> je velmi podobná vlastnosti <xref:System.Windows.Style> třídy. <xref:System.Windows.DataTemplate.DataType%2A> <xref:System.Windows.DataTemplate> Místo toho, abyste `x:Key` <xref:System.Windows.DataTemplate> v předchozím příkladu určili pro, můžete postupovat takto:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 To <xref:System.Windows.DataTemplate> se automaticky použije pro všechny `Task` objekty. Všimněte si, že v tomto `x:Key` případě je nastaven implicitně. Proto pokud přiřadíte tuto <xref:System.Windows.DataTemplate> `x:Key` hodnotu, přepíšete implicitní `x:Key` a <xref:System.Windows.DataTemplate> automaticky se nepoužije.  
  
 Pokud vytváříte vazbu a <xref:System.Windows.Controls.ContentControl> ke `Task` kolekci objektů, <xref:System.Windows.Controls.ContentControl> nepoužije se výše uvedené <xref:System.Windows.DataTemplate> automaticky. Důvodem je to, že vazba na <xref:System.Windows.Controls.ContentControl> určitou potřebnou informaci rozliší, zda chcete vytvořit vazbu na celou kolekci nebo jednotlivé objekty. <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Controls.ContentControl> Pokud sledujete výběr typu, můžete nastavit vlastnost vazby na`/`"", která označuje, že máte zájem o aktuální položku. <xref:System.Windows.Controls.ContentControl> Příklad naleznete v tématu [vazba na kolekci a zobrazení informací na základě výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). V opačném případě je nutné <xref:System.Windows.DataTemplate> explicitně zadat <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> nastavení vlastnosti.  
  
 Tato <xref:System.Windows.DataTemplate.DataType%2A> vlastnost je užitečná hlavně v případě, že <xref:System.Windows.Data.CompositeCollection> máte různé typy datových objektů. Příklad naleznete v tématu [implementace složené sadycollection](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Přidání dalších do šablony DataTemplate  
 V současné době se data zobrazují s potřebnými informacemi, ale pro zlepšení je k dispozici jen omezení místa. Pojďme vylepšit prezentaci přidáním <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Grid>, a a některých <xref:System.Windows.Controls.TextBlock> prvků popisujících zobrazená data.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Následující snímek obrazovky ukazuje <xref:System.Windows.Controls.ListBox> s tímto upraveným: <xref:System.Windows.DataTemplate>  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Můžeme nastavit <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> na ,<xref:System.Windows.Controls.ListBox> aby se zajistilo, že šířka položek zabere celé místo:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 S vlastností nastavenou na <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> teď vypadá takto: <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Použijte k použití hodnot vlastností datatriggery  
 Aktuální prezentace nám neřekne, jestli je `Task` to Domovská úloha nebo úkol Office. `Task` Mějte na paměti, že objekt `TaskType` má vlastnost typu `TaskType`, což je výčet s hodnotami `Home` a `Work`.  
  
 <xref:System.Windows.DataTrigger> V následujícím příkladu <xref:System.Windows.Controls.Border.BorderBrush%2A> nastaví `border` `Yellow` prvekelementu`TaskType.Home`s názvem na, pokud je vlastnost.`TaskType`  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Naše aplikace teď vypadá jako v následujícím příkladu. Domovské úkoly se zobrazí se žlutým ohraničením a úkoly Office se zobrazí s azurová ohraničením:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 V tomto příkladu <xref:System.Windows.Setter> používá <xref:System.Windows.DataTrigger> nástroj k nastavení hodnoty vlastnosti. Třídy triggeru mají <xref:System.Windows.TriggerBase.EnterActions%2A> také vlastnosti a <xref:System.Windows.TriggerBase.ExitActions%2A> , které umožňují spustit sadu akcí, například animace. Kromě toho existuje také <xref:System.Windows.MultiDataTrigger> třída, která umožňuje použít změny založené na více hodnotách vlastností vázaných na data.  
  
 Alternativním způsobem, jak dosáhnout stejného účinku, je vytvořit vazby <xref:System.Windows.Controls.Border.BorderBrush%2A> vlastnosti `TaskType` k vlastnosti a použít konvertor hodnoty k vrácení barvy na základě `TaskType` hodnoty. Vytvoření výše uvedeného efektu pomocí převaděče je mírně efektivnější z pohledu výkonu. Vytváření vlastního převaděče navíc přináší větší flexibilitu, protože poskytujete vlastní logiku. A nakonec, kterou metodu zvolíte, závisí na vašem scénáři a vaší předvolbě. Informace o tom, jak napsat převaděč, najdete v <xref:System.Windows.Data.IValueConverter>tématu.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Co patří do šablony DataTemplate?  

V předchozím příkladu jsme vložili Trigger do <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate>pomocí.<xref:System.Windows.DataTemplate.Triggers%2A> majetek. Aktivační událost nastavuje hodnotu vlastnosti elementu <xref:System.Windows.Controls.Border> (elementu <xref:System.Windows.DataTemplate>), který je v rámci. <xref:System.Windows.Setter> Nicméně `Setters` Pokud vlastnosti, které jsou na starosti, nejsou vlastnostmi prvků, které jsou v aktuálním <xref:System.Windows.DataTemplate>, může být vhodnější <xref:System.Windows.Style> nastavit vlastnosti pomocí <xref:System.Windows.Controls.ListBoxItem> třídy, která je pro třídu (Pokud ovládací prvek, který vytváříte <xref:System.Windows.Controls.ListBox>, je a). Například pokud chcete <xref:System.Windows.Trigger> , aby <xref:System.Windows.UIElement.Opacity%2A> animace hodnoty položky, když ukazatel myši přejde na položku, definovali triggery ve <xref:System.Windows.Controls.ListBoxItem> stylu. Příklad naleznete v tématu [Úvod do stylu a šablonování Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Obecně Pamatujte na to, že <xref:System.Windows.DataTemplate> se použije na každý z generovaných <xref:System.Windows.Controls.ListBoxItem> (Další informace o tom, jak a kde se ve skutečnosti používají) najdete na <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> stránce. Máte <xref:System.Windows.DataTemplate> obavy jenom o prezentaci a vzhled datových objektů. Ve většině případů všechny ostatní aspekty prezentace, například to, co položka vypadá, když je vybraná nebo jak <xref:System.Windows.Controls.ListBox> rozloží položky, nepatří do definice. <xref:System.Windows.DataTemplate> Příklad naleznete v části [stylování a šablonování oddílu ItemsControl](#DataTemplating_ItemsControl) .  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Výběr datové šablony na základě vlastností datového objektu  
 V části [vlastnosti DataType](#Styling_DataType) jsme probrali, že můžete definovat různé datové šablony pro různé datové objekty. To je obzvláště užitečné v případě, že <xref:System.Windows.Data.CompositeCollection> máte různé typy nebo kolekce s položkami různých typů. V části [použití datových triggerů k použití hodnot vlastností](#DataTrigger_to_Apply_Property_Values) jsme ukázali, že pokud máte kolekci stejného typu datových objektů, můžete vytvořit <xref:System.Windows.DataTemplate> a potom použít triggery k uplatnění změn v závislosti na hodnotách vlastností každého datového objektu. Triggery ale umožňují aplikovat hodnoty vlastností nebo spustit animace, ale neposkytují flexibilitu pro rekonstrukci struktury datových objektů. Některé scénáře mohou vyžadovat, abyste vytvořili jiný <xref:System.Windows.DataTemplate> pro datové objekty, které jsou stejného typu, ale mají různé vlastnosti.  
  
 Například pokud `Task` `1`má objekt `Priority` hodnotu, může být vhodné dát zcela odlišný vzhled, který bude sloužit jako výstraha pro sebe. V takovém případě vytvoříte <xref:System.Windows.DataTemplate> pro zobrazení objektů s vysokou prioritou. `Task` Pojďme do části Resources přidat následující <xref:System.Windows.DataTemplate> :  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Všimněte si, že <xref:System.Windows.DataTemplate>tento příklad používá.<xref:System.Windows.FrameworkTemplate.Resources%2A> majetek. Prostředky definované v tomto oddílu jsou sdíleny prvky v rámci <xref:System.Windows.DataTemplate>.  
  
 Chcete-li zadat logiku pro <xref:System.Windows.DataTemplate> výběr, který má být `Priority` použit na základě hodnoty datového objektu, <xref:System.Windows.Controls.DataTemplateSelector> vytvořte <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> podtřídu a přepište metodu. V následujícím příkladu <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> poskytuje metoda logiku k vrácení příslušné šablony na základě hodnoty `Priority` vlastnosti. Šablona, která se má vrátit, se nachází v prostředcích <xref:System.Windows.Window> obklopujícího prvku.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Pak můžeme deklarovat `TaskListDataTemplateSelector` jako prostředek:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Chcete-li použít prostředek selektor šablony, přiřaďte jej <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> k vlastnosti. <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListBox> Volá<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metodu pro`TaskListDataTemplateSelector` každou položku v podkladové kolekci. Volání předá datový objekt jako parametr položky. K tomuto datovému objektu se pak použije metoda ,kterájevrácenámetodou.<xref:System.Windows.DataTemplate>  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Při selektoru šablony se <xref:System.Windows.Controls.ListBox> nyní zobrazí následující:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Tím se dokončí naše diskuze na tomto příkladu. Úplnou ukázku najdete v tématu [Úvod do data šablonování Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Stylování a šablonování ItemsControl  
 I když <xref:System.Windows.Controls.ItemsControl> není jediný typ ovládacího prvku, který lze <xref:System.Windows.DataTemplate> použít s, je velmi <xref:System.Windows.Controls.ItemsControl> běžný scénář pro svázání s kolekcí. V části [co patří do datové šablony](#what_belongs_in_datatemplate) jsme probrali, že definice vaší služby <xref:System.Windows.DataTemplate> by měla být dotčena pouze s prezentací dat. Aby bylo známo, že není vhodné použít <xref:System.Windows.DataTemplate> , je důležité pochopit různé vlastnosti stylu a šablony, které poskytuje. <xref:System.Windows.Controls.ItemsControl> Následující příklad je navržen pro ilustraci funkce každé z těchto vlastností. V tomto příkladu je svázán se stejnou `Tasks` kolekcí jako v předchozím příkladu. <xref:System.Windows.Controls.ItemsControl> Pro demonstrační účely jsou styly a šablony v tomto příkladu deklarovány jako vložené.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Následuje snímek obrazovky příkladu při jeho vykreslení:  
  
 ![ItemsControl – ukázkový snímek obrazovky](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Všimněte si, že místo použití <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>můžete <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>použít. Příklad najdete v předchozí části. Podobně namísto použití nástroje <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>máte možnost <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>použít.  
  
 Dvě další vlastnosti <xref:System.Windows.Controls.ItemsControl> související se styly, které nejsou zde zobrazeny, jsou <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> a <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Podpora hierarchických dat  
 Zatím jsme se podívali jenom na to, jak vytvořit a zobrazit jednu kolekci. Někdy máte kolekci, která obsahuje další kolekce. Třída je navržena pro použití s <xref:System.Windows.Controls.HeaderedItemsControl> typy k zobrazení těchto dat. <xref:System.Windows.HierarchicalDataTemplate> V následujícím příkladu `ListLeagueList` je `League` seznam objektů. Každý `League` objekt `Division` má a kolekci objektů. `Name` Každá `Division` z nich `Name` má a a kolekci `Team` objektů a každý `Team` objekt má `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 Tento příklad ukazuje, že s použitím <xref:System.Windows.HierarchicalDataTemplate>můžete snadno zobrazit seznam dat, která obsahují další seznamy. Níže je příklad snímku.  
  
 ![Ukázkový snímek obrazovky HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
- [Hledání elementů generovaných šablonou DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Přehled stylů záhlaví sloupců a šablon GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
