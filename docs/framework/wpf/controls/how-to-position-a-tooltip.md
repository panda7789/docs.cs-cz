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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212346"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="b758c-102">Postupy: Umístění prvku ToolTip</span><span class="sxs-lookup"><span data-stu-id="b758c-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="b758c-103">Tento příklad ukazuje, jak určit pozici popisku na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="b758c-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b758c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b758c-104">Example</span></span>  
 <span data-ttu-id="b758c-105">Můžete umístění objektu tooltip s použitím sadu pěti vlastností, které jsou definovány v obou <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy.</span><span class="sxs-lookup"><span data-stu-id="b758c-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="b758c-106">Následující tabulka uvádí těmito dvěma sadami pěti vlastností a obsahuje odkazy na jejich referenční dokumentaci podle třídy.</span><span class="sxs-lookup"><span data-stu-id="b758c-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="b758c-107">Odpovídající vlastnosti popisku podle třídy</span><span class="sxs-lookup"><span data-stu-id="b758c-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="b758c-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="b758c-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="b758c-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Vlastnosti třídy</span><span class="sxs-lookup"><span data-stu-id="b758c-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="b758c-110">Pokud definujete obsah popisek pomocí <xref:System.Windows.Controls.ToolTip> objektu, můžete použít vlastnosti žádné ze tříd, nicméně <xref:System.Windows.Controls.ToolTipService> vlastnosti mají přednost.</span><span class="sxs-lookup"><span data-stu-id="b758c-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="b758c-111">Použití <xref:System.Windows.Controls.ToolTipService> vlastnosti pro popisy tlačítek, které nejsou definovány jako <xref:System.Windows.Controls.ToolTip> objekty.</span><span class="sxs-lookup"><span data-stu-id="b758c-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="b758c-112">Následující obrázky ukazují, jak pomocí těchto vlastností umístění objektu tooltip.</span><span class="sxs-lookup"><span data-stu-id="b758c-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="b758c-113">I když se [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tyto příklady ukazují, jak nastavit vlastnosti, které jsou definovány <xref:System.Windows.Controls.ToolTip> odpovídající vlastnosti z třídy <xref:System.Windows.Controls.ToolTipService> třídy řídit stejnými pravidly rozložení.</span><span class="sxs-lookup"><span data-stu-id="b758c-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="b758c-114">Další informace o možných hodnot pro vlastnost umístění najdete v tématu [chování při umístění automaticky otevíraného okna](popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="b758c-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  
 
 <span data-ttu-id="b758c-115">Umístění popisku pomocí vlastnosti umístění na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="b758c-115">The following image shows tooltip placement by using the Placement property:</span></span>  
  
 ![Diagram znázorňující umístění popisku pomocí vlastnosti umístění.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 <span data-ttu-id="b758c-117">Umístění popisku pomocí vlastnosti umístění a PlacementRectangle na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="b758c-117">The following image shows tooltip placement by using the Placement and PlacementRectangle properties:</span></span>   

 ![Diagram znázorňující umístění popisku pomocí vlastnosti PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 <span data-ttu-id="b758c-119">Umístění popisku pomocí vlastnosti umístění, PlacementRectangle a posun na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="b758c-119">The following image shows tooltip placement by using the Placement, PlacementRectangle, and Offset properties:</span></span>   
  
 ![Diagram znázorňující umístění popisku pomocí vlastnosti posun.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <span data-ttu-id="b758c-121">Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTip> vlastnosti k určení pozice popisku, jejichž obsah je <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="b758c-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="b758c-122">Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTipService> vlastnosti k určení pozice popisku, jejichž obsah je <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="b758c-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="b758c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b758c-123">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="b758c-124">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="b758c-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="b758c-125">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="b758c-125">ToolTip Overview</span></span>](tooltip-overview.md)
