---
title: Ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: f4aeb3dd60186a4060f7825257c7adb274fc8b24
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363147"
---
# <a name="controls"></a>Ovládací prvky
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se dodává s mnoha běžných součásti uživatelského rozhraní, které se používají v téměř všechny aplikace Windows, jako například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>, a <xref:System.Windows.Controls.ListBox>. Tyto objekty mají byla v minulosti uvedené jako ovládací prvky. Zatímco [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK pořád používá termín "control" volně rozumí jakékoli třídy, která představuje viditelného objektu v aplikaci, je důležité si uvědomit, že třídu není potřeba dědit z <xref:System.Windows.Controls.Control> třídě budou mít viditelné přítomnost. Třídy odvozené z <xref:System.Windows.Controls.Control> třída obsahovat <xref:System.Windows.Controls.ControlTemplate>, která umožňuje příjemci ovládacího prvku výrazně změnit vzhled ovládacího prvku bez nutnosti vytvořit novou podtřídu.  Toto téma popisuje, jak ovládací prvky (i těch, které dědí z <xref:System.Windows.Controls.Control> třídy a ty, které nejsou) se obvykle používají [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Vytvoření Instance ovládacího prvku  
 Můžete přidat ovládací prvek k aplikaci pomocí buď [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu.  Následující příklad ukazuje, jak vytvořit jednoduchou aplikaci, která uživatele vyzve k zadání jména a příjmení.  Tento příklad vytvoří šesti ovládacích prvků: dva popisky, dvě textová pole a dvě tlačítka v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podobně je možné vytvořit všechny ovládací prvky.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Následující příklad vytvoří stejné aplikace v kódu. Pro zkrácení vytváření <xref:System.Windows.Controls.Grid>, `grid1`, byly vyloučeny z ukázky. `grid1` má stejné definice sloupců a řádků, jak je znázorněno v předchozím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Změna vzhledu ovládacího prvku  
 Je běžné, chcete-li změnit vzhled ovládacího prvku pro přizpůsobení vzhledu a chování vaší aplikace. Můžete změnit vzhled ovládacího prvku pomocí jedné z těchto možností podle toho, co chcete dosáhnout:  
  
-   Změňte hodnotu vlastnosti ovládacího prvku.  
  
-   Vytvoření <xref:System.Windows.Style> pro ovládací prvek.  
  
-   Vytvořte nový <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek.  
  
### <a name="changing-a-controls-property-value"></a>Změna hodnoty vlastnosti ovládacího prvku  
 Mnoho ovládacích prvků mají vlastnosti, které umožňují změnit, jak ovládací prvek zobrazuje, jako <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. Můžete nastavit hodnotu vlastnosti v obou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kódu. Následující příklad nastaví <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, a <xref:System.Windows.Controls.Control.FontWeight%2A> vlastnosti <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Následující příklad nastaví stejné vlastnosti v kódu.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Vytvoření stylu pro ovládací prvek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje možnost určit vzhled ovládacích prvků velkoobchodních, místo nastavování vlastností pro každou instanci aplikace, tak, že vytvoříte <xref:System.Windows.Style>. Následující příklad vytvoří <xref:System.Windows.Style> , která je použita na každý <xref:System.Windows.Controls.Button> v aplikaci. <xref:System.Windows.Style> definice jsou obvykle definovány v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v <xref:System.Windows.ResourceDictionary>, například <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Můžete také použít styl na pouze některé ovládací prvky určitého typu přiřazením klíč stylu a zadáte tento klíč v `Style` vlastnost ovládacího prvku.  Další informace o stylech najdete v tématu [styly a šablony](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Vytvoření objektu ControlTemplate  
 A <xref:System.Windows.Style> vám umožní nastavit vlastnosti na více ovládacích prvků v čase, ale někdy může být vhodné přizpůsobit vzhled <xref:System.Windows.Controls.Control> rámec toho, co můžete udělat tak, že vytvoříte <xref:System.Windows.Style>. Třídy odvozené z <xref:System.Windows.Controls.Control> třídy <xref:System.Windows.Controls.ControlTemplate>, která definuje strukturu a vzhled <xref:System.Windows.Controls.Control>. <xref:System.Windows.Controls.Control.Template%2A> Vlastnost <xref:System.Windows.Controls.Control> je veřejné, takže můžete poskytnout <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> , která je jiná než výchozí. Často můžete zadat nový <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Control> namísto dědění z ovládacího prvku pro přizpůsobení vzhledu <xref:System.Windows.Controls.Control>.  
  
 Vezměte v úvahu velmi běžný ovládací prvek <xref:System.Windows.Controls.Button>.  Primární chování <xref:System.Windows.Controls.Button> je umožnit aplikaci provést některé akce, když na něj uživatel klikne.  Ve výchozím nastavení <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se zobrazí jako zvýšené obdélník.  Při vývoji aplikace, můžete chtít využít výhod chování <xref:System.Windows.Controls.Button>– to znamená, že pomocí manipulace klikněte na tlačítko události – ale můžete změnit vzhled na tlačítko rámec toho, co můžete dělat to změnou na tlačítko Vlastnosti.  V takovém případě můžete vytvořit nový <xref:System.Windows.Controls.ControlTemplate>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> Vytvoří <xref:System.Windows.Controls.Button> oblých rohů a barevného přechodu pozadí.  <xref:System.Windows.Controls.ControlTemplate> Obsahuje <xref:System.Windows.Controls.Border> jehož <xref:System.Windows.Controls.Border.Background%2A> je <xref:System.Windows.Media.LinearGradientBrush> se dvěma <xref:System.Windows.Media.GradientStop> objekty.  První <xref:System.Windows.Media.GradientStop> používá datové vazby k vytvoření vazby <xref:System.Windows.Media.GradientStop.Color%2A> vlastnost <xref:System.Windows.Media.GradientStop> na barvu pozadí tlačítka.  Při nastavení <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.Button>, barva tato hodnota se použije jako první <xref:System.Windows.Media.GradientStop>. Další informace o datové vazbě naleznete v tématu [Data Binding Overview](../data/data-binding-overview.md). Tento příklad také vytvoří <xref:System.Windows.Trigger> , který změní vzhled <xref:System.Windows.Controls.Button> při <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> je `true`.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A> Vlastnost <xref:System.Windows.Controls.Button> musí být nastaveno na <xref:System.Windows.Media.SolidColorBrush> například fungovala správně.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Vám může přihlásit k odběru události ovládacího prvku buď pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kód, ale může zpracovat pouze událost v kódu.  Následující příklad ukazuje, jak se přihlásit k odběru `Click` události <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Následující příklad popisovače `Click` události <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Formátovaný obsah v ovládacích prvcích  
 Většina tříd, které dědí <xref:System.Windows.Controls.Control> třídy mají kapacitu tak, aby obsahovala formátovaný obsah. Například <xref:System.Windows.Controls.Label> může obsahovat libovolný objekt, jako je řetězec, <xref:System.Windows.Controls.Image>, nebo <xref:System.Windows.Controls.Panel>.  Následující třídy poskytovat podporu pro formátovaný obsah a plnit funkci základní třídy pro většinu prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>– Příklady tříd, které z této třídy dědit <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, a <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>– Příklady tříd, které z této třídy dědit <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>, a <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>– Příklady tříd, které z této třídy dědit <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>, a <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>– Příklady tříd, které z této třídy dědit <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>, a <xref:System.Windows.Controls.ToolBar>.  

  
 Další informace o těchto základních třídách naleznete v tématu [Model obsahu WPF](wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také:
- [Styly a šablony](styling-and-templating.md)
- [Ovládací prvky podle kategorie](controls-by-category.md)
- [Knihovna ovládacích prvků](control-library.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Vstup](../advanced/input-wpf.md)
- [Povolení příkazu](../advanced/how-to-enable-a-command.md)
- [Návody: Vytvoření tlačítka s vlastní animací](walkthroughs-create-a-custom-animated-button.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
