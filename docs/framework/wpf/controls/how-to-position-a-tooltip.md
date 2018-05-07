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
ms.openlocfilehash: 218d8814cf75cd80a63c94397ed00e92c6a9a8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-position-a-tooltip"></a>Postupy: Umístění objektu ToolTip
Tento příklad ukazuje, jak určit umístění popisek na obrazovce.  
  
## <a name="example"></a>Příklad  
 Popisek můžete umístit pomocí sadu pěti vlastností, které jsou definovány v obou <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy. Následující tabulka uvádí tyto dvě sady pěti vlastností a poskytuje odkazy na jejich referenční dokumentaci podle třídy.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Odpovídající vlastnosti popisek podle – třída  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Vlastnosti třídy|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Vlastnosti třídy|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Definovat obsah popisek pomocí <xref:System.Windows.Controls.ToolTip> objekt, můžete použít vlastnosti buď třídy, nicméně <xref:System.Windows.Controls.ToolTipService> vlastnosti mají přednost před. Použití <xref:System.Windows.Controls.ToolTipService> vlastnosti pro popisy tlačítek, které nejsou definovány jako <xref:System.Windows.Controls.ToolTip> objekty.  
  
 Následující ilustrace znázorňují postup umístit popisek pomocí těchto vlastností. I když, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady v těchto obrázky ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> třídy, odpovídající vlastnosti <xref:System.Windows.Controls.ToolTipService> třída stejným pravidlům rozložení. Další informace o možných hodnot pro vlastnost umístění najdete v tématu [chování místní umístění](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).  
  
 ![Umístění popisku](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
Popis umístění pomocí vlastnosti umístění  
  
 ![Umístění popisek pomocí obdélníku umístění](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
Popis umístění pomocí vlastnosti umístění a PlacementRectangle  
  
 ![Diagram umístění popisu tlačítka](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
Popis umístění pomocí vlastnosti umístění, PlacementRectangle a odsazení  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTip> vlastnosti k určení umístění popisku, jejichž obsah se nachází <xref:System.Windows.Controls.ToolTip> objektu.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTipService> vlastnosti k určení umístění popisku, jejichž obsah není <xref:System.Windows.Controls.ToolTip> objektu.  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Témata s postupy](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [ToolTip – přehled](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [Použít ContextMenuService a ToolTipService](http://msdn.microsoft.com/library/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
