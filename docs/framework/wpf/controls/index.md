---
title: "Ovládací prvky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66c6cc58423a2af8d0fd6de93b8884918888fb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="controls"></a>Ovládací prvky
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]se dodává s mnoha společné součásti uživatelského rozhraní, které se používají v téměř každé aplikace pro systém Windows, jako <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>, a <xref:System.Windows.Controls.ListBox>. Tyto objekty mají byly v minulosti označovány jako ovládací prvky. Při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK budou nadále používat "dohledem" volně rozumí všechny třídy, která představuje objekt viditelné v aplikaci, je důležité si uvědomit, že třídu není potřeba dědí <xref:System.Windows.Controls.Control> třídy tak, aby měl viditelné přítomnosti. Třídy, které dědí od <xref:System.Windows.Controls.Control> třída obsahovat <xref:System.Windows.Controls.ControlTemplate>, která umožňuje příjemci ovládacího prvku výrazně změnit vzhled ovládacího prvku bez nutnosti vytvoření nové podtřídy.  Toto téma popisuje, jak ovládací prvky (i ty, které dědí <xref:System.Windows.Controls.Control> třídy a ty, které nechcete) běžně se používají v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Vytvoření Instance ovládacího prvku  
 Přidáním ovládacího prvku do aplikace pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu.  Následující příklad ukazuje, jak vytvořit jednoduchou aplikaci, která požádá uživatele o jejich křestní jméno a příjmení.  Tento příklad vytvoří šest ovládacích prvků: dva popisků, dvou textových polí a dvě tlačítka v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podobně se dají vytvořit všechny ovládací prvky.  
  
 [!code-xaml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 Následující příklad vytvoří stejnou aplikaci v kódu. Pro vytvoření jako stručný výtah <xref:System.Windows.Controls.Grid>, `grid1`, byl vyloučen z vzorku. `grid1`má stejné definice sloupců a řádků, jak je vidět v předchozím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Změna vzhledu ovládacího prvku  
 Je běžné, chcete-li změnit vzhled ovládacího prvku podle vzhledu a chování vaší aplikace. Jedním z následujících, v závislosti na tom, co chcete dosáhnout, můžete změnit vzhled ovládacího prvku:  
  
-   Změňte hodnotu vlastnosti ovládacího prvku.  
  
-   Vytvoření <xref:System.Windows.Style> pro ovládací prvek.  
  
-   Vytvořte novou <xref:System.Windows.Controls.ControlTemplate> pro ovládací prvek.  
  
### <a name="changing-a-controls-property-value"></a>Změna vlastností ovládacího prvku  
 Mnoho ovládacích prvků mají vlastnosti, které vám umožní změnit, jak ovládací prvek se zobrazuje, jako <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>. Můžete nastavit hodnotu vlastnosti v obou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kód. Následující příklad nastavuje <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, a <xref:System.Windows.Controls.Control.FontWeight%2A> vlastnosti <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 Následující příklad nastaví stejné vlastnosti v kódu.  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Vytváření styl pro ovládací prvek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje možnost určit vzhled ovládacích prvků velkoobchodních, místo nastavení vlastnosti na každou instanci v aplikaci, tak, že vytvoříte <xref:System.Windows.Style>. Následující příklad vytvoří <xref:System.Windows.Style> , se použijí na každou <xref:System.Windows.Controls.Button> v aplikaci. <xref:System.Windows.Style>definice jsou obvykle definovány v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v <xref:System.Windows.ResourceDictionary>, například <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Styl můžete taky použít jenom některé ovládací prvky určitého typu přiřazení klíče na styl a určením klíči v `Style` vlastnost ovládacího prvku.  Další informace o styly najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Vytváření ControlTemplate  
 A <xref:System.Windows.Style> umožňuje nastavit vlastnosti u více ovládacích prvků v čase, ale v některých případech můžete chtít přizpůsobit vzhled <xref:System.Windows.Controls.Control> nad rámec můžete provést vytvořením <xref:System.Windows.Style>. Třídy, které dědí od <xref:System.Windows.Controls.Control> třída mít <xref:System.Windows.Controls.ControlTemplate>, která definuje strukturu a vzhled <xref:System.Windows.Controls.Control>. <xref:System.Windows.Controls.Control.Template%2A> Vlastnost <xref:System.Windows.Controls.Control> je veřejný, takže můžete udělit <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> , je jiná než výchozí. Často můžete zadat nový <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Control> místo dědění z ovládacího prvku pro přizpůsobení vzhledu <xref:System.Windows.Controls.Control>.  
  
 Vezměte v úvahu velmi běžného ovládacího prvku, <xref:System.Windows.Controls.Button>.  Primární chování <xref:System.Windows.Controls.Button> je umožnit aplikaci určitou akci po kliknutí na ho.  Ve výchozím nastavení <xref:System.Windows.Controls.Button> v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se zobrazí jako vyvolané obdélníku.  Při vývoji aplikace, můžete chtít využívat výhod chování <xref:System.Windows.Controls.Button>– to znamená, ve zpracování klikněte na tlačítko události – ale můžete změnit vzhled tlačítka nad rámec můžete provést změnou na tlačítko Vlastnosti.  V takovém případě můžete vytvořit nový <xref:System.Windows.Controls.ControlTemplate>.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Button>.  <xref:System.Windows.Controls.ControlTemplate> Vytvoří <xref:System.Windows.Controls.Button> s zaoblenými hranami a barevného přechodu pozadí.  <xref:System.Windows.Controls.ControlTemplate> Obsahuje <xref:System.Windows.Controls.Border> jejichž <xref:System.Windows.Controls.Border.Background%2A> je <xref:System.Windows.Media.LinearGradientBrush> se dvěma <xref:System.Windows.Media.GradientStop> objekty.  První <xref:System.Windows.Media.GradientStop> používá datové vazby k vytvoření vazby <xref:System.Windows.Media.GradientStop.Color%2A> vlastnost <xref:System.Windows.Media.GradientStop> na barvu pozadí na tlačítko.  Když nastavíte <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.Button>, barva tato hodnota se použije jako první <xref:System.Windows.Media.GradientStop>. Další informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md). V příkladu se vytváří také <xref:System.Windows.Trigger> , mění vzhled <xref:System.Windows.Controls.Button> při <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> je `true`.  
  
 [!code-xaml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A> Vlastnost <xref:System.Windows.Controls.Button> musí být nastavena na <xref:System.Windows.Media.SolidColorBrush> například správně fungovat.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Přihlášení k odběru událostí  
 Můžete přihlásíte k odběru události ovládacího prvku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kód, ale může zpracovat pouze událost v kódu.  Následující příklad ukazuje, jak se přihlásit k odběru `Click` události <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 Následující příklad popisovače `Click` události <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Bohaté obsah v ovládacích prvcích  
 Většina tříd, které dědí od <xref:System.Windows.Controls.Control> třídy mají kapacitu tak, aby obsahovala složitý obsah. Například <xref:System.Windows.Controls.Label> může obsahovat libovolný objekt, jako je například řetězec, <xref:System.Windows.Controls.Image>, nebo <xref:System.Windows.Controls.Panel>.  Následující třídy poskytují podporu pro bohatou obsah a fungovat jako základní třídy pro většinu ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>– Příklady tříd, které dědí z této třídy lze <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, a <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>– Příklady tříd, které dědí z této třídy lze <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>, a <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>– Příklady tříd, které dědí z této třídy lze <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>, a <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>– Příklady tříd, které dědí z této třídy lze <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>, a <xref:System.Windows.Controls.ToolBar>.  
  
-  
  
 Další informace o tyto základní třídy najdete v tématu [modelu obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Ovládací prvky podle kategorie](../../../../docs/framework/wpf/controls/controls-by-category.md)  
 [Knihovna ovládacích prvků](../../../../docs/framework/wpf/controls/control-library.md)  
 [Přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vstup](../../../../docs/framework/wpf/advanced/input-wpf.md)  
 [Povolení příkazu](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)  
 [Návod: Vytvoření tlačítka s vlastní animací](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)  
 [Přizpůsobení ovládacího prvku](../../../../docs/framework/wpf/controls/control-customization.md)
