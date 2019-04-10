---
title: 'Postupy: Umístění prvku ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 811818fe6e7c0d8ce9e2aa058b42bf592ada4b92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212346"
---
# <a name="how-to-position-a-tooltip"></a>Postupy: Umístění prvku ToolTip
Tento příklad ukazuje, jak určit pozici popisku na obrazovce.  
  
## <a name="example"></a>Příklad  
 Můžete umístění objektu tooltip s použitím sadu pěti vlastností, které jsou definovány v obou <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy. Následující tabulka uvádí těmito dvěma sadami pěti vlastností a obsahuje odkazy na jejich referenční dokumentaci podle třídy.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Odpovídající vlastnosti popisku podle třídy  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Vlastnosti třídy|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Vlastnosti třídy|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Pokud definujete obsah popisek pomocí <xref:System.Windows.Controls.ToolTip> objektu, můžete použít vlastnosti žádné ze tříd, nicméně <xref:System.Windows.Controls.ToolTipService> vlastnosti mají přednost. Použití <xref:System.Windows.Controls.ToolTipService> vlastnosti pro popisy tlačítek, které nejsou definovány jako <xref:System.Windows.Controls.ToolTip> objekty.  
  
 Následující obrázky ukazují, jak pomocí těchto vlastností umístění objektu tooltip. I když se [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tyto příklady ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> odpovídající vlastnosti z třídy <xref:System.Windows.Controls.ToolTipService> třídy řídit stejnými pravidly rozložení. Další informace o možných hodnot pro vlastnost umístění najdete v tématu [chování při umístění automaticky otevíraného okna](popup-placement-behavior.md).  
 
 Umístění popisku pomocí vlastnosti umístění na následujícím obrázku:  
  
 ![Diagram znázorňující umístění popisku pomocí vlastnosti umístění.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 Umístění popisku pomocí vlastnosti umístění a PlacementRectangle na následujícím obrázku:   

 ![Diagram znázorňující umístění popisku pomocí vlastnosti PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 Umístění popisku pomocí vlastnosti umístění, PlacementRectangle a posun na následujícím obrázku:   
  
 ![Diagram znázorňující umístění popisku pomocí vlastnosti posun.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTip> vlastnosti k určení pozice popisku, jejichž obsah je <xref:System.Windows.Controls.ToolTip> objektu.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTipService> vlastnosti k určení pozice popisku, jejichž obsah je <xref:System.Windows.Controls.ToolTip> objektu.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [– postupy](tooltip-how-to-topics.md)
- [ToolTip – přehled](tooltip-overview.md)
