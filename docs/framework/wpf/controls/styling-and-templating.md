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
ms.openlocfilehash: 3fae4993a13b02ad998668f644a80ba7c07196fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132289"
---
# <a name="styling-and-templating"></a>Styly a šablony
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] styly a šablony najdete suite funkcí (styly, šablony, aktivační události a scénáře), které umožňují vývojářům a návrhářům vytvářet vizuálně působivé efekty a vytvořte konzistentní vzhled pro svůj produkt. I když vývojáři a návrháři můžete přizpůsobit vzhled náročným na základě aplikace aplikace, silné styly a šablony modelu je potřeba povolit sdílení výskytu v rámci a mezi aplikacemi a údržby. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Tento model poskytuje.  
  
 Další funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používání stylů pro model je oddělení prezentaci a logiku. To znamená, že návrháře může pracovat na vzhledu aplikace s použitím pouze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve stejnou dobu, která vývojářům pracovat na programovou logiku pomocí C# nebo Visual Basic.  
  
 Tento přehled se zaměřuje na styly a šablony aspektů aplikace a všechny koncepty vazeb dat se nezabývá. Informace o datové vazbě naleznete v tématu [Data Binding Overview](../data/data-binding-overview.md).  
  
 Kromě toho je důležité pochopit zdroje, které jsou co Povolit – styly a šablony, které znovu použít. Další informace o prostředcích najdete v tématu [prostředky XAML](../advanced/xaml-resources.md).

<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Styly a ukázky šablon  
 Kód příkladů použitých v tomto přehledu jsou na základě jednoduchého fotografii ukázky je znázorněno na následujícím obrázku:  
  
 ![Styl ListView](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 Tato ukázka jednoduché fotografii používá styly a šablony k vytvoření vizuálně působivé činnost koncového uživatele. Ukázka má dva <xref:System.Windows.Controls.TextBlock> elementy a <xref:System.Windows.Controls.ListBox> ovládací prvek, který je vázán na seznam imagí. Úplnou ukázku najdete v tématu [Úvod do používání stylů a šablon ukázková](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Základní informace o stylu  
 Můžete si představit <xref:System.Windows.Style> jako pohodlný způsob, jak použít sadu hodnot vlastností pro více než jeden element. Představte si třeba následující <xref:System.Windows.Controls.TextBlock> prvky a jejich výchozí vzhled:  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Snímek obrazovky ukázkový používání stylů pro](./media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Výchozí vzhled můžete změnit nastavením vlastnosti, jako například <xref:System.Windows.Controls.Control.FontSize%2A> a <xref:System.Windows.Controls.Control.FontFamily%2A>, na každém <xref:System.Windows.Controls.TextBlock> element přímo. Ale pokud chcete, aby vaše <xref:System.Windows.Controls.TextBlock> prvků, které se sdílejí některé vlastnosti, můžete vytvořit <xref:System.Windows.Style> v `Resources` část vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, jak je znázorněno zde:  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Při nastavení <xref:System.Windows.Style.TargetType%2A> z styl <xref:System.Windows.Controls.TextBlock> typ styl použitý pro všechny <xref:System.Windows.Controls.TextBlock> prvků v okně.  
  
 Nyní <xref:System.Windows.Controls.TextBlock> prvky vypadat následovně:  
  
 ![Snímek obrazovky ukázkový používání stylů pro](./media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Rozšíření styly  
 Můžete chtít každé z vašich dvou <xref:System.Windows.Controls.TextBlock> prvků, které se sdílejí některé hodnoty vlastností, jako <xref:System.Windows.Controls.Control.FontFamily%2A> a zaměřena na <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ale také chcete text "Obrázky" mít některé další vlastnosti. Můžete to udělat tak, že vytvoříte nový styl, který je založen na první styl, jak je znázorněno zde:  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Všimněte si, že je uveden v předchozím stylu `x:Key`. Použít styl, nastavíte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost na vaše <xref:System.Windows.Controls.TextBlock> k `x:Key` hodnoty, jak je znázorněno zde:  
  
 [!code-xaml[StylingIntroSnippet#UIText](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 To <xref:System.Windows.Controls.TextBlock> stylu má teď <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotu <xref:System.Windows.HorizontalAlignment.Center>, <xref:System.Windows.Controls.TextBlock.FontFamily%2A> hodnotu `Comic Sans MS`, <xref:System.Windows.Controls.TextBlock.FontSize%2A> hodnotu 26 a <xref:System.Windows.Controls.TextBlock.Foreground%2A> nastavena na hodnotu <xref:System.Windows.Media.LinearGradientBrush> ukazuje příklad. Všimněte si, že přepíše <xref:System.Windows.Controls.Control.FontSize%2A> hodnotu základní stylu. Pokud existuje více než jeden <xref:System.Windows.Setter> nastavení stejné vlastnosti v <xref:System.Windows.Style>, <xref:System.Windows.Setter> , který je deklarovaný poslední přednost.  
  
 Následující příklad zobrazuje co <xref:System.Windows.Controls.TextBlock> elementy teď měla vypadat jako:  
  
 ![Styl objekty TextBlock se](./media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 To `TitleText` rozšiřuje styl, který se vytvořil pro styl <xref:System.Windows.Controls.TextBlock> typu. Můžete také rozšířit styl, který má `x:Key` pomocí `x:Key` hodnotu. Příklad, podívejte se na příklad stanovené <xref:System.Windows.Style.BasedOn%2A> vlastnost.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Vztah vlastnost TargetType a atribut x: Key  
 Jak je znázorněno v prvním příkladu, nastavení <xref:System.Windows.Style.TargetType%2A> vlastnost `TextBlock` bez přiřazení styl `x:Key` způsobí, že styl, který má být použitý u všech <xref:System.Windows.Controls.TextBlock> elementy. V takovém případě `x:Key` implicitně nastavena na `{x:Type TextBlock}`. To znamená, že pokud explicitně nastavit `x:Key` hodnota, která se nic jiného než `{x:Type TextBlock}`, <xref:System.Windows.Style> není použitý u všech <xref:System.Windows.Controls.TextBlock> prvky automaticky. Místo toho musíte použít styl (s použitím `x:Key` hodnotu) k <xref:System.Windows.Controls.TextBlock> elementů explicitně. Pokud je vašemu stylu v části prostředky a nenastavíte <xref:System.Windows.Style.TargetType%2A> musí poskytnout vlastnost vašemu stylu, budete `x:Key`.  
  
 Kromě toho, že výchozí hodnota `x:Key`, <xref:System.Windows.Style.TargetType%2A> vlastnost určuje typ, ke které se vztahují požadované vlastnosti setter. Pokud nezadáte <xref:System.Windows.Style.TargetType%2A>, musí kvalifikovat vlastnosti ve vaší <xref:System.Windows.Setter> objektů s názvem třídy pomocí syntaxe `Property="ClassName.Property"`. Například místo nastavení `Property="FontSize"`, je nutné nastavit <xref:System.Windows.Setter.Property%2A> k `"TextBlock.FontSize"` nebo `"Control.FontSize"`.  
  
 Všimněte si také tolik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků se skládá z kombinace dalších [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků. Pokud vytvoříte styl, který se vztahuje na všechny ovládací prvky typu, může se zobrazit neočekávané výsledky. Například, pokud vytvoříte styl, který cílí <xref:System.Windows.Controls.TextBlock> zadejte <xref:System.Windows.Window>, tento styl aplikován na všechny <xref:System.Windows.Controls.TextBlock> ovládacích prvků v okně i v případě <xref:System.Windows.Controls.TextBlock> , jako je součástí jiného ovládacího prvku, <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Styly a prostředky  
 Můžete použít styl na libovolný element, který je odvozen od <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Nejběžnější způsob, jak deklarovat styl je jako prostředek v `Resources` tématu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, jak je znázorněno v předchozích příkladech. Protože styly jsou prostředky, dodržují stejná pravidla oboru, které se vztahují na všechny prostředky; Pokud deklarujete styl ovlivňuje, kde lze použít styl. Například, pokud deklarujete styl v kořenovém prvku definice aplikace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, styl lze je použít kdekoli v aplikaci. Pokud chcete vytvořit navigační aplikace a styl v jednom z vaší aplikace deklarovat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, styl, který lze použít pouze v tomto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Další informace o rozsahu pravidla pro prostředky, najdete v části [prostředky XAML](../advanced/xaml-resources.md).  
  
 Kromě toho můžete najít další informace o stylech a prostředky v [sdílené prostředky a motivy](#styling_themes) dále v tomto přehledu.  
  
### <a name="setting-styles-programmatically"></a>Nastavení stylů prostřednictvím kódu programu  
 Přiřadit pojmenované stylu elementu prostřednictvím kódu programu, získá styl z kolekce zdroje a přiřadit k elementu <xref:System.Windows.FrameworkElement.Style%2A> vlastnost. Všimněte si, že jsou položky v kolekci prostředků typu <xref:System.Object>. Proto musíte přetypovat načtený styl <xref:System.Windows.Style> před ji přiřadíte <xref:System.Windows.FrameworkElement.Style%2A> vlastnost. Například nastavte definovanou `TitleText` stylu na <xref:System.Windows.Controls.TextBlock> s názvem `textblock1`, postupujte takto:  
  
 [!code-csharp[StylingIntroSample_snippet#Code](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Všimněte si, že po použití stylu je zapečetěná a nedá se změnit. Pokud chcete dynamicky měnit styl, který se už používá, musíte vytvořit nový styl, který chcete nahradit stávající. Další informace najdete v tématu <xref:System.Windows.Style.IsSealed%2A> vlastnost.  
  
 Můžete vytvořit objekt, který vybere styl, který chcete použít na základě vlastní logiku. Příklad, podívejte se na příklad stanovené <xref:System.Windows.Controls.StyleSelector> třídy.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Vazby dynamické prostředky a obslužné rutiny událostí  
 Všimněte si, že můžete použít `Setter.Value` vlastnosti k určení [vazby – rozšíření značek](../advanced/binding-markup-extension.md) nebo [– rozšíření značek DynamicResource](../advanced/dynamicresource-markup-extension.md). Další informace, podívejte se na příklady stanovené <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> vlastnost.  
  
 Tento přehled popisuje zatím pouze pomocí metody setter a nastavit hodnotu vlastnosti. Můžete také zadat obslužných rutin událostí ve stylu. Další informace naleznete v tématu <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Šablony dat  
 V této ukázkové aplikaci je <xref:System.Windows.Controls.ListBox> ovládací prvek, který je vázán na seznam fotografie:  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 To <xref:System.Windows.Controls.ListBox> aktuálně vypadá následovně:  
  
 ![ListBox – před použitím šablony](./media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 Většina ovládací prvky mají některé typu obsahu a obsahu často pochází z data, která jsou vytvoření vazby na. Data v této ukázce je seznam fotografie. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je použít <xref:System.Windows.DataTemplate> k definování vizuální znázornění dat. V podstatě, co vložíte do <xref:System.Windows.DataTemplate> určuje vzhled data ve vygenerované aplikaci.  
  
 V naší ukázkové aplikaci, všechny vlastní `Photo` má objekt `Source` vlastnost typu řetězec, který určuje cestu k souboru obrázku. V současné době fotografii objekty jeví jako cesty k souborům.  
  
 Pro fotografie se zobrazují jako obrázky, vytvořte <xref:System.Windows.DataTemplate> jako prostředek:  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Všimněte si, že <xref:System.Windows.DataTemplate.DataType%2A> vlastnost je velmi podobný <xref:System.Windows.Style.TargetType%2A> vlastnost <xref:System.Windows.Style>. Pokud vaše <xref:System.Windows.DataTemplate> je v části prostředky, když zadáte <xref:System.Windows.DataTemplate.DataType%2A> na typ a nelze ji přiřadit `x:Key`, <xref:System.Windows.DataTemplate> se použije vždy, když se zobrazí tohoto typu. Vždy máte možnost k přidělení <xref:System.Windows.DataTemplate> s `x:Key` a nastavte ji jako `StaticResource` pro vlastnosti, které trvat <xref:System.Windows.DataTemplate> typy, jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost nebo <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost.  
  
 V podstatě <xref:System.Windows.DataTemplate> ve výše uvedeném příkladu definuje, která vždycky, když je `Photo` objektu, měl by se zobrazit jako <xref:System.Windows.Controls.Image> v rámci <xref:System.Windows.Controls.Border>. S tímto <xref:System.Windows.DataTemplate>, naši aplikaci nyní vypadá takto:  
  
 ![Fotografii](./media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Datový model šablonování poskytuje další funkce. Například, pokud zobrazujete shromažďování dat, který obsahuje jiné kolekce pomocí <xref:System.Windows.Controls.HeaderedItemsControl> jako <xref:System.Windows.Controls.Menu> nebo <xref:System.Windows.Controls.TreeView>, je <xref:System.Windows.HierarchicalDataTemplate>. Další funkcí šablon dat je <xref:System.Windows.Controls.DataTemplateSelector>, který umožňuje zvolit <xref:System.Windows.DataTemplate> použít podle vlastní logiku. Další informace najdete v tématu [přehled datových šablon](../data/data-templating-overview.md), která poskytuje podrobné informace o různých datových šablon funkce.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Šablony ovládacích prvků  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku definuje vzhled ovládacího prvku. Můžete změnit strukturu a vzhled ovládacího prvku tak, že definujete nový <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek. V mnoha případech získáte dostatečně flexibilní, takže není potřeba psát vlastní ovládací prvky. Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Aktivační procedury  
 Aktivační událost nastaví vlastnosti nebo spuštění akcí, jako je animace, při změně hodnoty vlastnosti nebo když je vyvolána událost. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, a <xref:System.Windows.DataTemplate> mají `Triggers` vlastnost, která může obsahovat sadu aktivační události. Existují různé druhy aktivačních událostí.  
  
### <a name="property-triggers"></a>Aktivační procedury vlastností  
 A <xref:System.Windows.Trigger> aktivační procedura vlastností je volána, nastaví vlastnost hodnoty nebo spuštění akce na základě hodnoty vlastnosti.  
  
 Ukazují použití aktivační procedury vlastností, můžete nastavit každou <xref:System.Windows.Controls.ListBoxItem> částečně transparentní, pokud je zaškrtnuto. Následující styl sad <xref:System.Windows.UIElement.Opacity%2A> hodnotu <xref:System.Windows.Controls.ListBoxItem> k `0.5`. Když <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> vlastnost `true`, ale <xref:System.Windows.UIElement.Opacity%2A> je nastavena na `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 Tento příklad používá <xref:System.Windows.Trigger> nastavíte hodnotu vlastnosti, ale Všimněte si, že <xref:System.Windows.Trigger> třída má také <xref:System.Windows.TriggerBase.EnterActions%2A> a <xref:System.Windows.TriggerBase.ExitActions%2A> vlastnosti, které umožňují provádět akce aktivační události.  
  
 Všimněte si, že <xref:System.Windows.FrameworkElement.MaxHeight%2A> vlastnost <xref:System.Windows.Controls.ListBoxItem> je nastavena na `75`. Na následujícím obrázku je třetí položka vybraná položka:  
  
 ![Styl ListView](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers a scénářů  
 Je jiný typ aktivační události <xref:System.Windows.EventTrigger>, která spustí sadu akcí, které jsou založené na výskyt události. Například následující <xref:System.Windows.EventTrigger> objektům určíte, že pokud kurzor myši vstoupí <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> animuje vlastnost na hodnotu `90` přes `0.2` druhou dobu. Pokud ukazatel myši přesune od položky, vlastnost vrací na původní hodnotu po dobu `1` druhý. Všimněte si, jak to není potřeba zadávat <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hodnota <xref:System.Windows.ContentElement.MouseLeave> animace. Je to proto, že animaci je schopen sledovat, původní hodnota.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Další informace najdete v tématu [přehled scénářů](../graphics-multimedia/storyboards-overview.md).  
  
 Na následujícím obrázku je ukazatel myši přejdete třetí položka:  
  
 ![Snímek obrazovky ukázkový používání stylů pro](./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers DataTriggers a MultiDataTriggers  
 Kromě <xref:System.Windows.Trigger> a <xref:System.Windows.EventTrigger>, se objeví jiné typy aktivačních událostí. <xref:System.Windows.MultiTrigger> Umožňuje nastavit hodnoty vlastností na základě více podmínek. Použijete <xref:System.Windows.DataTrigger> a <xref:System.Windows.MultiDataTrigger> při vlastnost vaše podmínka je vázaný na data.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Sdílené prostředky a motivů  
 Typická aplikace Windows Presentation Foundation (WPF) může mít více prostředky uživatelského rozhraní (UI), které jsou použity v celé aplikaci. Dále souhrnně nazývané tuto sadu prostředků lze považovat za motiv pro aplikaci. Windows Presentation Foundation (WPF) poskytuje podporu pro balení uživatelské rozhraní (UI) prostředky jako motiv pomocí slovníku prostředků, která jsou zapouzdřena jako <xref:System.Windows.ResourceDictionary> třídy.  
  
 Motivy Windows Presentation Foundation (WPF) jsou definovány pomocí stylů a šablon mechanismus, který zpřístupňuje Windows Presentation Foundation (WPF) pro přizpůsobení vizuály libovolný element.  
  
 Windows Presentation Foundation (WPF) motiv prostředky jsou uloženy ve slovnících integrovaný prostředek. Tyto slovníky prostředků musí být vložen v podepsané sestavení, a můžete buď vložit ve stejném sestavení jako samotný kód nebo v sestavení vedle sebe. V případě knihovně PresentationFramework.dll, sestavení, která obsahuje ovládací prvky Windows Presentation Foundation (WPF), motiv prostředky jsou v řadě sestavení vedle sebe.  
  
 Motiv se změní na poslední místem, kde můžete hledat při hledání stylu elementu. Obvykle hledání zahájíme procházením nahoru stromem prvků vyhledávání pro příslušný prostředek a hledat v kolekci prostředků aplikace a nakonec dotaz na systém. To poskytuje vývojářům aplikací možnost změnit styl pro libovolný objekt na úrovni stromu nebo aplikace před dosažením motiv.  
  
 Slovníky sloučených prostředků můžete definovat jako samostatné soubory, které vám umožní znovu použít motiv napříč více aplikacemi. Můžete také vytvořit swappable motivy definováním více slovníky prostředků, které poskytují stejné typy prostředků, ale s různými hodnotami. Tyto styly nebo další prostředky na úrovni aplikace, nově definují obor je doporučený postup pro změnu vzhledu aplikace.  
  
 Sdílet sadu prostředků, včetně – styly a šablony, mezi aplikacemi, můžete vytvořit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů a definování <xref:System.Windows.ResourceDictionary>. Například, podívejte se na následující obrázek, který ukazuje část [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating):

![Ovládací prvek v příkladech šablon](./media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Pokud se podíváte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory v ukázce uvidíte, že všechny soubory mají následující:  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 Je sdílení `shared.xaml`, která definuje <xref:System.Windows.ResourceDictionary> , který obsahuje sadu prostředků stylu a štětec, který umožňuje ovládací prvky v ukázce mít jednotný vzhled.  
  
 Další informace najdete v tématu [sloučené slovníky prostředků](../advanced/merged-resource-dictionaries.md).  
  
 Pokud vytváříte motiv pro vás vlastního ovládacího prvku, naleznete v části externí knihovna ovládacích prvků [Přehled vytváření ovládacího prvku](control-authoring-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Sbalení URI v technologii WPF](../app-development/pack-uris-in-wpf.md)
- [Postupy: Vyhledávání elementů generovaných objektem ControlTemplate](how-to-find-controltemplate-generated-elements.md)
- [Hledání elementů generovaných šablonou DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
