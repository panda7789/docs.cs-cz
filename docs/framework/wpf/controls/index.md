---
title: Ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2aab0fc8adaf17a8e9820a6269a740ef09540cda
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646489"
---
# <a name="controls"></a>Ovládací prvky
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Dodává se s mnoha běžnými součástmi nového prostředí, které <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label>se <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu>používají <xref:System.Windows.Controls.ListBox>téměř ve všech aplikacích systému Windows, například v aplikaci , , a . Historicky tyto objekty byly označovány jako ovládací prvky. Zatímco [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sada SDK nadále používá termín "ovládací prvek" volně znamenat všechny třídy, která představuje viditelný objekt v aplikaci, je důležité si uvědomit, že třída nemusí dědit z <xref:System.Windows.Controls.Control> třídy mít viditelné přítomnosti. Třídy, které <xref:System.Windows.Controls.Control> dědí <xref:System.Windows.Controls.ControlTemplate>z třídy obsahují , který umožňuje spotřebiteli ovládacího prvku radikálně změnit vzhled ovládacího prvku bez nutnosti vytvářet novou podtřídu.  Toto téma popisuje, jak se ovládací <xref:System.Windows.Controls.Control> prvky (ty, které dědí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]z třídy, tak ty, které nedědí) běžně používají v aplikaci .  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Vytvoření instance ovládacího prvku  
 Ovládací prvek můžete přidat do aplikace [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pomocí jednoho nebo kódu.  Následující příklad ukazuje, jak vytvořit jednoduchou aplikaci, která požádá uživatele o jeho jméno a příjmení.  Tento příklad vytvoří šest ovládacích prvků: dva popisky, dvě textová pole a dvě tlačítka v . [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Všechny ovládací prvky lze vytvořit podobně.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Následující příklad vytvoří stejnou aplikaci v kódu. V případě stručnosti bylo ze <xref:System.Windows.Controls.Grid> `grid1`vzorku vyloučeno vytvoření písmene , `grid1`má stejné definice sloupců a řádků, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jak je znázorněno v předchozím příkladu.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Změna vzhledu ovládacího prvku  
 Je běžné změnit vzhled ovládacího prvku tak, aby odpovídal vzhledu a chování aplikace. Vzhled ovládacího prvku můžete změnit jedním z následujících akcí v závislosti na tom, čeho chcete dosáhnout:  
  
- Změňte hodnotu vlastnosti ovládacího prvku.  
  
- Vytvořte <xref:System.Windows.Style> pro ovládací prvek.  
  
- Vytvořte <xref:System.Windows.Controls.ControlTemplate> nový ovládací prvek.  
  
### <a name="changing-a-controls-property-value"></a>Změna hodnoty vlastnosti ovládacího prvku  
 Mnoho ovládacích prvků má vlastnosti, které umožňují <xref:System.Windows.Controls.Control.Background%2A> změnit <xref:System.Windows.Controls.Button>vzhled ovládacího prvku, například rozhraní . Můžete nastavit vlastnosti hodnoty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v obou a kód. Následující <xref:System.Windows.Controls.Control.Background%2A>příklad nastaví <xref:System.Windows.Controls.Control.FontSize%2A>, <xref:System.Windows.Controls.Control.FontWeight%2A> a <xref:System.Windows.Controls.Button> vlastnosti na in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Následující příklad nastaví stejné vlastnosti v kódu.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Vytvoření stylu pro ovládací prvek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje zadat vzhled ovládacích prvků ve velkém, namísto nastavení vlastností pro <xref:System.Windows.Style>každou instanci v aplikaci vytvořením . Následující příklad vytvoří, <xref:System.Windows.Style> který je <xref:System.Windows.Controls.Button> použit pro každý v aplikaci. <xref:System.Windows.Style>definice jsou obvykle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] definovány <xref:System.Windows.ResourceDictionary>v , <xref:System.Windows.FrameworkElement.Resources%2A> jako je <xref:System.Windows.FrameworkElement>například vlastnost .  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Styl můžete také použít pouze na určité ovládací prvky určitého typu přiřazením klíče `Style` ke stylu a zadáním tohoto klíče ve vlastnosti ovládacího prvku.  Další informace o stylech naleznete v [tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
### <a name="creating-a-controltemplate"></a>Vytvoření šablony ovládacího prvku  
 A <xref:System.Windows.Style> umožňuje nastavit vlastnosti na více ovládacích prvků najednou, ale někdy <xref:System.Windows.Controls.Control> můžete chtít přizpůsobit vzhled <xref:System.Windows.Style>nad rámec toho, co můžete udělat vytvořením . Třídy, které <xref:System.Windows.Controls.Control> dědí <xref:System.Windows.Controls.ControlTemplate>z třídy mají , <xref:System.Windows.Controls.Control>který definuje strukturu a vzhled . Vlastnost <xref:System.Windows.Controls.Control.Template%2A> a <xref:System.Windows.Controls.Control> je veřejná, takže <xref:System.Windows.Controls.Control> můžete <xref:System.Windows.Controls.ControlTemplate> dát, která je jiná než její výchozí. Často můžete zadat <xref:System.Windows.Controls.ControlTemplate> nový <xref:System.Windows.Controls.Control> pro místo dědění z ovládacího <xref:System.Windows.Controls.Control>prvku přizpůsobit vzhled .  
  
 Zvažte velmi časté <xref:System.Windows.Controls.Button>ovládání, .  Primární chování a <xref:System.Windows.Controls.Button> je umožnit aplikaci provést určitou akci, když na ni uživatel klepne.  Ve výchozím <xref:System.Windows.Controls.Button> nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se in zobrazí jako zvýšený obdélník.  Při vývoji aplikace můžete chtít využít chování <xref:System.Windows.Controls.Button>--that je zpracováním události kliknutí tlačítka - ale můžete změnit vzhled tlačítka nad rámec toho, co můžete udělat změnou vlastností tlačítka.  V takovém případě můžete vytvořit <xref:System.Windows.Controls.ControlTemplate>nový .  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.ControlTemplate> for <xref:System.Windows.Controls.Button>a .  Vytvoří <xref:System.Windows.Controls.ControlTemplate> se <xref:System.Windows.Controls.Button> zaoblenými rohy a pozadím přechodu.  <xref:System.Windows.Controls.Border> Obsahuje, <xref:System.Windows.Controls.ControlTemplate> jehož <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Media.LinearGradientBrush> je <xref:System.Windows.Media.GradientStop> s dvěma objekty.  První <xref:System.Windows.Media.GradientStop> používá datovou vazbu <xref:System.Windows.Media.GradientStop.Color%2A> k <xref:System.Windows.Media.GradientStop> vázání vlastnosti na barvu pozadí tlačítka.  Pokud nastavíte <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.Button>, barva této hodnoty bude použita jako první <xref:System.Windows.Media.GradientStop>. Další informace o datové vazbě naleznete v [tématu Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md). Příklad také <xref:System.Windows.Trigger> vytvoří, který změní <xref:System.Windows.Controls.Button> vzhled <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> `true`when is .  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Vlastnost <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> musí být nastavena <xref:System.Windows.Media.SolidColorBrush> na pro příklad pracovat správně.  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 K odběru události ovládacího prvku se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] můžete přihlásit pomocí jednoho nebo kódu, ale událost můžete zpracovat pouze v kódu.  Následující příklad ukazuje, jak `Click` se přihlásit k odběru události <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Následující příklad zpracovává `Click` událost <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Bohatý obsah v ovládacích prvcích  
 Většina tříd, <xref:System.Windows.Controls.Control> které dědí z třídy mají schopnost obsahovat bohatý obsah. Může <xref:System.Windows.Controls.Label> například obsahovat libovolný objekt, například <xref:System.Windows.Controls.Image>řetězec, <xref:System.Windows.Controls.Panel>nebo .  Následující třídy poskytují podporu pro bohatý obsah a fungují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jako základní třídy pro většinu ovládacích prvků v .  
  
- <xref:System.Windows.Controls.ContentControl>-- Některé příklady tříd, které <xref:System.Windows.Controls.Label>dědí z této třídy jsou , <xref:System.Windows.Controls.Button>a <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>-- Některé příklady tříd, které <xref:System.Windows.Controls.ListBox>dědí z této třídy jsou , <xref:System.Windows.Controls.Menu>a <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- Některé příklady tříd, které <xref:System.Windows.Controls.TabItem>dědí z této třídy jsou , <xref:System.Windows.Controls.GroupBox>a <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Některé příklady tříd, které dědí <xref:System.Windows.Controls.TreeViewItem>z <xref:System.Windows.Controls.ToolBar>této třídy jsou <xref:System.Windows.Controls.MenuItem>, a .  

 Další informace o těchto základních třídách naleznete v [tématu WPF Content Model](wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také

- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Řízení podle kategorie](controls-by-category.md)
- [Knihovna ovládacích prvků](control-library.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Vstup](../advanced/input-wpf.md)
- [Povolení příkazu](../advanced/how-to-enable-a-command.md)
- [Návod: Vytvoření tlačítka s vlastní animací](walkthroughs-create-a-custom-animated-button.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
