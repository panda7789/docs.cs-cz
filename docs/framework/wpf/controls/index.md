---
title: Ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 42596c8adf1b8b27f250fa7a3cf6cc173a63e2eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459444"
---
# <a name="controls"></a>Ovládací prvky
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] lodích s mnoha běžnými součástmi uživatelského rozhraní, které se používají téměř v každé aplikaci pro Windows, například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>a <xref:System.Windows.Controls.ListBox>. Historicky tyto objekty byly označovány jako ovládací prvky. I když sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK nadále používá pojem "ovládací prvek" k volnému znamená libovolnou třídu, která představuje viditelný objekt v aplikaci, je důležité si uvědomit, že třída nepotřebuje dědit od <xref:System.Windows.Controls.Control> třídy, aby měla viditelné přítomnosti. Třídy, které dědí z třídy <xref:System.Windows.Controls.Control> obsahují <xref:System.Windows.Controls.ControlTemplate>, která umožňuje spotřebiteli ovládacího prvku odmocninovat vzhled ovládacího prvku bez nutnosti vytvořit novou podtřídu.  Toto téma popisuje, jak se v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]běžně používají ovládací prvky (obě ta, která dědí z třídy <xref:System.Windows.Controls.Control> a těch, které ne).  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Vytvoření instance ovládacího prvku  
 Můžete přidat ovládací prvek do aplikace pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu.  Následující příklad ukazuje, jak vytvořit jednoduchou aplikaci, která žádá uživatele o jejich křestní jméno a příjmení.  Tento příklad vytvoří šest ovládacích prvků: dva popisky, dvě textová pole a dvě tlačítka v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Všechny ovládací prvky lze vytvořit podobně.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Následující příklad vytvoří stejnou aplikaci v kódu. Pro zkrácení se z ukázky vyloučilo vytvoření <xref:System.Windows.Controls.Grid>`grid1`. `grid1` má stejné definice sloupců a řádků, jak je znázorněno v předchozím příkladu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Změna vzhledu ovládacího prvku  
 Je běžné, že změníte vzhled ovládacího prvku tak, aby odpovídal vzhledu a chování vaší aplikace. Vzhled ovládacího prvku lze změnit jedním z následujících způsobů v závislosti na tom, co chcete provést:  
  
- Změňte hodnotu vlastnosti ovládacího prvku.  
  
- Vytvoří <xref:System.Windows.Style> pro ovládací prvek.  
  
- Vytvoří nový <xref:System.Windows.Controls.ControlTemplate> ovládacího prvku.  
  
### <a name="changing-a-controls-property-value"></a>Změna hodnoty vlastnosti ovládacího prvku  
 Mnohé ovládací prvky mají vlastnosti, které umožňují změnit způsob zobrazení ovládacího prvku, například <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>. Vlastnosti hodnoty můžete nastavit jak v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tak i v kódu. Následující příklad nastaví vlastnosti <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>a <xref:System.Windows.Controls.Control.FontWeight%2A> na <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Následující příklad nastaví stejné vlastnosti v kódu.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Vytvoření stylu pro ovládací prvek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje určit vzhled pro velkoobchodní řízení a místo nastavení vlastností každé instance aplikace vytvořením <xref:System.Windows.Style>. Následující příklad vytvoří <xref:System.Windows.Style>, který se použije u každého <xref:System.Windows.Controls.Button> v aplikaci. definice <xref:System.Windows.Style> jsou obvykle definovány v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.ResourceDictionary>, jako je například vlastnost <xref:System.Windows.FrameworkElement.Resources%2A> <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Můžete také použít styl pouze na určité ovládací prvky určitého typu přiřazením klíče ke stylu a zadáním tohoto klíče do vlastnosti `Style` ovládacího prvku.  Další informace o stylech naleznete v tématu [stylování and šablonování](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Vytvoření objektu ControlTemplate  
 <xref:System.Windows.Style> umožňuje nastavit vlastnosti pro více ovládacích prvků najednou, ale někdy můžete chtít přizpůsobit vzhled <xref:System.Windows.Controls.Control> nad rámec toho, co můžete vytvořit <xref:System.Windows.Style>. Třídy, které dědí z třídy <xref:System.Windows.Controls.Control> mají <xref:System.Windows.Controls.ControlTemplate>, který definuje strukturu a vzhled <xref:System.Windows.Controls.Control>. Vlastnost <xref:System.Windows.Controls.Control.Template%2A> <xref:System.Windows.Controls.Control> je veřejná, takže můžete předat <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate>, který je jiný než výchozí. Můžete často zadat novou <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Control> namísto dědění ovládacího prvku pro přizpůsobení vzhledu <xref:System.Windows.Controls.Control>.  
  
 Vezměte v úvahu velmi běžný ovládací prvek <xref:System.Windows.Controls.Button>.  Hlavním chováním <xref:System.Windows.Controls.Button> je umožnit aplikaci provést nějakou akci, když na ni uživatel klikne.  Ve výchozím nastavení se <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zobrazí jako vystouplý obdélník.  Při vývoji aplikace můžete chtít využít výhod chování <xref:System.Windows.Controls.Button>– to znamená tím, že se postará událost kliknutí na tlačítko, ale můžete změnit vzhled tlačítka nad rámec toho, co můžete udělat změnou vlastností tlačítka.  V takovém případě můžete vytvořit novou <xref:System.Windows.Controls.ControlTemplate>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> vytvoří <xref:System.Windows.Controls.Button> pomocí zaoblených rohů a pozadí přechodu.  <xref:System.Windows.Controls.ControlTemplate> obsahuje <xref:System.Windows.Controls.Border>, jehož <xref:System.Windows.Controls.Border.Background%2A> je <xref:System.Windows.Media.LinearGradientBrush> se dvěma <xref:System.Windows.Media.GradientStop>mi objekty.  První <xref:System.Windows.Media.GradientStop> používá datovou vazbu k navázání vlastnosti <xref:System.Windows.Media.GradientStop.Color%2A> <xref:System.Windows.Media.GradientStop> na barvu pozadí tlačítka.  Když nastavíte vlastnost <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>, bude použita barva této hodnoty jako první <xref:System.Windows.Media.GradientStop>. Další informace o datové vazbě najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md). V příkladu se také vytvoří <xref:System.Windows.Trigger>, který změní vzhled <xref:System.Windows.Controls.Button>, pokud je <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> `true`.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Aby mohl příklad správně fungovat, musí být vlastnost <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> nastavena na hodnotu <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Můžete se přihlásit k odběru události ovládacího prvku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu, ale můžete zpracovat pouze událost v kódu.  Následující příklad ukazuje, jak se přihlásit k odběru události `Click` <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Následující příklad zpracovává událost `Click` <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Bohatý obsah v ovládacích prvcích  
 Většina tříd, které dědí z třídy <xref:System.Windows.Controls.Control>, mají kapacitu obsahující bohatou velikost obsahu. <xref:System.Windows.Controls.Label> například může obsahovat libovolný objekt, jako je například řetězec, <xref:System.Windows.Controls.Image>nebo <xref:System.Windows.Controls.Panel>.  Následující třídy poskytují podporu pro bohatou velikost obsahu a fungují jako základní třídy pro většinu ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Controls.ContentControl>– některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>a <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>– některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>a <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>– některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>a <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>– některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>a <xref:System.Windows.Controls.ToolBar>.  

 Další informace o těchto základních třídách naleznete v tématu [model obsahu WPF](wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](styling-and-templating.md)
- [Ovládací prvky podle kategorie](controls-by-category.md)
- [Knihovna ovládacích prvků](control-library.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Input](../advanced/input-wpf.md) (Vstup)
- [Povolení příkazu](../advanced/how-to-enable-a-command.md)
- [Návod: Vytvoření tlačítka s vlastní animací](walkthroughs-create-a-custom-animated-button.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
