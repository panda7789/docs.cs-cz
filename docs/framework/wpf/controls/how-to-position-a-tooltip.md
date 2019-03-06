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
ms.openlocfilehash: d20eea0890708eb2ec2ada503f5c871d54ccc035
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364530"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="d78e6-102">Postupy: Umístění objektu ToolTip</span><span class="sxs-lookup"><span data-stu-id="d78e6-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="d78e6-103">Tento příklad ukazuje, jak určit pozici popisku na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="d78e6-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d78e6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d78e6-104">Example</span></span>  
 <span data-ttu-id="d78e6-105">Můžete umístění objektu tooltip s použitím sadu pěti vlastností, které jsou definovány v obou <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy.</span><span class="sxs-lookup"><span data-stu-id="d78e6-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="d78e6-106">Následující tabulka uvádí těmito dvěma sadami pěti vlastností a obsahuje odkazy na jejich referenční dokumentaci podle třídy.</span><span class="sxs-lookup"><span data-stu-id="d78e6-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="d78e6-107">Odpovídající vlastnosti popisku podle třídy</span><span class="sxs-lookup"><span data-stu-id="d78e6-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="d78e6-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="d78e6-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="d78e6-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="d78e6-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="d78e6-110">Pokud definujete obsah popisek pomocí <xref:System.Windows.Controls.ToolTip> objektu, můžete použít vlastnosti žádné ze tříd, nicméně <xref:System.Windows.Controls.ToolTipService> vlastnosti mají přednost.</span><span class="sxs-lookup"><span data-stu-id="d78e6-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="d78e6-111">Použití <xref:System.Windows.Controls.ToolTipService> vlastnosti pro popisy tlačítek, které nejsou definovány jako <xref:System.Windows.Controls.ToolTip> objekty.</span><span class="sxs-lookup"><span data-stu-id="d78e6-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="d78e6-112">Následující obrázky ukazují, jak pomocí těchto vlastností umístění objektu tooltip.</span><span class="sxs-lookup"><span data-stu-id="d78e6-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="d78e6-113">I když se [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tyto příklady ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> odpovídající vlastnosti z třídy <xref:System.Windows.Controls.ToolTipService> třídy řídit stejnými pravidly rozložení.</span><span class="sxs-lookup"><span data-stu-id="d78e6-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="d78e6-114">Další informace o možných hodnot pro vlastnost umístění najdete v tématu [chování při umístění automaticky otevíraného okna](popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="d78e6-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="d78e6-115">![Umístění popisku](./media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="d78e6-115">![ToolTip placement](./media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="d78e6-116">Umístění popisku pomocí vlastnosti umístění</span><span class="sxs-lookup"><span data-stu-id="d78e6-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="d78e6-117">![Umístění popisku pomocí umístění obdélník](./media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="d78e6-117">![Placing a ToolTip by using a placement rectangle](./media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="d78e6-118">Umístění popisku pomocí vlastnosti umístění a PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="d78e6-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="d78e6-119">![Diagram umístění popisku](./media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="d78e6-119">![ToolTip placement diagram](./media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="d78e6-120">Umístění popisku pomocí vlastnosti umístění, PlacementRectangle a odsazení</span><span class="sxs-lookup"><span data-stu-id="d78e6-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="d78e6-121">Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTip> vlastnosti k určení pozice popisku, jejichž obsah je <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="d78e6-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="d78e6-122">Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTipService> vlastnosti k určení pozice popisku, jejichž obsah je <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="d78e6-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="d78e6-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d78e6-123">See also</span></span>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="d78e6-124">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="d78e6-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="d78e6-125">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="d78e6-125">ToolTip Overview</span></span>](tooltip-overview.md)
