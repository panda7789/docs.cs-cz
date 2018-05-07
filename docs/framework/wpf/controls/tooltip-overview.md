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
ms.openlocfilehash: b70387e604b0917d154fc056b904e9ee05f6fbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tooltip-overview"></a>ToolTip – přehled
Popisek je malé místní okno, které se zobrazí, když uživatel pozastaví ukazatel myši nad elementem, například jako přes <xref:System.Windows.Controls.Button>. Toto téma představuje popisek a popisuje, jak vytvářet a přizpůsobovat obsah popisku.  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>Co je popisek?  
 Při přesunutí ukazatele myši nad element, který má popisek se zobrazí okno, které obsahuje popis obsah (například obsah textu, který popisuje funkce ovládacího prvku) pro zadanou dobu. Pokud se uživatel přesune ukazatelem myši směrem od ovládacího prvku, okno zmizí, protože obsah Popisek nemůže přijmout fokus.  
  
 Obsah popisek může obsahovat jeden nebo více řádků textu, obrázky, tvary nebo jiný vizuální obsah. Můžete definovat popis tlačítka pro nastavení, jednu z následujících vlastností ovládacího prvku popisek obsahu.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Vlastností, které použijete, závisí na tom, zda se ovládací prvek, který definuje popisek dědí z <xref:System.Windows.FrameworkContentElement> nebo <xref:System.Windows.FrameworkElement> třídy.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Vytváření popisu tlačítka  
 Následující příklad ukazuje, jak vytvořit jednoduché popisek nastavením <xref:System.Windows.FrameworkElement.ToolTip%2A> vlastnost <xref:System.Windows.Controls.Button> řízení textového řetězce.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Můžete také definovat jako popisek <xref:System.Windows.Controls.ToolTip> objektu. Následující příklad používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] k určení <xref:System.Windows.Controls.ToolTip> objektu jako popis <xref:System.Windows.Controls.TextBox> elementu. Všimněte si, že v příkladu určuje <xref:System.Windows.Controls.ToolTip> nastavením <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> vlastnost.  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 Následující příklad používá ke generování kódu <xref:System.Windows.Controls.ToolTip> objektu. V příkladu se vytváří <xref:System.Windows.Controls.ToolTip> (`tt`) a přidruží ji s <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Můžete také vytvořit popisek obsah, který není definován jako <xref:System.Windows.Controls.ToolTip> objekt uzavřením popisek obsah do elementu rozložení, například <xref:System.Windows.Controls.DockPanel>. Následující příklad ukazuje, jak nastavit <xref:System.Windows.FrameworkElement.ToolTip%2A> vlastnost <xref:System.Windows.Controls.TextBox> k obsahu, který je součástí <xref:System.Windows.Controls.DockPanel> ovládacího prvku.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Pomocí vlastnosti popisu tlačítka a ToolTipService třídy  
 Obsah popis můžete přizpůsobit nastavení vizuálních vlastností a použití stylů. Pokud definujete obsah jako popisek <xref:System.Windows.Controls.ToolTip> objekt, můžete nastavit visual vlastnosti <xref:System.Windows.Controls.ToolTip> objektu. Jinak, je nutné nastavit ekvivalentní připojené vlastnosti na <xref:System.Windows.Controls.ToolTipService> třídy.  
  
 Příklad nastavení vlastností a zadejte umístění popisku obsahu pomocí <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> najdete v části vlastnosti, [popisek pozice](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Práce se styly popisek  
 Můžete styl <xref:System.Windows.Controls.ToolTip> tak, že definujete vlastní <xref:System.Windows.Style>. V následujícím příkladu definuje <xref:System.Windows.Style> názvem `Simple` který ukazuje, jak posun umístění <xref:System.Windows.Controls.ToolTip> a změnit její vzhled nastavením <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, a <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Pomocí vlastnosti Interval času ToolTipService  
 <xref:System.Windows.Controls.ToolTipService> Třída poskytuje následující vlastnosti vám umožní nastavit popis pro zobrazení časy: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Použití <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> vlastnosti k určení zpoždění, obvykle stručné, před <xref:System.Windows.Controls.ToolTip> se zobrazí a také určit, jak dlouho <xref:System.Windows.Controls.ToolTip> , zůstává viditelná. Další informace najdete v tématu [postupy: zobrazení popisek zpoždění](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Vlastnost určuje, pokud popisy pro ovládací prvky se bez počáteční zpoždění při přesunutí ukazatele myši rychle mezi nimi. Další informace o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> vlastnost, najdete v části [použijte vlastnost BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 Následující příklad ukazuje, jak nastavit tyto vlastnosti pro popisek.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [Témata s postupy](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
