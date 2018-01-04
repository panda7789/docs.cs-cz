---
title: "Postupy: Umístění objektu ToolTip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62e86f2adfbe8f8aac000d653e955555c7def750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="9d9b9-102">Postupy: Umístění objektu ToolTip</span><span class="sxs-lookup"><span data-stu-id="9d9b9-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="9d9b9-103">Tento příklad ukazuje, jak určit umístění popisek na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d9b9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d9b9-104">Example</span></span>  
 <span data-ttu-id="9d9b9-105">Popisek můžete umístit pomocí sadu pěti vlastností, které jsou definovány v obou <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="9d9b9-106">Následující tabulka uvádí tyto dvě sady pěti vlastností a poskytuje odkazy na jejich referenční dokumentaci podle třídy.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="9d9b9-107">Odpovídající vlastnosti popisek podle – třída</span><span class="sxs-lookup"><span data-stu-id="9d9b9-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="9d9b9-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="9d9b9-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="9d9b9-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="9d9b9-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="9d9b9-110">Definovat obsah popisek pomocí <xref:System.Windows.Controls.ToolTip> objekt, můžete použít vlastnosti buď třídy, nicméně <xref:System.Windows.Controls.ToolTipService> vlastnosti mají přednost před.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="9d9b9-111">Použití <xref:System.Windows.Controls.ToolTipService> vlastnosti pro popisy tlačítek, které nejsou definovány jako <xref:System.Windows.Controls.ToolTip> objekty.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="9d9b9-112">Následující ilustrace znázorňují postup umístit popisek pomocí těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="9d9b9-113">I když, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady v těchto obrázky ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> třídy, odpovídající vlastnosti <xref:System.Windows.Controls.ToolTipService> třída stejným pravidlům rozložení.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="9d9b9-114">Další informace o možných hodnot pro vlastnost umístění najdete v tématu [chování místní umístění](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="9d9b9-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="9d9b9-115">![Umístění popisku](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="9d9b9-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="9d9b9-116">Popis umístění pomocí vlastnosti umístění</span><span class="sxs-lookup"><span data-stu-id="9d9b9-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="9d9b9-117">![Umístění popisek pomocí obdélníku umístění](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="9d9b9-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="9d9b9-118">Popis umístění pomocí vlastnosti umístění a PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="9d9b9-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="9d9b9-119">![Diagram umístění popisu tlačítka](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="9d9b9-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="9d9b9-120">Popis umístění pomocí vlastnosti umístění, PlacementRectangle a odsazení</span><span class="sxs-lookup"><span data-stu-id="9d9b9-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="9d9b9-121">Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTip> vlastnosti k určení umístění popisku, jejichž obsah se nachází <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="9d9b9-122">Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTipService> vlastnosti k určení umístění popisku, jejichž obsah není <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="9d9b9-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="9d9b9-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d9b9-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="9d9b9-124">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="9d9b9-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="9d9b9-125">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="9d9b9-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="9d9b9-126">Použít ContextMenuService a ToolTipService</span><span class="sxs-lookup"><span data-stu-id="9d9b9-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/en-us/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
