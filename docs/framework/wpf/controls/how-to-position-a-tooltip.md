---
title: 'Postupy: Umístění objektu ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186942"
---
# <a name="how-to-position-a-tooltip"></a>Postupy: Umístění objektu ToolTip
Tento příklad ukazuje, jak určit umístění popisku na obrazovce.  
  
## <a name="example"></a>Příklad  
 Popis ekviátní bod můžete umístit pomocí sady <xref:System.Windows.Controls.ToolTip> pěti <xref:System.Windows.Controls.ToolTipService> vlastností, které jsou definovány v a třídách. V následující tabulce jsou uvedeny tyto dvě sady pěti vlastností a obsahuje odkazy na jejich referenční dokumentaci podle třídy.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Odpovídající vlastnosti popisku podle třídy  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>vlastnosti třídy|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>vlastnosti třídy|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Pokud definujete obsah popisku pomocí <xref:System.Windows.Controls.ToolTip> objektu, můžete použít vlastnosti obou tříd; vlastnosti <xref:System.Windows.Controls.ToolTipService> však mají přednost. Vlastnosti <xref:System.Windows.Controls.ToolTipService> použijte pro popisky, <xref:System.Windows.Controls.ToolTip> které nejsou definovány jako objekty.  
  
 Následující ilustrace ukazují, jak umístit popis pomocí těchto vlastností. Ačkoli příklady na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] těchto obrázcích ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> třídou, odpovídající vlastnosti <xref:System.Windows.Controls.ToolTipService> třídy postupujte podle stejných pravidel rozložení. Další informace o možných hodnotách vlastnosti Umístění naleznete v tématu [Chování umístění v místních rozteklích](popup-placement-behavior.md).  

 Následující obrázek znázorňuje umístění popisku pomocí vlastnosti Umístění:  
  
 ![Diagram znázorňující umístění popisu pomocí vlastnosti Umístění.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 Následující obrázek znázorňuje umístění popisku pomocí vlastností Umístění a UmístěníRectangle:

 ![Diagram znázorňující umístění popisu pomocí vlastnosti PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 Následující obrázek znázorňuje umístění popisu pomocí vlastností Umístění, UmístěníRectangle a Posun:
  
 ![Diagram znázorňující umístění popisu pomocí vlastnosti Posun.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 Následující příklad ukazuje, jak <xref:System.Windows.Controls.ToolTip> použít vlastnosti k určení polohy popisku, jehož obsah je <xref:System.Windows.Controls.ToolTip> objekt.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.ToolTipService> použít vlastnosti k určení polohy popisku, jehož obsah není objektem. <xref:System.Windows.Controls.ToolTip>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Témata s postupy](tooltip-how-to-topics.md)
- [ToolTip – přehled](tooltip-overview.md)
