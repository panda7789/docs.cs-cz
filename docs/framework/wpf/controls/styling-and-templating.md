---
title: Styly a šablony
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
ms.openlocfilehash: 9c2c38020bb57a008d0948a360a5b2cbe401089d
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457755"
---
# <a name="styling-and-templating"></a>Styly a šablony
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stylů a ukázka odkazují na sadu funkcí (styly, šablony, aktivační události a scénářů), které umožňují vývojářů a návrhářů, k vytvoření zajímavé vizuální efekty a k vytvoření konzistentního vzhledu jejich produktu. I když vývojáři a nebo Návrháři můžete přizpůsobit vzhled hojně na základě aplikace aplikace, je nutné povolit sdílení výskytu v rámci i mezi aplikacemi a údržby silné stylů a Ukázka modelu. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje tento model.  
  
 Jiné funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stylů modelu je oddělení prezentační a logiku. To znamená, že Designer můžete na vzhled aplikace fungují jenom pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve stejnou dobu, která vývojářům pracovat na logice programování s použitím jazyka C# nebo Visual Basic.  
  
 Tento přehled se zaměřuje na aspekty stylů a Ukázka aplikace a neobsahuje informace o všech koncepty vazby dat. Informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Kromě toho je důležité si uvědomit, zdroje, které jsou co Povolit styly a šablony znovu použije. Další informace o prostředcích najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).

<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Stylů a ukázkové ukázka  
 Příklady kódu použít v tomto přehledu jsou založeny na ukázku jednoduché fotografií vidět na následujícím obrázku:  
  
 ![Ve ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 Tato ukázka jednoduché fotografií používá stylů a ukázka k vytvoření vizuálně působivé možnosti uživatele. Ukázka má dva <xref:System.Windows.Controls.TextBlock> elementy a <xref:System.Windows.Controls.ListBox> ovládací prvek, který je vázaný na seznam bitové kopie. Kompletní příklad, najdete v části [Úvod do stylů a ukázka ukázková](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Základní informace o stylu  
 Si můžete představit <xref:System.Windows.Style> jako pohodlný způsob, jak použít sadu hodnot vlastností pro více než jeden element. Například vezměte v úvahu následující <xref:System.Windows.Controls.TextBlock> elementy a jejich výchozí vzhled:  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Snímek obrazovky stylů](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Můžete změnit vzhled výchozí nastavení vlastností, jako například <xref:System.Windows.Controls.Control.FontSize%2A> a <xref:System.Windows.Controls.Control.FontFamily%2A>, na každém <xref:System.Windows.Controls.TextBlock> element přímo. Ale pokud chcete vaše <xref:System.Windows.Controls.TextBlock> elementy sdílet některé vlastnosti můžete vytvořit <xref:System.Windows.Style> v `Resources` část vaší [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, jak je vidět tady:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Když nastavíte <xref:System.Windows.Style.TargetType%2A> vašeho stylu k <xref:System.Windows.Controls.TextBlock> typu, styl se použije pro všechny <xref:System.Windows.Controls.TextBlock> prvků v okně.  
  
 Nyní <xref:System.Windows.Controls.TextBlock> elementy měly vypadat následovně:  
  
 ![Snímek obrazovky stylů](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Rozšíření styly  
 Můžete potřebovat vaše dva <xref:System.Windows.Controls.TextBlock> elementy sdílet některé hodnoty vlastností, jako <xref:System.Windows.Controls.Control.FontFamily%2A> a na střed <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ale také chcete text "Moje obrázky" tak, aby měl některé další vlastnosti. Můžete to udělat tak, že vytvoříte nový styl, který je založen na první styl, jak je vidět tady:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Všimněte si, že je zadána styl předchozí `x:Key`. Použít styl, nastavíte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost na vaše <xref:System.Windows.Controls.TextBlock> k `x:Key` hodnoty, jak je vidět tady:  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 To <xref:System.Windows.Controls.TextBlock> styl má teď <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotu <xref:System.Windows.HorizontalAlignment.Center>, <xref:System.Windows.Controls.TextBlock.FontFamily%2A> hodnotu `Comic Sans MS`, <xref:System.Windows.Controls.TextBlock.FontSize%2A> hodnotu 26 a <xref:System.Windows.Controls.TextBlock.Foreground%2A> nastavena na hodnotu <xref:System.Windows.Media.LinearGradientBrush> v příkladu. Všimněte si, že přepíše <xref:System.Windows.Controls.Control.FontSize%2A> hodnota základního stylu. Pokud existuje více než jeden <xref:System.Windows.Setter> nastavení stejné vlastnosti <xref:System.Windows.Style>, <xref:System.Windows.Setter> tedy deklarované poslední přednost.  
  
 Následující znázorňuje, co <xref:System.Windows.Controls.TextBlock> elementy teď měl vypadat jako:  
  
 ![Ve objekty TextBlocks](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 To `TitleText` styl rozšiřuje na styl, který byl vytvořen pro <xref:System.Windows.Controls.TextBlock> typu. Můžete také rozšířit styl, který má `x:Key` pomocí `x:Key` hodnotu. Příklad, podívejte se na příklad stanovené <xref:System.Windows.Style.BasedOn%2A> vlastnost.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Vztah vlastnost TargetType a x: Key – atribut  
 Jak je znázorněno v prvním příkladu, nastavení <xref:System.Windows.Style.TargetType%2A> vlastnost `TextBlock` bez přiřazení styl `x:Key` způsobí, že styl použít na všechny <xref:System.Windows.Controls.TextBlock> elementy. V takovém případě `x:Key` implicitně nastavena na `{x:Type TextBlock}`. To znamená, že pokud explicitně nastavit `x:Key` hodnotu k ničemu jiné než `{x:Type TextBlock}`, <xref:System.Windows.Style> není použita pro všechny <xref:System.Windows.Controls.TextBlock> elementy automaticky. Místo toho musíte použít styl (pomocí `x:Key` hodnotu) k <xref:System.Windows.Controls.TextBlock> elementy explicitně. Pokud je vaše styl v oddílu prostředků a není nastaveno <xref:System.Windows.Style.TargetType%2A> musíte zadat vlastnosti na, jakým způsobem a potom `x:Key`.  
  
 Kromě výchozí hodnota pro `x:Key`, <xref:System.Windows.Style.TargetType%2A> vlastnost určuje typ, na kterou se vztahují Metoda setter vlastnosti. Pokud nezadáte <xref:System.Windows.Style.TargetType%2A>, musíte v vlastnosti v vaše <xref:System.Windows.Setter> objektů s názvem třídy pomocí syntaxe `Property="ClassName.Property"`. Například místo nastavení `Property="FontSize"`, je nutné nastavit <xref:System.Windows.Setter.Property%2A> k `"TextBlock.FontSize"` nebo `"Control.FontSize"`.  
  
 Všimněte si také tolika [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky se skládají z kombinace jiné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky. Pokud vytvoříte styl, který se vztahuje na všechny ovládací prvky typu, můžete získat neočekávané výsledky. Například, pokud vytvoříte styl s cílem <xref:System.Windows.Controls.TextBlock> zadejte <xref:System.Windows.Window>, je použit pro všechny <xref:System.Windows.Controls.TextBlock> ovládací prvky v okně i v případě <xref:System.Windows.Controls.TextBlock> , jako je součástí jiného ovládacího prvku <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Styly a prostředky  
 Styl můžete použít u libovolného elementu, který je odvozen od <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Nejběžnější způsob deklarace styl je jako prostředek v `Resources` tématu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, jak je znázorněno v předchozích příkladech. Protože styly jsou prostředky, se orientují stejné oboru pravidla, která se vztahují na všechny prostředky; kde deklarovat styl ovlivňuje, který lze použít styl. Například, pokud je deklarovat styl v kořenovém elementu definice aplikace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru styl lze použít kdekoli v aplikaci. Pokud chcete vytvořit navigační aplikace a deklarovat styl v jedné z aplikace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, styl lze použít pouze v tom, že [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Další informace o rozsahu pravidla pro prostředky, najdete v části [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Kromě toho můžete najít další informace o styly a prostředky v [sdílené prostředky a motivů](#styling_themes) dál v tomto přehledu.  
  
### <a name="setting-styles-programmatically"></a>Nastavení stylů prostřednictvím kódu programu  
 Prostřednictvím kódu programu přiřadit styl s názvem elementu, získá styl z kolekce prostředků a přiřadit k elementu <xref:System.Windows.FrameworkElement.Style%2A> vlastnost. Všimněte si, že položky v kolekci prostředků typu <xref:System.Object>. Proto musíte vysílat načtené styl, který se <xref:System.Windows.Style> před přiřazením jeho <xref:System.Windows.FrameworkElement.Style%2A> vlastnost. Chcete-li například nastavit definovaný `TitleText` styl na <xref:System.Windows.Controls.TextBlock> s názvem `textblock1`, postupujte takto:  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Všimněte si, že po použití styl, je zapečetěná a nelze je změnit. Pokud chcete dynamicky měnit styl, který již byl použit, musíte vytvořit nový styl, který chcete nahradit stávající. Další informace najdete v tématu <xref:System.Windows.Style.IsSealed%2A> vlastnost.  
  
 Můžete vytvořit objekt, který vybere styl, který chcete použít na základě vlastní logiky. Příklad, podívejte se na příklad stanovené <xref:System.Windows.Controls.StyleSelector> třídy.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Vazby, dynamické prostředky a obslužné rutiny událostí  
 Všimněte si, že můžete použít `Setter.Value` vlastnosti k určení [vazby – rozšíření značek](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) nebo [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Další informace najdete v tématu příklady stanovené <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> vlastnost.  
  
 Pokud tento přehled popisuje pouze použití setter nastavit hodnotu vlastnosti. Můžete také zadat obslužné rutiny událostí ve stylu. Další informace naleznete v tématu <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Šablony dat  
 V této ukázkové aplikaci je <xref:System.Windows.Controls.ListBox> ovládací prvek, který je vázaný na seznam fotografie:  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 To <xref:System.Windows.Controls.ListBox> aktuálně vypadá podobně jako následující:  
  
 ![ListBox – před použitím šablony](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 Většina ovládacích prvků má nějaký typ obsahu a obsahu často pochází z data, která jsou vytvoření vazby na. Data v této ukázce je seznam fotografie. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], můžete použít <xref:System.Windows.DataTemplate> k definování vizuální znázornění dat. V podstatě, co vložíte do <xref:System.Windows.DataTemplate> určuje vzhled data v vykreslené aplikaci.  
  
 V našem ukázkovou aplikaci, každý vlastní `Photo` objekt má `Source` vlastnost typu řetězec, který určuje cestu k souboru bitové kopie. V současné době objekty fotografie se zobrazí jako cesty k souborům.  
  
 Fotkám, které se objeví jako obrázky, vytvoříte <xref:System.Windows.DataTemplate> jako prostředek:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Všimněte si, že <xref:System.Windows.DataTemplate.DataType%2A> je velmi podobný jako vlastnost <xref:System.Windows.Style.TargetType%2A> vlastnost <xref:System.Windows.Style>. Pokud vaše <xref:System.Windows.DataTemplate> je v části prostředky, když zadáte <xref:System.Windows.DataTemplate.DataType%2A> vlastnost typu a přiřaďte ho není `x:Key`, <xref:System.Windows.DataTemplate> se použije vždy, když se zobrazí typu. Vždy máte možnost přiřadit <xref:System.Windows.DataTemplate> s `x:Key` a nastavte jej jako `StaticResource` pro vlastnosti, které provést <xref:System.Windows.DataTemplate> typy, jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost nebo <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.  
  
 V podstatě <xref:System.Windows.DataTemplate> v předchozím příkladu definuje, kdykoli dojde `Photo` objektu, mělo by se zobrazit jako <xref:System.Windows.Controls.Image> v rámci <xref:System.Windows.Controls.Border>. Pomocí této <xref:System.Windows.DataTemplate>, aplikace nyní vypadat třeba takto:  
  
 ![Obrázek fotografie](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Datový model ukázka poskytuje další funkce. Například, pokud jsou zobrazení kolekce dat, který obsahuje jiné kolekce pomocí <xref:System.Windows.Controls.HeaderedItemsControl> zadejte například <xref:System.Windows.Controls.Menu> nebo <xref:System.Windows.Controls.TreeView>, je <xref:System.Windows.HierarchicalDataTemplate>. Další data ukázka funkcí je <xref:System.Windows.Controls.DataTemplateSelector>, který umožňuje výběr <xref:System.Windows.DataTemplate> používat na základě vlastní logiky. Další informace najdete v tématu [přehled Ukázka dat](../../../../docs/framework/wpf/data/data-templating-overview.md), který poskytuje podrobné informace o různých datových ukázka funkcí.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Šablon ovládacích prvků  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku definuje vzhled ovládacího prvku. Můžete změnit strukturu a vzhledu ovládacího prvku tak, že definujete novou <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek. V mnoha případech to vám dává dostatek flexibilitu tak, aby nemusíte psát vlastní ovládací prvky. Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Aktivační procedury  
 Aktivační událost nastaví vlastnosti nebo spuštění akce, jako je animace, když se změní hodnota vlastnosti, nebo když se vyvolá událost. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, a <xref:System.Windows.DataTemplate> všechny `Triggers` vlastnost, která může obsahovat sadu aktivační události. Existují různé druhy aktivační události.  
  
### <a name="property-triggers"></a>Vlastnost aktivační události  
 A <xref:System.Windows.Trigger> vlastnost aktivační událost je volána, nastaví vlastnost hodnoty nebo spuštění akce na základě hodnoty vlastnosti.  
  
 Abychom ukázali, jak používat vlastnost aktivační události, můžete provést každý <xref:System.Windows.Controls.ListBoxItem> částečně transparentní, pokud je vybraná. Následující styl nastaví <xref:System.Windows.UIElement.Opacity%2A> hodnotu <xref:System.Windows.Controls.ListBoxItem> k `0.5`. Když <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> vlastnost je `true`, ale <xref:System.Windows.UIElement.Opacity%2A> je nastaven na `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 Tento příklad používá <xref:System.Windows.Trigger> nastavit hodnotu vlastnosti, ale Všimněte si, že <xref:System.Windows.Trigger> třída má také <xref:System.Windows.TriggerBase.EnterActions%2A> a <xref:System.Windows.TriggerBase.ExitActions%2A> vlastnosti, které umožňují aktivační událost k provádění akcí.  
  
 Všimněte si, že <xref:System.Windows.FrameworkElement.MaxHeight%2A> vlastnost <xref:System.Windows.Controls.ListBoxItem> je nastaven na `75`. Na následujícím obrázku je třetí položku vybrané položky:  
  
 ![Ve ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers a scénářů  
 Jiný typ aktivační události je <xref:System.Windows.EventTrigger>, který spustí sadu akcí v závislosti na výskyt události. Například následující <xref:System.Windows.EventTrigger> objekty určit, že když ukazatel myši přejde <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> animuje vlastnost na hodnotu `90` přes `0.2` druhé doby. Při přesunu myši směrem od položky, vlastnost vrátí na původní hodnotu v určitém období `1` druhý. Všimněte si, jak není nutné zadávat <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnota <xref:System.Windows.ContentElement.MouseLeave> animace. Je to proto, že animaci je možné ke sledování původní hodnotu.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Další informace najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Na následujícím obrázku myš ukazovat na třetí položku:  
  
 ![Snímek obrazovky stylů](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers a MultiDataTriggers  
 Kromě <xref:System.Windows.Trigger> a <xref:System.Windows.EventTrigger>, se objeví jiné typy služby aktivačních událostí. <xref:System.Windows.MultiTrigger> Umožňuje nastavit hodnoty vlastností na základě více podmínek. Používáte <xref:System.Windows.DataTrigger> a <xref:System.Windows.MultiDataTrigger> Pokud je vlastnost vaše podmínky vázané na data.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Sdílené prostředky a motivů  
 Typická aplikace Windows Presentation Foundation (WPF) může mít různé uživatelské rozhraní (UI) prostředky, které se použijí v celé aplikaci. Tuto sadu prostředků souhrnně, lze považovat motivu pro aplikaci. Windows Presentation Foundation (WPF) poskytuje podporu pro balení uživatelské rozhraní (UI) prostředky jako motiv pomocí slovník prostředků, který je jako zapouzdřený <xref:System.Windows.ResourceDictionary> třídy.  
  
 Windows Presentation Foundation (WPF) motivy jsou definované za použití ukázka mechanismus, který zveřejňuje Windows Presentation Foundation (WPF) a stylů pro přizpůsobení vizuály žádná položka.  
  
 Windows Presentation Foundation (WPF) motiv prostředky jsou uloženy ve slovnících vložený prostředek. Tyto slovnících prostředků musí být vložen v podepsané sestavení a můžete buď vložit do stejného sestavení jako samotný kód nebo v souběžně sdílená sestavení. V případě knihovně PresentationFramework.dll, sestavení, které obsahuje ovládací prvky Windows Presentation Foundation (WPF), motiv prostředky jsou v řadě souběžně sdílená sestavení.  
  
 Motiv se změní poslední místem při hledání styl elementu. Obvykle hledání budou začněte tím, že proti nahoru k elementu vyhledávání pro odpovídající prostředek, potom vyhledejte v kolekci prostředků aplikace a nakonec dotaz na systém. To poskytuje vývojářům aplikací možnost změnit definici stylu pro libovolný objekt na úrovni stromu nebo aplikace před dosažením motiv.  
  
 Můžete definovat slovnících prostředků jako jednotlivé soubory, které vám umožní použít motiv napříč různými aplikacemi. Můžete také vytvořit swappable motivy definováním více slovnících prostředků, které poskytují stejné typy prostředků, ale s různými hodnotami. Opětovná definice tyto styly nebo jiným prostředkům na úrovni aplikace se o doporučený postup pro změny vzhledu aplikace.  
  
 Chcete-li sdílet sadu prostředků, včetně styly a šablony a ve všech aplikacích, můžete vytvořit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru a definovat <xref:System.Windows.ResourceDictionary>. Například, podívejte se na následující obrázek, který ukazuje součástí [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating):

![Řízení šablony příklady](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Pokud se podíváte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory ve vzorku, si všimnete, že všechny soubory obsahují následující:  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 Je sdílení `shared.xaml`, která definuje <xref:System.Windows.ResourceDictionary> obsahující sadu styl a štětce prostředky, které umožňují ovládací prvky ve vzorku, který se podíváme se konzistentní.  
  
 Další informace najdete v tématu [sloučit slovnících prostředků](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Pokud vytváříte motiv můžete vlastní ovládací prvek, najdete v části Externí ovládací prvek knihovna [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Postupy: Vyhledávání elementů generovaných objektem ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [Hledání elementů generovaných šablonou DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
