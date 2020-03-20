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
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="e6ec2-102">Postupy: Umístění objektu ToolTip</span><span class="sxs-lookup"><span data-stu-id="e6ec2-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="e6ec2-103">Tento příklad ukazuje, jak určit umístění popisku na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6ec2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6ec2-104">Example</span></span>  
 <span data-ttu-id="e6ec2-105">Popis ekviátní bod můžete umístit pomocí sady <xref:System.Windows.Controls.ToolTip> pěti <xref:System.Windows.Controls.ToolTipService> vlastností, které jsou definovány v a třídách.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="e6ec2-106">V následující tabulce jsou uvedeny tyto dvě sady pěti vlastností a obsahuje odkazy na jejich referenční dokumentaci podle třídy.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="e6ec2-107">Odpovídající vlastnosti popisku podle třídy</span><span class="sxs-lookup"><span data-stu-id="e6ec2-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="e6ec2-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="e6ec2-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="e6ec2-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="e6ec2-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="e6ec2-110">Pokud definujete obsah popisku pomocí <xref:System.Windows.Controls.ToolTip> objektu, můžete použít vlastnosti obou tříd; vlastnosti <xref:System.Windows.Controls.ToolTipService> však mají přednost.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="e6ec2-111">Vlastnosti <xref:System.Windows.Controls.ToolTipService> použijte pro popisky, <xref:System.Windows.Controls.ToolTip> které nejsou definovány jako objekty.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="e6ec2-112">Následující ilustrace ukazují, jak umístit popis pomocí těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="e6ec2-113">Ačkoli příklady na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] těchto obrázcích ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> třídou, odpovídající vlastnosti <xref:System.Windows.Controls.ToolTipService> třídy postupujte podle stejných pravidel rozložení.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="e6ec2-114">Další informace o možných hodnotách vlastnosti Umístění naleznete v tématu [Chování umístění v místních rozteklích](popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="e6ec2-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  

 <span data-ttu-id="e6ec2-115">Následující obrázek znázorňuje umístění popisku pomocí vlastnosti Umístění:</span><span class="sxs-lookup"><span data-stu-id="e6ec2-115">The following image shows tooltip placement by using the Placement property:</span></span>  
  
 ![Diagram znázorňující umístění popisu pomocí vlastnosti Umístění.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 <span data-ttu-id="e6ec2-117">Následující obrázek znázorňuje umístění popisku pomocí vlastností Umístění a UmístěníRectangle:</span><span class="sxs-lookup"><span data-stu-id="e6ec2-117">The following image shows tooltip placement by using the Placement and PlacementRectangle properties:</span></span>

 ![Diagram znázorňující umístění popisu pomocí vlastnosti PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 <span data-ttu-id="e6ec2-119">Následující obrázek znázorňuje umístění popisu pomocí vlastností Umístění, UmístěníRectangle a Posun:</span><span class="sxs-lookup"><span data-stu-id="e6ec2-119">The following image shows tooltip placement by using the Placement, PlacementRectangle, and Offset properties:</span></span>
  
 ![Diagram znázorňující umístění popisu pomocí vlastnosti Posun.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <span data-ttu-id="e6ec2-121">Následující příklad ukazuje, jak <xref:System.Windows.Controls.ToolTip> použít vlastnosti k určení polohy popisku, jehož obsah je <xref:System.Windows.Controls.ToolTip> objekt.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="e6ec2-122">Následující příklad ukazuje, jak <xref:System.Windows.Controls.ToolTipService> použít vlastnosti k určení polohy popisku, jehož obsah není objektem. <xref:System.Windows.Controls.ToolTip></span><span class="sxs-lookup"><span data-stu-id="e6ec2-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="e6ec2-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6ec2-123">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="e6ec2-124">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e6ec2-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="e6ec2-125">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="e6ec2-125">ToolTip Overview</span></span>](tooltip-overview.md)
