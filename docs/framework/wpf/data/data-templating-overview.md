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
ms.openlocfilehash: 377ee76e7e3537e9cae010189306611a503acbed
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740635"
---
# <a name="data-templating-overview"></a>Přehled datových šablon
Model dat šablonování WPF poskytuje skvělou flexibilitu pro definování prezentace vašich dat. Ovládací prvky WPF mají integrovanou funkcionalitu, která podporuje přizpůsobení prezentace dat. Toto téma ukazuje, jak definovat <xref:System.Windows.DataTemplate> a potom zavádí další funkce šablonování dat, jako je například výběr šablon založených na vlastní logice a podpora zobrazení hierarchických dat.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma se zaměřuje na funkce šablonování dat a není Úvod k konceptům datových vazeb. Informace o základních konceptech datových vazeb najdete v tématu [Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> se týká prezentace dat a je jednou z mnoha funkcí poskytovaných stylem WPF a modelem šablonování. Základní informace o stylu a modelu šablonování pro WPF, jako je například použití <xref:System.Windows.Style> k nastavení vlastností ovládacích prvků, naleznete v tématu [stylování a šablonování](../controls/styling-and-templating.md) .  
  
 Kromě toho je důležité porozumět `Resources`ům, které jsou v podstatě ty, které umožňují opakované použití objektů, jako jsou <xref:System.Windows.Style> a <xref:System.Windows.DataTemplate>. Další informace o prostředcích najdete v tématu věnovaném [prostředkům XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Základy šablonování dat  
  
 Abychom ukázali, proč je důležité <xref:System.Windows.DataTemplate>, Projděte si příklad vytváření datových vazeb. V tomto příkladu máme <xref:System.Windows.Controls.ListBox>, která je vázaná na seznam objektů `Task`. Každý objekt `Task` má `TaskName` (String), `Description` (String), `Priority` (int) a vlastnost typu `TaskType`, což je `Enum` s hodnotami `Home` a `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Bez šablony DataTemplate  
 Bez <xref:System.Windows.DataTemplate>by náš <xref:System.Windows.Controls.ListBox> v tuto chvíli vypadal takto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 To se děje proto, že bez jakýchkoli specifických instrukcí <xref:System.Windows.Controls.ListBox> ve výchozím nastavení při pokusu o zobrazení objektů v kolekci `ToString` volá. Proto pokud objekt `Task` přepisuje metodu `ToString`, pak <xref:System.Windows.Controls.ListBox> zobrazí řetězcovou reprezentaci každého zdrojového objektu v příslušné kolekci.  
  
 Například pokud třída `Task` přepisuje metodu `ToString` tímto způsobem, kde `name` je pole pro vlastnost `TaskName`:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 <xref:System.Windows.Controls.ListBox> vypadá takto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 To však omezuje a neflexibilní. Pokud vytváříte vazbu na data XML, nebudete moci přepsat `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definování jednoduché šablony DataTemplate  
 Řešením je definování <xref:System.Windows.DataTemplate>. Jedním ze způsobů, jak to provést, je nastavit vlastnost <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ListBox> na <xref:System.Windows.DataTemplate>. Co určíte ve vašem <xref:System.Windows.DataTemplate> se stávají vizuální strukturou datového objektu. Následující <xref:System.Windows.DataTemplate> jsou poměrně jednoduché. Poskytujeme pokyny, které se v <xref:System.Windows.Controls.StackPanel>zobrazí jako tři <xref:System.Windows.Controls.TextBlock> prvky. Každý prvek <xref:System.Windows.Controls.TextBlock> je vázán na vlastnost `Task` třídy.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Podkladová data pro příklady v tomto tématu jsou kolekce objektů CLR. Pokud vytváříte vazbu na data XML, základní koncepty jsou stejné, ale je to mírně syntaktický rozdíl. Například namísto `Path=TaskName`byste měli nastavit <xref:System.Windows.Data.Binding.XPath%2A> na `@TaskName` (Pokud `TaskName` je atribut vašeho uzlu XML).  
  
 Teď náš <xref:System.Windows.Controls.ListBox> vypadá takto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Vytvoření DataTemplate jako prostředku  
 Ve výše uvedeném příkladu jsme definovali <xref:System.Windows.DataTemplate> inline. Je běžnější ji definovat v části Resources (prostředky), takže se může jednat o opakovaně použitelný objekt, jak je uvedeno v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Nyní můžete použít `myTaskTemplate` jako prostředek, jako v následujícím příkladu:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Vzhledem k tomu, že `myTaskTemplate` je prostředek, můžete ho teď použít na jiné ovládací prvky, které mají vlastnost, která přebírá <xref:System.Windows.DataTemplate> typ. Jak je uvedeno výše, pro <xref:System.Windows.Controls.ItemsControl> objekty, jako je například <xref:System.Windows.Controls.ListBox>, se jedná o vlastnost <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. U <xref:System.Windows.Controls.ContentControl> objektů je to vlastnost <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Vlastnost DataType  
 Třída <xref:System.Windows.DataTemplate> má vlastnost <xref:System.Windows.DataTemplate.DataType%2A>, která je velmi podobná vlastnosti <xref:System.Windows.Style.TargetType%2A> třídy <xref:System.Windows.Style>. Proto místo určení `x:Key` pro <xref:System.Windows.DataTemplate> v předchozím příkladu můžete provést následující:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Tento <xref:System.Windows.DataTemplate> se automaticky použije pro všechny objekty `Task`. Všimněte si, že v tomto případě je `x:Key` nastavena implicitně. Proto pokud přiřadíte tuto <xref:System.Windows.DataTemplate> hodnotu `x:Key`, přepíšete implicitní `x:Key` a <xref:System.Windows.DataTemplate> nebudou automaticky použiti.  
  
 Pokud vytváříte vazbu <xref:System.Windows.Controls.ContentControl> ke kolekci objektů `Task`, <xref:System.Windows.Controls.ContentControl> nepoužije <xref:System.Windows.DataTemplate> automaticky výše. Důvodem je to, že vazba na <xref:System.Windows.Controls.ContentControl> potřebuje další informace, abyste rozlišili, zda chcete vytvořit vazbu na celou kolekci nebo jednotlivé objekty. Pokud <xref:System.Windows.Controls.ContentControl> sleduje výběr <xref:System.Windows.Controls.ItemsControl>ho typu, můžete nastavit vlastnost <xref:System.Windows.Data.Binding.Path%2A> vazby <xref:System.Windows.Controls.ContentControl> na "`/`" a indikovat, že máte zájem o aktuální položku. Příklad naleznete v tématu [vazba na kolekci a zobrazení informací na základě výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). V opačném případě je nutné zadat <xref:System.Windows.DataTemplate> explicitně nastavením vlastnosti <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.  
  
 Vlastnost <xref:System.Windows.DataTemplate.DataType%2A> je užitečná hlavně v případě, že máte <xref:System.Windows.Data.CompositeCollection> různých typů datových objektů. Příklad naleznete v tématu [implementace složené sadycollection](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Přidání dalších do šablony DataTemplate  
 V současné době se data zobrazují s potřebnými informacemi, ale pro zlepšení je k dispozici jen omezení místa. Pojďme vylepšit prezentaci přidáním <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>a některých <xref:System.Windows.Controls.TextBlock> prvků, které popisují zobrazená data.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Následující snímek obrazovky ukazuje <xref:System.Windows.Controls.ListBox> s tímto upraveným <xref:System.Windows.DataTemplate>:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Můžeme nastavit <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>, aby <xref:System.Windows.HorizontalAlignment.Stretch> na <xref:System.Windows.Controls.ListBox>, aby se zajistilo, že šířka položek zabere celé místo:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Když je vlastnost <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> nastavena na hodnotu <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> nyní vypadá takto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Použijte k použití hodnot vlastností datatriggery  
 Aktuální prezentace nám neřekne, jestli je `Task` domovskou úlohou nebo úlohou Office. Mějte na paměti, že objekt `Task` má vlastnost `TaskType` typu `TaskType`, což je výčet s hodnotami `Home` a `Work`.  
  
 V následujícím příkladu <xref:System.Windows.DataTrigger> nastaví <xref:System.Windows.Controls.Border.BorderBrush%2A> elementu s názvem `border` na `Yellow`, pokud je vlastnost `TaskType` `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Naše aplikace teď vypadá jako v následujícím příkladu. Domovské úkoly se zobrazí se žlutým ohraničením a úkoly Office se zobrazí s azurová ohraničením:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 V tomto příkladu používá <xref:System.Windows.DataTrigger> k nastavení hodnoty vlastnosti <xref:System.Windows.Setter>. Třídy triggeru mají také vlastnosti <xref:System.Windows.TriggerBase.EnterActions%2A> a <xref:System.Windows.TriggerBase.ExitActions%2A>, které umožňují spustit sadu akcí, například animace. Kromě toho existuje také třída <xref:System.Windows.MultiDataTrigger>, která umožňuje použít změny na základě více hodnot vlastností vázaných na data.  
  
 Alternativním způsobem, jak dosáhnout stejného účinku, je navázání vlastnosti <xref:System.Windows.Controls.Border.BorderBrush%2A> na vlastnost `TaskType` a použití převaděče hodnoty k vrácení barvy na základě hodnoty `TaskType`. Vytvoření výše uvedeného efektu pomocí převaděče je mírně efektivnější z pohledu výkonu. Vytváření vlastního převaděče navíc přináší větší flexibilitu, protože poskytujete vlastní logiku. A nakonec, kterou metodu zvolíte, závisí na vašem scénáři a vaší předvolbě. Informace o tom, jak napsat převaděč, najdete v tématu <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Co patří do šablony DataTemplate?  

V předchozím příkladu jsme vložili Trigger do <xref:System.Windows.DataTemplate> pomocí <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> majetek. <xref:System.Windows.Setter> Trigger nastaví hodnotu vlastnosti elementu (<xref:System.Windows.Controls.Border> element), která je v rámci <xref:System.Windows.DataTemplate>. Nicméně pokud vlastnosti, které jsou v `Setters`, nejsou vlastnosti prvků, které jsou v rámci aktuální <xref:System.Windows.DataTemplate>, může být vhodnější pro nastavení vlastností pomocí <xref:System.Windows.Style>, která je pro třídu <xref:System.Windows.Controls.ListBoxItem> (Pokud je ovládací prvek, který vytváříte, <xref:System.Windows.Controls.ListBox>). Například pokud chcete, aby <xref:System.Windows.Trigger> animována hodnotu <xref:System.Windows.UIElement.Opacity%2A> položky, když ukazatel myši přejde na položku, definujete triggery ve stylu <xref:System.Windows.Controls.ListBoxItem>. Příklad naleznete v tématu [Úvod do stylu a šablonování Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Obecně Pamatujte na to, že <xref:System.Windows.DataTemplate> se aplikuje na jednotlivé generované <xref:System.Windows.Controls.ListBoxItem> (Další informace o tom, jak a kde se ve skutečnosti používají, najdete na stránce <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.). Vaše <xref:System.Windows.DataTemplate> se týkají pouze prezentace a vzhledu datových objektů. Ve většině případů všechny ostatní aspekty prezentace, například to, co položka vypadá, když je vybraná nebo jak <xref:System.Windows.Controls.ListBox> rozloží položky, nepatří do definice <xref:System.Windows.DataTemplate>. Příklad naleznete v části [stylování a šablonování oddílu ItemsControl](#DataTemplating_ItemsControl) .  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Výběr datové šablony na základě vlastností datového objektu  
 V části [vlastnosti DataType](#Styling_DataType) jsme probrali, že můžete definovat různé datové šablony pro různé datové objekty. To je zvlášť užitečné, pokud máte <xref:System.Windows.Data.CompositeCollection> různých typů nebo kolekcí s položkami různých typů. V části [použití datových triggerů k použití hodnot vlastností](#DataTrigger_to_Apply_Property_Values) jsme ukázali, že pokud máte kolekci stejného typu datových objektů, můžete vytvořit <xref:System.Windows.DataTemplate> a potom pomocí aktivační procedury použít změny založené na hodnotách vlastností každého datového objektu. Triggery ale umožňují aplikovat hodnoty vlastností nebo spustit animace, ale neposkytují flexibilitu pro rekonstrukci struktury datových objektů. Některé scénáře mohou vyžadovat, abyste vytvořili jiný <xref:System.Windows.DataTemplate> pro datové objekty, které jsou stejného typu, ale mají různé vlastnosti.  
  
 Například pokud má objekt `Task` `Priority` hodnotu `1`, může být vhodné mu dát zcela jiný vzhled, který bude sloužit jako výstraha. V takovém případě vytvoříte <xref:System.Windows.DataTemplate> pro zobrazení objektů `Task` s vysokou prioritou. Do části Resources (prostředky) přidáme následující <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Všimněte si, že tento příklad používá <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> majetek. Prostředky definované v tomto oddílu jsou sdíleny prvky v rámci <xref:System.Windows.DataTemplate>.  
  
 Chcete-li zadat logiku pro výběr <xref:System.Windows.DataTemplate>, který se má použít, na základě `Priority` hodnoty datového objektu, vytvořte podtřídu <xref:System.Windows.Controls.DataTemplateSelector> a přepište metodu <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>. V následujícím příkladu poskytuje metoda <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> logiku, která vrátí příslušnou šablonu na základě hodnoty vlastnosti `Priority`. Šablona, která se má vrátit, se nachází v prostředcích obklopujícího <xref:System.Windows.Window> elementu.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Pak můžeme deklarovat `TaskListDataTemplateSelector` jako prostředek:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Chcete-li použít prostředek selektor šablony, přiřaďte jej k vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> volá metodu <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> `TaskListDataTemplateSelector` pro každou položku v podkladové kolekci. Volání předá datový objekt jako parametr položky. <xref:System.Windows.DataTemplate>, který je vrácen metodou, se následně aplikuje na tento datový objekt.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Na místě selektoru šablony se <xref:System.Windows.Controls.ListBox> nyní zobrazí takto:  
  
 ![Snímek obrazovky ukázkového data šablonování](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Tím se dokončí naše diskuze na tomto příkladu. Úplnou ukázku najdete v tématu [Úvod do data šablonování Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Stylování a šablonování ItemsControl  
 I když <xref:System.Windows.Controls.ItemsControl> není jediným typem ovládacího prvku, který lze použít <xref:System.Windows.DataTemplate> s, je to velmi běžný scénář pro svázání <xref:System.Windows.Controls.ItemsControl> s kolekcí. V části [co patří do datové šablony](#what_belongs_in_datatemplate) jsme probrali, že definice <xref:System.Windows.DataTemplate> by měla být dotčena pouze v prezentaci dat. Aby bylo známo, že není vhodné použít <xref:System.Windows.DataTemplate> je důležité pochopit různé vlastnosti stylu a šablony, které poskytuje <xref:System.Windows.Controls.ItemsControl>. Následující příklad je navržen pro ilustraci funkce každé z těchto vlastností. <xref:System.Windows.Controls.ItemsControl> v tomto příkladu se váže ke stejné kolekci `Tasks` jako v předchozím příkladu. Pro demonstrační účely jsou styly a šablony v tomto příkladu deklarovány jako vložené.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Následuje snímek obrazovky příkladu při jeho vykreslení:  
  
 ![ItemsControl – ukázkový snímek obrazovky](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Všimněte si, že místo použití <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>můžete použít <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Příklad najdete v předchozí části. Podobně namísto použití <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>máte možnost použít <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Dvě další vlastnosti <xref:System.Windows.Controls.ItemsControl>, které zde nejsou uvedeny, jsou <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> a <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Podpora hierarchických dat  
 Zatím jsme se podívali jenom na to, jak vytvořit a zobrazit jednu kolekci. Někdy máte kolekci, která obsahuje další kolekce. Třída <xref:System.Windows.HierarchicalDataTemplate> je navržena tak, aby se používala s typy <xref:System.Windows.Controls.HeaderedItemsControl> k zobrazení těchto dat. V následujícím příkladu je `ListLeagueList` seznam objektů `League`. Každý objekt `League` má `Name` a kolekci objektů `Division`. Každý `Division` má `Name` a kolekci objektů `Team` a každý objekt `Team` má `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 Tento příklad ukazuje, že při použití <xref:System.Windows.HierarchicalDataTemplate>můžete snadno zobrazit seznam dat, která obsahují další seznamy. Níže je příklad snímku.  
  
 ![Ukázkový snímek obrazovky HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Viz také:

- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
- [Hledání elementů generovaných šablonou DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled stylů záhlaví sloupců a šablon GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
