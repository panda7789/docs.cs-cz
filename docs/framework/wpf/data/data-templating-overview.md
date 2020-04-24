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
ms.openlocfilehash: b9e55eac1c72cd3deec21754373da4364a7cfed2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646464"
---
# <a name="data-templating-overview"></a>Přehled datových šablon
Model wpf data šablonování poskytuje velkou flexibilitu při definování prezentace dat. Ovládací prvky WPF mají vestavěné funkce pro podporu přizpůsobení prezentace dat. Toto téma nejprve ukazuje, jak definovat <xref:System.Windows.DataTemplate> a pak zavádí další funkce šablon dat, jako je například výběr šablon na základě vlastní logiky a podporu pro zobrazení hierarchických dat.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Požadavky
 Toto téma se zaměřuje na funkce šablonování dat a není zavedení koncepty datové vazby. Informace o základních konceptech datové vazby naleznete v tématu [Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).

 <xref:System.Windows.DataTemplate>je o prezentaci dat a je jednou z mnoha funkcí poskytovaných wpf styling a šablonování modelu. Úvod wpf styl a šablonování modelu, například jak použít <xref:System.Windows.Style> nastavení vlastností na ovládací prvky, naleznete v [tématu Styling a šablonování.](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

 Kromě toho je důležité `Resources`pochopit , které jsou v <xref:System.Windows.Style> <xref:System.Windows.DataTemplate> podstatě to, co umožňují objekty, jako je například opakovaně použitelné. Další informace o prostředcích naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Základy šablon dat

 Chcete-li <xref:System.Windows.DataTemplate> ukázat, proč je důležité, pojďme projít příklad vazby dat. V tomto příkladu <xref:System.Windows.Controls.ListBox> máme, který je `Task` vázán na seznam objektů. Každý `Task` objekt `TaskName` má (řetězec), `Description` (řetězec), `Priority` (int) a `TaskType`vlastnost typu `Enum` , `Home` což `Work`je s hodnotami a .

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>Bez šablony dat
 Bez <xref:System.Windows.DataTemplate>, <xref:System.Windows.Controls.ListBox> naše v současné době vypadá takto:

 ![Ukázkový snímek obrazovky s šablonami dat](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 Co se děje je, že bez <xref:System.Windows.Controls.ListBox> konkrétnípokyny, ve výchozím nastavení volání `ToString` při pokusu o zobrazení objektů v kolekci. Proto pokud `Task` objekt přepíše `ToString` metodu, <xref:System.Windows.Controls.ListBox> pak zobrazí řetězcovou reprezentaci každého zdrojového objektu v podkladové kolekci.

 Pokud například `Task` třída přepíše `ToString` metodu tímto způsobem, `name` `TaskName` kde je pole pro vlastnost:

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 Pak <xref:System.Windows.Controls.ListBox> vypadá takto:

 ![Ukázkový snímek obrazovky s šablonami dat](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 To je však omezující a nepružné. Také pokud jste vazba na data XML, nebude možné `ToString`přepsat .

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Definování jednoduché šablony dat
 Řešením je definovat <xref:System.Windows.DataTemplate>. Jedním ze způsobů, jak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> to udělat, je nastavit vlastnost na <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>. To, co <xref:System.Windows.DataTemplate> zadáte ve svém objektu, se stane vizuální strukturou datového objektu. Následující <xref:System.Windows.DataTemplate> je poměrně jednoduché. Dáváme pokyny, že každá <xref:System.Windows.Controls.TextBlock> položka se <xref:System.Windows.Controls.StackPanel>objeví jako tři prvky v rámci . Každý <xref:System.Windows.Controls.TextBlock> prvek je vázán na `Task` vlastnost třídy.

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Podkladová data pro příklady v tomto tématu je kolekce clr objektů. Pokud jste vazba na data XML, základní pojmy jsou stejné, ale je mírný syntaktický rozdíl. Například místo toho, abyste <xref:System.Windows.Data.Binding.XPath%2A> měli `@TaskName` , byste nastavili `TaskName` `Path=TaskName`(pokud je atributem uzlu XML).

 Nyní <xref:System.Windows.Controls.ListBox> náš vypadá takto:

 ![Ukázkový snímek obrazovky s šablonami dat](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>Vytvoření šablony data jako prostředku
 Ve výše uvedeném příkladu jsme definovali <xref:System.Windows.DataTemplate> vřadit. Je běžnější definovat v části zdroje tak, aby mohl být opakovaně použitelný objekt, jako v následujícím příkladu:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Nyní můžete `myTaskTemplate` použít jako prostředek, jako v následujícím příkladu:

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 Protože `myTaskTemplate` je prostředek, můžete nyní použít na jiné ovládací prvky, které mají vlastnost, která má <xref:System.Windows.DataTemplate> typ. Jak je znázorněno výše, <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox>pro objekty, jako je například , je <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost. Pro <xref:System.Windows.Controls.ContentControl> objekty je <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>Vlastnost DataType
 Třída <xref:System.Windows.DataTemplate> má <xref:System.Windows.DataTemplate.DataType%2A> vlastnost, která je <xref:System.Windows.Style.TargetType%2A> velmi podobná <xref:System.Windows.Style> vlastnost i třídy. Proto místo zadání `x:Key` for for <xref:System.Windows.DataTemplate> ve výše uvedeném příkladu, můžete provést následující:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 To <xref:System.Windows.DataTemplate> se automaticky `Task` použije na všechny objekty. Všimněte si, `x:Key` že v tomto případě je nastavenimplicitně. Proto pokud <xref:System.Windows.DataTemplate> přiřadíte `x:Key` tuto hodnotu, přepíšete implicitní `x:Key` a <xref:System.Windows.DataTemplate> nebude použito automaticky.

 Pokud <xref:System.Windows.Controls.ContentControl> jste vazba kolekce `Task` objektů, <xref:System.Windows.Controls.ContentControl> nepoužívá výše uvedené <xref:System.Windows.DataTemplate> automaticky. Důvodem je, že <xref:System.Windows.Controls.ContentControl> vazba na potřebuje další informace k rozlišení, zda chcete vytvořit vazbu na celou kolekci nebo jednotlivé objekty. Pokud <xref:System.Windows.Controls.ContentControl> sledujete výběr <xref:System.Windows.Controls.ItemsControl> typu, můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost <xref:System.Windows.Controls.ContentControl> vazby na`/`" " označující, že máte zájem o aktuální položku. Příklad najdete v tématu [Vazba na kolekci a zobrazit informace založené na výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). V opačném případě je <xref:System.Windows.DataTemplate> třeba zadat <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> explicitně nastavením vlastnosti.

 Vlastnost <xref:System.Windows.DataTemplate.DataType%2A> je zvláště užitečné, <xref:System.Windows.Data.CompositeCollection> pokud máte různé typy datových objektů. Příklad viz [Implementace CompositeCollection](how-to-implement-a-compositecollection.md).

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>Přidání další chození do šablony Dat
 V současné době se data zobrazují s potřebnými informacemi, ale určitě je zde prostor pro zlepšení. Vylepšeme prezentaci přidáním <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>a , <xref:System.Windows.Controls.TextBlock> a některé prvky, které popisují data, která se zobrazuje.

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Následující snímek <xref:System.Windows.Controls.ListBox> obrazovky ukazuje <xref:System.Windows.DataTemplate>s tímto upraveným :

 ![Ukázkový snímek obrazovky s šablonami dat](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 Můžeme nastavit <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> na <xref:System.Windows.Controls.ListBox> na ujistěte se, že šířka položek zabírá celý prostor:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 S <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastností <xref:System.Windows.HorizontalAlignment.Stretch>nastavenou <xref:System.Windows.Controls.ListBox> na , nyní vypadá takto:

 ![Ukázkový snímek obrazovky s šablonami dat](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Použití aktivačních událostí data k použití hodnot vlastností
 Aktuální prezentace nám neříká, `Task` zda je úkol domácnosti nebo úkol kanceláře. Nezapomeňte, `Task` že objekt `TaskType` má `TaskType`vlastnost typu , což je `Home` `Work`výčet s hodnotami a .

 V následujícím příkladu <xref:System.Windows.DataTrigger> <xref:System.Windows.Controls.Border.BorderBrush%2A> nastaví prvek `border` pojmenovaný, `Yellow` `TaskType` pokud `TaskType.Home`je vlastnost .

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Naše aplikace nyní vypadá takto. Domácí úkoly se zobrazí se žlutým ohraničením a kancelářské úkoly se zobrazí s aqua ohraničením:

 ![Ukázkový snímek obrazovky s šablonami dat](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 V tomto <xref:System.Windows.DataTrigger> příkladu <xref:System.Windows.Setter> používá a nastavit hodnotu vlastnosti. Třídy aktivačních <xref:System.Windows.TriggerBase.EnterActions%2A> událostí <xref:System.Windows.TriggerBase.ExitActions%2A> mají také vlastnosti a, které umožňují spustit sadu akcí, jako jsou animace. Kromě toho je také <xref:System.Windows.MultiDataTrigger> třída, která umožňuje použít změny na základě více hodnot vlastností vázaných na data.

 Alternativní způsob, jak dosáhnout stejného <xref:System.Windows.Controls.Border.BorderBrush%2A> efektu `TaskType` je vázat vlastnost na vlastnost a použít `TaskType` převaděč hodnoty vrátit barvu na základě hodnoty. Vytvoření výše uvedeného efektu pomocí převodníku je o něco efektivnější z hlediska výkonu. Navíc vytvoření vlastního převaděče poskytuje větší flexibilitu, protože dodáváte vlastní logiku. Nakonec, jakou techniku zvolíte, závisí na vašem scénáři a vašich preferencích. Informace o tom, jak napsat <xref:System.Windows.Data.IValueConverter>převaděč, naleznete v tématu .

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>Co patří do šablony data?

V předchozím příkladu jsme umístili <xref:System.Windows.DataTemplate> aktivační <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType> událost do using vlastnost. Aktivační <xref:System.Windows.Setter> událost nastaví hodnotu vlastnosti elementu <xref:System.Windows.Controls.Border> (prvku), který <xref:System.Windows.DataTemplate>je v rámci . Však pokud vlastnosti, které `Setters` se týkají nejsou vlastnosti <xref:System.Windows.DataTemplate>prvků, které jsou v rámci aktuální <xref:System.Windows.Style> , může <xref:System.Windows.Controls.ListBoxItem> být vhodnější nastavit vlastnosti <xref:System.Windows.Controls.ListBox>pomocí, která je pro třídu (pokud ovládací prvek, který je vazba je ). Pokud například chcete <xref:System.Windows.Trigger> animovat <xref:System.Windows.UIElement.Opacity%2A> hodnotu položky, když myš odkazuje na položku, definujete aktivační události v rámci <xref:System.Windows.Controls.ListBoxItem> stylu. Příklad naleznete v [úvodu k stylingu a šablonování ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

 Obecně mějte na paměti, že <xref:System.Windows.DataTemplate> se použije na <xref:System.Windows.Controls.ListBoxItem> každý z generovaných (další informace o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> tom, jak a kde je skutečně použita, naleznete na stránce.). Týká <xref:System.Windows.DataTemplate> se pouze prezentace a vzhledu datových objektů. Ve většině případů všechny ostatní aspekty prezentace, například to, jak položka <xref:System.Windows.Controls.ListBox> vypadá, když je vybrána nebo jak <xref:System.Windows.DataTemplate>položky rozloží, nepatří do definice . Příklad naleznete v části [Styling a Šablonování ovládacího prvku ItemsControl.](#DataTemplating_ItemsControl)

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Výběr šablony data na základě vlastností datového objektu
 V části [Vlastnost datatypu](#Styling_DataType) jsme diskutovali o tom, že můžete definovat různé šablony dat pro různé datové objekty. To je užitečné zejména <xref:System.Windows.Data.CompositeCollection> v případě, že máte různé typy nebo kolekce s položkami různých typů. V části [Použít datové aktivační události k použití hodnot vlastností](#DataTrigger_to_Apply_Property_Values) jsme ukázali, že pokud máte <xref:System.Windows.DataTemplate> kolekci stejného typu datových objektů, můžete vytvořit a potom pomocí aktivačních událostí použít změny na základě hodnot vlastností každého datového objektu. Aktivační události však umožňují použít hodnoty vlastností nebo spustit animace, ale neposkytují vám flexibilitu při rekonstrukci struktury datových objektů. Některé scénáře mohou vyžadovat vytvoření <xref:System.Windows.DataTemplate> jiného pro datové objekty, které jsou stejného typu, ale mají různé vlastnosti.

 Například pokud `Task` objekt má `Priority` hodnotu `1`, můžete chtít, aby zcela jiný vzhled sloužit jako výstraha pro sebe. V takovém případě vytvoříte <xref:System.Windows.DataTemplate> pro zobrazení objektů `Task` s vysokou prioritou. Do oddílu zdroje <xref:System.Windows.DataTemplate> přidáme následující:

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

Tento příklad používá vlastnost [DataTemplate.Resources.](xref:System.Windows.FrameworkTemplate.Resources%2A) Prostředky definované v této části jsou <xref:System.Windows.DataTemplate>sdíleny prvky v rámci rozhraní .

 Chcete-li zadat <xref:System.Windows.DataTemplate> logiku pro `Priority` výběr, který chcete použít na <xref:System.Windows.Controls.DataTemplateSelector> základě hodnoty <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> datového objektu, vytvořte podtřídu a přepište metodu. V následujícím příkladu <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metoda poskytuje logiku vrátit příslušnou šablonu `Priority` na základě hodnoty vlastnosti. Šablona k vrácení se nachází ve zdrojích <xref:System.Windows.Window> obalového prvku.

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 Pak můžeme deklarovat `TaskListDataTemplateSelector` jako zdroj:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Chcete-li použít prostředek pro výběr <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> šablony, <xref:System.Windows.Controls.ListBox>přiřaďte jej k vlastnosti . Volá <xref:System.Windows.Controls.ListBox> metodu <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> `TaskListDataTemplateSelector` pro každou z položek v podkladové kolekci. Volání předá datový objekt jako parametr položky. Který <xref:System.Windows.DataTemplate> je vrácen a metoda je pak použita na tento datový objekt.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 S voličem šablony na <xref:System.Windows.Controls.ListBox> místě, nyní se zobrazí takto:

 ![Ukázkový snímek obrazovky s šablonami dat](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Tím končí naše diskuse o tomto příkladu. Kompletní ukázku naleznete v [tématu Úvod do ukázky šablonování dat](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Stylování a šablonování ovládacího prvku ItemsControl
 I když <xref:System.Windows.Controls.ItemsControl> není jediný typ ovládacího prvku, který můžete použít <xref:System.Windows.DataTemplate> s, <xref:System.Windows.Controls.ItemsControl> je velmi běžný scénář svázat s kolekcí. V části [Co patří do DataTemplate](#what_belongs_in_datatemplate) jsme diskutovali, že definice vašeho <xref:System.Windows.DataTemplate> by se měla týkat pouze prezentace dat. Chcete-li vědět, kdy není vhodné <xref:System.Windows.DataTemplate> použít, je důležité pochopit různé vlastnosti <xref:System.Windows.Controls.ItemsControl>stylu a šablony poskytované rozhraním . Následující příklad je určen k ilustraci funkce každé z těchto vlastností. <xref:System.Windows.Controls.ItemsControl> V tomto příkladu je `Tasks` vázán na stejnou kolekci jako v předchozím příkladu. Pro demonstrační účely jsou všechny styly a šablony v tomto příkladu deklarovány jako vložky.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Následuje snímek obrazovky příkladu při vykreslení:

 ![Příklad obrazovky PoložkyControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 Všimněte si, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>že místo použití <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, můžete použít . Příklad naleznete v předchozí části. Podobně namísto použití <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, máte možnost použít <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.

 Dvě další vlastnosti související <xref:System.Windows.Controls.ItemsControl> se stylem, <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>které zde nejsou zobrazeny, jsou a .

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Podpora hierarchických dat
 Zatím jsme se jen podíval na to, jak se vázat a zobrazit jednu sbírku. Někdy máte kolekci, která obsahuje další kolekce. Třída <xref:System.Windows.HierarchicalDataTemplate> je určena pro <xref:System.Windows.Controls.HeaderedItemsControl> použití s typy pro zobrazení těchto dat. V následujícím příkladu `ListLeagueList` je `League` seznam objektů. Každý `League` objekt `Name` má a `Division` kolekci objektů. Každý `Division` má `Name` a kolekce `Team` objektů a `Team` každý `Name`objekt má .

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 Příklad ukazuje, že pomocí <xref:System.Windows.HierarchicalDataTemplate>aplikace můžete snadno zobrazit data seznamu, která obsahují další seznamy. Následuje snímek obrazovky příkladu.

 ![Ukázkový snímek ukázky šablony HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Viz také

- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
- [Najít prvky generované šablonou dat](how-to-find-datatemplate-generated-elements.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled stylů záhlaví sloupců a šablon GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
