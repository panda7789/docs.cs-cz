---
title: Ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: faa1fbad85acf5788c10de7750c6a7c32b535bf5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957037"
---
# <a name="controls"></a>Ovládací prvky
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]dodává se s mnoha běžnými součástmi uživatelského rozhraní, které se používají téměř v každé aplikaci pro <xref:System.Windows.Controls.Button>Windows <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>například <xref:System.Windows.Controls.Menu>,, <xref:System.Windows.Controls.ListBox>, a. Historicky tyto objekty byly označovány jako ovládací prvky. I když <xref:System.Windows.Controls.Control> sada SDK stále používá termín "ovládací prvek" k volnému znamená jakékoli třídy, která představuje viditelný objekt v aplikaci, je důležité si uvědomit, že třída nemusí dědit od třídy, aby měla viditelné přítomnosti. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Třídy, které dědí z <xref:System.Windows.Controls.Control> třídy, obsahují <xref:System.Windows.Controls.ControlTemplate>a, což umožňuje spotřebiteli ovládacího prvku odvodit, že se vzhled ovládacího prvku bude měnit bez nutnosti vytvořit novou podtřídu.  Toto téma popisuje, jak se používají ovládací prvky (obě metody, <xref:System.Windows.Controls.Control> které dědí z třídy i těch, které nejsou) se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]běžně používají v.  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Vytvoření instance ovládacího prvku  
 Můžete přidat ovládací prvek do aplikace pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kódu nebo.  Následující příklad ukazuje, jak vytvořit jednoduchou aplikaci, která žádá uživatele o jejich křestní jméno a příjmení.  Tento příklad vytvoří šest ovládacích prvků: dva popisky, dvě textová pole a dvě tlačítka v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Všechny ovládací prvky lze vytvořit podobně.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Následující příklad vytvoří stejnou aplikaci v kódu. Pro zkrácení bylo z ukázky vyloučeno <xref:System.Windows.Controls.Grid>vytváření `grid1`,. `grid1`má stejné definice sloupců a řádků, jak je znázorněno v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] předchozím příkladu.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Změna vzhledu ovládacího prvku  
 Je běžné, že změníte vzhled ovládacího prvku tak, aby odpovídal vzhledu a chování vaší aplikace. Vzhled ovládacího prvku lze změnit jedním z následujících způsobů v závislosti na tom, co chcete provést:  
  
- Změňte hodnotu vlastnosti ovládacího prvku.  
  
- <xref:System.Windows.Style> Vytvořte pro ovládací prvek.  
  
- Vytvořte nový <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek.  
  
### <a name="changing-a-controls-property-value"></a>Změna hodnoty vlastnosti ovládacího prvku  
 Mnohé ovládací prvky mají vlastnosti, které umožňují změnit způsob zobrazení ovládacího prvku, jako je <xref:System.Windows.Controls.Control.Background%2A> například <xref:System.Windows.Controls.Button>z. Můžete nastavit vlastnosti hodnoty v kódu i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Následující <xref:System.Windows.Controls.Control.Background%2A>příklad nastaví vlastnosti <xref:System.Windows.Controls.Control.FontWeight%2A> , <xref:System.Windows.Controls.Control.FontSize%2A>av [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]v. <xref:System.Windows.Controls.Button>  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Následující příklad nastaví stejné vlastnosti v kódu.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Vytvoření stylu pro ovládací prvek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje určit vzhled pro velkoobchodní řízení, místo nastavení vlastností každé instance aplikace vytvořením <xref:System.Windows.Style>. Následující příklad vytvoří <xref:System.Windows.Style> , který je použit pro každý <xref:System.Windows.Controls.Button> v aplikaci. <xref:System.Windows.Style>definice jsou obvykle definovány v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.ResourceDictionary>v, jako <xref:System.Windows.FrameworkElement.Resources%2A> je například vlastnost třídy <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Můžete také použít styl pouze na určité ovládací prvky určitého typu přiřazením klíče ke stylu a zadáním klíče ve `Style` vlastnosti ovládacího prvku.  Další informace o stylech naleznete v tématu [stylování and šablonování](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Vytvoření objektu ControlTemplate  
 Umožňuje nastavit vlastnosti pro více ovládacích prvků najednou, ale v některých případech můžete chtít přizpůsobit vzhled <xref:System.Windows.Controls.Control> nad rámec toho, co <xref:System.Windows.Style>můžete udělat vytvořením. <xref:System.Windows.Style> Třídy, které dědí z <xref:System.Windows.Controls.Control> třídy <xref:System.Windows.Controls.ControlTemplate>, mají třídu, která definuje <xref:System.Windows.Controls.Control>strukturu a vzhled. Vlastnost je veřejná <xref:System.Windows.Controls.ControlTemplate> ,<xref:System.Windows.Controls.Control> takže můžete předat a, která se liší od výchozí hodnoty. <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.Control.Template%2A> Můžete často zadat nové <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Control> místo dědění z ovládacího prvku pro <xref:System.Windows.Controls.Control>přizpůsobení vzhledu.  
  
 Vezměte v úvahu velmi běžný ovládací <xref:System.Windows.Controls.Button>prvek.  Primární chování <xref:System.Windows.Controls.Button> funkce je, aby aplikace mohla provést nějakou akci, když na ni uživatel klikne.  Ve výchozím nastavení <xref:System.Windows.Controls.Button> se v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zobrazí jako vystouplý obdélník.  Při vývoji aplikace můžete chtít využít výhod chování a <xref:System.Windows.Controls.Button>– to znamená provedením události kliknutí na tlačítko, ale můžete změnit vzhled tlačítka nad rámec toho, co můžete udělat změnou vlastností tlačítka.  V takovém případě můžete vytvořit nový <xref:System.Windows.Controls.ControlTemplate>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>pro.  <xref:System.Windows.Controls.ControlTemplate> Vytvořísezaoblenýmirohya<xref:System.Windows.Controls.Button> přechodem na pozadí.  <xref:System.Windows.Controls.ControlTemplate> Obsahuje, jehož<xref:System.Windows.Controls.Border.Background%2A> je a<xref:System.Windows.Media.LinearGradientBrush> má dva<xref:System.Windows.Media.GradientStop> objekty. <xref:System.Windows.Controls.Border>  První <xref:System.Windows.Media.GradientStop> používá datovou vazbu pro <xref:System.Windows.Media.GradientStop.Color%2A> svázání vlastnosti <xref:System.Windows.Media.GradientStop> s barvou pozadí tlačítka.  Když nastavíte <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.Button>, bude použita barva této hodnoty jako první <xref:System.Windows.Media.GradientStop>. Další informace o datové vazbě najdete v tématu [Přehled datových vazeb](../data/data-binding-overview.md). V tomto příkladu se vytvoří <xref:System.Windows.Trigger> také, který změní vzhled v <xref:System.Windows.Controls.Button> případě <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> , `true`kdy je.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Vlastnost musí být nastavena na hodnotu <xref:System.Windows.Media.SolidColorBrush> , aby mohl příklad správně fungovat. <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A>  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Můžete se přihlásit k odběru události ovládacího prvku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu nebo, ale můžete zpracovat pouze událost v kódu.  Následující příklad ukazuje, jak se přihlásit k odběru `Click` události. <xref:System.Windows.Controls.Button>  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Následující příklad zpracovává `Click` událost <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Bohatý obsah v ovládacích prvcích  
 Většina tříd, které dědí z <xref:System.Windows.Controls.Control> třídy, má kapacitu obsahující bohatou velikost obsahu. Například <xref:System.Windows.Controls.Label> může obsahovat libovolný objekt, jako je například řetězec <xref:System.Windows.Controls.Image>, nebo <xref:System.Windows.Controls.Panel>.  Následující třídy poskytují podporu pro bohatou velikost obsahu a fungují jako základní třídy pro většinu ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Controls.ContentControl>– Některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>a <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>– Některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>a <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>– Některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>a <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>– Některé příklady tříd, které dědí z této třídy, jsou <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>a <xref:System.Windows.Controls.ToolBar>.  

 Další informace o těchto základních třídách naleznete v tématu [model obsahu WPF](wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](styling-and-templating.md)
- [Ovládací prvky podle kategorie](controls-by-category.md)
- [Knihovna ovládacích prvků](control-library.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Vstup](../advanced/input-wpf.md)
- [Povolení příkazu](../advanced/how-to-enable-a-command.md)
- [Návody: Vytvoření vlastního animovaného tlačítka](walkthroughs-create-a-custom-animated-button.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
