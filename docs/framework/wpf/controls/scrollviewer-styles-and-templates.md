---
title: ScrollViewer – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 5ad3738972ae9b33764d3b710077f6d4a0526a13
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="1c85e-102">ScrollViewer – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1c85e-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="1c85e-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c85e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="1c85e-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c85e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1c85e-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku tak, že vytvoříte ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="1c85e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="1c85e-106">ScrollViewer částí</span><span class="sxs-lookup"><span data-stu-id="1c85e-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="1c85e-107">V následující tabulce jsou uvedené části s názvem pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c85e-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="1c85e-108">Část</span><span class="sxs-lookup"><span data-stu-id="1c85e-108">Part</span></span>|<span data-ttu-id="1c85e-109">Typ</span><span class="sxs-lookup"><span data-stu-id="1c85e-109">Type</span></span>|<span data-ttu-id="1c85e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1c85e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1c85e-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="1c85e-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="1c85e-112">Zástupný symbol pro obsah <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="1c85e-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="1c85e-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="1c85e-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="1c85e-114"><xref:System.Windows.Controls.Primitives.ScrollBar> Používá k vodorovnému posouvání obsahu.</span><span class="sxs-lookup"><span data-stu-id="1c85e-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="1c85e-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="1c85e-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="1c85e-116"><xref:System.Windows.Controls.Primitives.ScrollBar> Umožňuje procházet obsah vertikálně.</span><span class="sxs-lookup"><span data-stu-id="1c85e-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="1c85e-117">ScrollViewer stavy</span><span class="sxs-lookup"><span data-stu-id="1c85e-117">ScrollViewer States</span></span>  
 <span data-ttu-id="1c85e-118">Následující tabulka uvádí visual stavy pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c85e-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="1c85e-119">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="1c85e-119">VisualState Name</span></span>|<span data-ttu-id="1c85e-120">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="1c85e-120">VisualStateGroup Name</span></span>|<span data-ttu-id="1c85e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1c85e-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1c85e-122">Platné</span><span class="sxs-lookup"><span data-stu-id="1c85e-122">Valid</span></span>|<span data-ttu-id="1c85e-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c85e-123">ValidationStates</span></span>|<span data-ttu-id="1c85e-124">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je přidružená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="1c85e-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1c85e-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1c85e-125">InvalidFocused</span></span>|<span data-ttu-id="1c85e-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c85e-126">ValidationStates</span></span>|<span data-ttu-id="1c85e-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="1c85e-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1c85e-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1c85e-128">InvalidUnfocused</span></span>|<span data-ttu-id="1c85e-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1c85e-129">ValidationStates</span></span>|<span data-ttu-id="1c85e-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je přidružená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="1c85e-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="1c85e-131">Příklad ControlTemplate ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="1c85e-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="1c85e-132">Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c85e-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="1c85e-133">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="1c85e-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1c85e-134">Kompletní příklad, najdete v části [styly s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="1c85e-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c85e-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c85e-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="1c85e-136">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="1c85e-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="1c85e-137">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="1c85e-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="1c85e-138">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1c85e-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="1c85e-139">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1c85e-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
