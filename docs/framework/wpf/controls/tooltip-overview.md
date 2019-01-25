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
ms.openlocfilehash: 9db511579e273a19c18800f2e0861ef4e9c00ab0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700569"
---
# <a name="tooltip-overview"></a>ToolTip – přehled
Malého vyskakovacího okna, který se zobrazí, když uživatel pozastavení ukazatele myši nad prvkem, například jako více než je ovládací prvek tooltip <xref:System.Windows.Controls.Button>. Toto téma představuje popisek a popisuje, jak vytvořit a přizpůsobit obsah popisku.  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>Co je popisek?  
 Když uživatel přesune ukazatel myši nad prvkem, který má popisek, zobrazí se okno, které obsahuje popis obsah (například text, který popisuje funkce ovládacího prvku) pro určenou dobu. Pokud se uživatel přesune ukazatel myši mimo ovládací prvek, v okně zmizí, protože popisek obsah nemůže získat fokus.  
  
 Obsah popisek může obsahovat jeden nebo více řádků textu, obrázky, obrazce nebo jiné vizuální obsah. Popis tlačítka pro ovládací prvek pomocí nastavení jedné z následujících vlastností můžete definovat popis obsahu.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Vlastností, které použijete, závisí na tom, zda ovládací prvek, který definuje popisek dědí z <xref:System.Windows.FrameworkContentElement> nebo <xref:System.Windows.FrameworkElement> třídy.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Vytvoření popisu  
 Následující příklad ukazuje, jak vytvořit jednoduchý popis tlačítka tak, že nastavíte <xref:System.Windows.FrameworkElement.ToolTip%2A> vlastnost <xref:System.Windows.Controls.Button> ovládací prvek textového řetězce.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Můžete také definovat popisek jako <xref:System.Windows.Controls.ToolTip> objektu. Následující příklad používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] k určení <xref:System.Windows.Controls.ToolTip> objektu jako text nápovědy <xref:System.Windows.Controls.TextBox> elementu. Všimněte si, že příklad určuje <xref:System.Windows.Controls.ToolTip> nastavením <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> vlastnost.  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 Následující příklad používá ke generování kódu <xref:System.Windows.Controls.ToolTip> objektu. V příkladu se vytvoří <xref:System.Windows.Controls.ToolTip> (`tt`) a přidruží ji k <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Můžete také vytvořit popisek obsah, který není definován jako <xref:System.Windows.Controls.ToolTip> objekt uzavřením popis obsahu v elementu rozložení, jako například <xref:System.Windows.Controls.DockPanel>. Následující příklad ukazuje, jak nastavit <xref:System.Windows.FrameworkElement.ToolTip%2A> vlastnost <xref:System.Windows.Controls.TextBox> s obsahem, který je uzavřen v <xref:System.Windows.Controls.DockPanel> ovládacího prvku.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Pomocí vlastnosti popisku a ToolTipService třídy  
 Popis obsahu můžete upravit nastavení visual vlastností a použitím stylů. Pokud definujete obsahu jako popis <xref:System.Windows.Controls.ToolTip> objektu, můžete nastavit vizuální vlastnosti <xref:System.Windows.Controls.ToolTip> objektu. V opačném případě je potřeba nastavit ekvivalentní připojené vlastnosti v <xref:System.Windows.Controls.ToolTipService> třídy.  
  
 Příklad toho, jak nastavit vlastnosti k určení pozice popisku obsah pomocí <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> vlastnosti, viz [umístění objektu ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Používání stylů pro popis tlačítka  
 Můžete nastavit styl <xref:System.Windows.Controls.ToolTip> tak, že definujete vlastní <xref:System.Windows.Style>. Následující příklad definuje <xref:System.Windows.Style> volá `Simple` , který ukazuje, jak posun umístění <xref:System.Windows.Controls.ToolTip> a změňte jeho vzhled pomocí nastavení <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, a <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Pomocí vlastnosti Interval doby ToolTipService  
 <xref:System.Windows.Controls.ToolTipService> Třída poskytuje následující vlastnosti lze nastavit popisek zobrazí časy: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Použití <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> vlastnosti k určení zpoždění, obvykle (BRIEF), než <xref:System.Windows.Controls.ToolTip> se zobrazí a také k určení, jak dlouho <xref:System.Windows.Controls.ToolTip> zůstává viditelná. Další informace najdete v tématu [jak: Prodleva zobrazení popisu](https://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Vlastnost určuje, pokud popisky dat pro různé ovládací prvky se zobrazí počáteční neprodleně při přesunutí ukazatele myši rychle mezi nimi. Další informace o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> vlastnost, naleznete v tématu [používání vlastnosti BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 Následující příklad ukazuje, jak nastavit tyto vlastnosti pro popis.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [Témata s postupy](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
