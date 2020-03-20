---
title: ToolTip – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181952"
---
# <a name="tooltip-overview"></a>ToolTip – přehled
Popisek je malé vyskakovací okno, které se zobrazí, když uživatel <xref:System.Windows.Controls.Button>pozastaví ukazatel myši nad elementem, například nad prvkem . Toto téma představuje popis ekazičně a popisuje, jak vytvořit a přizpůsobit obsah popisku.  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a>Co je popis?  
 Když uživatel přesune ukazatel myši nad element, který má popisek, zobrazí se okno, které obsahuje obsah popisku (například textový obsah popisující funkci ovládacího prvku) po určitou dobu. Pokud uživatel přesune ukazatel myši od ovládacího prvku, okno zmizí, protože obsah popisku nemůže získat fokus.  
  
 Obsah popisku může obsahovat jeden nebo více řádků textu, obrázků, tvarů nebo jiného vizuálního obsahu. Popisek ovládacího prvku definujete nastavením jedné z následujících vlastností pro obsah popisku.  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Vlastnost, kterou používáte, závisí na tom, zda ovládací <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.FrameworkElement> prvek, který definuje popis dědí z třídy nebo.  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a>Vytvoření popisu  
 Následující příklad ukazuje, jak vytvořit jednoduchý popis <xref:System.Windows.FrameworkElement.ToolTip%2A> nastavení <xref:System.Windows.Controls.Button> vlastnosti ovládacího prvku na textový řetězec.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Popisek můžete také definovat <xref:System.Windows.Controls.ToolTip> jako objekt. Následující příklad [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používá k <xref:System.Windows.Controls.ToolTip> určení objektu jako <xref:System.Windows.Controls.TextBox> popisek prvku. Všimněte si, že <xref:System.Windows.Controls.ToolTip> příklad <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> určuje nastavenívlastnosti.  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 Následující příklad používá kód <xref:System.Windows.Controls.ToolTip> ke generování objektu. Příklad vytvoří <xref:System.Windows.Controls.ToolTip> (`tt`) a přidruží <xref:System.Windows.Controls.Button>k .  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Můžete také vytvořit obsah popisů, který <xref:System.Windows.Controls.ToolTip> není definován jako objekt, uzavřením obsahu popisku do prvku rozložení, například <xref:System.Windows.Controls.DockPanel>. Následující příklad ukazuje, jak <xref:System.Windows.FrameworkElement.ToolTip%2A> nastavit <xref:System.Windows.Controls.TextBox> vlastnost obsahu, který je <xref:System.Windows.Controls.DockPanel> uzavřen v ovládacím prvku.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Použití vlastností tříd popisu a popisu služby  
 Obsah popisů můžete přizpůsobit nastavením vizuálních vlastností a použitím stylů. Pokud definujete obsah popisku <xref:System.Windows.Controls.ToolTip> jako objekt, můžete nastavit <xref:System.Windows.Controls.ToolTip> vizuální vlastnosti objektu. V opačném případě je nutné nastavit <xref:System.Windows.Controls.ToolTipService> ekvivalentní připojené vlastnosti třídy.  
  
 Příklad nastavení vlastností za účelem určení polohy obsahu popisku <xref:System.Windows.Controls.ToolTip> pomocí <xref:System.Windows.Controls.ToolTipService> vlastností a naleznete v [tématu Umístění popisu](how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a>Stylování popisku  
 Můžete styl <xref:System.Windows.Controls.ToolTip> a definováním <xref:System.Windows.Style>vlastní . Následující příklad definuje <xref:System.Windows.Style> volané, `Simple` které ukazuje, jak <xref:System.Windows.Controls.ToolTip> kompenzovat umístění a <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>změnit <xref:System.Windows.Controls.Control.FontSize%2A>jeho <xref:System.Windows.Controls.Control.FontWeight%2A>vzhled nastavením , , a .  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Použití vlastností časového intervalu služby ToolTipService  
 Třída <xref:System.Windows.Controls.ToolTipService> poskytuje následující vlastnosti pro nastavení časů <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>zobrazení <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>popisku: , , a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Pomocí <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> vlastností a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> určete zpoždění, obvykle <xref:System.Windows.Controls.ToolTip> stručné, před tím, <xref:System.Windows.Controls.ToolTip> než se zobrazí, a také určete, jak dlouho zůstane viditelné. Další informace naleznete v [tématu How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).  
  
 Vlastnost <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> určuje, zda popisky pro různé ovládací prvky se zobrazí bez počátečního zpoždění při rychlém přesunutí ukazatele myši mezi nimi. Další informace o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> vlastnosti naleznete [v tématu Use the BetweenShowDelay Property](how-to-use-the-betweenshowdelay-property.md).  
  
 Následující příklad ukazuje, jak nastavit tyto vlastnosti pro popis.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [Témata s postupy](tooltip-how-to-topics.md)
