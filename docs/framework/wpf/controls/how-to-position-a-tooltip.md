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
ms.locfileid: "33555935"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="66b50-102">Postupy: Umístění objektu ToolTip</span><span class="sxs-lookup"><span data-stu-id="66b50-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="66b50-103">Tento příklad ukazuje, jak určit umístění popisek na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="66b50-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66b50-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="66b50-104">Example</span></span>  
 <span data-ttu-id="66b50-105">Popisek můžete umístit pomocí sadu pěti vlastností, které jsou definovány v obou <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy.</span><span class="sxs-lookup"><span data-stu-id="66b50-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="66b50-106">Následující tabulka uvádí tyto dvě sady pěti vlastností a poskytuje odkazy na jejich referenční dokumentaci podle třídy.</span><span class="sxs-lookup"><span data-stu-id="66b50-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="66b50-107">Odpovídající vlastnosti popisek podle – třída</span><span class="sxs-lookup"><span data-stu-id="66b50-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="66b50-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="66b50-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="66b50-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="66b50-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="66b50-110">Definovat obsah popisek pomocí <xref:System.Windows.Controls.ToolTip> objekt, můžete použít vlastnosti buď třídy, nicméně <xref:System.Windows.Controls.ToolTipService> vlastnosti mají přednost před.</span><span class="sxs-lookup"><span data-stu-id="66b50-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="66b50-111">Použití <xref:System.Windows.Controls.ToolTipService> vlastnosti pro popisy tlačítek, které nejsou definovány jako <xref:System.Windows.Controls.ToolTip> objekty.</span><span class="sxs-lookup"><span data-stu-id="66b50-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="66b50-112">Následující ilustrace znázorňují postup umístit popisek pomocí těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="66b50-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="66b50-113">I když, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady v těchto obrázky ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> třídy, odpovídající vlastnosti <xref:System.Windows.Controls.ToolTipService> třída stejným pravidlům rozložení.</span><span class="sxs-lookup"><span data-stu-id="66b50-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="66b50-114">Další informace o možných hodnot pro vlastnost umístění najdete v tématu [chování místní umístění](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="66b50-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="66b50-115">![Umístění popisku](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="66b50-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="66b50-116">Popis umístění pomocí vlastnosti umístění</span><span class="sxs-lookup"><span data-stu-id="66b50-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="66b50-117">![Umístění popisek pomocí obdélníku umístění](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="66b50-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="66b50-118">Popis umístění pomocí vlastnosti umístění a PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="66b50-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="66b50-119">![Diagram umístění popisu tlačítka](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="66b50-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="66b50-120">Popis umístění pomocí vlastnosti umístění, PlacementRectangle a odsazení</span><span class="sxs-lookup"><span data-stu-id="66b50-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="66b50-121">Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTip> vlastnosti k určení umístění popisku, jejichž obsah se nachází <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="66b50-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="66b50-122">Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTipService> vlastnosti k určení umístění popisku, jejichž obsah není <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="66b50-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="66b50-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="66b50-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="66b50-124">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="66b50-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="66b50-125">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="66b50-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="66b50-126">Použít ContextMenuService a ToolTipService</span><span class="sxs-lookup"><span data-stu-id="66b50-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/library/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
